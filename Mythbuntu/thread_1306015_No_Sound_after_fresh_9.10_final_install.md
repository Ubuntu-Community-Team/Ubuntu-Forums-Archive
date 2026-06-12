---
title: "No Sound after fresh 9.10 final install"
date: 2009-10-30
forum: Mythbuntu
---

### Post by MikeInParadise on 2009-10-30
I have just installed the final version of Mythbuntu 9.10 on a motherboard Intel D945GCLF2 (atom330) on a new seperate partition and have no sound.   The sound is fine on the mythbuntu 9.04, windows 7 and OSX partitions on this machine.

When I installed the final straight ubuntu 9.10 on another machine it too had no sound but I could go to System/Preferences/Sound and unmute it and all was fine.

On MythBuntu 9.10 there is no System/Preference/Sound

QUESTION 1: Should this be here?  If not how do you access the sound setup?

I checked the ALSA Mixer and made sure that Master,PCM and Front controls were visible and not muted.  Also I made the IEC958 and IEC958 Default PCM switch visible and tried all combinations visible.

I started reading tons of stuff about ALSA, OSS and PulseAudio to the point that my poor little brain is starting to hurt and I am confused.  Seems like OSS was the orignal sound drivers that has been changed over to ALSA and now pulseaudio is slowly being mixed in causing some opportunities for improvement.

Found these bugs in sound which I think is what I am running into:

[https://bugs.launchpad.net/mythbuntu/+bug/436792]("https://bugs.launchpad.net/mythbuntu/+bug/436792")

[https://bugs.launchpad.net/mythbuntu/+bug/460579]("https://bugs.launchpad.net/mythbuntu/+bug/460579")

Seems like the fix to this is the following:

export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

Seems like this has to be put into a file

either to their launch command or to their .bashrc
or in .profile

QUESTION 2: How do you change the launch Command? or any menu commands or add menu command in MythBuntu as I cannot find access to the menus?

QUESTION 3: What is .bashrc and where do I find it.

QUESTION 4: What is .profile and where do I find it

My Head hurts and now I need to go get my Stihl chainsaw out and go cut some wood to take out my frustration of the hours spent on this so far.... :)

---

### Post by MikeInParadise on 2009-10-31
attempt 1: to fix sound...

Looks like ~/.bashrc refers to a hidden system file in your home directory.
I guess I learned that the tilde ~ reference your home directory.

So I did applications/accessories/terminal and then:

sudo mousepad ~/.bashrc

I added a line after the check that skips is not interactive.

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# MOD 2009-10-30 Try to fix sound
export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

Tried logging off and on - no joy

Tried rebootig - still no joy :(

I tried moving this to the end of th .bashrc file and still no joy

---

### Post by dacodo on 2009-11-06
Had the same problem with my fresh installs. I have been using a venerable Sound Blaster Live! Ubuntu 9.10 works fine with the card but a fresh install of mythbuntu yields no sound. 

Gave up and installed ubuntu 9.10 and then the mythtv packages on top.... got everything working perfectly except the system just compleetly lockes up after a bit when not in use.... cant ssh into it.... nothing.

trying to figure out my next step :( try mythdora? install debian and myth on top?

9.10 seems like a very buggy release.

---

### Post by MikeInParadise on 2009-11-06
I spent way, way too much time on this and had some strange stuff happen.   I played with way too many settings and then did something and got sound in Live TV.   Figuring that this is good I changed to the next channel and the sound was gone.  No more sound on the system.

Anyways I did another clean install.  No sound.  Then I started mucking around with things and again managed to get sound without understanding the exact sequence of what I did as I was changing lots of stuff and running lots of commands that I found. 

I need to wipe out the partition once again and start from scratch but to be honest I had kept the 9.04 working version and have just been using that.  This has taken up far too much time.

Some really, really stupid stuff are things like removing the system/preferences/sound from mythTV.

When you look this up almost all the instructions are for the standard ubuntu.

Anyways I will tinker with this as time permits but it is a really low priority as I will try again in a month or so and see if it is any better.

---

### Post by paulsmith99 on 2009-11-06
May sound daft, but I lost the sound after changing the default fresh-install mythbuntu xorg.conf to my previous file from my myth 0.21 setup.

I was trying to solve a playback issue so tried the older xorg.conf (that was working for months) but for some reason Myth frontend refused to play any sound using it, despite messing with the settings. KDE start up sounds worked, it just seamed like Myth front end lost the ability to play sounds. I tried the mythbuntu session as well as KDE but no help.

I reverted back to the original fresh-install copy of xorg.conf and it worked again - don't know why.

Just sharing my experience - in case it helps. :D

---

### Post by Andrew U.K. on 2009-11-07
I'm watching this thread.
I haven't got sound from either mythbuntu 9.04 or 9.10. Sound works fine with ubuntu 9.04 and 9.10 I have also added myth to ubutu 9.04 and 9.10 but with myth on top the sound stops.

It's a time consuming affair, which like you Mike I haven't got. But you have to keep trying.

---

### Post by dacodo on 2009-11-09
Well I made progress... 

So I started over with a fresh install. Went in synaptic and installed pulse audio volume control and pulse audio device selector.

That got sound working in VLC. Rebooted, sound was down but after raising the levels in the Pulse audio mixer it worked. Tinkered with my xorg.conf to get 1920x1080. Rebooted, no sound (bear in mind I'm using 2channel audio out of a sound blaster, not HDMI... strange).

At this point I'm thinking something about the nvidia drivers is causing the problem. Uninstalled them, installed older ones.. still no sound.

Reinstalled again from scratch, this time with an ATI card in the system and only installed the open source drivers.

Again went in synaptic and installed pulse audio volume control and pulse audio device selector. Got sound working again.

Ran all updates and rebooted, still have sound. Shutdown and swapped the nvidia card back in, booted up and with much trepidation reinstalled the latest nvidia drivers in the distribution source.

Rebooted and still have working sound.... I have no idea what I fixed by doing this, but at least it's all finally working. I blame this all on pulse audio, it's a really delicate balancing act getting this all working together. (I hate to say it, but I miss XP after all this, I may like this better longterm but setup is a bitch.)

But at least I've finally purged Windows off everything but my wife's computer. 100% unix derivatives now, OS X, Mythbuntu, Ubuntu, & NET BSD. Been a long 3 weekends to get here though.

Click the link in my Sig if you want to see the systems.

---

### Post by MikeInParadise on 2009-11-21
I fiddled with this a bit and did another clean install, still diddling around with the sound.

Anyways I tried some flash stuff on this and it is just slow.

There is way too much stuff taken out of the menus such performance monitor, sound mixers, etc.  I guess I have decided that MythBuntu is just not functional enough for me.

I installed Kubuntu.  Installed mythtv using the package manager.  Installed the remote control software.

Less than 30 minutes I had reinstall with sound, remote and Myth TV working. No messing about.    Plus I love the KDE desktop.

I think that I am giving up on the MythBuntu distribution for now.

---

