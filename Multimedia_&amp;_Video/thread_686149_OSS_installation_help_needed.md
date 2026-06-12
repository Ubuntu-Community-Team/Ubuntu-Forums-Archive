---
title: "OSS installation help needed"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by FirewolfX-7 on 2008-02-02
Hi I need good help here.  Yes I am new to Ubuntu.  I use Gutsy Gibbon and I need help installing a sound card.  I followed all the instructions followed here: [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60) but I got a message that said something else was using the sound device or something and couldn't complete soundon. I rebooted and tried to reinstall it and it didn't reinstall... I later went to step 9. and here is what I got:

firewolf@X-7:~$  ossinfo
No /dev/mixer device available in your system.
Perhaps Open Sound System is not installed or running.
firewolf@X-7:~$ 

anyone have a clue?  I guess you could tell me how to uninstall oss first to redo the installation. oh and I used oss-linux_v4.0-1013_i386.deb plus before that I tried to find it and sort of 'not' downloaded it and installed a file called alsa-oss_1.0.14-1ubuntu1_i386.deb ... yeah... don't ask why...

---

### Post by Yellow Pasque on 2008-02-04
Here you go. This will get OSS uninstalled so you can start from scratch: [http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by FirewolfX-7 on 2008-02-07
Ok... thanks for removing it... but also thanks for probably being some factor in screwing up my computer os.  I am now permanently stuck in graphics safe mode.  Relax though... you have either my friend either doing something that he shouldn't have done on the internet... although I highly doubt it, or me doing something through compiz that for some reason screwed me over... I doubt that agian... but of course it is my graphics.  I reinstalled the driver, ran nvidia-xconfig, nothing... yes I am using envy.  It all started after I booted my comp when I got back from school so it fail somewhere in start up.  Oh, there is a bunch of random stuff my computer is doing during boot... more than it usually does... WAY more.  Normal boot you see at least 5 lines of checks for 2 seconds.  Here I am exposed to page long lines of checks and stuff.  One of them is for oss.

Oh yeah... later I tried reinstalling the package before this all took place.  I found the key error message and copied it for you... i think its something in the kernel that is intruding the process.

ERROR: Module snd_pcm is in use by cx88-alsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloe is in use by snd_pcm

Oh... after the computer went wonky again I removed oss again (and realized I skipped a step back then from the first time)  Went the time and effort to also procure a possible suspect... xorg.conf file... here is the part that concerns my graphics and screen. and as I said neither are registering right:

Section "Monitor"
    Identifier     "Sceptre X9G-"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Sceptre X9G-"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


  Now here is my 'backup' this is from the same os.

Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Sceptre X9G-"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Sceptre X9G-"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

