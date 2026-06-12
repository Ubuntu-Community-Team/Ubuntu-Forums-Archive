---
title: "b44 NIC, ubuntu 9.04, eth0 continuous restarts"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by sarannmr on 2009-04-28
Hi,
   This problem has been happening since 8.10. ( 8.04 and previous were fine ). eth0 keeps going down every few seconds. Not an NIC problem as it works fine under windows. From the dmesg output, i thought the Flow Control thing could be a problem, but even though i changed it to 100baseTX-FD, (or HD) using mii-tool, it goes back to default auto-negotiate mode. 

Any help is welcome.
Please let me know if you need any info about my laptop.
( Which is a run-off-the-mill Dell Inspiron 6400 )

Here are some details.

[  783.559994] b44: eth0: powering down PHY
[  784.000159] b44: eth0: Link is down.
[  787.000247] b44: eth0: Link is up at 100 Mbps, full duplex.
[  787.000254] b44: eth0: Flow control is off for TX and off for RX.
[  908.149321] b44: eth0: powering down PHY
[  909.000149] b44: eth0: Link is down.
[  911.000237] b44: eth0: Link is up at 100 Mbps, full duplex.
[  911.000245] b44: eth0: Flow control is off for TX and off for RX.
[  948.441529] b44: eth0: powering down PHY
[  949.000151] b44: eth0: Link is down.
[  952.000233] b44: eth0: Link is up at 100 Mbps, full duplex.
[  952.000241] b44: eth0: Flow control is off for TX and off for RX.
[  997.297579] b44: eth0: powering down PHY
[  998.000190] b44: eth0: Link is down.
[ 1000.000236] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1000.000244] b44: eth0: Flow control is off for TX and off for RX.
[ 1041.604031] b44: eth0: powering down PHY
[ 1042.000153] b44: eth0: Link is down.
[ 1045.000238] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1045.000245] b44: eth0: Flow control is off for TX and off for RX.
[ 1117.120571] b44: eth0: powering down PHY
[ 1118.000142] b44: eth0: Link is down.
[ 1120.000236] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1120.000244] b44: eth0: Flow control is off for TX and off for RX.
[ 1203.072481] b44: eth0: powering down PHY
[ 1204.000147] b44: eth0: Link is down.
[ 1206.004217] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1206.004224] b44: eth0: Flow control is off for TX and off for RX.


           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:c4:f5:3a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

---

### Post by PowerPaul86 on 2009-04-28
Same here:

> 
paul@pp:/$ more /var/log/messages | grep eth0
Apr 27 19:43:50 pp kernel: [    4.457079] eth0: RTL8168b/8111b at 0xf7cbe000, 00:19:db:f5:ab:3a, XID 38000000 IRQ 2299
Apr 27 19:43:58 pp kernel: [   18.828294] r8169: eth0: link up
Apr 27 19:43:58 pp kernel: [   18.828299] r8169: eth0: link up
Apr 27 21:25:20 pp kernel: [ 6101.456906] r8169: eth0: link down
Apr 27 21:25:22 pp kernel: [ 6103.145263] r8169: eth0: link up
Apr 27 22:52:58 pp kernel: [11359.052364] r8169: eth0: link down
Apr 27 22:53:00 pp kernel: [11360.853738] r8169: eth0: link up
Apr 28 07:19:32 pp kernel: [41753.442319] r8169: eth0: link down
Apr 28 07:19:34 pp kernel: [41755.142667] r8169: eth0: link up
Apr 28 07:55:04 pp kernel: [43883.139597] r8169: eth0: link down
Apr 28 07:55:05 pp kernel: [43884.816643] r8169: eth0: link up
Apr 28 13:17:46 pp kernel: [63245.594827] r8169: eth0: link down
Apr 28 13:17:48 pp kernel: [63247.343351] r8169: eth0: link up
Apr 28 15:14:11 pp kernel: [70229.467877] r8169: eth0: link down
Apr 28 15:14:13 pp kernel: [70231.198727] r8169: eth0: link up
Apr 28 15:48:36 pp kernel: [72294.084853] r8169: eth0: link down
Apr 28 15:48:38 pp kernel: [72295.709436] r8169: eth0: link up
Apr 28 17:47:30 pp kernel: [79427.993778] r8169: eth0: link down
Apr 28 17:47:32 pp kernel: [79429.664589] r8169: eth0: link up
Apr 28 17:47:48 pp kernel: [79445.964878] r8169: eth0: link down
Apr 28 17:47:50 pp kernel: [79447.676563] r8169: eth0: link up


---

### Post by sarannmr on 2009-05-02
It turns out that this is a b44 driver problem, which the kernel chaps haven't fixed yet. I posted a bug report on launchpad, which turned out to be a duplicate of this bug [https://bugs.launchpad.net/bugs/279102](https://bugs.launchpad.net/bugs/279102).
And correspondingly [http://bugzilla.kernel.org/show_bug.cgi?id=11056](http://bugzilla.kernel.org/show_bug.cgi?id=11056) in kernel bugzilla.
This problem was caused when a new power saving feature was introduced in the b44 driver. Though not a solution to the problem, one can compile a new kernel with the old b44 module. 
Here is a link to one such compiled kernel. I've tested this and it works fine. [http://www.fi.muni.cz/~xbenes6/b44/](http://www.fi.muni.cz/~xbenes6/b44/)

---

### Post by phill84 on 2009-05-05
I'm having the same problem, is there a precompiled custom kernel for amd64?
or is there any other easier work-around beside using a custom kernel? Thanks

---

### Post by Agrivane on 2009-08-11
I encountered the same problem, disabling a BIOS feature called "Cool and Quiet" seems to have eliminated the issue.

...
Just to confirm, I've been running for about a day now without the issue appearing, if I turn the BIOS option back on, it occurs often.

---

### Post by manoova on 2009-08-16
> **Agrivane said:**
> I encountered the same problem, disabling a BIOS feature called "Cool and Quiet" seems to have eliminated the issue.

...
Just to confirm, I've been running for about a day now without the issue appearing, if I turn the BIOS option back on, it occurs often.

I am running mythbuntu 9.04 on a Dell Dimension E521.

# lspci | grep -i ether
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I have also disabled "Cool and Quiet" in the BIOS and the problem of the network card dropping the connection then reconnecting while using NFS and Samba has gone away. All seems fine at the moment. 

Can anyone else confirm this and does anyone know why the "Cool and Quiet" BIOS setting is conflicting with the Broadcom NIC?

---

### Post by Degian on 2009-08-16
> **manoova said:**
> I am running mythbuntu 9.04 on a Dell Dimension E521.

# lspci | grep -i ether
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

I have also disabled "Cool and Quiet" in the BIOS and the problem of the network card dropping the connection then reconnecting while using NFS and Samba has gone away. All seems fine at the moment. 

Can anyone else confirm this and does anyone know why the "Cool and Quiet" BIOS setting is conflicting with the Broadcom NIC?

My BIOS has a switch between Vista/Xp/UNIX but no "Cool and Quiet" option but the laptop does have a button which appears not to work but claims a similar function.   I too am experiencing continuous resets.   Can anyone help?

---

### Post by Degian on 2009-08-18
I have solved the problem by installing v.9.10 Alpha 3.

---

### Post by 1337_0N3 on 2009-08-31
Will this solution be back ported to Ubuntu 8.04 LTS??

---

