---
title: "No sound after suspend"
date: 2008-04-27
forum: Multimedia Software
---

### Post by reesje on 2008-04-27
Hi guys

After resinstalling a new version of Ubuntu I have no audio after the computer has been suspended. It worked perfectly in Gutsy. I have a Gigabyte P35 mobo with ALC889a sound controller built in.

Has anybody else seen this? Is there a solution to this?

BR,
René

---

### Post by akniss on 2008-04-27
You're not alone on this one:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/206478](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/206478)

However, it doesn't appear to have gotten too much attention from the developers as of yet.  I think there are many issues with pulseaudio, and so they may be a little overwhelmed right now.

---

### Post by reesje on 2008-05-16
> **akniss said:**
> You're not alone on this one:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/206478](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/206478)

However, it doesn't appear to have gotten too much attention from the developers as of yet.  I think there are many issues with pulseaudio, and so they may be a little overwhelmed right now.
It doesn't seem to be the same problem. What they are experiencing is that after resume the audio is blocked by pulseaudio. When they try to play bac a sound file with e.g. aplay they get an error message. Then they can killall pulseaudio and it works afterwards.

I don't get any error messages when playing a soundfile using aplay, there is just not being output any sound. A killall pulseaudio doesn't make any difference on my machine.

I don't think my problem is related to pulseaudio. Does anybody else have similar problems? It is really anoying, I am not using ubuntu at the moment, since I use suspend all the time.

BR,
René

---

### Post by reesje on 2008-05-20
Solved my problem

By adding options snd-hda-intel model=6stack-dig to my /etc/modprobe.d/alsa-base file, sound works after resume.

BR,

René

---

### Post by swarup on 2008-07-23
I am having the same problem you had, René . I use Ubuntu Hardy and my sound works fine on boot up, but if I put my laptop in standby mode, then upon resuming after that everything works in my computer but the sound. So I tried putting the line you suggest above ("options snd-hda-intel model=6stack-dig") in the alsa-base file, but it didn't make any difference. Any further suggestions or tips?

I found one site which gives a solution for Gutsy, but I felt hesitant to try it in Hardy:

[http://fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/](http://fak3r.com/2008/02/25/howto-sound-after-hibernate-in-linux-gustylenny/)

Does it sound like this site should work for Hardy as well?

---

### Post by reesje on 2008-07-24
Hi!,

Actually my post was not very informative or should I say generic. I you look at this page:[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt") and scroll down to line 770 you can see the options available (and there are many), probably one that fits your laptop. You don't write what make/model you have so I really can't make a surgestion.

BR,
René

---

### Post by swarup on 2008-07-24
Thanks for your reply!
Actually my laptop is a Gateway Solo, from 1999. I looked on line 700, but the only references I found for Gateway laptops were:

> 981		  gateway	Gateway laptops with EAPD control

and

> 1011		  m2-2		Some Gateway MX series laptops
1012		  m6		Some Gateway NX series laptops
1013		  pa6		Gateway NX860 series


I don't know whether any of the above fit my laptop, although somehow I suspect the above references may be to newer laptops than mine. 

At the end of this section, it also mentions:

> 1025	    The model name "genric" is treated as a special case.  When this
1026	    model is given, the driver uses the generic codec parser without
1027	    "codec-patch".  It's sometimes good for testing and debugging.

On the basis of the above, would you be able to make any further suggestion? Or is some further info regarding my computer needed such as chip or motherboard, etc?

Thanks!

Regards,
Swarup

---

### Post by reesje on 2008-07-26
> **swarup said:**
> Thanks for your reply!
On the basis of the above, would you be able to make any further suggestion? Or is some further info regarding my computer needed such as chip or motherboard, etc?

Yes it would definitely help with info on the audio chipset. Other than that you could always do trial and error :-)

BR,
René

---

### Post by gladstone on 2008-08-10
I have the same problem (no sound after suspend) with my EMU-1616m. I had to compile the latest ALSA myself for it to work.

Noticing:

> **reesje said:**
> Solved my problem

By adding options snd-hda-intel model=6stack-dig to my /etc/modprobe.d/alsa-base file, sound works after resume.

BR,

René

do I have to do something similar?

---

