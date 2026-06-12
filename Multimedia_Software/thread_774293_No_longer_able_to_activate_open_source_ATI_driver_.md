---
title: "No longer able to activate open source ATI driver in Hardy"
date: 2008-04-29
forum: Multimedia Software
---

### Post by theuninvitedguest on 2008-04-29
Hi folks!

With the release of Hardy Heron I made up my mind and decided to get finally rid of all the MS crap on my lappy, since (almost) everything worked perfectly fine with Gutsy. So I did, just to become disillusioned after the first boot. Apart from some minor flaws (i.e. the DVD won't open unless I push the tray button and the additional media button at the same time), the biggest issue is now the graphics card (surprise, surprise). My ATI Mobility Radeon 9700 worked like a charm with the open source driver (ati) under Gutsy, but now Xorg always falls back the the VESA driver. fglrx works out of the box, but doesn't give a satisfying performance (I'm not even talking about Compiz, but video playback).

There already exists a similar thread, which might be related to my problem:
[http://ubuntuforums.org/showthread.php?t=766968](http://ubuntuforums.org/showthread.php?t=766968)

lspci gives the following:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

xorg.conf (just the important section):
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
```

Any ideas anyone? Please help my 4-year old Asus M68 to make current Vista-notebooks look old again. :-)

Bye,
Alex

---

### Post by theuninvitedguest on 2008-04-30
*bump*

---

### Post by Padie on 2008-04-30
You could try Envy to reconfigure everything, but ATI is not supported with Envy. In other words, you use it at your own risk....but I'm sure it will work.

Search Synaptic Package Manager for "envy", let it install, and head over to Applications -> System Tools -> Envy, and follow the instructions. They should be easy enough, and when it asks you at the end to configure your Xorg file, let it. Hopefully this will then solve your issues.

---

### Post by MaindotC on 2008-04-30
What does *bump* mean ?

---

### Post by Padie on 2008-04-30
It's basically a way of getting your post to show first in the list again if it's old.....basically making your post more visible in the hope of someone helping you out....

---

### Post by park8b156 on 2008-04-30
I just went to Google typed "envy ATI" the first site on the list should be it.  Go down the page and install the program that matches the Distro version. And make sure you read what you doing before you do it auto is your friend I needed envy with 7.10 but not 8.04 thank you Ubuntu team/ATI
and I am using ATI Radeon Xpress 1100.

---

### Post by theuninvitedguest on 2008-04-30
Thanks for the help so far!
Concerning Envy, I don't intend to install the proprietary driver from ATI, but the open source one. It worked in Feisty and Gutsy, but no longer in Hardy which is a pity, since it was way more stable and faster than fglrx in my case.

Bye,
Alex

---

### Post by CarloMagno on 2008-04-30
Perhaps is a silly suggestion, but have you tried to configure manually your xorg.conf file. When I upgraded my videocard, I remember I had to change the xorg.file for a vesa compatible one and then going back to the proper driver "ati". Are you using "strange" resolutions?
Why does the fglrx driver fail to do properly? In my case the fglrx problems in videoplayback were solved changing the video output mode of the programs (basically gxine, mplayer and mythtv) to opengl (instead of Xv). I think composite is broken for this driver.. but I am not totally sure (and don't know enough about the subject)... well summing up :-) I would try to change the /etc/X11/xorg.conf file changing in the driver section "fglrx" for "ati" if that is what you want, and check if it works. And before that, I suggest you do a backup, just in case (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_pre-ati).

In my laptop (fujitsu-siemens) I have the same video card Ati mobility radeon 9700 but it is still running Gutsy. I remember I had to install the fglrx driver to get opengl working properly. If I upgrade that system I will post you the results.

---

### Post by theuninvitedguest on 2008-05-01
I tried everything you described the day I set up Hardy Heron, but as opposed to Gutsy the open source ATI driver would refuse to start working. Strange...

Thanks anyway,
Alex

---

### Post by Melcar on 2008-05-01
Xorg.conf is configured a bit differently in Hardy.  There are no device identifiers anymore, as well as the device driver not being listed. If you check your xorg.0.log you will notice that those options are still being used, so I guess they removed them from the configuration file for simplicity.  You can still specify options yourself thought; just change your driver parameter to vesa or ati and it should load.  If you reconfigure X (dpkg-reconfigure xserver-xorg) it should revert to original settings, even if the configuration wizard does not let you choose the video driver; when I reconfigure it, it reverts to using the ati driver automatically.

---

### Post by theuninvitedguest on 2008-05-03
@melcar: I already did what you suggested, but this time I had a look at xorg.0.log as well. Obviously the ati driver is loaded (there are no errors listed), but still glxinfo says that Mesa is running. I don't get it...

Alex

---

### Post by CarloMagno on 2008-05-06
I don't know too much about the subject, but I think that if you use the open source "ati" driver, "Mesa" is the open source project for graphics hardware acceleration, so it is OK if the log of the X server states that Direct Rendering (DRI) comes from mesa.

If you were using the proprietary driver (fglrx), glxinfo would tell you that Direct Rendering is provided by ATI.
I had some problems when I upgraded from Gutsy to Hardy. For me the problem was that the driver was not used, in the Restricted Driver Manager it marked the "Ati proprietary driver" as "Enabled" but "Not in Use", I had to manually load it as suggested in post:
[http://ubuntuforums.org/showthread.p...94#post4809394](http://ubuntuforums.org/showthread.p...94#post4809394)

but now, after the kernel and fglrx upgrades (four days ago) the driver loads automatically when starting X and it works properly, although I have to do more testing before being sure everything is OK (specially video playback and Xv)

---

### Post by peakshysteria on 2008-05-06
Solutions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

