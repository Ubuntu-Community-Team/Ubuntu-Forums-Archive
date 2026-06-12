---
title: "Wireless Network Connection - Annoying Problems"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by amjjawad on 2010-12-12
Hello everyone,

I have some annoying problems with my main PC. One of these problems I've been suffering from since I have installed Ubuntu 10.04 (*Desktop 32-bit*) is:

**Connecting to Internet using my Wireless Network is a headache.**

How is that? I'll explain.

[B][U]Case1
[/U][/B]_Problem_: Whenever I choose "Hibernate" sometimes and then turn my PC on, I lose the Wireless Connection.

_Solution_: Restart/Reboot my PC. Sometimes, I have to restart my Router and sometimes I have to reboot my PC more than once. Usually, once do the job.


[B][U]Case2
[/U][/B]_Problem_: Whenever I disconnect my Wireless Connection (regardless why I'm disconnecting it), I can not re-connect at all.

_Solution_: Restart/Reboot my PC. Sometimes, I have to restart my  Router and sometimes I have to reboot my PC more than once. Usually,  once do the job.

[U][B]Case3
[/B]Problem[/U]: Whenever I restart my Router, I can't connect to it through the Wireless Connection.

_Solution_: Restart/Reboot my PC either once or more than one time.


Above are the main 3 scenarios I do have at the moment and I've chosen to live with it all that time but enough is enough.

**_Additional info that might help:_**
Network Card is: D-Link Airplus G Adapter
ADSL Router is: CableWireless

I'm sure there's another way much easier and better than keep restarting (as this is not Windows) but if I know it, I would never post here :)

Your help is much appreciated ;)

---

### Post by amjjawad on 2010-12-12
I'm patient ;)

Edit:
Can someone who is online on this forum more than 12hours every day to be patient for one week and not to receive one single reply? I don't think anyone could be patient more than me :)

---

### Post by amjjawad on 2010-12-30
> **amjjawad said:**
> Hello everyone,

I have some annoying problems with my main PC. One of these problems I've been suffering from since I have installed Ubuntu 10.04 (*Desktop 32-bit*) is:

**Connecting to Internet using my Wireless Network is a headache.**

How is that? I'll explain.

[B][U]Case1
[/U][/B]_Problem_: Whenever I choose "Hibernate" sometimes and then turn my PC on, I lose the Wireless Connection.

_Solution_: Restart/Reboot my PC. Sometimes, I have to restart my Router and sometimes I have to reboot my PC more than once. Usually, once do the job.


[B][U]Case2
[/U][/B]_Problem_: Whenever I disconnect my Wireless Connection (regardless why I'm disconnecting it), I can not re-connect at all.

_Solution_: Restart/Reboot my PC. Sometimes, I have to restart my  Router and sometimes I have to reboot my PC more than once. Usually,  once do the job.

[U][B]Case3
[/B]Problem[/U]: Whenever I restart my Router, I can't connect to it through the Wireless Connection.

_Solution_: Restart/Reboot my PC either once or more than one time.


Above are the main 3 scenarios I do have at the moment and I've chosen to live with it all that time but enough is enough.

**_Additional info that might help:_**
Network Card is: D-Link Airplus G Adapter
ADSL Router is: CableWireless

I'm sure there's another way much easier and better than keep restarting (as this is not Windows) but if I know it, I would never post here :)

Your help is much appreciated ;)

Solved after formatting the HDD and install Ubuntu 10.04 again.

I have to do it manually (Enable Networking). At least, I don't have to "reboot/restart".
[B][COLOR=Red]

[COLOR=Black]Thanks a lot guys for [/COLOR][/COLOR][COLOR=Black]all[/COLOR][/B][COLOR=Black]** your replies, so nice of you** :D[/COLOR]

---

### Post by amjjawad on 2011-06-26
Looks like I have to live with this problem forever with each and every release of Ubuntu, sigh!

Long story short. I have NEW Wireless Modem Router. I have NEW Wireless USB Adapter. I have formatted and installed Ubuntu 11.04.
Despite all that, NOW, the Wireless Connection keeps disconnecting every now and then. I have NO IDEA what's going on?

With the previous mentioned problems above, the disconnecting was somehow happening when "I" do something like "Hibernate". Now, it's happening all from itself.

Is there a solution for this problem? any advice?

I don't have money to buy a range expander so I'm using this PC as a server or somehow to connect my other PC through that one. It's a bit of a complicated story. 

I appreciate if someone could help.

Thanks a lot :)

---

### Post by chili555 on 2011-06-26
Sometimes, this helps:```
sudo gedit /etc/pm/config.d/config
```Add a single line:```
SUSPEND_MODULES="your_driver"
```Of cource, substitute your wireless driver. It should be listed in:```
sudo lshw -C network
```Here is a sample from my machine:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       logical name: wlan0
       version: 02
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fffSo, in my example, I'd put iwl3945 in place.

Be sure to proofread carefully, save and close gedit.

---

### Post by amjjawad on 2011-06-26
> **chili555 said:**
> Sometimes, this helps:```
sudo gedit /etc/pm/config.d/config
```Add a single line:```
SUSPEND_MODULES="your_driver"
```Of cource, substitute your wireless driver. It should be listed in:```
sudo lshw -C network
```Here is a sample from my machine:So, in my example, I'd put iwl3945 in place.

Be sure to proofread carefully, save and close gedit.

Hi Chili555,

Thanks a lot for your reply.

There was no such file in **/etc/pm/config.d**  so I created it and inserted this line:

```
SUSPEND_MODULES="rt2800usb"
```

I'll keep watching and will let you know in case it did not work.

---

### Post by chili555 on 2011-06-26
I'm not a fan of rt2800usb. Other than Suspend, does it work well for you?

---

### Post by amjjawad on 2011-06-26
> **chili555 said:**
> I'm not a fan of rt2800usb. Other than Suspend, does it work well for you?

Well, I'm downstairs on another machine. I'll check it when I'll go up and will let you know.

Will "Suspend" keep the connection alive as long as possible?

Thank you again :)

---

### Post by chili555 on 2011-06-26
I believe Suspend will end the connection. If the file we wrote does it's job, the driver will reload when the computer comes out of Suspend, Network Manager will wake up and the connection will be re-established immediately with no human intervention. It certainly does on my system.

I've had quite a few cases where users report it works perfectly and a few that report it does nothing. All we can do is try. No pain, no gain, etc.

---

### Post by amjjawad on 2011-06-26
> **chili555 said:**
> I believe Suspend will end the connection. If the file we wrote does it's job, the driver will reload when the computer comes out of Suspend, Network Manager will wake up and the connection will be re-established immediately with no human intervention. It certainly does on my system.

I've had quite a few cases where users report it works perfectly and a few that report it does nothing. All we can do is try. No pain, no gain, etc.

That's great but just to make sure we are both on the same page, my recent problem is explained in [**post#4**]("http://ubuntuforums.org/showpost.php?p=10983650&postcount=4")

I'll keep an eye and I really hope this will fix it once and for all.

Yes, definitely there is no harm to try :)

I think you know a lot about these issues.

---

### Post by amjjawad on 2011-06-27
It just happened again and I couldn't reconnect :(

Had to log off, plugged the USB Adapter to another USB port (I do that usually when this problem occur) and logged in.

I'm connected now but God knows for how long :/

---

### Post by chili555 on 2011-06-27
Ahem...I'm not a fan of rt2800usb. Other than Suspend, does it work well for you? Evidently not. Mind if I have a peek at:```
lsusb
lsmod | grep rt2
```Thanks.

---

### Post by amjjawad on 2011-06-27
> **chili555 said:**
> Ahem...I'm not a fan of rt2800usb. Other than Suspend, does it work well for you? Evidently not. Mind if I have a peek at:```
lsusb
lsmod | grep rt2
```Thanks.

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 7392:7711 Edimax Technology Co., Ltd EW-7711UTn nLite Wireless Adapter [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


```
rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  5 rt2800usb,rt2800lib,rt61pci,rt2x00usb,rt2x00pci
mac80211              257001  4 rt2800lib,rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

```

---

### Post by chili555 on 2011-06-27
> rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  5 rt2800usb,rt2800lib,rt61pci,rt2x00usb,rt2x00pci
mac80211              257001  4 rt2800lib,rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211Man! That is a great big pile of drivers all fighting amongst themselves for control of one littel wireless device! Let's kick one out and see if things stabilize. Remove the device. Open a terminal and do:```
sudo su
gedit /etc/pm/config.d/config
```Change the module from rt2800usb to rt2870sta. Proofread, save and close gedit. Now back to the open terminal:```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800usb
exit
```Reinsert the device and let us hear your report.

---

### Post by amjjawad on 2011-06-27
> **chili555 said:**
> Man! That is a great big pile of drivers all fighting amongst themselves for control of one littel wireless device! Let's kick one out and see if things stabilize. Remove the device. Open a terminal and do:```
sudo su
gedit /etc/pm/config.d/config
```Change the module from rt2800usb to rt2870sta. Proofread, save and close gedit. Now back to the open terminal:```
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800usb
exit
```Reinsert the device and let us hear your report.

Oh boy, it's MUCH better when Firefox tries to load any page ... it's much faster :D
Before, I had to wait for a long time until a simple page finishes loading :(
[B]However, this USB Adapter's MAX Speed is 150 Mb/s but for some weird reason, the speed is stuck on 54 Mb/s only!!!
[/B] 
Is this has anything to do with what we have done?

By the way, once I connected/inserted the USB Adapter, it connected itself without any action from my side.

I think we're in the right path now but I do need to keep an eye on this :)

THANK YOU :)

---

### Post by amjjawad on 2011-06-27
Are we good?

Edit:

```

*-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan1
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.2.51 multicast=yes wireless=Ralink STA

```I forgot to add that I have another PCI Wireless Adapter except the antenna is broken so I'm not using it. Shall I remove it? I don't think it interferes but your suggestion is highly appreciated :)

```

*-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 00
       serial: 00:15:e9:47:1c:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fddf0000-fddf7fff

```

---

### Post by chili555 on 2011-06-27
> **amjjawad said:**
> Okay, the driver is: 8139too
Speed is: 100 Mb/s

Are we good?

Edit:

```

*-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan1
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.2.51 multicast=yes wireless=Ralink STA

```

I forgot to add that I have another PCI Wireless Adapter except the antenna is broken so I'm not using it. Shall I remove it? I don't think it interferes but your suggestion is highly appreciated :)

```

*-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 00
       serial: 00:15:e9:47:1c:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fddf0000-fddf7fff

```I suggest blacklisting the driver; that will keep the PCI device quiet. If you wish to do so:```
sudo su
echo "blacklist rt61pci" >> /etc/modprobe.d/blacklist.conf
exit
```On reboot, the PCI device will be out of the way.> However, this USB Adapter's MAX Speed is 150 Mb/s but for some weird reason, the speed is stuck on 54 Mb/s only!!!There are lots of threads here about N speeds on rt2870sta. No one seems to have gotten it done yet; I guess we have to wait for the next kernel version. Sorry.

---

### Post by amjjawad on 2011-06-27
> **chili555 said:**
> I suggest blacklisting the driver; that will keep the PCI device quiet. If you wish to do so:```
sudo su
echo "blacklist rt61pci" >> /etc/modprobe.d/blacklist.conf
exit
```On reboot, the PCI device will be out of the way.


```
*-network:1 UNCLAIMED
       description: Network controller
       product: RT2561/RT61 rev B 802.11g
       vendor: Ralink corp.
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fddf0000-fddf7fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.2.51 multicast=yes wireless=Ralink STA

```

I think we're done here, right?

> There are lots of threads here about N speeds on rt2870sta. No one seems to have gotten it done yet; I guess we have to wait for the next kernel version. Sorry.
Really? I have no experience with this. This is my first attempt to fix such a thing.
So, are you saying I'm not the only one? is it because of the driver we used? or it has to do with something else?
I'm sorry if I'm asking too much but really I have never done this before!

Thanks a lot for your continuous support :)

---

### Post by chili555 on 2011-06-27
> So, are you saying I'm not the only one? is it because of the driver we used?You are not the only one. I don't know for sure if it's the driver or the combination of the driver, Network Manager and wpa_supplicant. All I know is that a lot of guys have fiddled with this and not been successful yet. I haven't studied it thoroughly because I don't have such a device and my specialty is more getting users from 'my wireless doesn't work' to 'my wireless works. you're a genie.'

My sister calls me 'Atmel genie' based on a complicated case I solved here more or less accidentally!

If I had one, I might download the latest RT2870 from Ralink and poke about in the code and see what I could see. I'd probably also download the compat-wireless package and do the same. I'm not much of a code hacker, so I'd guess if it was apparent, someone a lot more knowledgable than me would have cracked the case before now.> I think we're done here, right?I believe we are.

Have fun!

---

### Post by amjjawad on 2011-06-27
> **chili555 said:**
> You are not the only one. I don't know for sure if it's the driver or the combination of the driver, Network Manager and wpa_supplicant. 


I still have so much to learn about Linux but I don't know why I have that feeling which is telling me that Network Manager is not good enough to handle such job. I might be wrong.


> and my specialty is more getting users from 'my wireless doesn't work' to 'my wireless works. you're a genie.'
Oh yes, you're :D

> If I had one, I might download the latest **RT2870** from Ralink and poke about in the code and see what I could see. 
Sorry again but why RT2870 specifically? 
I'm on it now (_[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)_[]("http://www.ralinktech.com/product.php?s=33")) but I just want to know how did you find out about the model or number?

> I'd probably also download the compat-wireless package and do the same. I'm not much of a code hacker, so I'd guess if it was apparent, someone a lot more knowledgable than me would have cracked the case before now.
That's why beyond my knowledge as of now :)

> I believe we are.

Have fun!
THANK YOU SO MUCH :)

---

### Post by chili555 on 2011-06-27
> Sorry again but why RT2870 specifically?
I'm on it now ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)) but I just want to know how did you find out about the model or number?
That's the driver you are working with that you'd like to do N speeds, right? The Ralink site clearly shows RT2870USB(RT2870/RT2770). I only know that's the driver for your device because it was loaded, along with rt2800usb. When we removed rt2800usb, you said:> Oh boy, it's MUCH better when Firefox tries to load any page ... it's much fasterSo, evidently rt2870sta is correct for your device. There are other, more tedious ways to match up the driver with the hardware. I try, when I can, to skip a few steps since users usually want to understandably get their wireless going right now.

---

### Post by amjjawad on 2011-07-02
> **chili555 said:**
> That's the driver you are working with that you'd like to do N speeds, right? The Ralink site clearly shows RT2870USB(RT2870/RT2770). I only know that's the driver for your device because it was loaded, along with rt2800usb. When we removed rt2800usb, you said:So, evidently rt2870sta is correct for your device. There are other, more tedious ways to match up the driver with the hardware. I try, when I can, to skip a few steps since users usually want to understandably get their wireless going right now.

Thanks yet again for your help :)

I don't mind the long details/steps as long as I'll going to learn something from that :)

I just followed the same steps on Lubuntu 11.04 (I have both Ubuntu 11.04 and Lubuntu 11.04 installed on the same PC). I forgot to remove the device while I was removing the drivers but that wasn't a problem. I unplugged it, logged of, plug it again and logged in and it's working now.

Now, let's say I want to revert to the old driver, what shall I do?
Just trying to learn how to :)

Thanks a lot!

---

### Post by chili555 on 2011-07-02
> **amjjawad said:**
> 
Now, let's say I want to revert to the old driver, what shall I do?
Just trying to learn how to :)

Thanks a lot!Remember we blacklisted rt61pci. If you wanted to re-activate it, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change the line:```
blacklist rt61pci
```To this:```
#blacklist removed to activate pci card again
#blacklist rt61pci
```Proofread, save and close gedit. Then do:```
sudo modprobe rt61pci
```You should be all set.

---

### Post by amjjawad on 2011-07-02
> **chili555 said:**
> Remember we blacklisted rt61pci. If you wanted to re-activate it, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change the line:```
blacklist rt61pci
```To this:```
#blacklist removed to activate pci card again
#blacklist rt61pci
```Proofread, save and close gedit. Then do:```
sudo modprobe rt61pci
```You should be all set.

Sorry but that was my other old PCI Wireless Adapter.
The one which was causing the problem is: rt2800usb

Shall I follow the same above steps and use "rt2800usb" or there are another steps?

Thanks :)

---

### Post by chili555 on 2011-07-02
> Shall I follow the same above steps and use "rt2800usb" or there are another steps?You absolutely should! And when you find rt2800usb completely unsatisfactory and it won't connect, post back so the world will learn from your heartache.

Seriously, I have read that rt2800usb has been greatly improved and we'd all like to hear if it works as expected. Thanks.

---

### Post by amjjawad on 2011-07-02
> **chili555 said:**
> You absolutely should! And when you find rt2800usb completely unsatisfactory and it won't connect, post back so the world will learn from your heartache.

Seriously, I have read that rt2800usb has been greatly improved and we'd all like to hear if it works as expected. Thanks.

Great :)
Then the previous steps will work to unblock both PCI Adapter's Driver and rt2800usb's Drivers. Understood :)

Well, as you know, it was giving me hard time indeed. I'll not go back to rt2800usb unless there is a huge improvements :)

Thanks a lot, Genie :D

Edit:
Does it mean I had an old version of rt2800usb and I just have to update that?

---

### Post by chili555 on 2011-07-02
> Does it mean I had an old version of rt2800usb and I just have to update that?These drivers are a part of the kernel. When a new kernel or linux-image is installed by Update Manager, a later driver will be included. You could also install the compat-wireless package by compiling from source, by why torture yourself when your wireless is now:> Oh boy, it's MUCH better when Firefox tries to load any page ... it's much faster I suppose you could try compat-wireless to get N speeds, but I haven't read a post so far that reports that's the answer.

---

### Post by amjjawad on 2011-07-02
> **chili555 said:**
> These drivers are a part of the kernel. When a new kernel or linux-image is installed by Update Manager, a later driver will be included. 

Understood :)

> You could also install the compat-wireless package by compiling from source, by why torture yourself when your wireless is now:

I suppose you could try compat-wireless to get N speeds, but I haven't read a post so far that reports that's the answer.

Need to learn how to compile. I've been away from my PCs and everything for few months due to health problems. I'm trying to take it easy and also trying to be active here to refresh my memory.

Will stick with what we have done so far and will report back in case something new will pop up :)

Many thanks my genie friend :)

Will mark this thread as SOLVED as of now.

---

### Post by amjjawad on 2011-08-12
Hi Chili555,

Just a quick Question.
I formatted my PC and installed Lubuntu 11.04. I followed the same steps and everything is ok. I even removed the PCI adapter so now I have only one LAN and one USB Wireless Adapter:

```

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:16:76:85:ad:92
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:de00(size=256) memory:fddff000-fddff0ff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:1f:1f:a8:e5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.2.103 multicast=yes wireless=Ralink STA

```

So, I didn't have to blacklist anything.

Now, I have a weird issue.
My LAN adapter has MAC address and everything but for some reason, I can't connect my Laptop in the other room to this PC. I used to do that in the past with Ubuntu 11.04 with the same setup we did together.

No matter what I do, I can't get the LAN Connection to work.
From Edit Connection > Wired > IPv4 Settings > Method > Shared to other Computers **OR** Automatic (DHCP) in both cases, nothing happened.


Once I change the Wireless Connection to "Shared to other Computers", it stops and can't reconnect again unless I changed it back to Automatic (DHCP). But that for the Wireless Connection.

I know my connection is so funny and weird but I don't have another choice. Last time I bought a range extender (I told you about it), it didn't work.
I have to live with this kind of weird connection because ... it's a long story.

Any idea what exactly shall I do to fix that?

---

### Post by chili555 on 2011-08-12
When you click the Network Manager icon and select Create New Wireless Network and fill in the details there, are you able to connect? Be sure to make sure the Mode is Ad Hoc. Please see attached.

---

### Post by amjjawad on 2011-08-12
> **chili555 said:**
> When you click the Network Manager icon and select Create New Wireless Network and fill in the details there, are you able to connect? Be sure to make sure the Mode is Ad Hoc. Please see attached.

I don't have problem with the Wireless Network, my problem is with the Wired Network.

The other machine (Laptop) is connection to this PC via LAN cable. I can see the lights ON but there is NO Internet.

Ad-Hoc? but before, it wasn't Ad-Hoc and it was working just perfect!

P.S.
I'm Online now from my PC. I can't be Online from my Laptop which is connected via LAN with this PC.
This PC is connected to the internet via Wireless USB Adapter.

---

### Post by amjjawad on 2011-08-12
I'm attaching these 3 screen shots:

I tried the Ad-Hoc but it didn't work.
As I posted earlier, I never had to use "Ad-Hoc" before. It was working, I just changed the OS (Ubuntu 11.04 is SO SLOW on 512MB RAM).

---

### Post by chili555 on 2011-08-12
I'm a bit confused here. The computer you are trying to connect is *GETTING* the internet via ethernet cable from another computer? Or is it *GIVING* the internet to another computer via ethernet cable?

I am no expert on connection sharing, but I believe the computer giving the internet needs to be the one set up as Shared to other Computers.

The computer getting the internet needs nothing in particular, I'd think you can set it up for DHCP and get an address from the other computer. If you connect but can't access the internet, you may need a DNS nameserver listing in /etc/resolv.conf.

---

### Post by amjjawad on 2011-08-12
> **chili555 said:**
> I'm a bit confused here. The computer you are trying to connect is *GETTING* the internet via ethernet cable from another computer? Or is it *GIVING* the internet to another computer via ethernet cable?


I'll explain but don't laugh at me :P

[U]There you go:
[/U]The router is in the ground floor.
My PC and My Laptop is on the Upper floor.

My PC is connected to the router (and to the internet) via Wireless USB Adapter.

My Laptop is connected to the internet via LAN Cable.

The LAN cable is from my PC to my Laptop.

My PC is giving the internet to my laptop.

My Laptop is getting the internet from my PC.

Now, before, the above scenario was working perfectly. However, Ubuntu 11.04 is so slow on my PC so I decided to go light and installed Lubuntu 11.04.

Problem is, The Laptop is no longer able to be ONLINE because it can NOT get the internet from my PC as it used to before.

Is it ok now?
I know it's the most stupid connection I have ever made but I don't have another choice at the moment. It's long story and perhaps I'll explain that later.

> I am no expert on connection sharing, but I believe the computer giving the internet needs to be the one set up as Shared to other Computers.
Already done as the previous screenshots. 

> The computer getting the internet needs nothing in particular, I'd think you can set it up for DHCP and get an address from the other computer. If you connect but can't access the internet, you may need a DNS nameserver listing in /etc/resolv.conf.

The Laptop has Win7. The silly seller asked me NOT to format it because I'll lose the warranty and I can't even install another OS for the same reason. SO LAME :/
I'm waiting until I can go Linux on that Laptop.

Yes, I don't have to do anything on the Laptop but to connect the LAN Cable.

---

### Post by chili555 on 2011-08-13
I don't think your setup is crazy or lame. Actually, I have seen a lot worse! I understand that people have complicated houses, internet situations and even limited budgets, me included. Not everyone can march down to the store and order a more powerful wireless router and two or three wireless cards, me included. Please don't apologize. 

I am quite sure you can easily do what you are trying to do. The only problem is that I know next to nothing about internet connection sharing. I suggest you start a new thread with internet connection sharing in the title. Tell about your setup in detail just as above. I'm sure a better guru than me will have you going quickly. 

I suspect that Network Manager seems to be set up for sharing to be wireless. Your sharing is wired.

I wish I could be of more help.

---

### Post by amjjawad on 2011-08-13
> **chili555 said:**
> I don't think your setup is crazy or lame. Actually, I have seen a lot worse! I understand that people have complicated houses, internet situations and even limited budgets, me included. Not everyone can march down to the store and order a more powerful wireless router and two or three wireless cards, me included. Please don't apologize. 


I used to work and was able to buy whatever I need but I'm jobless for 3 years now and I'm having hard time over here. Thank God I'm still breathing :)

> I am quite sure you can easily do what you are trying to do. Yes, no need to a new thread. I managed to fix it with ONE command only and a restart :)

```
sudo apt-get install dnsmasq

```Problem Fixed.

Thank you so much and don't worry about it :)

I just don't get it. Lubuntu and Ubuntu must be using the same base so why some packages are not included? I have Ubuntu 11.04 and Lubuntu 11.04 installed on VirtualBox on my Laptop. I compared between them and I found that Ubuntu has "dnsmasq" while Lubuntu does not. LAME!
I knew there was something missing, a package or a step to do. I wasn't sure what is missing. I did quick Google Search and I found this:

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

Skimmed through the text and I found:

**ipmasq **and **dnsmasq**

Only dnsmasq was required :)


I do remember that I faced exactly the same issue with Lubuntu 10.04 but at that time, formatting and installing another OS was my easy solution. Such solutions are no longer exist in my dictionary :)

I'm posting this from my Laptop on my room :D

---

### Post by chili555 on 2011-08-13
> so I decided to go light and installed Lubuntu 11.04.
It seems that, in order to lighten it up, they omitted dnsmasq and probably a lot of other things. I'm glad you got it working and I hope you enjoy Ubuntu.

I also hope and pray that the economy and employment will be kinder to you in the near future. 

Thanks for the explanation. You will have helped some searchers, too.

---

