---
title: "[SOLVED] What is needed for watching tv and recording?"
date: 2008-05-06
forum: Mythbuntu
---

### Post by Doc Hoss on 2008-05-06
I will be moving soon, and setting up a media center computer.  After looking at Linux MCE and MythBuntu, it seems that for now at least, Mythbuntu is the solution that would work best for me.  I'm pretty new to Linux, but not scared to get my hands dirty.  I would however, like to keep costs down.

So enough about me...my questions are these: 

1) What would I need to be able to record shows and do all the "fancy" TiVo-style navigation and recording?  Is this functionality built directly into Mythbuntu?  

2) Would I need, for instance, an HDHomeRun and a Hauppauge PVR card, or just one or the other?  I heard a brief mention that the HDHomeRun may not be needed any more due to multirec...?

3) Will other computers on my network need tv cards to display live or recorded tv?

Thanks in advance for any input!  The Ubuntu community continues to impress me!

The Hoss

---

### Post by andrewc6l on 2008-05-06
You really just need a TV capture card (preferably one which can capture HD since things are switching in February) and Mythbuntu. And a fairly fast machine if you're going to playback HD :-)

You might also want a remote... I ended up getting the pcHDTV 5500 capture card and the StreamZap remote; they seem to work pretty well. (Also, you'll want a video card that's compatible with your TV's video in!)

Also, you'll need to subscribe to SchedulesDirect.org or get your TV listings some other way.

In answer to your questions:
1. All that is built into MythTV - and hence into Mythbuntu.

2. Just a capture card; you shouldn't need HDHomeRun to share if you set up the other machines as frontends for MythTV.

3. Any machine that's recording TV will need a TV card. Any machine that's just playing does not.

---

### Post by Doc Hoss on 2008-05-06
Thanks for the info, man!  Your post reminded me of another question though...

What if my cable company (which would likely be Verizon at this point) provided listings?  If they give me a set-top box, it should have a guide feature in that...is there a way to just use that information instead of having to pay another fee?

---

### Post by tgm4883 on 2008-05-06
> **andrewc6l said:**
> You really just need a TV capture card (preferably one which can capture HD since things are switching in February) and Mythbuntu. And a fairly fast machine if you're going to playback HD :-)

You might also want a remote... I ended up getting the pcHDTV 5500 capture card and the StreamZap remote; they seem to work pretty well. (Also, you'll want a video card that's compatible with your TV's video in!)

Also, you'll need to subscribe to SchedulesDirect.org or get your TV listings some other way.

In answer to your questions:
1. All that is built into MythTV - and hence into Mythbuntu.

2. Just a capture card; you shouldn't need HDHomeRun to share if you set up the other machines as frontends for MythTV.

3. Any machine that's recording TV will need a TV card. Any machine that's just playing does not.

The analog changeover only affects broadcast channels, not channels you get from the cable company

> **Doc Hoss said:**
> Thanks for the info, man!  Your post reminded me of another question though...

What if my cable company (which would likely be Verizon at this point) provided listings?  If they give me a set-top box, it should have a guide feature in that...is there a way to just use that information instead of having to pay another fee?

No, you would have to use a service like schedules direct.

Secondly, multirec allows you to record multiple shows with a single tuner (digital only), but there are other factors to consider.  It does depend on how much tv you watch and on what channels.  I would probably still get 2 digital tuners (or a dual digital tuner) if I had digital cable (I have satellite, so that doesn't apply to me)

---

### Post by Doc Hoss on 2008-05-06
Thanks for the info, tgm4883.  

For HD playback and recording, I've been eyeing the Hauppauge cards (particularly the one with two tuners), and the one that andrew mentioned above.  I'm curious...I've got a fairly robust computer (P4 Dual core 3Ghz, 1gig RAM, fast mobo, good hard drives), but it has only one PCI 1x slot that is currently occupied by my sound card (has good sound and optical out, so I don't want to lose it if possible...if it's supported under Linux).  The best Hauppauge cards that I could find take a PCI 1x slot, but they also make a standard PCI version.  Would a standard PCI TV card be sufficient for recording and playing back HD video?  If not, what should I replace?

---

### Post by andrewc6l on 2008-05-06
A PCI capture card is sufficient for recording HD. For playback you don't need a capture card at all - but a good video card.

---

### Post by tgm4883 on 2008-05-06
Which pci card are you looking at getting?

If space is an issue, i'd look at getting the HDHomerun (it connects via ethernet)

---

### Post by Dewey_Oxberger on 2008-05-07
My system is an ABIT AN-M2HD, Athlon X2 BE-2400 Brisbane 2.3GHz Socket AM2 45W Dual-Core, 2 x 1GB DDR2 800 (PC2 6400), Seagate Barracuda 7200.10 250GB (workable but 500G would be better), LITE-ON 20X DVD±R SATA Model LH-20A1S, HDHomeRun, and a 100MBit hub.  All connected via HDMI to a Samsung 40" TV.  I had to run composite audio along with the HDMI to the TV.  Rumor has it the ALSA stuff now supports audio over HDMI on that chipset but it doesn't work for me.

So far I've watched:

a DVD while recording a show.
a show while recording a show.
a recording while it is recording.
a recording while recording another show.

I have not watched a DVD while recording two shows...

No issues of any kind with Mythbuntu 7.10.  (8.04 doesn't install for me).

---

### Post by Doc Hoss on 2008-06-21
Man I forgot I posted this topic...haven't tuned into it in almost 2 months now.  Sorry about that to those of you who were helping me out with this.  

Dewey, sounds similar to the setup I will have once I do some upgrades.  Good to know that it'll be smooth sailing with MythBuntu!

Thanks for all your help guys!  I'll mark this one solved.

---

