---
title: "No torrents download"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by ghitoy on 2009-11-07
Hi guys,

On my 9.10 Ubuntu torrents refuse to download. I´ve used Ktorrent, Transmission and Vuze so far and none of them download. What could be the problem?

There are enough seeders/leechers on those torrents so what could be the problem? (i see this on thepiratebay.com, my program doesn´t show any seeders/leechers)

Greetings,
Ghitoy

---

### Post by pastalavista on 2009-11-07
Maybe your ISP has blocked torrent files. I've heard some of them have.

---

### Post by ghitoy on 2009-11-07
Good idea! Ehhmm, how can i check this? just go to their website and look around?

---

### Post by pastalavista on 2009-11-07
[Google]("http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=rh2&num=50&newwindow=1&q=ISP+blocks+torrent+files&btnG=Search&aq=f&oq=&aqi=") is our friend

;)

---

### Post by ghitoy on 2009-11-07
Ok, i tried some things with google, and it looks fine. No blocks.
i also called a friends using my ISP too, and he´s downloading fine. I think there is something wrong in my network. what could be wrong?

---

### Post by ghitoy on 2009-11-07
Ok, guys. This is really weird. 

I was thinking what the heck could be wrong? And put my internetcable in it, and it started downloading. I got it out, got back on my wifi again and then it stops. For some reason i can download by cable but not by wireless..

---

### Post by markoh on 2009-11-07
Could services like [http://itshidden.com](http://itshidden.com) help to bypass ISPs that block torrent?

---

### Post by Defrector on 2009-11-07
Something to check is if your NAT/Router is set up to send all packets to Bittorent ports to a specific IP on you LAN. If your wireless is using DHCP but ethernet is static you may have trouble with wireless torrenting.

...though theoretically it would still work when downloading so I don't know for sure.

---

### Post by pastalavista on 2009-11-07
Only thing I can think of is an ipv6 issue. Have you disabled it?

Try this... in terminal
```
gksu gedit /etc/sysctl.conf
```
and add this line

net.ipv6.conf.all.disable_ipv6=1

save and reboot

---

### Post by arjuntank on 2009-11-07
is it only the torrents that are not working on your wireless?

---

