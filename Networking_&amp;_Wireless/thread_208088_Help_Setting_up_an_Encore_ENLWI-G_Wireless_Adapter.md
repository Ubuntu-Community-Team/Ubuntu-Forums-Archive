---
title: "Help Setting up an Encore ENLWI-G Wireless Adapter (Marvel 88w8335 Libertas chipset)"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by fernando on 2006-07-03
Hi ppl! Well, I've been trying to fix this for a hour already.. Guess I'm gonna need some help. 
This adapter is based on a Marvel 88w8335 chipset, it's an pci board. I already got it working using ndiswrapper, but what I really want to do is make it work in this way. I can set it in any mode I want, ndiswrapper wont allow me..
Ok, thats what I did.

After a clean install of Dapper, I downloaded the firmware extractor program located at ```
http://www.saillard.org/linux/mrv8k/files/
```
I compiled the mrv8k_extract_fw.c program using 
```
gcc mrv8k_extract_fw.c -o mrv8k_extract_fw
``` After I finished this step, I downloaded the wireless driver from [www.encore-usa.com](www.encore-usa.com), and used the firmware extractor on the Mrv8000c.sys. 
It then extracted the firmware, creating the following files:
```
mrv8k-b.fw
mrv8k-f.fw
mrv8k_fw_boot.h
mrv8k_fw_main.h
```
After this step was finished, I copied these files to /lib/firmware/2.6.15-23-386/, and then rebooted the system. After it initialized, the wireless card was recognized as an ethernet device, the problem is that it recognized the device as an wired card, and not as a wireless one.
I did a ```
lshw -C network
``` and got the following result:
```
 *-network:1
       description: Ethernet interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: e
       bus info: pci@00:0e.0
       logical name: eth1
       version: 03
       serial: 00:40:f4:e8:7f:fb
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=mrv8k multicast=yes
       resources: iomemory:fac00000-fac0ffff iomemory:fab00000-fab0ffff irq:193
```
As you can see, this is a wireless device, but it has no wireless capabilities. Can anybody help me with this problem??
Thanks in advance,

Fernando

---

### Post by fernando on 2006-07-03
anyone?

---

### Post by ToneDispenser on 2006-07-17
Hi Fernando,

I have a card with the same chipset family. I got it working with ndiswrapper.

I'll give the mrv8k module a try with my drivers...

---

### Post by ToneDispenser on 2006-07-17
I tried extracting the Firmware and Bootloader from my MRV8335NT.sys and MRV8335XP.sys, but it didn't work...

Both bootloader and firmware were not found in my driver.

---

### Post by tturrisi on 2006-07-17
> I already got it working using ndiswrapper, but what I really want to do is make it work in this way. I can set it in any mode I want, ndiswrapper wont allow me..
afaik you won't be able to change modes if use ndswrapper...or what mode are you wanting to put the card in to?  fyi, you cannot put any card into monitor mode when using ndswrapper ande then have the card used by a sniffer app, it just cannot be done.

---

### Post by yugo on 2006-08-17
I have reached the same point.
```
 *-network DISABLED
       description: Ethernet interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:40:f4:d9:d2:bf
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=mrv8k multicast=yes
       resources: iomemory:e8400000-e840ffff iomemory:e8410000-e841ffff irq:177

```
Any solution?

---

### Post by FrodoB on 2006-12-05
Was this ever resolved?

If not then this instruction and the drivers that it points out on the TRENDnet site should hopefully resolve it:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by TomNI on 2007-03-11
Hi,

anyone have a working solution for that problem? i have a 64 bit system and doenst find a 64 bit drive for the PCI wlan card (Encore ENLWI-G ). 

can anyone pls help me?

---

### Post by j0v3m on 2007-05-07
I have the same problem here, with ubuntu feisty amd64. I was able to connect the card with ndiswrapper in x86, but now with amd64 the driver doen't work and I can't find another.

# lspci
[...]
03:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

# ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present

But it simply doesn't work :( 

The ndis gtk interface says "Hardware presence: No" to it.

---

### Post by macabro22 on 2007-05-19
Doodes!

I got it working. Check it out:
[http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g](http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g)

---

