---
title: "No HMDI audio at all"
date: 2015-09-15
forum: Mythbuntu
---

### Post by Denis_Papathanasio on 2015-09-15
I'm running the latest mythbuntu (14.04), and the latest software update this past weekend completely fubared my audio.

The [previous solution]("http://ubuntuforums.org/showthread.php?t=2256787&") -- [http://ubuntuforums.org/showthread.php?t=2256787&](http://ubuntuforums.org/showthread.php?t=2256787&) -- i.e., cycle through all the NVidia options listed in 'aplay -L' until I find one that produces sound, and then updating the audio setting through the mythfrontend doesn't work any more at all.

Previously, the only options that worked were one of the 'plughw:CARD=NVidia' choices.

This time, there is only one -- plughw:CARD=NVidia,DEV=3 -- and it produces no sound, though the myfrontend setting is happy to accept it as valid.

This is the full output of 'aplay -L | grep NV':

```

hdmi:CARD=NVidia,DEV=0
    HDA NVidia, ID b Digital
dmix:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
hw:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
plughw:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
```

I've tried all of these as the '-D' target for aplay (e.g., aplay -D hdmi:CARD=NVidia,DEV=0 /usr/share/sounds/alsa/Front_Center.wav) but none of them produce sound.

I am using the alsa-daily ppa, so I was wondering if there was something new there which might be causing the problem.

Any suggestions?

---

### Post by MoebusNet on 2015-09-16
Are you getting sound outside of Myth ie from VLC in the Xubuntu desktop? Pulseaudio Control helped me configure sound properly from desktop; once that works then Mythaudio configuration should be as described.

---

### Post by Denis_Papathanasio on 2015-09-16
I did try that, but neither vlc nor the mythfrontend, nor any other application capable of playing audio works.

The Pulse Audio controller shows activity when an application like vlc is running (i.e., the volume bars move), but nothing comes out of the TV's speakers.

> **MoebusNet said:**
> Are you getting sound outside of Myth ie from VLC in the Xubuntu desktop? Pulseaudio Control helped me configure sound properly from desktop; once that works then Mythaudio configuration should be as described.

---

### Post by MoebusNet on 2015-09-17
The only suggestion I can come up with for now is to try: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

If that doesn't help, maybe someone else can give a hand. Best of luck!

---

### Post by Denis_Papathanasio on 2015-09-20
Right, I am very familiar with the audio troubleshooting page, and I have implemented the advice about using the oem-audio-hda-daily-dkms package.

Here's how my "Additional Drivers" are setup:

[IMG]http://i.imgur.com/LcK8njn.png[/IMG]

And this is what the Pulse Audio controller looks like:

[IMG]http://i.imgur.com/W2U3cJ4.png[/IMG]

So it all looks good, and even aplay shows me NVidia options:

[HTML]$ aplay -L | grep NV
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, ID b Digital
dmix:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
hw:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital
plughw:CARD=NVidia,DEV=3
    HDA NVidia, ID b Digital[/HTML]

But when I try any of those, I get errors and no sound:

[HTML]$ aplay -D hdmi:CARD=NVidia,DEV=0 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:722: audio open error: Device or resource busy

$ aplay -D dmix:CARD=NVidia,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
aplay: main:722: audio open error: Device or resource busy

$ aplay -D hw:CARD=NVidia,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:722: audio open error: Device or resource busy

$ aplay -D plughw:CARD=NVidia,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
aplay: main:722: audio open error: Device or resource busy[/HTML]

The setting which used to work was "plughw:CARD=NVidia,DEV=7" but that doesn't appear as a choice any more.

> **MoebusNet said:**
> The only suggestion I can come up with for now is to try: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

If that doesn't help, maybe someone else can give a hand. Best of luck!

---

### Post by blm-ubunet on 2015-09-20
Your jockey additional drivers is showing the video h/w as "GT218  Geforce 8400GS".
This can not be right.. The GT218 processor is the marketing model GT205/GT210.
IIRC the GT205/210 was not quite as HDA audio capable as the others in the 200s family.

---

### Post by Denis_Papathanasio on 2015-09-21
It doesn't make any sense to me, either.

In the end, I found this combination worked:

[IMG]http://i.imgur.com/IvT41wB.png[/IMG]

It may not be optimal, but when I scan "aplay -L" now, I do see "plughw:CARD=NVidia,DEV=7" which does give me audio, again, finally.

> **blm-ubunet said:**
> Your jockey additional drivers is showing the video h/w as "GT218  Geforce 8400GS".
This can not be right.. The GT218 processor is the marketing model GT205/GT210.
IIRC the GT205/210 was not quite as HDA audio capable as the others in the 200s family.

---

