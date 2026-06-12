---
title: "Wireless problems in 10.04"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Erbun on 2010-05-16
Hey guys, I'm fairly new to Ubuntu.  I have used it off and on for the past year but just recently decided to make the jump and force myself to learn it.  So far so good, really good actually, minus a serious problem I'm having with my wireless.

I installed 10.04 just the other night and had 0 problems installing.  Got it up and running, booted up, and realized that I was not seeing any wireless networks.  I have had a similar problem in the past, and learned that my wireless card, Atheros AR5001, worked best with the ATH5K driver.  Atleast this seemed to be the case from previous experience.

I checked to verify that the kernel could in fact recognize the card, verified that the ATH5K driver was installed and used, (I have not tried installing any other wireless drivers), and rebooted the computer.  Once I logged in I saw the Wireless network that I was looking for and was able to associate with no problems.  I thought the problem was gone until the next day I just lost the conection and immediately was unable to see the network.  I also had a second laptop running windows so I am sure the network itself was still functioning fine.  After a while it just magically started working again until after a while it magically stopped working.  Now I seem to be stuck in this back and forth and would really like to have reliable wireless connection.

I have been googling and searching on here for most of the day with not much luck.  I have found many people with problems and resolutions involving situations where it just didn't work but have not had much luck in finding any problems that seem to rubberband such as mine.  Any help/ideas/directions to be pointed in would be much appreciated.  Thanks in advance!

---

### Post by NUboon2Age on 2010-05-16
please provide the network controller results from 

lshw -C network

---

### Post by Erbun on 2010-05-16
[I]  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:11:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:af:06:08
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=172.16.1.28 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:a000(size=256) memory:f8300000-f8300fff memory:84400000-8441ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:17:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:70:82:12
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8200000-f820ffff
[/I]

At the time of these results it is acting up.  I am unable to see any APs whether through the GUI or "iwlist wlan0 scan"  Thanks for the reply.  :)

---

### Post by NUboon2Age on 2010-05-16
Okay, also results of
```

ifconfig
iwconfig

```

---

### Post by Erbun on 2010-05-16
ifconfig:
[I]eth0      Link encap:Ethernet  HWaddr 00:1b:38:af:06:08  
          inet addr:172.16.1.28  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:feaf:608/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:108470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:125749024 (125.7 MB)  TX bytes:10523733 (10.5 MB)
          Interrupt:27 Base address:0xe000
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:70:82:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1724 (1.7 KB)  TX bytes:3833 (3.8 KB)
[/I]

iwconfig:

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[/I]


One more bit of info that may or may not help.. One time I was able to modprobe -r ath5k and then bring it back up and after rebooting it worked but couldn't duplicate it so I'm guessing it was a fluke.  But wanted to let you guys know just in case.  Thanks again!

---

### Post by NUboon2Age on 2010-05-16
Is this a proprietary driver? What happens when you run jockey (System->Adminstration->Hardware Drivers) ?

---

### Post by Erbun on 2010-05-16
Its  non proprietary.  When I open up hardware drivers it tells me there are no proprietary drivers in use on this system.

Several months ago when I last had Ubuntu on this laptop, 9.10 I believe it was, I used the ATH5K driver with no problems.  I had searched hoping that it was a common issue/bug with this new version but from my searches it appears to be only me.  Luckily my ethernet is working fine but I'm really hoping to get my wireless to a reliable state as while I won't put windows back on this machine just because of one problem, it's definetely a pain.  Thanks again for you input.

---

### Post by NUboon2Age on 2010-05-16
> **Erbun said:**
> 
One more bit of info that may or may not help.. One time I was able to modprobe -r ath5k and then bring it back up and after rebooting it worked but couldn't duplicate it so I'm guessing it was a fluke.  But wanted to let you guys know just in case.  Thanks again!

When you say you "couldn't duplicate it" do you mean that you were only able to get it running one time and then could not use that method to restart on next boot up, or do you mean that you were able to restart wireless and then it automatically started next time you rebooted, or do you mean something else?

---

### Post by Erbun on 2010-05-16
> **NUboon2Age said:**
> When you say you "couldn't duplicate it" do you mean that you were only able to get it running one time and then could not use that method to restart on next boot up, or do you mean that you were able to restart wireless and then it automatically started next time you rebooted, or do you mean something else?

One of the times that it wasn't working I did that and rebooted right after.  After the system booted up my wireless worked.  After a time the same problem occurred, kicking me off the wireless and I was unable to see any access points.  I then tried that method again, modprobe ath5k -r then modprobe ath5k then rebooted.  However it has not had the same effect so I am guessing that it was simply a fluke as there has been a couple of times that simply rebooting the system allows the wireless to work properly.  

After learning this I figured that I must have something interfering.  ie - Sometimes the correct driver gets loaded upon boot without any problems then others something is effecting it from properly loading all the way, or, as I have seen, an error was occurring somewhere that is causing the problem.  I checked the logs for today but saw nothing, but then again I have not been able to get it to work today.  I am currently getting ready to look at previous logs.  (I am assuming that log files from the past couple days are saved in the same area).

---

### Post by Erbun on 2010-05-16
Ok found a little bit of interesting info.  Going through the previous log file I did a search for anything involving "ath5k"  going through all the results most of them appear to be logs of the kernal finding the device and properly associating with a network.  Around the times that I remember have problems, and this is just guessing because I didn't at the time think to write down myself the exact time when a disconnect occured, I am seeing a strange line that I am unsure of.  The messages all pretty much read as this:

*May 15 06:48:00 erbun kernel: [115684.923602] ath5k phy0: unsupported jumbo*

I am still google'n for any info on this that I can find, but thought I would throw it up here just in case you have any insight on it.  Thanks.

---

### Post by NUboon2Age on 2010-05-16
(I posted this before reading your two previous notes so it may or may not be relevant).

Hmmm... I wonder if this is related to any of these bugs?  Even though some are older they may still be relevant or provide clues:

[https://bugs.launchpad.net/linux/+bug/356768](https://bugs.launchpad.net/linux/+bug/356768)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435452](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435452)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565367](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565367)
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/444885](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/444885) 
[https://bugs.launchpad.net/ubuntu/+bug/459625](https://bugs.launchpad.net/ubuntu/+bug/459625)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501961](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/501961)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/367543](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/367543)
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/444885](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/444885)
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/245990](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/245990)
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/294399](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/294399)
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/413781](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/413781)

---

### Post by NUboon2Age on 2010-05-16
Is it only encrypted networks that you're having trouble with (or maybe the problem starts with them and knocks the driver out?)  In your kernel log file do you get a "ath5k deauthenticated Reason 7"?  If so see [this]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/spotty-wireless-with-atheros-wireless-card-and-ath5k-driver-debian-squeeze-testing-779325/#post3812444").

---

### Post by Erbun on 2010-05-16
Nah actually the AP I have been having trouble with is open.  I also found in dmesg where im getting a noise floor calibration timeout and a gain calibration timeout.  I work with rf every day so this is finally getting into my language:)  Ive finally found some examples of people having similar problem but Im also gonna check out the links you posted.  This is definetely looking to be a conflict with drivers somewhere so Im gonna remove/blacklist ath5k and try a couple others and see where it gets me.  If I figure this thing out Ill post back here and let you know what came of it.  Thanks for your time and help man.. Greatly appreciate it.

---

### Post by NUboon2Age on 2010-05-16
Some [ath5k bugs related to "noise floor calibration"]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=ath5k%2C+noise+floor+calibration&search=Search+Bug+Reports&field.scope=all&field.scope.target="):

Thank you in advance for posting your findings.  Also please, if you find a bug that matches, please confirm it, affirm that it effects you too, subscribe yourself to it and comment on it.  This will help to get the developer's attention and hopefully get some action moving on it.  If you don't find a bug that matches, please file one.:P

---

### Post by JohnDoe365 on 2010-05-19
Once again, you're not alone. I only wonder by the mass of very similar problems that there is no statement yet, that WiFi in 10.04 with current kernel / WiFi subsystem has issues.

Please try the following:

disable WiFi
enable WiFi and wait for re-association with AP

Is speed back to normal? This helped some people (me too), but is only a temporal fix, speed will suddenly drop back to unacceptably slow.

CF: [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and consider leaving a bug report @ [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)

I couldn't find any more apporpriate launchpad bug report yet ...

---

### Post by phillytomcat on 2010-06-12
> **Erbun said:**
> Its  non proprietary.  When I open up hardware drivers it tells me there are no proprietary drivers in use on this system.

Several months ago when I last had Ubuntu on this laptop, 9.10 I believe it was, I used the ATH5K driver with no problems.  I had searched hoping that it was a common issue/bug with this new version but from my searches it appears to be only me.  Luckily my ethernet is working fine but I'm really hoping to get my wireless to a reliable state as while I won't put windows back on this machine just because of one problem, it's definetely a pain.  Thanks again for you input. 
I have hp pavillion dv6000 with broadcom wireless. I installed 10.04 and got the "no proprietary drivers in use" dialog box. 
 I went into synaptic package manager and typed broadcom. Sure enough the linux for broadcom drivers were there. Just no internet. I am typing this from windows vista sp2.

---

### Post by ugm6hr on 2010-06-12
> **phillytomcat said:**
> I have hp pavillion dv6000 with broadcom wireless. I installed 10.04 and got the "no proprietary drivers in use" dialog box. 
 I went into synaptic package manager and typed broadcom. Sure enough the linux for broadcom drivers were there. Just no internet. I am typing this from windows vista sp2.

If you are asking for help, please start your own thread, including details from the Wifi help link below.

This thread is for ath5k users.

---

### Post by glitchster on 2010-06-12
> **NUboon2Age said:**
> please provide the network controller results from 

lshw -C network
I posted a few days ago on different thread with attachments of outputs from terminal.
Can someone PLEASE give me some advice at the thread I posted?

---

