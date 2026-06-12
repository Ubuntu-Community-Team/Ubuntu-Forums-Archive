---
title: "ethernet fails during heavy traffic"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by nazarener on 2009-04-04
I am using the latest jaunty packages (64bit) and have the followning problem since about 2 days:

I have a d945gclf2 board acting as a fileserver. when i access files over the network(and do some copying etc), the fileserver just vanishes from the local network.
Pinging FROM the fileserver then gives me "no buffer space available"
After some time the fileserver can be pinged again.
and the end of my /var/log/dmesg looks like this:
```
[   47.508201] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   47.508214] ACPI: I/O resource 0000:00:1f.3 [0x2000-0x201f] conflicts with ACPI region SMB1 [0x2000-0x2016]
[   47.508220] ACPI: Device needs an ACPI driver
[   47.668034] i2c-adapter i2c-0: found SMSC47M192 or compatible, version 2, stepping A0
[   47.719821] smsc47m1: Found SMSC LPC47M15x/LPC47M192/LPC47M997
[   47.966998] Adding 979956k swap on /dev/sda4.  Priority:-1 extents:1 across:979956k
[  140.344724] EXT3 FS on sda1, internal journal
[  155.188655] kjournald starting.  Commit interval 5 seconds
[  155.188896] EXT3 FS on sda3, internal journal
[  155.188908] EXT3-fs: mounted filesystem with ordered data mode.
[  155.546572] type=1505 audit(1238843367.547:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3282
[  155.659380] type=1505 audit(1238843367.659:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3286
[  155.659690] type=1505 audit(1238843367.659:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3286
[  155.659807] type=1505 audit(1238843367.659:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3286
[  155.659902] type=1505 audit(1238843367.659:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3286
[  155.959163] type=1505 audit(1238843367.959:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3291
[  155.959578] type=1505 audit(1238843367.959:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3291
[  156.036408] type=1505 audit(1238843368.036:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3295
[  156.493949] r8169: eth0: link up
[  156.493964] r8169: eth0: link up
[  167.308413] eth0: no IPv6 routers present
[  174.833628] [drm] Initialized drm 1.1.0 20060810
[  174.904086] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  174.904102] pci 0000:00:02.0: setting latency timer to 64
[  174.904817] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  174.912740] [drm:i915_setparam] *ERROR* unknown parameter 4
[  174.912831] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  175.271722] warning: `proftpd' uses 32-bit capabilities (legacy support in use)

```
The ethernet card is onboard and there are no other cards in the computer.

---

