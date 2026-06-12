---
title: "Purging/Installing ALSA Drivers?"
date: 2010-03-29
forum: Multimedia Software
---

### Post by wbee on 2010-03-29
Hello,

I'm reading LordRaiden's guide above and have some questions.

1.Here is the relevant part of ```
lspci -v
```:

```
04:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```

Note the <access denied>. Is that why my sound is not working?

Is there a way to restore the access without having to go through a Purge/Reinstall? 

-----

2. The instructions to purge and then install the ALSA drivers warn me it will also remove my Gnome desktop. It then provides the code to reinstall it,(along with the gdm).

Will the purge that will remove the old corrupted(?) drivers remove the desktop before a reboot or after?

If if removes the desktop after a reboot,do I install the fresh drivers before the reboot?

If it removes the desktop after a reboot,should I reinstall the gnome desktop before a reboot?

If it removes the desktop after a reboot,should I reinstall the desktop at that point?


**If it does not,will it prompt me after the reboot to install the desktop?

--------

Thank you.

((Moderator,I know I have something else in this section asking a similar question,but it's been about a day,so this is a bump,"in spirit",because maybe my title is confusing in the other one.))

---

### Post by lidex on 2010-03-30
That's the typical output for that command. No need to purge alsa. What exactly is your audio problem?

---

### Post by wbee on 2010-03-31
Lidex,

Over the weekend,I booted up and the sound did not work. Previous to that,it had worked perfectly.

I purged and reinstalled the drivers,reinstalled the desktop,and rebooted,still no sound.

I checked all the connections and seating of the sound card---all that is fine. The bios is set on "disable" the onboard sound.

When I boot up,I get that annoying pop through my speakers,which tells me the soundcard and speakers are working. But I no longer get the drumbeat sound I used to get.

I get no sound from VLC,Rhythmbox,the audio portion of UTUBE,an fm stream,and a cd.

---

### Post by lidex on 2010-03-31
Try and think what may have changed on your pc recently. Updates to packages, etc. Could have been further back but just became evident after reboot. It didn't just quit for no reason and knowing where to look is a giant help.

---

### Post by wbee on 2010-04-01
Lidex,

These two possibilities may be way off the wall,but here are two weird things:

1. Whatever knocked out the sound changed the bios setting for the on board sound card from "disabled" to "auto". I changed it back to "disabled"(I have a pci sound card),but still,no sound.

1a.Does disabling the on board sound on the bios automatically blacklist the on board sound? Is it possible that even with the setting on "disable" that the on board sound could still be interfering,and if so,how do I check to see if the onboard sound (AC 97) is blacklisted.

2. I often listen to VLC while I'm doing stuff,including using the "Google Books" window. A day or two before the sound went out,I was listening to a compact disk using VLC and used the magnifying glass icons on the Google Books screen to increase the print size. Could that somehow have piggy backed onto something,and confused the sound driver into trying to recongize the command the magnifying glass icon sent?

---------

Those are the only two instances that come to mind.

**EDIT:** I tried the live disk and the sound worked perfectly. Also,I have the KDE desktop installed along with the Gnome. I was in KDE and whatever knocked out the audio also knocked out the Logout function in KDE. I had to physically toggle the on/off switch on my power surge bar---which I hate to do.

---

### Post by lidex on 2010-04-01
Two things right off the top of my head:
(1)Re-installing alsa resets the mixer levels - it mutes them. Check in alsamixer. Terminal command:
```
alsamixer
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels.
Use the left/right arrow keys to select and up/down arrow keys to change levels.
(2)Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by wbee on 2010-04-02
Lidex,

Thanks,but no joy.

The guys at Launchpad,especially the audio team,are,I guess,working against a deadline to release LL. And they have to triage what they do.

Soooooo......While I'm curious,since I know it works from the live disk,I'm going to reinstall it,since Launchpad has all my ALSA and PULSE data,if it ever helps them solve something similar.

---

### Post by lidex on 2010-04-02
Did you run the alsa-info script and if so where is the output text?

---

