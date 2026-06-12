---
title: "CD ripper recommendatons and help"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by drfox on 2007-12-13
I've been playing with CD Rippers and have some questions:
I've tried Asunder, Grip, K3b, Rubyripper and Sound Juicer.
Rubyripper is nice because you can simultaneously rip FLAC and OGG, but it doesn't get the song information from the internet databases. Asunder likewise can't seem to reach the databases.
Sound Juicer and Grip only allow you to rip one output at a time. 
Is there a ripper that can download the song/artist information and also rip in multiple formats at one time?

Thanks. Larry

---

### Post by logos34 on 2007-12-13
ABCDE is the best if you want to rip to multiple formats. It can do flac, ogg, mp3/lame, aac/m4a and mpc/musepack all at once.  And add replaygain to boot.  Lots of other options too (gapless, etc. etc.)

So Rubyripper and Asunder aren't fetching track info from freedb?

---

### Post by drfox on 2007-12-13
> **logos34 said:**
> ABCDE is the best if you want to rip to multiple formats.

So Rubyripper and Asunder aren't fetching track info from freedb?

Not for me. I googled Rubyripper, and others are having the same problem.
I'll check ABCDE..., but I'm more comfortable with GUI than CLI

Larry

---

### Post by logos34 on 2007-12-13
you know, the freedb.org main server was down a few days ago.  Maybe it's down again.  Try [gnudb.org]("http://www.gnudb.org/howto.html")

---

### Post by drfox on 2007-12-13
> **logos34 said:**
> you know, the freedb.org main server was down a few days ago.  Maybe it's down again.  Try [gnudb.org]("http://www.gnudb.org/howto.html")

Maybe I'm doing something wrong...I accessed Rubyripper>Preferences>Freedb
I checked enable freedb metadata fetching. It doesn't seem to matter whether I have the next box checked. For freedb server, I've tried freedb.freedb.org and gnudb.gnudb.org and cddb.cddb.com.
My user name is drfox and my hostname is my domain. I'm behind a router, but no proxy. I even added port triggering to my router to open port 8880, but I don't know if that's wise or necessary. 
Do you have any suggestions?

Larry

---

### Post by logos34 on 2007-12-13
same here.  I'm behind a router.  I didn't configure anything.

If it's a Rubyripper issue, maybe someone else has some ideas, because I can't even get it to recognize my cdrom to read the audio disc (although it sees it well enough to open and close the tray--go figure).  But if other apps will fetch the info then it sounds like your problem is elsewhere.

If and when you solve that issue, I really encourage you to try ABCDE.  Yeah, it's cli, but after you read the man page and learn eveything it can do and how to configure the .conf file, you're hooked.  I couldn't get it to work the first time I tried it and gave up (and like you I was scared off by the terminal).  But now I use it probably more than Grip and it is one fantastic little ripper and encoder.  Not quite as secure a ripper as Rubyripper, but you can configure cdparanoia.  I've even figured out how to have it run c2 error check on the disc automatically prior to every rip, which is really nice becuase my dvd/cdrom does not have that feature.

---

### Post by elliio on 2007-12-16
About Rubyripper 0.4.4, and freedb... here are my freedb preferences, which now work!

1. Enable freedb metadata fetching (checked)

2. Freedb server: freedb.freedb.org

3. Username: anonymous

4: Hostname: port=8880

Hopefully these settings will work for you, too!

---

### Post by drfox on 2007-12-16
> **elliio said:**
> About Rubyripper 0.4.4, and freedb... here are my freedb preferences, which now work!

1. Enable freedb metadata fetching (checked)

2. Freedb server: freedb.freedb.org

3. Username: anonymous

4: Hostname: port=8880

Hopefully these settings will work for you, too!

Weird...doesn't work for me. :(

---

### Post by Angus77 on 2007-12-17
The default for me was:

```
1. Enable freedb metadata fetching (checked)

2. Freedb server: **freedb.org** *(rather than freedb.freedb.org)*

3. Username: anonymous

4: Hostname: **my_secret.com**
```

and it hasn't given me any problems.

---

### Post by Lostincyberspace on 2007-12-18
I never thought of dual ripping, That is a good idea.

---

