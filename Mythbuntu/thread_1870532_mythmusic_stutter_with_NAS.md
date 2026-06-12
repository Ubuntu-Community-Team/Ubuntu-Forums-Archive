---
title: "mythmusic stutter with NAS"
date: 2011-10-27
forum: Mythbuntu
---

### Post by Saubazi on 2011-10-27
I got myself a NAS (Netgear ReadyNAS Duo). Mounted it via nfs and everything seems to be ok so far, except I am experiencing a choppy playback on mythmusic. The network speed should be ok, everything is connected with cable inside my household. Also videos and stuff play without problems - I think it is really a matter with mythmusic. I also googled and found that people have had similar probs when playing from CD.

When I was still playing the stuff directly from internal HD everything was ok. So I don't know. Is there a way to define buffer size or something for the player to resolve this issue.

There are few other things to note I did not try a real stress test BUT I fired up my laptop, started frontend (backend is the same) - mounted NAS and the playback was ok.

I did not manage to deactivate upmix from my media-PC, deactivating it and leaving device to default caused mythmusic to stuck. (not frozen, just did not play anything) - so it could be an issue with upmixing in combination with NAS - any chance increasing buffer?

---

### Post by nickrout on 2011-10-27
> **Saubazi said:**
> I got myself a NAS (Netgear ReadyNAS Duo). Mounted it via nfs and everything seems to be ok so far, except I am experiencing a choppy playback on mythmusic. The network speed should be ok, everything is connected with cable inside my household. Also videos and stuff play without problems - I think it is really a matter with mythmusic. I also googled and found that people have had similar probs when playing from CD.

When I was still playing the stuff directly from internal HD everything was ok. So I don't know. Is there a way to define buffer size or something for the player to resolve this issue.

There are few other things to note I did not try a real stress test BUT I fired up my laptop, started frontend (backend is the same) - mounted NAS and the playback was ok.

I did not manage to deactivate upmix from my media-PC, deactivating it and leaving device to default caused mythmusic to stuck. (not frozen, just did not play anything) - so it could be an issue with upmixing in combination with NAS - any chance increasing buffer?

what does your frontend log say?

---

### Post by Saubazi on 2011-10-28
AFAICS nothing, it is minimal, like needle jumping on old vinyl but it's there.
It does not seem to produce a log entry when it occurs...

---

### Post by nickrout on 2011-10-28
> **Saubazi said:**
> AFAICS nothing, it is minimal, like needle jumping on old vinyl but it's there.
It does not seem to produce a log entry when it occurs...

mythfrontend -v playback,audio

---

### Post by Saubazi on 2011-10-28
I tried that and I think this is relevant in log:

[ac3 @ 0x6515160] No channel layout specified. The encoder will guess the layout, but it might be incorrect.
2011-10-28 21:53:19.710 AO: Opening audio device 'iec958:CARD=SB,DEV=0' ch 2(2) sr 44100 sf signed 16 bit reenc 0
2011-10-28 21:53:20.001 avfdecoder.o: seek time 49
2011-10-28 21:56:30.408 Read frame failed
2011-10-28 22:01:38.986 Read frame failed
2011-10-28 22:09:06.247 Read frame failed

EDIT:

the output does not seem to come from -v playback,audio - somehow I did not get the option included in startup, although I included it in /etc/mythtv/session-settings

I'll have to take a thorough look at my startup methdos, as I have changed here and there in order to get suspend to work and I am now not sure where the frontend/mythwelcome starts...
Funnily, I also seem to have two frontend processes:
jykke     1819  1792  0 08:35 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
jykke     1822     1  0 08:35 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
mythtv    2130  1017  1 08:36 ?        00:00:25 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
jykke     2153  1868  0 08:36 ?        00:00:01 /usr/bin/mythwelcome
jykke     2250  2153  0 08:36 ?        00:00:00 sh -c /usr/bin/mythfrontend -l /var/log/mythtv/mythfrontend.log
jykke     2251  2250  2 08:36 ?        00:00:37 /usr/bin/mythfrontend.real -l /var/log/mythtv/mythfrontend.log

And in my laptop there is only one...anyway the options in those processes do not seem to include the given audio options...

---

### Post by Saubazi on 2011-10-29
Now I got something more but I am not sure I heard any stutters this time.
However, every minute or so I get this:
2011-10-29 09:58:29.184 ScreenSaverX11Private: Calling xscreensaver-command -deactivate
2011-10-29 09:59:19.184 ScreenSaverX11Private: Calling xscreensaver-command -deactivate

Can I get rid of this?

---

