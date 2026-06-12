---
title: "Wireless Problems outside house"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by planemanx15 on 2009-01-30
Ok so heres my problem:

I have an ibex dual boot and the wifi works fine at my house, but when I use the laptop at work or school; the wifi will connect but there is no internet.  I have all the Correct IP address, but Firefox will not go to any page.

My girlfriend also has an ibex build and her wifi works at her house, but not my house.  She has the same problem, it will connect and stay connected, but will not load a page.

The networks: My house is a WEP, My office is WEP, school is WPA and my Girlfriend's house completely open.

I can verify that the network works because I can boot into Windows Vista :( and log into the networks.  

Is this a problem anyone else is having?  Has anybody found a fix?  I hate logging into Windows!

---

### Post by planemanx15 on 2009-02-20
Nobody else has this problem?!

---

### Post by superprash2003 on 2009-02-20
did you setup the ip address manually?? leave it to roaming or DHCP mode and allow it to get an ip from the network

---

### Post by planemanx15 on 2009-02-24
I'm already in roaming mode and can see many networks.  This problem is really annoying! 

Ive tried "sudo gedit /etc/network/interfaces" right now I have 

auto lo
iface lo inet loopback

If i add  auto ath0
          iface ath0 inet dhcp

nothing happens, start-up is much longer and I have no networks at all
Any ideas?

---

### Post by planemanx15 on 2009-03-23
FIGURED IT OUT!!!

I use the madwifi diver and to make the wifi resume on standby i have to:


command: sudo gedit /etc/pm/config.d/madwifi

insert SUSPEND_MODULES=ath_pci and save

After that was done, I could not go on other networks.  After undoing this I was able to connect to any network.

---

