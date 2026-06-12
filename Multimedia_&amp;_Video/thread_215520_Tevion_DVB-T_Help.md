---
title: "Tevion DVB-T Help"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by sebz2005 on 2006-07-14
Hi,
I have a Tevion DVBT-220RF PCI card that I want to run on my Linux TV box (opposed to having to run it on windows :rolleyes:)

Are there any Tv Tuner programs that support my card? Or will I have to tweek a program?

---

### Post by koshari on 2006-07-14
providing you can get the drivers to recignise it, you can use any dvb program including mythtv and kaffeine to name a few,

in conjunction with tzap you should be able to use it with mplayer and xine also, 

vlc player supports dvb also but i havnt got mine to work through that yet.

---

### Post by sebz2005 on 2006-07-14
I'm not sure I have the drivers. Is there a way to port Windows drivers to Linux, should I search the internet or just give up?

Edit: Yeah, I tryed to install MythTV but I had errors trying to communicate with their server, and so I downloaded the packages off their site.
So tryed to install it, but I needed Lame on there first, but when I tryed to install it through apt-get I the only thing it said was that there were refrences to it from other apps, but couldn't find it.

---

### Post by koshari on 2006-07-14
for starters you cant port windows driver to linux, 

however tevion is no rare make ant you will likely find that the kernal supports that card already, 

as for mythtv, why dont you simply use synaptic and it will  meet all your dependencies?

look here 

[http://kernelnewbies.org/Linux_2_6_17](http://kernelnewbies.org/Linux_2_6_17)

seems your hardware is supported in th abovementioned kernel

---

### Post by sebz2005 on 2006-07-14
Ah, you should see my face right now. I'm so happy! :grin:
I'll retry MythTV

How would go about putting the Divx and Xvid codecs on my Linux box?

---

### Post by koshari on 2006-07-14
"How would go about putting the Divx and Xvid codecs on my Linux box?"

easy , enable the multiverse and universe repos in synaptic and just add them through there.

---

### Post by sebz2005 on 2006-07-14
Ok.

Thank you for all your help! :)

---

### Post by sebz2005 on 2006-07-14
I retryed it, and it didn't really work.
I followed the MythTV.org's directions - Failed.
Then I tryed the links at [http://debian.video.free.fr/](http://debian.video.free.fr/) - Also failed.

What an I doing wrong?

---

### Post by sebz2005 on 2006-07-14
Now I'm stuck.
I got MythTV to install and run, but I need to update the Kernal. How do I?

---

