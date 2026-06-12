---
title: "Compiling OSS on Ubuntu"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by Desolator on 2007-12-31
After lots and lots of wrong guides and so, I thought I'd update the script by Lavendem from 4Front Technologies to do it. Well, I've finished it and here is a copy of my post on the 4Front Technologies forums (the script is attached here as well):

> Alright, after some more testing and modifications, I've finished rewriting Lavendem's script that installs OSS on Debian-like systems. It is tested in Ubuntu 7.10 (Gutsy Gibbon) and should work without any problems.
 I've licensed it under the X11 license (aka the MIT license), and I encourage you to modify it and share your modifications.

Here it is: [http://paste.ubuntu-nl.org/50350/](http://paste.ubuntu-nl.org/50350/)

Paste it in a file, preferably "compile-oss.sh" and then chmod it:
```
$ chmod u+x compile-oss.sh
```

Then simply run the script:
```
$ ./compile-oss.sh
```

It will remove ALSA and any OSS emulation and will install ESD for OSS. Then it'll download the OSS source, compile and install it. Then after a restart, change your system (and the player's you use as wel, if it supports that) sound system to OSS (if the player uses ESD, this is unnecessary).

I'd like someone to figure out how to install aRTs for OSS instead of ESD on Kubuntu, since I don't have a Kubuntu install, and I'm not willing to download and install a full desktop system just for a few changes.

Thank you and happy New Year!

If you are really wondering why bother installing OSS, I can tell you in a flash: The old OSS 3.8 was deprecated for a good reason (it's 10 years old), however, 4Front has continued development as a proprietary product, and this year it's been GPL'd, and IMO. it's better than ALSA in many aspects. Here's some further reading:

[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)
[http://4front-tech.com/hannublog/?p=5](http://4front-tech.com/hannublog/?p=5)

---

### Post by Yellow Pasque on 2007-12-31
Yeah, ALSA doesn't work for a lot of people and when they're ready to give up, I try to steer them towards the OSSv4 .deb file as an alternative.

---

### Post by Desolator on 2008-01-01
I'd use the .deb only for cards which have only proprietary drivers, as compiling OSS will reduce the latency quite a bit, and it only takes 5 minutes here on a 600 MHz P3 CPU.

---

### Post by mister_mm on 2008-01-29
When I try to run script

./compile-oss.sh

I get the following:

bash: ./compile-oss.sh: /bin/bash^M: bad interpreter: No such file or directory

Cud you tell me what I need to do to run the script?  

I would like to install oss to see if it will work for me with TvTime and my tv card.

Thanks   mm

---

