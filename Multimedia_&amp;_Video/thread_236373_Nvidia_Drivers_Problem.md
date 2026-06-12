---
title: "Nvidia Drivers Problem"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by htmlguy716 on 2006-08-14
I'm trying to enable 3D acceleration and OpenGL on my computer for gaming. I installed Nvidia's proprietary driver using method one given [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper"). However, when I tried to restart gdm, I get an "out of range" message on my LCD. I then had to revert to my backup xorg.conf file, with no 3D acceleration. Any ideas on getting this to work?

I have an eVGA GeForce 7600GT video card running a ViewSonic VX2025wm LCD.
My current (working) xorg.conf file is attached as "xorg_good.conf.txt". The file that I get after running "sudo nvidia-xconfig" that should work, but displays the "out of range" error is attached as "xorg_bad.conf.txt".

---

### Post by hopstah on 2006-08-14
i would try adding this line to your xorg.conf file under the 
```
Section "Device"
	Identifier	"NVIDIA GeForce 7600GT"
```
section.  it's there in your 'good' file, but not there in your 'bad' file.  anyways, add this line to that section: ```
	BusID		"PCI:1:0:0"
```

ps.  it's at least a good thing you made a backup of your xorg file, otherwise you'd be in some deep shit

---

### Post by tseliot on 2006-08-14
Maybe you just need to configure the monitor:

Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by htmlguy716 on 2006-08-26
I waited until I had enough time to do some extra fiddling (after Xorg 10.3 messed up my system on Wednesday). Then I upgraded my Xorg to 10.4 and tried the tips above. TsEliot's recomendation to add ```
Option "UseEDID" "False"
``` to the device section of my Xorg.conf file worked! I now have a system that can run Doom 3 just fine with my current graphics card. The only problem is my resolution. With the new drivers, my resolution dropped from 1680x1050_75 to 800x600_60 with no other options. I've tried manually setting different refresh rates on the resolutions, but it doesn't seem to have any effect. I'm really grateful for all the help I've had so far, and I hope one of you knows a way for me to combine great games with great screen size. My Xorg.conf file is attached.
-Daniel

---

### Post by htmlguy716 on 2006-09-10
I'll keep trying to figure this out myself, but I'm really baffled. Apparently this is a rather obscure problem...
If someone could help with this, my LCD will be forever grateful.

---

### Post by tseliot on 2006-09-10
> **htmlguy716 said:**
> I'll keep trying to figure this out myself, but I'm really baffled. Apparently this is a rather obscure problem...
If someone could help with this, my LCD will be forever grateful.

You can try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by htmlguy716 on 2006-10-09
My monitor is finally working. I'm still not entirely sure why it works, but I managed to fix it by swiping the settings off a similar ViewSonic monitor.
Here are the differences between the /etc/X11/xorg.conf file I originally had and the file that works:

The native resolution of the monitor is 1680x1050, but that will only run at 60Hz. All other resolutions can run at variable settings.
```
Section "Screen"
	...
	SubSecton "Display"
		Depth		24
		Modes		"1680x1050_60" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
Make sure to *remove* this line if you have it: ```
Option "UseEDID" "false"
```
Lastly, it is not critical to running the monitor at 1680x1050, but I added DRI with this text in my modules section: ```
Load	"dri"
``` and this section and the very end of the file: ```
Section "DRI"
	Mode	0666
EndSection
```

Attached is an example of the final result in all its splendor.

**EDIT:** I decided to write a howto with instructions on reproducing my results. To view it, go to [HOWTO: ViewSonic 20.1" LCD with nVidia drivers](http://ubuntuforums.org/showthread.php?p=1597740).

---

