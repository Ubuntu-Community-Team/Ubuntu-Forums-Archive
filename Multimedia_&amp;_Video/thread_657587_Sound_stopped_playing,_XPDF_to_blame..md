---
title: "Sound stopped playing, XPDF to blame."
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Rabbitbunny on 2008-01-03
XMMS (1.2.10) stalled mid song on my 6.06 system, only to report;

```
Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard
```

The first and secord were obviously not the problem since I had sound not a second before, so I went to Google looking for similar problems, I saw many mentions of 'esd' running in multiples so I attempted to run it.

it output:
```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```

This was a lot more detailled than XMMS' output so I asked around in various chatrooms until infi on Freenode handed me gold, seemingly off the top of his head.

```
user@host:~# for i in /dev/snd/* ; do fuser $i ; done
/dev/snd/controlC0:  27069 31100
/dev/snd/pcmC0D0p:   29872
/dev/snd/timer:      29872
```

This shows everything using the sound card and by looking at each we can find the culprit.

```
user@host:~# ps ax | grep 27069
27069 ?        Ss     0:18 xfce-mcs-manager
31294 pts/2    R+     0:00 grep 27069
user@host:~# ps ax | grep 31100
31100 ?        Ssl    0:01 xmms
31296 pts/2    R+     0:00 grep 31100
user@host:~# ps ax | grep 29872
29872 ?        Sl     0:29 /usr/bin/evince /tmp/c01120651.pdf
31298 pts/2    S+     0:00 grep 29872
```

Evince using sound? it's displaying a pdf! That's definatly not what I expected, but it can be fixed.

So in the end, By simply closing the PDF I was reading I got sound back, How easy is that?

---

### Post by bodhi.zazen on 2008-01-03
Moved to Multimedia & Video  

You may want to consider filing a bug report

	How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

