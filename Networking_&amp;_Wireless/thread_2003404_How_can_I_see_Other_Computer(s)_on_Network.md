---
title: "How can I see Other Computer(s) on Network???"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2012-06-14
hi. just as the title ask I am trying to find out how I can see other computers on the same network wifi. I am not very familar with networking at all.
I can access the router but the router doesn't have any pages to show computers that are actively using it.

this is how I know nothing about networking. I don't even understand why firestarter shows multiple active connections anyway. they all say firefox under program (sometimes python shows up for some reason) and under service unknown,ftp, and http. the source ip and destination is all the same under all 5-7 entries except 1 destination is different right now. and all different ports.  and this is while only this 1 computer is on the network. I don't think it really shows me the other ones ever.

I am sharing a friends internet connection they were nice enough to allow me to use it for free so mainly the reason i am wanting to know exactly when they are online is so i can actually use a little more bandwidth i.e. 2-4am when i know no ones on it anyway but i just want to make CERTAIN. I currently use wondershaper and only allow myself 50KB/sec this is fast enough for just normal browsing of the web but not for downloading 200-300MB updates and for games.

there computer uses peppermint linux as well and there other one is windows 7 ( i am not trying to SHARE anything over the network just simply see when they are on the internet )

Thanks to any help sorry if confused any1 just ask.

---

### Post by poolet on 2012-06-14
To understand what you want..!! You want to have 4 computers independent OS, (may windows,linux distro) connected into an internal network. All computers must have a limited bandwidth except of yours?? Also any computer can't be able to communicate with other but only to have internet access....Please correct me if I'm wrong..!! At the end if you can let us know your modem/router manufacturer and model...

---

### Post by slixz85 on 2012-06-14
thanks for reply. sorry for how i typed it i guess. to better explain of exact situation...
my friend lets me used wifi from my house which is practically ALMOST next door. I am connected to it right now. I dont need any help limiting bandwidth for my computer. i use wondershaper for that and it works great i can watch the KB/sec in firestarter and they never go above what i set of only 100KB/sec tops usually only 50KB because for the most part i only browse the internet.
now i am just wanting to know HOW i can see when they may be online since there house isnt made of glass. I dont know anything about networking and how to do this at all right now. I don't need to share any files with them or access their computer at all. they have 2 computers in there house and i have 1. so 3 computers are on this network together at times.
I am not trying to interfere with them trying to stream youtube or do whatever they do so that is what i use wondershaper for. they have like a 2MB/sec connection and 100KB/sec is a tiny fraction of that.
so i just want to know if there is a tool i could use to easily open it and see if they are on there computer that way I know if i can download big files or not and change my wondershaper to be able to download at 500KB and over.
are you following?

it is a linksys cisco WRT54G2

---

### Post by jocefus on 2012-06-14
Kismet
 
[http://www.kismetwireless.net/](http://www.kismetwireless.net/)
 
If you have access, there is a mac address table somewhere in that router's web access software. I have the same router, but don't remember exactly where it is located. I am not home right now, so I can't find it this moment. I believe it's in the menu where you can setup mac address filtering. There is a button that will return "wireless client mac list."

---

### Post by poolet on 2012-06-14
> **slixz85 said:**
> thanks for reply. sorry for how i typed it i guess. to better explain of exact situation...
my friend lets me used wifi from my house which is practically ALMOST next door. I am connected to it right now. I dont need any help limiting bandwidth for my computer. i use wondershaper for that and it works great i can watch the KB/sec in firestarter and they never go above what i set of only 100KB/sec tops usually only 50KB because for the most part i only browse the internet.
now i am just wanting to know HOW i can see when they may be online since there house isnt made of glass. I dont know anything about networking and how to do this at all right now...............................................

it is a linksys cisco WRT54G2

Ok. If you want to just see how many machines are connected on modem/router, you can simply find the default ip address and login on your modem/router, on the toolbar should be to buttons **lan** & **wireless without make any changes, **try to see if there is any status or **Attached Devices **there maybe other attached devices on lan and other on wireless so be careful and search carefully.. As you find that you be able to see how many machines (with mac address and hostname).
Your modem/router ip address is:: 192.168.1.1 user: none and password: admin. Now if you want to see the traffic of the specific address for example you find an ip address of 192.168.1.10 hostname: pc1 , I prefer to download wireshark and capture your network... you just simple set filter interfaces on modem/router (run it as root to do that) and just capture you modem/router traffic, after filtering interfaces you see a bunch of misunderstand  information you just search the ip address on the board (our example 192.168.1.10) and you are able to see the traffic of the specific computer not exactly website traffic but ip address traffic and destination...
Check the links below:: 
[http://www.wireshark.org/download.html](http://www.wireshark.org/download.html)
[http://wiki.wireshark.org/](http://wiki.wireshark.org/)

Optional you can even easier used traceroute by command 
```
traceroute "ip address" 
```and you can see the destination address of each until the final destination (something like a path) or with nmap  check the detail below:: 
[http://nmap.org/](http://nmap.org/)Hope that helps you!! :)

::**Note**::Something that I forgot to mention is that, traceroute will not show you exactly the source, if you traceroute from your computer the 192.168.1.10 will show up the until the end path of reaching the ip address, not the specific traffic, but the source that helps you to understand how the nmap works with a sort of a specific detail!!

---

