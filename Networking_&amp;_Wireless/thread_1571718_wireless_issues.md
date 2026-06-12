---
title: "wireless issues"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by jlangholzj on 2010-09-10
Hey all,

I've got 10.04 installed on both my laptop and desktop. Our router is set up with a WEP/WPA passphrase and for some reason my desktop is "spotty" with when it wants to connect. It see's all the networks fine and i can connect to the same router okay through my lappy. Both are up to date. 

whats weird is that sometimes it works on my desktop others it doesn't. I can also connect to an unsecured network just fine through my desktop.


any ideas???? this has been my first big hickup ever with ubuntu and I'm very impressed so far!!! just hope this gets resolved...

---

### Post by Jonny87 on 2010-09-10
> **jlangholzj said:**
> Hey all,

I've got 10.04 installed on both my laptop and desktop. Our router is set up with a WEP/WPA passphrase and for some reason my desktop is "spotty" with when it wants to connect. It see's all the networks fine and i can connect to the same router okay through my lappy. Both are up to date. 

whats weird is that sometimes it works on my desktop others it doesn't. I can also connect to an unsecured network just fine through my desktop.


any ideas???? this has been my first big hickup ever with ubuntu and I'm very impressed so far!!! just hope this gets resolved...

This sounds exactly like the problem I'm having except with me it my laptop having trouble. My desk top is connected to the same router via ethernet. My laptop is up an down. Some times it connects fine other times it won't event see the network. The only other minor difference that I can think of is that I'm using wpa2.

---

### Post by xllxjustinxllx on 2010-09-10
What client are you using to connect to your network?

I had trouble with the network-manager and ended up moving to wicd even though it has problems too.

---

### Post by Jonny87 on 2010-09-10
> **xllxjustinxllx said:**
> What client are you using to connect to your network?

I had trouble with the network-manager and ended up moving to wicd even though it has problems too.

I'm using the network-manager applet (the default gnome network manager that comes with Ubuntu). I'll look into wicd and if i have too much trouble will give it ag unless someone know of one that is defiantly better.

---

### Post by grahammechanical on 2010-09-10
Is the wireless card built into the motherboard or is it an actual card sitting in an expansion slot? May be it has worked loose or not seated properly. Could you put the card into another expansion slot? It might be a physical fault and not an operating system problem

Regards

---

### Post by jlangholzj on 2010-09-10
> **xllxjustinxllx said:**
> What client are you using to connect to your network?

I had trouble with the network-manager and ended up moving to wicd even though it has problems too.

I installed wicd and it won't connect through wicd either, says it has the wrong password. If i have wicd and the default program that came with gnome both installed however, will the conflict with eachother?


> **grahammechanical said:**
> Is the wireless card built into the motherboard or is it an actual card sitting in an expansion slot? May be it has worked loose or not seated properly. Could you put the card into another expansion slot? It might be a physical fault and not an operating system problem

Regards

works 100% fine on my windows7 partition on the same machine, and has for the last year or so.

---

### Post by sydbat on 2010-09-10
Sounds like we are all having similar problems. Wireless card in one box will only connect to unsecured AP (at ~85% strength), even though it "sees" the secured one (that has no signal strength).

Personally, I am thinking it might be the new wireless D-Link router from Telus, as the old one connected securely via WPA2 without problems before it suddenly died.

Other than the built in applet and wicd, are there any other utilities to connect wirelessly?

Wireless card is Atheros 5800 (according to lshw).

---

### Post by jlangholzj on 2010-09-10
I'm just confused at why it works on one machine and not the other. Does anybody know of a good app that can spit out system information so we can try and help someone help us? 

I want to get this resolved bc the person I'm leeching off of has really poopy internet :p

---

### Post by jlangholzj on 2010-09-10
just as an update I wiped lucid off my HD and re-installed it. STILL the same result.....so my conclusion is that is has to be my wireless client. I dont have any other routers that are protected to try and connect to but my guess is that for some reason it doesn't like the WPA of the router and that my laptop has a different chipset.

anyone knonw how to find out what wireless chipset i have?? and if there would be a second driver or other support for it?

---

### Post by jlangholzj on 2010-09-11
for anybody that may be following this thread:

i found this little beauty:

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

I use the RaLink 2860 chipset and i intend to try this one out and see if it works. Unfortunately I've not been able to try it because i can't downlaod the latest driver from ralink and I can't find it anywhere else...yet...lol....I'll let ya'll know if this solves my issue or not once i find the latest driver

---

### Post by jlangholzj on 2010-09-12
mods jumped on this one a bit.....

that link did solve the issues for my chipset, hope ya'll that have the same problem are able to find an answer

---

### Post by candtalan on 2010-09-21
> 
whats weird is that sometimes it works on my desktop others it doesn't.

which chip is being used?
lspci 
will include it I think

---

