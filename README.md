# Golang complier study

Hi all. This golang fork adds `try` keyword to golang compiler so you do not need to write ```if err != nil ``` every time.
``` go
    try file, err := parser.ParseFile(path)
    fmt.Println(file) 
```


## Usage:

1. Clone this repo.
2. Build compiler with all.bash
3. Compile code with new compiler:

```
~/code/go/bin/go build
```

``` go
func testFn(err error) (int, error) {
    return 99, err
}

func sampleFn() (v int, err error) { // Remember to use named return params for "try" to work properly
    try v, err := testFn(errors.New("test error"))
    panic("not this time")
}
```

Compiler will expand `try` to

```
    v, err := testFn(errors.New("test error"))
    if err != nil {
        return
    }
```

## gopls

If you like to add support to gopls just compile gotools fork and move to bin dir.

```
git clone git@github.com:study-gocompiler/gotools.git
cd gotools/gopls
~/code/go/bin/go build
mv gopls TO bin
```

# The Go Programming Language

Go is an open source programming language that makes it easy to build simple,
reliable, and efficient software.

![Gopher image](https://golang.org/doc/gopher/fiveyears.jpg)
*Gopher image by [Renee French][rf], licensed under [Creative Commons 4.0 Attributions license][cc4-by].*

Our canonical Git repository is located at https://go.googlesource.com/go.
There is a mirror of the repository at https://github.com/golang/go.

Unless otherwise noted, the Go source files are distributed under the
BSD-style license found in the LICENSE file.

### Download and Install

#### Binary Distributions

Official binary distributions are available at https://go.dev/dl/.

After downloading a binary release, visit https://go.dev/doc/install
for installation instructions.

#### Install From Source

If a binary distribution is not available for your combination of
operating system and architecture, visit
https://go.dev/doc/install/source
for source installation instructions.

### Contributing

Go is the work of thousands of contributors. We appreciate your help!

To contribute, please read the contribution guidelines at https://go.dev/doc/contribute.

Note that the Go project uses the issue tracker for bug reports and
proposals only. See https://go.dev/wiki/Questions for a list of
places to ask questions about the Go language.

[rf]: https://reneefrench.blogspot.com/
[cc4-by]: https://creativecommons.org/licenses/by/4.0/
