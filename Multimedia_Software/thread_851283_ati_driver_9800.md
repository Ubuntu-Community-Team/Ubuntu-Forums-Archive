---
title: "ati driver 9800"
date: 2008-07-06
forum: Multimedia Software
---

### Post by sonaural on 2008-07-06
when i installed the driver on prompt from my system, the graphics got worse.

i just downloaded the driver from the ati website but it won't open.

i already opened a terminal and checked exactly what my version of ubuntu and what graphics card i have.

any ideas why the driver won't even run?

---

### Post by sonaural on 2008-07-06
i think the problem with the restricted driver is that its binary.  the error message i got said something about the system "only reading english make sure you're not trying to open a binary file"

---

### Post by Melcar on 2008-07-06
Is it a plain 9800?  I got a 9800pro on a spare PC running Xubuntu 8.04 with the open source drivers.  Works incredibly well.
I tried the 8.6 fglrx drivers and they work too.  I did install those ones myself thought, because the restricted manager never works for me. Use the [second method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide").
I prefer the open source drivers since they seem more stable and work better in Compiz.  Not as fast, however, and no openGL 2.0 support, so if you're after heavy graphics use don't bother with them.

---

### Post by sonaural on 2008-07-06
it's a 9800pro.  i had the same problem with the restricted drivers and i got the one from the website it just won't seem to open.  i can't quite tell if it's that i'm a real beginner or that there's a prob with the driver/system

---

### Post by Melcar on 2008-07-06
You have to open it from a terminal with root privileges.

```
sudo sh ati*.run
```

The guide I linked to earlier tells you how to install it.

---

### Post by s3a on 2008-07-07
Type:

**sudo apt-get install envyng-gtk**

*THE ABOVE COMMAND WORKS ONLY FOR UBUNTU 8.04 LTS.*

After entering that command you need to launch a graphical application that will _download & install_ the latest proprietary ati driver for your video card. In order to launch that application, click on "_Applications_" and search through the menus as I am not sure where it could be located but it probably is located in "_System Tools_."

---

