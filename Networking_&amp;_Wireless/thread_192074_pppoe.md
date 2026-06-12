---
title: "pppoe"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Michal77 on 2006-06-08
Hi everyone,
I had problems with pppoe after update Breezy to Dapper. So I made fresh installation. I run pppoeconf and it was working. I restart computer and… no connection. OK.
I use pon dsl-proviader. And…
No file etc/ppp/peers/dsl-proviader.
Ok. I go to etc/ppp/peers and it’s there.
Ok I run again pppoeconf and still nothing, no internet connection…
Anyone any idea what’s wrong????
:(

---

### Post by adwait on 2006-06-08
maybe because the spelling is "dsl-provider"?

---

### Post by Michal77 on 2006-06-08
[QUOTE=adwait]maybe because the spelling is "dsl-provider"?[/QUOTE]

Nice try. Wish it could be so easy. :) 
But it's not:

naakoole@Nexus:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
naakoole@Nexus:~$ plog
Jun  8 23:07:25 Nexus pppd[5118]: Plugin rp-pppoe.so loaded.
Jun  8 23:07:25 Nexus pppd[5120]: pppd 2.4.4b1 started by naakoole, uid 1000
Jun  8 23:08:00 Nexus pppd[5120]: Timeout waiting for PADS packets
Jun  8 23:08:00 Nexus pppd[5120]: Unable to complete PPPoE Discovery
Jun  8 23:08:43 Nexus pppd[5183]: Plugin rp-pppoe.so loaded.
Jun  8 23:08:43 Nexus pppd[5185]: pppd 2.4.4b1 started by naakoole, uid 1000

And still no conection ](*,)

---

### Post by Bunyak on 2006-08-31
I get the same thing as you.  Here's my situation:
- running an HP lappie with D-link pcmcia ethernet card recognized as eth0
- ran pppoeconf ok from root
-first time internet connection worked and thought all was fine
- after computer re-booted, no internet connection
- ran pon dsl-provider, no internet
- ran plog and got:

Plugin rppppoe.so loaded.
pppd 2.4.4b1 started by root, uid 0
PPP session is 3182
Using interface ppp1
Connect: ppp1 <> eth0
PAP authentication failed

- repeatedly used pon and poff dsl-provider to toggle the connection
- interface changed from ppp1 to ppp2 to ppp3 to ppp4 (not sequentially, though).  I have only one ethernet installed (the d-link)
- finally, internet connection was established when interface toggled to ppp0, which seems to match with the same number designation for my ethernet:

PPP session is 3234
Using interface ppp0
Connect: ppp0 <> eth0
PAP authentication succeeded

My internet connection CONSISTENTLY works when "ppp0 <> eth0".  Is there a way to force Ubuntu Dapper to use only "ppp0"?  I think this would solve my problem.

Thank you, Ubuntu-land ;)

---

### Post by Bunyak on 2006-09-04
more...
tried fix found on [https://help.ubuntu.com/commuunity/adslpppoe](https://help.ubuntu.com/commuunity/adslpppoe)
involved changing "interfaces" file under /etc/network
added lines as they suggested.
still a no-go.

so.........any ideas?

Presently, my "interfaces" file reads as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

perhaps someone can help me...my only ethernet card is eth0. do i need lines like "auto eth1" and "auto ath0" and "auto wlan0"?  Are these lines buggering my connection?  Also, should my "iface eth0 inet dhcp" line read "iface eth0 inet manual", and if so, what's the diff?

My idea is to try to force Ubuntu to use nothing but interface ppp0 when using eth0, because it seems that only under that situation will PAP authentication be successful.  Any thoughts?  (remember, I am a total newbie at this stuff.):D 

kindest regards to you all.

---

