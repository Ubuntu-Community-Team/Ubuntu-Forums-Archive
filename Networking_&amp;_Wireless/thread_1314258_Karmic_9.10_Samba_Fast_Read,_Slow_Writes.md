---
title: "Karmic 9.10 Samba Fast Read, Slow Writes"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by MaxRC on 2009-11-04
I have a NAS that I built with 9.10 server on a MSI Nettop 100 atom device with two SATA drives in RAID1 array. This installation was initially done with an alpha release of Karmic, Alpha 5, I think, and gradually updated using apt-get. I've setup Samba shares on this server and access the shares with Vista clients.
 
I am now experiencing a situation where writes to the NAS is reasonably fast, 50-60MB/s on the gigabit lan. However, reading files from the NAS is capped at 10-12MB/s. It's almost as if reading from the NAS is limited to 100mbps for some reason. 
 
Any help would be greatly appreciated. Here's lspci info for my nic card:
 
```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Micro-Star International Co., Ltd. Device 4180
        Flags: bus master, fast devsel, latency 0, IRQ 28
        I/O ports at e800 [size=256]
        Memory at febff000 (64-bit, non-prefetchable) [size=4K]
        Memory at fdff0000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at febc0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
        Capabilities: [d0] Vital Product Data <?>
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>
        Capabilities: [160] Device Serial Number 00-f0-4b-58-00-00-00-01
        Kernel driver in use: r8169
        Kernel modules: r8169

```
 
And here is my smb.conf
 
```
 
#======================= Global Settings =======================
[global]
        log file = /var/log/samba/log.%m
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\s
successfully* .
        obey pam restrictions = yes
        map to guest = bad user
        encrypt passwords = true
        passwd program = /usr/bin/passwd %u
        passdb backend = tdbsam
        dns proxy = no
        netbios name = ubumax
        server string = %h server (Samba, Ubuntu)
        unix password sync = yes
        workgroup = WORKGROUP
        os level = 20
        syslog = 0
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
        preferred master = no
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
 
Here is the output from ethtool and mii-tool:
 
```
root@ubumax:/etc/samba# ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
root@ubumax:/etc/samba# mii-tool eth0
eth0: negotiated 1000baseT-HD flow-control, link ok
root@ubumax:/etc/samba#

```

---

### Post by ojobson on 2010-03-15
Did you find a fix for this? I have a similar problem, but reversed (slow reads, fast writes) and you configuration looks similar - which is just strange.

I have had this problem since I started using ubuntu... in January and am yet to find a solution having reinstalled three times and recently shifted from 9.04 to 9.10.

---

### Post by mchlor on 2010-06-19
me three.  My writes for a lack of a better word "pwn" at 65 MB/s but reads at pathetic 28 to 30 MB/s.  I believe there is some cacheing to the ram thing going on during the write cycles but not read cycle.  We need to get to the bottom of this.

---

### Post by mchlor on 2010-06-25
bump

---

