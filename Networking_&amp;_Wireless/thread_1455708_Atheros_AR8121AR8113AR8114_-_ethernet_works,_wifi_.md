---
title: "Atheros AR8121/AR8113/AR8114 - ethernet works, wifi doesnt"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by jamesco on 2010-04-16
I have a brand new ASUS EEE PC 900HA with Ubuntu 9.10 installed on it. The wireless hasn't worked yet but the ethernet is fine. I've been browsing the forums for hours to find a fix but now I've installed/queried/removed so many things I'm totally confused. 

lspci -v gives me this
```
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 8324
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at dc00 [size=128]
    Capabilities: [40] Power Management version 2
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [180] Device Serial Number ff-4e-cb-e0-0e-f3-53-ff
    Kernel driver in use: ATL1E
    Kernel modules: atl1e
```ifconfig only lists *eth0* and *lo*

I'm pretty confused right now and probably need to provide more info, so let me know what I'm missing.

---

### Post by coffeecat on 2010-04-16
Ubuntu 9.10 wireless should work just fine with (most of) the EeePC 900 series. Your posted lspci output is for the ethernet device, so I guess it didn't list the wireless. Which would agree with the output of ifconfig.

A slightly obscure feature of the EeePCs is that you can disable certain hardware devices in the BIOS. Sometimes this can happen spontaneously for no particular reason. Go into the BIOS, then Advanced tab > Onboard Devices Configuration. What does "onboard WLAN" say?

Failing that you could try toggling wireless on with Fn+F2 in the Ubuntu desktop, but I believe the BIOS setting over-rides this.

---

### Post by jamesco on 2010-04-16
No the WLAN is enabled in the BIOS, and I've tried turning on and off the wireless many times. Thinking about just doing a clean re-install since I was randomly downloading things before based on what people were saying. Hmm...

---

### Post by coffeecat on 2010-04-17
Even with trying out various things that may or may not work, lspci should see the wireless card. It simply interrogates the hardware. Which makes me wonder if the hardware is faulty, or whether the mini-pcie card is physically disconnected.

When you say a brand new EeePC, do you mean brand shop new? Did it come with Ubuntu or Windows (or another OS)? Did the wireless work before Ubuntu was installed?

---

### Post by jamesco on 2010-04-17
It is shop new, it came with a proprietary OS which was almost unusable, I just put Ubuntu on it immediately. Didn't test anything out to be honest. Is there a way to reset ubuntu back to the original install settings? Like, to remove all the things I've installed on it?

---

### Post by coffeecat on 2010-04-17
> **jamesco said:**
> Didn't test anything out to be honest. Is there a way to reset ubuntu back to the original install settings? Like, to remove all the things I've installed on it?

Tbh, a reinstall would probably be quickest. It only takes about half-an-hour.

It might be an idea to test the wireless in the live session before you reinstall. (I guess you're using a bootable USB stick.) It *should* work out of the box since it uses an Atheros  AR5007EG wireless chipset (according to a quick google.)

If the live session can't see the wireless card (with lspci or in Network manager) then you really have to think of a hardware problem.

---

### Post by jamesco on 2010-04-19
Ok I've reinstalled Ubuntu and it seems to be back to normal (but the wifi of course doesnt work)

I am now seeing this when I do sudo lshw -C network:

```
 *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:fbff0000-fbffffff

```lspci -nn gives me this:
```
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller [1969:1026] (rev b0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
```

Carefully wondering what to do first...

---

### Post by coffeecat on 2010-04-19
Well, at least lspci is seeing the wireless device this time around:

> **jamesco said:**
> ```

02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)
```

It's the 168c:002c bit that's important - the ID code. Googling that came up with:

[http://ubuntuforums.org/showthread.php?t=1369304](http://ubuntuforums.org/showthread.php?t=1369304)

... which suggests that my earlier google that told me the 900HA has an AR5007EG was wrong. There seems to be some confusion on that thread about which actual chipset it is, but the poster who says it uses the ath9k driver (rather than the ath5k) might be on to something. Some other google hits agreed with that (about the ath9k driver, that is).

Before you try ndiswrapper or try compiling your own driver, try this. Install the two packages (you'll need to connect with an ethernet cable, obviously):

linux-backports-modules-karmic
linux-backports-modules-wireless-karmic-generic

They will bring in an updated ath9k driver. Some people (myself included) have found this to be helpful with other Atheros wireless chipsets that use the ath9k driver. Whether you will with that one, I don't know, but it's worth a try. If not, then try googling '168c:002c' - you might find something useful.

---

### Post by jamesco on 2010-04-19
**success! ** :)

Installed ndiswrapper and used the driver that was posted in the other thread. Even though ndiswrapper gave an error, after restarting Ubuntu could see the wireless networks. However it couldn't connect to any, so I installed wicd and was able to connect using that. YES!

My next step is getting a thermal printer working, one that seemingly works with CUPS and Linux. So maybe expect another post from me soon :) 

Thanks for the help!
Jayme

---

### Post by ekeyme on 2010-05-03
> **jamesco said:**
> **success! ** :)

Installed ndiswrapper and used the driver that was posted in the other thread. Even though ndiswrapper gave an error, after restarting Ubuntu could see the wireless networks. However it couldn't connect to any, so I installed wicd and was able to connect using that. YES!

My next step is getting a thermal printer working, one that seemingly works with CUPS and Linux. So maybe expect another post from me soon :) 

Thanks for the help!
Jayme

hi, I have a Asus EeePc 900HA too. & the wifi-fixing road is very boring time. I'm very glad you have solved this problem. Can you tell me the detail step for this. very appreciated. Thanks&#65281;:D

---

### Post by RIT_girl on 2010-06-12
Hi! 

I've downloaded the ndiswrapper, but I'm having trouble knowing what to do now - or even get the necessary drivers. Ubuntu keeps blocking the download from their site.....

thanks in advance!

---

