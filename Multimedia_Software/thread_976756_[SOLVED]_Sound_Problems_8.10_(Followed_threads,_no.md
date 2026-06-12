---
title: "[SOLVED] Sound Problems 8.10 (Followed threads, now what)"
date: 2008-11-09
forum: Multimedia Software
---

### Post by nexist on 2008-11-09
I have a Ubuntu 8.10 install, and there is no sound. I've been trying to fix it, but nothing seems to fix it. WHat do I need to do, what information do you need so we can diagnose & fix this problem.

Thank you

---

### Post by Ubuntist on 2008-11-09
I have this problem every time I upgrade Ubuntu.  For me the solution is to go to System|Preferences|Sound, select the Devices tab and change each of the "sound playback" entries to an entry referring to your sound card.  Click "Test" in each case; if you've got it right, you'll hear a tone when you click test.

Hope that helps....

---

### Post by nexist on 2008-11-09
Thank you. Do we know why PulsAudio does not work even though all the controls seem to be for that? I ended up using the OSS device.

Anyway, I can hear sound again so hopefully all is good

---

### Post by Ubuntist on 2008-11-09
No idea.  I don't really even understand what ALSA, OSS, etc. actually do.

---

### Post by SyntaxMage on 2008-11-09
> **Ubuntist said:**
> I have this problem every time I upgrade Ubuntu.  For me the solution is to go to System|Preferences|Sound, select the Devices tab and change each of the "sound playback" entries to an entry referring to your sound card.  Click "Test" in each case; if you've got it right, you'll hear a tone when you click test.

Hope that helps....

you just became my personal jesus. I had this problem and it worked to fix it. Thanks so much.

---

### Post by nexist on 2008-11-10
While that got my MP3's to play, I still had problems with Firefox and other sounds. I finally broke down and just uninstalled pulse as per [Ubuntu 8.10 (Ibex) Pulse Audio removal.]("http://ubuntuforums.org/showthread.php?t=973637http://ubuntuforums.org/showthread.php?t=973637") Everything is rosy now. Maybe pulse will work in 9.04

---

### Post by Ubuntist on 2008-11-10
What's the difference among Pulse, ALSA, OSS and ESS?

---

### Post by nexist on 2008-11-10
I can't answer on a technical level, but they are merely competing platforms. Pulse is supposed to be a better (in the long term) solution. From what I gather on the various posts, ALSA is hitting design problems now. Sadly, I cannot get Pulse to work so I will choose the practically working solution over the theoretically better non-working option.

---

### Post by psyke83 on 2008-11-10
> **Ubuntist said:**
> What's the difference among Pulse, ALSA, OSS and ESS?

**ALSA** is the Advanced Linux Sound Architecture, which provides the core audio drivers (kernel) and support libraries (userspace). Virtually every modern Linux application now uses ALSA.

**OSS** stands for Open Sound System - it was the precursor to ALSA. In the past it was viewed as too limiting (such as being inable to mix multiple sounds), which spurred the development (and later, universal adoption) of ALSA.

**PulseAudio** is a sound server. What this means in simplified terms is that it runs as a layer on top of ALSA, but it replaces some of the core functionality of the ALSA libraries. The most obvious example is sound mixing.

**ESD** is the ESound Daemon, a very simplified sound server created by the GNOME developers & used primarily to play system event sounds (but is not suited to anything more complex). It is now obsoleted by PulseAudio and libcanberra (a system sound event library).

Usually ALSA mixes multiple sounds via its software "dmix" ("**d**evice **mix**er") device, which allows sounds from multiple applications to play simultaneously on your system. If you are running PulseAudio, then it will directly access your sound card (bypassing "dmix"), and provide an enhanced alternative that performs the same function.

Although OSS is still being developed (though not widely used), ALSA itself provides OSS support. Similarly, PulseAudio supports ALSA and OSS applications using a kind of "compatibility layer".

I strongly suggest you don't disable or uninstall PulseAudio.

Take a look at the [Intrepid]("http://ubuntuforums.org/showthread.php?t=866965") guide for PulseAudio (first read the FAQ, and ignore steps 1a and 1b if you wish to follow the instructions). Also, see the [Hardy]("http://ubuntuforums.org/showthread.php?p=4928900") guide for information on troubleshooting (Appendix B). I will soon consolidate these guides into one, but either will give you a better understanding of PulseAudio.

N.B. PulseAudio works correctly out of the box for most Intrepid users, but it is possible that users may have inadvertently misconfigured their systems, especially when upgrading from Hardy. The guides above perform the steps required to eliminate these problems.

---

### Post by nexist on 2008-11-10
I had a fresh install on a 64-bit quad system with an audigy soundcard. No system sounds, no movies, no music. I managed to get the music working via the instructions earlier in this thread, but not the rest. It appears to be the same problem as with 8.04 (I had the same symptoms). If it is nothing more than a configuration issue, then (1) I couldn't configure it after several days of trying; & (b) if it isn't important enough for the devs to fix between revisions then I can make do with the ALSA/ESD combo until it is fixed.

It sucks because I actually wanted to use the PulseAudio system, but I want to use my system more.

---

### Post by psyke83 on 2008-11-10
> **nexist said:**
> I had a fresh install on a 64-bit quad system with an audigy soundcard. No system sounds, no movies, no music. I managed to get the music working via the instructions earlier in this thread, but not the rest. It appears to be the same problem as with 8.04 (I had the same symptoms). If it is nothing more than a configuration issue, then (1) I couldn't configure it after several days of trying; & (b) if it isn't important enough for the devs to fix between revisions then I can make do with the ALSA/ESD combo until it is fixed.

It sucks because I actually wanted to use the PulseAudio system, but I want to use my system more.

If you didn't yet remove PulseAudio, then I suggest you look at Appendix B of the (Hardy) PulseAudio guide that I listed above. That will explain how to perform troubleshooting on PulseAudio, and what debug output may be useful. You need to provide us with some information to realistically expect any help...

Sometimes the problem is a very simple matter of a muted/low PCM or Master mixer; check the levels via:

```
& alsamixer -Dhw
```

---

### Post by nexist on 2008-11-10
Well, I did remove it last night. However, I can always reinstall and try to get Pulse working.

Would I need to uninstall ESD or will Pulse preempt it?

---

### Post by psyke83 on 2008-11-10
> **nexist said:**
> Well, I did remove it last night. However, I can always reinstall and try to get Pulse working.

Would I need to uninstall ESD or will Pulse preempt it?

I think that the ESD packages conflict with PulseAudio, yes. You have to be careful to ensure that you reinstall all the necessary packages, though (i.e., did you note which packages were removed?).

This list from my system may help:
```
conn@inspiron:~$ dpkg -l | grep pulse
ii  gstreamer0.10-pulseaudio                  0.10.10.4-1ubuntu1                    GStreamer plugin for PulseAudio
ii  libpulse-browse0                          0.9.10-2ubuntu9                       PulseAudio client libraries (zeroconf suppor
ii  libpulse-mainloop-glib0                   0.9.10-2ubuntu9                       PulseAudio client libraries (glib support)
ii  libpulse0                                 0.9.10-2ubuntu9                       PulseAudio client libraries
ii  libpulsecore5                             0.9.10-2ubuntu9                       PulseAudio sound server core
ii  pulseaudio                                0.9.10-2ubuntu9                       PulseAudio sound server
ii  pulseaudio-esound-compat                  0.9.10-2ubuntu9                       PulseAudio ESD compatibility layer
ii  pulseaudio-module-gconf                   0.9.10-2ubuntu9                       GConf module for PulseAudio sound server
ii  pulseaudio-module-hal                     0.9.10-2ubuntu9                       HAL device detection module for PulseAudio s
ii  pulseaudio-module-x11                     0.9.10-2ubuntu9                       X11 module for PulseAudio sound server
ii  pulseaudio-module-zeroconf                0.9.10-2ubuntu9                       Zeroconf module for PulseAudio sound server
ii  pulseaudio-utils                          0.9.10-2ubuntu9                       Command line tools for the PulseAudio sound 

```

---

### Post by Jarlathg on 2008-11-10
> **Ubuntist said:**
> I have this problem every time I upgrade Ubuntu.  For me the solution is to go to System|Preferences|Sound, select the Devices tab and change each of the "sound playback" entries to an entry referring to your sound card.  Click "Test" in each case; if you've got it right, you'll hear a tone when you click test.

Hope that helps....

Thanks Ubuntist. Problem solved. This was driving me crazy.

---

### Post by psyke83 on 2008-11-10
> **Jarlathg said:**
> Thanks Ubuntist. Problem solved. This was driving me crazy.

Sound mixing may break if you do this.

---

### Post by nexist on 2008-11-17
OK. The current status is that I have PulseAudio installed. I also have the OSS soundcard devcie selected (I get no sound otherwise). It works for both Movies and Music, but not for system sounds. Nor can I have more than one soundcard using device active at a time.

Can someone tell me where to go from here?

---

### Post by psyke83 on 2008-11-17
> **nexist said:**
> OK. The current status is that I have PulseAudio installed. I also have the OSS soundcard devcie selected (I get no sound otherwise). It works for both Movies and Music, but not for system sounds. Nor can I have more than one soundcard using device active at a time.

Can someone tell me where to go from here?

Quite simple: either a) reinstall and configure PulseAudio, or b) install ESD.

As for configuring PulseAudio, see my guide [here]("http://ubuntuforums.org/showthread.php?t=789578"). There's also a reason for the troubleshooting part of the guide... to troubleshoot.

P.S. In System/Preferences/Sound, setting the Playback devices to OSS is the worst way to configure your system. Setting the OSS drivers causes GStreamer* applications to use ALSA's OSS **emulation** drivers. This means that audio mixing will break (e.g. between Totem and Flash).

* The System/Preferences/Sound application only affects the settings for GStreamer applications (Totem, Rhythmbox, Sound Recorder, Ekiga official GNOME-provided applications). Everything else (e.g. games/SDL, Flash, Java, Skype, VLC, mplayer, and virtually every application you could possibly imagine) will still try to use ALSA (or PulseAudio, if it's running).

---

### Post by nexist on 2008-11-17
Ah, it appears that there is an 8.10 section now. The only reason I was using the OSS setting was because it was the only one that worked. Anyway, I will try out those steps when I get home. Thank you.

PS. I was using ESD, but every time my Flash caused a lock-up, I would lose it.

---

### Post by nexist on 2008-11-29
Since I just quit smoking, I got really frustrated and decided to install Xubuntu. Since this had the same problems, I started checking and found that I had two sound devices, one forgotten built into the motherboard. I disabled it at the BIOS level and it started working. I've reinstalled Ubuntu and all seems to be working. I am still waiting for Songbird to finish reading in the library, but I have system sounds and everything else now.

---

### Post by darksideforge on 2008-11-29
> **Ubuntist said:**
> I have this problem every time I upgrade Ubuntu.  For me the solution is to go to System|Preferences|Sound, select the Devices tab and change each of the "sound playback" entries to an entry referring to your sound card.  Click "Test" in each case; if you've got it right, you'll hear a tone when you click test.

Hope that helps....


I tried your suggestion because it seemed to give good results to others. Unfortunately, the following shows up when I do as you instructed:
[IMG]http://i38.photobucket.com/albums/e129/diveclint/Screenshot-UntitledWindow-1.png[/IMG]

Any assistance would be appreciated!

---

### Post by darksideforge on 2008-11-29
> **psyke83 said:**
> If you didn't yet remove PulseAudio, then I suggest you look at Appendix B of the (Hardy) PulseAudio guide that I listed above. That will explain how to perform troubleshooting on PulseAudio, and what debug output may be useful. You need to provide us with some information to realistically expect any help...

Sometimes the problem is a very simple matter of a muted/low PCM or Master mixer; check the levels via:

```
& alsamixer -Dhw
```

Very informative and impressive! Unfortunately, it seems to be telling me my level is 0.00, 0.00. What do I do to increase my level(s)? Here is a screenshot of my Terminal:
[IMG]http://i38.photobucket.com/albums/e129/diveclint/ALSAmixerLevels.png[/IMG]

---

