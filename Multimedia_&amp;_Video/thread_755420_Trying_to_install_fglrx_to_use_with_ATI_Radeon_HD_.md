---
title: "Trying to install fglrx to use with ATI Radeon HD 2600 XT, please help!"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by invertedtwisted on 2008-04-14
Hi everyone,

I've played around with Ubuntu a little before, but never really got 'into' it because I'd always try and properly set up my graphics card to no success, then just get bored and go back to windows. But, I've been playing around with Ubuntu all day, completely ignoring the fact that I'm stuck with basic graphics, and damn it, I really like using Ubuntu. However, it's just far to irritating to me to keep using Ubuntu just knowing that it *could* work so much nicer, if I could just properly install my graphics card. (an ATI Radeon HD 2600 XT)

So, I've just been having a proper serious attempt to install the fglrx driver. I've been following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

I've got up to the point of configuring the driver. My problem is that if I reboot after changing xorg.conf to use the fglrx driver, at reboot my monitor simply doesn't respond. It's hard to explain, but, once I've enabled fglrx and rebooted, heres what happens:

Green light on my monitor as GRUB lets me choose to install Ubuntu.
I see the 'Ubuntu' logo and the loading bar underneath it.
THEN me monitor goes from a green light to an orange light (which is what it does I think when it isn't receiving signal or when it is in standby mode) and the screen goes black, and remains black.

If I just hit control+alt+backspace rather than restart, the monitor just dies instantly - that is, it immediately changes to an orange light and black screen.

I can get Ubuntu to start up again by going into the recovery start up, reconfiguring X and then resuming a normal boot. After doing so, xorg.conf looks like it did to start with, before I made the changes described by the tutorial.

Sorry, I'm rambling a bit. Simply, my problem is that after enabling fglrx and rebooting, my monitor just shows a black screen. I would be really grateful if anyone could help me get this working properly, or give any advice at all.

Thank you so much! I know it is silly, but I really can't switch to Ubuntu unless I've got this working... it's just a nagging feeling all the time while I'm using it. Thanks very much!

---

### Post by phidia on 2008-04-14
> Green light on my monitor as GRUB lets me choose to install Ubuntu.

That line above is a little confusing. Are you working in a livecd an expecting changes to be there after a reboot? Changes done in the livecd will not be saved. The livecd is for exploring ubuntu prior to installation.

If you are in a hard drive install it's hard to say why the driver doesn't work after a reboot. When you get the black screen you can press the Alt+Ctrl+F1 keys at the same time and hopefully be able to look at the /etc/X11/xorg.conf file to determine what driver you have listed there. The section you want to look at for the driver looks something like this:
> Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:0:18:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"

This is my xorg.conf though and since my computer uses a different card your xorg.conf will show a different driver..

 From the commandline that Alt+Ctrl+F1 keystrokes should put you into you can also type startx and press enter. What error message do you get?

---

### Post by invertedtwisted on 2008-04-15
Hi, thanks for your response.

I'm running from an install, not the live CD. Sorry, I can see how that sentence was confusing. I think GRUB is the name of the thing that lets me choose to start Ubuntu or Windows? What I mean is that THAT (GRUB?) loads fine, and the power light on my monitor is green. It stays green and my monitor continues working whilst the Ubuntu logo and loading bar shows. After some time though, the power light on my monitor goes orange and the monitor goes dead, just a black screen.

I tried your advice of pressing control + alt + F! at this point. I seem to have to press this combination a couple of times to get a response, but when I do get a response, my monitor comes back on. Instead of showing my xorg.conf, instead I see just a garbled mess of black and white patterns. If I try to type anything, the garbled mess is slightly altered in the spot presumably where I'm typing. It's kind of hard to explain, if this is all useless to you I'll try and shoot a video later.

I just tried using 'envy' to install the driver, found exactly the same - at reboot, screen goes black.

Thanks very much!

---

### Post by phidia on 2008-04-15
My best idea on this is for you to use a livecd that would allow you to edit your xorg.conf. Conversely you could try booting into your system in failsafe mode but since you are having the problem you described with your display I'm not sure if that will work. 
You say you tried to use ALt+Ctrl+F1 keys (you can try all the rest of the Function keys too (F2, F3, F4.....) with the Alt+Ctrl keys. I don't know why you can't get to a tty (the commandline) using those keys.
You might try [system rescue cd]("http://www.sysresccd.org/Main_Page") or a good livecd like [dyne:bolic]("http://dynebolic.org/"). If you can get either of those running on your computer you can then cd into /etc/X11 and open your xorg.conf with a text editor; find the driver section in there (see the example I listed in previous post) and change the driver to vesa. That should get you a working desktop.

---

### Post by invertedtwisted on 2008-04-15
I can easily get xorg.conf to go back to how it was by starting in recovery mode and choosing "reconfigure X" then choosing to resume a normal boot. I'd just really like to get fglrx running properly instead.

Thanks very much.

---

### Post by phidia on 2008-04-15
Sorry for the miscommunications. Have you tried the howto [here]("http://ubuntuforums.org/showthread.php?t=515573")?

---

### Post by invertedtwisted on 2008-04-15
No, I haven't tried that guide yet. I'll follow that and let you know how it goes.

---

### Post by invertedtwisted on 2008-04-15
Ok, I actually ended up running through THIS guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
As I am running Hardy - sorry, I probably should have said that.

I followed method 2 (I've now forgotten what the problem with method 1 was). I've followed all the way through a few times, so I'm pretty certain I did everything right. But after my reboot and running fglrxinfo, this is what I get:

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

I've tried a few times and got the same result every time. For one variation, I tried adding 
```

Section "Extensions"
    Option "Composite" "Disable"
EndSection
```
to my xorg.conf, but still had the same results.

The actual noticeable results after doing this are that my desktop loads in full 1280x1024 resolution with full colour, but whatever my graphics driver is doing at the moment, it's pretty terrible. I don't know what the technical name is, but it's horribly slow to redraw a window if I drag it around, or try to scroll up and down a page in firefox (do you call it draw rate? That's just a guess, really).

I can solve this problem, like my previous one, by rebooting into recovery mode, choosing "reconfigure X" then choosing to resume a normal boot.

Any suggestions now?

Thanks again for your help.

---

### Post by aphroneo on 2008-04-15
I've looked at your xorg log [http://paste.ubuntu-nl.org/63365/](http://paste.ubuntu-nl.org/63365/) .  First thing I see is you are not getting the right kernel module (or no kernel module) installed. You could try sudo depmod -a && sudo modprobe fglrx , and then restart X to see if that helps.

---

### Post by phidia on 2008-04-16
Because this is hardy and still a beta you could also check the [development forum]("http://ubuntuforums.org/forumdisplay.php?f=305").

---

### Post by wallsensus on 2008-05-22
whoops wrong thread.

---

