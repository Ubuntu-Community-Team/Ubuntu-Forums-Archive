---
title: "newbie question: No Sound 15.10"
date: 2015-11-28
forum: Multimedia Software
---

### Post by nfisheremti on 2015-11-28
i have an old computer i am trying to resurrect and use as a multimedia server.

i have everything working except the sound.

i have installed an ASUS XONAR DG PCI card, I had found this was a card that was listed on the ASLA matrix and should be supported in kernels greater than 3.14.  i originally tried 14.04, but that did not work, so i have upgraded to 15.10 (kernel 4.2).

i have tried everything i could find regarding "ubuntu no sound" that i could find on the interwebz, no luck.

the only device shown in sound settings is "Dummy Output"

for some reason alsa does not seem to have loaded correctly, and will not reload or force-reload.

here is what i've been able to deduce so far.

[FONT=courier new]neil@kanga:~$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

neil@kanga:~$ sudo lshw
...
           *-multimedia UNCLAIMED
                description: Multimedia audio controller
                product: CMI8788 [Oxygen HD Audio]
                vendor: C-Media Electronics Inc
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=24 mingnt=2
                resources: ioport:e800(size=256)[/FONT]
...

i have rebooted inumerable times,
some advice had me look for ".asoundrc" in home: it was not there.  i searched all dir for .asoundrc and could not find it anywhere.
i tried: 
sudo gedit /etc/default/speech-dispatcher

[FONT=arial]and found that run already was = to no, so that wasn't it.
i tried:
[/FONT]
sudo add-apt-repository ppa:ubuntu-audio-dev
sudo apt-get update
sudo apt-get dist-upgrade

[FONT=arial]where i get this at the end:
[/FONT]
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

[FONT=arial][/FONT][FONT=arial]not really worried about the first, since the processor is an intel atom, but the i386 might be an issue, but if it is, i don't know where to go from here.
any suggestions?

i'm stuck.

since i am a noob, please do't assume that i know anything.  obviously i've figured out how to open a terminal window, beyond that....
i probably don't know how to use various applications or even know where to find them.
thanks in advance for your help.
[/FONT]

---

### Post by nfisheremti on 2015-12-01
bump.

---

