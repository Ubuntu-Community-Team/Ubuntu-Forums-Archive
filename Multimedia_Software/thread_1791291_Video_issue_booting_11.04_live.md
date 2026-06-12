---
title: "Video issue booting 11.04 live"
date: 2011-06-26
forum: Multimedia Software
---

### Post by giddensdb on 2011-06-26
I have an older desktop that I want to install xubuntu on.  I have created a bootable USB with Xubuntu 11.04 and when it boots I have no video.  The video hardware in the pc is a built-in S3 VT8375 ProSavage8.  I can access terminal by CTL+ALT+F1 but no xorg video at all.  Suggestions are very welcomed.

---

### Post by Toz on 2011-06-26
There appear to be alot of issues with this card in the newer versions of Ubuntu. References:
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/217004]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/217004")
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-vesa/+bug/320313]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-vesa/+bug/320313")
- [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660301]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660301")

Lets see if you have an xorg.conf file: Ctrl+Alt+F1, login to the terminal, and type:```
ls -l /etc/X11/xorg.conf
```What is the response?

Lets also see if the savage driver is loaded: Type in:```
lsmod | grep -i savage
```Post back the results.

And finally, what make/model of monitor do you have?

It would also be helpful to see the contents of /var/log/Xorg.0.log, but I don't know how you'll be able to do that without an X session.

If you are using the savage driver and you have no xorg.conf file, I'm thinking we can try using a modified version of a working copy of xorg.conf from a few versions back and see if it works. ([https://launchpadlibrarian.net/3085659/xorg.conf]("https://launchpadlibrarian.net/3085659/xorg.conf") &
 [http://aurelianomartins.wordpress.com/2010/12/06/pro-savage-no-ubuntu-10-10/](http://aurelianomartins.wordpress.com/2010/12/06/pro-savage-no-ubuntu-10-10/) & 
[http://ubuntuforums.org/showpost.php?p=9562852&postcount=5]("http://ubuntuforums.org/showpost.php?p=9562852&postcount=5"))

---

### Post by giddensdb on 2011-06-27
I'm booting live. Not sure about editing conf files. I downloaded the ISO and burned it to a USB. Do I just need to give up and go back to an older version?

---

### Post by Toz on 2011-06-27
Not necessarily. What make/model of monitor are you using?

---

### Post by giddensdb on 2011-06-27
Hp pavilion mx50. Quite old but had been working fine.

---

### Post by Toz on 2011-06-27
Maybe you can try this. Boot with the live CD and go to the terminal (Ctrl+Alt+F1) and login. 

Type in:```
sudo nano /etc/X11/xorg.conf
```
and type in the following:
```
Section "Device"
	Identifier	"Configured Video"
        Driver          "savage"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       30-54
        VertRefresh     47-100
        Option          "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video"
EndSection
```

Type **Ctrl+o** (that's o as in Oscar) to save the file, then **Ctrl+x** to exit.

Now restart gdm (the display manager):```
sudo /etc/init.d/gdm restart
```

Do you get a graphical screen now?

---

### Post by giddensdb on 2011-06-27
Ok, I had nothing in xorg.conf so I followed those instructions. It says I don't have gdm. This is xubuntu. Could it be lightdm?

---

### Post by Toz on 2011-06-28
You must have gdm. Xubuntu uses gdm. What is the result of:
```
sudo /etc/init.d/gdm restart
```

---

### Post by giddensdb on 2011-06-28
Itells me that gdm is not found.

---

### Post by Toz on 2011-06-28
ok.Try:
```
sudo service gdm restart
```

Can you post back exactly what you type in and exactly what the reply is? Here is a sample of checking the status of gdm.
> $ sudo service gdm status
gdm start/running, process 816

It makes it easier to diagnose if I can see the exact text that is being entered and the exact responses.

---

### Post by giddensdb on 2011-06-28
Since the box I'm testing on obviously is in no shape to caputre screens, I took a picture of the output with my phone and attached it here.

According to research in the newest *buntu release lightdm is replacing gdm as the default display manager.

---

### Post by Toz on 2011-06-29
Then you must have downloaded the ISO for 11.10, not 11.04. Either way, try a:```
sudo lightdm restart
```

This should be after you created an xorg.conf file. Does it bring up a screen? If not, go to the xorg.conf file again, change the word **savage** to **vesa**, restart lightdm and see if that works.

BTW, 11.10 is still in the alpha phase

---

### Post by giddensdb on 2011-06-29
Tried that with both savage and vesa. Nothing is happening. I have Xubuntu Intepid that works fine from booting live. When I upgrade it to Lucid video breaks. Maybe this hardware is just not supported anymore. Thats a shame since it works in WINDOWS...  Make this thread closed. Maybe I'll play with other distros and see if I can make it work. Thanks for trying.

---

### Post by danieljames on 2011-09-03
I'm having the same problem here trying to get 11.04 to run on a Dell Inspiron 1501.  I can't see if I can load to recovery to get to a terminal command prompt from the install boot list.

I found this thread [http://ubuntuforums.org/showthread.php?t=1490821](http://ubuntuforums.org/showthread.php?t=1490821)
 . . .  "does live usb have recovery mode?"  but it doesn't seem to go anywhere.

I am trying to see if I can find the xorg.conf in the usb from my hdd ubuntu install on my other computer.   But I can't find the file system in the usb.  Perhaps that isn't visible until you boot from it.

---

### Post by Toz on 2011-09-03
@danieljames, have a look at [http://ubuntuforums.org/showthread.php?p=11121392]("http://ubuntuforums.org/showthread.php?p=11121392") for information on how to get natty to boot up on a dell inspiron 1501 using the **nomodeset** kernel parameter.

---

