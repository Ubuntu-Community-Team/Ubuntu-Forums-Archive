---
title: "Blocky digital reception during windy weather"
date: 2008-11-17
forum: Mythbuntu
---

### Post by mfearby on 2008-11-17
I have a brand-new Hauppauge Nova-T-500 dual digital tuner with mythbuntu 8.10 that has problems with the digital signal during windy weather. Right now in Tamworth, NSW, it's pretty windy and the visual display is blocky and the audio cuts in and out with loud screeching noises. If I press the DTV buttin on my Samsung Plasma remote to switch to the built-in tuner, it can pick up the same channel without a hitch.

both are connected to the same antenna (via a splitter) but MythTV is the only one that seems to have issues. when this happens, occasionally changing the channel and back again "fixes" it, but it would be nice to tell Myth somehow to increase its tolerance for choppy data or whatnot. it's getting the same signal so theoretically it shouldn't have a problem. I also bought this card because of all the glowing Linux references for it.

---

### Post by fatmonk on 2008-11-17
I may be stating the obvious, here, so my appologies if I am, but you have enabled the LNA on that card via the config file haven't you?

The Nova-T 500 has two seperate tuners and its own internal splitter (passive, I'd guess) so effectively you are getting even less signal into each tuner on the card. The LNAmp may well sort your issues.

-FM

---

### Post by ian dobson on 2008-11-17
Hi,

Have a look here:-

[http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830)

Regards
Ian Dobson

---

### Post by Caps18 on 2008-11-17
I found that one of my wires come loose from my splitter (or from the back of the computer) somehow and it was causing my signal to be a lot less than the antenna hooked directly into the TV's tuner was getting.

---

### Post by mfearby on 2008-11-21
> **fatmonk said:**
> I may be stating the obvious, here, so my appologies if I am, but you have enabled the LNA on that card via the config file haven't you?

You haven't stated the obvious to me :-) I've only been using MythTV for the past few weeks so I'm still figuring it all out.

> **ian dobson said:**
> Have a look here:-

[http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830)

Thanks. I followed the instructions found in that thread and my TV signal now locks on in the low 60% range as opposed to high 30% or low 40%. It's pretty windy outside and my TV signals are nice and calm, now.

Thank you both very much.

Now if I may pose what may be a stupid question... In order to record one channel and watch another, do I have to tune in the channels on both tuners or does MythTV use the channels from one tuner on the other? At the moment I don't think watching one and recording another is working, and I don't really want to run another scan at this point in case I totally mess up what is a near-perfect installation (save for suspend, divx-encoding of recorded TV, and getting a samba share to work in Mythbuntu without getting bizarre ntfs tree disconnect errors on my other Linux box, which is Mandriva 2008.1).

---

