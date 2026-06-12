---
title: "Debugging firewire connection to SA8300HDC (p2p and bcast fail 100%)"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Vchat20 on 2008-09-23
Here's the lowdown: I have a cable set-top here. A Scientific Atlanta 8300HDC running Mystro. Both available firewire ports are enabled as far as I can tell (box diagnostics list the firestb module as loaded and running anyway). Recently got a VIA based generic firewire PC card for my laptop dual booting XP SP3 and ubuntu.

I've been trying to find some way to get recordings to work and so far other resources for help seem to be nil so I figured I'd look it up here.

On the XP side it's a quick and painless diagnoses, but vague at best. I only get two unknown devices and no tuner or panel devices as covered for the installation of the only avilable drivers for windows operation. None of the capture programs can see either unknown device as a valid capture source.

On ubuntu, plugreport shows a blank node and a valid node as expected. The supplied firewire testing script in the wiki fails every time on both p2p and broadcast tests. I haven't tried myth yet as I wanted to wait to see if this setup was gonna work first since it would be my only capture device. But I have pulled a couple related firewire scripts from the myth source and tried them on their own and still cannot get anywhere. mencoder and VLC get nowhere either.

I'm half assuming this means that the firewire port's are disabled in some fashion, but just wanted to see if anyone else could possibly confirm it or inform me of another route to try. Only thing I haven't tried yet is checking again on a local network channel either live or recorded. But I kinda figured that PC-side diagnostics would show the same regardless of channel, just any recordings made over firewire would vary depending on content.

---

### Post by Vchat20 on 2008-09-24
Well, tried again earlier with mythprime which from the sounds of it is a defacto test for this and it even failed 100% every time.

Tried it both on a local channel live, recorded, a (possibly) encrypted channel, live and recorded, and even a music channel. Nothing solved the problem.

---

### Post by majoridiot on 2008-09-26
> **Vchat20 said:**
> Well, tried again earlier with mythprime which from the sounds of it is a defacto test for this and it even failed 100% every time.

Tried it both on a local channel live, recorded, a (possibly) encrypted channel, live and recorded, and even a music channel. Nothing solved the problem.

the SA8300 is pretty much useless for anything firewire related.  every one i have
experience with outputs garbage transport streams- which is why firewire priming
and capture fail.

*to the best of my knowledge* the only way to record from the 8300 is capturing
material pre-recorded to its dvr.  capturing livetv is not a possibility.

thank your local cable operator for this.  the firmware exists for firewire output
but they will not implement it... which is against federal law in the US, by
the way...

sorry, dude.  yer outta luck with that stb. :(

---

### Post by dsbw on 2008-12-13
[I]to the best of my knowledge the only way to record from the 8300 is capturing material pre-recorded to its dvr. capturing livetv is not a possibility.
[/I]

What about the usual analog stuff: S-Video, etc?

---

### Post by majoridiot on 2008-12-13
> **dsbw said:**
> [I]to the best of my knowledge the only way to record from the 8300 is capturing material pre-recorded to its dvr. capturing livetv is not a possibility.
[/I]

What about the usual analog stuff: S-Video, etc?

absolutely.  you can use firewire to change the channel and capture with the analog capture card of your choice.

---

### Post by bmwman on 2008-12-16
> **majoridiot said:**
> absolutely.  you can use firewire to change the channel and capture with the analog capture card of your choice.

Can you point us to a good How_To for using the firewire to change channel only and record with HDhomeRun or whatever else tuner. I assume the tuner supposed to stay on channel 3 and I'm not sure how to do that.

Thank you.

---

### Post by majoridiot on 2008-12-17
> **bmwman said:**
> Can you point us to a good How_To for using the firewire to change channel only and record with HDhomeRun or whatever else tuner. I assume the tuner supposed to stay on channel 3 and I'm not sure how to do that.

Thank you.

as far as firewire channel changing (in general) goes, all you need to do is use *mythchanger* to change
the stb channel.  source with README can be found here:

[https://wiki.ubuntu.com/majoridiot](https://wiki.ubuntu.com/majoridiot)

i am not at all familiar with the HDHomeRun, so i can not give you any specific advice.  however, you can find
more info on setting it up here:

[http://mythtv.org/wiki/index.php/Silicondust_HDHomeRun](http://mythtv.org/wiki/index.php/Silicondust_HDHomeRun)

OTA antenna info can be found here:

[http://mythtv.org/wiki/index.php/OTA_Antenna_Tuning](http://mythtv.org/wiki/index.php/OTA_Antenna_Tuning)

i am sure there is also a lot of other info available in the mythbuntu wiki and forums as well as elsewhere.
you might also consider other options, such as the hauppauge 1212 (not sure the status of this), as well as
capturing via s-video or video out, etc. with an SD capture card.

good luck!

---

