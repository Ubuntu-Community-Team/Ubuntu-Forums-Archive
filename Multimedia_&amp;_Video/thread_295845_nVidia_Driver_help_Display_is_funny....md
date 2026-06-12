---
title: "nVidia Driver help? Display is funny..."
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by DanSchnell on 2006-11-08
> I've been -attempting- to try the liveCD for Ubuntu 6.10 and 6.06 for the last month now and I can't get anything to work.

This is what happens when I try to boot ubuntu after the first option screen: 
[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0151.jpg[/IMG]

Solutions I've tried:

Sudo dpkg-reconfigure xserver-xorg
-Setting driver to vesa
-setting monitor at medium setting
sudo /etc/init.d/gdm restart
-NOTE: Starting GNOME Display Manager...[FAIL] (WHY?!)
Sudo apt-get install nvidia-glx
Sudo nvidia-xconfig

Editing xorg manually doesn't work either...

Can somebody please help me!?

Graphics card= 2 of eVGA nVidia GeForce 6800GS CO running SLI
AMD 64 ASUS A8N-SLI Prem mottherboard

I've posted this in the beginner section, but it hasn't really been noticed.  

I've tried the first 2 methods of Latest_nVidia_Edgy too...so >.<

Help?

---

### Post by Cynical on 2006-11-08
What monitor do you have?

---

### Post by DanSchnell on 2006-11-08
19" Samsung...

Res: 1280*1024 with 60Hz

---

### Post by DanSchnell on 2006-11-09
bump

---

### Post by tseliot on 2006-11-09
Try booting the livecd in Safe Mode

OR

If you tried the livecd and you were not able to install Ubuntu even when using the Safe Mode:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

