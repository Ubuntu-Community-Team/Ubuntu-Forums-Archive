---
title: "Just switched from knoppmyth, having problems"
date: 2008-02-01
forum: Mythbuntu
---

### Post by jkbowle on 2008-02-01
(a little background) Last year I setup knoppmyth on a dedicated backend and a seperate frontend.

Mythtv worked near flawlessly.. but there were some glitches so I decided to go with a frontend / backend all in one box.. and install mythbuntu.. (BTW I successfully transferred all recorded material to the new box)

But I'm having some minor issues... here's my setup, followed by my issues.

Motherboard: Biostart P4M80 socket 478
CPU: Intel Pentium 4 2.8 ghz
Ram: 2 sticks of 512mb DDR Ram
Graphics Card: Radeon AIW 9700 Pro series (not using it to capture video)
Onboard sound/Ethernet
Capture Card: Haughpauge PVR 150
Power Supply: 1U Silencer 250W (fits 1U server, hacked it to fit (cuz it's quiet)
Remote: ATI Wonder Remote

I'm using proprietary drivers to get the TV-out to work.

Problems:
Watching record material: the frame rate seems slow.. it's watchable but irritating at times.  Lower quality avi's in Myth video seems to play okay though.

Watching DVD's.. again choppy (I've verified that DMA is enabled.. so not sure)
Importing DVD's.. Only works half way.. I can see the vob file in the temp directory.. but nothing ever shows up in my videos folder.  I checked the mtd log and it says everything worked successfully... I also cut and paste the command from the log and ran it myself and it fails after 20 minutes.. (I need to try again on another DVD)
Importing Music: WORKS!  but seems slow.

The TV-out cuts off the about a centimeter on both sides of picture and I can't find the ATI tool that will reposition the picture so it fits on my tv.. if one exists.

Also the system status says I only have 512 mb of ram.. So I think one of my sticks is bad. (great)

I'm wondering if my problems are related to the Ram, and or my Graphics Card being ATI.

Also, I'm concerned my power supply isn't enough to keep up.. ( how would I know).

Other than problems I stated the system is stable and I've left it running for days.. and it always seems to work. (it did lock up once when watching a youtube video full screen, BTW when is someone going to write a youtube plugin for Myth???)

Let me know if you have suggestions on my course of action.

---

### Post by superm1 on 2008-02-01
> **jkbowle said:**
> (a little background) Last year I setup knoppmyth on a dedicated backend and a seperate frontend.

Mythtv worked near flawlessly.. but there were some glitches so I decided to go with a frontend / backend all in one box.. and install mythbuntu.. (BTW I successfully transferred all recorded material to the new box)

But I'm having some minor issues... here's my setup, followed by my issues.

Motherboard: Biostart P4M80 socket 478
CPU: Intel Pentium 4 2.8 ghz
Ram: 2 sticks of 512mb DDR Ram
Graphics Card: Radeon AIW 9700 Pro series (not using it to capture video)
Onboard sound/Ethernet
Capture Card: Haughpauge PVR 150
Power Supply: 1U Silencer 250W (fits 1U server, hacked it to fit (cuz it's quiet)
Remote: ATI Wonder Remote

I'm using proprietary drivers to get the TV-out to work.

Problems:
Watching record material: the frame rate seems slow.. it's watchable but irritating at times.  Lower quality avi's in Myth video seems to play okay though.

Watching DVD's.. again choppy (I've verified that DMA is enabled.. so not sure)
Importing DVD's.. Only works half way.. I can see the vob file in the temp directory.. but nothing ever shows up in my videos folder.  I checked the mtd log and it says everything worked successfully... I also cut and paste the command from the log and ran it myself and it fails after 20 minutes.. (I need to try again on another DVD)
Importing Music: WORKS!  but seems slow.

The TV-out cuts off the about a centimeter on both sides of picture and I can't find the ATI tool that will reposition the picture so it fits on my tv.. if one exists.

Also the system status says I only have 512 mb of ram.. So I think one of my sticks is bad. (great)

I'm wondering if my problems are related to the Ram, and or my Graphics Card being ATI.

Also, I'm concerned my power supply isn't enough to keep up.. ( how would I know).

Other than problems I stated the system is stable and I've left it running for days.. and it always seems to work. (it did lock up once when watching a youtube video full screen, BTW when is someone going to write a youtube plugin for Myth???)

Let me know if you have suggestions on my course of action.
Very first thing with questionable hardware is test it.  There is a memory tester on the live disk when you boot up.  Please let that run for a couple hours and see.

---

### Post by jkbowle on 2008-02-01
on the mythbuntu disk, or on a regular ubuntu disk?  What's the app?  Can I install it with apt-get or through synaptic(sp?)?

---

### Post by superm1 on 2008-02-01
> **jkbowle said:**
> on the mythbuntu disk, or on a regular ubuntu disk?  What's the app?  Can I install it with apt-get or through synaptic(sp?)?
Either disk, boot it up and in the boot menu there is a memtest item.

Also, there should be one in your grub listing from what i remember.

---

### Post by jkbowle on 2008-02-05
Okay the memory is all good now. I had to open up the case and make sure both sticks were seated fully.  

Also been able to test Live TV and it works!  But I scheduled my first recording and the system locked up on me.. I'm trying another one today.

The DVD Import is still not working though.. I tried a 4th DVD.. same as all the others.. the VOB is copied to the temp folder fine.. but no video shows up in my videos folder.. the MTD log says that it ran successfully.

The last one I checked it and it was running fine with about 5 mins left in the creation of the VOB file.. checked it 10 mins later and it was done??
But yet no file in my videos folder... I'm stumped..

Any one else have this problem???

And anyone know how I can get my screen repositioned for my Tv-out from my ATI card??

Thanks

---

### Post by jkbowle on 2008-02-05
Bump..

FYI - My scheduled recording worked today.. so Still looking for answers for my problems with import DVD funtionality and getting ATI tv-out to fit TV.

---

### Post by jkbowle on 2008-02-06
I've done some research and found that transcode is failing but the mtd is not picking up that failure for some reason.

Running transcode on my own and I think I have found the problem.. I'm starting a new thread for that.. ([http://ubuntuforums.org/showthread.php?t=689221](http://ubuntuforums.org/showthread.php?t=689221))

Still would like to know how to get the menu bar off my tv screen.. and how to adjust the size of my window to fit the tv better.

Anyone?

---

