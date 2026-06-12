---
title: "flash streaming"
date: 2008-08-01
forum: Multimedia Software
---

### Post by anv on 2008-08-01
Hi some of my favorite web channels have changed to web streaming from earlier mediaplayer streaming. is it possible to follow the stream basing on the ip.s and finding the source stream which would be *.asf material?

I don't want to register to every site, neither log-in to watch flash streamed sites, nor use flash if I can choose not to.

---

### Post by cozmicharlie on 2008-08-01
Yes it is possible.  You can copy and paste the url to a player like vlc and play it will play outside the web site. In vlc go to menu>file>open network stream>mark http,https,ftp,mms and add the url and it should play.

Enjoy

---

### Post by anv on 2008-08-02
I tried with Mplayer and VLC,while trying through VLC I ran it through terminal it told: "...no suitable access module " maybe it is missing login information or the macromedia-fcs is not possible to open through VLC..  

(87.248.197.133)

---

### Post by cozmicharlie on 2008-08-03
What is the actual web site you are trying to access?

---

### Post by anv on 2008-08-06
one of them is [www.god.tv](www.god.tv) which previously send .asf format streams. now it is made available only for registered users only

there's now flash streams from several areas and speeds here is couple of ip addresses which I took from wireshark while watching the streams from web browser ( which is pain in 64 bit ubuntu, because Adobe has not released 64 bit flash player ):

87.248.197.181 (UK low)
87.248.197.172 (US high)


p.s. (off topic note) this absolutely weird that the nature of internet and it's basic functionality has been changed, to the two companay owned media war machine. And most of don't care. :confused:

---

### Post by cozmicharlie on 2008-08-07
OK - I see what you are trying to do.  I am not sure if you can get the url needed without registering.  Maybe someone else will come along that knows how to do that.

---

### Post by RadioMirchi on 2008-08-07
thankss dude

---

### Post by mocha on 2008-08-07
google for "streamsniff"

Note that some flash streams use some wierd method where part of the URL changes every second, I haven't found a better way to rip those other than the good old "gtk-recordmydesktop" method!

---

### Post by anv on 2008-08-10
it gives the stable IP as I mentioned before, those IP.s are those which I get in wireshark (net analyze softw.) while watching sending from the website.

---

