---
title: "Wired Ethernet Not Connecting"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by joebrueske on 2012-12-22
The other day I pulled my computer out of suspension, and a message popped up (console type) about a service not being started. It came and went so fast I didn't see what it said, so it may not have anything to do with my current issue. However, immediately Ubuntu told me that my Wired Connection was disconnected and I am now offline. Odd. So, I checked the setting and the connection was turned to off. I tried getting to the connection settings, but the systems menu wouldn't let me. VERY odd! Also VERY frustrating.

I logged out of my GNOME Shell session and logged in to GNOME classic. Same thing, except I could look at the settings. Everything looked fine, DHCP set to automatic since I'm using a cable modem.

This seems to be a Ubuntu issue. Something broke, because no matter how many times I restart and suspend, I can't get back my default Wired Connection. I really don't have time between now and the New Year to go searching for the solution, so I thought I'd just ask here. Thanks. :)

XP doesn't seem to have an issue getting the connection going, so it's not hardware. Though, sometimes there's an I/O conflict on the motherboard, and that's been fun to troubleshoot. But this isn't that.

---

### Post by Cheesehead on 2012-12-22
Look in /var/log/dmesg to see boot messages.

Did wired networking ever work in Ubuntu on this machine?

Try the command [FONT="Courier New"]lspci[/FONT] to see the hardware connected to the PCI bus. Look for a the ethernet controllers:
For example,
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AMBIT Microsystem Corp. AR5BXB63 802.11bg NIC
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

05:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0213
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```
See how both of mine have kernel modules assigned? Post yours here.

If one of yours is missing a kernel module, then search in /var/log/dmesg for relevant boot messages and post them here. For example:```
cat /var/log/dmesg | grep atl1c
[    1.674906] atl1c 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.674937] atl1c 0000:05:00.0: setting latency timer to 64
[    1.804790] atl1c 0000:05:00.0: version 1.0.1.0-NAPI
[   48.760807] atl1c 0000:05:00.0: irq 42 for MSI/MSI-X
```
All that gibberish means something to us.

However, if both controllers do have kernel modules assigned, then please post the result of the command [FONT="Courier New"]ifconfig -a[/FONT]

---

### Post by Shijy on 2012-12-23
Hello, Cheesehead!
I have encountered the same problem with joebrueske!
Before the forced shutdown &#65292;wired networking work properly in Ubuntu on my machine!
Now, although I reinstall my operating system, it doesn't work without port leds lighting.
When I type the "lspci" command, I can only find one item  about the ethernet controllers. As follows:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

When I type the "cat /var/log/dmesg | grep atl1c" command, I could not see anything.

Can you provide a workaround for me? Thank you!

---

### Post by joebrueske on 2012-12-23
> **Cheesehead said:**
> Look in /var/log/dmesg to see boot messages.

Did wired networking ever work in Ubuntu on this machine?
Yes, it's always worked. Every once in a while it doesn't. I'm guessing that happens because the CPU finds an I/O conflict and it doesn't get assigned. It happens more with XP than Linux, though.

Oddly enough, when I booted into Linux tonight, it works. I'll still post the information you're requesting. Oddly enough the Gnome's system tray wasn't there. After futzing with it for a bit (and trying other sessions) I reset GNOME. Now it's all back to normal!

> **Cheesehead said:**
> Try the command [FONT="Courier New"]lspci[/FONT] to see the hardware connected to the PCI bus.
```
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```

> **Cheesehead said:**
> If one of yours is missing a kernel module, then search in /var/log/dmesg for relevant boot messages and post them here.
```
[    1.364190] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.364262] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
......
[    1.251729] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    1.251734] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.251765] e1000e 0000:02:00.0: Disabling ASPM L0s L1
[    1.251917] e1000e 0000:02:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.258397] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.268073] Refined TSC clocksource calibration: 3199.995 MHz.
[    1.268081] Switching to clocksource tsc
[    1.272857] usb 3-1: New USB device found, idVendor=0461, idProduct=4d0f
[    1.272863] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.272867] usb 3-1: Product: USB Optical Mouse
```

> **Cheesehead said:**
> However, if both controllers do have kernel modules assigned, then please post the result of the command [FONT="Courier New"]ifconfig -a[/FONT]
Of course I read this last. :P Why I didn't post this in the first place is beyond me.
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:2e:d4:c8  
          inet addr:69.76.195.223  Bcast:69.76.199.255  Mask:255.255.248.0
          inet6 addr: fe80::216:76ff:fe2e:d4c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11958388 (11.9 MB)  TX bytes:691689 (691.6 KB)
          Interrupt:16 Memory:90100000-90120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24164 (24.1 KB)  TX bytes:24164 (24.1 KB)
```

---

### Post by Shijy on 2012-12-23
> **joebrueske said:**
> Yes, it's always worked. Every once in a while it doesn't. I'm guessing that happens because the CPU finds an I/O conflict and it doesn't get assigned. It happens more with XP than Linux, though.

Oddly enough, when I booted into Linux tonight, it works. I'll still post the information you're requesting. Oddly enough the Gnome's system tray wasn't there. After futzing with it for a bit (and trying other sessions) I reset GNOME. Now it's all back to normal!


```
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
```
```
[    1.364190] e1000e 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.364262] e1000e 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
......
[    1.251729] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[    1.251734] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.251765] e1000e 0000:02:00.0: Disabling ASPM L0s L1
[    1.251917] e1000e 0000:02:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.258397] e1000e 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.268073] Refined TSC clocksource calibration: 3199.995 MHz.
[    1.268081] Switching to clocksource tsc
[    1.272857] usb 3-1: New USB device found, idVendor=0461, idProduct=4d0f
[    1.272863] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    1.272867] usb 3-1: Product: USB Optical Mouse
```
Of course I read this last. :P Why I didn't post this in the first place is beyond me.
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:2e:d4:c8  
          inet addr:69.76.195.223  Bcast:69.76.199.255  Mask:255.255.248.0
          inet6 addr: fe80::216:76ff:fe2e:d4c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11958388 (11.9 MB)  TX bytes:691689 (691.6 KB)
          Interrupt:16 Memory:90100000-90120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24164 (24.1 KB)  TX bytes:24164 (24.1 KB)
```
Do you solve your problem now?

---

### Post by joebrueske on 2012-12-23
> **Shijy said:**
> Do you solve your problem now?
Who knows! I works, but I didn't do anything except let it sit over night. That doesn't mean it's fixed or won't happen again. So for now, yes.

---

### Post by Shijy on 2012-12-23
> **joebrueske said:**
> Who knows! I works, but I didn't do anything except let it sit over night. That doesn't mean it's fixed or won't happen again. So for now, yes.
You are so lucky! I have do anything I can do, include reinstall the operating system, replace the cable, configure it according to posts, let it have enough rest  etc. But it doesn't work yet.

---

