---
title: "How to make a network bridge in linux?"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by TimeGoneBomb on 2006-02-18
I've got 2 network cards in this computer, connected to different networks, and I want to bridge these netorks. In windows it is super trivial to do, but in linux I have no idea what to do. Can anyone point me in the right direction?

---

### Post by racyrefinedraj on 2006-02-18
download firestarter (it's in the repositories)

select your internet network

select your local network

check the box for share networks

bam.

---

### Post by david.cab on 2006-02-18
[QUOTE=TimeGoneBomb]I've got 2 network cards in this computer, connected to different networks, and I want to bridge these netorks. In windows it is super trivial to do, but in linux I have no idea what to do. Can anyone point me in the right direction?[/QUOTE]
Check out this [simple how to]("http://experience.projektas.lt/Making-bridge-linux.htm"). It shows how to brige interfaces eth0 and eth1. For more detailed information check this [brige wiki]("http://linux-net.osdl.org/index.php/Bridge"). Hope it helps.

---

### Post by woedend on 2006-02-18
its even easier in linux.  just add 
iface br0 inet dhcp
bridge_ports eth0 eth1

to /etc/network/interfaces
then reboot, run terminal and run sudo ifup br0.

---

### Post by Rakoun on 2006-02-19
Hello every body!

I have a problem with my bridge. This is what I did at home.
First, i created a network with three computers as following:
- Computer A on ubuntu witch has two network cards
- Computers B and C on Windows XP.
On computer A I assigned the following IP adress for the to card:
- 192.168.10.1 for the one connect on computer B,
- 192.168.10.2 for the one connect on computer C.
Then I create a bridge gathering eth0 and eth1 and I assigned it 192.168.10.1 as IP address.
After having doing this my network walks very well, all computers was able to ping each others.
So I decide to create a service that create my brige at Ubuntu starting.

Then I install speedtouch_ng in order to have Internet on my computer A.
Unfortunetaly, after this, computer A was unable to ping computer B and computer C. But, what I find strange it that Computer B and Computer C can ping each others?
Note that I deactivated firestarter.

Can somebody help me?

**PS: my Ubuntu distribution is Breezy**

Rakoun
:arrow:

---

### Post by Rakoun on 2006-02-19
[QUOTE=Rakoun]Hello every body!

I have a problem with my bridge. This is what I did at home.
First, i created a network with three computers as following:
- Computer A on ubuntu witch has two network cards
- Computers B and C on Windows XP.
On computer A I assigned the following IP adress for the to card:
- 192.168.10.1 for the one connect on computer B,
- 192.168.10.2 for the one connect on computer C.
Then I create a bridge gathering eth0 and eth1 and I assigned it 192.168.10.1 as IP address.
After having doing this my network walks very well, all computers was able to ping each others.
So I decide to create a service that create my brige at Ubuntu starting.

Then I install speedtouch_ng in order to have Internet on my computer A.
Unfortunetaly, after this, computer A was unable to ping computer B and computer C. But, what I find strange it that Computer B and Computer C can ping each others?
Note that I deactivated firestarter.

Can somebody help me?

**PS: my Ubuntu distribution is Breezy**

Rakoun
:arrow:[/QUOTE]

No ideas?

Rakoun
:arrow:

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=Rakoun]Hello every body!

I have a problem with my bridge. This is what I did at home.
First, i created a network with three computers as following:
- Computer A on ubuntu witch has two network cards
- Computers B and C on Windows XP.
On computer A I assigned the following IP adress for the to card:
- 192.168.10.1 for the one connect on computer B,
- 192.168.10.2 for the one connect on computer C.
Then I create a bridge gathering eth0 and eth1 and I assigned it 192.168.10.1 as IP address.
After having doing this my network walks very well, all computers was able to ping each others.
So I decide to create a service that create my brige at Ubuntu starting.

Then I install speedtouch_ng in order to have Internet on my computer A.
Unfortunetaly, after this, computer A was unable to ping computer B and computer C. But, what I find strange it that Computer B and Computer C can ping each others?
Note that I deactivated firestarter.

Can somebody help me?

**PS: my Ubuntu distribution is Breezy**

Rakoun
:arrow:[/QUOTE]

Sounds like maybe a routing issue?  Does the routing table look different before and after you run speedtouch_ng (I am not familiar with the speedtouch_ng software).

---

### Post by Rakoun on 2006-02-19
[QUOTE=cwaldbieser]Sounds like maybe a routing issue?  Does the routing table look different before and after you run speedtouch_ng (I am not familiar with the speedtouch_ng software).[/QUOTE]

Thanks for the tip, I will see.

Rakoun
:arrow:

---

