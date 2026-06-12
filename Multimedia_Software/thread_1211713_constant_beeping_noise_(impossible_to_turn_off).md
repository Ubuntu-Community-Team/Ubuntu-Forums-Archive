---
title: "constant beeping noise (impossible to turn off)"
date: 2009-07-12
forum: Multimedia Software
---

### Post by manualqr on 2009-07-12
Hello, I just installed Mint Linux 7 and upgraded. I should be using most of the same packages as many of you. I've installed on a brand new Hp dv4t laptop, and used the x86_64 bit version.

My issue is that after I give GDM my password to log in, a beeping noise starts. It's impossible to turn off and blocks out all other audio (e.g: no sound in videos). I've blacklisted the pcspkr module and turned off the GDM log-in sound - but that hasn't helped. The sound is like this: 'bip bip bip bip bip bip bip' ... ad infinitum. Sometimes it gets softer, and sometimes louder. If I press the mute button on my laptop, it stops - though (so I don't think it's a hard drive spin issue).

If anyone has experienced something similar, could you please help? I would greatly appreciate it.

---

### Post by manualqr on 2009-07-13
It turns out this beeping noise only starts when I try to play audio. I rebooted after disabling the GDM login noise, and all was well.. but when I tried to watch a video the beeping sound started again. Watching the video is made even trickier because flash is so sluggish..

Could this be a x86_64 issue?

edit:
the sound when watching youtube videos is more abrasive, imagine a chainsaw (except not quite as loud)

---

### Post by igorzwx on 2009-07-13
Do you have PulseAudio installed?

---

### Post by manualqr on 2009-07-13
Yes, I do.
I tried following this guide: [http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437), but it had no effect. I re-installed pulseaudio.

---

### Post by igorzwx on 2009-07-13
read this story:
[http://ubuntuforums.org/showthread.php?t=1207636](http://ubuntuforums.org/showthread.php?t=1207636)
[http://ubuntuforums.org/showthread.php?t=1207636&page=2](http://ubuntuforums.org/showthread.php?t=1207636&page=2)

---

### Post by manualqr on 2009-07-13
I followed the wiki guide on OpenSound. I blacklisted ALSA, purged pulseaudio, and installed OSS4. I also used the 'workaround' to add OSS4 emulation to alsa programs. I guess it sort of worked - the beeping noise is gone but I also have no sound!

btw: I checked to see if my hardware is supported by OSS4. It is. Makes me wonder why sound was working perfectly in Fedora 11 :(..

---

### Post by igorzwx on 2009-07-13
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Additional Support**

 If you have OSS installed properly, but still have issues, the OpenSound project has free user support forums and an IRC channel. Be sure to include the output from these commands so the experts don't have to prompt you for them 
ossmix
ossinfo -v3Also, you'll want to note if the osstest command works and plays sound. 
 
**Forums**

 You can make a thread on [the OpenSound user forums]("http://www.4front-tech.com/forum/index.php").

---

### Post by manualqr on 2009-07-13
I just got it all working with soundcheck's script :D:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by igorzwx on 2009-07-13
My congratulations!

---

### Post by manualqr on 2009-07-14
thanks!

(and by the way, could someone tell me how to properly mark a thread as solved?)

---

### Post by igorzwx on 2009-07-14
Hi!

I have already recommended your solution to several users.

It might be nice, perhaps, if you would add a small howto to it.

Best,
Igor

---

### Post by manualqr on 2009-07-15
I don't take any credit at all for that solution - it was all soundcheck's idea. In fact, he has a very detailed howto himself:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

thanks

---

