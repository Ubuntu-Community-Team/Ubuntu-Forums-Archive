---
title: "Network Manager: &quot;Device not managed&quot;"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by marciovinicius on 2009-07-09
Hi!!
I'm trying to setup the network on a Xubuntu 9.04 in order to make it act as a router

Everything was going fine, both cards was recognized by system and they seem to work fine. I easily setup the internal network on one of them (eth1) with Network Manager.

When I decided to setup the other (eth0) to receive the Internet (dsl) I didn't know how to do it with Network Manager, so i used pppoeconfig. It made the job very well. But now the card connected to Internet is listed by Network Manager as "device not managed".

I've been searching the Internet and it seems that Natwork Manager is acting this way because pppoeconfig is managing this card.

I'd like to know two things:
1- What do I have to do to make Network Manager manage my card again?
2- What do I have to do to erase everything what pppoeconfig did (if necessary)?

I'd like to use GUI to manage my network cards.

---

### Post by superprash2003 on 2009-07-10
hope this helps [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

### Post by marciovinicius on 2009-07-10
Thanks, Superprash2003!
I'll take a look. Only next Monday I'll be able to test it.
I'll post the results here.

---

### Post by marciovinicius on 2009-07-14
I solved, but I didn't do what was suggested.
I was afraid to create a even bigger mess (with two different programs fighting to manage the same card). As I wanted to concentrate all management in NetworkManager, I decided not to touch it.

Here is what I did (someone suggested it to me in Brazilian Forum):
1- I opened the interfaces configuration file
```
gksudo mousepad /etc/network/interfaces
*(it was on Xubuntu, so mousepad was the chosen text editor)*
```2- I erased every config leaving only this (besides the default comment # lines):
```
auto lo
iface lo inet loopback
```3- I restarted the system in order to make Network Manager recognize everything again.

That's it. In this process, I lost all my configuration, but everything was back there (actually it went back to how it was before I messed it up with pppoeconfig). I could configure very well with MAC Address (I took note of them before all the problem happened).

---

