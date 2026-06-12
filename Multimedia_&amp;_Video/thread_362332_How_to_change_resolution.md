---
title: "How to change resolution?"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Scooter7 on 2007-02-15
Hi, how can I set my resolution to 1280x1024?   It's currently set to 1024x768.   I can't change it to anything higher in the system settings panel (btw, I'm using KDE), as this resolution isn't set in my xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I tried changing that to:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

But when I rebooted, I just got a black screen with a message saying 'Cannot display this resolution'.   However, I use it in Windows all the time.   1024x768 is just too small for my liking.   Any way to fix this?

Thanks,

Teh DS (Scooter7)

---

### Post by n00bish on 2007-02-15
You may be able to add it to your available resolutions by running the setup for your X server again:

First, it's always a good idea to back up your configuration file before you edit it:
```

sudp cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Next, reconfigure the x server:
```

sudo dpkg-reconfigure xserver-xorg

```
Select 1280x1024 as one of your resolutions you want to use when it asks for video hardware.  You may have to select "No" to "Attempt to Autodetect Video Hardware" - once you run through (most of it is just hitting enter), you should come to a panel where you can select what resolutions to use.

Let me know if that fixes it.

---

### Post by bnuytten on 2007-02-15
You may have to select the specific monitor you are using. If you are using a CRT the refresh rate may be too high for that resolution. If you're using a TFT 60Hz should be adequate. If it is any help, I'm using a TFT on an old ATI All-In-Wonder card (1280x1024):

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

---

### Post by carontis on 2007-02-15
Just follow this link and read all. To me it works fine.

[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=bootup+screen+resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=bootup+screen+resolution")

---

### Post by Scooter7 on 2007-02-15
n00bish, I tried your suggestion, and the resolution doesn't appear in my system settings panel, and I'm not set to that res... the highest I can go, still, is 1024x768.   The strange thing is, the res I want (1280x1024) is in my xorg.conf file now.   And bnuytten, how do I know what kind of monitor I'm using?   I really don't know... also, I tried carontis' suggestion, but I can't find the lines mentioned in the howto.   Might have to do with the fact that my kernel was recently updated...

---

### Post by carontis on 2007-02-15
Well, let me know: what kind of monitor do you have, a CRT or LCD? Behind the monitor you should see / have a label with the name of it. Try to post this here and we'll see what is possible to do. And if you can, please post also the result of your /var/log/Xorg.0.log (it has all information about your pc)

---

### Post by Scooter7 on 2007-02-15
It's an LCD monitor, Dell.   I don't know the name of the monitor, but the model # is E173FPt.

The log's too long to post, so I put it on my webserver: [http://shadowserve.ath.cx/xorg.0.log.txt](http://shadowserve.ath.cx/xorg.0.log.txt)

-EDIT-

Nevermind, I got things working.   There was an option in the X Server reconfiguration utility, something like 'Kernel Rebuffer', or something... I enabled that, and it worked!

Thanks for all your help,

   ~Teh DS (Scooter7)

---

