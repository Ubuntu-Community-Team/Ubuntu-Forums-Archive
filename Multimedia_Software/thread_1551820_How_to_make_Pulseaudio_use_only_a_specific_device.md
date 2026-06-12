---
title: "How to make Pulseaudio use only a specific device"
date: 2010-08-12
forum: Multimedia Software
---

### Post by jabeavers on 2010-08-12
I am trying to setup a complex audio system, but I won't bore you with the details (unless you ask). Basically, I want to have pulseaudio only use one specific device and ignore the rest of the devices. I've searched google and found nothing. I'm sure it is a simple answer, so if you don't want to tell me how to do it, then at least point me to an article that explains it.

Thanks,
John

---

### Post by philetus on 2010-08-12
Why just one device?You going to use ALSA for everything else?
How is Pulse audio in 10.04?
Is Pulse audio already dead?

---

### Post by jabeavers on 2010-08-12
Yes, I will have the outputs of the other devices going into a mixing console, but I want to have one that can be shared with the system for system sounds or what not. I will use alsa for the others, or jack for my multichannel card and low latency recording.

I don't know how pulse audio is in 10.04 yet, I'm still trying to figure it out: I'm a complete noob with audio in linux.

---

### Post by lidex on 2010-08-14
It can get rather involved, but it looks like you want to swim in the deep end. A lot of info here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by jabeavers on 2010-08-14
Thanks for the link. I seem to have had some success, but not with what I want. The pulseaudio server plays great, but it still sees my other sound card. I would like it to not even see it, although I guess it would work, as is, if pa never uses the second card. I read through many of the links in the guide, but did not see anything exactly pertaining to what I want. Here's a portion of my default.pa file:

#!/usr/bin/pulseaudio -nF

.fail

load-module module-alsa-sink device=hw:0,0 sink_name=output
set-default-sink output
disallow-module-loading true

I used disallow-module-loading so that it wouldn't load anything except the intel card, but it's still loading my M-Audio card. I disabled the udev-detect so it wouldn't detect stuff, but it still seems to be loading modules I told it not to.

I basically want to blacklist my M-Audio card from pulseaudio. Any help would be appreciated.

---

### Post by lidex on 2010-08-15
Swimming around in the back of my brain is a thought that you could route all the audio for the delta to a specific sink that is then routed to the delta? Or maybe set delta as default device and route what you want pulse to use to the secondary device? What do you think?

---

### Post by jabeavers on 2010-08-15
Well, I think I've got it setup pretty close to what I want. I split my onboard outs to be independant as separate pcm's. This works fine. I will have those outs sent to an actual mixing board (which I also use for recording with the delta). I want to have system sounds (controlled by pulse) on one slider, then my video editing software on a separate slider and vlc or other media players on a different slider. The delta (ie, home studio recording) will be controlled by jackd, so I want it out of the pulseaudio loop. I know I can do all of this via the pulseaudio mixer, but I have a mixing console, so I want to use it. Basically, I'm stuck at this point trying to make pulse only see / control the pcm for system sounds & background music.

Does this make sense??

---

### Post by lidex on 2010-08-15
Hmm. Maybe these will help. (Have a hard time getting my head around these types of configurations as I've never used them personally.):
[http://ubuntuforums.org/showthread.php?t=884643](http://ubuntuforums.org/showthread.php?t=884643)
[http://ubuntuforums.org/showthread.php?t=1528503](http://ubuntuforums.org/showthread.php?t=1528503)
[http://ubuntuforums.org/showthread.php?t=1062120](http://ubuntuforums.org/showthread.php?t=1062120)
[http://pulseaudio.org/wiki/Modules#JACKConnectivity](http://pulseaudio.org/wiki/Modules#JACKConnectivity)
[http://ubuntuforums.org/showthread.php?t=1539564](http://ubuntuforums.org/showthread.php?t=1539564)

---

### Post by jabeavers on 2010-08-16
I read those links, thanks. But, i'm not trying to connect pulse and jack, I'm trying to keep them separate. What I really need is for pulse to grab a single pcm on my soundcard and ignore the rest. I have asked markbuntu on another thread, though, so if he gets my question answered, I will post the solution here. Unless you can think of something else, thanks for your help and I'll keep you posted.

---

### Post by jabeavers on 2010-08-18
I was actually able to do what I wanted with asound.conf and alsa. I have disabled pa and have my sound working like I want it! It's so cool. I have split the outputs on my onboard card (hda-intel) to four independant devices. One of those is set as the default and firefox/flash uses that one without grabing the entire card (yay). I have vlc on the next set of outs, kdenlive on the next, and a fourth with nothing on it right yet. These outputs go into my mixing board so I can leave the background audio going while editing video, etc, and just turn it down manually when I don't need it.

Then, my delta is controlled by jack and I can record through it while listening to source via the other card, thus creating separate tracks that I can edit individually. It's so cool!!! I'm excited to get to try it out. Thanks for your help.

---

### Post by lidex on 2010-08-19
Nice work. I'll bookmark this thread in case I run into someone with similar needs.

---

### Post by sdaau on 2012-04-12
Hi all, 

First of all, thanks for this awesome thread!

> **jabeavers said:**
> 
I basically want to blacklist my M-Audio card from pulseaudio. Any help would be appreciated.

> **jabeavers said:**
> Basically, I'm stuck at this point trying to make pulse only see / control the pcm for system sounds & background music.


I basically have the same problem - I too want to have pulseaudio ignore a specific device. 

Thanks to the documentation in this thread, I didn't go into trying to change configuration files, given that such an approach didn't result with anything useful for the OP (at least not in respect to pulseaudio). 

So I looked a bit further, and I found this - which seems to be the answer for ignoring/blacklisting modules/drives from pulseaudio: 

[Re: Pulseaudio config problem](http://www.mail-archive.com/fedora-list@redhat.com/msg51197.html):
[quote=http://www.mail-archive.com/fedora-list@redhat.com/msg51197.html]
... it was the manager that allowed me to turn devices off in pulseaudio.  It was
the PulseAudio Volume Control.

Applications -> Sound and Video -> PulseAudio Volume Control

First select the Output Devices tab and make sure the drop down in the
lower right corner is set to All output devices.
Then select the Configuration tab.  If you right click on the device you
want Pulse to ignore, at the bottom of the menu is an off selection.
Pulse won't know about that device if you turn it off.
[/quote]

Note that the PulseAudio Volume Control is called ```
pavucontrol
``` - and by following the above instruction, I could get a particular driver to be ignored by setting it to "Off" in pavucontrol - proof is that I can insmod/rmmod the driver multiple times without pulseaudio getting a lock on it - even if pulseaudio recognizes the driver as loaded (and indeed, shows it in pavucontrol when it is). 

Well, hope this helps someone...

Cheers!

---

