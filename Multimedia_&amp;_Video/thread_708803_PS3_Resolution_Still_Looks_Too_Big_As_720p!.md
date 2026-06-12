---
title: "PS3 Resolution Still Looks Too Big As 720p!"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Tamacracker on 2008-02-26
What's up guys. I own a 32' Syntax Olevia 232v HDTV.

I just installed Gutsy 7.10 onto my Playstation 3 and I changed the resolution so that it uses 720p. The resolution/video mode is: ps3fb:mode:131

But everything still looks horribly bulky. If I use the 1080i resolution, it becomes flickery (i know that's not a word) and looks a lil too small.. but it isn't that much of a problem. Now I know that if the screen is flickering that means the hertz are too high but they shouldn't be since they're @50 in both 720p and 1080i. 

These are the specs for my HDTV, also it uses ** ATI Xilleon Technology Video Processor**:

> Product details
General
Product Type 	32" LCD TV
Digital Television Certification 	HDTV
TV Tuner 	1x analog/digital combo
Video Interface 	Component, composite, HDMI, S-Video
PC Interface 	VGA (HD-15)
HDCP Compatible 	Yes
Width 	37.8 in
Depth 	9.4 in
Height 	22.2 in
Weight 	35.5 lbs
Display
Diagonal Size 	32" - widescreen
Technology 	TFT active matrix
**Resolution 	1366 x 768**
Display Format 	720p
Image Aspect Ratio 	16:9
Dynamic Contrast Ratio 	1600:1
Progressive Scan 	Progressive scanning (line doubling)
Widescreen Modes 	Conventional 4:3, Full, Zoom, Panorama
Viewing Angle 	178 degrees
Viewing Angle (Vertical) 	178 degrees
Pixel Response Time 	8 ms
**V-Sync Rate at Max Res. 	60 Hz**
Max V-Sync Rate 	80 Hz
Max H-Sync Rate 	85 kHz
Display Menu Language 	English, French, Spanish
Comb Filter 	3D digital
V-Chip Control 	Yes
Color Temperature Control 	Yes
Additional Features 	Video noise reduction, parental control, on-screen menu, 3:2 pulldown compensation, 2:2 pulldown compensation
TV Tuner
Analog TV Tuner 	NTSC
Stereo Reception System 	MTS
Secondary Audio Program (SAP) 	Yes
Digital TV Tuner
Digital TV Tuner 	ATSC
Video Features
HDTV Ready 	Yes
Input Video Formats 	480p, 720p, 1080i, 480i
**Supported Computer Resolutions 	1360 x 768**
Parental Channel Lock 	Yes
Closed Caption Capability 	Yes
Remote Control
Type 	Remote control - infrared
Audio System
Sound Output Mode 	Stereo
Audio Controls 	Balance, bass, treble
Speakers Included 	2 speakers
Output Power / Total 	20 Watt
Additional Features 	Auto volume adjustment
Speaker(s) 	2 x right/left channel speaker - built-in - 10 Watt
Connections
Connector Type 	1 x HDMI input ( 19 pin HDMI Type A )
1 x VGA input ( 15 pin HD D-Sub (HD-15) )
1 x headphones ( mini-phone stereo 3.5 mm )
3 x audio line-in ( RCA phono x 2 )
1 x serial
1 x S-Video input ( 4 pin mini-DIN )
1 x composite video input ( RCA phono )
1 x HD component input ( RCA phono x 3 )
1 x audio line-out ( RCA phono x 2 )
1 x USB
Miscellaneous
Compliant Standards 	FCC Class B certified, CSA, UL, cUL, EPA Energy Star, ICES-003
Power
Power Device 	Power supply - internal
Power Consumption Operational 	180 Watt


I dunno if you can tell by this image, but my applications look really bulky, seems like I still dont have enough "desktop" space/room:
[IMG]http://i62.photobucket.com/albums/h116/Tamacracker/Ps3Linuxapps.png[/IMG]



What the heck can I do? I don't think there's a resolution option that's between 720p and 1080i. I wish I could just modify the resolution within the 720p video mode.

---

### Post by wolfen69 on 2008-02-26
> I dunno if you can tell by this image, but my applications look really bulky, seems like I still dont have enough "desktop" space/room:
i might actually have to be there to get a proper feel, but judging by your screenshot, everything looks pretty good. 
> my applications look really bulky
do you mean your icons? you can right click them and choose stretch icon to shrink/enlarge.

---

### Post by Tamacracker on 2008-02-27
Well I tried to go back to 720p... and now it's locked @ 1920x1080 with refresh rate @ 25hz.
The text is jumping as well as images.

This is what my kboot looks like.

> message=/etc/kboot.msg
default=linux
timeout=100
linux='/boot/vmlinux initrd=/boot/initrd.img root=UUID=7e7f5f77-824f-4cdd-9685-f83e6e0cc282 quiet splash'
old='/boot/vmlinux.old initrd=/boot/initrd.img.old root=UUID=7e7f5f77-824f-4cdd-9685-f83e6e0cc282 quiet splash'
linux='/boot/vmlinux initrd=/boot/initrd.img root=/dev/ps3da1 video=ps3fb:mode:131'



Also my ps3pf-utils is broken. I tried configuring it without kboot. This is what I get:

> illmortal@illmortal:~$ ps3videomode -h
The program 'ps3videomode' is currently not installed.  You can install it by typing:
sudo apt-get install ps3pf-utils
bash: ps3videomode: command not found
illmortal@illmortal:~$ sudo apt-get install ps3pf-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ps3pf-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
illmortal@illmortal:~$ sudo apt-get --reinstall install ps3pf-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of ps3pf-utils is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

