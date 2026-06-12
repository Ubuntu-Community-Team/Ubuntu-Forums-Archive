---
title: "Hauppauge HVR 1600 Installation Progress"
date: 2008-09-11
forum: Mythbuntu
---

### Post by sbhargav21 on 2008-09-11
Hi All,
I started recently with building a DVR & just wanted to share my experiences & progress with this.

**My Hardware:**
Hauppauge HVR 1600
ATI Radeon x1300 pro AGP 256mb
Celeron
1 GB RAM
40 GB Harddrive
400 GB SATA Harddrive (Not yet connected)
CD Drive

**Start:**
1. Downloaded 8.04 distribution ISO
**Problem #1:**
Was trying to burn it on a CD but was not getting detected. 
 - Stupid me realised later that ISO needed to be burnt using ISO to CD maker.
 - Downloaded one of the free ISO to CD burner & then it was detected. :)

2. Started installation of Mythbuntu
Followed [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841) tutorial.

**Problem #2:**
Installation worked till steps 10. The part where he says /bin/cat /dev/video0 > test.mpg did not work!. :(
 - Please read later on for the continuation of this fix.

**Problem #3:**
The display on TV was not full, most parts of the output were off the screen. I had to guess using the installation manual & tabs which field I was in & what I was supposed to enter.
 - Followed the following installation guide to get a proper output on my TV.
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
 - Display was corrected :)

**Problem #4:**
The display was still black & white on TV. I tried to play with xorg.conf settings but nothing worked.
 - Was thinking of changing the s-video cable as suggested by some posts. Switched the ends of the cable. Connected the previous TV end to card & card end to TV.
 - Color display :)

**Problem #2 Revisited:**
 - I was having same issue as sofasurfer in post #25 at [http://ge.ubuntuforums.com/showthread.php?t=813429&page=3](http://ge.ubuntuforums.com/showthread.php?t=813429&page=3).
 - Followed post #26 by willoconley.
 - Card detected :)

**Problem #5:**
I have connected the output of my Cox settop to Tuner Anlog input. Not able to scan any channels. Not sure what to do next.
When I try cat /dev/video0 > test.mpg. No picture but just hissing sound!. :)
 - I had to define a video source. Defined as no guide data as I do not have a subscription to scheduledirect yet. Named 'Analog Digital Cable'
 - In the input connection in the Tuner 1 had to select input source defined earlier 'Analog Digital Cable'
 - Scan button was enabled, detected Channels 3,4 & 48 
 - Channel 3/4 is regular TV Settop output, not sure what channel 48 is.
 - Starting channel set as 3.
 - Tuner able to tune & channel gets displayed on TV :)

**Problem #6:**
The TV display freezes up. When I record a channel it is recorded but playback freezes. I can use VLC player to play the recorded .mpg file & it plays well.
 - Am fiddling with the playback settings but nothing has worked so far 
 - I have been told that it might be a ATI driver config issue, about Overlay & other things .. not sure how to fix this :(


- Meanwhile any advice on this is appreciated

---

### Post by 24jedi on 2008-09-11
> 
Problem #5:
I have connected the output of my Cox settop to Tuner Anlog input. Not able to scan any channels. Not sure what to do next.
When I try cat /dev/video0 > test.mpg. No picture but just hissing sound!.
- I had to define a video source. Defined as no guide data as I do not have a subscription to scheduledirect yet. Named 'Analog Digital Cable'
- In the input connection in the Tuner 1 had to select input source defined earlier 'Analog Digital Cable'
- Scan button was enabled, detected Channels 3,4 & 48
- Channel 3/4 is regular TV Settop output, not sure what channel 48 is.
- Starting channel set as 3.
- Tuner able to tune & channel gets displayed on TV 


I am having similar issues ... but with FIOS. When I connect the [COLOR="Navy"]**STB --to--> MythTV --to--> TV**[/COLOR], the only way I could get a signal was with MythTV on channel 1... and leave it on 1.

All channel controls were made exclusively from the STB.

---

### Post by sbhargav21 on 2008-09-15
**Problem #6: (Contd.)**

Apparently my issue TV display is a result of 3D Rendering not getting enabled. Following are the things I tried to enable it.
 - Method 2 from [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
 - Mirror mode tweak entioned in Post#5 of [http://ubuntuforums.org/showthread.php?t=580796&highlight=ATI+video+overlay+TV](http://ubuntuforums.org/showthread.php?t=580796&highlight=ATI+video+overlay+TV)
 - Envy [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
 - Post# 120 in [http://ubuntuforums.org/showpost.php?p=1955179&postcount=120](http://ubuntuforums.org/showpost.php?p=1955179&postcount=120)
 - Method 1 & 2 in [http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver](http://www.mythtv.org/wiki/index.php/ATI_Proprietary_Driver)
 - None of the above methods have worked so far, the only thing that gets loaded is the **MESA** ones! :(

---

### Post by zepfan on 2008-09-19
> **sbhargav21 said:**
> 
**Problem #6:**
The TV display freezes up. When I record a channel it is recorded but playback freezes. I can use VLC player to play the recorded .mpg file & it plays well.
 - Am fiddling with the playback settings but nothing has worked so far 
 - I have been told that it might be a ATI driver config issue, about Overlay & other things .. not sure how to fix this :(


While I offer no help to fix. My display froze using fglrx driver. When using the default driver (after clean install) it didn't freeze. The last couple times I've used the fglrx drivers, I've found a black screen after booting and only recovery console to default will fix. Maybe you want to back up your xorg file and try the recovery console to reset x server to default, and see if that fixes your freezing. Then at least we'll know what the problem is.

---

### Post by jesusdemontreal on 2008-09-27
No pretending to solve any issues but rather a comment on my personnal story.

I have two HVR 1600 cards in the same pc along with a NVidia 6200, sound card and network. I had some issues with one of my card being badly or not at all recognized. After a while, I came to understand that the card was sharing IRQ with the NVidia card, which for some reason resulted in my broken card.

A rather barbaric fix for this was to turn off the computer, remove the HVR cards, network and sound and installing them in this order

PCI-1 HVR 1600
PCI-2 HVR 1600
PCI-3 Empty
PCI-4 Network
PCI-5 Sound

On my motherboard, the PCI slots are actually marked down, but on most motherboard, if not indicated, the first PCI slot is the closest one to the CPU. 

Doing so and telling my BIOS to clear the ESCD data (in the PnP options from the BIOS) changed my IRQ's so now my soundcard shares IRQ with the HVR 1600. This seemed to solve all my issues with lags, freezes and system malfunction.

---

