---
title: "lame encoder question."
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by kesuki on 2008-01-01
why is it that all the linux based lame encoders are completely off the net when a 'quick' download.com search for 'lame' turns up almost 70 programs most of which include a lame-enc binary for windows?   

with some of those programs being commercial or shareware you would think the lawyers could sue them for monitary damages, but instead windows users can keep using lame, while linux users are being discriminated against. 

not to mention all the windows apps using blade-enc or other open source encoders..

there are probabbly over a thousand windows applications that come with an open source encoder dll or exe so why is it just 'linux' being targeted?

---

### Post by icheyne on 2008-01-01
Maybe because you can just do:

sudo aptitude install lame

It's v. 3.97.

---

### Post by kesuki on 2008-01-01
well, that fails to explain why there are _no_ mp3 encoders in synaptics package manager. and in fact, the 'install lame' only works because of a lone lame mirror that DIDN'T get pulled.  at ftp.debian-unofficial.org/debian/pool/main/l/lame/

that is the _only_ mirror for any mp3 encoder that i could find at all. 

why did all the official mirrors get pulled, why is it not in synaptics anymore?

---

### Post by philc on 2008-01-01
FFMPEG is in the official repositories. It supports MP3 encoding through libmp3lame.

Or there's the abcde audio encoder which will handle MP3 through distmp3. Both in the repositories.

gogo perhaps?

Seems like there's lots of options. Maybe I missed the thrust of your question.

---

### Post by icheyne on 2008-01-01
Here you go.

[http://www.rarewares.org/debian.php](http://www.rarewares.org/debian.php)

 ## RareWares/Debian Multi-Media Repository for Unstable
 deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./ 
 ## RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging
 deb [http://www.rarewares.org/debian/packages/experimental/](http://www.rarewares.org/debian/packages/experimental/) ./ 
 ## Christian Marillat's Mult-Media Repository for Unstable
 deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main 
 ## Christian Marillat's Mult-Media Repository for Unstable - Experimental Staging
 deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) experimental main

No idea if this works for Ubuntu.

---

