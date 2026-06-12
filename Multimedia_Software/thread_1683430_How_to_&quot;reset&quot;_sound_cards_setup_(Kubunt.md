---
title: "How to &quot;reset&quot; sound cards setup? (Kubuntu, Phonon, XINE, ALSA)"
date: 2011-02-07
forum: Multimedia Software
---

### Post by User4519 on 2011-02-07
Hey hey :)

Have a couple of very annoying problems. I recently did a re-install of Kubuntu Maverick on my HTPC/fileserver box.

It has an onboard (Realtek?) audio card, recognized as... I think, ALC888... Yeah, not sure, KInfoCenter lists a bunch:
ALSA Sequencer Device
USB 2881 Device ALSA Control Device (my DVB-T stick)
ALSA Timer Device
HDA Intel ALSA hardware specific Device
ALC888 Analog ALSA Capture Device
ALC888 Analog ALSA Capture Device
ALC888 Analog ALSA Playback Device
ALC888 Digital ALSA Playback Device
USB Audio ALSA Capture Device (DVB-T stick again)
HDA Intel ALSA Control Device

So far, so good. My problems, I believe, stem from the fact that I also threw in a SoundBlaster Live! 5.1 PCI card when I re-installed, thinking I'd use it for playing Thief (old game) in a Windows XP dual-booted, as it has the old EAX, which Thief likes.

I later changed my mind, and removed it.

I now have two problems:
1) Kmix has close to zero channels I can fiddle with. There's one under "Playback Devices" called "Internal Audio Analog Stereo", two in Capture Devices, of which one is the DVB-T stick, and zero in "Playback Streams" and "Capture Streams". It used to have a lot more.
2) In System Settings > Multimedia > Phonon, I still have my old SB Live! card listed, greyed out, impossible to remove. I've tried locating all config files related to phonon, xine and alsa on my system and wiped them to try to get rid of it, but to no avail.

Now, the greyed out SB Live! thing in System Settings can stay there for all I care, I just have this big problem that I no longer get sound out of the SPDIF output on this thing. It's connected via a long 75o coax cable to a D/A converter in my living room so that I can watch movies via XBMC and listen to music in there. And I have nowhere to enable it that I can find.

Alsamixer sees all the channels I had in Kmix on my old installation, including the digital SPDIF output, but I can only toggle it on and off, which I can hear is working, because when toggling it off, my D/A converter goes, "krkkkzz" in the living room. I just need to get sound through it :)

I have a feeling this is all because there're some settings that've gotten badly messed up from the now gone SB Live! card, but I have not a clue as to how I'm gonna "reset" this so that the audio subsystem can start over and just get it right like it did the last time I installed.

I've already configured ssh, samba, postfix, pvr, zfs, smartmontools, etc. etc. etc., so I'm hoping I won't have to do a re-install... Also because that's so damn Redmond-y :D

Anyone got a good idea?

Thanks,
Daniel

---

### Post by User4519 on 2011-02-07
Well... I'll be damned... Don't know what I did, but SPDIF is now working... :)

Would still like to know, though, if anyone knows how to get rid of the SB Live! entry in the Phonon settings thing, and somehow get back the channels in Kmix :)

---

