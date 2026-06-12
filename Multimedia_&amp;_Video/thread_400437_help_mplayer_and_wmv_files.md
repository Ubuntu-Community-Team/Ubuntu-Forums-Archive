---
title: "help mplayer and wmv files"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by Richard_2007 on 2007-04-03
I have sucessfully loaded ubuntu edgy and am writing this on it.

I have used automatix to add support for multimedia on the web. Most everything works except for wmv files.

I recieve at least two errors from different sites when mplayer pops up. 

One is Fatal error Opening/initializing the selected video out (-VO) device.
The other I get is Error! couldn't resolve name for AF_INET6:[www.cvc.org](www.cvc.org)

What am i missing or doing wrong? Help please!

Richard:confused: :guitar:

---

### Post by r4ik on 2007-04-03
I suppose you have these,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

If yes right click and set video to xv.

Good luck !

---

### Post by Richard_2007 on 2007-04-04
ok added the repositorys or rather unhashed the ones that were hashed out. and changed the video but mv didnt work. It finally worked after I clicked on x11. But it still gives me the error couldnt resolve name for AF_INET6. Even though it works and playsback I can both see and hear the video, this error still pops up.

Any ideas? what the heck is AF_INET6?

Thanks so much

Richard :confused: :guitar:

---

### Post by krussell on 2007-04-04
Hello :-)
Have you tried video driver "xv" in mplayer preferences? This driver consumes least memory and works fine.
Also, i have downloaded mplayer source from their web site and compiled it, it works better than the *.deb package (i don't know why).

---

