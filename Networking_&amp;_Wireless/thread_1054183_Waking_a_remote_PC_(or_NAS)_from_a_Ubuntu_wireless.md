---
title: "Waking a remote PC (or NAS) from a Ubuntu wireless laptop"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by trgz on 2009-01-29
The scenario:
Dell Inspiron 2200 with Edimax wireless card running Intrepid with Spotify (under Wine) and Songbird and an ATI Remote Wonder - forms part of the hi-fi. Would like to be able to switch on laptop with just the one button and not need to do any tweaking to get connected to mp3's on another device that may need to be woken up.
So far I've added lines to 'interfaces' (in 'etc/network') to get the card to connect at the correct speed (was only 1Mbps!) and to connect/remount a Windows share where my music currently resides (using 'post-up sudo mount -a'). I've also got Spotify & Songbird auto-starting courtesy of the startup preferences tool. The ATI remote works straight out of the box but Spotify doesn't like the multimedia keys as yet. The whole setup works well when up and running (VGA link to TV, headphone out to hi-fi) and it's doing a great job of getting me into using Linux. 

My problem:
I can wake the remote desktop using a wakeonlan command from the terminal but I can't seem to be able to add it into the interfaces file so the laptop runs the command when it boots and hence wakes the remote desktop. I'm guessing I could do with a pause somewhere in the whole process but how? or am I expecting too much.

FYI The mp3's on the desktop is an interim measure which I hope to replace with a NAS but I'll want to keep the NAS powered down and wake it up only when required (and shut it down after).
(I'll also need to figure out how to shut the remote device down, but that's another day!)

---

