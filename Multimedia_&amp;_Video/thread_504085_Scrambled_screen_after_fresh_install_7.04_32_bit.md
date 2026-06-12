---
title: "Scrambled screen after fresh install 7.04 32 bit"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by agibby5 on 2007-07-18
I had to re-install my Ubuntu after botching up trying to rebuild the kernel.  Anyway, after re-installing and rebooting, I get a scrambled screen (red, orange and black) after the UBUNTU loading screen.  I tried doing what others suggested by doing the Ctl + Alt + F1, etc, and Ctl + Alt + Backspace.  When I do any of that, all that happens is more scrambling usually in a white and black display.  This is my second attempt at a re-install of Ubuntu and I'm getting the same results.  Any ideas?

BTW: I have a 7600GTOC Pci-e card.

---

### Post by agibby5 on 2007-07-18
Ok, I did Ctl + Alt + F1 right after clicking which kernel I wanted to boot and I got to the terminal login prompt. At that point I reconfigured xserver.  Then I tried the Envy script: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then I got the black screen.  I then disabled the driver in my xorg.conf file (replaced nvidia with vesa).  When I rebooted the computer, it booted properly.  Once I logged in, I got a notification about using a Restricted Driver.  I went into that menu item and noticed that the Nvidia driver was in use.  Is there something I'm missing with my xorg.conf file?

EDIT: When I tried to run the Desktop Effects, I was informed that my Nvidia driver wasn't enabled and would I like to enable it.  I said yes, and rebooted.  Black screen again. 

Then I edited my xorg.conf file again to use the vesa driver. And this time there were other options, which I also commented out, figuring that they had to do specifically with the nvidia driver.  Here's my xorg.conf file device section: 

```

Section "Device"
	Identifier	"BFG 7600GTOC"
	Driver		"vesa" #"nvidia"
	#Option		"AddARGBVisuals"	"True"
	#Option		"AddARGBGLXVisuals"	"True"
	#Option		"NoLogo"	"True"
EndSection
```

---

### Post by agibby5 on 2007-07-20
I guess this is a persistant problem not yet easily repaired?

---

### Post by tfarinella on 2007-07-20
no its just i find these forums to be picky on who they reply to and are very biest on who they concider a noob

---

### Post by agibby5 on 2007-07-21
I feel like I did some due diligance.  I'm not asking for an answer.  I just need some help in the right direction.  I've already tried the Envy script, I tried editing my xorg.conf file myself.  I even posted some of my xorg.conf file for others to view.  Seems weird that I've not gotten any help on this.  I thought I was going to get a few replies by now.

---

