---
title: "Where do I get WiFi-radar?"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by Hyphessobrycon on 2006-06-10
First off, please excuse my ignorance; I have only been using Ubuntu for 2 days. I have an IBM Aptiva whose usb wireless adapter is picking up signals from the nearby routers, but cannot connect to any of them. I tried setting everything up in the administrative Network utility, but even though I set the ESSID and WEP key and selected DHCP IP allocation, I still cannot get a connection. I read that maybe the WiFi-Radar package could help me. I looked in packages.ubuntu.com and get pages like [this]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=wifi-radar&version=dapper&arch=all") and [this]("http://packages.ubuntu.com/dapper/net/wifi-radar"), but I still cannot figure out what I'm supposed to click to download the packages. I tried using the add/remove programs thing, and of course, since I was not connected to the internet, I could not get the package. I also tried Synaptic, but it did not even list the package. And I did those both with the live cd in the cd-rom drive. What am I supposed to do? I know this is an incredibly stupid question, but I am lost. Thanks.

---

### Post by Patsoe on 2006-06-10
Hey, that's funny, I just replied to your other topic.

I don't know much about Wifiradar. You might want to try out NetworkManager to see if that suffices for your purposes, it's supported quite well on the forum. 

Install from the main menu Applications > Add/Remove... and scroll down to Network Manager.

Instructions are in the wiki: wiki.ubuntu.com/NetworkManager

---

### Post by nrayever on 2006-06-10
wifi-radar is at synaptic. maybe you need to add multiverse and universe repositories to your synatptic to see it. my sources.list looks like this.

```
deb http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://mx.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```

and i just installed it, pretty cool wifi-radar! :-D :-D 

sincerly nrayever

---

