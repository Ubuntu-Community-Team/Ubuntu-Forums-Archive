---
title: "Just Installed, and my graphics card isn't working..."
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by gdxchris on 2008-01-06
I'm new to this so if this is a noob question, please bare with me.  I have a Nvidia GeForce Go 6150 graphics card.  128MB shared video memory.  Whenever I try to start my computer it says that it needs to be started in screen resolution 800x400 due to a graphics card issue.  How can I resolve this issue?

Help is much appreciated!

---

### Post by Steve1961 on 2008-01-06
Try downloading envy and installing the nvidia driver with that:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by gdxchris on 2008-01-06
okay.  Thank you.  Ill try that.


EDIT: And also, thanks for replying so fast!

---

### Post by gdxchris on 2008-01-06
ok.   I installed it.  Now do I restart my computer?

---

### Post by Steve1961 on 2008-01-06
> **gdxchris said:**
> ok.   I installed it.  Now do I restart my computer?

You first need to run envy and follow these instructions to install the driver:

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

Once you've done that you can reboot

---

### Post by gdxchris on 2008-01-06
The tut that shows me how to set up the repositories is for Ubuntu 6.1 I am running 7.1 and its differernt from what this tut shows.
[http://www.monkeyblog.org/ubuntu/videos/Extra_repositories.gif](http://www.monkeyblog.org/ubuntu/videos/Extra_repositories.gif)


EDIT:  Nevermind.  I got it.  Now for the rest... *sighs*

---

### Post by Steve1961 on 2008-01-06
This guide shows you how to add the extra repos for gutsy

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by gdxchris on 2008-01-06
Okay.  I installed it.  Did what the tut told me to.  Rebooted my computer, and it still only boots in low graphics mode.  Is there perhaps another software driver I can try?

EDIT:  Whoops.  LOL.  Problem solved again.  Just needed to install some missing packets.  Now to see if it works.

---

### Post by Steve1961 on 2008-01-06
OK, open a terminal and type the following:

sudo gedit /etc/X11/xorg.conf

Then find a section that looks something like this:

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"


make sure that the driver sections says "nvidia"

Then look for this section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_60" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Make sure that the resolution you want is inserted in the entries.  Save and close the file and then hit ctrl-alt-backspace to restart x.

If nothing changes post the output of this command here:

cat /etc/X11/xorg.conf

---

### Post by gdxchris on 2008-01-06
oh my god. Thanks sooo much for your help!!!  Its working PERFECTLY now!:)

---

### Post by Steve1961 on 2008-01-06
> **gdxchris said:**
> oh my god. Thanks sooo much for your help!!!  Its working PERFECTLY now!:)

You're welcome  :)

---

