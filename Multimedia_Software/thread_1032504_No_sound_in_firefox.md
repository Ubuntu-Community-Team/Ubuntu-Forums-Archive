---
title: "No sound in firefox"
date: 2009-01-06
forum: Multimedia Software
---

### Post by numbness05 on 2009-01-06
Hi everyone

Have Ubuntu 8.10 installed through wubi.
I have every thing up and running other than the audio when streaming video on the net Youtube for example...

Any bright ideas please anybody??

Many thanks

---

### Post by umechanism on 2009-01-06
> **numbness05 said:**
> Hi everyone

Have Ubuntu 8.10 installed through wubi.
I have every thing up and running other than the audio when streaming video on the net Youtube for example...

Any bright ideas please anybody??

Many thanks

Same here.
Welcome to the club.
[http://ubuntuforums.org/showthread.php?p=6505022#post6505022](http://ubuntuforums.org/showthread.php?p=6505022#post6505022)

---

### Post by AJB2K3 on 2009-01-06
Have you installed everything in accordance with the faq?
Have a look in the mixer and check nothing is muted then check in System>preferences>sound that your sound card is selected.

---

### Post by numbness05 on 2009-01-06
I think believe so... 
Flash 10 and Gstreamer I think it is..what else may I need?

Forgive me I am relatively new to Linux

Many thanks in advance
support structures like this just don't exist in Windows :D

---

### Post by AJB2K3 on 2009-01-07
> **numbness05 said:**
> I think believe so... 
Flash 10 and Gstreamer I think it is..what else may I need?
Lots, 
Various codecs,
Flac,
ffmpeg
Xine,
laem, etc

Have a long read through this
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Theres alot there to do and it took me 3 days to realize I missed loads.

---

### Post by umechanism on 2009-01-07
> **AJB2K3 said:**
> Lots, 
Various codecs,
Flac,
ffmpeg
Xine,
laem, etc

Have a long read through this
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")
Theres alot there to do and it took me 3 days to realize I missed loads.

I can watch DVDs and streaming online video with no problems after I followed the advice in the above link.  However, none of these videos have sound.  As a matter of fact, I do not have system sounds either.  Suggestions?  Ihave a very new Dell Desktop with a RealTec ALC888 sound card in it.  Sounds work just fine in Vista (dual booting) but absolutely nothing in Ubuntu 8.10.

All help is appreciated.

---

### Post by clueless_about_all_this on 2009-01-08
Same here, no systems sounds nor sound in firefox. Running Intrepid 64bits and using Logitech Z-10 USB Speakers. 

BTW, when I restart the pulseaudio daemon I get the following in syslog:

```
Jan  8 08:42:11 clueless-desktop pulseaudio[29126]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan  8 08:42:11 clueless-desktop pulseaudio[29127]: pid.c: Stale PID file, overwriting.
Jan  8 08:42:11 clueless-desktop pulseaudio[29127]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan  8 08:42:11 clueless-desktop pulseaudio[29127]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan  8 08:42:11 clueless-desktop pulseaudio[29127]: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 48000 Hz.
```

But I'm able to hear mp3 files saved on my computer but I have no system sounds nor sound in firefox.

---

### Post by tm002dy on 2009-01-08
&#19981;&#33021;&#31616;&#21333;&#30340;&#20174;&#23383;&#27597;&#21644;&#25968;&#23383;&#30340;&#25645;&#37197;&#21028;&#39321;&#28207;&#20845;&#21512;&#24425;&#20154;&#27665;&#24065;&#30340;&#30495;&#20551;&#12290;&#29616;&#24050;&#21457;&#34892;&#30340;&#20154;&#27665;&#24065;&#20896;&#23383;&#21495;&#20063;&#26377;HD90&#24320;&#22836;&#30340;&#65292;&#22240;&#27492;&#19981;&#33021;&#35828;&#20896;&#23383;&#21495;&#20197;HD90&#24320;&#22836;&#30340;&#37117;&#26159;&#20551;&#24065;&#12290; [&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.org.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.ac.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.bj.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm262.sh.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;&#32593;&#31449;](http://www.tm262.tj.cn)

---

### Post by umechanism on 2009-01-08
I've tried everything I know.  I even submitted a bug report.  Hopefully, I can find a fix but for now, I just have to use my imagination.

---

