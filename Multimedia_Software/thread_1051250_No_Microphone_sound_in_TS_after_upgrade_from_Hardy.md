---
title: "No Microphone sound in TS after upgrade from Hardy to Intrepid"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Toneri on 2009-01-26
Like title says...

After some hassle in 8.04 I finally got my Teamspeak client to work just fine when running the Windows client through wine.

Now after upgrading to 8.10, somehow the microphone just wont work anymore in Teamspeak.

Other than TS, capture works just fine (I can hear myself when not muting the mic, capture on recorder works etc)

Only way of getting microphone to work with Teamspeak is to run normal linux client which is using oss. (and no, running linux client through alsa oss or pulseaudio wont work / is not acceptable in quality)

Any ideas what to try because I'm really running out? Hate to boot Vista every day because of this little problem... :(

---

### Post by miceterminator on 2009-01-26
Hi,
is it just in teamspeak or also in skype, audirecorder etc?

EDIT:
sorry for this crap post

---

### Post by Toneri on 2009-01-26
> **Toneri said:**
> capture on recorder works etc

Like said, capture works on audio recorder and it works also on linux client of ts using oss.

---

### Post by Toneri on 2009-01-27
...anyone?

---

### Post by Toneri on 2009-01-27
okies...

Turns out it's mostly wine problem, followed one of the tutorials and basically switched wine to use oss(go to wine, configure wine, audio, check oss) -> start wine apps with "padsp" to push them through pulseaudio and now Teamspeak works.

No idea why ALSA wont work on capture in intrepid.

---

### Post by markbuntu on 2009-01-27
The alsa plugin for wine is broken and has been for a long time due to faulty assumptions about hardware which wine or any other application should not be making. Supposedly a fix is working its way to their repository but most likely by then they will have a working pulseaudio plugin and it will no longer be necessary.

---

