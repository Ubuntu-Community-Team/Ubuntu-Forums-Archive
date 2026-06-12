---
title: "HowTo: Pipe scp to STDOUT"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by Filmorependrgn on 2009-09-26
The short answer: don't

Instead, use ssh. You can specify a command to do when ssh logs in. for example

```
$ ssh work.workdomain 'echo "testing"'
```

Let's say you have a file foo.tar.bz2 on a remote server (work.workdomain) that you would like to extract on your local server, and lets say that this is a very large file, so you don't want to download it, then extract.

One way around this problem is to do the following:
```
$ ssh work.workdomain 'cat foo.tar.bz2' | tar -jxv
```

This will transfer the whole archive, and extract it to the current directory.

---

