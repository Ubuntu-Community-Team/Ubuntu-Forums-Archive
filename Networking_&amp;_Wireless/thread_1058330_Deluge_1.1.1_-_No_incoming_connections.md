---
title: "Deluge 1.1.1 - No incoming connections"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by kiprit on 2009-02-02
Hi people,

I switched to Ubuntu 2 weeks ago and since then I keep reading these forums... and what i found helped me to solve lots of things. But here I have something I cannot solve:

I am running on Ubuntu intrepid. I used to have an older version of deluge, which seemed to work fine. It was sometimes showing that ports were fine, sometimes not. But it was always downloading at a fair speed. 

Today I upgraded to Deluge 1.1.1 by adding [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) to my repository list.

My router is smc 7908... I am using a static IP 192.168.2.100 and forwarded port 32881 to that IP.

also following [this thread]("http://ubuntuforums.org/showthread.php?t=331161&highlight=deluge") I opened ports 32881 through 32890 to the iptables.

however since the upgrade deluge keeps saying "No incoming connections" and downloads nothing. It sees all the seeders and leechers but does not connect to them.

I tried Vuze with the same port... it is able to see only half of the peers and manages to download at a very slow speed...

any help will be very much appreciated.

---

### Post by musicguyguy on 2009-05-08
> **kiprit said:**
> It sees all the seeders and leechers but does not connect to them.
I have the exact same problem with Deluge. When I used Transmission, however, this problem didn't seem to show up...

---

### Post by joanmunoz on 2009-05-20
> **kiprit said:**
> Hi people,

I switched to Ubuntu 2 weeks ago and since then I keep reading these forums... and what i found helped me to solve lots of things. But here I have something I cannot solve:

I am running on Ubuntu intrepid. I used to have an older version of deluge, which seemed to work fine. It was sometimes showing that ports were fine, sometimes not. But it was always downloading at a fair speed. 

Today I upgraded to Deluge 1.1.1 by adding [http://ppa.launchpad.net/deluge-team/ppa/ubuntu](http://ppa.launchpad.net/deluge-team/ppa/ubuntu) to my repository list.

My router is smc 7908... I am using a static IP 192.168.2.100 and forwarded port 32881 to that IP.

also following [this thread]("http://ubuntuforums.org/showthread.php?t=331161&highlight=deluge") I opened ports 32881 through 32890 to the iptables.

however since the upgrade deluge keeps saying "No incoming connections" and downloads nothing. It sees all the seeders and leechers but does not connect to them.

I tried Vuze with the same port... it is able to see only half of the peers and manages to download at a very slow speed...

any help will be very much appreciated.

Hi!

How did you forwarded that port? I recommend you forward a few ports (5 i.e., and ports above 43500 at least) and choose TCP&UDP protocol type.

[IMG]/home/joan/Escritorio/pantallazo.png[/IMG]

I think you don't need to open ports as you did, Ubuntu now comes with all ports open. I'm assuming you selected the forwarded ports on Deluge "Preferences - Net" window, don't you? 

[IMG]/home/joan/Escritorio/pantallazo-1.png[/IMG]

I did that a few minutes ago and everything works fine!

Regards!

Joan

---

### Post by akvilio on 2010-07-22
Hi, i know this thread is 1.5 years old but...
I'm having the same problem and my firewall on the router is off... which means, as far as i know, that all the ports should be open. nevertheless, I opened the ports suggested and it's the same... I just started using deluge, after a not so good work of transmission. 

please help...

---

