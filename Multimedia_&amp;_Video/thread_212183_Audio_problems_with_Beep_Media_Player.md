---
title: "Audio problems with Beep Media Player"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by mdh on 2006-07-09
Hi ubuntu users,

I installed BMP and it looks very impressive, but I ran into problems right away. When I try to play any audio I get the following error message
[I][CENTER]
Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.[/CENTER][/I]

I get the same error messages with xmms too, but oddly enough mplayer and rythmbox plays just fine. Any thoughts on what might be wrong ?

---

### Post by mdh on 2006-07-09
Resolved :p 

This tip from xmms homepage helped to get it going [http://www.xmms.org/faq.php#Running5](http://www.xmms.org/faq.php#Running5)

I had to change the permissions of /dev/dsp and /dev/mixer.

---

### Post by codypumper on 2006-07-09
Beep media player has never worked for me... have you used Automatix?

---

### Post by mdh on 2006-07-09
I used easyubuntu to install the necessary audio codecs. Beep media player works like a charm after changing the permissions for /dev/dsp and /dev/mixer files. 

Do you get the same error messages that I reported for BMP ?, if so check the permissions for /dev/dsp and /dev/mixer. Here are my permission settings

```
crw--w--w- 1 root audio 14, 3 2006-07-04 09:42 /dev/dsp

crw-rw-rw- 1 root audio 14, 0 2006-07-04 09:42 /dev/mixer
```

If your permissions right then probably it might be an issue of missing codecs.

---

