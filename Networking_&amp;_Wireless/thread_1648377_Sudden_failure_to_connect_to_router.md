---
title: "Sudden failure to connect to router"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by ironic.demise on 2010-12-18
Ok, so I was connecting to the internet with no problems at all until two days ago.
a while back I set my local IP to #.#.#.11, the internet failed.
```

sudo nano /etc/network/interfaces

```
I removed the added code from /etc/network/interfaces and the internet started up again, however the card retained the .11 IP address and has done through many installs... Don't know why or how, probably just a router DHCP setting not retiring the IP of machines.

That wasn't a problem as far as I know.

Ok, so I check a wired connected win7 pc and an ipconfig /all shows he's got the #.#.#.11 address.
Checked a wireless win7 netbook and it got a #.#.#.24 address
Wireless key double checked and is correct.

I'm now on my WinXP partition (dual boot with the same ubuntu install that won't connect to the internet)
it's getting the IP #.#.#.5 and is connecting with no trouble(albeit slow windows)

All machines are set to automatic configure, but obviously retain the same ip for a while.

I've tried
```

sudo nano /etc/network/interfaces
auto wlan0
iface wlan0 inet dhcp

```

iwconfig show that the wireless card is indeed wlan0

Here's basic information
```

Router ip: 192.168.1.1
DNS:       ""
Gateway:   ""
Windows IPs on  auto-obtain: 192.168.1.5, 192.168.1.11,192.168.1.24
Wireless card on non-connecting machine: Belkin N+ wireless card, v2001, NDISWRAPPER

```

will this work?:
```

auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

The problem is that if I try and connect to the router it does the "connecting rotating circle" and then just either has a message "disconnected from wireless" or asks me again and again for the WPA key, which is already correct.

LiveCD and fresh install both fail, used ndiswrapper and it's always worked fine before.

using Ubuntu 10.04

Any ideas on how I can get connected again?
This is a desktop, a wired connection is just NOT possible.

---

### Post by ironic.demise on 2010-12-18
+

---

### Post by ironic.demise on 2010-12-19
Tried setting static IP in /etc/network/interfaces but that caused the NetworkManager applet to dissapear until I remove the wlan0 entry entirely.

sudo /etc/init.d/restart throws an error every time it's used.
I need help fixing this if I'm going to be able to get on the net in ubuntu.

---

### Post by ironic.demise on 2010-12-19
Right, On the router I've just added some address reservation to the PC with trouble, reserved #.#.#.21 as opposed to 11, I might change it to 11 if it doesn't work this way.

DHCP server is on on the router and it gave this machine #.#.#.5

---

### Post by ironic.demise on 2010-12-19
I've got my 192.168.1.11 ip back and I still can not connect to the router in Ubuntu.

I'm going to try and download a fedora CD and see if that works.

I can't see why it isn't working, can anybody else tell me if they have any ideas?

---

### Post by JayD2 on 2010-12-19
I recently had a similar problem - my wireless just stopped working even though it worked fine with Windows. I went into edit connections and under the wireless tab noticed an 'auto home" and 'auto (name of my router)' listings. I don't know how the auto home one got there so I just deleted both and re-entered my router's password. Everything seems to be working fine now.

Based on your posts you know more about this than me but as you haven't been getting any replies I figured I'd reply anyway in case it is that simple too.

---

### Post by ironic.demise on 2010-12-19
Will try straight away, This may help as I have got two router connections in my list... if this IS a problem, then my god I'll be glad it's solved but annoyed it's something so crazy.

For anybody else reading:
In fedora I've been unable to connect because I've been unable to install ndiswrapper... it's not on the liveCD and I'm having dependency trouble with the .rpm file... can't really be bothered to go hunting down every dependencie's .rpm file.

If I can get it working though, Fedora is FOR SURE going into my bootloader as a trial thing, just for the experience.

:edit:
Tried that, no dice.
I used the same partition as /home for both Fedora 14 and Ubuntu 10.04.
I thought that would be fine, but both of them have hit the roof over user permissions and settings of things!

On a fresh install(albeit using the same /home)
Tried removing all networks and starting afresh, no success. Thankyou for the tip JayD2, didn't hurt to try.
On a LiveCD it didn't work and that's with no previous configurations by myself... no old networks there either.

Will grab an old ndis with less dependencies or all the dependencies and try Fedora 14.

---

### Post by ironic.demise on 2010-12-20
++

---

### Post by ironic.demise on 2010-12-21
Marking as solved
Installed 10.10, works straight away.

---

