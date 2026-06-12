---
title: "VLC = Doesn't save default audio volume level."
date: 2008-07-19
forum: Multimedia Software
---

### Post by Roasted on 2008-07-19
When I open VLC, I noticed that if the application's volume is 100%, sometimes (sometimes) I may get some clipping at high volume. But, if I back off of VLC's volume a bit, and compensate it by cranking the volume on my system more, it's fine. So, naturally, I wanted to set my default volume lower so it didn't come on as 100% all the time.

So, there's a feature for this under preferences. If I set it and hit save, close VLC, reopen VLC, it saves.

But if I close VLC and put in a DVD, which opens VLC automatically, it's kicked back to 100%. Why?

---

### Post by steveneddy on 2008-07-20
open up your /home folder, hit ctrl+h

scroll down until you see a folder names

.vnc

open it up

open the file named

vlcrc

scroll down to

Default audio volume (integer)

Delete the # sign before the line.

Save

restart VLC and see what the volume is now.

adjust as necessary

---

### Post by pauper on 2008-07-20
Maxed out PCM setting may cause some distortion. Check yours and bring it down
to around 80%.

---

### Post by Roasted on 2008-07-20
steven, thanks, but that didn't work. If I close VLC and reopen it, my volume is adjusted. However, if I have VLC closed and I put a DVD in or click on an mpg file and VLC opens as a result, the volume just shoots back to 100%.

pauper - Thanks. I know a little bit about PCM levels, so I keep mine at 74% all the time just to avoid any distortion.

General Question - Would OSS result in a difference in sound quality? Or would it pretty much give me the same results alsa is already giving me?

---

### Post by pauper on 2008-07-20
Well, having said about clipping issues occurring every so often, you definitely
need to try out OSS. Just for the sake of comparison. There are claims about
far out superiority in contrast to ALSA on the same hardware: more clear sound,
higher volume. Why claims? I have a sceptic attitude to anything that I didn't
go through myself (read: I don't have any experience using OSS).
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)
[http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

For my part, I haven't had any problems with ALSA so far: the headphone volume
never needn't to be cranked up more then a halfway; front speakers don't produce
any kind of distortion or choppiness at full (to my non-musical ears :)) and
it's quite loud enough for me; of course there will be some kind static, heard
at full volume without any audio source. So at this point I'm satisfied with
ALSA. If you feel that something doesn't work out well for you--get a second
opinion--have a go with OSS:
[http://www.opensound.com/download.html](http://www.opensound.com/download.html)

---

