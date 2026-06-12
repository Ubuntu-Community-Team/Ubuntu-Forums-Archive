---
title: "Dual Monitor Setup"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Miki01 on 2006-09-03
Hey everyone. I wanted to ask, what preparations would I need to do to do a dual monitor setup? Would I just need to plug in the other monitor to the other port on my video card and Ubuntu will automatically recognize it? Because at the moment, my resolution is 1280x1024. Would it automatically add another option for a wider resolution for the second monitor?

I will be using 17" LG Flatron L1718S monitors.

---

### Post by Ziox on 2006-09-03
I hate to say this, but please search through the forums before posting a new thread. Because there is a stickied thread that is specifically written for enabling dual monitors.

But for the quick link, just check my signature...

---

### Post by Miki01 on 2006-09-03
Well I was going through your tut on the TwinView thing and when I got to the point of "Add these lines to your 'Devices' section" I got lost. Where is my 'Devices' section? I looked at the xorg.conf file in gedit, but I don't understand...

Is it this section:

> Section "Device"
	Identifier	"XFX GeForce 7300 GS"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection

---

### Post by Ziox on 2006-09-03
yes, sorry about that....i'll change it...

---

### Post by Miki01 on 2006-09-04
Okay, thanks. Another thing. After I finished all the steps in the nvidia TwinView, I looked at System > Preferences > Screen res and my 800x600 doesn't show up anymore. Was that supposed to happen? And will the wider resolutions show up once my second monitor is detected?

---

### Post by Ziox on 2006-09-04
> **Miki01 said:**
> Okay, thanks. Another thing. After I finished all the steps in the nvidia TwinView, I looked at System > Preferences > Screen res and my 800x600 doesn't show up anymore. Was that supposed to happen? And will the wider resolutions show up once my second monitor is detected?

Yeah it is suppose to happen.  I don't think xorg is smart enough to calculate the total dimentions of two screens, so there shouldn't be anything displayed...

---

### Post by Miki01 on 2006-09-04
Okay, I can't boot my computer anymore... It keeps bringing me to a page saying that it may have been configured improperly and it shows a yes or no option on viewing it, but I cannot choose yes or no because the Ubuntu login appears and makes me log in. After that, its just a black terminal shown. When I type "gksudo gedit xorg.conf" it said "cannot open display". I do not know what to do. I am typing this through my Kubuntu liveCD. What do you suggest I do? What do I type in to restore it to how it was before I went through your tutorial? School is back as of tomorrow, and I need a computer to use... When I go to the recovery mode in GRUB, it just gives me a black terminal display with root access... Your help is greatly appreciated.

---

### Post by Ziox on 2006-09-04
you can't use GUI applications in a terminal, because X hasn't started yet.  The easiest tool to use is called nano, so boot into recovery mode, then to edit xorg.conf:

> sudo nano /etc/X11/xorg.conf

and see what you can change to.  also, if you don't know how to switch it back, make a backup of that file:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

then do:

> sudo dpkg-reconfigure xserver-xorg

then reboot:

> sudo reboot

I have some doubt that xorg caused the "crash" so post your xorg.conf after you are able to boot.  I'm interested...

---

### Post by Miki01 on 2006-09-04
Unfortunately, I did just that... And its as if nothing happened... It still gives me a screen saying that it still isn't setup correctly...

---

### Post by Ziox on 2006-09-04
are you sure that your computer isn't impacted by the "not-so-recent" xserver-xorg update?

---

### Post by Miki01 on 2006-09-05
I gave it another shot and it finally worked (4th time is a charm for me ;) There was one option, it said if that it continued to give problems, select no, I chose no for that one on the 4th attempt, and it worked :)

---

