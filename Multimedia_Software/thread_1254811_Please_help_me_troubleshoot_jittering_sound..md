---
title: "Please help me troubleshoot jittering sound."
date: 2009-08-31
forum: Multimedia Software
---

### Post by zob on 2009-08-31
Hi.

I'm trying to locate an error. You see, I can play sound in perfect quality with following players: VLC, flash in firefox, mpg123.

All other players seem to fail. They all make a terrible jittering og glitches or whatever it's called. That includes: Banshee, Rhythmbox, Miro, quod libet and Totem.

The question then is: What is the difference between these apps in how sound is produces and/or wired?

I suspect an answer to that question would bring me much closer to the problem and be a great help in my troubleshooting.


If anyone is interested I'm on ubuntu 9.04, 2.6.28-15. I have a RME HDSP 9632 sound card (which is kind of tricky). I uninstalled pulseaudio (because it doesn't work with my sound card). The problem started after I tried to install pulseaudio 0.9.15 ('cause I would really like it to work), and then removed it.
Well, we can get to all of this later. But if someone could just answer the question about the difference between the apps that I have described as working and the ones not working, I would be very interested.

By the way. Here's my alsa-info url: [http://www.alsa-project.org/db/?f=887835f2924b3c03d417a5dc9b782c6de4ec5028](http://www.alsa-project.org/db/?f=887835f2924b3c03d417a5dc9b782c6de4ec5028)

---

### Post by zob on 2009-08-31
Let me start myself. Am I right in suspecting that "the bad ones" all use the gstreamer engine - totem, banshee, quod libet, rhythmbox, Miro?

And that VLC, mpg123 and flash sound is produced in another way?

---

### Post by zob on 2009-08-31
Ok. Kind of solved. I booted on an older kernel and all was fine!

I would still like to know what the problem is in the most recent kernel (maybe headers), so if anyone have suggestion it would be great.

But I have sound now.

---

### Post by ApEkV2 on 2009-08-31
I have the same problem (but occurs randomly).  Ever since my upgrade to 9.04 the following stopped working properly: ffmpeg (converting formats), 
flash video is glitchy, totem randomly refuses to play videos and music, synaptic freezes alot more, and startup scripts fail on startup (random occurrence).  
Oh and apache gui freezes on server restart

So far I've heard it's the new X.org or something to the effect.
But I do think you're right about apps that use Gstreamer having problems.

---

### Post by zob on 2009-09-01
I think they are two different problems. Though yours is probably as serious as mine.

If you think they are the same. Try to uninstall pulseaudio. It works for me every time.
Well except last time. But now I found out the it was because I somehow messed up the latest kernel, trying to install pulse, and that changing to an older "pulsevirgin" kernel, solved my problem. 

It is probably still true that it has something to do with gstreamer and maybe the pulse configures gstreamer, if that is the case, I don't know.

I haven't had any video related problems.

But try to uninstall pulse and setup sound to ALSA (it's easy to reinstall). If your sound card is a semipro one, maybe you will have to install alsa-firmware and alsa-firmware-loaders from medibuntu repos.

---

### Post by ApEkV2 on 2009-09-02
both pulseaudio and ALSA work for me, but both still show the same problems sometimes.
right now though i'm currently using ALSA

---

