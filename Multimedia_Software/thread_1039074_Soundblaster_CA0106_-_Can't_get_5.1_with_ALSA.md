---
title: "Soundblaster CA0106 - Can't get 5.1 with ALSA"
date: 2009-01-14
forum: Multimedia Software
---

### Post by blaine1984 on 2009-01-14
I understand this problem has been discussed many times, yet i tried to follow the steps suggested to other thread starters and sooner or later we part ways: they manage to resolve, I don't... I'd be grateful if someone could try to help me in this matter.
I've got 2 Soundcards on my PC: an integrated one and a Sound Blaster Audigy.
Actually, my 5.1 system is connected to the Audigy.

In System ---> Preferences ---> Audio ---> Devices (btw... sorry if i mismatch something but my Ubuntu isn't in English) i've got a WIDE choice of possible devices:

Sound Events:

Eventi Sonori:

ALi M5455 with ALC850 ALi M5455 - IEC958 (ALSA)
ALi M5455 with ALC850 ALi M5455 (ALSA)
Audigy SE [SB0570] CA0106 (ALSA)
Audigy SE [SB0570] CA0106 (ALSA)
Audigy SE [SB0570] CA0106 (ALSA)
Audigy SE [SB0570] CA0106 (ALSA)
ALi M5455 with ALC850 ALi M5455 (OSS)
ALi M5455 with ALC850 ALi M5455 (OSS)
ALi M5455 with ALC850 ALi M5455 (OSS)
Audigy SE [SB0570] CA0106 (OSS)
Audigy SE [SB0570] CA0106 (OSS)
Audigy SE [SB0570] CA0106 (OSS)
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
Server audio PulseAudio

Same choices under Music and Movies and under Videoconference (?).

The test button works only if i choose "Audigy SE [SB0570] CA0106 (ALSA)" or "Audigy SE [SB0570] CA0106 (OSS)" (well, one of them).

Keeping the first one, Audigy SE [SB0570] CA0106 (ALSA), from these settings, I went to configure the video player.

In my VLC player under Output Modules ---> ALSA the choice is still wide enough:

ALI M5455: ALi M5455 (hw:0,0) ----> No Audio
ALI M5455: ALi M5455 IEC958 (hw:0,2) ----> No Audio
CA0106: CA0106 (hw:1,0) ----> Side-Frontal Speakers working (everything else muted)
CA0106: CA0106 (hw:1,1) ----> Side-Back Speakers working (everything else muted)
CA0106: CA0106 (hw:1,2) ----> Front-Central Speaker & LFE working (everything else muted)
CA0106: CA0106 (hw:1,3) ----> Still no audio.

Seems almost like all my analog exits has been mapped on different devices... :(

Desktop mixer is set right (no IEC958 switch... I'm on analog), Analog LFE, Front, Center, Rear, and Side all at middle value (working on CA0106 Alsa MIXER).

I've tried even to run alsamixer -c 1 from terminal, and even inside there everything is fine.

p.s.
MP3 has the same problems, using Rythmbox only the Front-Side speakers works, Rear, Center & LFE are dead.
[COLOR=gray]Firefox, for the last, is completely silent.
Managed to fix this by myself by configuring PulseAudio. Yet it's still just 2.0 and VLC won't see PulseAudio as a Output Module (there is no option to set it at all)[/COLOR]

p.p.s.
About the analog exits on different devices, running aplay -l shows 4 different entries for CA0106... all the same but with Device 0, 1, 2, 3... I'll try to switch Ubuntu to english so I can paste something here.

---

### Post by blaine1984 on 2009-01-14
up (i hope it's not forbidden to up 2nd page threads)
Any ideas?
Please don't make me switch back to windows to watch movies :(

---

