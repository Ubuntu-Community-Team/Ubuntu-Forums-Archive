---
title: "Pulseaudio - a dream come true"
date: 2011-04-13
forum: Multimedia Software
---

### Post by realn on 2011-04-13
Just wanted o share my experience with sound on ubuntu. Here's the summary:

 I've been using for some 6 years Kubuntu. I was using alsa as sound driver. I accumulated so much anger and frustration because of its total lack of transparency/easiness/user-friendliness.
Those were the main problems:
- couldn't change on the fly the audio device, and only after so much time spent in finding workarounds (shell scripts, inserting and removing kernel modules in order to switch from one audio device to another, asoundconf-gtk, editing .asoundrc, etc.) I got to a more or less workable solution for changing the device;
- separate volume control per application - some applications had this "software volume" , but some of them don't;
- couldn't play more than one audio source at a time - sometimes I even had to completely exit from the program using the soundcard (firefox, for instance even if it doesn't really play something, somehow gets the sound card busy all the time, once it got hold of it) in order to be able to play something else with another program.

Some days ago I installed Kubuntu Trinity 10.04 on my server, and decided to think. I knew that Ubuntu (not Kubuntu) didn't have most of the problems mentioned above. I knew that it uses pulseaudio. I took a plunge and :
 sudo /etc/init.d/alsa-utils stop
 sudo apt-get install pulseaudio pavucontrol
 and then: WAWWW
Everything I couldn't do before and always wanted to do, it worked without the slightest problem. Can play 3 audio sources with 3 different programs at the same time, can talk on Skype without having to kill, modprobe -r, alsa restart and then reboot, I can even change the I/O audio device WHILE TALKING.
 My eternal gratitude goes to all people who contributed to this wonderful piece of software - pulseaudio. Its easyness and straightforwardness is amazing, how come that not all Linux distribution/variants use it?

PS I forgot to mention - the only thing not working (for the moment, I hope) is the AC3 passthrough on SPDIF. I hope it will be soon integrated.

---

