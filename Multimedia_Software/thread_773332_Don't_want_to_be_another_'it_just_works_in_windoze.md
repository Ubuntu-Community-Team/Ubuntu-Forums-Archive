---
title: "Don't want to be another 'it just works in windoze'..."
date: 2008-04-28
forum: Multimedia Software
---

### Post by tai1spin on 2008-04-28
I need some help here. First off, I have an Intel Centrino Duo laptop (fujitsu 6460) with dual 2.2 procs, 4 gig ram, built in ATI RAdeon 2600 HD w 256MB and 17 inch screen. Hardy looks great on it. For the last 3 weeks I have been battling MYTHTV. I have a Hauppauge HVR 950. I have gotten it to work to some degree. However, there are a lot of different links to how to install and make it work... So my first question is

1. Which repository should I use to compile against the 2.6.24-generic kernel? linuxtv.org or mcentral.de? I beleive the mcentral is supposed to be the latest drivers, but I am not sure.

I will post further questions later... this has been fun, but damn!

---

### Post by AlecJ on 2008-04-28
Your best bet for the HVR 950 is here:-
[http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)

As for which drivers are best I would try both, you will end up building it a few times anyway.

And the best Guide I followed is here
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I built mine last year, using a new desktop case (that fits under the telly) amd64 daul core x2,Nvidia 7800 (Svideo out to TV),7.1 sound (on board and wired to 8 speakers with amps) 1Gb ram, 160Gb drive, 1 Kworld DVb-T and 1 Nova T-500 (2 tuners in one) and this card carries the remote
No Keyboard or mouse, I VNC to it from a windows machine in the office.
Would not be parted from it now!

---

### Post by msrinath80 on 2008-05-04
I would not waste too much time with Hardy and the HVR-950. There are some kernel mismatch issues with alsa versions inside the kernel and outside. As a result sound does not work. The easiest way for me was to install Fedora 9 and copy the firmware file (xc3028-v27.fw) to /lib/firmware. Once that is done, all you need to do is plug the stick into the USB port and fire up tvtime/mplayer/mythtv and you can watch TV without any problems.

If, on the other hand, you want it to work with Hardy and are willing to fool around for some time with configuration, then I would appreciate if you could let me know when you have both audio and video working without problems.

---

