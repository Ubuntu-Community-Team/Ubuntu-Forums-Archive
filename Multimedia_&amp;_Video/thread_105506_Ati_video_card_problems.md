---
title: "Ati video card problems"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by jenco on 2005-12-18
before i get flamed i just want you  to know that i know i posted this in the kubuntu forums too but noone has responded and was hoping someone here could help me out

Well i got kubuntu installed yay! figured out how to install my belkin wifi card =D. But now my ati card causes problems when i install the card ~ The Reason i removed the card to begin with is that it causes a acip fatal error and the kernel panics : /

Well i removed the card and the rest of the installation went smoothly =).  But using the intergrated 8mb intel card sucks =-/.

So i put in the ati card and getting the same problems ~ damn compaq :/ the card installs perfectly on my 450 P3 cpu.  SO i know its not the card ;p.   Tried the noacip option at boot (btw if it matter i have to use the acpi=off option to even boot on this machine ><. But any help would be appreciated =)

P.S. u can't really turn off the intel card in the bios or with jumpers :/

Here's a link to my machine [http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?dlc=en&tool=prodinfoCategory&lc=en&cc=us&dest_page=prodinfoCategory&product=425916](http://h10025.www1.hp.com/ewfrf/wc/prodinfoCategory?dlc=en&tool=prodinfoCategory&lc=en&cc=us&dest_page=prodinfoCategory&product=425916)

I've upgraded to a gig ram. And added a 120 gig hd. Thank u in advance for any help you can offer 

 well been experiminting all day ~.~

Istill using my itel intergrated card ~ Does'nt lock up until i disable my intergrated card and switch to my ati card.  I've tracked the probem down to the hotplug module not liking them both there ~ Is there a way to disable the hotplug system from seeing my intel card?

I do not know if this is even possible been playing around with everything and before i break my system i wanted to get your ideas =p

---

### Post by jenco on 2005-12-19
Yay got it all working =D~

FOr anyone having troubles with intergraded intel video and trying to upgrade to a better card here are some tips that got mine working after 4 days of googling ;p

in /etc/hotplug/blacklist

edit at the bottom intel_agp (prevent hotplug from causing a kernel panic)

in your xorg.config file 

Section "Device"
	Identifier	"ATI"
	Driver		"fglrx"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"no"

# You don't actually need this next BusID bit - unless maybe you have dual monitors?
# I've removed it from mine (single monitor only) and all is well.
# I think it's a leftover from fxglrconfig - doh!
         [COLOR="Red"]BusID		"PCI:1:10:0"  <- Remove this line ~![/COLOR]
EndSection

Section "Monitor"
	Identifier	"ENVISION"
	Option		"DPMS"
	HorizSync	30-94
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"ENVISION"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

and follow directions from this post closely =)

[http://ubuntuforums.org/showthread.php?t=24557&highlight=Ati+drivers+0.2](http://ubuntuforums.org/showthread.php?t=24557&highlight=Ati+drivers+0.2)

Hope this saves u from all the headache it has caused me =P and thanks to all the people in #Ubuntu channel for all your help =)

---

### Post by Ocxic on 2005-12-19
check your bios to see if it initializes the PCI or AGP slot first, it should be set to  AGP. i dunno if that would help but, i know it could cause problems

---

