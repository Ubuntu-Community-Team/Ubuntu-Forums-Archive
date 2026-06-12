---
title: "Last hope! Apollo Fast Ethernet card not detected."
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by Elamite on 2005-12-22
Hello!

This is the fourth forum I try to get an answer for my problem. Other forums hasn't even said beep...

I'm quite new to LINUX and have tried to boot my laptop with KNOPPIX. Lacking the result I wished for I've tried getting some help from everywhere... After not getting any help from anywhere I finally stumbled upon the UBUNTU live-cd and was hoping everything should work... Still the same problem.

So, what is my problem? My problem is an Apollo Fast Ethernet PCMCIA card not being detected properly. The card works in windows but not in LINUX. Not since kernel 2.6 at least. I know I tried an old KNOPPIX cd a year ago and that cd could detect my network card automatically. 

When I type ifconfig I get local loopback. No eth0 is available. When I try 'ifconfig eth0 up' I get: "eth0: ERROR while getting interface flags: No such device". When I type 'dmesg' I have localized a line saying "cs: pcmcia_socket1: unable to apply power", which is quite weird since the Power-lamp, the FULL-lamp and 100-lamp is lit. The ACT(IVE)-lamp flashes now and then as well. Just as if everything was working, just as it does in windows when working.

I know from earlier experience that the driver 'pcnet_cs' should support my particular ethernet card but I don't know what to do after I type 'modprobe pcnet_cs'.

I really, really want to go to the bottom with this issue. I just don't know where to start looking since everywhere I go, I get no answer. This card has been working under KNOPPIX with 2.4 kernel.

ANY help would be GREATLY appreciated! ;)

---

### Post by Lambert on 2005-12-22
If it is supported by pcnet_cs and it modprobes ok then here are some things I would consider.

Have you looked here though. Haven't read it nor do I know if it answers your questions.

[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

1. after you modprobe pcnet_cs run this command

```
sudo lshw -C network
``` 
You should see your ethernet device and a line configuration: does it show the pcnet_cs driver allocated to the device? Here's what mine looks like. (of course it's not same device, yours should say driver=pcnet_cs.) 

```
configuration: autonegociation=on broadcast=yes driver=e100
``` 
2. If driver is allocated then go to system>administration>networking enable the device and configure the network settings. then try to activate.

---

