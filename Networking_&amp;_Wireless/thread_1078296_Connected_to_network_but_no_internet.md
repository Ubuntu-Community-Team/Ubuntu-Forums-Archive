---
title: "Connected to network but no internet"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Sh4wn on 2009-02-23
Hi,

I've got a quite annoying problem:
I have a cable modem, where only one network cable can be plugged in to. So I have bought a switch (Sitecom), that switch contains five ports for network cables. One of them goes to the cable modem, and two other ports are used by computers.

The problem is, I can successfully connect to the network, and I have an IP etc. But I can't browse the internet.

ifdown doesn't work: 'ignoring unknown device eth0'
ifup gives the same message.

I included the output of dmesg, syslog, ifconfig and my /etc/network/interfaces as an attachment.

/etc/resolv.conf does have 2 entries retrieved from the network manager.
I also can't browse any site using only the IP, so I don't think it's a DNS problem.

---

### Post by rickyjones on 2009-02-23
> **Sh4wn said:**
> Hi,

I've got a quite annoying problem:
I have a cable modem, where only one network cable can be plugged in to. So I have bought a switch (Sitecom), that switch contains five ports for network cables. One of them goes to the cable modem, and two other ports are used by computers.

The problem is, I can successfully connect to the network, and I have an IP etc. But I can't browse the internet.

ifdown doesn't work: 'ignoring unknown device eth0'
ifup gives the same message.

I included the output of dmesg, syslog, ifconfig and my /etc/network/interfaces as an attachment.

/etc/resolv.conf does have 2 entries retrieved from the network manager.
I also can't browse any site using only the IP, so I don't think it's a DNS problem.

Have you tried just connecting a single computer directly to the modem? Please post results of that operation.

My guess is the switch is the problem but more tests will need to be done.

Thanks,
Richard

---

### Post by Sh4wn on 2009-02-23
Ok, the problem just got stranger. When I connect directly to the cable modem, it also doesn't work, got exactly the same symptons. Output is included as attachment.

Even windows can't connect to the internet, while the other computer can. Maybe the IP adress is in 'use'? or something. I have no clue.

---

### Post by rickyjones on 2009-02-23
> **Sh4wn said:**
> Ok, the problem just got stranger. When I connect directly to the cable modem, it also doesn't work, got exactly the same symptons. Output is included as attachment.

Even windows can't connect to the internet, while the other computer can. Maybe the IP adress is in 'use'? or something. I have no clue.

Is everything configured using DHCP? Have you tried contacting your ISP support?

I know some ISPs will lock the connection to a specific MAC address. That could be the problem as well.

Thanks,
Richard

---

### Post by Sh4wn on 2009-02-23
> **rickyjones said:**
> Is everything configured using DHCP? Have you tried contacting your ISP support?

I know some ISPs will lock the connection to a specific MAC address. That could be the problem as well.

Thanks,
Richard

Yes, everything is configured as Automatic (Use DHCP). I'm just back from vacation, and before my vacation it mostly worked (sometimes it couldn't connect to the **network**, but most of times it worked perfectly).

I haven't contacted the ISP, because I don't own this connection.

---

### Post by Iowan on 2009-02-23
> **rickyjones said:**
> I know some ISPs will lock the connection to a specific MAC address. That could be the problem as well.Sometimes the modem will lock onto the MAC address - you can cycle power to the modem to see if it resets.  If it does, you will need to repeat the process when you restore original configuration.

The "ignoring unknown device" message sounds like driver issue... but you said you can connect to the local neteowrk?

---

### Post by Sh4wn on 2009-02-23
> **Iowan said:**
> Sometimes the modem will lock onto the MAC address - you can cycle power to the modem to see if it resets.  If it does, you will need to repeat the process when you restore original configuration.

The "ignoring unknown device" message sounds like driver issue... but you said you can connect to the local neteowrk?

Well, it did work before, so I don't think it's the driver. It has an onboard ethernet adapter, realtek chipset. That one is quite good supported isn't it?

And this adapter has worked fine for more then a year on my previous network (I moved to the city where I study)

---

### Post by Sh4wn on 2009-02-24
Bump?

---

### Post by rickyjones on 2009-02-24
> **Sh4wn said:**
> Bump?

Did you say that one of your other computers was working with this connection? Is it configured any differently? Have you tried using a router instead of a switch?

Thanks,
Richard

---

### Post by mckenna1977 on 2009-02-24
It sounds like you're connected to the network and have the IP address from DHCP but you're not getting the correct routes

from a terminal try printing your route table using
route -n

if your route to the internet isn't there try adding it
Example:
route add -net 0.0.0.0 gw 192.168.100.1 dev eth0

You can also try making sure you've the right DNS entries in /etc/resolv.conf

---

### Post by Sh4wn on 2009-02-24
route -n output:
```

Destination      Gateway       Genmask            Flags    Metric       Ref     Iface
83.84.136.0      0.0.0.0       255.255.248.0      U        1            0       eth0
169.254.0.0      0.0.0.0       255.255.0.0        U        1000         0       eth0
0.0.0.0          83.84.136.1   0.0.0.0            UG       0            0       eth0

```

I guess it's allright?

@ricky I do not have a router (only an ADSL router, which I can't connect to the cable modem)

And I have no idea how my house mate has configured his computer, he only says it's quite slower through the switch than directly. I don't think he did something special in windows XP

---

### Post by matikk on 2010-03-05
why not to visit [www.virtualsaver.co.uk](www.virtualsaver.co.uk)

---

