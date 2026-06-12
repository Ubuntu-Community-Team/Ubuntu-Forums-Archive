---
title: "New installation not going to GUI"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by toshiaki on 2006-08-02
I have an Averatec desktop, where I partitioned the hard drive a couple of times, installed Windows XP on the first partition, then installed Ubuntu on the next partition over, and then added a small swap partition, and a very large partition for files both OSes can access. The Ubuntu installer automatically set up GRUB so I can choose which system to run at startup, saving me the trouble of mucking with /etc/grub.conf. I'm rather new to the Linux experience, so that's actually very good for me.

However, when I ran Ubuntu on this machine for the first time, I only got a command line in a text environment; I didn't recognize any attempt by the OS to launch GNOME. A re-install didn't really help. I'm guessing, tyro that I am, that it's because the installer couldn't find a driver for the graphics card (VIA/S3G UniChrome Pro IGP). I looked around on Google and found some smug guy with a tutorial for SuSE that, according to him, assumes an advanced knowledge of Linux. Other people with problems like my own asked him questions and got responses that boiled down to "read my guide more closely."

So, would you think installing a driver the most likely solution?  Are there any easy-to-follow guides on getting one and installing it?

---

### Post by Ziox on 2006-08-02
> **toshiaki said:**
> I have an Averatec desktop, where I partitioned the hard drive a couple of times, installed Windows XP on the first partition, then installed Ubuntu on the next partition over, and then added a small swap partition, and a very large partition for files both OSes can access. The Ubuntu installer automatically set up GRUB so I can choose which system to run at startup, saving me the trouble of mucking with /etc/grub.conf. I'm rather new to the Linux experience, so that's actually very good for me.
 
However, when I ran Ubuntu on this machine for the first time, I only got a command line in a text environment; I didn't recognize any attempt by the OS to launch GNOME. A re-install didn't really help. I'm guessing, tyro that I am, that it's because the installer couldn't find a driver for the graphics card (VIA/S3G UniChrome Pro IGP). I looked around on Google and found some smug guy with a tutorial for SuSE that, according to him, assumes an advanced knowledge of Linux. Other people with problems like my own asked him questions and got responses that boiled down to "read my guide more closely."
 
So, would you think installing a driver the most likely solution? Are there any easy-to-follow guides on getting one and installing it?
 
Since you are saying that there is no GUI, then i'm assuming that you can type in the command line, am I correct on that?
 
If you can type in the command line, then try this command:
 
sudo dpkg-reconfigure xserver-xorg
 
that'll reset X (graphics) system.
 
P.S. What cd did you use to install ubuntu? (Hopefully it isn't the server cd) :)

---

### Post by tseliot on 2006-08-02
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine

If it doesn't work you can try this:
```
apt-get install xserver-xorg-driver-via
```

```
dpkg-reconfigure xserver-xorg
```

and set the driver to "via".

If even that doesn't work set the driver to "vga"

---

### Post by toshiaki on 2006-08-02
I tried the commands listed by the previous user, and based on how the computer responded to them, and checking the documentation, I have determined that the version of Ubuntu I'm using is too damned old (2.6.8). I'm going to get the new version, then try those commands again and see if I have better luck this time.

---

### Post by bingwalker on 2006-08-08
Has anyone been able to get 1280x768 resolution with this graphics card on their laptop?  (VIA/S3G UniChrome Pro IGP)  If so, how?

---

### Post by tseliot on 2006-08-08
> **bingwalker said:**
> Has anyone been able to get 1280x768 resolution with this graphics card on their laptop?  (VIA/S3G UniChrome Pro IGP)  If so, how?

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

