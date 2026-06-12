---
title: "Graphics Card Problem with 3.2.0-38 linux headers"
date: 2013-02-21
forum: Multimedia Software
---

### Post by ceezax on 2013-02-21
Hello,

After upgrading my linux headers from 3.2.0-37 to 3.2.0-38, the system does not load and present the following error:

"The system is running in low-graphics mode"

I tried multiple things to fix it, but no luck. I was able to use my system again after pressing SHIFT and selecting "use previous version of linux" which loaded the old 3.2.0-37 and everything is fine.

This line is listed in my hardawre as a graphic driver:
"VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]"

Now, what should I do ? Should I remove the new linux headers and stick to the old one 3.2.0-37 which is working fine ?

Thanks in advance.

---

### Post by kholburn on 2013-02-21
> **ceezax said:**
> Hello,

After upgrading my linux headers from 3.2.0-37 to 3.2.0-38, the system does not load and present the following error:

"The system is running in low-graphics mode"

....

Now, what should I do ? Should I remove the new linux headers and stick to the old one 3.2.0-37 which is working fine ?

Thanks in advance.

Not that you should do this but I had the same problem with my ATI Radeon HD 6450 at linux kernel 3.2.0-33.  I changed grub so that my system always boots 3.2.0-31.  I edited /etc/default/grub and added this line:
```

GRUB_DEFAULT="2>Ubuntu, with Linux 3.2.0-31-generic"

```
The quotes are important.  The first 2 characters of the name "2>" indicate that the entry is in a grub submenu.  If you don't have a grub submenu you don't need them.

To find the exact thing to put there you look in the grub menu file.  The simplest way is to use this command from the terminal:
```
grep menuentry /boot/grub/grub.cfg
```
Put the name of the latest kernel that works like this:
```
GRUB_DEFAULT="Ubuntu, with Linux 3.2.0-37-generic"
```
You'll need to use a text editor running in privileged mode:
Either run a terminal command like:

```
sudo vim /etc/default/grub
```
or
```
sudo nano /etc/default/grub
```
or
use a graphical editor
```
gksudo gvim /etc/default/grub
```
or
instead of gvim: gedit, kwrite etc.

Once you've edited the file, run this command:
```
sudo update-grub
```
Then when you boot your system it should boot from the last working kernel.  When new kernels come out you can try them and see if your graphics card works yet.  No luck for me so far.  Something about ATI cards seems to be not supported.

---

### Post by ceezax on 2013-02-21
Thank you for your response.

As per your response, I think that removing the new header is more convenient that editing the grub "please correct me if I am wrong". but actually, I do not know how to remove this new installed header without affecting the current one ?

---

### Post by howefield on 2013-02-21
> **ceezax said:**
> I tried multiple things to fix it, but no luck.

This information would be useful to anyone that wanted to help.

---

### Post by ceezax on 2013-02-21
Sorry for that. I followed the instructions listed here

[http://ubuntuforums.org/showthread.php?t=1968492](http://ubuntuforums.org/showthread.php?t=1968492)

---

### Post by kholburn on 2013-02-22
Each time you get a kernel upgrade you are going to face the same issue.

The other way is that because apparently there aren't drivers for the radeon HD series yet, you can install proprietary drivers.  Be warned though, you have to reinstall each time you get a kernel upgrade: 
[http://askubuntu.com/questions/25321/how-do-i-install-drivers-for-an-amd-radeon-hd-6450](http://askubuntu.com/questions/25321/how-do-i-install-drivers-for-an-amd-radeon-hd-6450)

---

