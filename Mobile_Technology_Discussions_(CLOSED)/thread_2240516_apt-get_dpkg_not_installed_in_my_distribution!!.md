---
title: "apt-get dpkg not installed in my distribution!! :\"
date: 2014-08-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by shanmukhateja on 2014-08-20
Hello there, I have downloaded this file "ubuntu-13.10.SMALL.ext4.img" from sourceforge today and have **mounted it in my mobile [Moto E] **and later I found out that it was **missing apt-get and dpkg. **Can anybody tell me 
    1>why was it missing 
    2>HOW DO I INSTALL APPS?

I need a vncserver and I can't seem to find any way to install apps to the distribution!


Thank you

---

### Post by Bashing-om on 2014-08-20
shanmukhateja; Hi !

I will take my stab at this:
1st -> "ubuntu-13.10.SMALL.ext4.img"; release 13.10 is End_Of_Life and has no support, thus I can believe supporting libraries are no longer available.

2nd -> you say "found out that it was missing apt-get and dpkg. Can anybody tell me " ; Well those come installed as default applications on every linux distribution - that I am aware of -.
Check and see:
```

dpkg -l apt
dpkg -l dpkg

```

3rd -> why do the vncserver the hard way ? Those tools are available in the software repository !
```

apt-cache search vncserver

```

[INDENT][INDENT]let's see where we go from here
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-08-21
> **shanmukhateja said:**
> Hello there, I have downloaded this file "ubuntu-13.10.SMALL.ext4.img" from sourceforge today

Downloading obsolete software from random internet places seems rather unwise and a waste of effort. Who knows what other surprises you have waiting?
Please see [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) for the official, supported, Minimal .iso.

---

### Post by shanmukhateja on 2014-08-21
Sorry it was my mistake, the PATH environment variable was missing a "/usr/bin:/usr/sbin" line and hence bash never saw the apps in the first place

Thank you for all the responses!

---

