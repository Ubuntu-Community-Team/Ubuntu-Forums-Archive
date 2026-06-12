---
title: "What to configure to get the best sound results?"
date: 2011-01-10
forum: Multimedia Software
---

### Post by amr-maro on 2011-01-10
[SIZE=3]Hi, I use Kubuntu 10.10 and I'd like to know what to configure (say in daemon.conf - PulseAudio) to get the best sound quality & the most out of my *_sound card_*. By the way, I don't have any sound problems. I just want to get the best results from the built-in speakers & when I connect my laptop to external speakers. I have a Sony VAIO VGN-NR32M laptop. Thanks!
[/SIZE]

---

### Post by ankspo71 on 2011-01-12
Hi,
It's possible to install a system wide graphical equalizer for pulseaudio in Kubuntu 10.10. Warning: I have only been testing this in Kubuntu 10.10 for the past 15 minutes, but so far so good, it is working for me. My instructions are based on what I wrote here (for Kubuntu 10.04): [http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html](http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html) 

First, you will need to download the equalizer specifically made for Ubuntu 10.10 from this page:
[http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)
Install the package. That is enough to have it work in Ubuntu 10.10.

But to get it to work in Kubuntu 10.10, you will also need the following packages:
gnome-media 
pulseaudio 
pavucontrol 
padevchooser
(I'm pretty sure pulseaudio is already installed)

Once everything is installed, you can launch the equalizer by typing "pulseaudio-equalizer-gtk" in the terminal (without the quotes). It should be working as is without making any further settings in the system. If not, refer to what I wrote here for Kubuntu 10.04:
[http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html](http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html)

Once you know it works properly you can create a start menu entry for pulseaudio-equalizer-gtk.

Here is more info on the equalizer itself:
[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)
Here is the original repository for the equalizer:
[https://launchpad.net/~psyke83/+archive/ppa](https://launchpad.net/~psyke83/+archive/ppa)

Hope this helps.

---

### Post by amr-maro on 2011-01-16
[SIZE=2]Thanks very much ankspo71. Besides the equalizer, I was wondering if any of the settings in the file /etc/pulse/daemon.conf (e.g. "resample-method", "default-sample-format" & "default-sample-rate") would be configured to get the best sound quality and the best settings for the sound card (Intel High Definition Audio on a Sony VAIO [/SIZE][SIZE=2]VGN-NR32M laptop). Thanks![/SIZE]

---

