---
title: "After boot, freeze during frontend &quot;pre-scaling&quot;"
date: 2008-12-19
forum: Mythbuntu
---

### Post by dvanbrunt on 2008-12-19
Well, this is troubling. After a power failure the other day (I have an APC back-ups, but assume a rough shut down) the MythBox won't boot up... here's what happens:
[LIST=1]
[*]Normal System boot
[*]Reach the desktop
[*]Frontend starts to launch
[*]Hangs on "Pre-Scaling Theme images"
[*]Screen starts to get stuck in spots
[*]Eventually ends up with screen full of gray lines, in pattern repeating with diagonal iterations across entire screen
[*]system is unresponsive. Even SSH logins freeze.
[/LIST]

If I am in an SSH session during this process, I can see that backend launches. I can kill frontend right at the start, but the whole system is still really stop-and-start with regard to mouse movement, and the "Xorg" process is consuming nearly 100% of the CPU. 

I tried running "mythfrontend --reset" and it didn't help.

Short of trying to back up my entire library and re-install, is there any way of recovering from this?

---

### Post by 4dognight on 2008-12-19
Your xorg.conf may have got corrupted on the power failure?

I was in a similiar situation once. If it is video related, You could try reverting back to an old basic xorg.conf, or even using the vesa video driver. As for Xorg using 100%, that is usually fixed by adding the  line,

Option "UseEvents" "True"

in your device section of xorg.conf

---

### Post by dvanbrunt on 2008-12-19
Thanks for the reply! 

You said: 
> **4dognight said:**
> Your xorg.conf may have got corrupted on the power failure?

I was in a similiar situation once. If it is video related, You could try reverting back to an old basic xorg.conf, or even using the vesa video driver. As for Xorg using 100%, that is usually fixed by adding the  line,

Option "UseEvents" "True"

in your device section of xorg.conf

I was able to do "cat /etc/X11/xorg.conf" and the file loaded OK, no garbage characters. There was a section with this: 
 
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Option		"DPI"	"100x100"
	Option		"UseEvents"	"1"
	Option		"AddARGBVisuals"	"1"
	Option		"AddARGBGLXVisuals"	"1"
	Option		"NoLogo"	"True"
EndSection

```

... which I assume does what you were talking about.

Unless this is not the config file that's actually used? I found it by typing "locate xorg.conf".
**Interestingly, the machine is otherwise operational, dutifully recording and serving other frontends in the house.** So it seems to be just the "mythfrontend" software on the Master Backend/Frontend that is borked. 

Suggestions? Anyone? Anyone? Bueller? ;)

---

### Post by 4dognight on 2008-12-20
It seems like a video driver problem to me. As you only notice the problem when you start the frontend. Try going into the MCC and turning off the proprietry driver for nvidia and then see if you can get the frontend to work. If it does work, then something iswrong with your video driver setup in the xorg.conf file. Or at least that is my guess.

---

### Post by dvanbrunt on 2008-12-20
> **4dognight said:**
> It seems like a video driver problem to me. As you only notice the problem when you start the frontend. Try going into the MCC and turning off the proprietry driver for nvidia and then see if you can get the frontend to work. If it does work, then something iswrong with your video driver setup in the xorg.conf file. Or at least that is my guess.

Is there a way to do that via the command line via SSH? The desktop is so halted and stalled that it's hard to do anything on that machine through its own desktop. But the command line from remote still works fine.

---

### Post by 4dognight on 2008-12-20
you can try copying /etc/X11/xorg.conf.failsafe to xorg.conf

If you want first copy xorg.conf to something like xorg.conf.save first, as a backup.

reboot or restart X by ctrl-alt-backspace

---

### Post by dvanbrunt on 2008-12-20
> **4dognight said:**
> you can try copying /etc/X11/xorg.conf.failsafe to xorg.conf

If you want first copy xorg.conf to something like xorg.conf.save first, as a backup.

reboot or restart X by ctrl-alt-backspace

Thank you!  I did that via SSH, and the system fired up and the Frontend launched just fine! Video isn't all that smooth, though (not terrible, but clearly not optimal).

Now... how to get all my settings back...  ? I guess I'll have to compare the failsafe with the original, to see what dependencies might be the culprit..

I'll post results and questions as I go, for posterity.

---

### Post by dvanbrunt on 2008-12-21
> **dvanbrunt said:**
> 

I'll post results and questions as I go, for posterity.

Ok, here's the "Failsafe" and the old xorg.conf... I'll only include sections where there are disagreements, bold the lines that are different, and delete things that don't seem related to video:

xorg.conf.failsafe: 
```


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

Now the one that was running when the misbehaving:
```

Section "ServerLayout"
	Identifier	"Default Layout"
[B]  screen "Default Screen" 0 0
[/B]	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

[B]Section "Module"
	Load		"glx"
EndSection[/B]

Section "Monitor"
[B]	Identifier	"Generic Monitor"
	Option		"DPMS"
[/B]EndSection

Section "Device"
	Identifier	"Generic Video Card"
[B]	Driver		"nvidia"
	Option		"DPI"	"100x100"
	Option		"UseEvents"	"1"
	Option		"AddARGBVisuals"	"1"
	Option		"AddARGBGLXVisuals"	"1"
	Option		"NoLogo"	"True"
[/B]EndSection

Section "Screen"
	Identifier	"Default Screen"
[B]	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"	"1920x1080"	"1280x720"	"1024x768"	"720x480"	"800x600"	"640x480"[/B]
	EndSubSection
EndSection

Section "ServerFlags"
	Option "blank time" "0"
	Option "standby time" "0"
	Option "suspend time" "0"
	Option "off time" "0"
EndSection

```

So it seems to reference "glx" and "nvidia"... I'll see if there are corrupted config files for anything with those names attached...

Any other pointers?

---

### Post by dvanbrunt on 2008-12-22
> **dvanbrunt said:**
> 

So it seems to reference "glx" and "nvidia"... I'll see if there are corrupted config files for anything with those names attached...

Any other pointers?

Gaaaa!!

Ok, I booted from the disk with the "xorg.conf" as a copy of "xorg.conf.failsafe", and it booted fine, ran the frontend OK, although in the wrong dimensions for my screen and less than stellar playback of HD content... but it worked sort of, at least.

Then I quit the frontend, and did nothing more than open the settings manager and turn the nvidia driver back on, and reboot.

Same gray diagonal pattern, same freeze of the system. SO THATS THE CULPRIT, though I don't know why it STOPPED working, and how to get to START working again! 

Any advice? Is there better driver? Should I re-install the driver or an older version? (If so, how do I do that?) 

Sorry for the questions. Really aggravating and a real hit on the WAF!

---

### Post by jMon54 on 2008-12-23
I used the program Envy to determine the best nVidia driver to use for my system.  If you do not have it you can easily get it via synaptic software download/install (aka apt-get but with gui).

---

### Post by dvanbrunt on 2008-12-27
> **jMon54 said:**
> I used the program Envy to determine the best nVidia driver to use for my system.  If you do not have it you can easily get it via synaptic software download/install (aka apt-get but with gui).

Thanks for the suggestion. I found and installed Envy, and after rebooting it had the same issue. So I did it again (SSH'd back in on reboot, hurriedly putting the xorg.conf.failsafe in place, then rebooting) then re-ran envy and chose each nvidia driver in turn, stepping backward through versions. Same issue every time. So each time, it seems to re-write the xorg.conf, and no matter the driver version I still get the abberant behavior when Frontend launches. 

Is it possible that the card itself is borked in some way? Note that even without the drivers enabled, I am still watching (successfully, sort of) through the physical connection of that same card.

Running out of ideas here.

---

### Post by dvanbrunt on 2009-01-25
Well, I used the nuclear option... backed up media and database to another machine, then re-installed from scratch (complete with reformat) from a new MythBuntu disk. Guess what? **same problem**. If I use just the open source drivers for video, the UI all looks OK, but playback (esp HD) is occasionally stalling... then every now and then, xorg will shoot to 100% (or more!) and everything freezes.

Just for kicks, I then installed MythDora and even tried KnoppMyth... SAME PROBLEM. If I //do// load the nVidia drivers, I get real problems. Sometimes the frozen pixels as Frontend starts, sometimes just a hashed screen as the driver loads... Right now am using MythDora, which seems to be slightly better... but I'd rather get MythBuntu working again.

Does this mean my video card is bad? Or worse? Any troubleshooting help greatly appreciated (or a recommendation for a good video card, if you think that's it).

---

