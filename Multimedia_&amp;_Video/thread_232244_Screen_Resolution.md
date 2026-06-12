---
title: "Screen Resolution"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by 1Paul on 2006-08-08
I have just installed a new driver for my ATI RADEON 9500 Pro: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Now I have the problem that I have almost none screen-res to choose from. Is there any way to get more? Or do I have to look for å new driver? where?

thanks

---

### Post by zxee on 2006-08-08
What screen resolutions do you have in /etc/X11/xorg.conf?

---

### Post by 1Paul on 2006-08-08
Im a bit new, so i didnt find out.

paul@paul-desktop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
paul@paul-desktop:~$ sudo /etc/X11/xorg.conf
Password:
sudo: /etc/X11/xorg.conf: command not found

But in my system/preferences/.. I have 1600-1200(to small) 1280-1024(wrong format) 1152-864(to big)

Before I installed the driver I had 1400-1050 and 1280-960.

---

### Post by zxee on 2006-08-08
To look at the file I mentioned you can just open Places>computer>filesystem and keep browsing your install i.e. /etc/X11/xorg.conf
Or from a terminal do> less /etc/X11/xorg.conf
What's called out in your xorg.conf is going to be what the xserver uses.

---

### Post by tseliot on 2006-08-08
> **1Paul said:**
> I have just installed a new driver for my ATI RADEON 9500 Pro: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Now I have the problem that I have almost none screen-res to choose from. Is there any way to get more? Or do I have to look for å new driver? where?

thanks

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by thenonoman on 2006-08-08
I am a newbie who had a similar problem.  The only option I was given for refresh rate was 85Hz, which was too high for my monitor.  I had no luck modifying the xorg file, don't know if I did it right or not, but it didn't work.  What worked for me is loading KDE and using the graphical setup there.  I was able to choose from lists of resolution and refresh rate, so I could just match what my monitor supports.  In the xorg setup, my video card was not an option to choose from, but in KDE, it was, so I was able to give the right card description and choose the right driver.  I realize that it required loading a whole lot of software to solve a simple problem, but it worked.  No more screen resolution errors on the login page either.

--

Silence is golden, but duct tape is silver.

---

### Post by 1Paul on 2006-08-20
I did this guide:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

When I was done(and added a new screen res), my xorg.conf had been modified a bit and graphic like screen savers lagged a bit. So I did the ATI driver install once more. Now the graphic is good, and the new screen resolution is in my xorg.conf. But I cant choose that resolution from the list in: System>Preferences>Screen Resolution>..

I might also add that I didnt have any more resolutions with my windows driver. So maybe it wont ever work. Not with this driver anyway?

thanks

---

