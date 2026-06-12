---
title: "Mic not working, can't launch alsamixer after pulse audio removal"
date: 2008-06-26
forum: Multimedia Software
---

### Post by bcardarella on 2008-06-26
I had to remove Pulseaudio to get some of my Wine applications working. I did so at the command line:

sudo apt-get remove pulseaudio

I then made sure that alsa was fully installed:

sudo apt-get install alsa  (might have been alsasound, I forget)

Anyway, all output sound is working just fine. My issue is now with the mic. Via the sound control panel I have unmuted and pumped up the volume on my mic input. No result. I tried to get into alsamixer to see if it was disabled but when I try to run the command I get this error:

*** PULSEAUDIO: Unable to connect: Connection refused

I thought Pulse Audio was removed?

Audio device listing from lspci:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


Any help would be appreciated.

---

### Post by bcardarella on 2008-06-26
I didn't post the entire error message from alsamixer:


*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

---

### Post by buntu_hugenewbie11 on 2009-03-14
Did you ever get this working?
I have the same problem.

---

### Post by peterhoeg on 2009-08-21
Sure, just do the following

rm $HOME/.asoundrc
asoundconf list (make note of the card name - for me it's called Intel or NVidia depending on the machine)
asoundconf set-default-card NAME_OF_CARD_FROM_PREVIOUS_STEP

And presto, all is peachy again.

---

