---
title: "[SOLVED] no audio for wmv format"
date: 2008-02-13
forum: Multimedia Production
---

### Post by vikasmk on 2008-02-13
i there is no audio coming for wmv format is there some sort of plugin for totem player????

---

### Post by linuxwizard on 2008-02-13
Make sure you have all codecs installed.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Have you installed the w32codecs you will need for wmv.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by vikasmk on 2008-02-15
i tried installing it but this is what i got

vikasmk@vikasmk:~$ sudo apt-get install w32codecs
[sudo] password for vikasmk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
 
 what next ???????:confused:

---

### Post by linuxwizard on 2008-02-15
For i386, the package is called w32codecs:
Copy & Paste below into teriminal make sure you get all text.

wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

---

### Post by vikasmk on 2008-02-17
vikasmk@vikasmk:~$ wget -c [http://packages.medibuntu.org/pool/n...untu1_i386.deb](http://packages.medibuntu.org/pool/n...untu1_i386.deb)
--22:19:34--  [http://packages.medibuntu.org/pool/n...untu1_i386.deb](http://packages.medibuntu.org/pool/n...untu1_i386.deb)
           => `n...untu1_i386.deb'
Resolving packages.medibuntu.org... failed: Name or service not known.
vikasmk@vikasmk:~$ sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb
[sudo] password for vikasmk:
dpkg: error processing w32codecs_20071007-0medibuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20071007-0medibuntu1_i386.deb
 
 :(

---

### Post by vikasmk on 2008-03-01
Hello  a little help here:confused:

---

### Post by Pancake8989 on 2008-03-28
Try:
```

wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

```

---

