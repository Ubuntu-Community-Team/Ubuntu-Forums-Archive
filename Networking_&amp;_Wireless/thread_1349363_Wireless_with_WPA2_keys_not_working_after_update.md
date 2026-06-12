---
title: "Wireless with WPA2 keys not working after update"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by ducu on 2009-12-08
Hello, 

I have a Broadcom BCM4309 wireless card and it's working like a charm using the following kernel: 
 2.6.31-14-generic #48-Ubuntu SMP

The problem is that after an update when booting other kernels, i cannot connect anymore to WPA2 enabled wireless networks (i can however connect to free wereless access points without issues).

From what i have noticed, when everything is working fine, i can see in System->Administration->Hardware Drivers that Broadcom B43 Wireless Driver is loaded and working, however after booting a more recent kernel, this entry is not present anymore.

I would like to have Wireless working with more recent kernels also, it is not that comfortable to edit grub settings after each update to boot the above kernel :(

Any help is appreciated :)
Thanks.

L.E. forgot to mention that i am running Ubuntu 9.10 on a Dell X300 laptop

---

### Post by HuTPaT on 2009-12-08
Nearly same issue here.
After last updates i can`t connect to any wireless network.

My wireless card is Broadcom Corporation BCM4311 on DELL Inspiron 1520
Linux 2.6.31-16-generic #52-Ubuntu SMP

Does anyone know something about this and how to debug the problem?
Thaks.

---

### Post by Smika on 2009-12-08
Same problem here. I have an acer aspire 3630. I can;t remember my wireless ethernet card. I can login on a non-secure network, but I can't on a secure network with Dynamic WEP, Tunneled TLS and PAP.

---

### Post by mikey.duhhh on 2009-12-08
I just posted a new thread on this..  But here it is again:

 Seahorse, Ubuntu 9.10 wireless not connecting to WPA
A few days ago I installed Ubuntu 9.10 on a friend's laptop. He has a 4306 Broadcom wireless card. And having had a laptop with a bcm4312 card I knew there would be an issue with the wireless.

So, I searched the forums and found the b43legacy/b43 tar, downloaded it, placed the unzipped folders in /lib/firmware and rebooted. Well, at least it was trying to connect now. But Seahorse wanted a password for me to use the wireless, so I gave it one. Then, of course so did the WPA wireless spot I was in. Still no connect.

So, I found a lan, plugged the laptop in and downloaded all 147 updates for 9.10. Rebooted, Wow! It connected no problem to the open wireless network available to me. I called my friend and told him it was now working. Then I drove all the way across the metro area back to the coffee shop and tried to boot up. First Seahorse wanted a password again, then the WPA encrypted hot spot wanted it's password, too. Trying, trying, trying.... Up comes the box for the password again, trying, trying, trying.... Password box reappears. Etc., etc., and so on. I won't connect to a WPA connect.


First, off. I have never seen this behavior from Seahorse before. Before 9.10 it never bothered me for any sort of prompt unless I PGP'd email. So what is going on with Seahorse demanding a password to use wireless? Anyone? Can I just remove Seahorse without destroying access to Ubuntu? You know, sudo apt-get purge seahorse?

Could that fix the wireless connect WPA problem? Or do I need to go back to 9.04?
mikey.duhhh is online now Report Post   	Edit/Delete Message

---

### Post by damnsavage on 2009-12-09
I have the same problem with an SL Technology NB1000 netbook. The wifi with WPA was working out of the box, but after some software updates by synaptic package manager the wifi is no longer working. 

It seems theres no driver for the wifi now, unfortunately I never checked what driver it was using out of the box. As far as I can see the only relevant app changed by synaptic package manager was network-manager. I downgraded the version to the original but this didn't help.

Here's my setup:

kernel version: 2.6.27-16-generic
Ubuntu 8.10 Intrepid ibex

% lspci
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)

% iwconfig
lo        no wireless extensions.
eth2      no wireless extensions.
pan0      no wireless extensions.

% lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 02
       serial: 00:24:25:01:d7:1b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.57 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:64:c7:52:34:7e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by MartijnLoth on 2009-12-09
It seems an update broke the NetworkManager...

Installing wicd as follows did the trick for me :)

```
sudo apt-get install wicd
```

Now just start up wicd and you should be ready to rumble again!

Good luck!

---

### Post by dog_biscuits on 2009-12-21
> **MartijnLoth said:**
> It seems an update broke the NetworkManager...

Installing wicd as follows did the trick for me :)

```
sudo apt-get install wicd
```Now just start up wicd and you should be ready to rumble again!

This worked for me too on me Asus Eee 1005HE. Thanks for the help.

---

### Post by ducu on 2010-01-02
hello, 

it seems that after kernel updates the wireless driver is not loaded anymore in my case. 
loading the driver again solves my initial issue. 
```
sudo modprobe b43
```

---

### Post by SandRat on 2010-01-02
Yep. Same as MartijnLoth.

I just posted what I did at [http://ubuntuforums.org/showthread.php?t=1365078&highlight=broadcom+pcmcia+bcm4318](http://ubuntuforums.org/showthread.php?t=1365078&highlight=broadcom+pcmcia+bcm4318)

It now works for all my different wireless needs open or keyed.

Wicd rocks!

---

