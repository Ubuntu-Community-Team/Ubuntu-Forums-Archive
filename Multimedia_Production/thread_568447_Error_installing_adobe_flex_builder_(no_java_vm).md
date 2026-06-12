---
title: "Error installing adobe flex builder (no java vm?)"
date: 2007-10-05
forum: Multimedia Production
---

### Post by djrobthaman on 2007-10-05
Hi there everyone,

So I finally found out about adobe flex which looks like it actually brings flash development to linux.  But now that I've downloaded the file it won't install.  Does anybody know how to get it installed?

Just for reference here's the output I get from the terminal when I run the file.

```

douglas@douglas-desktop:~$ '/home/douglas/Desktop/flexbuilder_linux_install_a1_100207.bin' 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

```

---

### Post by suoko on 2007-10-06
install sun-java6-jre
and then choose it in the list proposed after the command:
sudo update-alternatives --config java

---

### Post by djrobthaman on 2007-10-07
Thanks,

It worked.  I had it installed but not selected.  The install works fine now.  Just have to install eclipse 3.3 (somehow that's not the latest version in the repositories that I have)

---

### Post by xunling on 2008-05-30
can somebody plz help me under gentoo?

i want to install flex under gentoo but i have the same error, the command doesnt work,

is there any else command i can try?

---

