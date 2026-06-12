---
title: "Lots of packet loss"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by Bigfatnoob on 2011-03-03
Hey there, im having a really hard time with massive packet losses

when i use mtr <router ip> i get about 80% packet loss out of 100 packets sent

same thing when i mtr google.com for instance (packet loss even worse)

Ive reinstalled ubuntu 10.04, im using a brand spanking new network card, ive tired 4 different cables, changed IP and mac adresses. nothing seems to work

Any ideas as to what is causing my packet loss. 

Im going to do memeory test and bios flash next :/

---

### Post by matt_symes on 2011-03-03
Hi

> **Bigfatnoob said:**
> Hey there, im having a really hard time with massive packet losses

when i use mtr <router ip> i get about 80% packet loss out of 100 packets sent

same thing when i mtr google.com for instance (packet loss even worse)

Ive reinstalled ubuntu 10.04, im using a brand spanking new network card, ive tired 4 different cables, changed IP and mac adresses. nothing seems to work

Any ideas as to what is causing my packet loss. 

Im going to do memeory test and bios flash next :/

This not my area but to help others diagnose the issue i suspect people will need more information.

Are you wired or wireless ?

Run the mtr test and copy and paste the results of 100 pings back here so people can see to both your local router and google.

What hardware do you have. Open a terminal and type

```
sudo lshw -C network
```

Post the results back here.

Do you have a firewall running ?

```
sudo iptables -F
```

and run tests again.

Are you behind a proxy ?

Kind regards

---

### Post by pl@yer on 2011-03-03
So other systems on this network are not experiencing same problem?

Router maybe has a messed up port, try plugging into a different one?

---

### Post by Bigfatnoob on 2011-03-03
Im on wired connection.


my hardware = 

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:19:66:d8:08:be
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:d800(size=256) memory:fdeff000-fdefffff(prefetchable) memory:fdee0000-fdeeffff(prefetchable) memory:feae0000-feafffff(prefetchable)
  *-network
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth0
       version: 8b
       serial: 00:24:01:01:8c:af
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.15 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e800(size=256) memory:febffc00-febffcff


When i enter "sudo iptables -F" into terminal i get NO response.

mtr 192.168.0.1 (3 attempts)

1st attempt :
 
Host        Loss%    Snt    Last    Avg     Best     Wrst    StDev    
1. 192.168.0.1       78%    100    0.3    0.3    0.3    0.3    0.0


2nd attempt :

1. 192.168.0.1       45%    100    

3rd attempt :

1. 192.168.0.1       63%     100


mtr google.com (3 attempts)

1st attempt :

Host                                                Loss%    Snt    Last    Avg     Best     Wrst    StDev
1. 192.168.0.1                                   37%     100
2. portal.csfs.co.za                             37%    100
3. 10.0.0.1                                        37%    100
4. ???
5. ppp72-217.netactive.co.za               37%    100
6. 196.38.73.17                                   37%    100
7. core2b-rba-te2-0-1.ip.isnet.net         37%    100
8. mi-za-rba-p6-gi3-0-2-104.ip.isnet.net 37%    100
9. mi-uk-dock-p2-po2-2,ip.isnet.net      37%    100
10.core-dock-gil-0-19-104.ip.isnet.net  37%    100
11.168.209.246.3                               37%    100
12.195.66.226.125                             37%    100
13.209.85.252.76                               37%    100
14.209.85.251.58                              37%    100
15.74.125.230.147                            37%    100

2nd attempt roughly 77% loss

3rd attempt roughly 17%

---

### Post by Bigfatnoob on 2011-03-03
just me having the problem no other machines having troubles...

alrdy tried plugging into different port that one of the other machines are using... that machine has 0% packet losses

---

### Post by matt_symes on 2011-03-03
Hi

Hmmmm. That's terrible packet loss. It seems to be between you and the router.

EDIT: Did not fully read your last post. Scratch below.

What's your setup? Modem into a router into you PC ?

Assuming you have a router, do you have a spare router you can try ? Or as suggested try another port ? How have you configured it ?

Kind regards

---

### Post by pl@yer on 2011-03-03
You tried a different NIC...did you try plugging it into a different card slot? Maybe the slot itself is flakey (IMHO seems like a long shot).

It couldn't hurt to run memtest. I would also check your PSU voltages.

---

### Post by matt_symes on 2011-03-03
Hi

What are your other PC's running ? Is this a Ubuntu problem or a Ubuntu machine specific problem ?

Kind regards

---

### Post by Bigfatnoob on 2011-03-03
HAHA

i did put card into all the slots :P no change

I also did memory check and no problems found

---

### Post by pl@yer on 2011-03-03
I would also make sure there isn't an IP address conflict.

I had a funny situation with DHCP server the other day where a scpecific NIC kept loosing  its IP. I excluded the IP from the DHCP pool and manually assigned its IP and it suddenly worked great.

I noticed the problem using wireshark, filtered traffic by it's own IP.

this would show any traffic with either ip addresses
```

ip.addr == 192.168.0.1 || ip.addr== 192.168.0.3

```

---

### Post by Bigfatnoob on 2011-03-03
hmm i dont have access to the other PC's (passwords)

but i know the one is running WIN 7, the other is 10.04 and the last is 10.10

mine is 10.04

---

### Post by Bigfatnoob on 2011-03-03
I also checked for IP conflicts... then i unplugged one of the PC that has 0% packet loss
and used its IP on my machine. i still had the packet loss

---

### Post by pl@yer on 2011-03-03
You could run wireshark on the problem machine and filter by your IP address and the router's IP. 

```

ip.addr == 192.168.0.1 || ip.addr== 192.168.0.3

```

---

### Post by Bigfatnoob on 2011-03-03
[FONT=monospace]that command only gives me errors
[/FONT]

---

### Post by pl@yer on 2011-03-03
Is it possible someone is playing with ettercap or something? Doing a man in the middle on you and their etterfilter is messing you up? 

How well do you know the others on the LAN segment? :)

---

### Post by pl@yer on 2011-03-03
> **Bigfatnoob said:**
> [FONT=monospace]that command only gives me errors
[/FONT]

Not a command.
That was a filter to put in the filter box when running wireshark.

---

### Post by Bigfatnoob on 2011-03-03
i doubt they would be screwing around... time is money

how can i see if sumone is using this ettercap thing?

---

### Post by pl@yer on 2011-03-03
I am not an expert at this...just played with it a little (on my own network, my own machines and only victims were my kids :D) 

Arp poisoning is a way to fool;
 the router into thinking the attacker is you 
 and the victim that the attacker is the router

If you know the mac address of your router and your local arp table shows something different then I would wonder :)

I don't think this is likely what is going on... Just thought I'd dust off the old tinfoil hat :D

---

### Post by pl@yer on 2011-03-03
I would try booting a live CD if you still have the problem it might be hardware.

---

### Post by jugad on 2012-07-29
This is coming a bit late... but I am sure other people are still facing the issue. In my case, this was because of a bad realtek driver...

This is where I found the fix: [http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping](http://askubuntu.com/questions/46942/how-do-i-stop-my-ethernet-network-connection-from-dropping)

---

### Post by wildmanne39 on 2012-07-30
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

