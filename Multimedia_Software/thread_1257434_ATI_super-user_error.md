---
title: "ATI super-user error"
date: 2009-09-03
forum: Multimedia Software
---

### Post by kpholmes on 2009-09-03
ive installed the catalyst driver and it seems to be working fine, i can adjust color and which monitor to use but, cant change the resolution, it says i need to close the program and open it as super user. this is what i do

applications >>> other >>> ATI catalyst control center (super-user)

and i get this error:

**could not launch menu item**

Failed to execute child process "amdxdg-su" (No such file or directory)

after this i opened the terminal and typed: ```
amdxdg-su -c amdcccle
```

and receive this:

```
bash: amdxdg-su: command not found
```

so end result, regular user can open the regular ATI software, but can use the super user software or open from terminal as super user.

this is how i installed the driver

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

driver version is 8.64.3
catalyst 9.8


if anyone could help that would be awesome so im not stuck at 800 X 600

---

### Post by sora90 on 2009-09-13
I have the exact same problem and i used the steps in that site too... any solutions so far?

---

### Post by swajime on 2009-09-15
This is a duplicate post.  I answered this question here -> [http://ubuntuforums.org/showthread.php?p=7953477#post7953477](http://ubuntuforums.org/showthread.php?p=7953477#post7953477)

---

