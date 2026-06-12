---
title: "[SOLVED] Intrepid /etc/modprode.d/alsa-base no longer seems to work."
date: 2008-11-02
forum: Multimedia Software
---

### Post by AlexEagar on 2008-11-02
In Hardy, I used /etc/modprode.d/alsa-base to make my Audigy2 card my default audio card. I added the following lines to that file.

options snd_emu10k1 index=0
options snd_hda_intel index=1

Now when I add those lines to that file it doesn't seem to have any effect. I can even delete the file and my audio just keeps on running through the integrated Intel audio. My computer is a Dell 530. I upgraded from Hardy. Why don't those lines work any more?

The command 'cat /proc/asound/modules' returns the following.

 0 snd_hda_intel
 1 snd_emu10k1

Like I mentioned, in Hardy I was able to change that output so that emu10k1 was 0 and hda_intel was 1. But now I can't seem to change that setting.

The integrated audio works and the Audigy2 audio does not work. Could someone please help me get the Audigy2 sound working?

---

### Post by AlexEagar on 2008-11-02
I got my sound working. I unchecked 'Audigy Analog/Digital Output Jack' within the Switches tab of the Volume Control. It had to be checked in Hardy. I then enabled "Audigy 2 ... Multichannel Playback (ALSA)' within Sound Preferences. Then in VLC advanced options I set the ALSA device to 'Audigy 2 ... PCM Playback (hw:1,0).' I didn't have to change anything for Rythmbox or Movie Player. The solution didn't have anything to do with that the default sound device order.

Ugh, Flash sound doesn't work. That'll be a project for another day.

---

### Post by AlexEagar on 2008-11-03
Well, I got my Flash sound fixed. I'm not sure exactly what part of what I did fixed the problem. I threw away .asoundrc.asoundconf .asoundrc and .pulse-cookie. I think they were all in my home directory. I didn't want to log out and log back in, so I ran 'pulseaudio -k' and 'sudo pulseaudio -k' and then 'pulseaudio &' followed by 'exit'. I then restarted Firefox and Flash sound was working.

This erased the value in VLC. I just had to set it again.

---

