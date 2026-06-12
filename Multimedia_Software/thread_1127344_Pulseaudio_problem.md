---
title: "Pulseaudio problem"
date: 2009-04-16
forum: Multimedia Software
---

### Post by steviefordi on 2009-04-16
When an application tries to play sound, pulseaudio always pushes the stream to the wrong output device. Once I move the stream to the correct output device using 'PA volume control' the application behaves. From then on it will always play to the correct output device.

I have the correct output device selected as default in the volume control, so why isn't this being used as default? And how can I sort it out?

---

### Post by markbuntu on 2009-04-16
If you played the app on the wrong device once then that is what pulse remembers. The default setting is strictly for new applications so it is somewhat misnamed. This has all been changed considerably in the new pulseaudio, 0.9.15 and the new pavucontrol that comes with it. It has just been released.

---

### Post by steviefordi on 2009-04-16
Thanks for the reply Gambitt. When I entered pulseaudio -k I got the following error:

```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: main.c: Failed to kill daemon.

```
I think I've seen this in my system log or kernel log before, any ideas what to do?

markbuntu - I was hoping you'd see my thread as you are clearly the most knowledgable person on pulseaudio in these forums. To clarify for you - new apps, that have never attempted to play a sound, play to the wrong device.

---

### Post by markbuntu on 2009-04-17
Well, if you are not set up like the link below, that can still happen.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You can always post in one of my threads, I check them as often as I can. I usually just make a simultaneous sink and push all the apps to that. Then it doesn't matter where I am listening.

---

### Post by steviefordi on 2009-04-20
Thanks for the reply markbuntu. I'm pretty sure I followed that setup to get my audio going. I'll go through it again to check that I didn't miss anything.

> I usually just make a simultaneous sink and push all the apps to that

How do you do that? Is it documented somewhere?

---

### Post by markbuntu on 2009-04-20
It is in that guide I linked to but you can just click on the padevchooser/configure local sound server/simultaneous output and click the little box in that window. This will put a virtual sink called simultaneous output....... in output devices that you can use like any other sink. I use it a lot myself.

---

### Post by steviefordi on 2009-04-21
Thanks again markbuntu. Just one last question if you can spare me the time...

The 'wrong sink' that pulseaudio sends sound to is actually the PC Speaker. This results in a crackling noise rather than any recognisable sound coming from my laptop. The only way I know to re-direct to the correct sink is through pointing and clicking on the play tab of padevchooser whilst the sound is playing.

If I can't re-direct the sound when it is playing - for instance during the log-in process, or when it's a very short sound and I'm not quick enough - how else can I re-direct it?

---

### Post by markbuntu on 2009-04-21
There is a way top disable the pc speaker, maybe in bios? I am not sure.

---

### Post by steviefordi on 2009-04-21
I've gotten around it by muting the PC Speaker. Thanks for all your help, both here and in your howto threads.

---

