---
title: "Jittery TV"
date: 2009-08-25
forum: Mythbuntu
---

### Post by obrient on 2009-08-25
So here it goes. I have an HP Pavillion 780N that I got from a friend. With the new HD broadcasting I figured it was time to update my MythTV installation anyways. The original was on an older AMD home built with 328MB of RAM.

So I decided to install Mythbuntu since my last Mythbox was Ubuntu and I figured I would save resources by installing with the respun distro. 

So here is my issue. I have 1.80 GHz P4 and a gig of ram in the machine. I have a Hauppauge HVR 1600 and an Nvidia GeForce4 MX2000 all with two hard drives one 250 that I made /home and another 320 that is /.

Basically I go to watch TV and I get jutters and jumps in the video and the audio. I have tried a few of the following; 

added a line to decrease the usage of the video card editing /etc/X11/xorg.conf
```
 Option  "UseEvents" "True"
```

I have increased the virtual memory in the Grub menu to be 
```
vmalloc=512M
```

I changed the Current Video Playback profile to CPU++

And none of these have helped. The video pauses and picks up again. Really frustrating. Oh and I am just recording from the DVB on the HVR 1600 card.

Does anyone have any other suggestions or ideas? I am not new to Ubuntu, but new to Mythbuntu. I am not scared to try things and not a complete newb...

Thanks in advanced.

---

### Post by tgm4883 on 2009-08-25
Your processor isn't fast enough.

From [http://www.mythbuntu.org/requirements](http://www.mythbuntu.org/requirements)
> * A 3.0 Ghz processor is recommended for frontend installations using HD video due to the increased load upon decoding. A lower end processor can be used however with multiple functions on a single machine (ie - Frontend/Backend Install) it is not recommended.

---

### Post by obrient on 2009-08-25
Thanks, just order a new system on New Egg. 3.1 GHZ and 4 Gigs of RAM. No more worries.

---

