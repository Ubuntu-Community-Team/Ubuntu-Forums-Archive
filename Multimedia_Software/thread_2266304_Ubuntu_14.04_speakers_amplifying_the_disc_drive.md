---
title: "Ubuntu 14.04 speakers amplifying the disc drive"
date: 2015-02-21
forum: Multimedia Software
---

### Post by Cyber72 on 2015-02-21
Getting clicks and whirs theough the speakers (laptop with small speakers plugged in). it sounds as though they are amplifying the noise made by the hard disc Any cure? Also I'd be interested to know the cause. I had pulse audio and removed that but it didn't cure the problem.

I've had so many issues since upgrading to 14.04 apart from it being the slowest OS I've ever used. It's a lemon - makes Microsoft look good.

---

### Post by sandyd on 2015-02-22
Moved to *Multimedia*

---

### Post by Cyber72 on 2015-02-22
I opened the terminal and typed [COLOR=#000080]**alsamixer**[/COLOR] then pressed enter, (some fannying about to no avail) then pressed F4 and reduced the capture to 0<>0
This has reduced the problem by 90%. It looks as though the microphone was picking up the noise and outputting it on the speakers. Still don't have a cause nor why the problem is greatly reduced and not solved. Any insight welcome.

From what I read it looks likely but not certain that the microphone is integrated with the speakers. The speakers blew some time ago, hence external USB speakers from Fasttech. So I thought maybe I can put an end to the problem by unsoldering the built in speakers. Might this create any new problems. I've never used the microphone so I won't miss it.

ps I wanted to highlight the word "alsamixer" above but couldn't see how to. Anyone care to let me in on the secret.

---

