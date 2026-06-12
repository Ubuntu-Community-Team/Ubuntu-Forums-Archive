---
title: "Really hopes that the Gnome/Ubuntu Devs ditch PulseAudio"
date: 2010-07-07
forum: Multimedia Software
---

### Post by Rhemat on 2010-07-07
I've been using Ubuntu for a while, and though I've had some annoying problems, I can usually fix them.  I'm really tired of PulseAudio, as it will quit on me after a few days, and then I have to purge and reinstall to get it to work.  I've tried various guides online to fix PA permanently, but they don't work.  I've tried various guides to replace PA, but PA is wedged so tightly into Gnome/Ubuntu that removing it gets rid of sound.
I know others are having this issue, so if a Gnome/Ubuntu developer is reading this, could you please give us the option of what sound server we want to use in the next version?  I would really love to use OSS4 or Alsa in Ubuntu 10.10, not PA.  I don't like fixing PA every few days.

---

### Post by cchhrriiss121212 on 2010-07-07
I don't use pulse but I wouldn't object to it being included in Ubuntu. What I would like to see is the ability to removing it without taking the ubuntu-desktop package with it.
Removing pulse does not "get rid of sound", I have removed pulse on the last 3 releases while still having a functioning ALSA output.

---

### Post by kerry_s on 2010-07-07
you must have some kind of hardware glitch in your sound card.

1. sound works just fine without pulse audio
2. alsa is there, pa enhances it.

---

### Post by Rhemat on 2010-07-07
@Chris

Every time I've removed Pulse, it took audio with it.  I know that it works with Alsa, but I the one time I was able to use something in place of PA, it was only temporary; sound eventually stopped working.

@Kerry_s

I've tried this on two machines, the so the chances of a glitch are slim.

---

### Post by Simian Man on 2010-07-07
> **Rhemat said:**
> I've tried this on two machines, the so the chances of a glitch are slim.

I, and many others, have used Pulseaudio on a hell of a lot more than 2 machines without problems.  Plus the fact that sound still doesn't work for you after removing PA seems to pretty much indicate that PA isn't your problem at all anyway.

---

### Post by kerry_s on 2010-07-08
i found it, i knew there use to be a program to select, but couldn't remember the name.

anyways run-> **gstreamer-properties**
and select "alsa" instead of having it auto.

---

### Post by Lion-Simba on 2010-07-08
I don't use PulseAudio since it was included in Ubuntu.

The reason is - PA don't work with my Creative SB Audigy 5.1 surround sound setup:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/525705](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/525705)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/494099](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/494099)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/515698](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/515698)
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/426788](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/426788)

Removing PA solves all my problems.

Those who use PA with no problems, do you use surround sound with it?

---

### Post by fi2 on 2010-07-08
> **Lion-Simba said:**
> 
Those who use PA with no problems, do you use surround sound with it?

I couldn't, only with ALSA and only after a driver upgrade.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Only then I could configure to surround. 
By the way, after upgrade 5.1 options appeared in Preferences->Sound->Hardware that I had not seen there before.

---

### Post by aeiah on 2010-07-08
maybe im just lucky, but on 4 different computers ive never had sound issues.

---

### Post by Rhemat on 2010-07-08
> I, and many others, have used Pulseaudio on a hell of a lot more than 2 machines without problems. Plus the fact that sound still doesn't work for you after removing PA seems to pretty much indicate that PA isn't your problem at all anyway.

The point is, saying that it was a glitch with the hardware is less likely, considering the fact that the two machines have different audio processors.
As for PA not being the problem, it quits every so often on me giving me a message:

```
ALSA lib pulse.c:229pulse_connect) PulseAudio: Unable to connect: Timeout
```

So I remove PA, but once it is gone, then sound is gone.  If I had more technical knowledge, then I'm sure that I would know how to put something else in PA's place, and make that work.  That is the problem though, seeing that I've had to rely on guides online, and I couldn't get them to work.
You also have to consider that people new to Linux, who start using  Ubuntu, are likely going to have this problem.  If they do, they won't know that PA is busted, they'll just think Linux audio is busted.  This will not help people switch to Linux.
Also, I can't be that unlucky.  This forum alone is full of other people having problems with PA too.  Even if I'm in the minority, the minority still consists of a lot of people.
At least this group might find a solution for some though:
[http://ubuntuforums.org/showthread.php?t=1312624](http://ubuntuforums.org/showthread.php?t=1312624)

---

### Post by Offoffoff on 2010-07-14
Using of PulseAudio is good way to get audio in Ubuntu. But PulseAudio needs be more faster and lighter.

---

### Post by denispnr on 2010-08-07
i don't want to use pulse in the future...
it very bug drv's in ubuntu...
i want to see alsa only because using it i have no one bug with play to the music ore all video content in my pc in different formats

---

