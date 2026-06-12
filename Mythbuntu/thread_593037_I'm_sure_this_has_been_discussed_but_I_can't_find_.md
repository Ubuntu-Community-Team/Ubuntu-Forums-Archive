---
title: "I'm sure this has been discussed but I can't find the answer..."
date: 2007-10-26
forum: Mythbuntu
---

### Post by Zelgadis on 2007-10-26
I have the problem with Audio not stopping when you pause Live TV.  I tried to follow the advice on the guide but I got stuck at the part of setting Line In as Capture.  I hit Space and nothing happened.  I did notice it said "Capture All" at the top but I don't know if that means anything.  In the gui version of AlsaMixer I notice 3 sound settings that aren't in the command line version called "Capture" "Capture1" "Capture2" and I noticed it seems to correspond with three Mic Input Sources that don't seem to be adjustable at all.  This is strange considering I actually only have two Mic inputs (front and back).  In addition, the sound coming out of the tuner sounds like crap.  I haven't tested other sources of sound yet though the sound worked fine in Windows.

Specs:
CPU:  AMD64x2 4000+
Motherboard: GA-MA69GM-S2H
2 GB RAM
pcHDTV 5500

Using onboard video and audio.

I should probably go ahead and note that this is my first time using any form of Linux.

Since I'm already making a post, I guess I should mention the other problems I have experienced.  When I tried to install Mythbuntu initially, I ran into the problem of my monitor saying that the frequency was out of range (75 and my monitor only supports 60) and had to borrow my LCD from another computer (which was rather troublesome and I can't see why the install doesn't support lower refresh rates).  Yes, I did try safe video mode and it didn't help at all.

When I updated to ATI drivers for the onboard video, I rebooted and no longer could get a signal with my LCD so I switched back to my CRT and luckily was able to change the resolution to one that wasn't insane.

I then had trouble getting the sound to work for the TV tuner.  To make a long story short, I installed the AlsaMixer to adjust the volume since I couldn't find any other way to adjust volume.

As for problems that I haven't even tried to fix yet, the Forward and Back buttons on my mouse don't behave as expected (I'm not sure what they try to do but they try to open web links or something).  Also, there seems to be quite a few unused buttons on my MCE remote and some of the buttons don't act correctly.  I figure there's something out there that might explain how to map them to something useful but I haven't even looked yet.  _Then there's the problems with the TV signal being horrible (it's super grainy and there's band of distortion at the top of the image) and that the picture gets completely scambled when it gets shrunk into a little box when I bring up the guide._  The guide which doesn't seem to be updating at all but I think that might be because I didn't check XMLTV option when installing Mythbuntu.  It's currently connected to an analog cable signal, if it matters.

So yeah, I'm not terribly thrilled with my first experience with Linux.  Then again, my first experience with Windows was Win 3.11 so I can't say my early Windows experiences were thrilling either.  I'm not too concerned about the problems with poorly mapped buttons but I hope someone can help me figure out the problem with the sound and video.  I underlined the sentence about my problem with video in case you skimmed that last few parts.

---

### Post by Zelgadis on 2007-11-08
I found out that I didn't need the audio cable after all and have it capturing sound directly from the card.

I also noticed that if you scan for channels(before fetching them), the channels get named "Adding Channel" and the only way to get the correct names is to delete all the channels and then fetch.

---

