---
title: "Java Media Framework"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Flacker2 on 2008-09-02
I put in this command:/bin/sh ./jmf-2_1_1e-linux-i586.bin

this was my output:
Unpacking...
tail: cannot open `+309' for reading: No such file or directory
Extracting...
./install.sfx.11135: 1: cannot open ==: No such file
./install.sfx.11135: 1: ==: not found
./install.sfx.11135: 3: Syntax error: ")" unexpected
chmod: cannot access `JMF-2.1.1e/bin/jmstudio': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfregistry': No such file or directory
chmod: cannot access `JMF-2.1.1e/bin/jmfinit': No such file or directory
./jmf-2_1_1e-linux-i586.bin: 305: JMF-2.1.1e/bin/jmfinit: not found
/bin/cp: cannot stat `JMF-2.1.1e/lib/jmf.properties': No such file or directory
this was after the license agreement and I'm on hardy... yes Im logged under root.

---

### Post by Briga on 2008-11-11
It's not your fault it's in the script. 

Before running the bin you need to give the following command:

```
sed -i 's/tail +309/tail -n +309/g' jmf-2_1_1e-linux-i586.bin
```

After that it should work (it did for me)

Briga

---

