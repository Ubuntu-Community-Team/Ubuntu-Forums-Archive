---
title: "Can't play dvd'z.."
date: 2008-12-27
forum: Multimedia Software
---

### Post by DelawerH on 2008-12-27
trying to play dvd's but get this error msg 

[[IMG]http://img123.imageshack.us/img123/3388/49912677wc7.png[/IMG]](http://imageshack.us)
By [DelawerH](http://profile.imageshack.us/user/DelawerH)

---

### Post by 2hot6ft2 on 2008-12-27
You need this in a terminal
Applications>Accessories>Terminal
> **Toshibawarrior said:**
> Then for playback type this on a terminal:

```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```

These lackages are also necessary...:) Hope this helps!

---

### Post by DelawerH on 2008-12-27
> **2hot6ft2 said:**
> You need this in a terminal
Applications>Accessories>Terminal



i Get this

shaju@shaju-desktop:~$ sudo apt-get install ubuntu-restricted-extras libdvdcss2
[sudo] password for shaju: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
shaju@shaju-desktop:~$

---

### Post by taurus on 2008-12-27
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by 2hot6ft2 on 2008-12-27
Interesting.
You can also get it here just get the one for which ever your OS is i386 or AMD64 bit. [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html)

You might also want to run ```
sudo apt-get update
```

---

