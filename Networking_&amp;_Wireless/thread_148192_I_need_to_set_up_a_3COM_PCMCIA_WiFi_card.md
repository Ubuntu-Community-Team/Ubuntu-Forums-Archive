---
title: "I need to set up a 3COM PCMCIA WiFi card"
date: 2006-03-21
forum: Networking &amp; Wireless
---

### Post by jamespi on 2006-03-21
Hi,

I've just installed Ubuntu Breezy on a Toshiba Satellite PRO 4200 laptop. All devices work fine except my PCMCIA WiFi card. It is a 3Com 3crwe62092a 

[http://www.3com.com/products/en_US/detail.jsp?tab=features&sku=3CRWE62092A&pathtype=purchase](http://www.3com.com/products/en_US/detail.jsp?tab=features&sku=3CRWE62092A&pathtype=purchase)

I know the card works becuase it was running fine under Win98 and it was connecting to my other Ubuntu PC OK. I believe Win98 said it was an ATMEL card.

The laptop contains an absolute vanilla install of Ubuntu 5.10.

here is some output of things i did to see if the card was recognised by Ubuntu:

jamespi@colossus:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.


jamespi@colossus:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:58987 (57.6 KiB)  TX bytes:58987 (57.6 KiB)

jamespi@colossus:~$ sudo apt-get install atmel-firmware
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package atmel-firmware
jamespi@colossus:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Subsystem: Toshiba America Info Systems Toshiba Tecra 8100 Laptop System Chipset
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f0000000-f7ffffff

0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at fff0 [size=16]

0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at ff80 [size=32]

0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

0000:00:07.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
        Subsystem: Toshiba America Info Systems Internal V.90 Modem
        Flags: bus master, medium devsel, latency 0, IRQ 3
        Memory at ffefff00 (32-bit, non-prefetchable) [size=256]
        I/O ports at 02f8 [size=8]
        I/O ports at 1c00 [size=256]
        Capabilities: <available only to root>

0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
        Subsystem: Toshiba America Info Systems FIR Port Type-DO
        Flags: bus master, slow devsel, latency 64, IRQ 11
        I/O ports at ff60 [size=32]
        Capabilities: <available only to root>

0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 10100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=0
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 10101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=0
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at efff8000 (32-bit, non-prefetchable) [size=32K]
        I/O ports at ff00 [size=64]
        I/O ports at fefc [size=4]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 11
        Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
        Expansion ROM at 000c0000 [disabled] [size=64K]
        Capabilities: <available only to root>

=====================================

Correct me if im wrong but it doesnt look like the card is showing up. A couple of other threads on this forum said the kernel for breezy has ATMEL drivers built in and all you need to do idownload the firmware, but it doesn't look like this card is being noticed at all by the kernel.

I could be totally wrong and it isnt even an ATMEL or there could be a million other logs and things to check, so any advice is appreciated.

thanks,
james

---

### Post by jamespi on 2006-03-21
OK, here's some more info, the card better known as an X-Jack, and it is a clone of an NWN 1148.

Here is a thread about setting it up on an old 2.4 kernel version of Suse (8.0):
[http://www.linuxquestions.org/questions/showthread.php?t=21563](http://www.linuxquestions.org/questions/showthread.php?t=21563)

I'm a little out of my depth on this stuff, but i hope it helps someone else find my solution :)

---

### Post by Henry Rayker on 2006-03-21
my card (completely different, but still PCMCIA) doesn't work either. I'm having a hell of a time trying to figure out how to get any PCMCIA card to show up to ubuntu...

---

### Post by jamespi on 2006-03-21
OK another howtos for Gentoo:
[http://forums.gentoo.org/viewtopic-t-139831-start-0-postdays-0-postorder-asc-highlight-3crwe62092a.html](http://forums.gentoo.org/viewtopic-t-139831-start-0-postdays-0-postorder-asc-highlight-3crwe62092a.html)

hope this gives anyone more clues


As for what the previous poster said, is this a PCMCIA problem rather than a problem with my WiFi card?

---

### Post by jamespi on 2006-03-21
OK, i found another howto for <i>WARTY</i> with warnings about BETA quality drivers

[http://jouston.no-ip.com/archives/000127.html](http://jouston.no-ip.com/archives/000127.html)

i have to go to bed now so i dont have time to try it right now. if anyone has some thoughts on it, please post them anyway; you might save me some nightmares.

thanks,
james

---

### Post by Henry Rayker on 2006-03-22
> Correct me if im wrong but it doesnt look like the card is showing up.

I just, based off of that statement, that perhaps your card's not really the problem. Perhaps it's actually the cardbus. Maybe the card isn't being detected. I'm rather certain that my problem involves the card not being detected, so perhaps it'syour problem as well.

This is all just suggestion, because I know how frustrated I became when I realized that my drivers were fine, but the hardware is screwy...still haven't gotten it fixed, though...

---

### Post by jamespi on 2006-03-22
I know for sure that my hardware isn't screwy in the sense of physically broken because it worked under win98. 

But its totally possible this is a cardbus thing.

The two cardbus slots i have showed up in lscpi so i assume they are being driven by the kernel, but i know so little about linux hardware troubleshooting that i cant be sure of anything.

Is there some kind of equivalent to windows device manager? even if it is some CLI commands.

It was always handy to be able to tell that 
[LIST]
[*]the operating system detected the hardware
[*]there were drivers installed
[*]the device was working properly
[/LIST]

i assume lspci just tells you what devices are connected to the pci bus. can it tell you if drivers are loaded, and that devices are working correctly?

ok i just found the device manager in system->admin->device manager (duh)
it doesnt seem to have too much useful info though.

it shows both the cardbus bridges, but the status field just says "Status: status". Marvellous.

---

### Post by jml on 2006-03-22
I just did a Google search on your particular card and Linux.  I came up with a few bits of info.  There are many posts describing difficulties similar to yours.  Without any solutions.  I also searched the 3Com website for your card.  It was listed, but I was not able to get any specific info on what type of wireless chipset it uses.  I suspect that this is in fact a software driver issue and not a hardware one.  Especially since you state that the card worked in Windows.

Your best chance of getting this card to work is to utilize a program called NDISWRAPPER plus the Windows driver for your card and see if you can get it running that way as there appears to be no Native Linux drivers for this card.  If you search this forum for NDISWRAPPER and /or wireless you should be able to find several links explaining how to get this application and how to set it up.  The process in general terms involves first making sure you have the Windows driver for the card and NDISWRAPPER.  Then running the application and ultimately rebooting.  Then checking to see if the card is now recognized.  If it is then you can then set up the card and activate it in the networking application included with Ubuntu.  

If cost is not a concern, another option is to search this forum for compatible PCMCIA wireless cards and simply buy a new card to use in your laptop.  The cards that seem to be most compatible are the ones that utilize the Atheros chipset.  The one I use is the NetGear WG511T.  It is recognized by Ubuntu out of the box and simply requires configuration and activation.  Another card that works but is a little more pricey is the Cisco Aironet 350 series 802.11b card.  Hope this helps.

Joe

---

