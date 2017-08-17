# proxy-check

Mass proxy checker.

## Usage

Make sure you have [curl](https://curl.haxx.se/) and
[newlisp](http://newlisp.org) installed. To run it, use:

```sh
newlisp proxy-check <file>
```

`<file>` will be a file path with list of proxies you'd like to
try. The format is proxy address with port per line, like:

```
127.0.0.1:9050
8.8.8.8:80
...
```

In case you'd like to speed it up by testing 3 hosts at the same time,
use `-m` option, like:

```sh
newlisp proxy-check -m <file>
```

Output will be put in terminal (stdout) in form proxy address and
`good` or `bad` string, depending on status, like:

```
127.0.0.1:9050 good
8.8.8.8:80 bad
...
```

Use `sed` to filter out only good proxies, in case of huge number of
them, like:

```sh
$ newlisp proxy-check -m proxies.txt | sed -ne '/good/p'
```

## Testing host

By default http://google.com is used as testing host. To change it,
edit `proxy-check` file and change `*test-host*` variable on top of
the file.

## License

Copyright © 2017 Sanel Zukan.
