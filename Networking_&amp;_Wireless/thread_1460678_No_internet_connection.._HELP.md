---
title: "No internet connection.. HELP"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Nikor on 2010-04-23
Hi there!

For the first time i installed Ubuntu on my PC. Before ubuntu i had Windows XP.
With windows XP the internet worked fine, i just had to disable the integrated network card.

To the problem in Ubuntu:
The thing is that i can't connect to an network connection, i've tried almost all possible things, like writing the ip, gateway etc manualy. But with no results..

I have two network cards (One integrated in the motherboard).
The one integrated is not working (But i get two connections with two different mac-adressen in the network manager)

i've checked a couple of forums for persons with the same problem and tried the commands in terminal that they did, but with no results.

I'm using the 9.10 version of ubuntu.

Specifikations of my computer:

Grafikcard: Geforce 8600 GT (512mb grafik memory)
RAM: 2gb (Kingston i think)
HDD: 500gb (Western digital)
Processor(?): AMD athlon 64 x 2

I hope that someone can help me.. i don't want to go back using Windows XP..





Edit:
If i change the "Automatic DHCP" to "Link-lokal only" it says "Connection established" but i still cant use the internet.. Im using 24Mbit (ISP: telia) My computer is connected via a switch (the switch is shared by 3-4 pc:s, with the OS windows) directly to a router.
i've also tried to reboot the router/modem.. with no results.

My theory is that the problem is the switch . . .



Network connection:



(My PC)--------------------------------->
                                                  (Windows pc 1)----------------------->(SWITCH)-----------------(ROUTER)-----------------(MODEM)
                                                  (Windows pc 2)----------------------->




Greetz - Niko

---

### Post by Iowan on 2010-04-23
Does the machine get an IP address?
From a terminal (Applications>Accessories>Terminal):```
ifconfig -a
```

---

### Post by Nikor on 2010-04-24
> **Iowan said:**
> Does the machine get an IP address?
From a terminal (Applications>Accessories>Terminal):```
ifconfig -a
```


I managed to fix the problem, the problem was the switch.. apparently Linux based and windows based computer don't get along so well together..

First i unplugged all the other computers, then i got "connection established" so i updated and downloaded some packages. Then i plugged the remaining computers back to the switch, now internet runs smoothly.

The only thing is that i get "Network service discovery disabled. your current network has a .local domain, which is not recommended and incompatible with Avahi network service discovery. The service has been disabled"

But like i said, internet runs smoothly and i can download the packages that i need without any problem.

Greetz Niko

---

### Post by Iowan on 2010-04-24
Odd... but glad you found a solution... :)
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

