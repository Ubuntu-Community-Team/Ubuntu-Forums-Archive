---
title: "Old and new NVDIA graphics drivers on the same machine?"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by AndrewTK on 2006-07-09
Hi all,

Hopefully someone can explain how to do this, or in fact whether it is possible to do this at all.

Firstly what I'm trying to do:

I have an older machine which a dual head setup and it has a new AGP graphics card Nvidia FX5200, I also have an Nvidia PCI card which is a RIVA TNT2 64 Pro.

After installing, I am left with the default open "nv" drivers which obviously aren't as good, so first step is update the drivers through synaptic. The problem is that I can only install one set, either the new one covering the FX5200 or the old one covering the RIVA - it would seem they can't coexist.

My rationale is that they can't coexist because they have the same name "nvidia" as opposed to "nv" which causes a conflict.

So my state of play is that I have it installed for the FX5200 which gives me one accelerated screen and left the default for the RIVA which is pig slow - but unfortuantely I can't use Xinerama to have one desktop because it causes a nightmare moving things from one monitor to another as the two graphics cards' speed difference is too great with the different drivers.

Anyone that can help me install the two drivers side by side then apply them within Xorg.conf will be greatly appreciated.

Cheers
AndrewTK

---

### Post by Max Luebbe on 2006-07-09
can you post your Xorg.conf?

---

### Post by tseliot on 2006-07-09
I think a compromise can suit your needs:
install the legacy driver 7178 (which supports both cards and it's new).

You can try my script for driver 7178:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by psylo on 2006-07-12
Hi mate

Thanks for the link. Am about to try it now - have read through your instructions so hopefully this will all work now.

Cheers
AndrewTK

---

### Post by psylo on 2006-07-12
Righto - seems I bit the dust in not too short an order.

Basically followed the direction on the link you sent me tseliot and went to execute the script and it got to the point where it FTP'd to the NVidia server then gave me the following:

CWD /XFree86/Linux-x86/1.0-7178...
No such directory XFree86/Linux-x86/1.0-7178

Error: I Can't find the Nvidia Installer make sure it is in the same folder as this script.

Looking at the nVidia site it would appear that there isn't a folder for 1.0-7178 any idea which one I should use?

Cheers
AndrewTK

---

### Post by tseliot on 2006-07-12
> **psylo said:**
> Righto - seems I bit the dust in not too short an order.

Basically followed the direction on the link you sent me tseliot and went to execute the script and it got to the point where it FTP'd to the NVidia server then gave me the following:

CWD /XFree86/Linux-x86/1.0-7178...
No such directory XFree86/Linux-x86/1.0-7178

Error: I Can't find the Nvidia Installer make sure it is in the same folder as this script.

Looking at the nVidia site it would appear that there isn't a folder for 1.0-7178 any idea which one I should use?

Cheers
AndrewTK
My bad, there is a typo in my script.
I'll fix it and upload it in a minute.

---

### Post by tseliot on 2006-07-12
Done!

Refresh the page on my website and download the script again

---

### Post by psylo on 2006-07-12
HI chief,

I might have tried this already though I am going to download your script rather than my edit. 

I FTP'd up to nvidia and realised the 7178 didn't exist so changed the script to 7182 as the version. It did all the downloading fine but when the installer ran it threw a fatal error - looking through the error log it would appear I don't have libc dev installed.

I'm going to synaptic that and then try again with your script and see what happens...

Any other dependencies I might run into?

Cheers
AndrewTK

---

### Post by psylo on 2006-07-12
Hi tseliot,

Right I have something very weird going on now. I tried your script but it seems like the mod I made was the same, as such the error I got was the same. 

Essentially looking through the error log for the nvidia installer it gets to the point where it does a version check on gcc and goes to compile a file and it is throwing an error there saying that check your development libc is installed and that "cc" is a valid compiler.

Off I went to synaptic to make sure it was all installed and it would appear as though all of the GCC stuff is installed [as it should be in a distribution] and all of the dev libraries have been installed as well.

What has weirded me out about this is that if I try a "whereis gcc" etc it just says command not recognised.

Now I did a distribution ubreage from Breezy to Dapper and I am wondering whether something has gone awry there where it is telling me these things are installed but they haven't been...

Any ideas here would be very welcome.

Cheers
AndrewTK

---

### Post by tseliot on 2006-07-12
> **psylo said:**
> HI chief,

I might have tried this already though I am going to download your script rather than my edit. 

I FTP'd up to nvidia and realised the 7178 didn't exist so changed the script to 7182 as the version. It did all the downloading fine but when the installer ran it threw a fatal error - looking through the error log it would appear I don't have libc dev installed.

I'm going to synaptic that and then try again with your script and see what happens...

Any other dependencies I might run into?

Cheers
AndrewTK
Weird, my script should handle the dependencies

---

### Post by tseliot on 2006-07-12
> **psylo said:**
> Hi tseliot,

Right I have something very weird going on now. I tried your script but it seems like the mod I made was the same, as such the error I got was the same. 

Essentially looking through the error log for the nvidia installer it gets to the point where it does a version check on gcc and goes to compile a file and it is throwing an error there saying that check your development libc is installed and that "cc" is a valid compiler.

Off I went to synaptic to make sure it was all installed and it would appear as though all of the GCC stuff is installed [as it should be in a distribution] and all of the dev libraries have been installed as well.

What has weirded me out about this is that if I try a "whereis gcc" etc it just says command not recognised.

Now I did a distribution ubreage from Breezy to Dapper and I am wondering whether something has gone awry there where it is telling me these things are installed but they haven't been...

Any ideas here would be very welcome.

Cheers
AndrewTK

Make sure you have all the repositories enabled (and pointing to Dapper instead of Breezy)

---

### Post by psylo on 2006-07-13
Hi there,

What was really weird is that in the end I had to remove all my repositories then re-add them and then get Synaptic to do a complete refresh of the repository list - at that point all of a sudden GCC hadn't been installed etc...

The new problem I have is that now as I try it the nvidia installer is bailing out because it sees that the installer already exists and is telling me to move it or create a new --target folder. Any ideas where the installer is copied to so I can remove it and give this a proper go?

---

### Post by tseliot on 2006-07-13
> **psylo said:**
> The new problem I have is that now as I try it the nvidia installer is bailing out because it sees that the installer already exists and is telling me to move it or create a new --target folder. Any ideas where the installer is copied to so I can remove it and give this a proper go?
That is not a problem.

1) What happens then?

2) Can you post your /var/log/nvidia-installer.log ?

---

### Post by psylo on 2006-07-13
Hi mate,

I removed the extracted folder and it all seemed to work fine - looking through the installer log [rather than posting the whole thing which is pretty long] it does the installation can does the sanity checks at the end - the final line is: 

-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-7182) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README for details.

So that is all good.

Because I have such as specific xorg.conf - because of the two gfx cards, I didn't let the script update it. As such I went back into it and changed the drivers from "nv" to "nvidia" on both my cards and then restarted - basically it just hung on the nVidia splash screen and went no further. 

This is what happened when I originally tried doing this, not realising that there were two different drivers for the different chipsets...

Any ideas what I can do now chief?

Cheers
AndrewTK

---

### Post by psylo on 2006-07-13
Here also is the pertinent parts of my xorg.conf file if it is of any use: - I have snipped certain bits out where it won't be relevant.



Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:0:13:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	VendorName	"NVIDIA"
	Driver		"nv"
	BusID		"PCI:1:00:0"
EndSection

Section "Monitor"
	Identifier	"Compaq MV720"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Monitor"
	Identifier	"Benq FP767-12"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Screen"
	Identifier	"Screen Left"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Compaq MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen Right"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	Monitor		"Benq FP767-12"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen Left"
	Screen		"Screen Right" RightOf "Screen Left"
	Option		"Xinerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

All I tried to change was the "nv" driver to "nvidia" on both screens...

Cheers
AndrewTK

---

### Post by tseliot on 2006-07-13
> **psylo said:**
> Here also is the pertinent parts of my xorg.conf file if it is of any use: - I have snipped certain bits out where it won't be relevant.




All I tried to change was the "nv" driver to "nvidia" on both screens...

Cheers
AndrewTK
First off let's try to solve 1 problem per time: see the corrections in red:

(Twinview might be causing problems)

> Section "Module"
	[COLOR="Red"]#[/COLOR]Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	[COLOR="Red"]#[/COLOR]Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection


Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"[COLOR="Red"]nvidia[/COLOR]"
	BusID		"PCI:0:13:0"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	VendorName	"NVIDIA"
	Driver		"[COLOR="Red"]nvidia[/COLOR]"
	BusID		"PCI:1:00:0"
EndSection

Section "Monitor"
	Identifier	"Compaq MV720"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Monitor"
	Identifier	"Benq FP767-12"
	HorizSync	30-68
	VertRefresh	50-85
	Modeline 	"1152x864@75" 107.48  1152 1208 1336 1584   864  864  867  904
EndSection

Section "Screen"
	Identifier	"Screen Left"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Compaq MV720"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen Right"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)"
	Monitor		"Benq FP767-12"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x768" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen Left"
	[COLOR="Red"]#[/COLOR]Screen		"Screen Right" RightOf "Screen Left"
	[COLOR="Red"]#[/COLOR]Option		"Xinerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by psylo on 2006-07-13
Hi Alberto,

Thanks for your patience on this... much appreciated as having a sluggish desktop has really put me off using linux day-to-day...

Right, I've updated my xorg.conf file to what you have specified then tested it. It all works well and I notice a definite speed improvement as well so it must be accellerating.

Now, I've done a "next step" which is worth mentioning which was that I commented out the "Screen 'Screen Left'" bit and put in a "Screen 'Screen Right'" to test whether this would all work okay...

Unfortunately when I restarted X all I got was a blank screen - just black with nothing. I had this way back when I first started mucking around with this whole dual-head stuff when I was trying to work out how to get the various drivers working for the different cards.

I've also tested setting to the driver for screen right back to the normal "nv" one and then trying this with just the right hand screen and it works so the config is definitely okay, it's just something to do with the driver not being happy - I think anyway.

Any more thoughts or should I just go and sink £100 into a new gfx card which is AGP with dual head onboard? Solves the symptom I guess but not the problem...

Cheers
AndrewTK

---

### Post by psylo on 2006-07-13
One other thought I have had...

Is it possible to install the non-legacy driver along side the legacy one and call them different things as far as driver names are concerned... maybe referring to the new one as "nvidianew" rather than "nv" or "nvidia"?

Cheers
Andrew

---

### Post by tseliot on 2006-07-13
> **psylo said:**
> One other thought I have had...

Is it possible to install the non-legacy driver along side the legacy one and call them different things as far as driver names are concerned... maybe referring to the new one as "nvidianew" rather than "nv" or "nvidia"?

Cheers
Andrew
I doubt you can do that. At least not with the Nvidia installer. Maybe an Ubuntu or a Debian developer could do such a thing but I can't.

You can buy a cheap card (e.g. mine is a GeForce FX 5500 128mb)

---

### Post by psylo on 2006-07-13
I think that might be the way forward to be fair. Whilst it would be nice to use this kit I have sitting here PCI cards are getting more and more out of date and the real options long term will be dual head AGP or PCI-E cards anyway which I believe are quite well supported with TwinView and the like.

The really galling thing is it all works so nice and easily on bloody Windows which I know everyone hates people saying and I have no doubt at all by the way the NV and NVIDIA drivers sit perfectly next to each other in Xorg that if there was just a way of installing the two with different reference names this issue would be completely resolvable...

Thanks loads for your help on this Alberto, you've been really helpful - espeically as my old card is now running a lot more smoothly so there has been some moving forward...

Cheers
Andrew

---

### Post by tseliot on 2006-07-13
> **psylo said:**
> I think that might be the way forward to be fair. Whilst it would be nice to use this kit I have sitting here PCI cards are getting more and more out of date and the real options long term will be dual head AGP or PCI-E cards anyway which I believe are quite well supported with TwinView and the like.

The really galling thing is it all works so nice and easily on bloody Windows which I know everyone hates people saying and I have no doubt at all by the way the NV and NVIDIA drivers sit perfectly next to each other in Xorg that if there was just a way of installing the two with different reference names this issue would be completely resolvable...

Thanks loads for your help on this Alberto, you've been really helpful - espeically as my old card is now running a lot more smoothly so there has been some moving forward...

Cheers
Andrew
I wish I could help you more but I have never had 2 graphic cards in the same computer.

Regards

Alberto

---

