---
title: "DVD playback 'dragging'"
date: 2008-11-23
forum: Mythbuntu
---

### Post by Ransak on 2008-11-23
Hi,

I recently built a Mythbuntu DVR (8.04) and after some tweaking everything was great until a failed hard drive. I rebuilt the system with a new, much larger hard drive using Mythbuntu again, but this time version 8.10.

Most everything is working as it should be, but this time I'm seeing a problem with DVD playback. It appears that playback 'drags' for lack of a better term. It doesn't pause, but every second or so the picture slows down in a very perceptible way. The audio does stay in sync.

The DVD player I'm using is an IDE drive in an external USB enclosure (both the motherboard and the enclosure are USB 2.0). Aside from the hard drive there hasn't been any hardware changes and it worked great under 8.04.

I've looked through the logs (dmesg, mythfrontend and mythbackend, messages) and I haven't seen any problems at all. Has anyone seen this? Is this a known bug?

Here's a more detailed listing on my hardware if it helps.

P4 2.4Ghz Intel CPU
1TB SATA HDD
2 Hauppauge PVR-150 Tuners
nVidia GeForce FX 6200 (AGP) (using DVI)
P4P800-X Asus Motherboard
Packard Bell remote/receiver (with kernel serial disabled per the guide)
Tivo remote
Soundblaster Live! PCI soundcard
1 GB RAM
Onboard Realtek NIC (1GB)
42" Panasonic plasma TV

---

### Post by dmfrey on 2008-11-23
I am having a similar issue with dvd playback.  The logs tell me it can't access the /dev/dvd resource.  However, I can burn a dvd without any issue.  Upon playback (even one of the dvd's i just created) i get a black screen and then back to the optical menu.

I did as you did, rebuilt on the same hardware I was running 8.04 on with the exception of a larger hard drive.  I have to do some more digging to see if I can't find the problem.

---

### Post by Ransak on 2008-11-23
> **dmfrey said:**
> I am having a similar issue with dvd playback.  The logs tell me it can't access the /dev/dvd resource.  However, I can burn a dvd without any issue.  Upon playback (even one of the dvd's i just created) i get a black screen and then back to the optical menu.

I did as you did, rebuilt on the same hardware I was running 8.04 on with the exception of a larger hard drive.  I have to do some more digging to see if I can't find the problem.

I think by default Mythbuntu uses xine for DVD playback (at least that's how I have it configured, you might want to check your setup to be sure - DVD burning is handled by a different app). I know I had to open up the xine configuration outside of Mythbuntu and enable the advanced interface to point the DVD player to the right device to get it to work. Play with that and see if it helps your issue.

I've been tinkering with the DVD drive speed setting in Mythbuntu but it hasn't made a difference. Has anyone seen 'dragging' while playing a DVD?

---

### Post by SiHa on 2008-11-24
Dumb question time.

You aren't VNC-ing in from a remote machine are you?

I only ask because I had exactly the same issue. I'd forgotten I had left a connection open to a remote machine, whilst I was trying to setup DVD playback, and the frontend clearly couldn't handle the extra overhead of squirting the video down the ethernet at the same time as decoding the DVD.

Strangely this doesn't occur if I VNC in to the same frontend whilst I'm watching Live TV or a recording, only for DVD playback.

---

### Post by dmfrey on 2008-11-24
Ransak,
I think mine is setup to use the Internal DVD Player.  I didn't think about changing it to use xine or mplayer, but I will try that tonight.

SiHa,
I did have vnc open and closed and tried the dvd in both scenarios, but the same result.  When I looked at the logs, i was seeing issues like libdvdnav couldn't find a mapping xml file, etc.

Thanks for the responses.

---

### Post by Archmage on 2008-11-24
> **dmfrey said:**
> Ransak,
I think mine is setup to use the Internal DVD Player.  I didn't think about changing it to use xine or mplayer, but I will try that tonight.

Maybe the internal player is set on playing everything with reduce speed?

If this isn't the case, check out the video drivers.

---

### Post by Ransak on 2008-11-24
No, no VNC sessions. VNC is turned on, but I'm positive nothing is connected.

> **SiHa said:**
> Dumb question time.

You aren't VNC-ing in from a remote machine are you?

I only ask because I had exactly the same issue. I'd forgotten I had left a connection open to a remote machine, whilst I was trying to setup DVD playback, and the frontend clearly couldn't handle the extra overhead of squirting the video down the ethernet at the same time as decoding the DVD.

Strangely this doesn't occur if I VNC in to the same frontend whilst I'm watching Live TV or a recording, only for DVD playback.

---

### Post by dmfrey on 2008-11-24
I switched it to xine for dvd playback.  DVD's play now.  Thanks for the suggestion.

---

