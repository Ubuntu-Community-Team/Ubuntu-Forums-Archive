---
title: "Keep analog card, IR Blast Digital Converter Box"
date: 2008-10-28
forum: Mythbuntu
---

### Post by ljbeng on 2008-10-28
What if I don't change my Hauppauge analog tuner card.  Can I get the IR Blaster to change the channels on the RCA digital converter box then just record channel 3 all the time in my PVR.  The boxes only cost $10 after the rebate.  

Anyone done this?

---

### Post by newlinux on 2008-10-28
yes, I'm pretty sure you can do this. I've never used coax to capture this way, but I have used S-video to capture from a cable box with an external channel changer with my pvr-150. I imagine it wouldn't be much different.

---

### Post by kbarter on 2008-10-28
I am doing something very similar with an RCA box, the only difference is that I am using svideo for my input.

It should work just fine.

---

### Post by anonymousdog on 2008-10-28
I'm currently doing that with the RCA DTA800, a PVR500, schedules direct, an mceusb blaster, and a pretty standard channel change script.  irrecord did a great job creating the config file I included in /etc/lirc/lircd.conf.  You must set the DTA800 never to go to sleep.  Schedules direct was the hardest part since the channel numbers don't match up with the channel numbers as they should be sent via IR.  You basically have to set up all the chanels manually (e.g. with channel editor) using the xml ID as listed in the SD lineup you create.

---

### Post by ljbeng on 2008-10-30
Are there any step-by-step procedures floating around?  My Ubuntu/Linux knowledge is well below 0.  I hate making changes after I actually get things to look and act correctly with MythTV.  Every time I reboot, the screen size and look on my TV changes.  I just keep rebooting until things get back to normal.


Thanks for the input so far.

---

### Post by mocha on 2009-05-21
I'm have a similar setup and have not been able to get this to work.

My setup:
PVR-250 analog capture card
irblaster.info IRblaster hardware
Comcast PACE DTA box (external tuner box)
Comcast box connected to PVR via coax, signal shows up on channel 3

I tested the hardware with a channel changer script and it works fine from the command line.  In mythtv-setup I said to always start the PVR-250 card on channel 3 and use the channel changer script for tuning.  It doesn't work.  When I go into live TV and type a channel number (I use a keyboard by the way) it usually tunes the Comcast box to channel 50 or channel 225 no matter whay number I type.  It's very strange.

Does this setup not work because I don't use Schedules Direct, and I don't have the channels listed in my guide?  Why can't you just tell the PVR-250 to stay on channel 3, and then any number you enter with the keyboard should be used as input to the channel changer script??  The only thing Myth needs to care about is that it is always on channel 3.

---

### Post by newlinux on 2009-05-21
You don't need schedules direct, but I think you will need to add the channels to your video source. I'm guessing this may be needed so myth can keep track of what was recorded on what channel in the recordings listings and in the DB, but I don't know for sure. But I am pretty sure you need to have the channels you want to have send available in your video source. Your backend logs will have more clues.

---

### Post by mocha on 2009-05-22
Okay, I guess I had some corruption in my PVR-250 channels.  In the channel editor I noticed that there were many duplicate analog channels that were not showing up in the guide.  I deleted them all, connected my cable directly to the PVR-250, re-scanned to get most of the channels back (so I wouldn't have to manually add too many), then manually added the non-analog DTA channels.  Now it works properly.  Thanks.

---

