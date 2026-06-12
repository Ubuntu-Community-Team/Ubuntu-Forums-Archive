---
title: "FGLRX installation problem"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Law_Guy on 2008-07-27
I followed the directions here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I enabled the restricted ATI driver, it downloaded it and installed it automatically.

Then I tried the following.  Here is what I have in the terminal:

```
username@computername:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
[sudo] password for username: 
username@computername:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
insmod: error inserting '/lib/modules/2.6.24-19-generic/volatile/fglrx.ko': -1 Operation not permitted

```

What's with that error?  It happened the last time I tried this.  I know right now if I restart, the computer will get to the login screen, let me log-in, but then I'll just get a white screen.

Why is the operation not permitted and what should I do?

ETA: I replaced the real username and computer name as they appear in the terminal with "username@computername" just for security reasons.  Also, I'm running 8.04 with all of the latest updates.  This was after a fresh installation.

---

### Post by NvidiaN on 2008-07-27
I THINK you need to be in root to do that, but I'm far from a professional. Give that a try though.

---

### Post by Law_Guy on 2008-07-28
I thought Ubuntu had root locked out and that sudo was the only way to do things with administrative privileges?

---

### Post by Law_Guy on 2008-07-28
I can't figure out how to become root other than sudo.

Anybody know what to do to fix this?  I don't want to reboot until I get this resolved because I know if I do I'll just get a blank screen and will basically be locked out of anything other than a command prompt.

---

### Post by Law_Guy on 2008-07-28
nobody?

---

### Post by Law_Guy on 2008-07-29
I posted the output of dmesg here:

[http://pastebin.org/58289](http://pastebin.org/58289)

---

### Post by markbuntu on 2008-07-29
I don't know about that guide. It never worked for me. I use this one:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

