---
title: "XGL Problem"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by carbra on 2007-08-24
Can anyone help and point me in the right direction. I've been trying to get Compiz Fusion onto my Acer 5100 laptop, but when I change the to Gnome XGL the screen becomes unreadable, with lots of lines where the icons should be. I'm a real newby at this, so any help would be gracefully be accepted.

Computer is as I said an Acer 5100 laptop, with AMD 64 and a radion ATI X1100.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-25
Hi, try to change your "/etc/X11/xorg.conf" file (in terminal type, "sudo gedit /etc/X11/xorg.conf")

Find this line:
```

DefaultDepth   16

```

Change to 
```

DefaultDepth   24

```

Save the file and then restart X (pressing Ctrl-Alt-Backspace at once).

Does it help?
If not, i'm sorry, i don't know any other alternatives (i also a newbie).

But, you could see this [thread]("http://ubuntuforums.org/showthread.php?t=272104"), specially link to [Compiz Fusion for ATI cards + XGL in Feisty]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by carbra on 2007-08-25
Cheers for that, I first had a look at your suggestion and found that the "default depth"  is 24, all the settings are as below. Not too sure if each of the displays should be set to 24.

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by Milk &amp; Toast &amp; Honey on 2007-08-25
It seems that the problem's not there, I was had the same problem when the DefaultDepth is set to 16, so it just my raw prediction.

[QUOTE="carbra"]
Not too sure if each of the displays should be set to 24.
[/QUOTE]
Don't do that :) .

I suggest you see the link I provide, since I cannot help you further than this (i'm really sorry, i'm a newbie too).
Please see or follow this howto : "[Compiz Fusion for ATI cards + XGL in Feisty]("http://ubuntuforums.org/showthread.php?t=488385")".

---

### Post by soxs on 2007-08-25
Do you have the compostie extension enabled? if yes.. disable and try again.

---

