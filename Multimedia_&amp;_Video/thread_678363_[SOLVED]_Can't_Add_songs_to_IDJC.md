---
title: "[SOLVED] Can't Add songs to IDJC"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by LinuxLlama422 on 2008-01-25
...i drag them in, but they don't show up on the list....

is it a problem with the jack server or my mp3 files, i tried dragging and m3u file in too, and that doesn't work.

---

### Post by LinuxLlama422 on 2008-01-26
i have no idea....

---

### Post by schaumkeks on 2008-01-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/154880](https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/154880) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **LinuxLlama422 said:**
> ...i drag them in, but they don't show up on the list....

is it a problem with the jack server or my mp3 files, i tried dragging and m3u file in too, and that doesn't work.

This is maybe related to the Bug [IDJC MP3 Playback problem]("https://bugs.launchpad.net/ubuntu/+source/idjc/+bug/154880").

---

### Post by LinuxLlama422 on 2008-01-26
ok

so, i upgraded to 7.0

and now when i go to the server button, it is greyed out when i switch it to shoutcast...

---

### Post by schaumkeks on 2008-01-27
> **LinuxLlama422 said:**
> ok

so, i upgraded to 7.0

and now when i go to the server button, it is greyed out when i switch it to shoutcast...

Have a look at my comment in the same bug report :)

Bye, Sven

---

### Post by LinuxLlama422 on 2008-01-27
somehow my mind told me there was another answer in that bug report. lol.

---

### Post by schaumkeks on 2008-01-27
> **LinuxLlama422 said:**
> somehow my mind told me there was another answer in that bug report. lol.

Sorry for that, I didn't test enough.
But now I have spent some time compiling idjc myself. I didn't get mp3 streaming support into 0.7.0 possibly because of this problem during configure:
```
checking for lame_init in -lmp3lame... no
```

Then I tried to convince 0.6.12 to play mp3 and it works for me. You can try my [inofficial IDJC deb package]("http://user.cs.tu-berlin.de/~svenh/linux/idjc/") and report if it works for you. Playing FLAC should work at least after modifying the appropriate line of the file /usr/share/pycentral/idjc/site-packages/idjc/idjc_config.py to
```
flacenabled = 1
```
and installing package "flac".

Bye, Sven

---

### Post by Steveway on 2008-01-27
If you want more recent .deb files then check out my signature.
I made .debs for the past few releases and try to keep it up to date.

---

