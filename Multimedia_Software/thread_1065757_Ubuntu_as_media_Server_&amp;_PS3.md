---
title: "Ubuntu as media Server &amp; PS3"
date: 2009-02-10
forum: Multimedia Software
---

### Post by DShad on 2009-02-10
Hello,

I have Mythtv (frontend & backend) installed on Ubuntu 8.10 and my PS3 automatically detects my system as a Media Server. It can stream Videos, Music but I can't make it to display my photos. The is simply NO "pictures" directory when I try to select Photo on my PS3. I only get "Recordings", "Videos" and "Music" folders.

I need to mention here that if I use the frontend on that same Ubuntu 8.10, I am able to see the picture without any problem.

What is wrong with my configuration?

---

### Post by LoermansA on 2009-02-10
Hi,

Although I can't tell you what's wrong with your configuration, I can perhaps give you an alternative; mediatomb. It's in the repository and is able to serve most media (photo's, movies, music) to the PS3. I use it as well and works pretty good. It has a web interface with which you can add or delete stuff to it's database and can be configured to serve a PS3 (among other clients).

I don't know how well MythTV's UPnP will play nice with mediatomb (I have both on seperate machines) but it might be a good solution for you.

Regards,

Arjan

---

### Post by redroad55 on 2009-02-10
What OS do you have installed on PS3 ?

---

### Post by LoermansA on 2009-02-11
> **redroad55 said:**
> What OS do you have installed on PS3 ?

Just the basic OS. It can stream stuff from a UPnP media server. Mediatomb does just that; provide content to UPnP client devices.

Works pretty good, only problem I have is that only subs that are mux'ed in the DivX or XviD are displayed. .sub, .srt and such don't display.

Arjan

---

### Post by redroad55 on 2009-02-11
The reason I asked was I'm working on a thread with someone 
[http://ubuntuforums.org/showthread.php?t=1055246]("http://ubuntuforums.org/showthread.php?t=1055246")
where we have installed the PS3 version of the 8.10 kernel .. we are currently trying to get Java installed ..
we've been looking at this as an alternative:
[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")
this looks like a promising alternative ...

With reference to your problem I found these links that may or may not be useful:

 [http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=161]("http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=161")
[http://ps3mediaserver.org/forum/viewtopic.php?f=6&t=72&p=283&hilit=+photo#p283]("http://ps3mediaserver.org/forum/viewtopic.php?f=6&t=72&p=283&hilit=+photo#p283")
[http://ps3mediaserver.org/forum/viewtopic.php?f=6&t=72&p=1491&hilit=photo#p1491]("http://ps3mediaserver.org/forum/viewtopic.php?f=6&t=72&p=1491&hilit=photo#p1491")
 If you have any input on the 8.10 install please post on above thread..
Post back with any thoughts or questions .. Best to you

---

