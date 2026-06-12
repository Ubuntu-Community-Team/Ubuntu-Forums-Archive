---
title: "Get ubuntu to be a DHCP server"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-06-12
hi guys

my ubuntu box picks up the internet on wlan0, and cna share it on eth0 (using firestarter ICS). So far, so good.

However I now need 2 devices to connect to eth0. Unfortunately the router I have will not act as a DHCP server. I can set the IP Address and DNS settings in one device, but the other (a media streamer) is pretty dumb, and needs to be spoon fed.

So the answer is to set up teh ubuntu box to act as a DHCP server fo eth0 ...

is there is simple config to achieve this. I'm a windows native, and tried to use Webmin to configure the DHCP server, but feel I'd have better luck piloting the space shuttle.

---

### Post by Iowan on 2010-06-12
I used DHCP3 on my first server, but opted for DNSMasq on my current one. It's in the repos - more info [here.]("http://www.thekelleys.org.uk/dnsmasq/doc.html")

---

### Post by Jethro_uk on 2010-06-14
I tried dnsmasq .... no joy.

Having read the debian wiki, I made 2 changes ...

I added an 

"interface=" line, 

to restrict it to my eth0 interface, and 

"dhcp-range=192.168.0.10,192.168.0.20"

When my PC connected through my router-acting-as-a-hub, the *router* said it had an attached device with an IP address of 192.168.0.10, but "ipconfig" (vista box) revealed the PC didn't seem to think it had an IP address.

From there, I obviously was unable to see if DNS was working :-(

I think I shall have to dump the acquired router (it's a BT 2wire jobbie, for those in the UK) and get a proper one. The problem with the 2wire one is it is also an ADSL modem, and the fact it's not acting as one appears to be problematic.

---

### Post by Jethro_uk on 2010-06-15
duh !!!! Firestarter had an option all along to enable DHCP !

Turned it on, and all is peachy !

---

### Post by Iowan on 2010-06-15
Does "peachy" mean [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by Jethro_uk on 2010-06-16
> **Iowan said:**
> Does "peachy" mean [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

you got it !8)

---

