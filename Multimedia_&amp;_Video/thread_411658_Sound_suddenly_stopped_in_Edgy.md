---
title: "Sound suddenly stopped in Edgy"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Master Goodheart on 2007-04-17
Hi,

Yay I fixed it. I had the wrong sound drivers selected! How dumb. ;)

I've been using Ubuntu 6.10 for a while now, but recently the sound just suddenly stopped. I checked alsamixer and unmuted everything and turned it up, but nothing worked.

I recently removed some 'un-needed packages' (mostly python ones needed for some games I uninstalled) if that helps. Also I accidentally left some changes to the gmd custom config file (I was wanting to try out compiz but decided not to) which I forgot to remove. It wouldn't start then (i uninstalled xgl which It was pointing to) so I removed the lines I added and it seems to start fine, except sound. 

This is the aplay -l output if it helps:
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

