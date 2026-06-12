---
title: "AR8152 Ethernet Not Working in 10.10"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by abelian jeff on 2011-05-20
Hi everyone,

I'm having a strange problem with my ethernet card. In previous installs of 10.10 on this same computer, I've never had any trouble with either my wireless or my wired internet. However, after messing around with some other distros, I recently did a fresh install of 10.10 on this computer, and now only wireless internet is working. When I plug in an ethernet cable, I do not get connected.

One difference between this install and the previous installs is that, previously, I had always installed while connected to the internet via ethernet. This time I did it while connected wirelessly.

I've tried methods from other threads, but I've had no luck. In particular, I have trouble "make install"ing the official Atheros driver, and I've installed the compat-wireless driver atl1c, but I'm still not getting a connection.

Here is the relevant output of lspci -vv:

```
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Lenovo Device 396b
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 45
    Region 0: Memory at d2000000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 6000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```Thanks for your help!

-------------------

EDIT:  After a reboot, my ethernet is now working. I don't understand, but I'm happy.

---

### Post by moonport on 2011-07-29
> **abelian jeff said:**
> Hi everyone,

I'm having a strange problem with my ethernet card. In previous installs of 10.10 on this same computer, I've never had any trouble with either my wireless or my wired internet. However, after messing around with some other distros, I recently did a fresh install of 10.10 on this computer, and now only wireless internet is working. When I plug in an ethernet cable, I do not get connected.

One difference between this install and the previous installs is that, previously, I had always installed while connected to the internet via ethernet. This time I did it while connected wirelessly.

I've tried methods from other threads, but I've had no luck. In particular, I have trouble "make install"ing the official Atheros driver, and I've installed the compat-wireless driver atl1c, but I'm still not getting a connection.

Here is the relevant output of lspci -vv:

```
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Lenovo Device 396b
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 45
    Region 0: Memory at d2000000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 6000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

```Thanks for your help!

-------------------

EDIT:  After a reboot, my ethernet is now working. I don't understand, but I'm happy.

I've the same issue in my Lenovo laptop after an Ubuntu upgrade.
My Network card is a AR8152 v1.1 Fast Ethernet.
Here [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) you have the updated drivers.
Best

---

