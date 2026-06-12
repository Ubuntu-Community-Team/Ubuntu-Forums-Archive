---
title: "Ubuntu 9.04 Audio Problem (crackling static sound)"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Auzzie666 on 2009-08-13
Hey there, I'm having a problem with my audio in ubuntu 9.04. It was working fine previously, now when I play back mp3's or any sound for that matter, all I get is a crackling static-like sound. 

The only thing I can think of, is I recently did a 'sudo apt-get install timidity' in order to get my sound to work properly in TuxGuitar. Today, I typed sudo apt-get remove timidy and removed it.

Aside from that, I cant figure out what is going wrong, any help would be appreciated!

Thanks!

---

### Post by grumman on 2009-08-14
i think it maight have been an update messing with things,havind the same problem here, but i didn't install anything that could mess things up, it's realy annoying.

however if you put your output to OSS instead of alsa/pulseaudio you should be able to get sound. (for example if you use totem)

but it would be nice if the problem could get fixed

---

### Post by Auzzie666 on 2009-08-14
It could be, but I haven't updated for awhile and it was working fine a few days ago :/

---

### Post by fela on 2009-08-14
Edit /etc/pulse/default.pa, and add

```
load-module module-hal-detect tsched=0
```

To the file. Then run

```
sudo /etc/init.d/pulseaudio restart
```

Or reboot the system. That should fix it ;)

---

### Post by grumman on 2009-08-14
it seems my problem could be solved by following this troubleshooting guide

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

(seems i didn't do it quite right the fisrt time)

however: the tip above caused me to have extra trouble, when I tried toget ALSA or pulseaudio to start it would give me an "can't connect to device: connection refused" error,so be sure to tru the troubleshooting guide first, before applying the suggestion in the above post)

---

### Post by zugins on 2009-08-15
I have exactly same issue. I plugged in a force feedback joystick then tried playing an old game in wine. After exiting I tried to reboot the system but it seemed to have stuck so I had to shut the powef off. After that I only get static from the card.

I tried refreshing install[SIZE=2]**(**[/SIZE]**[SIZE=2]Refreshing/Reinstalling the drivers)[/SIZE]** from the guide and doing what fela suggested. It did not seem to do anything, getting same exact static.

Here is what worked (not 100% sure why)
editing /etc/modprobe.d/alsa-base.confadding

options snd-hda-intel model=5stackthen

sudo alsa force-reload

---

