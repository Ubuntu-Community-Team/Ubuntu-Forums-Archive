---
title: "No sound output after upgrade to 12.10"
date: 2013-08-23
forum: Multimedia Software
---

### Post by BarryM on 2013-08-23
I have just upgraded to 12.04 and tried to play some MP3 files through Rhythmbox, but am getting no sound. In system settings the sound output is directed to Dummy Output, and there seems to be no way of changing this. It worked OK on 12.04. Can anyone make any suggestions how I get my sound back?

---

### Post by Yellow Pasque on 2013-08-24
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by BarryM on 2013-08-24
OK, I have done that, and got this response:
[http://www.alsa-project.org/db/?f=c763843ff58a7be592feaeda19f247b87e55ead0]("http://www.alsa-project.org/db/?f=c763843ff58a7be592feaeda19f247b87e55ead0")
now what do I do?

Thanks!

---

### Post by Yellow Pasque on 2013-08-24
ALSA info looks okay, so I would try resetting pulse user configuration files:
```
rm -r ~/.pulse*; pulseaudio -k
```
Does that help?

---

### Post by BarryM on 2013-08-25
I have tried that and get this:

     E: [pulseaudio] main.c: Failed to kill daemon: No such process

still no sound output.

I have checked what I have installed in the synaptic package manager and, on a search for pulseaudio have the following flagged as installed:
gstreamer0.10-pulseaudio, indicator-sound, libcanberra-pulse, libpulse-mainloop-glib0, libpulse0, libpulsedsp, libsdl1.2debian, pulseaudio, pulseaudio-esound-compat,
pulseaudio-module-bluetooth, pulseaudio-module-gconf, pulseaudio-module-x11, pulseaudio-utils.

Is there perhaps some package missing that I should have there?

Thanks for your patience!

---

### Post by BarryM on 2013-09-18
This has all gone very quiet! I still have no sound, so I was wondering if anyone out there can suggest a solution for me?

---

### Post by Yellow Pasque on 2013-09-18
The latest driver is always worth a shot: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by BarryM on 2013-09-24
Treid that, but still no sound, (it took a while before I found the right file on the DKMS pages). I think that the system can detect my sound card, but for some reason, does not seem to actually enable it. Sound is still directed to Dummy, with no other options available.

---

### Post by Yellow Pasque on 2013-09-24
> Sound is still directed to Dummy, with no other options available.
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by BarryM on 2013-09-25
I tried following the instructions given at the link, and this is what I got:
     (user)@(user)-desktop:~$ echo autospawn = no >> ~/.config/pulse/client.conf  #use ~/.pulse/client.conf on Ubuntu <= 12.10
     bash: /home/(user)/.config/pulse/client.conf: No such file or directory
I can't find a file called client.conf anywhere: I wonder if this is the problem?

---

### Post by Yellow Pasque on 2013-09-25
Note the comment: > use ~/.pulse/client.conf on Ubuntu <= 12.10
You didn't do that...

> I can't find a file called client.conf anywhere
By default, it does not exist (there is one in /etc/pulse, but it's best not to tamper with a system conf file belonging to a .deb package when you can avoid it).

---

### Post by BarryM on 2013-09-27
Verbose log generated and posted with bug report. Thanks for your assistance!

---

### Post by BarryM on 2013-09-28
Problem now resolved, with assistance from Alsa Bug team. It turned out to be an incorrect statement at the end of alsa-base.conf, the line 6stack-dig should have read 6stack-digout.
I now have sound!

---

### Post by Yellow Pasque on 2013-09-28
Great. Please mark thread solved.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1231903](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1231903)

---

