---
title: "Video and audio will not play/unresponsive"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Colinhero on 2007-11-01
I have seen other threads like this but I will try to provide more details
Ubuntu Gutsy
All gstreamer apps/plugins installed/enabled
Restricted drivers installed

Whenever I attempt to open any audio or video file... the program attempts to load it and then fades to black and becomes unresponsive. OGG, MP3, AVI, MPEG. All file types fail. However, I am getting inconsistent results. Sometimes when I reboot it's gone, others it is not. The login and start up sounds play at event, but when I attempt to play them again through sound preferences, they do not play. Window becomes unresponsive. I have tried Totem, Xine, VLC, Firefox, and Audacity.

Any help on this would be GREATLY appreciated as it is a major annoyance. I can't even watch a youtube video! HELP!!

---

### Post by Light- on 2007-11-02
Whats the specifications of your system?

---

### Post by Colinhero on 2007-11-04
Acer TravelMate 2420
Ubuntu 7.10
2gb Ram
1.5ghz Intel Celeron M
 Intel Graphics Media Accelerator 900 (128 MB)

---

### Post by Tsjies on 2007-11-05
Got the same problem here on a Toshiba Satellite A60. First I thought it was a problem with mp3 but flac also hangs the media player (Amarok, Rhytmbox, Exaile) after a short period of time. Don't know where to begin. 

Tsjies

---

### Post by juzzblack on 2007-11-05
I'm also having exactly the same issues as Colinhero describes - can't play Youtube videos (any browser), can't play audio (Rhythmbox hangs), can't play video/DVD (Totem/Mplayer hang). VLC will play WMV files, albeit in a greyed out window and no sound.

My system:

Gutsy 7.10
Kernel Linux 2.6.22-14-generic
Gnome 2.20.0

on a Acer 3023WLMi laptop;AMD Sempron 3100+; 512MB RAM; ATI RADEON X700 graphics card.


I've noticed that if I run Totem or Rhythmbox from a terminal, it returns the message: 'sh: jackd: not found' then hangs. I tried installing jackd from Synaptic but that didn't resolve anything; just returned a different message: 'JACK tmpdir identified as [/dev/shm]'

---

### Post by Colinhero on 2007-11-05
I don't know what I just found but may have stumbled on a solution...

Opened up terminal..
jackd -d alsa

Now, while the terminal is still open, i can open and play video and audio.
I don't know what this is, but I sure hope it helps somebody to develop a solution!

---

### Post by Tsjies on 2007-11-06
Tried to do that and got the message: 

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

So ... no solution for me. The system monitor tells me that the program is taking up to 100% of the cpu so it is running heavily. I feel there should be an easy solution since every audio application is reacting in exactly the same manner. But which solution?


Tsjies

---

### Post by juzzblack on 2007-11-06
> **Colinhero said:**
> I don't know what I just found but may have stumbled on a solution...

Opened up terminal..
jackd -d alsa

Now, while the terminal is still open, i can open and play video and audio.
I don't know what this is, but I sure hope it helps somebody to develop a solution!

Thanks, I tried this and found it cured the problem. I was able to play Youtube videos, flash, wmv, mp4 videos, also mp3 files played in Rhythmbox. All without any windows becoming unresponsive. :)

However, this only worked as long as I kept the terminal open. :(

So I did some digging because I didn't understand what 'jackd -d alsa' was doing. I think '-d' is simply a debugging argument. So (in a terminal) I typed 'jackd -d' This returned the output:

Unknown option character d
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


usage: jackd [ --realtime OR -R [ --realtime-priority OR -P priority ] ]
             [ --name OR -n server-name ]
             [ --no-mlock OR -m ]
             [ --unlock OR -u ]
             [ --timeout OR -t client-timeout-in-msecs ]
             [ --port-max OR -p maximum-number-of-ports]
             [ --debug-timer OR -D ]
             [ --verbose OR -v ]
             [ --clocksource OR -c [ c(ycle) | h(pet) | s(ystem) ]
             [ --silent OR -s ]
             [ --version OR -V ]
         -d backend [ ... backend args ... ]
             The backend can be `alsa', `coreaudio', `dummy',
                                `freebob', `oss' or `portaudio'.

       jackd -d backend --help
             to display options for each backend

Note the section near the end: '-d backend [ ...backend args ...] The backend can be 'alsa', 'coreaudio', 'dummy', ... '

So: 'jackd -d alsa' seems to be saying 'use alsa as the backend for jackd'

So next I opened Synaptic and searched for 'jackd' to check I had everything installed. This revealed I did indeed have jackd installed, but if I right-clicked on it, the menu pop-up revealed two options 'Mark Recommended for installation' and 'Mark Suggested for installation'. Theses listed some packages which were not installed:

jack-tools
meterbridge
libjackasyn0
qjackctl
libpam-modules

I wasn't sure if any or all were needed, so I selected and installed them all. So far this seems to have fixed everything! :)

Tsjies, your output seems to be saying you're having some problem using alsa as the backend to jackd. Maybe try an alternative, such as: 'jackd -d oss' or check you have everything required for alsa installed and everything I've mentioned for jackd.

Hope this post makes sense and is of some help. I don't claim to understand it all and I'm no expert but it seems to be working for me.


EDIT:

Sorry, apologies. I spoke too soon! I'm getting the same problems again. I will try completely unistalling jackd.

---

### Post by Colinhero on 2007-11-08
Well, I think that I have fallen into some sort of *nix trap. The more that I try to fix, the more seems to go wrong. Now, my power settings are whacked, can't hibernate... :(
Sorry, unrelated.

Haven't made any more headway with this... tried your suggestion and have the same problems. 
Let me know about reinstalling jack... otherwise I'm heading for the hills and dumbing to Fiesty.:mad:

---

### Post by juzzblack on 2007-11-10
I uninstalled Jack but no change. :( So I'm stumped too. :confused::(

---

### Post by Colinhero on 2007-11-12
Hooray!:guitar:

I think I found a fix for this problem!

I followed these instructions on updating alsa for gutsy and after reboot seems to be working fine!
[http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html](http://lastkth-en.blogspot.com/2007/11/upgrade-alsa-ubuntu-gutsy-update.html)

Good luck!

Edit: Nevermind....:(

---

### Post by cyosolo on 2007-12-27
Hi,

I find a solution of this problem and it is very simple, next to do actualization of drivers of ALSA sound you must to know that model is your sound card, for example for me is intel ALC888. Then write 

sudo nano /etc/modprobe.d/alsa-base

And type at end

options snd-hda-intel model=ALC888

If you sound card is different, change  snd-hda-intel and ALC888 with your distribution and model.

Next 
sudo reebot, and the system will started fine.

Cheers ,

---

