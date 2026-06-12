---
title: "Pre-mythtv fails at mplayer /tmp/test_capture.mpg"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-04-07
Second myth box problems;

 I'm following the Mythtv Edgy guides to prepare the box for Myth installation.  MythTV_Edgy_Backend_Frontend
MythTV_Edgy_hardware
Install_IVTV_Edgy
Install_IVTV_Troubleshooting

 I breezed through backend_frontend to the point that I had to jump to hardware, then followed the link in hardware and installed IVTV with the same ease.

  Now to pay for my foolish optimism; I decided to test the capture card at this point using the Ubuntu specific troubleshooting link.  

"dmesg |grep Initialized"  gives me the expected response:  ivtv: Initialized WinTV PVR 150, card #0.

"cat /dev/video0 > /tmp/test_capture.mpg"  seems to work and return to the command line after a Control-C.  I checked /tmp and test_capture.mpg is in the directory.

The fun begins when I try to view the recording.    

I type "mplayer /tmp/test_capture.mpg", hit enter, then excrement hits the rotary impeller:  Many lines of code scroll by (several screens full) ending with errors like "permission denied"  "Error opening frame buffer device!"  and many more.

At the end of al this the command line reappears, but every key I hit just doesnt operate correctly; enter doesn't react. the c key gives a period on the screen, the up arrow is now "g", Page up is "I" etc

Since I have no control at this point, I can't scroll up to see the start of the errors so I have to force a shutdown or reset via the PC tower's buttons.

I've tried the live cd's with less than great results; 6.10 live won't get past the logon/password entries, 6.06 
live does fire up the pc, but as I found out, the live system doesn't have my capture card installed (D'ouh!)

I'm going to try to record some static, and store it somewhere other than temp to see if I can access it from 6.06 live and totem.  
At this point I'm trying to see if the PC is capable of viewing the .mpg file.  If not I will have to figure out if it is the amount of memory or the video card.   -  Totem fires up, but errors when trying to play video from samples folder.

 The PC is a dell dimension xps 450, with a 800 mhz P3 cpu, 384megs of ram, the Hauppague 150 card and whatever stock video card came with it.

Any ideas what else to check on this one? 

TIA
"Panhead Bill"

---

### Post by Panhead Bill on 2007-04-10
Curiouser and curiouser.

  I wiped the drive and tried the live install disk.  Live "almost" loaded but gave me a three image desktop screen - that is to say the image was shreaded horizontally and the slices were shifted onto three partial images.  (one left, center, and right)  attempting to logon put me into an endless loop of attempts to build the desktop.

Tried the install and got to the logon screen but then immeadiately went into an all brown screen but no top or bottom bar, no cursor. 

 Reset and tried the alternate disk OEM install result: endless loop after "oem" logon - where the desktop starts to load through nautilus, then the screen flashes black then back to logon screen.

I'm nearly convinced that this is a hardware issue, but will try a dapper install before I start swapping parts.

---

### Post by Panhead Bill on 2007-04-12
I feel like i'm talking to myself here.

Anyway Dapper live disk loads onto the test mule PC in both the live mode and the install mode.

I wonder why Egdy doesn't?

---

