---
title: "Dell inspiron 6400: no wifi after upgrade!"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by danielgrosvenor on 2011-05-09
Hi everyone, I'm really hoping somebody can help me out as I'm posting this via my phone.

I'm on a Dell Inspiron 6400 which had been running Ubuntu 10.10 (32 bit) perfectly.Today I upgraded it to Natty and the wifi now refuses to work.

Details: While no Additional Drivers were needed on 10.10, upon installing Natty it prompted me to install "Broadcom STA proprietary wireless driver". Now when it's active I don't even have the option 'Enable Wireless' (only Enable Networking). If I disable STA the Enable Wireless option comes back, yet I can't actually search for wifi networks or connect to my saved one. The keyboard key to enable/disable wireless also does nothing.

I can take this laptop to somewhere with an ethernet connection for an afternoon if need be, but am currently stumped as to what to do. Obviously I know this machine can handle Wifi under Ubuntu - it's definitely a Natty problem.

Any advice would be greatly appreciated.

---

### Post by garvinrick4 on 2011-05-09
You are showing us the intel 5100 card which uses the iwlagn driver which is in the kernel.
Can you run this in terminal:
```
sudo lshw -C network
```

---

### Post by danielgrosvenor on 2011-05-10
> **garvinrick4 said:**
> You are showing us the intel 5100 card which uses the iwlagn driver which is in the kernel.
Can you run this in terminal:
```
sudo lshw -C network
```

I've taken the laptop home for the evening so I can at least plug it into ethernet while I get this WiFi problem fixed.

Here are the results of that Terminal command:

```
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a4:da:aa
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.15 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff

```

---

### Post by garvinrick4 on 2011-05-10
Here is to make sure you have right driver installed: Couple of threads on your card:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)
[http://ubuntuforums.org/showthread.php?t=1751459](http://ubuntuforums.org/showthread.php?t=1751459)
# If you do:
Run and make sure all is at true:
```
gedit /var/lib/NetworkManager/NetworkManager.state
```If not:
                          ```
sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start 
```If still not going post:
```
iwconfig

```

---

### Post by Onesimus on 2011-05-10
I too have a Dell Inspiron 6400, but unlike yourself I have no problems with the Wifi.  I wonder if you get the wifi option if you select Fn+F2 that may turn the Wifi on.

---

### Post by nachete33 on 2011-05-10
I had the same problem but that solved it for me:

 - Disable the non supported driver.
 - Go to Synaptic and install b43-fwcutter and firmware-b43-installer.

That's all.

---

### Post by josephmills on 2011-05-10
if you think that you might need the b43 fwcutter or the b43sta please take a look at post number 44 thanks [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)   but in this case I could see the b44 and the b43 colliding

---

### Post by lavallie on 2012-10-25
> **nachete33 said:**
> I had the same problem but that solved it for me:

 - Disable the non supported driver.
 - Go to Synaptic and install b43-fwcutter and firmware-b43-installer.

That's all.

Sounds good, but I have absolutely no idea how to do these?  Can you explain how pls.  Tks,

Having problems with the Dell insppiron 6400 after upgrade also.....

---

### Post by ahallubuntu on 2012-10-25
Not every 6400 has a Broadcom wireless card.  Dell shipped them with both Intel and Broadcom wireless cards.  (I have an E1505 which is the same hardware; my friend has a 6400 and I upgraded his Broadcom card to an Intel card.)  The Broadcom solution mentioned above will not work for a laptop with an Intel card.

If you do

```
sudo lshw -C network
```

and find out you indeed have the Broadcom card not the Intel card, you can track down instructions to figure out how to install b43-fwcutter and firmware-b43-installer.  (Synaptic Package Manager is not installed by default in Ubuntu 12.04 anymore.)  Just search this forum for "b43-fwcutter" and/or "6400 broadcom wireless" and you'll surely find detailed instructions for installing it.  Having a wired network connection temporarily may make things a lot easier, however.

---

### Post by wildmanne39 on 2012-10-25
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

