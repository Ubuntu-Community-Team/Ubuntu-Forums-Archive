---
title: "Reactive EIT - or dynamic rescheduling or recordings"
date: 2008-12-25
forum: Mythbuntu
---

### Post by Modiford on 2008-12-25
Hello all,

I have recently been hacked to death by my partner for MythTV not recording the end of her EastEnders because, in true time tested ways, the BBC will oftenrun late.  This has happened a number of times, more so now the Christmas scheduling is upon us.

Either MythTV (in my case, on Mythbuntu, I think 8.10, with the Hauppauge 4000-Lite custom kernel patch for Freesat use) does not keep an eye on the current "now and next" EIT / EPG information and reschedule the recordings or I am missing a setting that allows it to do so.

I have searched the four corners of the internet for information and found references to an EITpf (or EITp/f) feature but not a lot documented about it.

If anyone could be so kind as to either confirm whether this is a feature or not or offer a reference to another source so that I can research into this further I would be very grateful.

Many thanks,

Have a Merry Christmas and a Happy New Year!

Modiford.

---

### Post by ian dobson on 2008-12-26
Hi,

The this/next EPG is a real pain in the butt. My cable provider sends out BBC1,2,3,4,HD but only with this/next EPG.

The EPG is OK as long a your not recording anything but as soon as you start recording from a different multiplex myth can read the EPG data from other multiplexes anymore.

To get round the problem I've written a small XMLTV grabber that grabs the channels I want from bleb.org, changes the XMLTV ID's and generally fixes up the data so that mythfilldatabase can use.

The actual download from the internet is only about 300Kb and takes less than 15seconds. If you want I'll bang up a copy of the script to the forum for you to play with.

To go back to your original problem just change to recording rules so that it records an extra "few" minutes at the end of the recording. I've got my system setup to start recording 5 minutes early and end 8minutes late.

Regards
Ian Dobson

---

