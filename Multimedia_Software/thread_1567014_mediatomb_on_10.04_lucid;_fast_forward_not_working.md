---
title: "mediatomb on 10.04 lucid; fast forward not working (Samsung UE-32B7020)"
date: 2010-09-03
forum: Multimedia Software
---

### Post by surfer on 2010-09-03
i followed [this thread]("http://art.ubuntuforums.org/showthread.php?t=1198689") and got [mediatomb]("http://mediatomb.cc/") on my ubuntu 10.04 lucid running. i have a samsung UE-32B7020 tv.

the only problem is that for .avi and .mp4 movies (these are the ones i tried), fast forward and rewind do not work. transcoding is not enabled.

any ideas?

---

### Post by surfer on 2010-09-06
bump...

---

### Post by SquirrelOfDoom on 2010-11-08
I have the same problem, with an LG BD590C... is there a fix for this?

---

### Post by surfer on 2010-11-08
still haven't found any...

would that work using mythbuntu?

---

### Post by surfer on 2010-12-08
...bump.

---

### Post by minisori on 2011-01-17
Try the arrows instead of the fast foward or rewind buttons.

---

### Post by surfer on 2011-01-19
> **minisori said:**
> Try the arrows instead of the fast foward or rewind buttons.

will try that! thanks minisori!

---

### Post by mac-duff on 2011-02-20
Hi,

I am coming across now the same issue that the fast forward isnt working probably. I can use the arrows but then everytime the file is reloading and I cant jump really far, just some seconds.

Is this an error of mediatomb or of the TV? I have a Samsung something

cu

---

### Post by lo.j on 2011-12-22
natty 11.04
samsung ue40d5000

same problem... any fix? thanks.

---

### Post by surfer on 2011-12-22
sorry, no news on that front... but please report back should you find a fix. tanks!

---

### Post by takeoo111111 on 2012-01-05
Hi,
i have the same issue with my UE37D6500. I can jump 15 sec for-/backward with the arrow keys. Transcoding is switched off. (Not working with .mpg)
A fix would be very fine. I've heard there is something wrong with the RC and Logitech Harmony seem to fix this, but i don't have one.
This we i will try to check the traffic with wireshark perhaps i can find something there.

lg

---

### Post by takeoo111111 on 2012-01-05
Hi all,
i found a much better solution.  My first thought was to buy a small PC and install XBMC instead. But thats expensive and as i am a student i don't have a lot of money.
There is a platform called "Plex" with a fronted like XBMC (not as powerful in that App version, but ok).
Composed of a client and a server. The client ist not avaiable for Linux (iOS, Windows and Android only) but there is a Smart Hub App. It works really great!

Here you can have a look at it:
[http://www.youtube.com/watch?v=4E3A0lGo7mU](http://www.youtube.com/watch?v=4E3A0lGo7mU)

-At first you have to install the "Plex Media Server":
 [http://www.plexapp.com/linux/linux-pms-download.php](http://www.plexapp.com/linux/linux-pms-download.php)
-You can add video/pictures/music, using a webfrontend:
 [http://serveradress:32400/manage](http://serveradress:32400/manage)
-Then you can install the App on your TV using Smarthub. As it can't be found in the   App-Repo you have to add it from your own repo. Thats how it works:
[http://forums.plexapp.com/index.php/topic/34067-howto-install-samsung-plex-app/](http://forums.plexapp.com/index.php/topic/34067-howto-install-samsung-plex-app/)
-Finally you enter the IP-adress of your new Plex-Server at first startup

I think its much better than using UPnP or DLNA


 Hf,
 

 Takeoo111111
 

 Hope my english is not too bad.

---

