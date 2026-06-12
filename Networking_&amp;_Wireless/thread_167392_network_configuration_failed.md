---
title: "network configuration failed"
date: 2006-04-28
forum: Networking &amp; Wireless
---

### Post by yaru22 on 2006-04-28
Hi. I tried to install Ubuntu 5.10 on my laptop, Acer Aspire 1692WLMi.

When I installed it, it detected two lan cards:

eth0: Intel Corp. PRO/wireless 2200BG
eth1: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet

I chose eth1 as my main lan card.

However, on the next step, network autoconfiguration keeps failing.

My laptop is connected to a router, which in turn is connected to a cable modem.

And DHCP is enabled on my router.

But it keeps saying that "Your network is probably not using DHCP protocol."

I don't know what to do.

I tried skipping this step, finishing my installation, and try to configure in linux.

I failed in every possible ways I could think of.

The internet worked on Windows XP. 

I don't know why Ubuntu can't connect my laptop to the Internet.

Can anyone help me out of this please?

Thank you very much.

---

### Post by the_burk on 2006-04-28
are you sure you are using the right card so you arent using eth1 ?? :-k

---

### Post by yaru22 on 2006-04-28
yes, I'm sure I'm using the right card.
Beside, my wiereless lan was not enabled (it was turned off at that moment)
Also, I tried the autoconfiguration with eth0, too.
But I got the same result.

---

### Post by the_burk on 2006-04-28
is it the correct card .. 

check lspci and see if it is the right one .. 

otherwise modprobe for the correct driver

---

### Post by yaru22 on 2006-04-28
sorry, I don't know how to use lspci and modprobe. (i'm new to linux)

Could you tell me how to use it?

Thans.

---

### Post by Sef on 2006-04-28
for lspci:

Applications > Accessories > Terminal

then type lcpci and push enter.  Copy what you see there and paste in here.

---

### Post by yaru22 on 2006-04-28
here's the result of lspci:==============================
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rec 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Model Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801/FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:01.3 Unknown mass storage controller: texas Instruments: Unknown device 8033
0000:06:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Boadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
==============================================

I still don't know what to do with modprobe though ;

Thanks for helping me guys.

---

