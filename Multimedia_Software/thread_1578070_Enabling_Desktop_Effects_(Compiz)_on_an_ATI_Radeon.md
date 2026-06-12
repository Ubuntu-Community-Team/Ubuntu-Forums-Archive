---
title: "Enabling Desktop Effects (Compiz) on an ATI Radeon 7200"
date: 2010-09-19
forum: Multimedia Software
---

### Post by sweBers on 2010-09-19
I finally did it.  After spending a lot of time researching and testing, I finally enabled Desktop Effects.

I'm posting this for all of the other users out there who have posted threads over the past decade regarding this issue but either never resolved the issue or never reported back that they had done so.

To begin, I am running Ubuntu 10.04, and have 2GB of memory on a Celeron clocked at 2.40GHz.  I am not using swap, although I may enable it again soon.

My issue began when I had first installed 7.10 and was experiencing video problems directly after the install.  Being a noob to Linux, and after discussing the matter with a friend of mine, I was under the impression that ATI drivers were not readily available that would provide the access I wanted.  At that time I switched to a newer Nvidia card.

Recently, I had cannibalized the Nvidia card and returned the ATI card to the Linux machine.  I felt more ready to tackle the driver issue after reading about FGLRX and the Radeon drivers, and realized that FGLRX will not support the ATI Radeon 7200.  I had poked around, and came across this page that details how to remove FGLRX and install Radeon:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Following the instructions of the page, I had believed that FGLRX was uninstalled and tried to install the Radeon driver.  The graphics did not work right and I was experiencing some strange bugs.  At one point, I had tried to follow the directions on the community help page and ended up locking up my X server (only key combo that functioned was ctrl-alt-del).

I knew that my xorg.conf has been edited many times, and I wanted to see if it was possible to come across a clean version.  At that point, I booted from my old 7.10 disk and tried to enable desktop effects (just to see if it was possible).  Surprised at the way that they were enabled and ran, I copied the temporary xorg.conf to my desktop and restored my backup.  (**HEAR THAT KIDS, ALWAYS MAKE A BACKUP COPY OF YOUR xorg.conf BEFORE YOU MAKE _ANY_ CHANGES!**)

After comparing the configuration that had been automatically provided and my cobbled-together disaster, I copied some of the values into my xorg.conf and came up with the following settings.  Please note that I'm using a 21" monitor, and you will want to look up your own display settings before setting them.  Forcing bad settings is reported to break monitors.

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R100 QD [Radeon 7200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Frustrated that my system still would not display desktop effects, I Googled more and came across Compiz-Check, that should check to see if your system is set up properly to run desktop effects:

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

After running the application, I learned that my system was not attempting to render any graphics.  Referencing the open source ATI driver documentation and Googling further, I ran across documentation describing how to install the binary ATI driver (FLGLRX).

After running a check to see whether FGLRX was installed properly and getting a segmentation fault (the first response or clue that it was installed in the first place), I realized that FGLRX had to be still installed, and tried this:

sudo apt-get remove fglrx

Amazingly, fglrx was still installed to that point and was finally removed.  At that point, I restarted and was able to enable desktop effects.

---

