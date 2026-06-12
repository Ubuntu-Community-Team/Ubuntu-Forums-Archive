---
title: "No connection with wireless network anymore"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by BCMerlin on 2010-11-28
Since a few days i'm running Ubuntu on my laptop, so I'm very new in this. First day I had a wireless internet connection, but since yesterday I am not able to use wireless anymore and I don know why. Now I have a wired connection, but that's not my wish.

When I click in the icon above it tells me: "device not ready (firmware missing)".

Please tell me what to do.

---

### Post by mikewhatever on 2010-11-28
Can you post the output of the following from Applications->Accessories->Terminal.

```
sudo lshw -class network
```

The output should show the wireless model, and whether or not the module is loaded.

---

### Post by BCMerlin on 2010-11-29
> **mikewhatever said:**
> Can you post the output of the following from Applications->Accessories->Terminal.

```
sudo lshw --class network
```The output should show the wireless model, and whether or not the module is loaded.

Here it is:

Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by bazzal1941 on 2010-11-29
I think to give mikewhatever the information he needs you only need a single hyphen in front of class.

sudo lshw -class network

---

### Post by BCMerlin on 2010-11-29
> **bazzal1941 said:**
> I think to give mikewhatever the information he needs you only need a single hyphen in front of class.

sudo lshw -class network

Like this? 

  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:e3:1e:7e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.110 duplex=full firmware=sb v3.04 ip=192.168.1.33  latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:95200000-9520ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:94100000-94103fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:2e:b3:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=2.6.35-23-generic firmware=N/A link=yes multicast=yes  wireless=IEEE 802.11bg

---

### Post by Sam Fallow on 2010-11-29
> **BCMerlin said:**
> Like this? 

  
  *-**network DISABLED**
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:e1:2e:b3:eb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=2.6.35-23-generic firmware=N/A link=yes multicast=yes  wireless=IEEE 802.11bg

I'm going for the obvious here, but it though it detects the hardware it says 'network disabled'. 
Have you turned it off? 
For my laptop it's Fn+F11 to enable\disable. 
It's an easy mistake to make and one I'm guilty of in the past.

---

### Post by BCMerlin on 2010-11-29
> **Sam Fallow said:**
> I'm going for the obvious here, but it though it detects the hardware it says 'network disabled'. 
Have you turned it off? 
For my laptop it's Fn+F11 to enable\disable. 
It's an easy mistake to make and one I'm guilty of in the past.

Fn+F11... euheuh where do I find that Fn button??? :oops:

---

### Post by BCMerlin on 2010-11-29
Already found it... heheh, but it doesn't make a difference.

---

### Post by grahammechanical on 2010-11-29
Try either left clicking the icon and selecting your wireless network form the list of available wireless networks. Or right click the icon and click Enable Networking to disable networking, then click it a second time to enable networking. If your wireless connection is set to Automatically connect it should search for the transmissions from the router/modem and connect.

If you have already tried this, then switch on wireless from the keyboard before you load Ubuntu. The OS will detect a functioning wireless network card/device and try to make a wireless connection with it to the wireless modem.

Regards.

---

### Post by BCMerlin on 2010-11-29
> **grahammechanical said:**
> Try either left clicking the icon and selecting your wireless network form the list of available wireless networks. Or right click the icon and click Enable Networking to disable networking, then click it a second time to enable networking. If your wireless connection is set to Automatically connect it should search for the transmissions from the router/modem and connect.
Tried this. When clicking left I can't click on the wireless option, actually it isn't an option. Under wireless networks is mentioned in grey [I]"device not ready (firmware missing)".
[/I] 
When clicking right I see the wireless is already enabled.

> **grahammechanical said:**
> If you have already tried this, then switch on wireless from the  keyboard before you load Ubuntu. The OS will detect a functioning  wireless network card/device and try to make a wireless connection with  it to the wireless modem.
How do I switch on wireless from the keyboard? (and what's OS?)

---

### Post by mikewhatever on 2010-11-29
You use the b43 driver which is known to have connection problems. Sometimes reloading the module helps temporarily.
```
sudo modprobe -r b43 && sudo modprobe b43
```

If you don't have to use b43, remove it, then switch to the STA driver.

---

### Post by BCMerlin on 2010-11-29
> **mikewhatever said:**
> You use the b43 driver which is known to have connection problems. Sometimes reloading the module helps temporarily.
```
sudo modprobe -r b43 && sudo modprobe b43
```If you don't have to use b43, remove it, then switch to the STA driver.
Hmmmmz ok... I wrote the code in terminal, but nothing happens.
I don't know what b43 is, neither STA driver. Can you explain me?

---

### Post by mmsmc on 2010-11-29
when i do this it tells me that i am now disconnected
what do i do now

---

### Post by mikewhatever on 2010-11-29
> **BCMerlin said:**
> Hmmmmz ok... I wrote the code in terminal, but nothing happens.
I don't know what b43 is, neither STA driver. Can you explain me?

The code above just reloads the module with no output. B43 and STA are two drivers available for Broadcom wireless cards.
To switch to the STA driver, connect an ethernet cable and install the bcmwl-kernel-source package.

```
sudo apt-get install bcmwl-kernel-source
```

A reboot it required after that.

---

### Post by BCMerlin on 2010-11-30
Thanx. Before I switch:

How do I know I don't need the b43?
Why is b43 on my computer in the first place, when I don't need it? What is it doing?

---

### Post by BCMerlin on 2010-11-30
I have working wireless again!
What I did was going to system>administration>additional drivers
I changed the driver and after rebooting my laptop the wireless is working. Yaay :D
Thank you all for the assists.

---

### Post by nooodles on 2010-11-30
Quick add-in 
I found this thread to help me out quite a bit.

Turns out that my fix was a problem of camouflage
Seams the WiFi activity light is also the enable/disable wifi button ](*,)

....you have to see the laptop to understand this oversight... *insert facepalm here*

---

### Post by grahammechanical on 2010-11-30
Sorry. OS = Operating System (the software that runs on the computer).

Sometimes we change things like settings and the Operating System does not notice that things have been changed because it reads the configuration files when it boots - loads up - you switch on.

I was suggesting that by pressing the Fn + F11 button your wireless device on the motherboard will be switched on in hardware. Then when you load up the Operating System (Ubuntu) it will detect a working wireless device and switch on the parts that work wireless.

I do not have your problem because I have a desktop machine. The wireless hardware activates when I switch the machine on. As I understand laptops, you can disconnect the wireless part of the laptop to reduce battery power usage (by pressing the function key combination).

If you go to System>preferences>Startup Applications and chose the Options tab, you press the button Remember Currently Running Application. This might (I said might) help Ubuntu remember to switch on its wireless bits and pieces when you next switch on.

Regards.

---

