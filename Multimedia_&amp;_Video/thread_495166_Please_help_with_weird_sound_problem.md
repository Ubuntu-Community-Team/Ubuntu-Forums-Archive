---
title: "Please help with weird sound problem"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by margaf77 on 2007-07-07
I had working sound in all multimedia apps (xmms, totem, rhythmbox, amarok and vlc) now I only get sound from amarok and vlc. 

I have tried purging the drivers with info from this link [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and reinstalling them but still the problem persists. I tried typing alsamixer and got this error:

```

ALSA lib control.c:875:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

In xmms I get an error box that says:

Couldn't open audio.

Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard.


What could be blocking the sound card? If this is it at all how would I check?

---

### Post by margaf77 on 2007-07-08
Also when I use gedit from the command prompt to edit I get the following. I also included the command I used (nothing special just figured Id put it there).


[email]XXXX@XXXX-desktop:~/.moz[/email]]lla-thunderbird$ gedit profiles.ini

ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
ALSA lib pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so



Ive gotten sound to work in the apps from the OP by changing the sound from alsa to oss in everything in System > Pref > Sound but I still get the above error and when I login I get no startup sounds except the drum sound when the username screen comes up, but not the sound I used to get after typing my username /password and logging in. 

Is it possible to not use alsa at all and just use OSS or are they interconnected?

---

### Post by margaf77 on 2007-07-08
anyone? Im starting to feel invisible here :(

---

### Post by nico9julio on 2007-10-09
I've the same problem too

---

### Post by mastroDani on 2007-11-02
apt-get install libasound2-plugins

:)

---

### Post by SpookComix on 2007-12-16
I'm having the same problem.  "apt-get install libasound2-plugins" did nothing.

My problem started after following some advice in another thread to install "pulseaudio."  I couldn't get sound from Monkey Bubble, but everything else worked.  After installing "pulseaudio," Monkey Bubble wasn't fixed and nothing else other than Amarok that I tried produced sound.

I uninstalled "pulseaudio" and the one or two other packages it had brought with it.  Now, no system sounds, no game sounds...the only thing that seems to produce sound is Amarok.

Is there a way to "reset" the system (Kubuntu Gutsy in my case) to the way it was when it was installed, as far as drivers and whatnot go?

--SC

---

### Post by thieste on 2007-12-23
open a terminal and try 

asoundconf unset-pulseaudio


that works for me

---

### Post by wavesound on 2008-02-24
HI This is driving me nuts!
I had my realtek working mostly and not the rme card.
I have removed pulse audio but still no sound.
Some times it works and some not!
Any ideas?

Cheers
Bob

---

