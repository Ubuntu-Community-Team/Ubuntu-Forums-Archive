---
title: "Problem with 1080p"
date: 2011-07-01
forum: Multimedia Software
---

### Post by X_Splinter on 2011-07-01
Hey guys, I have this problem for a long time.

It's simple I can not play 1080p movies in my Ubuntu, I can play 720p just fine, I can paly and edit 1080p with Windows with no problems my PC has more than enought power for that.

But when trying play them in Ubuntu with any player app I get a very very low FPS and the CPU only gets to 65%

I heard this was bug, I am using 10.04 LTS

Any one can help?

---

### Post by pawhtiobo on 2011-07-01
Hi,

What kind of VGA are you using, Nvidia, Ati, Intel?

see ya...

---

### Post by X_Splinter on 2011-07-01
> **pawhtiobo said:**
> Hi,

What kind of VGA are you using, Nvidia, Ati, Intel?

see ya...

Hi,

Intel X3100

---

### Post by pawhtiobo on 2011-07-01
Hi, 

Check this out:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) (Extra repository for drivers)

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

[http://ubuntuforum-br.org/index.php?topic=49634.0](http://ubuntuforum-br.org/index.php?topic=49634.0)

[http://ubuntuforums.org/showthread.php?t=859606](http://ubuntuforums.org/showthread.php?t=859606)

[http://www.vivaolinux.com.br/topico/Aceleracao-3D/Intel-GMA-X3100](http://www.vivaolinux.com.br/topico/Aceleracao-3D/Intel-GMA-X3100)

It can be a driver problem or you need to do some tweaking in your xorg.conf.

See ya...

---

### Post by X_Splinter on 2011-07-01
> **pawhtiobo said:**
> Hi, 

Check this out:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) (Extra repository for drivers)

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

[http://ubuntuforum-br.org/index.php?topic=49634.0](http://ubuntuforum-br.org/index.php?topic=49634.0)

[http://ubuntuforums.org/showthread.php?t=859606](http://ubuntuforums.org/showthread.php?t=859606)

[http://www.vivaolinux.com.br/topico/Aceleracao-3D/Intel-GMA-X3100](http://www.vivaolinux.com.br/topico/Aceleracao-3D/Intel-GMA-X3100)

It can be a driver problem or you need to do some tweaking in your xorg.conf.

See ya...

Thanks for the links but that can't be my problem, my compiz works great so as my 3D acceleration with games inside Linux

I installed the drives from your first link and everything is the same

---

### Post by pawhtiobo on 2011-07-01
Hi,

You can try this, grab a 10.10 or 11.04 CD, boot the machine using it, select "Try" after entering the Desktop, try to load a HD movie from a BRD or a external HDD, just to see if something changes...

See ya...

---

### Post by beew on 2011-07-01
Try install mplayer from this ppa 
[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

Don't be bothered by coreavc, it has nothing to do with the player, if you don't want it just don't install dishowserver (I don't use it and don't recommend it) 

The "mplayer" is actually mplayer2 and it is by far the best video player I have tried (Much better than the Ubuntu stock version of mplayer and VLC)

---

