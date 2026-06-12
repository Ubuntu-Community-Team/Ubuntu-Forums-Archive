---
title: "Problem with embedded NIC on Dell Optiplex 390"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by Karl1982 on 2012-02-14
Quick system summary.  I have a pair of **Dell Optiplex 390**s that must have **Lucid Server x64 **installed on them for a particular project (the software only supports LTS releases).  We got these computers for the project, and they're almost identical (only real difference is one is minitower with i5 4GB RAM, other is desktop with i3 and 2GB RAM).

The problem is with the embedded NICs.  I believe it to be purely a driver problem.  They work fine in Windows, and both systems are affected the same way.  Here is what the system has to say about the NIC:

>   *-network
       description: Ethernet interface
       product: **RTL8111/8168B **PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: [REMOVED]
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169 driverversion=2.3LK-NAPI** duplex=full firmware=N/A ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:2000(size=256) memory:e0a10000-e0a10fff memory:e0a00000-e0a03fffWhat happens is the NIC stalls during transfers.  More than half the  time, I can't even update my package list.  **Apt-get downloads packages  at 20-80 KB/s and frequently stalls**.  Anything else going through the NIC is slow and sometimes stalls.  As a test, I hooked a known-working laptop directly to it, generated a 500MB zero file, and attempted to transfer it via SFTP.  It stalls less than 1-2 MB into the transfer every time.

I did some reading, and apparently there are known issues with the Realtek r8169 driver.  According to [bug #839393]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393") it was fixed in an update for Oneiric.  I haven't for the life of me been able to figure out where/how this driver is installed (usually I don't have to mess around with too many drivers in Ubuntu), but from the thread in that bug report, it sounded like it might be an embedded kernel driver.  So I installed **linux-image-server-lts-backport-oneiric** to upgrade the system to kernel 3.0.0.15.  This fixed an unrelated issue with the video driver, but made no difference with the NIC.

I'm continuing to troubleshoot the problem, but I could really use some guidance.  I'm at the point where I really need to get this fixed and get the project underway, and I don't want to have to resort to using add-in NICs.  We're a couple days behind schedule because of these problems.

Thanks

---

### Post by Karl1982 on 2012-02-14
It never fails... I ALWAYS resolve my problems with Ubuntu right after posting for help on the forum.  I do apologize for the extra threads, but maybe the info will come up quicker in a search for the next person.

After doing a little more digging, I noticed in the bug thread that the OP was able to fix it by loading the r8168 driver instead of r8169.  So I searched for r8168 instead and landed on [this thread]("http://ubuntuforums.org/showthread.php?t=1831870") describing exactly how to fix the problem.

All I had to do was download and install the proper driver [from here ]("http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=fa#2")(and look, it's only a couple weeks old, isn't that nice?).  Although it says for kernel 2.4/2.6, it appears to be working just fine on the backported kernel 3.0.0.15, so maybe I'll keep it... although since installing the backported kernel, now the system halts instead of rebooting.  :(  So many issues on a new box...

And while I've been struggling with this one, it appears the smaller box has had a change of heart and is working fine with the default r8169 driver.

---

### Post by Karl1982 on 2012-02-14
Got the rebooting fixed.  In the backported kernel, the system needs a special reboot kernel argument ([here's a list]("http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/")).  Core i3 box with default server kernel and driver is still networking like a champ after having the same issue as the i5 for the first two days...

What worked: pci
What didn't work: warm cold bios triple kbd acpi
What I didn't try: smp efi force

---

