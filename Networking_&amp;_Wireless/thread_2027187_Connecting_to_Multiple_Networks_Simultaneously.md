---
title: "Connecting to Multiple Networks Simultaneously"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by CaptainRandom on 2012-07-16
Hi,

I'm a new Ubuntu user, but I've finally had the confidence to make the jump from Windows and install it as my only operating system on my laptop. I'm enjoying it so far, but struggling to configure my network settings.

What I'm trying to do is configure a wired connection to a device that I need to configure, whilst maintain a wireless connection to the internet so that I can bridge the connections for the wired device to download updates.

Bridging aside, I can't get the wired and wireless interfaces to play nicely with one another. I'm connected to the 'net via wireless and everything functions happily. I connect the device via ethernet (device has an address of 172.16.1.1 /24), configure eth0 with 172.16.1.100 /24 and under routing tick the checkbox for "use this connection only for resources on it's network". I ping the device and I get the message:

```
ping: sendmsg: Operation not permitted
```

I disconnect the wireless, and I can connect to the device on eth0 no problems. I reconnect the wireless and I have no internet connectivity until I disconnect the wired interface. Can anybody please give me some pointers on how to make both work?

---

### Post by Kirk Schnable on 2012-07-16
Can you give me the output of the following commands, both WITH and WITHOUT the wired connection plugged in (but with the wireless active both times)?

First of all I want to verify that your settings are what you say:
```
ifconfig
```

Then let's have a look at your routing table:
```
route -n
```

Thanks
Kirk

---

