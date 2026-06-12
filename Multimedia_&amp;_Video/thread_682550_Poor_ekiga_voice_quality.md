---
title: "Poor ekiga voice quality"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by aspora.isernia on 2008-01-30
Hi guys,
recently I installed ekiga and properly configured it to work with voipstunt and my free sip provider. I also modified the preferred codecs in order to use PCMU and PCMA that should be the best ones (I read they should be the same as G.711).

Ekiga works perfectly despite the fact that the voice quality seems "metallic": I make the difference with the Windows version of the free client of voipstunt and with the free softphone X-Lite (of CounterPath). With these two Windows programs and with the same connections that I use in ekiga, I obtain a much much better voice quality.
The difference is so evident that I prefer to switch to Windows in order to use voip services...

Has anyone some hint to improve voice quality in ekiga? Or, maybe, the problem is with the ubuntu sound server?

Many thanks!!

a.i :)

ps: I have xubuntu 7.10 and a laptop Dell Latitude X200.

---

### Post by YannickDefais on 2008-01-30
Hi,

Try to disable echo cancellation in prefs -> audio codecs.

Regards,
Yannick

---

### Post by aspora.isernia on 2008-01-31
> Hi,

Try to disable echo cancellation in prefs -> audio codecs.

Regards,
Yannick

Thanks for the suggestion, but I didn't notice any quality improvement... :(

a.i

---

### Post by Versusnja on 2008-03-07
[edit]
didnt notice you already using good codecs...

---

### Post by aspora.isernia on 2008-03-19
I start to think that is a alsa problem... Ekiga sound quality under windows is AMAZING!! Under my ubuntu it's really pooooor... :(

---

