---
title: "Getting Internet @ my University"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by WildgOphers on 2010-01-27
So, when I went to college I decided to bring my linux box with me along with my cheap xp laptop. Turns out when I first plug in the internet it works, all systems are go, whoopee. But then when I upgrade to 9.10 all that happens is that my internet connectivity icon constantly spins and tells me that I'm disconnected and then spins some more. 

Tried out a different computer, same story. The only thing I could really think of that I did different was that at home, I had the machine set up so that I could SSH to it and grab files off of it from the mythtv that I had set up. 

The only real information that I can find on the universities website is this : "nix and Linux are pretty complicated operating systems. If you are able to get Unix and Linux running, you probably have a pretty good idea how to setup the network card by yourself. ResNet doesn't support Unix or Linux computers for setup, however, they are compatible with the ethernet connection in the residence halls. Remember, you must use a DYNAMIC IP address. Static IP addresses are not allows without permission of ResNet." 
[URL="http://resnet.und.edu/faq.php#12"]
link[/URL]

I'm hoping there's an easy solution here that I'm not seeing. I mean, I bought myself a shiny new (used) pc with two, count 'em, two 3.2 ghz xeon processors. I was so stoaked about using it too.

So any help is appreciated

---

### Post by WildgOphers on 2010-01-28
alright, so when I dmesg | grep eth0 i get a repeating message that may help explain / diagnose my problem.

```
[974.576871] e1000: eth0: e1000_watchdog: NIC Link is Down
[976.229119] e1000: eth0: e1000_watchdog: Nic Link is up 100 Mbps Full Duplex, Flow Control: RX
```

This message repeats over and over with different numbers (timestamps?) out front.

some info from lshw about my network card:
product: 82545GM Gigabit Ethernet Controller

But I really don't think It's a problem with my card as I had the same problem on a different computer with a different card **after** I had decided to update to 9.10. 

Help appreciated.
~Brenden

---

### Post by Dayofswords on 2010-01-28
i cant figure out why but
but an explaintion of ResNet would be nice
> **WildgOphers said:**
> "nix and Linux are pretty complicated operating systems. If you are able to get Unix and Linux running, you probably have a pretty good idea how to setup the network card by yourself. ResNet doesn't support Unix or Linux computers for setup, however, they are compatible with the ethernet connection in the residence halls. Remember, you must use a DYNAMIC IP address. Static IP addresses are not allows without permission of ResNet." 
[URL="http://resnet.und.edu/faq.php#12"]
link[/URL]

i'm sorry but what the hell, some support.
> I bought myself a shiny new (used) pc with two, count 'em, two 3.2 ghz xeon processors. I was so stoaked about using it too.
sounds like you bought a server computer:o

oh, check
[http://uptime.netcraft.com/up/graph?site=resnet.und.edu](http://uptime.netcraft.com/up/graph?site=resnet.und.edu)
doesnt support linux, but sure does run it, CentOS to be exact

---

### Post by WildgOphers on 2010-01-28
ResNet is just the name for the on campus tech support staff, that doesn't support linux. Yay:rolleyes:

---

### Post by WildgOphers on 2010-01-29
Alright so I went and grabbed the .deb package for WICD and installed that and tried some stuff based on the info that I got off of my windows computer that successfully connects to the internet.

If I set my connection static IP and set my IP to say, 192.168.0.109 and use the DNS servers that I got through windows WICD shows that I get connected and then disconnected, and then connected and disconnected, same as before.

But when I don't use a static IP the whole process gets stuck at "Obtaining IP address".

I'm really scratching my head here. I'm not quite sure where to go next.

---

### Post by tubasoldier on 2010-01-29
I would try a live CD of a different distro. You did say it worked until you upgraded. 

Just a thought.

---

### Post by WildgOphers on 2010-01-29
No way man.

Now ... Now it's made me angry.
And I have to beat it into submission 'till it works.

---

### Post by WildgOphers on 2010-01-29
So I tried both Fedora and Gentoo live CDs and got the same story. I'm really not sure what it is that I was doing before that worked.

---

