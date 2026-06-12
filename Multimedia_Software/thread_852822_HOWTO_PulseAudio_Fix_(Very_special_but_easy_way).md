---
title: "HOWTO: PulseAudio Fix (Very special but easy way)"
date: 2008-07-08
forum: Multimedia Software
---

### Post by twinklellon on 2008-07-08
sudo gedit /etc/pulse/default.pa

1.Find:
#load-module module-alsa-sink ...
Change it to:
load-module module-alsa-sink device=dmix

2.Find:
load-module module-suspend-on-idle
Comment it out&#65306;
#load-module module-suspend-on-idle

3.Find:
load-module module-hal-detect
Comment it out&#65306;
#load-module module-hal-detect

Then Log out and log in again.

That's all and everything should work fine. No more war between ALSA and PulseAudio.

Now it is no need to use libflashsupport for Flash pulseAudio support. Alsa audio streams can get along well with pulseaudio audio streams since ALSA dmix will do all the work. Skype can work on its ALSA way, and at the same time, totem can play audio files via PulseAudio.

[IMG]http://5201314.googlepages.com/module.jpg[/IMG]

Example: SMplayer(ALSA), Skype(ALSA), Totem(PulseAudio), Rhythmbox(PulseAudio)

[IMG]http://5201314.googlepages.com/dmix.png[/IMG]

---

### Post by twinklellon on 2008-07-09
just updated... now it works better~

---

### Post by xc3RnbFO8P on 2008-07-09
I tried **load-module module-alsa-sink device=dmix**
it solved the problem with not to be able to watch TV in Kaffeine
and talk in Skype. (I just mute Kaffeine when I talk in Skype)

---

### Post by psyke83 on 2008-07-09
Your method will allow sound mixing in most applications, but it will cause several applications to bypass PulseAudio entirely as well as increasing CPU usage and latency - why would you want to do this?

ALSA's "dmix" is a virtual mixing device that performs sample conversions and channel copying - in other words, it allows sounds from multiple applications to play at once. Note that many cards do not support hardware mixing, so the CPU does the work of mixing sounds. PulseAudio itself performs the same function as ALSA's "dmix" virtual device, so by configuring your system in this way, you are running one software mixing device on top of another, potentially doubling latency and CPU usage.

Configuring PulseAudio to use the "dmix" device was briefly tested during Hardy's development cycle to fix some mixing problems, but it was rejected due to the issues mentioned above. The links below give some more detail on the issue:

PulseAudio developer Lennart Poettering's comments on dmix: [http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg00636.html](http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg00636.html)
Using dmix to fix Flash was tested here: [https://bugs.launchpad.net/bugs/192888](https://bugs.launchpad.net/bugs/192888)

The real solution is to configure PulseAudio properly (or else get rid of it entirely!). The fixes in my [guide]("http://ubuntuforums.org/showthread.php?t=789578") are merely Ubuntu-fied instructions based on upstream's [PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup"), and extra information that upstream don't provide in a single place.

---

### Post by xtrumanx on 2008-08-01
Hey, I used your tutorial since I couldn't have 2 applications play sound together. But this seems to have caused a different problem. Everyone once in a while for no inexplicable reason the audio starts to stutter and the only way that I know of to get rid of this is to restart my pc. It's happening often enough that I'm thinking of going back to the default solution than use this. Any idea how to get rid of the stuttering?

EDIT: I changed my default.pa back to how it was originally. This solution wasn't working very well for me due to the above problem. Guess I can hope 8.10 will fix my problems...

---

### Post by twinklellon on 2008-10-13
Stuttering Audio Fix (bug #188226 and bug #190754)
PulseAudio appears to create stuttering audio issues on many systems, perhaps due to the default CPU scheduler in Hardy's shipping kernel 2.6.24-16-generic (bug #188226), buffering problems (bug #190754), or both combined. This information should hopefully solve or at least reduce these problems.

These settings are ideal for my audio card, an "Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)". They may not work as well for you, so try adjusting the fragment values if you have problems.

1. Make sure your system is up-to-date and you are using at least kernel 2.6.24-18-generic, as it provides important scheduler fixes to prevent PulseAudio skipping.

2. Add your user to the groups "pulse-access" and "pulse-rt":
Code:

$ sudo adduser $USER pulse-access
$ sudo adduser $USER pulse-rt

3. Edit "~/.pulse/daemon.conf":

Code:

$ gedit ~/.pulse/daemon.conf

Add the following lines to the end of the file, and save:

Code:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragments = 8
default-fragment-size-msec = 5
resample-method = speex-float-0

Note 1: If you still notice stuttering, try modifying the fragment sizes marked in red.
Note 2: The resample method listed in blue will reduce CPU usage, potentially at the cost of some audio quality. Change back to "speex-float-3" if you don't care about higher CPU usage.

---

