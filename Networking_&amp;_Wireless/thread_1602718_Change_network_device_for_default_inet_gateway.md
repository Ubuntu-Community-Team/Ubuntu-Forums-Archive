---
title: "Change network device for default inet gateway?"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Ferrat on 2010-10-21
I've been struggeling with this for a few hours now, googleing and so on trying to find an easy way to just switch which device I want as primary for internet connections. 

After long battles I'm at a loss, this is the current automatic routing 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
85.225.76.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
85.225.76.0     0.0.0.0         255.255.252.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     2      0        0 wlan0
0.0.0.0         85.225.76.1     0.0.0.0         UG    0      0        0 eth0

```

If I remove the wired connection I get 

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
85.225.76.0     0.0.0.0         255.255.252.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     2      0        0 wlan0
0.0.0.0         85.225.76.1     0.0.0.0         UG    0      0        0 wlan0

```

now before I installed 10.10 the wlan was set as primary since I used that one to install 10.04, however not thinking about that now I used the wired connection and now I'm stuck with that as primary as soon as it's active :( 

I need both connections live, yes both have internet access actually getting their IPs from the same AP but I want to switch so that the wlan0 device is the primary and eth0 secondary, I can mees around with route commands etc but as soon as the eth0 connects again it's once more recognized as primary by Ubuntu and given a default inet route even if wlan0 already has one manually set by me.

Looked around in the settings but can't find where I change it? it must be just a config file or something somewhere that I need to fix?

what I want is 
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
85.225.76.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
85.225.76.0     0.0.0.0         255.255.252.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     2      0        0 wlan0
0.0.0.0         85.225.76.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by Ferrat on 2010-10-21
Ok, sort of solved it, blocked the eth0 connection from ever becoming default, however this is not exactly what I wanted since I now can't be with out the wireless if needed without changing it back so still marked as unsolved as I really want to know how to change priority on them.

---

### Post by Nazgand on 2012-08-22
I am looking for the same thing.

I work in networking, and I often need to plug and unplug into many ethernet jacks throught the day, but this interrupts my telnet connections, and in some cases ruins them.

So what I would like is to be able to send all my traffic over the wifi. This would be very helpful.

---

### Post by Kirk Schnable on 2012-08-23
> **Nazgand said:**
> I am looking for the same thing.

I work in networking, and I often need to plug and unplug into many ethernet jacks throught the day, but this interrupts my telnet connections, and in some cases ruins them.

If you work in networking, I'd expect you to be familiar with static routes.

```
sudo route add -host 192.168.1.55 dev wlan0
```

That will route 192.168.1.55 out wlan0.


> **Nazgand said:**
> So what I would like is to be able to send all my traffic over the wifi. This would be very helpful.
Is there something I'm missing here?  If you want to use your wireless for everything then why are you plugging in?

Kirk

---

