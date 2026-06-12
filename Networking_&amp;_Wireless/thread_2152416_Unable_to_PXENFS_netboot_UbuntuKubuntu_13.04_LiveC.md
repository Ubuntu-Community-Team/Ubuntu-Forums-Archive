---
title: "Unable to PXE/NFS netboot Ubuntu/Kubuntu 13.04 LiveCD"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by mrnedburns on 2013-06-07
Hello,

I have a system in place to PXE boot the Ubuntu 11.04 LiveCD.  This system works well but I need to create a 13.04 version to support some newer hardware.  Following the steps given at:

[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

I have the ISO mounted under loop at /srv/nfsroot/ubuntucd.  I also have the initrd.lz and vmlinuz files from the casper folder placed in my TFTP root.  My pxelinux entry is as follows:

LABEL 13.04 LiveCD Test
KERNEL casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=172.18.96.32:/srv/nfsroot/ubuntucd initrd=casper/initrd.lz

When I PXE boot, the kernel is retrieved via TFTP and initrd.lz launches.  I get as far as

Begin: Running /scripts/casper-premount ... done. done.

...before the system seems to hang.  There are then several messages about ethernet devices giving up after 2 seconds, 5 seconds, etc.

If I change the kernel arguments to boot=nfs it still attempts to boot but drops to BusyBox with a message about /dev/nfs not found.  I've been scouring the web and finding suggestions for various combinations of the kernel arguments but nothing has worked.

I hit the same symptoms with 12.04, so apparently something changed between 11.04 and 12.04.  Oh... my NFS share has been exported and I am able to mount it from other machines from the CLI so i don't believe it is an NFS share issue.  NFS share is running on ubuntu server 12.04, in case that matters.

Has anyone had success PXE booting the 12.04 or 13.04 LiveCD?  If so, please let me know.  I'm beginning to think it just isn't possible any more.

---

### Post by mrnedburns on 2013-06-07
I've just discovered something odd.  This system has 4 x GB NICs.  I typically only have 1 NIC plugged in.  Just for kicks, while it was in the hung state I plugged in the other NICs and came back to my desk.  The thing proceeded to mount the NFS share and boot the LiveCD.  It seems the problem must be related to initrd not finding the active NIC to use!  

Is this a bug, or something I should have known and need to configure?  I need it to just use the NIC that is active (the one that PXE booted to begin with!).  Any advice?

Thanks,

N

---

### Post by mrnedburns on 2013-06-17
It seems Ubuntu isn't able to properly detect which NIC is active.  I can force it to choose the proper NIC if I know which NIC it is ahead of time by using the kernel arg of ip=eth0 (if I'm using NIC1).  On platforms where there is an internal NIC for use in connecting to a peripheral I have to specify eth1.  I've simply created different pxelinux menu options for the platforms and seem to be in good shape now.  Too bad it quit working the old way, but at least this works!

---

### Post by keithspg on 2014-03-02
It took a bunch of time, but I was able to, finally, get this to work on my network.

I have: DDWRT router (dnsMasq), Freenas Server (9.2.1 for tftp and NFS)

Process: 

[LIST=1]
[*]unpack the CD into a directory on the server
[*]Share the directory  via NFS
[*]Set up tftp server
[*]put pxelinux.0 and appropriate config file in the tftp directory
[/LIST]

The troubles I was having were with ddwrt/freenas being a bit different than using linux server for everything (this underpins many of the howtos on the net)

In ddwrt, you need to make sure you put the appropriate DNSMasq commands in the correct box in its configuration
DDWRT: Under 'Services', there is a box labeled DNSMasq. Under "Additional DNSMasq Options" put the appropriate TFTP info
"dhcp-boot=pxelinux.0,<server_name>,<server_IP>" If yours does not have a name, just leave it blank and put in the IP after 2 commas.

on Freenas, you turn on the tftp service and select the directory where pxelinux.0 is. I suggest that you put the extracted iso contents in a folder in the tftp directory as it keeps things together.

Under freenas, all shared directories are all under '/mnt/<nas_pool_name>' in my case it is called 'first_NAS', and my pxe directory is called 'pxelinux'
so my tftp directory is "/mnt/first_NAS/pxe_linux"

I unpacked the full iso into the directory '/mnt/first_NAS/pxe_linux/ubuntu'. There are a bunch of howtos on this step.

In the NFS shares section, you have to export this directory with the full CD contents and make sure it is 'Maproot user = root' and 'Maproot group = wheel'

At this point, you need to make sure that the command in pxelinux.cfg will boot the live CD. I have a menu of a number of images, but the 13.10 live CD boots with this (edit to your configuration - key edits are in bold):
```
label xubuntu 13.10 -64    menu label xubuntu -64 Live - NFS
    kernel xubuntu/casper/vmlinuz  # the directory under the tftp server where the kernel is same directory where initrd.lz lives
    append initrd=xubuntu/casper/initrd.lz file=/cdrom/preseed/xubuntu.seed boot=casper vga=1 **netboot=nfs nfsroot=192.168.2.198:/mnt/first_NAS/pxe_linux/xubuntu** nosplash --

```

This is a minor edit to the command that boots the iso found in /isolinux/txt.cfg ('try Ubuntu without installing').

Hope this helps someone. I beat my head against the monitor until I figured out that the biggest problem I was facing was a buggy network card driver that caused a kernel panic at every boot! Now I am trying to put this fixed driver in the xubuntu directory on my server. I have been unsuccessful, so far, as it seems that many howtos are also out of date with the current iso.

Keith

---

