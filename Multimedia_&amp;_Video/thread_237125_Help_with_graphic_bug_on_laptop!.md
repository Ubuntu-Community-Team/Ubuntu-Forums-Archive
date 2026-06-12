---
title: "Help with graphic bug on laptop!"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by dragze on 2006-08-15
Hi all,
Ok i have installed Ubuntu on a friends laptop and all is well except for a little glitch in the graphics :o  

All is displayed correctly accept for action buttons in program windows which display dots through the button untill you hover the cursor over the button and then all is displayed correctly! :confused: see below:
[IMG]http://dragze64.net/temp/graphic%20bug.png[/IMG]

Everything else is displayed fine, movies, images etc. it is just the action buttons in programs.

Here is my Xorg config file:

> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

To see full xorg config file follow this link: [Full xorg.conf]("http://dragze64.net/temp/xorg.conf")

I am using the ati driver that default installed with ubuntu install, i did try to install the fglrx driver but xserver failed to start afterwards. I didnt bother trying to tweak with the fglrx driver to try to get it to work cause the ati driver is working fine except this minor glitch wid the buttons.

So if anyone has a soloution or any suggestions on how to solve this glitch with the buttons plz let me know!! :) 

Could someone also give me a link to a good source of reference for editing  your xorg.conf cause i want to make some adjustments with the mouse etc.

Thanks in advance!

dragze

---

### Post by dragze on 2006-08-17
Still got this problem! Nobody got any ideas???? :confused: 

Pretty please help me!! :D 

Need anymore info just ask.

---

### Post by onocrotalus on 2006-08-18
I installed Ubuntu 6.06 on my laptop yesterday - my first deviation from windows - and all went well, except that I have the graphical glitch described at the start of this thread. Is there any advice about how to fix it?  Thanks.

---

### Post by Ziox on 2006-08-18
> **onocrotalus said:**
> I installed Ubuntu 6.06 on my laptop yesterday - my first deviation from windows - and all went well, except that I have the graphical glitch described at the start of this thread. Is there any advice about how to fix it?  Thanks.

It appears to be a bug in dapper, or X, or just the Human Theme.  I installed Dapper close to a dozen times since it came out, and everytime it is the same problem, however, switching to other themes, I noticed that there is no glitch.  So for now, swich to another theme.  It should be fixed in the next release (hopefully)

---

### Post by Ziox on 2006-08-18
> **dragze said:**
> Hi all,
Ok i have installed Ubuntu on a friends laptop and all is well except for a little glitch in the graphics :o  

All is displayed correctly accept for action buttons in program windows which display dots through the button untill you hover the cursor over the button and then all is displayed correctly! :confused: see below:
[IMG]http://dragze64.net/temp/graphic%20bug.png[/IMG]

Everything else is displayed fine, movies, images etc. it is just the action buttons in programs.

Here is my Xorg config file:



To see full xorg config file follow this link: [Full xorg.conf]("http://dragze64.net/temp/xorg.conf")

I am using the ati driver that default installed with ubuntu install, i did try to install the fglrx driver but xserver failed to start afterwards. I didnt bother trying to tweak with the fglrx driver to try to get it to work cause the ati driver is working fine except this minor glitch wid the buttons.

So if anyone has a soloution or any suggestions on how to solve this glitch with the buttons plz let me know!! :) 

Could someone also give me a link to a good source of reference for editing  your xorg.conf cause i want to make some adjustments with the mouse etc.

Thanks in advance!

dragze

It seems like I have the same graphic card as your friend..."ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)0"

maybe it is graphic card specific...

what graphic card do you have, onocrotalus?

---

### Post by onocrotalus on 2006-08-18
I'm not at that computer so I can't give full details for certain, but I know it's an ATI Radeon of some sort. The machine is a laptop, Sony NV109M; shipping specs say ATI Mobility Radeon 7500, and I haven't changed it.

---

### Post by Ziox on 2006-08-18
> **onocrotalus said:**
> I'm not at that computer so I can't give full details for certain, but I know it's an ATI Radeon of some sort. The machine is a laptop, Sony NV109M; shipping specs say ATI Mobility Radeon 7500, and I haven't changed it.

anyone else have a sony? cuz I do...and it's not so great...Sony Vaio PCG-FRV31

---

### Post by Anthem on 2006-08-27
I have this bug as well on the Human theme.

Like everyone else, my graphics card is an ATI 320m IGP.

My laptop is a Compaq Presario 2103US.

---

### Post by Ziox on 2006-08-27
I can comfirm that this "bug" also appears for Xubuntu w/ Human Theme+ so perhaps it relates to the graphic cards we use...

---

### Post by Anthem on 2006-08-29
I've filed a bug in Malone...

[https://launchpad.net/distros/ubuntu/+bug/58124](https://launchpad.net/distros/ubuntu/+bug/58124)

If you're experiencing this problem, please leave a comment on the bug report!

---

### Post by dragze on 2006-08-31
Apologies for the late reply!

Cheers everyone for all your help im glad to see im not the only person with this bug and that the bug has been reported. Lets hope they get this bug fixed soon cause i like the human theme! :D

Cheers all,
Dragze

---

