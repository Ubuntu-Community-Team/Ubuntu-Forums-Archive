---
title: "sound guru needed"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by exbootie on 2006-01-16
multimedia is shot!. I have AC97 onboard sound by C media.
K mix - all switches are on, volume levels are up.
I get the following error messages:-
CD ripper:- "malformed URL "   forum search- nil result
                                                 google search - seems to be a security issue where the program is trying to access root folder and not the designated folder.
Kaffeine:- error "no URI handler implemented" google search -  nil result.
Amorok:- cannot test as there is no installed media yet.
Xmms:- will not load.
Kscd:- WORKS but only because I have connected on board sound header directly to dvd rom drive.
Question! . Is this a problem with Alsa, do I need to enable processor rendered sound, if so how please.there does not appear to be any options in GUI to do this. will I have to try to install OSS. I have never yet been able to do this sucessfully in other distros. thanks in advance for any advice.I forgot to say all system sounds are OK.I have very limited experience of CLI.

---

### Post by az on 2006-01-16
[QUOTE=exbootie]multimedia is shot!. I have AC97 onboard sound by C media.
.[/QUOTE]

I take it you are running kubuntu.  Kubuntu uses arts for sound.  What does the KDE sound thinggy in the control panel tell you about sound?

Also, did you set up a software modem?  Sometimes an AC97 codec modem puts you in an either/or situation with your sound card.  You would have to dissable the modem to get sound, in that case.

---

### Post by exbootie on 2006-01-16
Yes I am using Kubuntu (breezy). No I do not have any modem installed . ethernet NIC to broadband connection.
Sound card info as follows:-
 sound driver: 3.8.1a-980706(ALSA v1.0.9 emulation code)
kernal linux 2.6.12-10386# thur dec 11.37:10 UTC 2005 i686
config options 0
installed drivers
Type 10: ALSA emulation
card config
VIA8237 with CM19761 at   0xd000 irg 22
audio devices
0:VIA 8237(DUPLEX)
synth devices NOT ENABLED IN CONFIG
midi devices NOT ENABLED IN CONFIG
mixers 0: C-Media electronics CM19761

---

