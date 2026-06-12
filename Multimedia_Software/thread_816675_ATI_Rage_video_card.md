---
title: "ATI Rage video card"
date: 2008-06-02
forum: Multimedia Software
---

### Post by BryanG3301 on 2008-06-02
Hey everyone, I've been on Linux Ubuntu for a total of about 4 weeks now and I've loved it except for the fact everytime I reboot I get a new screen resolution. I've had two friends try to assist me with getting it configured but to no luck. We believe the resolution issue is because Ubuntu isn't "reading" the video card for some reason, possibly the monitor as well. My Monitor is a Gateway EV910 CRT and below I'll post the sudo lshw -C video from my video card. If you need anything else about it, please let me know and I'll post away.

Thanks in advance for your assistance.

Bryan

bryan@BryanG3301:~$ sudo lshw -C video
[sudo] password for bryan: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Rage 128 Pro Ultra TF
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=32 mingnt=8

---

### Post by Prospero2006 on 2008-06-02
Are you familair with /etc/X11/xorg.conf 

?

---

### Post by BryanG3301 on 2008-06-02
Yeah one of my Linux friends informed me of it and this is the reply:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by Dr.Ninethousand on 2008-06-07
I don't know what's going on with Hardy and xorg, but I keep seeing 'blank' xorg.conf files like that..  I had to generate a useful xorg.conf in Debian and copy it over..

---

### Post by BryanG3301 on 2008-06-08
hmmmmmm and how would that be done exactly???? I apologize for my noob-ness at this.

---

### Post by Dr.Ninethousand on 2008-06-08
well I don't recommend it, but what I did was actually install Debian and make a copy of it's xorg.conf file, then re-install Ubuntu again and use that file..  this was on a 500MHz Celeron that's over a decade old..  I'm sure you can find a better solution..


I have read that Gutsy didn't have this problem, so you might try booting into a live CD of Ubuntu 7.10 aka Gutsy, and saving the xorg.conf from there to a floppy or usb drive.  then boot back into Hardy and replace xorg.conf with the one you saved from Gutsy..  I tried this solution myself, and I'm sure it would have worked, but the computer I was working on wouldn't boot 7.10..

---

### Post by BryanG3301 on 2008-06-09
I have a version of Knoppix from a book I bought a lil while back, would that work you think? (my burner doesn't work right else I would just get 7.10 and use it as you suggested)

---

### Post by Dr.Ninethousand on 2008-06-10
unfortunately that didn't work for me when I tried it, but don't let that stop you..  at least boot it up and take a look at the xorg.conf, maybe if you spend more time on that than I did you'll get it going..  :p


it will at least tell you some things about your system that may prove useful in solving your problem..

---

### Post by sim-value on 2008-06-10
just in the section screen:
SubSection "Display"
		Viewport	0	0
		Depth	24
                Resolution 1024x768 or whatever you resolution is
EndSubSection or endsection i forgot ...

---

### Post by BryanG3301 on 2008-06-10
Yeah I would just change those specific lines in the file but I wanna make sure I don't do something to totally muck it up lol. Which is why I wanna get get exact lines for that file lol

---

### Post by Dr.Ninethousand on 2008-06-13
I noticed there have been a few automatic updates to xorg components in the last few days..

maybe now you can try something like "sudo dpkg-reconfigure xserver-xorg" and have it actually work?.

---

### Post by BryanG3301 on 2008-06-15
When I did the "sudo dpkg-reconfigure xserver-xorg" all it "reconfigured was the keyboard because that was all that was on there I'm guessing lol, anyways, I now have an NVidia e-GeForce 6200 PCI card and I can only use one of the video out plugs due to the way the back of my computer is configured (I can't win for losing) and I can't get Ubuntu to recognize that card either, am I doing something wrong or does this just not like me? ](*,)

---

