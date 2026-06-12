---
title: "Getting 1920 x 1200 resolution"
date: 2011-01-03
forum: Multimedia Software
---

### Post by Tomski_1991 on 2011-01-03
Hi, I'm a newbie when it comes to Ubuntu, in fact I've only been using it for about 6 hours. I'm impressed by what I've seen so far, but I'm having trouble getting a higher screen resolution. 

I have an Acer Aspire 5536 with an ATI Radeon 3200 graphics card. I installed Ubuntu 10.10 with Wubi to dual boot alongside Windows 7. When I go to change the screen resolution, I can not choose a higher one than 1366x768. I would really appreciate it if someone could help me get a resolution of 1920x1200. 

Like I said, I'm a Ubuntu newbie (and I don't have much savvy on graphics cards either) so please go easy on me. Many thanks! :)

---

### Post by tjones00 on 2011-01-03
Ah welcome to the world of Linux! 

The first lesson, Linux gives you much more freedom to manipulate your system than commercial os's but this can be a double edged sword if you are not careful. BEFORE you make any major modification to your system be sure you know how to REVERSE it so you can get back to square one if something goes wrong. This type of mindset will save you a lot of headaches.

To start. What driver are you using? Are you using the default one or did you install the ATI proprietary driver from the web or Ubuntu System > Administration > Additional Drivers?

If you are not sure open a terminal Applications > Accessories > Terminal and type:

```
lsmod
```

If you see ati or radeon that is the open source driver developed by the linux community, if you see fglrx that is the ATI proprietary binary driver released by ATI/AMD.

If you are using the fglrx driver I suggest trying to modify the resolution in ATI Catalyst Control Center that can be found in one of the menus.

Another great thing about Linux is there is a vast amount of documentation online. If you are using the open source driver (ati/radeon in lsmod) I suggest reading the following.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Especially the section.

> **Setting resolution changes in xorg.conf -- resolution lower than expected**

  
****



The above covers how to manipulate resolutions and even how to obtain resolutions found in windows but appear to be missing in linux with the open source driver.

You'll notice Ubuntu 10.10 does not have an xorg.conf file in /etc/X11/ you can generate one to modify by typing the following in a terminal:

```
sudo Xorg --configure 
```

To reverse this change remove the file xorg.conf from /etc/X11/

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Tomski_1991 on 2011-01-04
Hi, thanks for your informative reply! :)

From what I can tell in lsmod, I have the fglrx driver. When I go to the ATI Catalyst Control Center, the maximum resolution available is 1366 x 768.

Do you know how I can select a 1920 x 1200 resolution, or if it is possible to get the open source driver you mentioned (assuming that it's the better driver of the two)?

---

### Post by Tomski_1991 on 2011-01-04
Sorry for the double post, just a quick update.

It appears my graphics card is only capable of having a max resolution of 1366x768 on my laptop, or so it would seem. When I booted up Windows 7 and checked what resolution it was set to, it was also 1366x768. The reason why I thought Ubuntu had a lower res was because it doesn't look as "crisp" as Windows 7. It actually looks as though it's a lower res when in fact it's the same.

Is that just the way Ubuntu is or is there a way to get it looking more "crisp"?

---

### Post by Yellow Pasque on 2011-01-04
I don't like the default font settings either. Look under System -> Preferences -> Appearance and play with the font options.

---

