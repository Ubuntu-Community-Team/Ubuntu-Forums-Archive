---
title: "Issues connecting with wireless"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by diggs on 2006-01-04
When I first installed ubuntu on my laptop, I was near my router, got both wireless and wired going fine. just fine.

Next morning, for what ever reason neither XP or ubtuntu would start up. I was not really surprised, as things have been going wrong a lot with ubuntu. but nevermind that, I can post a link to my drunken rant if you like.

Anyways; when I type in iwconfig this is what I get:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"derek"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

etho is my wired connection. Now, I have an idea why it isn't working, as when I reinstalled ubuntu for the 40th time on my laptop I was nowhere near a wireless connection, and therefor it just wasn;t configured! that is my best explanation.
I already tried going system>admin>networking  and nothing happened. I have also tried pushing function+f2 to enable the wireless card but nothing happened.

Help?

P.S. it's intel centrino in a dell inspiron 600 laptop if that helps!

---

### Post by KingBahamut on 2006-01-04
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

We have a whole guide over there, written by our friend Lambert. 

Alternately, 

[https://wiki.ubuntu.com/WiFiHardware](https://wiki.ubuntu.com/WiFiHardware) 

Should also help. 

let us know if either work for you.

---

### Post by diggs on 2006-01-04
It kind of worked. I can now ping my router, but go no further. **sigh**

Why is everything that is so simple in windows a real pain in the ass in ubuntu?

---

### Post by LeTon on 2006-01-05
Hi, good people....

Could somone point a finger where do I go from here?????Please

vch@leton:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:63:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:fe8fec00-fe8fecff irq:21
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@01:05.0
       logical name: eth1
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.0 f[B][B][I][B][B][B][B][B]irmware=)\uffff\uffff\uffff\uffff\uffff\uffff\uffff (\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffffW8 link=no multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
vch@leton:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: FF:00:FF:00:FF:00
          Bit Rate=0 kb/s   Tx-Power=off
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/B][/B][/B][/B][/I][/B][/B]
[/B]

I guess the question is...how to fix this...can't seem to be able to figure it out on my own.
Thank you.

---

### Post by Lambert on 2006-01-05
[quote=diggs]It kind of worked. I can now ping my router, but go no further. **sigh**

Why is everything that is so simple in windows a real pain in the ass in ubuntu?[/quote]

Plain and simple answer to this....Vendors support and test their products with windows and release it to market knowing it will work with everything you need. Linux is gaining in this area but it's still a ways off before it's just as easy in linux. Depending on the device and driver some will say it's easier in linux. 

I personally fought with my wireless card for a couple weeks and many different distros. Finally decided to research and buy supported hardware and settled on ubuntu because it's wireless is a little better then most other gnu/linux distros.

Now I'm not sure of the steps you took and I have no personal experience using wireless device in the centrino package. But you said you can ping your router so I'll take it from there.

If you can ping your router that means you're associated with it and have an ip address assigned to the device. Post the output of these commands.

```
 route -n
```
```
sudo cat /etc/network/interfaces
```

can you ping a site via it's ip address?
```
ping -c 4 82.211.81.166
```
post this file

```
sudo cat /etc/resolv.conf
```

Are you running open signal or encryption (wep or wpa)
Are you doing a static ip assignment or dhcp?

NOt knowing where you looked did you go through the WTG in my signature? There was a link to there where KB pointed you to.

I'll stop here and see where we get.

---

### Post by Lambert on 2006-01-05
[quote=LeTon]Hi, good people....

Could somone point a finger where do I go from here?????Please

vch@leton:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:63:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.101 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:fe8fec00-fe8fecff irq:21
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@01:05.0
       logical name: eth1
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.0 f[B][B][I][B][B][B][B][B]irmware=)\uffff\uffff\uffff\uffff\uffff\uffff\uffff (\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffff\uffffW8 link=no multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
vch@leton:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 19
of Wireless Extension, while this program supports up to version 18.
Some things may be broken...

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: FF:00:FF:00:FF:00
          Bit Rate=0 kb/s   Tx-Power=off
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/B][/B][/B][/B][/B][/I][/B]
[/B]

I guess the question is...how to fix this...can't seem to be able to figure it out on my own.
Thank you.[/quote]

Hmmm, not sure exactly but I would consider building a new driver. See if these instructions can get you going.

[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

The instructions only state to install linux headers. You will also need build-essential and gcc-3.4 which are both on the install cd if you don't have internet access.

You also may want to start a new thread about this. after trying to activate wireless run the command *dmesg* and look for any relevant output pertaining to your device and post it in that thread. There may be another error that can be searched for better.

---

### Post by LeTon on 2006-01-06
Thank you Mr. Lambert

I'll fiddle around with this for a while...see what happens.

---

### Post by diggs on 2006-01-07
thanks, I got it figured out a while ago. what was perplexing me was that it worked under ubuntu at first, ben then not when I reinstalled it. turned out that there was a powerout at night that screwed up all my router's settings. defaulted all the security and passwords and what not.
That's what you get for living in an igloo in Canada I guess.

---

