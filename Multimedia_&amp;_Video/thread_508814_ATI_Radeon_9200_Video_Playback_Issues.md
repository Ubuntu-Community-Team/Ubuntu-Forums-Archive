---
title: "ATI Radeon 9200 Video Playback Issues"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by regomodo on 2007-07-24
Hi, i know that there are a lot of issues with ATI cards but i gave a bash at installing Ubuntu on my family's comp as i thought a 5year old g'card would be supported.. Everything works off the bat except for 1 thing.

I can play videos but when maximised the playback becomes really choppy. DVDs are fine. Avi's and mpegs aren't.

What could be the issue as i've installed codecs through automatix (meh, not how i usually do it) and used the default ATI drivers?

Could anyone help? Cheers

---

### Post by regomodo on 2007-07-25
bump

---

### Post by Harmshi on 2007-07-25
I seem to have the same problem. have you tried to disable desktop effects / compiz / beryl? For me videoplayback only works well with the opensource ATI driver if desktop effects are disabled.

I've been looking for a better solution, but have not found any yet.

---

### Post by regomodo on 2007-07-25
> **Harmshi said:**
> I seem to have the same problem. have you tried to disable desktop effects / compiz / beryl? For me videoplayback only works well with the opensource ATI driver if desktop effects are disabled.

I've been looking for a better solution, but have not found any yet.

no. i haven't got those enabled. i did try that but it was horrendous.

this ubuntu for my family's computer is getting more and more annoying ([http://tls.sf.net](http://tls.sf.net) is down so i'm going to have my brother bitching at me until i get aMSN sorted). I've wanted to "impress" them but it's been a day and i've had complaints all the damn time.

Please guys, help. I'm always contributing and i never get any answers to my questions. Take a look if you don't believe me. It constantly feels like i'm being ignored.

---

### Post by regomodo on 2007-07-25
bloody typical. I bumble my way through "guides" which don't work. This -->> [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) crashed my xserver so i fixed it with a 

$ sudo dpkg-reconfigure xserver-xorg

Added these lines as an idea
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

And restarted the xserver. That seems to have fixed the video issue but everything seems a little laggy in general.

This whole "community" is feeling like an elusive thing for me. Unless you are asking a question which has been asked since forever you haven't got a hope in hell.

Cheers, again. If you do have any ideas please, please, please post it here.

---

