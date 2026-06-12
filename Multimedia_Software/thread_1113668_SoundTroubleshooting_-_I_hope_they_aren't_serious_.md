---
title: "SoundTroubleshooting - I hope they aren't serious on this!"
date: 2009-04-01
forum: Multimedia Software
---

### Post by DGeeez on 2009-04-01
I just spent the whole evening hunting for clues and trying out all sorts of fixes (most for older versions than Intrepid) which did not work, and eventually was directed to this official, copyrighted Ubuntu document, called SoundTroubleshooting:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

There, some snarky writer who apparently presumes that all Linux newbies have chimpanzee intelligence had me checking to make sure the volume controls weren't on zero, and that the sound wasn't muted, before showing one more way of listing the hardware on my laptop. I'm writing from my PC now, so here are the hardware specs available for cut n' paste from running lshw: 

id:	
multimedia
description: 	Audio device
product: 	82801I (ICH9 Family) HD Audio Controller
vendor: 	Intel Corporation
physical id: 	
1b
bus info: 	
pci@0000:00:1b.0
version: 	03
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list
configuration:	
driver	=	HDA Intel
latency	=	0
module	=	snd_hda_intel

The details listed aren't precisely what was yielded for the specified command which I ran on my laptop, but I think this is the same data, which I saved and transferred a few days ago:

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)

Sorry I can't send code boxes, but my whole panel of control buttons is unresponsive! I'm sending this from another Ubuntu machine, maybe that's just one more Intrepid bug. Anyway,the next step was to drop the first hint on who Alsa is - apparently, they are the only source for linux audio support. Official Ubuntu doctrine is that Alsa either supports my sound card or they don't, and that if they don't, go buy a new card! I don't even know if a laptop can be opened for a new card, but I find it really unbelievable that a mid-priced model which is widely available in Office Depot is too obscure for Linux coverage. I've seen several threads in the past two days (if years back-dated) which tell of success in overcoming sound-quality issues with Toshiba models computers which are NOT on the Alsa list, but then they aren't mine either, and that's why I hope somebody here can be more helpful than the official documents.

My laptop model is Toshiba Satellite L305-S5933 - I would much appreciate any info anyone has on sound with the Satellite series, especially the L line. 

Thanks.

---

### Post by TBerk on 2009-04-01
OK, 1st off I usually find the controls you mention are 'broken' by script blocking utils in your browser, or some other lack of Java or similar scripting dysfunction.

You can still past URLs into your text, people have the option to copy/paste them in a more ala carte manner than just clicking on a link.

2ndly, you can place url and /url on the front and back of the URL, keeping in mind these will need to be bracketed  with [ and ]. 

> [ url ] & [ /url ]  with the spaces removed.

read this:

BB Code
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

How it works, SOUND
[http://ubuntuforums.org/showthread.php?p=5931543]("http://ubuntuforums.org/showthread.php?p=5931543")

But most all I'd have you read this:
[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")


Here is some good info; it didn't fix my lack of sound in 9.04 but I still found it useful:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)


TBerk

---

### Post by Excedio on 2009-04-01
> **DGeeez said:**
> There, some snarky writer who apparently presumes that all Linux newbies have chimpanzee intelligence had me checking to make sure the volume controls weren't on zero, and that the sound wasn't muted, before showing one more way of listing the hardware on my laptop. I'm writing from my PC now, so here are the hardware specs available for cut n' paste from running lshw:
 
Looks like good troubleshooting steps to me. Better safe than sorry right?

---

### Post by markbuntu on 2009-04-02
You would be surprised at how many people do not know to check their volume controls. Anyway, there is a more comprehensive troubleshooting guide here. In the Drivers/hda section there is a link to fix your L305 problem.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by DGeeez on 2009-04-02
> **TBerk said:**
> OK, 1st off I usually find the controls you mention are 'broken' by script blocking utils in your browser, or some other lack of Java or similar scripting dysfunction.

You can still past URLs into your text, people have the option to copy/paste them in a more ala carte manner than just clicking on a link.

2ndly, you can place url and /url on the front and back of the URL, keeping in mind these will need to be bracketed  with [ and ]. 

 with the spaces removed. 

You got me, that one was my fault - I forgot that I had installed NoScript, which has turned out to be quite a machine gun - that means not on target, and hard to control! 

> read this:

BB Code
[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

How it works, SOUND
[http://ubuntuforums.org/showthread.php?p=5931543]("http://ubuntuforums.org/showthread.php?p=5931543")

But most all I'd have you read this:
[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

Here is some good info; it didn't fix my lack of sound in 9.04 but I still found it useful:

[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html) Tberk

Tried them all, and still don't have better sound.

markbuntu> You would be surprised at how many people do not know to check their volume controls. Anyway, there is a more comprehensive troubleshooting guide here. In the Drivers/hda section there is a link to fix your L305 problem.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
markbuntu

I just went through this one too - downloaded more files, installed PulseAudio over the default, made certain that my card is listed where it's supposed to be, and all the volume controls are maxed. My problem dosen't even fit the descriptons listed on this forum - There has always been sound, and not particularly distorted (hard to tell at very low volume), but it's just that, no matter what the GUI says, the sound is barely there. It's there, but you can barely hear it on the loudest setting, and that's certainly not loud enough. I'm not having difficulty hearing people, nor the sound on my desk computer, so there is still a problem which the last 12 hours of following as many tutorials has not fixed on that Toshiba laptop. In fact, the sound became even fainter since I rebooted, following the installation of PulseAudio over the default driver. It only seems noteable that none of official tutorials on this website except for the one titled SoundConfiguration even address issues with specific hardware cards, and while that left me with some negative vibes, perhaps the author was right. I didn't actually see any references to Toshiba or Intel hardware, where have you seen this?

---

### Post by markbuntu on 2009-04-02
There is a link in the hda section of that guide I posted to here, which is all about intel hda and has a specific listing for the toshiba L305

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

