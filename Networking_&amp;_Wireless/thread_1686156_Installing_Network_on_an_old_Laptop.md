---
title: "Installing Network on an old Laptop"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by adhika on 2011-02-11
Hi all,

I just salvaged a very old laptop (still running a Pentium III) from my lab's storage room. I am thinking of using this laptop for outdoor testing so that I don't have to bring my "good" laptop out.

Since this laptop is very old and nobody has been using it for like years, I formatted it and installed Gutsy (7.10) on it -- too bad that I only have a live CD for this version. 

One thing that I realized is that although it has an ethernet port but when I plugged in my LAN cable, it does not recognize it immediately.

ifconfig returns just the local loopback.
```

lo Link encap:Local Loopback
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 addr:   ::1/128 Scope:Host
   UP LOOPBACK RUNNING  MTU:16436   Metric: 1
   RX packets: 16 errors:0 dropped:0 overruns:0 frame:0
   TX packets: 16 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0
   RX bytes:1232 (1.2 KB) TX bytes:1232 (1.2 KB)

```

Is there anyway to have internet on this laptop?

Thanks!

---

### Post by adhika on 2011-02-12
Is there any way that I still use this laptop? Thanks!

---

### Post by snowpine on 2011-02-12
The terminal command 'lspci | grep Ethernet' should tell you what kind of ethernet card is present. You can use this information to seek a solution.

Be warned however that the 7.10 release is over 3 years old and is no longer supported in any way. Newer releases have newer kernel and driver versions and will have better support for a wider range of hardware. It is possible your ethernet will work flawlessly "out of the box" with the current 10.10 release (although, not knowing which card you have, I can make no promises).

Even if you do manage to get 7.10 working, it receives no bug fixes or security patches. All of the software is extremely outdated and browsing the web may be a security vulnerability due to the obsolete browser. I highly recommend using a supported Ubuntu release. If you cannot download the current Live CD for whatever reason, you can find it periodically in a Linux magazine at your local newstand or request a CD by snail mail using the Ship It service: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by adhika on 2011-02-12
Hi snowpine,

Thanks. I tried lspci | grep Ethernet and it returns nothing. However, lspci it returns the following:
(Just a summary, can't really copy paste here)

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DZ
00:01.0 PCI Bridge: -ditto-
00:03.0 CardBus bridge: Texas Instruments PCI1420PC
00:03.1 -ditto-
00:07.0 Bridge: Intel Corp 82371AB/EB/MB PIIX4 ISA
00:07.1 IDE Interface
00:07.2 USB Controller
00:07.3 Bridge: Intel Corp 82371AB/EB/MB PIIX4 ACPI
00:08.0 Multimedia audio controller
01:00.0 VGA Compatible controller.

What I don't understand is why there is an ethernet port when there is no ethernet card inside.

I am trying to download 10.10.

---

### Post by snowpine on 2011-02-12
Check the computer's BIOS to see whether an Ethernet card is listed and enabled (some hardware allows you to disable the card).

If you can't get the internal card working, you might also consider a PCMCIA or USB network adapter. They are very inexpensive (under $20 US).

---

