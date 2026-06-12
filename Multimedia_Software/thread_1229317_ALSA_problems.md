---
title: "ALSA problems"
date: 2009-08-01
forum: Multimedia Software
---

### Post by Apollo2366 on 2009-08-01
Hey, I think this is actually my first post here. Anyway, I've been fighting Ubuntu's sound system ever since I installed Intrepid, sometime in the spring. I was initially having trouble using sound-recorder and gtk-recordmydesktop, but then all of a sudden (in the middle of a session) I found that there was no sound output. I followed this : [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) and it sort of solved my problem, but everytime I started a new session, I'd have to run sudo alsa force-reload in order to restore audio playback.

Recently however, I decided to "upgrade" to jaunty (a horrible idea, as it turns out.) I ran the upgrade, restarted my machine, and I've been unable to get any audio output ever since. Not even the login screen sounds, which had always worked in Intrepid. I've already been to what feels like every troubleshooting guide there is, and nothing has helped in the slightest. The only interesting thing to come of any of them is that I seem to have a very strange audio setup. I'm using the 1.0.18rc3 ALSA driver and the VIA VT1708S codec, which is not mentioned anywhere in my Alsa-Configuration file. I really need help on this. It's making me hate Ubuntu. Seriously.

Troubleshooting guides I've visited:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://alsa.opensrc.org/index.php/AlsaFixing](http://alsa.opensrc.org/index.php/AlsaFixing)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

My Alsa-Configuration file:
[http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=30499cf77d5628968a9347b3a6440a0064713eaf;hb=4c767126ddc90264b8d6584548f4aa859216f481](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=30499cf77d5628968a9347b3a6440a0064713eaf;hb=4c767126ddc90264b8d6584548f4aa859216f481)

My sound setup info:
[http://www.alsa-project.org/db/?f=d7132e79422d5f4c16417968c20eb5a2fa5d1432](http://www.alsa-project.org/db/?f=d7132e79422d5f4c16417968c20eb5a2fa5d1432)

---

### Post by ArmenianLeader4 on 2009-08-02
I don't know if you ever had Windows XP, but I do know that I had a similar problem when I had it. I was able to track down the process that was the cause of the problem, and as it turns out, a specific process called "svchost" was not running, and thus providing no sound. I haven't been able to find a similar process on Jaunty yet, but that may be the source of your problem. If not, you can always install a new sound device in your computer (although there should be no reason that your current one doesn't work.)

---

### Post by Apollo2366 on 2009-08-02
Thanks, but I don't think there is a process that's analogous to svchost in Ubuntu. Also, I REALLY don't want to resort to getting a new sound card. I know that mine's still physically ok, it's just some part of my configuration that's the problem. It has to be.

---

### Post by Apollo2366 on 2009-08-03
Bumping. No one has any idea? Also, I tried to get some audio while running from the Live CD, but I got the same behavior as my install. When I was having trouble before, the same thing happened, the problems from the cd and from my install were identical. Why is this? Does the Live CD take any configuration from the hard-drive?

---

### Post by freakalad on 2009-08-03
I'd hazard a guess & say that the problem is not so much ALSA, but PulseAudio. 
PA has been an absolute nightmare from the get-go, there's been much griping about it, and my personal feeling is that the matter is still pretty far from resolved.

You can try this: from your synaptic manager, remove pretty-much all traces of PA, except for a library that I think is required by some other apps (libpulse0, I think). 
Reboot, log in & load up `gnome-sound-properties`, & select & test the devices that work for you

I'm a pretty big Ubuntu fan, but I seriously thing that the ball was BADLY fumbled on this one...
Hopefully this matter gets resolved for Koala, but we'll have to wait & see

---

### Post by Apollo2366 on 2009-08-03
freakalad, in Synaptic, if I remove pulseaudio it also forces me to remove ubuntu-desktop, and I'm pretty sure I don't want to do that. Marking libasound2-plugins, pulseaudio-esound-compat, libpulsecore9, and gstreamer0.10-pulseaudio also mark ubuntu-desktop for deletion.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by Apollo2366 on 2009-08-03
Well I got my sound to work again. I switched everything to OSS in Sound Preferences and I get playback from Rhythmbox. No playback in Firefox though. I wonder why that is? Also, when I switch songs in Rhythmbox, I get a popping sound from my speakers and I cannot run two audio applications at the same time. Any suggestions on any of those three? Also, should I still remove Pulse Audio?

---

### Post by Apollo2366 on 2009-08-05
SOLVED: [http://ubuntuforums.org/showthread.php?t=1134447](http://ubuntuforums.org/showthread.php?t=1134447)

---

### Post by silvagroup on 2009-09-08
My problem with sound started by upgrading to kernel 2.6.28-15. Went back 2.6.27-11 and all sound works fine.
From Launchpad it appears that there have been some bugs introduced with kernels after 27-11.

---

