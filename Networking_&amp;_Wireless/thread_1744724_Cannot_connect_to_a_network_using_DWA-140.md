---
title: "Cannot connect to a network using DWA-140"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Michael_BoG on 2011-04-30
Hello Ubuntu forums!
I'm a kinda experienced Linux-user, but this has got me scratching my head. I followed [this]("http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working") on how to install and configure the DWA-140 to work with Ubuntu 11.04, and "iwlist scan" outputs all of the networks. When i try to connect to my network however, the icon up in the right corner with the signal bars just keeps on going until it prompts for a password to join the network. I enter the password and it goes on for some time, and then it prompts me for the password again. 

I'm using a D-Link DIR-655 with the "Only N" mode active. It works fine on other computers (Windows, sigh) but not on my Ubuntu one. 

Could someone please help me with this?

- Michael

---

### Post by chili555 on 2011-04-30
> I'm using a D-Link DIR-655 with the "Only N" mode active.Is the behavior improved if the router is set to mixed B,G and N mode?

---

### Post by Michael_BoG on 2011-04-30
Hello. I'll try to set it to both tomorrow. I use N only because then the router won't have to throttle down the N to match the G units. Are there compability issues with N in Ubuntu? Or are there any fixes for this, since i did buy the DWA-140 to get the N functionality. 
 
Thanks,
Michael

---

### Post by chili555 on 2011-04-30
> Are there compability issues with N in Ubuntu?Oh, yes; with some wireless drivers. Search this forum for 'N speed' and you'll see quite a few questions. My thought is that perhaps your card won't connect at N speed because it can't.

Does yours use rt2870sta?```
lsmod | grep rt2
```

---

### Post by andryandrew on 2011-04-30
Yes, there's an issue with the DWA-140 rev.B2 and the N mode (I have the dongle too). I found a solution, but it has to be redone for EVERY kernel update, because I'm not able to build a DKMS module.
I've posted the a step-by-step guide on the bug page on Launchpad ([#606839]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606839")):
                 > With the instructions from this ([http://]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[www.linuxcrew.]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[de/2010/]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[10/11/rt2870-]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[compile-]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[error-under-]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[kubuntu-]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[maverick-]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[10-10/?]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")[lang=en]("http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en")) site, adapted for the rt3070 driver, I managed to get the dongle working also in Maverick and Natty.
To sum up, That's what I've done:
 - Downloaded the source of the package "rt3070" from from  ppa:logari81/ppa (lucid version). Maybe on the ralink site there's a  newer version, but they have messed up the driver names in a way that i  couldn't understand.
 - Extracted the source and patched with the patch provided in the linked article ([http://www.linuxcrew.de/2010/10/11/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch](http://www.linuxcrew.de/2010/10/11/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch))
 - Unplugged the dongle, typed "sudo rmmod rt2870sta"
 - make && sudo make install
 - sudo modprobe rt3070sta
 No need for me to blacklist the previous driver, at the reboot it  selected the 3070 automatically. Obviously with this method you lose  dkms support, so you have to recompile the driver for every kernel  update. Maybe we can contact the developer of that package? The problem  with Maverick is very easy to fix: that patch only changes some function  names that changed in the .35 kernel.


I've noticed that the patch is not downloadable anymore. However you can still follow the instruction on the linked article.

---

### Post by Michael_BoG on 2011-05-01
> **chili555 said:**
> Oh, yes; with some wireless drivers. Search this forum for 'N speed' and you'll see quite a few questions. My thought is that perhaps your card won't connect at N speed because it can't.

Does yours use rt2870sta?```
lsmod | grep rt2
```

Yes it does.

> **andryandrew said:**
> Yes, there's an issue with the DWA-140 rev.B2 and the N mode (I have the dongle too). I found a solution, but it has to be redone for EVERY kernel update, because I'm not able to build a DKMS module.
I've posted the a step-by-step guide on the bug page on Launchpad ([#606839]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606839")):
                 

I've noticed that the patch is not downloadable anymore. However you can still follow the instruction on the linked article.

So if i do that it should work with the "N" mode?

Edit: This requires internet on the machine.. I don't have any ability to stretch wires all over the house to get internet on it.. Shame..

---

### Post by Michael_BoG on 2011-05-01
Alright, i got the network working by switching the router to B/G/N mode. Shame the speed is a bit slower on the N units, oh well. Another kind of problem now tho, internet keeps randomly falling out. I have no idea why this is happening. 
Also, can i run the DWA-140 on Ubuntu Server too? Or am i doomed to using Ubuntu Desktop on a server..
(No moral speech about hosting servers on wireless, please)

---

### Post by chili555 on 2011-05-01
> Also, can i run the DWA-140 on Ubuntu Server too? Certainly.> internet keeps randomly falling out. I have no idea why this is happening. Please post:```
lsmod | grep rt2
```Perhaps we have a driver conflict.

---

### Post by Michael_BoG on 2011-05-01
Here is the output of it, the issues however seems to have gone away after i rebooted it.
```

root@buwk:/home/michael# lsmod | grep rt2
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta

```Also, if you could be so kind and tell me how i connect to the network via terminal and no GUI features, that'd be awesome.

---

### Post by chili555 on 2011-05-01
I see no driver conflict.> tell me how i connect to the network via terminal and no GUI features, that'd be awesome. The usual way in a server is to populate /etc/network/interfaces; for example:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.x.y
netmask 255.255.255.0
gateway 192.168.x.1
wpa-essid your_router
wpa-psk your_key
```And also /etc/resolv.conf:```
nameserver 192.168.x.1
```Usually, the router will do as a DNS nameserver. Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```You should connect. Let's check:```
ping -c3 www.google.com
```If you don't connect, recheck your settings; if you do, you will connect on boot automatically.

You did want a static IP address, didn't you?

---

### Post by Michael_BoG on 2011-05-01
Out of that config, i see that there is a static IP set, which is what i wanted. Thanks a lot for all the help!

---

### Post by Michael_BoG on 2011-05-02
Gah, when i finally got it working then it stops working again.
When i connect to the network, i get the IP 192.168.0.194, when i browsed to that IP before the "crash" then i could access the webpage and all that, ssh and stuff, now the internet crashed on it, like, it can ping other computers, it can ping google so i know it's got internet, but when i try to ping that machine or when i try to browse to it's IP then it doesn't work. 
Any solutions?

---

### Post by chili555 on 2011-05-02
On the server:```
ifconfig
ping -c3 www.google.com
route -n
```On another machine on the network:```
ping -c3 192.168.0.194
route -n
```Can you confirm that x.194 is outside the range of the DHCP server in the router?

---

### Post by Michael_BoG on 2011-05-02
> **chili555 said:**
> On the server:```
ifconfig
ping -c3 www.google.com
route -n
```On another machine on the network:```
ping -c3 192.168.0.194
route -n
```Can you confirm that x.194 is outside the range of the DHCP server in the router?

It seems like it didn't happen now, i re-formatted the system with a clean install. No issues atm. 

```
wlan0     Link encap:Ethernet  HWaddr f0:7d:68:fb:0d:50
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f27d:68ff:fefb:d50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:252874 (252.8 KB)  TX bytes:51041 (51.0 KB)

```

```
ping -c3 google.com
PING google.com (74.125.39.104) 56(84) bytes of data.
64 bytes from fx-in-f104.1e100.net (74.125.39.104): icmp_req=1 ttl=51 time=60.3 ms
64 bytes from fx-in-f104.1e100.net (74.125.39.104): icmp_req=2 ttl=51 time=59.5 ms
64 bytes from fx-in-f104.1e100.net (74.125.39.104): icmp_req=3 ttl=51 time=61.2 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 59.562/60.367/61.225/0.679 ms

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0

```

And the static-ip is not outside of the dhcp subnet. I'll change it now.

Edit: I've changed the IP to 192.168.0.200, ip is now outside of the dhcp pool (x.199)

---

### Post by chili555 on 2011-05-02
I'm subscribed to the thread, so post back if you have more questions.

---

### Post by Michael_BoG on 2011-05-03
Ok, well, i got one other question: the internet on the machine keeps falling out, not by any faults tho, could it be that it's disabling it because of some inactivity thing? If i make a cron-job to ping -c3 google.com every 10 minutes, would that work?

---

### Post by chili555 on 2011-05-03
> could it be that it's disabling it because of some inactivity thing?I doubt it.> If i make a cron-job to ping -c3 google.com every 10 minutes, would that work? Maybe or maybe not.

Usually, if your machine doesn't get a periodic response from the router, it drops. Is the router close enough? Does it have a power setting? Is it set to 100%? Is it on channel 6, the same as microwaves, cordless phones, etc.? I have better luck on channel 1. Is the router old? Is it time to retire it?

---

### Post by Michael_BoG on 2011-05-03
> **chili555 said:**
> I doubt it.Maybe or maybe not.

Usually, if your machine doesn't get a periodic response from the router, it drops. Is the router close enough? Does it have a power setting? Is it set to 100%? Is it on channel 6, the same as microwaves, cordless phones, etc.? I have better luck on channel 1. Is the router old? Is it time to retire it?

The router is aprox. 10m apart from the machine. Power setting on the router is set to 100%, and yes, it's on channel six, every other network around here runs on 1 or 11 (ye, all networks actually). The router is about 4 months old (D-Link DIR-655).

I haven't noticed anything after the last format, i actually got the nameservers for my domains working with it too. 

We'll see what happens, thanks for all the help so far!

---

### Post by streetwriter on 2012-01-11
> **andryandrew said:**
> Yes, there's an issue with the DWA-140 rev.B2 and the N mode (I have the dongle too). I found a solution, but it has to be redone for EVERY kernel update, because I'm not able to build a DKMS module.
I've posted the a step-by-step guide on the bug page on Launchpad ([#606839]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606839"))...

I've been struggling with this over several nights on Natty, without success. It was able to connect using my WDA-140 by blacklisting everything but rt2870sta, but I was still stuck at g speed. Meanwhile, I had problems compiling the 3070 driver. It wasn't made clear to me that it should be compiled from my home folder. I finally figured that out and I was able to compile it without errors. I ran the rmmod and modprobe commands and checked with lsmod that the rt3070 was the only thing loaded. But I was still at g speed. I shut down and started up again and couldn't connect at all via wireless. 

I've gone over the instructions numerous times and it's just not working for me. What am I missing?

I'm now back to the Broadcomm adapter built in to my Acer Aspire laptop and using B43 to connect. I'd rather put my new WDA-140 to use at n speed. Any suggestions?

Oh, and I should add that my D-Link DIR-655 gig router is set up to use WPA2 encryption.

---

### Post by chili555 on 2012-01-12
There are three great mysteries in life:

# Where were we before we were born?
#Where will we be after we die?
#How do I get N speeds in a RT2870 device?

I am quite sure I don't know the definite answer to any of the three. However, if you compiled a driver from source, it uses an /etc/Wireless/RT2870STA/RT2870STA.dat, or somesuch file and was compiled with specific settings in os/linux/config.mk. Are there any adjustments there that are helpful? If you need to change config.mk, you will need to recompile:```
cd Desktop/downloaded_file
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```

---

### Post by streetwriter on 2012-01-12
Thank you very much for trying to help; however, as I am not completely familiar with the arcane aspects of Linux programming, I don't really know what to make of your suggestion or understand what I might do next. Specifically, what might I change in config.mk and why would that be necessary?

I did fix the linux.h file as directed in the posting with details about a supposed remedy for getting n speed on the device. It was clear enough why I should do that and how to do it.

I also blacklisted my rt2870sta, shut down, powered up with the DWA-140 plugged in, expecting to have the newly compiled and installed rt3070sta loaded, but instead, when I typed lsmod in a terminal I discovered the rt2870sta had in fact loaded anyway (perhaps if only to demonstrate my lack of Linux understanding). It hardly mattered: I couldn't connect with my wireless. That's when I unblacklisted b43 and reverted to my original settings, while intending to investigate further.

Is Oneiric any better with its support for the DWA-140?

---

### Post by chili555 on 2012-01-12
> Is Oneiric any better with its support for the DWA-140?Not so far with respect to N. So far, it's compile your own, cross you fingers and hope.

Let's start at the start. Did you compile an rt2870sta driver or an rt3070sta driver? Which one? Let's go back through it step-by-step and see what we can do.

Please also give me a link to the linux.h (?) fix.

DISCLAIMER: I don't have the device, so you are my eyes and ears.

---

### Post by streetwriter on 2012-01-12
Reply #5 in this thread seemed to offer the hope of a solution, so I followed the directions in it.

-Downloaded the source of the package "rt3070" from from ppa:logari81/ppa (Lucid version).
-Extracted the source and followed the instructions at [http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en](http://www.linuxcrew.de/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en)) site, adapted for the rt3070 driver. (Specifically, I renamed usb_buffer_alloc() and usb_buffer_free() as directed.)
- Unplugged the dongle, opened a terminal and typed "sudo rmmod rt2870sta."
- Typed "make" (or "sudo make," I can't remember now), which ran without errors.
- Typed "sudo make install," which ran without errors.
- Type "sudo modprobe rt3070sta," which ran without error.
- Inserted the dongle and typed "lsmod | grep ^rt," which showed that the rt3070sta was loaded.

There were a few attempts to connect but I think eventually it worked. I tried so many things that a lot of it remains a blur, but I think I then blacklisted my rt2870 to ensure there was no conflict on booting, but after I powered down and up again my wireless could not connect and with lsmod I discovered the 2870 had loaded anyway and there was no report of the 3070.

---

### Post by chili555 on 2012-01-12
I downloaded and extracted the file rt3070-2.3.0.2. In the config.mk file it already says, in part:> #Support features of 802.11n Draft3
HAS_DOT11N_DRAFT3_SUPPORT=y

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=yThere doesn't appear to be anything further we might change here.

The folder contains a file RT3070STA.dat. It installs it in /etc/Wireless/RT3070STA/. I notice it says:> WirelessMode=5That is defined as 11ABGN mixed, which seems reasonable. You might try amending it to WirelessMode=9, which is defined as 11BGN mixed.```
sudo gedit /etc/Wireless/RT3070STA/RT3070STA.dat
```Proofread carefully, save and close gedit. Reload the driver:```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe rt3070sta
```Any improvement?> with lsmod I discovered the 2870 had loaded anyway and there was no report of the 3070. Let's have a look at:```
cat /etc/modprobe.d/blacklist.conf.
```

---

### Post by streetwriter on 2012-01-12
Interesting. And I certainly appreciate the help. Unfortunately, my laptop is at home today and I am at my office. I won't be able to do anything more until this evening (EST in Ottawa, ON).

If it helps in the interim, I did set my DIR-655 router to GN mode only, because there didn't seem to be a need for anything else. Would that make any difference in settings I might change? And, as I mentioned before, I am using WPA2 encryption.

I should add, too, that I also referred to your instructions in reply #10 at [http://ubuntuforums.org/showthread.php?t=1650311](http://ubuntuforums.org/showthread.php?t=1650311) and inserted at the top of my blacklist.conf the following:

```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
b43
ssb
```

I put # comments before and after, to make it clear what I'd added and where. I blacklisted b43 and ssb just to ensure there'd be no conflict with my existing adapter and driver. And I did that after opening the file from the terminal with sudo gedit.

---

### Post by chili555 on 2012-01-12
> I did set my DIR-655 router to GN mode only, because there didn't seem to be a need for anything else.I'd think it might be easier to connect if it were set to BGN. A bit of negotiation goes on between the router and wireless card; I wonder if the router rejects the connection if the card doesn't start at G. Most cards start at B and, if the signal quality is sufficient, ramp up to G and hopefully beyond.> I think I then blacklisted my rt2870 to ensure there was no conflict on booting,Evidently not; it isn't there. Also, the form of the listings for b43 and ssb is incorrect. Please change to:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800lib
blacklist rt2x00lib
blacklist b43
blacklist ssb
blacklist rt2870sta
```Be sure to leave the preceding part of the file untouched. Some of my esteemed colleagues may point out that some of the listings here are redundant; I'll point out that I may be just a bit OCD!

Now let's load rt3070sta automagically:```
sudo su
echo rt3070sta >> /etc/modules
exit
```Now reboot and tell us how it's working.

---

### Post by streetwriter on 2012-01-12
My mistake. I did blacklist b43 and ssb as you suggest; I just didn't type that correctly in my previous reply.

I'll try the other things you recommend and let you know how it all turns out.

---

### Post by streetwriter on 2012-01-12
No change. I am writing this whilst connected via ethernet. Wireless is not working.

I changed my DIR-655 to use BGN and edited line 9 of RT3070STA.dat to WirelessMode=9

In a terminal, I entered:
```
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe rt3070sta
```
Here's the top of my edited blacklist.conf file:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# My custom additions, added Jan 12, 2012, to make DWA-140 work 
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist b43
blacklist ssb
blacklist rt2870sta
# End my custom additions
```
I entered the following as instructed:
```
sudo su
echo rt3070sta >> /etc/modules
exit
```
And quit the terminal.

I shut down, plugged in the DWA-140, and powered up. My wireless tried for several minutes to connect (I am sitting less than six feet from my router, btw) and then quit. I tried it again manually, and the same happened. No connexion.

In a terminal, I typed:
```
lsmod | rt^
```
and it says the rt3070sta is loaded.

What have I missed or done in the wrong order? Any suggestions?

One other thing I am wondering about. I have read so many forum threads over the last few days that something in my router settings jumped out at me. I noticed it's channel width is set to 20MHz. There's an option for 20/40. Just mentioning it in case it could be a factor.

Previewing this, it occurred to me that it's starting to look like so many other postings I've seen with tons of code that often leaves me completely bewildered and frustrated. To any other neophytes watching, relax. It will all get sorted one way or another.

---

### Post by streetwriter on 2012-01-12
I've gone over every step and checked every file to make sure changes were saved. I even confirmed:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070sta
```

---

### Post by streetwriter on 2012-01-12
Meanwhile, the light on the DWA-140 is blinking madly, to taunt me.

Whilst:

```
jeff@jeff-Aspire-5000:~$ lsmod | grep ^rt
rt3070sta             579065  1 
jeff@jeff-Aspire-5000:~$ 
```

---

### Post by chili555 on 2012-01-12
Is the ethernet detached, I hope, as you are trying to connect? Any clues here?```
sudo cat /var/log/syslog | grep -e etwork -e ra0 | tail -n20
```

---

### Post by streetwriter on 2012-01-12
It was. I connected ethernet afterwards to see the world.

You asked (yikes):

```
jeff@jeff-Aspire-5000:~$ sudo cat /var/log/syslog | grep -e etwork -e ra0 | tail -n20
[sudo] password for jeff: 
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> (ra0): device state change: 6 -> 4 (reason 0)
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> (ra0): device state change: 4 -> 5 (reason 0)
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0/wireless): connection 'Auto MalNet' has security, and secrets exist.  No new secrets needed.
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Config: added 'ssid' value 'MalNet'
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Config: added 'scan_ssid' value '1'
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Config: added 'psk' value '<omitted>'
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> (ra0): supplicant connection state:  scanning -> disconnected
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> Config: set interface ap_scan to 2
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Jan 12 21:19:35 jeff-Aspire-5000 NetworkManager[673]: <info> (ra0): supplicant connection state:  scanning -> associating
Jan 12 21:19:50 jeff-Aspire-5000 NetworkManager[673]: <warn> (ra0): link timed out.
jeff@jeff-Aspire-5000:~$ 
```

Nothing terribly personal in there, I trust.

---

### Post by chili555 on 2012-01-13
Nothing personal in there at all. The name of your network is available to anyone on your street that has a wireless card. The authentication key is needed, but is obscured here.

By any chance is your router set to mixed mode WPA *and* WPA2? I think your card will associate easier to WPA2 only. Let's check:```
sudo iwlist ra0 scan
```

---

### Post by streetwriter on 2012-01-13
Again, stupid me: my laptop is at home; however, I am pretty sure it is set to WPA2 only.

---

### Post by streetwriter on 2012-01-13
Remember when I asked in an earlier reply about the channel width setting on my router? I noted it is set at 20MHz. I found this while reviewing my router manual again today:

[INDENT]**Select the Channel Width:** 
**Auto 20/40** - This is the default setting. Select if you are using both 802.11n and non-802.11n wireless devices. 
**20MHz** - Select if you are not using any 802.11n wireless clients. 
**40MHz** - Select if using only 802.11n wireless clients.[/INDENT]

Somehow, the Auto 20/40 did not get set by default; it went to 20 instead. I'm not an expert, but intuitively it could be that I am basically excluding my usb adapter.

---

### Post by streetwriter on 2012-01-13
```
sudo iwlist ra0 scan
```
I tried that and got a bunch of info about two other wireless connexions I can see in my neighbourhood, but nothing about mine. (It isn't broadcast, if that makes a difference.)

Also, whatever I did pretty much froze my system and I had to reboot.

Oh, and although I now get the sense that it probably doesn't make any difference, I changed the channel width on the router to auto 20/40MHz.

---

### Post by chili555 on 2012-01-13
> it could be that I am basically excluding my usb adapter.Sounds very reasonable to me. Have you changed it and tried it?

---

### Post by streetwriter on 2012-01-13
As Sherlock Holmes said, and his distant relative Spock often repeated:
> &#8220;When you eliminate all other possibilities, what remains, no matter how improbable, is the answer."

[LIST]
[*]I've had the adapter working with rt2870sta, but at G speed only.
[*]I downloaded the 3070 driver from the recommended source and compiled it using the required fix noted by linuxcrew.de (which has subsequently [posted another note]("http://www.linuxcrew.de/blog/2011/05/09/rt2870-under-kubuntu-natty-11-04/?lang=en") about performing the same fix to get N speed with Natty.
[*]I've blacklisted all drivers except rt3070sta and it appears as loaded when I type lsmod | grep ^rt.
[*]I've changed settings on my router to ensure I am not eliminating any N-speed signal.
[*]I cannot connect via wireless (my ethernet is disconnected when I try.) I can see my wireless AP listed, but I can't connect.
[/LIST]
The question is: Have I eliminated all the possibilities? If so, what remains? The adapter is defective? There's something about my laptop that doesn't fit with it? I would have to try the adapter on another computer running Natty or Win-something (the latter of which I don't have) to find out.

Still stumped.

---

### Post by streetwriter on 2012-01-14
I also tried other USB ports and connecting the adapter directly instead of using its cradle. And, I've used the adapter on another network, albeit at only G speed.

---

### Post by chili555 on 2012-01-14
> Have I eliminated all the possibilities? If so, what remains? The adapter is defective? There's something about my laptop that doesn't fit with it? I would have to try the adapter on another computer running Natty or Win-something (the latter of which I don't have) to find out.
The conclusion I have, so far, is that rt3070sta may not be correct for your device.

Here is a post that suggests that rt3572sta is the RT2870 driver that gets N speeds: [http://forums.opensuse.org/english/get-technical-help-here/wireless/457238-270mb-s-dwa-160-dwa-140-ralink-rt2870-opensuse-11-4-a.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/457238-270mb-s-dwa-160-dwa-140-ralink-rt2870-opensuse-11-4-a.html)

I built the driver myself and I get a few warnings but no errors; most importantly, none that require a patch. I do not know if it is correct for your device. Please insert the device and run:```
lsusb
```Compare the usb.id, for example, 04E8:2018 to this list:```
 modinfo os/linux/rt3572sta.ko
filename:       os/linux/rt3572sta.ko
license:        GPL
version:        2.5.0.0
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     7A5279A18C5DA16F76E8411
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]04E8[/COLOR]p[COLOR="Red"]2018[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```As you can see, my example usb.id is listed. Is yours? If so, let's build rt3572sta.

---

### Post by streetwriter on 2012-01-14
Almost, but not quite. I get:
```
Bus 003 Device 002: ID 046d:c064 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 001 Device 005: ID 13fe:3123 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
(The other devices are my mouse and a USB drive.)

I should also mention that there isn't a Linux driver on the CD that comes with the adapter. I tried the one that's posted on the D-Link website, but it wouldn't compile without errors and the corrections noted elsewhere don't seem to have corresponding code in the include/os/rt_linux.h file.

*Edit:*
Looking at that output, I am a bit perplexed. I have three USB ports on my laptop, all of which are supposedly USB 2.0, but buses 2 and 3 are reporting 1.1 aren't they? Two of the ports are on the right side of the laptop and I have my Logitech USB mouse plugged into one, bus 3. The adapter is plugged into the other. There's also a port on the front, where I had my Kingston USB drive. (I've already tried the adapter in it and nothing happened.)

There's also evidently a conflict with bus 1, which is showing both the wireless adapter and USB drive. Or am I reading the output wrong?

---

### Post by chili555 on 2012-01-14
To be a bit too blunt, I am running low on ideas/mojo/talent. Did your device ever work with rt2800usb? We might try the newer firmware blob attached along with rt2800usb. If you'd like to try it and need guidance, post back.

---

### Post by streetwriter on 2012-01-14
I want you to know that I really, really appreciate all the time and effort you've put into trying to help me find a solution. From reading lots of threads on the forums, I know that you've often done the same for others. People helping people is just one of the many things that makes the Ubuntu community so special.

I've wondered about the usb driver and will try the one you sent. I'll let you know how it all turns out.

Cheers,

J

---

### Post by chili555 on 2012-01-14
> I've wondered about the usb driver and will try the one you sent. "Danger, Will Robinson!" What I attached is firmware, not a whole new driver. If you are in the slightest doubt about how to use it and how to back up your current firmware, please post back.

Thank you for your kind comments.

---

### Post by streetwriter on 2012-01-14
Yes, I am confused and, in this case, clueless. What do I do, and what might new/different firmware do?

---

### Post by chili555 on 2012-01-14
```
 modinfo rt2800usb
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
[COLOR="Red"]firmware:       rt2870.bin[/COLOR]
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     61CFBA7ACB6A210B48AA6CB

```Firmware is a little piece of code that the manufacturer (I think) writes to work with the driver and the hardware. The firmware that comes with Ubuntu 11.10 has a digital signature of:```
$ md5sum /lib/firmware/rt2870.bin 
[COLOR="Red"]36c944c3138125605d28c0a3a1338be9[/COLOR]  /lib/firmware/rt2870.bin
```The file I sent you is the file currently on Ralink's site and, presumably newer. Its signature is:```
$ md5sum rt2870.bin 
[COLOR="Red"]**2bb89af3a7d446deb4695c9a3daa7f9d**[/COLOR]  rt2870.bin
```...which is different. So let's back up the current firmware and install the attachment in its place:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.old
```Assuming you downloaded my attachment to your desktop, now do:```
cd Desktop
unzip RT2870_Firmware_V22.zip
cd RT2870_Firmware_V22
sudo mv rt2870.bin /lib/firmware
```Now we unload the lazy, no good rt3070sta and try rt2800usb:```
sudo modprobe -r rt3070sta
sudo modprobe rt2800usb
```Any improvements?

---

### Post by streetwriter on 2012-01-15
O M G. It worked. It worked! I'm getting 120 Mb/s. That's warp speed for me.

The only other thing I did apart from your instructions was to try the adapter in a different USB port. I'll experiment more with that later to see if it actual affects anything.

In the meantime, I suppose I need to go back to my blacklist.conf and remove rt2800usb and add rt3070sta in my custom settings -- correct?

But before that, a huge bear-hug thank you for all your help. I'm hoping that others who have a similar problem find this thread and that the solution works for them. I'll look through it all and see if I can summarise the steps.

You've also helped me learn a lot more about the inner workings of Ubuntu. 

Wow. Good, good karma, my friend. Thank you.

P.S. I had my laptop on a workbench next to a panel in my basement where I have a rack for my digital OTA and network connexions and hardware (modem, router, VoIP router, and switch), so I could plug in to ethernet (my desk is too far away for the longest network cable I could fabricate). As soon as I got a wireless connexion, I moved back to my desk (oh, how I'd missed a comfortable chair instead of a hard wooden bar stool). I noticed my speed dropped to 54 Mb/s. The adapter sits in a cradle with a 36" USB cable to my computer, and so I tried moving it around, including lifting it above my head, while monitoring my connexion information. At one point, the speed jumped to 240 Mb/s. In fact, it seems to be moving up and down a fair amount, depending on where it's positioned. A moment ago it was at 121. Then, at 108. I moved it a foot in another direction and it jumped to 216 Mb/s. Then, 270, 300. Suddenly, it dropped to 30 and I briefly lost the connexion. Now, it's at 45. No, 121. Crazy, but it works!

---

### Post by chili555 on 2012-01-15
> In the meantime, I suppose I need to go back to my blacklist.conf and remove rt2800usb and add rt3070sta in my custom settings -- correct?Correct. Or, if you are OCD like me, you could uninstall rt3070sta altogether. 

I am very glad it's working! I am glad not just for you, but because we have learned a new lesson: the right firmware can make the rt2800usb not only work but work well.

I am sure the searchers will find this and download the firmware.> A moment ago it was at 121. Then, at 108. I moved it a foot in another direction and it jumped to 216 Mb/s. Then, 270, 300. Suddenly, it dropped to 30 and I briefly lost the connexion. Now, it's at 45. No, 121. Crazy, but it works! You might experiment with the channel your router uses; I have the best luck with 1 and 11. I also found that my router connects to my laptop about three rooms away with better link quality with the router standing on its nose as attached.

Would you please use Thread Tools at the top and Mark Solved?

---

### Post by streetwriter on 2012-01-15
> **chili555 said:**
> Would you please use Thread Tools at the top and Mark Solved?

Happily, sir. Except, I'm not sure if I can do that. The option doesn't appear under Thread Tools. Perhaps I don't have "enough beans" for that privilege. 

Also, I have to remember how to uninstall the 3070!

---

### Post by chili555 on 2012-01-15
> Also, I have to remember how to uninstall the 3070!
```
cd Desktop/RT3070folder
```^^^ or wherever you extracted the folder when you downloaded it, if not desktop, and then:```
sudo su
make uninstall
exit
```Check:```
ls /lib/modules/`uname -r`/kernel/drivers/net/wireless/ | grep rt3070 
```If it comes up blank, it's gone.

Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by streetwriter on 2012-01-16
Jinxed by my inability to mark the issue SOLVED, my old problem has returned. I can't connect. I did, briefly, earlier today, but not as expected. When I checked the network connexion, evidently I was using "usb" for the driver. I manually inserted the rt2800usb using modprobe and that got me the connexion, but only at 54Mb/s (I am not sure if my work network is gigabyte). I ran "lsmod" and it showed the 3070 loaded along with the 2800, which surprised me because I had blacklisted it. Of course, I couldn't remove it because it was declared "in use."

I uninstalled the 3070 as instructed and it did not appear when I entered the call in the command line. I rebooted, but still couldn't connect by wireless.

Here's what I see now:
```
jeff@jeff-Aspire-5000:~$ lsmod | grep ^rt
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
```
That surprises me, too, because everything but the rt2800usb are supposed to be blacklisted.

What have I missed?

Meanwhile, I discovered this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070sta
```
That probably explains why the 3070 is loading even though it's not supposed to (although, I thought I'd uninstalled it -- weird).

---

### Post by chili555 on 2012-01-16
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt3070staIt would only explain a stumble or confusion. If the module has been uninstalled and is provably not there, it can't load. Please amend the file to remove it and reboot, then let us have your report.

---

### Post by streetwriter on 2012-01-16
Same result. No wireless connexion. It keeps trying to authenticate but can't (credentials are correct). Also, same report using lsmod. I don't understand why supposedly blacklisted items are loading.

---

### Post by chili555 on 2012-01-16
> Also, same report using lsmod. I don't understand why supposedly blacklisted items are loading.I don't understand. Aren't we expecting rt2800usb and its dependents to load? Isn't that what you showed me?> jeff@jeff-Aspire-5000:~$ lsmod | grep ^rt
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usbAre you saying that rt3070sta is loading nontheless?```
sudo updatedb
locate rt3070sta.ko
```

---

### Post by streetwriter on 2012-01-16
Yes, the rt2800usb and its dependents are loading:
```
jeff@jeff-Aspire-5000:~$ lsmod | grep ^rt
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
```
Even though everything but the rt2800usb are supposedly blacklisted. Should I remove those from my blacklist.conf file?

I ran the other line:
```
locate rt3070sta.ko
jeff@jeff-Aspire-5000:~$ locate rt3070sta.ko
/home/jeff/rt3070-2.3.0.2/os/linux/.rt3070sta.ko.cmd
/home/jeff/rt3070-2.3.0.2/os/linux/rt3070sta.ko
```
Those are from the unzipped folder from which I created the rt3070sta.

---

### Post by chili555 on 2012-01-16
> the rt2800usb and its dependents are loading:Good!> Should I remove those from my blacklist.conf file?If you'd like; it won't help or hurt either way, although it will be tidy, consistent and (my favorite!) OCD.> locate rt3070sta.ko
jeff@jeff-Aspire-5000:~$ locate rt3070sta.ko
/home/jeff/rt3070-2.3.0.2/os/linux/.rt3070sta.ko.cmd
/home/jeff/rt3070-2.3.0.2/os/linux/rt3070sta.koPerfect. It's nowhere in /lib/modules/etc. and therefor not loadable.

Let's see what syslog says:```
sudo cat /var/log/syslog | grep wlan | tail -n20
```

---

### Post by streetwriter on 2012-01-16
I've revised my blacklist.conf as follows:
```
# My custom additions, added Jan 15, 2012, to make DWA-140 work 
blacklist b43
blacklist ssb
# End my custom additions
```
In other words, I am no longer blacklisting anything related to the 2800. (Oh, crap, was the rt2870sta supposed to stay in it? I think so.)

*[snip]*

Incidentally, I didn't have any success connecting at home earlier today, either.

---

### Post by streetwriter on 2012-01-16
Suddenly, it works. Perhaps a few changes I made helped (including leaving the office?).

I edited the blacklist.conf file to include rt2870sta. When I returned home and booted up again, I was able to connect. Only the rt2800usb and its associated files load, according to lsmod. I got 300 Mb/s initially, but it's been wavering since, to as low as 27, even though I am sitting six feet from the router.

I am also getting intermittent connexions, which is annoying. 

The router is set to auto channel scan and defaulting to 6. I could try other settings.

---

### Post by chili555 on 2012-01-17
Woo hoo!!! Glad it's working.> The router is set to auto channel scan and defaulting to 6. I could try other settings.I suggest you do, especially try channels 1 and 11 in the router.

---

### Post by streetwriter on 2012-01-17
> **chili555 said:**
> I suggest you do, especially try channels 1 and 11 in the router.

I've tried various channel settings on my DIR-655. Channel 11 seemed to be the most stable but it also seemed to sit steadily at 65 Mb/s. Channel 1 is perhaps the worst, even if it offered more fluctuations in access speed. The "needle" swung a lot more, but I also had more annoying dropouts. I tried channel 6 and it moved a bit -- I just noticed it's at 130 -- but mainly it sat at 65 Mb/s. Yep, it's back at that speed. And I'm still getting dropouts. Web pages just don't load consistently. One second they load in a flash, the next Chrome is telling me "Oops!"

So, the story about connecting with a DWA-140 has two facets: one, getting the hardware to work; and, two, getting everything to work in a way that doesn't make you wonder why you bought it.

---

### Post by streetwriter on 2012-01-18
I don't often quote myself, but I can't resist:
> **streetwriter said:**
> So, the story about connecting with a DWA-140 has two facets: one, getting the hardware to work; and, two, getting everything to work in a way that doesn't make you wonder why you bought it.
Seriously, I am wondering about the value of this dongle. I've tried various channels on my router, with little improvement. Channel 3 seems to work well, but I still get dropouts. Even adjusting my router settings with the DWA-140 in use was painful, given that the interface would freeze while my wireless connexion vanished (all while I am still seeing impressive speeds on my connexion information window). In frustration, I switched back to my internal adapter and B43 driver and was content again with 54 Mb/s because at least it was stable and predictable.

I am not sitting that far from my router. It should be blasting me with wireless radiation goodness, regardless of which channel I select on it. If nothing else, it should be giving me G speed consistently. But it's not. There's something else about my combination of hardware -- Acer laptop, D-Link router and wireless adapter -- that must be the culprit. For the benefit of others as well as myself, figuring out what that is merits *not* marking this issue SOLVED, in my opinion.

---

### Post by ankah on 2012-01-18
with just my motorola L6 phone, i am connected  to the internet

---

### Post by chili555 on 2012-01-19
> Seriously, I am wondering about the value of this dongle. I've tried various channels on my router, with little improvement. Channel 3 seems to work well, but I still get dropouts.As I've said elsewhere, rt2x00 is hit or miss these days. I wish I could be more helpful.

---

### Post by streetwriter on 2012-01-19
Having scolded it, it is now working a bit more reliably with my router set to channel 3; however, based on past performance, I am still in "wait-and-see" mode.

---

