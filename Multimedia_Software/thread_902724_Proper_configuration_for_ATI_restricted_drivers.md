---
title: "Proper configuration for ATI restricted drivers??"
date: 2008-08-27
forum: Multimedia Software
---

### Post by Grone1985 on 2008-08-27
Hi!

So my problem is thatI get pixelated video on fullscreen and kinda choppy image (BTW I don't have Compiz enabled when watching videos)... sometimes I get flickering on effects when Compiz enabled... 

I have the restricted drivers enabled but never did this...

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

...as suggested [in this tutorial]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). I never knew about this guide so far and I don't know if that step is needed. Should I do this? Will it fix or make anything better?

Some information...

To the command 'lspci -nn | grep VGA' I get this:

```
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
```

And on /etc/X11/xorg.conf I see this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection
```

So my question is if there's anything I can do to make my card work better?? or does it all look properly configured??

BTW all of this is under Ubuntu Hardy x64.
Thanks in advance!

---

### Post by markbuntu on 2008-08-27
You can use the Catalyst Control Center, amdcccle, to tweak performance. If you do not have it, you shoould get it from the repos. You can also try this thread for tweaks that may or may not help but you will learn some things:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Also, there have been a lot of changes in the driver, if you want the latest 8.8 driver go here, use Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Grone1985 on 2008-08-28
And what about this part? is it necessary?

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```

Thanks!

---

### Post by markbuntu on 2008-08-28
Just follow that guide I gave you a link to very carefully and everything will be just fine. It has never failed me through 5 updates on 3 different installs.

---

