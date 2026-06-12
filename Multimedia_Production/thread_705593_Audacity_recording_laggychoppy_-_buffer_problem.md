---
title: "Audacity recording laggy/choppy - buffer problem?"
date: 2008-02-23
forum: Multimedia Production
---

### Post by cowzkull on 2008-02-23
I'm running Ubuntu 7.10 on an Acer Extensa 5220 with ALSA 1.0.16 driving hda-intel and a generic usb microphone.
$cat /proc/asound/modules
 0 snd_hda_intel 
 1 snd_usb_audio <-- C-Media USB Audio Device

My problem is that when I'm recording in Audacity the recording ends up being choppy/laggy even when recording the first track (with the usb mic.).
When I record the second track the lagging gets even worse. I been looking and looking but nothing seems to solve the problem.
Mostly the recordings sound like some kind of buffer underrun but I'm not sure.

Any ideas?:confused:

Edit: I used the same hardware in Windows Vista with Cool Edit Pro with no problems at all...

---

### Post by SmallIsland on 2008-02-24
Try using Audacity in combination with Jack and Qjackctl...

From experience, the portaudio/alsa interface in Audacity only works with a few hardware combinations.

As an alternative to Audacity I would recommend Traverso...

---

### Post by nlz on 2008-02-24
If you are already using Jack, it could be Xruns.. Check the message box..

---

### Post by cowzkull on 2008-02-24
Hi, thanks for the advice guys.

I've tried to get JACK up and running for a while now but have pretty much given up but I usually always end up with errors like these:

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:1|256|2|44100|1|2|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 256 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
**** alsa_pcm: xrun of at least 1203837457137.664 msecs
**** alsa_pcm: xrun of at least 1203837457137.664 msecs
... and so on infinitely.

And since I havent been able to get jack running I have no how I could use it with audacity. How does et work on a user level? How would a normal user set up jack to make a simple recording and play it through the speakers?

I'll look into Traverso.

Thanks again

---

### Post by nlz on 2008-02-25
please look around on the forum, a lot of things were said and done about JACK, als by me..

You just have to play around with the frame/period, sample rate and the buffer. In the right below corner of settings in qjackctl is mentioned how much latency you have with JACK, start high and work your way down until you get xruns again.

You can use port audio. If you have JACK and audacity running, select jack in the preferences..

---

### Post by cowzkull on 2008-02-27
Thank you so much!
After all, all it took was a bit of fiddling around with JACK.
Ended up with a latency of 34,8 Msec.
It'll do:)

---

### Post by nlz on 2008-02-29
34 msecs is too much! What are your system specs? Almost everyone should be able to make it <15 msec, it's asport ;):guitar:

---

### Post by cowzkull on 2008-03-05
I thought that was a bit much.
Running with 1G of RAM and Intel Celeron 530 @ 1,73Ghz...1,8Ghz 
Should that suffice?

---

### Post by nlz on 2008-03-05
i'm running almost the same specs on my ASUS s96j, 1 GB ram and 1,8 GHZ processor (dual core)

i have 11,6 msecs latency, but then i run about 10 heavy audioprograms on it for live sets, and then i can't have xruns.

but i get as far down as 4 or 5 msecs for normal audio things.

you can check my setting in the attached screenshot

Ow yeah, forgot to say: i use the realtime kernel, if you want to get low latency, you should too! The kernel is really nice, and your system can easily handle it. Just install it and edit rtlimits, and you're good to go!

---

### Post by cowzkull on 2008-03-10
Thank you very much for the tips:) I wondered why I had to install a new kernel with the Ubuntu studio upgrade.. I'm running 2.6.22-14-rt and have been all the way through this problem.

I believe my problem must be with the rtlimits since I'm still having trouble with high latency and a few xruns here and there.

I usually also get a lot of these:
delay of 7857.000 usecs exceeds estimated spare time of 2752.000; restart ...

or similar.

Where do I edit the limits?

Best regards

Edit: I guess the limits you're talking about are the ones in /etc/security/limits.conf but they're already set. rtprio 99 and the memory one to 512000 .. Anything else I should set?

---

### Post by kapello on 2008-03-10
If you don't need to monitor the recording live, as you are recording, there is an easy solution.

In Audacity preferences, set Latency to for example 100ms, then set Latency Correction to *minus* 100ms. 

Works a treat for me.

PS This works whether or not you are using Jack. So you could just ignore Jack, run Audacity on its own, and use this Latency correction solution.

---

### Post by nlz on 2008-03-10
@ cowzkull 
you're probably not running JACK in realtime mode. You can only do that if you run JACK as root (sudo qjackctl) or if you edited rtlimits.conf.

Just google a bit on how you have to get access to JACK as non-root. But first check to be sure if you can run JACK in rt if you run it as root (but don't get yourself accustomed to it, it's dangerous).

---

### Post by cowzkull on 2008-03-11
Arh. Of course!
I have edited limits.conf, but I havent tried running as root.

Two minutes later.

Tried running as root but still get xruns with the settings in the attachment.

---

### Post by nlz on 2008-03-11
stop forcing 16 bit, it also gives me xruns if i use it.

---

### Post by cowzkull on 2008-03-12
Doesn't make much of a difference for me but seems to work better when I force 16bit.. :/

---

