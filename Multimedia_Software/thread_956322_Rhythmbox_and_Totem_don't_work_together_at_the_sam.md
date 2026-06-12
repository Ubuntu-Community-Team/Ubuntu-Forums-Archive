---
title: "Rhythmbox and Totem don't work together at the same time anymore"
date: 2008-10-23
forum: Multimedia Software
---

### Post by Bazon on 2008-10-23
Hello! 

After upgrading to hardy, audio playback in totem and rhythmbox doens't work anymore at the same time.

When I first start rhythmbox, totem stay quite without an error message.
When I first start totem, rhythmbox says: 
"Could not open audio device for playback. Device is used by another application."

Messages and configuration while totem is playing are visible in this image:
[[img]http://img293.imageshack.us/img293/6863/audioprobsic1.th.png[/img]](http://img293.imageshack.us/my.php?image=audioprobsic1.png)

How can I make them work at the same time again?

---

### Post by Bazon on 2008-10-23
additional comment:
When I switch to ALSA, both applications work fine together, BUT only on my onboard soundcard, not my PCI-soundcard which I like to use. 
Although my /etc/modprobe.d/alsa-base file contains:
```
options snd_ens1371 index=0
options snd_via82xx index=1
```
which worked before Hardy and made my snd_ens1371 default. 

(And:
```
cat /proc/asound/modules
```
shows
```
 0 snd_ens1371
 1 snd_via82xx
```
so that *_schould_* work...)

Also, neither rhythmbox nor totem appear in PulseAudio Volume Control.
(See screenshot posted before)

---

### Post by Bazon on 2008-10-23
up for afternoon in america.... ;-)

---

### Post by Bazon on 2008-10-24
no one knows??? :(

---

### Post by xc3RnbFO8P on 2008-10-24
This worked for me:
[http://ubuntuforums.org/showthread.php?t=852822]("http://ubuntuforums.org/showthread.php?t=852822")

---

### Post by Bazon on 2008-10-25
That did not change the situation.... :-(

---

### Post by xc3RnbFO8P on 2008-10-25
Yes it doesnt, I was wrong.
[http://ubuntuforums.org/showthread.php?t=800242]("http://ubuntuforums.org/showthread.php?t=800242")

---

### Post by Bazon on 2008-10-25
Ah:

> **billgoldberg said:**
> Correct me when I am wrong, but this sounds like the famous PulseAudio bug.

In that it can only use one source at the time.

I use ALSA instead of PulseAudio because of this. However it seems this bug has been fixed in Intrepid.

OK, so I think it's reasonable to wait the few days for Intrepid...

---

### Post by Bazon on 2008-11-03
After having read about some problems with 8.10 which could affect me I stayed at 8.04.

And finally, I found a solution to make Rhythmbox work properly again:

```
asoundconf unset-pulseaudio 
```
(in terminal of course...)

Yippie! :-) I thank myself... ;-)

---

### Post by Bazon on 2008-11-03
Aaargh!

After a restart, the problem is as before!
The sound system drives me crazy....  (envy)

---

