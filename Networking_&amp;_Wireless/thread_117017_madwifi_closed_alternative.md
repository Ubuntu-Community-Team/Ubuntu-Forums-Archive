---
title: "madwifi closed? alternative?"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by nalmeth on 2006-01-14
I followed this howto to install wireless support for my DWL-G650 card here:
[http://ubuntuforums.org/showthread.php?p=408470#post408470](http://ubuntuforums.org/showthread.php?p=408470#post408470)

The wget got me a '404' NOT FOUND. I went to the website, and it informed me the link was closed as of 5 weeks ago? It refered me to snapshots.madwifi.org
There is no CVS version here. Only versions for 'subversion'.
Something seems weird. Anybody know what is up?
Can anyone direct me to the CVS elsewhere, or a better way to setup a DWL-G650 wireless card?

---

### Post by nalmeth on 2006-01-14
UPDATE:

I believe now, that my card is a common one and should have been set up out of the box, only it is not picked up as present.
I learned this when I found the windows drivers, and installed them, and found "hardware not present".
```

sudo cardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
```
wlan0 is not present anywhere by default. 

```
lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc.: Unknown device b115
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
0000:00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
0000:00:07.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Modem] (rev 20)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1420
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1420
0000:00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:1D:83:FE
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe1d:83fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17684675 (16.8 MiB)  TX bytes:937580 (915.6 KiB)
          Interrupt:10 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2437914 (2.3 MiB)  TX bytes:2437914 (2.3 MiB)

```

Can anyone offer any ideas with this information:confused:  Could my wireless card be busted, or my network adapter? I still get eth0 just fine.
Sorry for long post, but figured this information might be needed.

EDIT: The laptop itself is a Sony Vaio amd 800 mgz. Is this a factor?

---

### Post by Lambert on 2006-01-14
Your card looks like it's not being added into the bus. Is the card broken?? It might just be a problem with the slot. Do you have another slot or pc you can test it in?

Run this command to see if it's recognized.

sudo lshw 

The driver you need will be in a package called linux-restricted-modules for the kernel you're using. It's on the install cd if it doesn't install but the first step is getting card recognized and inserted into the bus.

---

### Post by spd106 on 2006-01-14
Check that the card revision is compatible, I seem to remember that you need b1 or later firmware version for madwifi to work.

 Do any of the lights come on when you plug the card in?

Can you test it on another machine?

---

### Post by nalmeth on 2006-01-14
Thanks for reply's guys!

sudo lshw doesn't show my wireless card. I just found there is another slot below the one I was using, but its on the same port. Should I need to reboot for it to work, in case it was a faulty slot? Or would the lights come on whenever its plugged in? 

The lights have not come on at all since I've been trying.
What was that last point about firmware? This is what sudo lshw says about it:
*-firmware
description: BIOS
vendor: Sony Corporation
physical id: 0
version: R0102K5 (03/19/2001)
size: 86kb
capacity: 448kb
capabilities: isa pci pcmcia pnp apm upgrade shadowing bootselect acpi

EDIT: Do you know where I can update the firmware? I went to sony's website, and they think migrating to a new OS means migrating to Windows Me or Windows 2000..
Also they are asking for a lot more information than I think is necessary to submit a email for tech support.

prompt me and I will provide any info that would help.

Thank you

---

### Post by nalmeth on 2006-01-14
UPDATE:

The card works (lights come on) on a laptop with XP.
So has this rightfully been narrowed down to firmware issue? Or are there any other possibilities??

---

### Post by tripleee on 2007-04-18
Do other cards work in the same slot?

---

### Post by tturrisi on 2007-04-18
How do you know you need madwifi?  The DWL 650 has been manufactured using 4 different chipsets so far.  Madwifi is for atheros chipsets and NO additional firmware is needed for these chipsets.  Look on the back of the card and post here the full name & version # of the card.

---

