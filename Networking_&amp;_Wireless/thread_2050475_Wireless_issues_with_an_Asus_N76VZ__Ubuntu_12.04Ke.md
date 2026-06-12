---
title: "Wireless issues with an Asus N76VZ / Ubuntu 12.04/Kernel 3.4/Intel Wireless-N 2230"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by blinduck on 2012-08-30
Hi everyone, fairly new to Linux. I've installed Ubuntu 12.04 on my Asus N76VZ, and I'm having issues with the wireless connection dropping every few minutes. I can disconnect and reconnect and it will then work again. 

I've already tried disabling IPV6, but that doesn't seem to do anything for me.

From: -lspci
Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

From: -ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:558665 (558.6 KB)  TX bytes:558665 (558.6 KB)

wlan0     Link encap:Ethernet  HWaddr 68:5d:43:74:0f:09  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:175053810 (175.0 MB)  TX bytes:11473651 (11.4 MB)

From -iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"SINGTEL-2042"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 98:2C:BE:ED:DB:B2   
          Bit Rate=6 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3741  Invalid misc:457   Missed beacon:0

And from: sudo lshw -C network
*-network               
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:74:0f:09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.4.0-030400-generic firmware=18.168.6.1 ip=192.168.1.36 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:f7900000-f7901fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f783ffff ioport:d000(size=128)

---

### Post by chili555 on 2012-08-31
Let's try a driver parameter. Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one quick file and make it persistent.

---

### Post by blinduck on 2012-09-02
This seems to have helped! How do I make that permanent?

---

### Post by chili555 on 2012-09-02
> **blinduck said:**
> This seems to have helped! How do I make that permanent?Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```A new, empty file will open. Use kate or leafpad or any text editor if you don't have gedit. Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close the text editor. You should be all set.

So the searchers can find the answer, please use thread tools at the top to mark Solved.

Have fun!

---

### Post by blinduck on 2012-09-03
Ok scratch that, nope it doesn't seem to work. Connection still drops frequently. Seems to be a random thing, doesn't follow any pattern..

Any other suggestions?

---

### Post by chili555 on 2012-09-03
You might try a different parameter:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the contents to:```
options iwlwifi 11n_disable=1 bt_coex_active=N 
```Proofread, save and close the text editor. Reboot and let us have your report.

---

### Post by Asus User on 2012-09-03
I also just bought an Asus N76VZ V2G today. 
Have had it for only 4 hours, and already have the same problem with the wireless network...
REALLY anoying... And I've tried to disable it in the powersafe mode, but nothing makes a difference...
I would give anything for a solution, since the computer is sooooo nice in every other way. But this is kind of important to get fixed... Seems like it might be a problem with this specifik model. But it's gotta be possible to solve it somehow, right ?

---

### Post by chili555 on 2012-09-03
> **Asus User said:**
> I also just bought an Asus N76VZ V2G today. 
Have had it for only 4 hours, and already have the same problem with the wireless network...
REALLY anoying... And I've tried to disable it in the powersafe mode, but nothing makes a difference...
I would give anything for a solution, since the computer is sooooo nice in every other way. But this is kind of important to get fixed... Seems like it might be a problem with this specifik model. But it's gotta be possible to solve it somehow, right ?What is your experience after the solution I proposed above?

---

### Post by Asus User on 2012-09-04
I havn't tried your solution yet.
I've ready that Intel in generel have major problems with many of their network cards.

I assume that is the same problem in this case.
My network card is an Intel Centrino Wireless-N 2230.
 
Therefore I will try to look for some driver updates.
 
If that doesn't work, I might give your solution a try :)

---

### Post by blinduck on 2012-09-04
> **chili555 said:**
> You might try a different parameter:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the contents to:```
options iwlwifi 11n_disable=1 bt_coex_active=N 
```Proofread, save and close the text editor. Reboot and let us have your report.
Hmm nope, that isn't working either. Connection still dropping really often.

@Asus User: If you manage to make it work, please post your solution here as well! This problem is making it really hard for me to work with ubuntu.

---

### Post by benTheLightman on 2012-09-25
Got exactly the same problem with the Asus N56vz with the Intel centrino 2230 wireless card. It seems to only occur on N-networks. Have no problems at all with my home G-network.

The fix didn't work either... still disconnects every few minutes

---

### Post by giannilinux on 2012-09-27
> **chili555 said:**
> Let's try a driver parameter. Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one quick file and make it persistent.

It worked for me!
Dell Inspiron 7520
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

---

### Post by burna on 2013-01-05
> **chili555 said:**
> Let's try a driver parameter. Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one quick file and make it persistent.

That worked for me, too!

Asus N76V
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

Great, thank you!

---

### Post by Grinage on 2013-01-29
this seems to be a persistent problem with all intel Centrino variants, i have option of ditching my Centrino and using Killer's Bigfoot Wireless instead, are there similar issues with that particular wifi card?  

Additionally after a kernel update sometimes the problem comes back and becomes persistent regardless of what solution may have worked in the past.

---

### Post by chili555 on 2013-01-29
>  i have option of ditching my Centrino and using Killer's Bigfoot Wireless instead, are there similar issues with that particular wifi card?The Bigfoot wireless I am familiar with uses the driver ath9k. Search this forum and see if there are ever any disconnects and drops or slow speeds with ath9k. Here, for example: [http://ubuntuforums.org/showthread.php?t=1877120&highlight=ath9k](http://ubuntuforums.org/showthread.php?t=1877120&highlight=ath9k)

Have you tried turning N speeds off at the router? My iwlwifi device is about perfect.

---

### Post by nezero on 2013-09-25
> **chili555 said:**
> Let's try a driver parameter. Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we'll write one quick file and make it persistent

Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```A new, empty file will open. Use kate or leafpad or any text editor if you don't have gedit. Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close the text editor. You should be all set.

So the searchers can find the answer, please use thread tools at the top to mark Solved.

Have fun!

Dell Vostro 3650 - Does the trick for this machine too, thanks for your posts

---

