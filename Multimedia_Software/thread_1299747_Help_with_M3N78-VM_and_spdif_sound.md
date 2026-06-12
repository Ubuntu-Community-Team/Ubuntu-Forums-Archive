---
title: "Help with M3N78-VM and spdif sound"
date: 2009-10-24
forum: Multimedia Software
---

### Post by tibbsthecat on 2009-10-24
I am trying to get surround sound working on this motherboard using optical out, connected to a stereo receiver.

The motherboard BIOS revision is up-to-date.

"aplay -l" indicates that the audio device is VT1708B.

Running gnome mixer I see options for IEC958 & IEC958 Default PCM & a third IEC958, all of which are checked.  Everything is un-muted.

"alsamixer" also indicates three IEC958 options all set to "00" with no sliders.

"aplay -L" shows a:

iec958:CARD=NVidia,DEV=0
    HDA NVidia, VT1708B Digital
    IEC958 (S/PDIF) Digital Audio Output

I edited "/etc/pulse/daemon.conf" with "default-sample-channels = 6" in an attempt to enable 5.1 surround sound, as I have 5 speakers with a subwoofer.  

In Ubuntu Sound Preferences I only have two options for Digital IEC958 - Digital Stereo Duplex & Digital Stereo ("IEC958" Output + Analog Stereo Input, which I have selected.  It does not seem to recognize 5 speakers.

Everything appears to be properly recognized but I cannot get sound.

Can anyone help?  I'm not sure if this could be a configuration problem, a problem with ALSA or a problem with pulseaudio.  If someone would be kind enough to walk me through some configuration/testing steps that would be much appreciated.

---

### Post by servicetech on 2009-10-24
I have the same board and can't get SPDIF to work with Windows 7 either (W7 doesn't even pick it up as one of the devices). I'm thinking it's a hardware issue.

---

### Post by oxymoron on 2009-11-02
I'm just this minute downloading 9.10 so will report back with my 9.10 findings.

As for windows 7 i have SDIF working, the option is just exceptionally well hidden within the Asus sound (realtek?) control panel, I think its under advanced. It is there!!!!!! It just extremely hard to see the button or switch.

I would provide more details but my HTPC is not plugged in atm.

---

### Post by Laryllan on 2009-11-10
The board has an additional internal SPDIF connector, which seems to be used by default.

The ALSA driver (snd-hda) needs to patched to detect alls digital I/O ports. Look here for more details (you can log in as guest):
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4330)

---

### Post by Laryllan on 2009-12-22
UPDATE: I built a SPDIF connector myself for the internal port - it's working. :)

---

