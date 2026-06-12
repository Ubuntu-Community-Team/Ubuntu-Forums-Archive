---
title: "Soundcard not detected"
date: 2008-06-10
forum: Multimedia Software
---

### Post by miickEe on 2008-06-10
This was posted some time ago in the Sound sticky but has not been solved.

> 
Help. Help help help help help. Help.

I moved from 8.04 to 7.10 to avoid problems and now I've walked straight back into another bloody problem. No sound. First it was CRAP sound, now NO sound.

Ok.

I did everything I did normally in 8.04 (which was specified in full in this tutorial) in 7.10 and it does not work..

Now, even after reentering sudo modprobe snd-emuk10k1, when I do
cat /proc/asound/modules

I get
0 snd_via82xx

When it used to be
0 snd-emuk10k1x
1 snd-via82xx

I don't even know why that via82xx is there, I don't want to use my ONBOARD sound.

I've kept purging alsa and whatever and it does nothing.

Sound is tinny with onboard (via82xx), I want my emu10k1 back.

NOTE: When emu10k1 driver was installed, from experience in hardy some channels needed to be muted to get good sound, otherwise there would be heaps of distortion. I tried the same things and unmuted only the channels I needed and BAM, still distortion, still crap sound. Now emu10k1 is not even an option, it's early in the morning and I just want my damn sound to work so I can sleep.


Any suggestions? I have sound now but it's with the onboard device, which is (IMO) pretty lousy.

---

### Post by ibutho on 2008-06-10
If you have two soundcards, disable the onboard soundacard via your motherboards BIOS configuration tools and see if that helps.

---

### Post by miickEe on 2008-06-13
I got the emu10k1 soundcard device to work, however, as always with ubuntu and my sound card, they clash. First it ran nicely (as always), then decided to screw up. The sound heavily distorts. Sometimes this is fixable by going into alsamixer and muting unneeded channels, which sometimes is the cause of the distortion.

After playing with alsamixer I figured it has nothing to do with the channels.

I'm now forced to, again, listen to music with the onboard card, with no real depth or clarity as compared to the sound card. I just wish it would work.

---

### Post by markbuntu on 2008-06-13
I had problems with my two sound cards until I went to a pure alsa setup. First, I stopped pulseaudio from starting at boot with bum (Boot Up Manager). Then I made sure that alsa-utils was loaded in System Admonstration/Services. 

Then I made sure I had all of these:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)

libasound2-plugins (jack, OSS, pulseaudio)

libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

Then I set my default alsa sound card to the proper card and set all other defaults to alsa. reboot, adjust in gnome-alsamixer which has a few more things than alsamixer and everything works.

I tried all the pulseaudio how tos , multimedia foolproof guides, etc, and the one good thing I ended up with was flash 10b and the new libasound2 which fixed the flash audio problems so flash now plays along with other sound apps rather than tromping them. I got that from here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

The rest of the instructions did not work for me and eventually killed all my sound so, back to alsa.

---

