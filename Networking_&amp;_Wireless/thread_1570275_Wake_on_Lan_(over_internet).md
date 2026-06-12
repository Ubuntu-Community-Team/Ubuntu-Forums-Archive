---
title: "Wake on Lan (over internet)"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2010-09-07
Ok i have been searching for a while on how to get WOL over the internet. I have a server which i only use for development and would rather it not be on all the time. But i need to be able to access it when im out

I have WOL working over the LAN. SO next step is internet.

Ubuntu 10.04 LTS

---

### Post by ductiletoaster on 2010-09-09
Ok i figured it out on my own after alot of trial and error.

Here is my setup:
```


INTERNET <-> ROUTER <-> WIRELESS BRIDGE <-> SERVER

Server Specs: 
Ubuntu 10.04 LTS 64bit
AMD Athlon 3700
2gb Ram

Router Specs:
Linksys WRT54G
Firmware DD-WRT v24 mini

Bridge Specs:
Linksys WRT54G
Firmware DD-WRT v24 micro


```

Ok so Im goin to keep updating this post with information regarding WAKE ON LAN

---

### Post by ductiletoaster on 2010-09-09
**[SIZE="5"]Wake On Lan Guide:[/SIZE]**

**Recommended:** For Steps Two and Beyond this guide assumes your system is behind a router installed with DD-WRT firmware. However this guide may work for other systems.


**[SIZE="4"]Remote Wake On LAN Local Only[/SIZE]**

**Step One:** Start with this great guide by Chris Tucker
[http://ubuntuforums.org/showthread.php?t=234588]("http://ubuntuforums.org/showthread.php?t=234588")

Summary: This guide works for Wake on Lan (no internet) however if you want to be able to wake on lan from anywhere continue on.

**[SIZE="4"]Remote Wake On LAN via Port Forwarding[/SIZE]**

**Step Two:** 
Login into your router and go to the port forwarding section and input the following.

```
wol  |  9  |  9  |  udp  |  xxx.xxx.x.xxx  | Enable
```
Where the xxx.xxx.x.xxx replace with the static Ip for your computer that you want to wake. Some guides also tell you to put the broadcast IP however I found that didn't work for me.

**Step Three:**
Add a static ARP entry. You will need to add the following lines under the commands section of your router.

```

ip neigh change xxx.xxx.x.xxx lladdr [MAC ADDRESS] nud permanent dev br0
ip neigh add xxx.xxx.x.xxx lladdr [MAC ADDRESS] nud permanent dev br0

```
Where the xxx.xxx.x.xxx replace with the static Ip for your computer that you want to wake. Replace where it says MAC ADDRESS with the mac address of the machine you want to wake. Be sure to reboot your router before testing.

**Step Three Alternate:**
If after step three you still can't connect then try these alternate cmds.

```

ip neigh change xxx.xxx.x.xxx lladdr ff:ff:ff:ff:ff:ff  nud permanent dev br0
ip neigh add xxx.xxx.x.xxx lladdr ff:ff:ff:ff:ff:ff  nud permanent dev br0

```
The only difference is that im using the broadcast mac address instead of the machines mac address. This is what I did.

**Reference:** [http://www.dd-wrt.com/wiki/index.php/WOL]("http://www.dd-wrt.com/wiki/index.php/WOL")

**Step Four:**
If you have a static external IP then you are all set. However, if you are like the rest of us then you probably have a Dynamic Ip. You then need to sign up for a service like that provided by dyndns.com. Once you have either determined that your under a static IP or have signed up for a dynamic service then you can proceed to testing.

Wake Up with static IP:
```
wakeonlan -i 12.345.67.890 01:23:45:67:89:ab
```

Wake Up with Domain or Dynamic Service (DynDns):
```
wakeonlan -i domain.dyndns.com 01:23:45:67:89:ab
```
Make sure to replace the values. 

**Status:** Incomplete. I wont consider this complete until I can solve some of connection issues I'm having. The wak on lan works but for some reason it seems to not allow reliable connections on any other port. Now this could be just because of how my system is setup.

**Summary:** This guide is no more than a representation of how I managed to some how get wake on lan over the internet working. unfortunately I am having troubles with connections now so obviously i messed something up. Ill continue to update this guide and then re-post it in its completed form when I am finished. Please use the wonderful references I have linked too they will be an essential part of your adventure.

---

