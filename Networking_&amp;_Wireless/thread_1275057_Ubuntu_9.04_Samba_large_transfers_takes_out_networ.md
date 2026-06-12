---
title: "Ubuntu 9.04 Samba large transfers takes out network"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by MaxRC on 2009-09-25
After spending all night last night trying to figure this out I am at wit's end. Any help would be greatly appreciated.
 
Problem: I have Samba shares on a Ubuntu 9.04 32-bit server. Writing from Vista client to Samba shares works well - I've transferred over 400GB of files without issue. But reading large files, or large collection of files from Ubuntu to Vista client, breaks the network connection on Ubuntu. Both the Ubuntu and Vista client are on a gigabit LAN and transfer rates reach about 50MB/s on writes and 70MB/s on reads. The transfer stops all of a sudden after about 500MB-1GB of transfer, network monitor on Vista shows network activity dropping from 50% on a gigabit lan all the way to zero. When this happens, Ubuntu becomes unreachable through Samba, SSH, and HTTP. Ubuntu apparently looses all network connectivity and doing a "ping www.google.com" from the console returns an unknown host error. But as soon as the error is returned, pinging google again works, network is restored to Ubuntu, and I can once again connect to Ubuntu using Samba, SSH or HTTP. The file transfer that got interrupted cannot continue and must be cancelled.
 
I first noticed this problem yesterday, after running this configuration for about 2 weeks. I am not sure if this same problem existed before, because I don't remember if I've tried to pull that much data off of it in the past couple of weeks. I've performed a clean install from CD of Ubuntu 9.04 server with only webmin added. Server components installed at the time of installing Ubuntu include LAMP, mail, print, file, and OpenSSH.
 
Hardware/Software Configuration:
 
It's a MSI Nettop 100 (with Atom 330) with Ubuntu installed on a 4GB compact flash card in the on-board CF reader. Two Samsung 1.5TB drives are in a RAID1 array, with subdirectories shared out as SAMBA shares.
 
My network card info reported by Ubuntu:
 
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Device 4180
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        I/O ports at e800 [size=256]
        Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Memory at fdff0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
        Capabilities: [d0] Vital Product Data <?>
        Kernel driver in use: r8169
        Kernel modules: r8169

```
 
smb.conf:
```

[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = WORKGROUP
        os level = 20
        syslog = 0
        preferred master = no
        panic action = /usr/share/samba/panic-action %d
        usershare allow guests = yes
        max log size = 1000
        pam password change = yes
 
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
 
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
 
[Public]
        writeable = yes
        create mode = 777
        public = yes
        guest only = yes
        path = /mnt/raid/public
        directory mode = 777
 
[Multimedia]
        writeable = yes
        create mode = 777
        public = yes
        guest only = yes
        path = /mnt/raid/multimedia
        directory mode = 777
 
[Download]
        writeable = yes
        create mode = 777
        public = yes
        guest only = yes
        path = /mnt/raid/download
        directory mode = 777

```

---

### Post by sedawk on 2009-09-25
You can run "netstat -i" and check if any "Error"-columns show
a problem.
If this error happens also check "sudo ifconfig eth0".
Is the interface still up or is it marked as down?
Can you check the output of "dmesg" for any messages
at the end reporting problems ("link down", "link up").

There are some basic settings you might change with
the "ethtool" but this is nothing I would recommend at
this point.

Have you installed latest updates (newer kernel)?
What I would do is to boot the latest Live-CD (9.10 karmic)
and test network stability with the new Live-CD (e.g. 
mounting and configuring your samba shares and checking
the transfers again.)

---

### Post by MaxRC on 2009-09-25
Thanks for the suggestions!  After making my initial post, I continued to research this issue and  believe I found a very relevant thread on launchpad.net:
 
[https://bugs.launchpad.net/linux/+bug/347711](https://bugs.launchpad.net/linux/+bug/347711)
 
 
Based on the recommendations there, as well as sedawk's suggestion, I ran a dm
esg and saw the following segment:
 
```

[  340.000153] ------------[ cut here ]------------
[  340.000161] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
[  340.000167] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
[  340.000171] Modules linked in: ppdev video output input_polldev lp parport iTCO_wdt iTCO_vendor_support pcspkr serio_raw s
nd_hda_intel snd_pcm snd_timer snd soundcore intel_agp snd_page_alloc agpgart usbhid r8169 mii raid10 raid456 async_xor async
_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
[  340.000229] Pid: 0, comm: swapper Not tainted 2.6.28-11-server #42-Ubuntu
[  340.000233] Call Trace:
[  340.000244]  [<c01411d0>] warn_slowpath+0x60/0x80
[  340.000254]  [<c02c0030>] ? __freed_request+0xa0/0x120
[  340.000261]  [<c0138a4d>] ? find_busiest_group+0x15d/0x7e0
[  340.000271]  [<c0133e6c>] ? enqueue_entity+0x13c/0x360
[  340.000278]  [<c015e4a3>] ? getnstimeofday+0x53/0x110
[  340.000285]  [<c011f200>] ? get_physical_broadcast+0x0/0x50
[  340.000292]  [<c01616c8>] ? clockevents_program_event+0x98/0x150
[  340.000299]  [<c015e4a3>] ? getnstimeofday+0x53/0x110
[  340.000306]  [<c02d379d>] ? strlcpy+0x1d/0x60
[  340.000313]  [<c043f5f2>] ? netdev_drivername+0x32/0x40
[  340.000320]  [<c0453c59>] dev_watchdog+0x219/0x230
[  340.000327]  [<c01596ea>] ? hrtimer_forward+0x12a/0x170
[  340.000334]  [<c015e4a3>] ? getnstimeofday+0x53/0x110
[  340.000340]  [<c011f2f3>] ? lapic_next_event+0x13/0x20
[  340.000347]  [<c01616c8>] ? clockevents_program_event+0x98/0x150
[  340.000354]  [<c014b6d0>] run_timer_softirq+0x130/0x200
[  340.000360]  [<c0453a40>] ? dev_watchdog+0x0/0x230
[  340.000367]  [<c0453a40>] ? dev_watchdog+0x0/0x230
[  340.000374]  [<c01467d7>] __do_softirq+0x97/0x170
[  340.000379]  [<c015a876>] ? hrtimer_interrupt+0x186/0x1b0
[  340.000386]  [<c015a6c9>] ? ktime_get+0x19/0x40
[  340.000393]  [<c014690d>] do_softirq+0x5d/0x60
[  340.000399]  [<c0146a85>] irq_exit+0x55/0x90
[  340.000405]  [<c011f8fb>] smp_apic_timer_interrupt+0x5b/0x90
[  340.000412]  [<c010ac2c>] apic_timer_interrupt+0x28/0x30
[  340.000419]  [<c0110a12>] ? mwait_idle+0x42/0x50
[  340.000429]  [<c010884d>] cpu_idle+0x6d/0xd0
[  340.000435]  [<c04fde4e>] rest_init+0x4e/0x60
[  340.000440] ---[ end trace eeab9f5451916a76 ]---
[  340.040634] r8169: eth0: link up
[25762.040626] r8169: eth0: link up

```
 
I believe this was recorded when the link went down.  According to the thread I posted above, there appears to be a lingering issue with the Realtek RTL8111/8168B gigabit ethernet controller.  Some even suspected that it may be a hardware issue based on how long it's been around and ineffectiveness of patches to date.  However, it appears that there is hope as posters in that thread mentioned that newer kernels, especially the 2.6.30 kernel for Karmic, seem to resolves this issue.  I am using kernel 2.6.28-11. So happy.  Can't wait to go home and give this a try.  I will definitely report back with results.
 
I am a Linux newb, so thanks for all the help regarding what commands to run to check on the health of the network connection.  I am going to research if a new kernel can be installed without touching any of the other stuff...

---

### Post by MaxRC on 2009-09-25
I had another question:  why is it that doing an apt-get update and then apt-get upgrade does not upgrade me to the newest kernel of 2.6.28-15?  For giggles, I installed ubuntu desktop when I first started playing with this and that upgraded me to the -15 kernel.  Ubuntu desktop is no longer installed but why doesn't the server installation upgrade itself to the new kernel?

---

### Post by sedawk on 2009-09-29
You can try "apt-get dist-upgrade" but all this will
not move your computer from 9.04 to 9.10.

I've never done a command line upgrade, but there
seems to be a tool for it:
[http://ubuntuforums.org/showthread.php?t=590813](http://ubuntuforums.org/showthread.php?t=590813)

---

