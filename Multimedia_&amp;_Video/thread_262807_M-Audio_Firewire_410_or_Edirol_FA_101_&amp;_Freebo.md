---
title: "M-Audio Firewire 410 or Edirol FA 101 &amp; Freebob driver &amp; Dapper ?"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by scotty64 on 2006-09-22
Does anyone got the M-Audio Firewire 410 or an Edirol FA 101 running on Dapper?
It looks to me as it needs the "freebob" driver [http://freebob.sourceforge.net](http://freebob.sourceforge.net) installed.
I want to get mysef an external audio device for recording and live broadcasting. Preferrably the M-Audio as it is cheaper then the Edirol.
It is important for me that it works fine with JACK and Ardour.
So any evidence of a working setup with Ubuntu would be great!

---

### Post by sebos69 on 2006-10-03
I'd like to know also :)

---

### Post by noou on 2006-11-06
I also have a firewire 410 but I think there's no way to make it work with linux because of the boot issue [http://www.mail-archive.com/linrad@antennspecialisten.se/msg00417.html](http://www.mail-archive.com/linrad@antennspecialisten.se/msg00417.html)

let me know if I'm wrong! it would be nice indeed!

cheers,
Stefano

---

### Post by scotty64 on 2006-11-10
I have decided for a Presonus Firebox and got it running well on Dapper.
I got all inputs and outputs supported and can run the box on all samplerates from 44100 to 96000. Audio is perfect! :KS And it is nice that JACK/freebob are automatically using the right names for the JACK ports. That makes patching in Qjackctl easy. I think the Presonus is a good choice and real value for money.:) 
I think the M-Audio and the Edirol would work too as they have working setups listed on the freebob page. The big disadvantage is that due to the lack of JACK and freebob support in Dapper, JACK and all related JACK enabled applications that you want to use with freebob have to be recompiled. :( The good news is that Ardour, although a big chunk of software, compiles well and without any probs. I got VLC and artsd JACK enabled too.
I used the latest SVN versions of freebob and the libraries mentioned on the freebob page [http://freebob.sourceforge.net/index.php/Building_and_Installing](http://freebob.sourceforge.net/index.php/Building_and_Installing)
When you try to compile it, be sure you do not have any developer packages of the Ubuntu libraries that you are going to upgrade to SVN versions installed.
Otherwise you may run into linking problems.


Enjoy the Sound!

---

### Post by leleobhz on 2006-11-13
Please, see this post:

[http://ubuntuforums.org/showthread.php?t=214911&page=3](http://ubuntuforums.org/showthread.php?t=214911&page=3)

---

### Post by leleobhz on 2007-02-21
Follow the last link again!!!!

---

