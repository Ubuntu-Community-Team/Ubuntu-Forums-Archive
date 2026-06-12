---
title: "pulseaudio not working anymore after latest updates on Maverick 64bit vs Dell M1330"
date: 2010-12-10
forum: Multimedia Software
---

### Post by lviggiani on 2010-12-10
Hi Everybody,
I've been running Maverick 64bit fine on my Dell M1330 laptop until a couple of days ago. After the latest updates (I guess to kernel 2.6.35-24-generic), sound stopped working properly.
The sound indicator applet tells me that the sound system is not responding. The login sound doesn't play anymore.

On the other hand Rhythmbox plays and I can hear the music. I can adjust Rhythmbox volume but not the global volume (as neither the sound indicator applet nor the multimedia volume keys on my laptop work).

If I open up the terminal and run
```
$alsamixer
```
it works flawless.

Here is what I get if I try to run pulseaudio from the terminal
```
$ pulseaudio
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-3.4,1.3,2.6,1.6,-1.3,-3.2,-2.6,-3.5,-7.1,-6.5,-5.5,-6.5,-4.8,-4.8,-3.2"): initialization failed.
E: main.c: Module load failed.
E: main.c: Inizializzazione del demone non riuscita.
```
Last sentence is in Italian and it means "could not initialize the daemon".

Can someone help me please?
Thanks, Luca.

---

### Post by lviggiani on 2010-12-10
Hi again,
I googled around a little bit more and I found someone having had the same issue.
The solution is pretty easy:

1) Delete the folder ~/.pulse
2) Restart the gnome session

That's it.
I hope that my experience could help someone else.
Cheers, Luca

---

### Post by bt420 on 2012-11-18
Thank you sir. Your experience did help someone else.

---

