---
title: "How to share your Internet (From wireless to Ethernet - Network Bridge)"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by ArielEnter on 2009-12-04
So how to share the Internet from a computer that is getting it wirelessly with another computer that doesn't have a wireless card using a Ethernet cable? Of course both will have to have a Ethernet slot available. For example from a Laptop computer to a desktop computer with no wireless card.
 I do this all the time with the help of a crossover UTP cable, but I guess you could use a switch/hub between them as well.
 It doesn't matter what operating system the computer you are sharing the Internet with has. At least with Windows or Mac it worked the same.
 I don't think this is a network bridge. In Windows I used to accomplish the same thing by bridging two connections, but I think this is more a &#8220;Share the Internet with the other connections&#8221; thing.
 

 Let's take the example of the laptop and the desktop computer.
 

 1.- Take your laptop and go to System>Administration>Network Connections
 

 2.- The first tab you will be in is &#8220;Wired&#8221;, there you will select the Ethernet connection that you will plug in with the desktop computer. Usually it will be Auto Eth0.
 

 3.- Click on Edit and you will go to the Ipv4 Settings Tab, and where it says &#8220;Method&#8221; you will chose "Shared to other computers" and you click apply.
 

 4.- Finally you connect both computers through the Ethernet using a crossover UTP cable or by using a hub/switch and two regular Ethernet cables.
 

 And there you go. The laptop will behave kind of like a DNS and will assign an IP to the desktop computer and it will provide it with Internet.
 

 I wanted to share this because I went through a lot of troubles finding this:
 [http://ubuntuforums.org/showthread.php?t=1290067](http://ubuntuforums.org/showthread.php?t=1290067)
 I guess this could have gone to Absolute Beginner Talk but believe me, it was insane.

---

### Post by community nerd on 2009-12-04
prety good

---

