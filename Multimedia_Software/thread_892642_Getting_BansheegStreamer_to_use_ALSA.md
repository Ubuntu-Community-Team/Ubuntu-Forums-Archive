---
title: "Getting Banshee/gStreamer to use ALSA"
date: 2008-08-17
forum: Multimedia Software
---

### Post by jvincent08 on 2008-08-17
Ok, like many before me, I started out having issues with getting multiple programs to have access to sound. After searching around I found that only applications configured to use ALSA can have access at the same time. Now, Xine (and I'm assuming any application that uses it) and Firefox (Flash) can both play sound at the same time. But I still can't Banshee to cooperate, as I can't find any options to specify which sound architecture to use. If I open Banshee first, neither Firefox nor Xine can play. I've searched many threads on this and the only thing I can find isn't Banshee-specific. I've only found that using aoss is supposed to make any application use alsa, but "aoss banshee" doesn't seem to make a bit of difference (nor does "aoss firefox"). 

I'm still new to Linux and I'm struggling to figure out the technical aspects behind the way sound works in it. So far I understand that the ideal order is something like this..

Application speaks to framework. Framework speaks to archictecture. Architecture speaks to sound card driver. 

The way I understand it, if two applications do that, they can both have sound access simultaneously. 

So I'm assuming that gStreamer is skipping over the architecture and speaking directly to the driver, or its still using OSS (which can only handle single streams, right?).

Please correct me if I'm wrong in any of this. I'm still learning :)



Update: [This]("http://ubuntuforums.org/showthread.php?t=885437") seems to have solved the problem. Now, Xine, Banshee, and Firefox can all play sounds at the same time. I wasn't aware that this was related to PulseAudio.. I don't even know what PulseAudio is *shrug*..
But if there are any other tips, or if I still need correcting on anything above, don't hesitate to reply.

---

