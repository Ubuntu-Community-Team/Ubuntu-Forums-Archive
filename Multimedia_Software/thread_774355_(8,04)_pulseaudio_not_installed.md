---
title: "(8,04) pulseaudio not installed"
date: 2008-04-29
forum: Multimedia Software
---

### Post by DkkD on 2008-04-29
I have checked Xubuntu 8.04 release notes and it says that it comes with pulseaudio preinstalled, but my Xubuntu installation doesn't have any pulseaudio packages installed. I searched for "pulse" in Synaptic and the only installed packages are: libgsm1 and libpulse0.

That alone wouldn't bother me, but I can't get the sound working as I would like. When I first installed it the sound was working, but only on 2 speakers. I tried to enable 5.1 by editing "/etc/pulse/daemon.conf" but the file wasn't there (that's when I found out there was no pulseaudio installation at all). So, I tried to edit .asoundrc file. But there also was no .asoundrc file, so I created it. 

Now I do get 5.1 sound in media players, but I don't get any sound in firefox (for example, youtube videos have no sound). I have closed all other software that might be using the sound card, so that's not the issue.

I have no idea why is that so, if anyone has any ideas that would be great.

Thanks!

---

### Post by lancern on 2008-04-29
> **DkkD said:**
> I searched for "pulse" in Synaptic and the only installed packages are: libgsm1 and libpulse0

Did you enable 3rd party rebos in Synaptic settings..I have seen the pulseaudio package in mine..I to use xubuntu..all my sound is working and im scared to install it :p

---

### Post by DkkD on 2008-04-29
Yes I did, I can see pulseaudio package in Synaptic, it just isn't installed. Can you get sound in more applications at the same time?

---

### Post by lancern on 2008-04-29
yes tried it just now with rhythmbox and gnome mplayer and could hear both..but just to be clear I did not install pulseaudio..I used upgrade manager to upgrade from 7.10 to 8.04..and my sound just worked..

my soundcard is an old pci SBL xgamer card..

---

### Post by DkkD on 2008-04-29
Yes, I see. I have just removed my .asoundrc file and after restart I can hear sound in firefox and get more applications to play sound at the same time. But now on only 2 speakers.

I don't get it, where else can I configure sound in xubuntu? There is no */etc/pulse/daemon.conf* file and *.asoundrc* just messes things up. I didn't have those problems in Ubuntu (8.04).

---

### Post by Jerdsy on 2008-04-30
I've also just upgraded to 8.04 in anticipation of the Pulse Audio mixer.  In doing a big of research, it seems that PulseAudio is NOT a feature of xubuntu 8.04 hardy.  
See this link:
[http://ubuntuforums.org/showthread.php?p=4793090](http://ubuntuforums.org/showthread.php?p=4793090)


In my case, none of the PulseAudio preferences or libraries were installed.  (there was one service related to Pulse installed.)  In any case, I used the directions here, installed everything via Synaptic and it still doesn't work. 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Audio does still work.  But Pulse is not active and will not allow a connection.  The post above indicates that it can be made to work, but not persistently at user level.  

Does anyone know how to get Pulse working under XFCE?

Thanks

---

### Post by ivotron on 2008-05-29
> **Jerdsy said:**
> I've also just upgraded to 8.04 in anticipation of the Pulse Audio mixer.  In doing a big of research, it seems that PulseAudio is NOT a feature of xubuntu 8.04 hardy.  
See this link:
[http://ubuntuforums.org/showthread.php?p=4793090](http://ubuntuforums.org/showthread.php?p=4793090)


In my case, none of the PulseAudio preferences or libraries were installed.  (there was one service related to Pulse installed.)  In any case, I used the directions here, installed everything via Synaptic and it still doesn't work. 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Audio does still work.  But Pulse is not active and will not allow a connection.  The post above indicates that it can be made to work, but not persistently at user level.  

Does anyone know how to get Pulse working under XFCE?

Thanks

Follow the instructions found [here]("https://wiki.ubuntu.com/PulseAudio"). After that you'll have the pulse server configured and every app should use it without any problem, unless it needs to be specifically configured to use it (like Exaile).

But still there's the issue on how to run it automatically without needing to run it manually. The packages installed (the ones you installed based on the link provided above) add an entry to the list of autostarted programs. This loads a module to let a user use pulse each time that starts a session, however, by default, the pulse audio server isn't configured to run as a daemon (or service), neither to allow users to load modules. To change this, open the file /etc/default/pulseaudio and change this line:

PULSEAUDIO_SYSTEM_START=0

by putting 1 instead of 0. Do the same for the remaining line (DISALLOW_MODULE_LOADING=1) but replace 1 with 0.

Save and close and restart and you should see (ps aux | grep pulse) that pulse is running.

If you use skype, you'll experience difficulties when trying to use it. [This link]("http://www.pulseaudio.org/wiki/PerfectSetup#Skypehttp://www.pulseaudio.org/wiki/PerfectSetup#Skype") provides a workaround for it.

Cheers

---

