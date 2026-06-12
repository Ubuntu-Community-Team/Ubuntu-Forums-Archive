---
title: "TwinView Quad Output questions"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by jnicita on 2006-10-19
I have a couple of questions. Hoping someone could help me understand. Especially if someone has success with (2) Dual Output DVI GeForce 7900 GTX cards.

My confusion is that I have (2) dual head video cards. So I am not sure if using twinview is supposed to get me dual video off of one card, which is not what I would think I want for performance.

Right now I have gotten all the accellerated crap to work on 1 display, I was getting about 5 times the frame rate on the atunnel screensaver using the nvidia driver (I downloaded it from nvidia's site) but in xorg.conf its calling it the 'nvidia' driver.

I also have some experiece with ATI dual head (but single card) configurations using the standard aticonfig --initial=dual-head and the left/right of commands with xinerama = true. Im sure this is confusing me even more, as I keep thinking and applying these pricipals.

Anyways, can I run the 2 cards in SLI mode and DUAL headed monitors? How would I run 1 video per card, how do I know which of the two dvi's per card is the one I should use (I assume a BUS X:Y:a and BUS X:Y:b where a/b would be the two displays per single vidoe card) and maybe X:Y change per card? I havent found any postings or knowledge on this matter. Any help woul dbe apperciated. Right now I have two CRT semi crappy monitors as work connected for attempting to configure this thing (more time at work than at home). But eventually I have two 21" 16:9 lcd monitors at 1600x1050 to hook  up too, I realize I gotta get it working with the crts and I should be able to make the slight modes for diffrent monitors at a later date.

Thanks in advance...

John

---

### Post by jnicita on 2006-10-19
I suppose I should have tested and messed with it a little before posting, but I am still going to need help. I used the Option SLI NO command along with the generic twinview postings from users here. I was getting nowhere at first, but I decided to unplug the monitor from the 2nd nvidia card and connect both monitors to the same 7900gtx and the dual headed (1 virtual screen, I can move windows from left to right) worked instantly. 

I guess, now my question is, how do I get the video fired up on the 2nd 7900gtx, and if I did that, can 1 virtual desktop be used, or is it basically twinview across 2 ouputs of one card, or can you virtual desktop across two distinct diffrent cards.

from my Xorg log:

(II) NVIDIA X Driver  1.0-8762  Mon May 15 14:01:11 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03:00:0
(--) Assigning device section with no busID to primary device
(WW) NVIDIA: No matching Device section for instance (BusID PCI:6:0:0) found
(--) Chipset NVIDIA GPU found

I believe I interpret that to be that I should duplicate all of my Device sections to point to PCI BusID 6:0:0 as well as 03:00:0 and those are my 2 cards?

Guess I'll go mess with that next.

Thanks again.

---

### Post by CatKiller on 2006-10-20
> **jnicita said:**
> I guess, now my question is, how do I get the video fired up on the 2nd 7900gtx, and if I did that, can 1 virtual desktop be used, or is it basically twinview across 2 ouputs of one card, or can you virtual desktop across two distinct diffrent cards.
I'm fairly sure you can have TwinView across two video cards as long as they're both nVidia. It's not an option for me, since mine aren't.
> I believe I interpret that to be that I should duplicate all of my Device sections to point to PCI BusID 6:0:0 as well as 03:00:0 and those are my 2 cards?

You will need the BusID for each card, and probably to define the screen number of each output of each card. That's how it works with multiple Screen definitions anyway. As I said, I don't have much experience of TwinView to know if that's the same.

Good luck, and don't forget to post back with your results so that there is some knowledge on the matter :)

---

### Post by thexaspect on 2006-11-25
Catkiller is correct, you can run twinview across both. Sli will NOT work with dual monitors, that's straight from the nVidia faq. which is totally lame, btw. i only know this because i spent a few days beating my head against the wall trying to figure out why i was stupid. so, the easiest way is to run each card separately, and set twinview up to run across both cards/monitors simultaneously. Unless you actually want to run 4 monitors, in which case, sorry bud, you're on your own. I wont go into twinview, there are plent yof posts that already do that, just search for them, it's not too rough though. good luck =)

---

