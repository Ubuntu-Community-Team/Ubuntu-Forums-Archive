---
title: "download speed suddenly slow - 1.00 mbps"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by mystmaiden on 2011-01-09
I finally got Lucid LTS working yesterday and am really pleased, but at about the same time my internet speed has slowed to almost non-existant. I called our provider and they reprovisioned and reset the modem from there and I have reset the modem several times.

I did enable samba yesterday but I'm not at all sure that's the trouble. Is there something I can check via commands that might disclose the difficulty?

Any help is much appreciated, this one has me baffled.

mystmaiden


Edited to add what I've done since I posted.

I had two machines hooked to the modem (wired connection) via the vonage device to snag some files with samba. It worked well. It was later that my internet speed fizzled. I read some posts here that pointed to samba and since it isn't essential to me, I removed it and samba-common, reinstalled the desktop and reverted to the original samba file when asked. No real change.

Per suddenlink's suggestion I unhooked the vonage device and the spare computer and connected the primary computer to the modem. Before I did that though I checked the dl speed of the secondary computer it was over 4mbps when the primary was 1 or under. Connecting the primary directly to the modem actually slowed it down even more, .83 mbps.

Just out of curiousity, I popped a puppy linux cd in and rebooted, I got close to 5 mbps with it on the same computer that was giving me .83 moments before. So.. its obvious something is going on with the 10.04 OS, but I just don't know what....

suggestions?

thanks,
mystmaiden

---

### Post by PatchesTheCaveman on 2011-01-10
Try updating your Ethernet network adapter drivers.  To do that, run:
```
sudo apt-get install linux-backports-modules-net-lucid-generic
```

---

### Post by mystmaiden on 2011-01-10
Thank you for the reply, Patches, the command didn't work but its a good idea.

Here's what it returned -

```
sudo apt-get install linux-backports-modules-net-lucid-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-net-lucid-generic

```Can you think of something else I could try? Or maybe another way to phrase the command?

thanks again,

mystmaiden

Edited to add -

I ran this command, not sure if its helpful in this instance

```
sudo lshw -C Network
```

and got -

```
*-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:e0:06:09:07:85
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=74.194.224.250 latency=32 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:d400(size=256) memory:cfff8000-cfff8fff memory:2c000000-2c01ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

I do have virtualbox up and running on this machine, it seems to be doing as well as possible with the amount of internet speed I have right now...

---

### Post by PatchesTheCaveman on 2011-01-11
I'm sorry, I forgot you need to enable the *backports* repository for that to work.  To do that, run:
```
gksudo software-properties-gtk
```
and check the *backports* repository.

---

### Post by mystmaiden on 2011-01-11
Thank you again for replying, Patches. I don't see anything on the first software sources window that specifically says 'backports' but I have everything checked on the list.

I updated apt-get and it looked like backports were included but I got an error as well

```
W: GPG error: http://download.virtualbox.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-backports/Release  Unable to find expected entry  restricteddeb/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

when I ran the command to get the updated ethernet drivers, I got the same return as before 'unable to find'

---

### Post by PatchesTheCaveman on 2011-01-12
Looks like there's a problem with your APT configuration.  Please copy and paste the output of:
```
cat /etc/apt/sources.list
```

---

### Post by mystmaiden on 2011-01-12
You may be right, synaptic has been being a bit strange, I may have messed something up there. 

```
~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid-backports universe multiverse restricteddeb http://mirror.anl.gov/pub/ubuntu/ lucid restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid universe restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.anl.gov/pub/ubuntu/ lucid-security restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security restricted
deb http://mirror.anl.gov/pub/ubuntu/ lucid-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security multiverse
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
deb http://download.virtualbox.org/virtualbox/debian lucid contrib
deb http://archive.ubuntu.com/ubuntu lucid-backports universe multiverse restricted

```

Let me know if something looks out of place 

thanks

mystmaiden

---

### Post by PatchesTheCaveman on 2011-01-12
There are two problems with your configuration.  First, the lucid-backports repository line is repeated.  Remove the second line at the very bottom of the file.

Second, most Ubuntu mirrors to not mirror the lucid-security repository.  Change those lines to point to Canonical's official security updates repository:
```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by mystmaiden on 2011-01-13
Thanks for the hand holding.
Patches wrote:> There are two problems with your configuration. First, the lucid-backports repository line is repeated. Remove the second line at the very bottom of the file.I removed the second line of the bottom grouping since virtualbox was the one second Up from the bottom

```
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security restricted
```Patches wrote:

> Second, most Ubuntu mirrors to not mirror the lucid-security repository. Change those lines to point to Canonical's official security updates repository:I wasn't really clear on what 'mirrors to not mirror' meant but I replaced the next four lines with what you showed. 

```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse

```
Pretty sure this wasn't what I was supposed to do because when I ran 
```
sudo apt-get install linux-backports-modules-net-lucid-generic

eading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-backports_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package linux-backports-modules-net-lucid-generic

```

Edited - I've got the duplicates fixed now, still no linux-backports-modules-net-lucid-generic though.

---

### Post by PatchesTheCaveman on 2011-01-13
Sorry about the confusion.  I also missed one error, which was probably the biggie.  To make things easier this time, just replace the whole kit and caboodle with this:
```
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ lucid restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid universe restricted main
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-backports restricted universe multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-backports restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and th
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu/ lucid-security restricted main
deb-src http://security.ubuntu.com/ubuntu/ lucid-security restricted
deb http://security.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://security.ubuntu.com/ubuntu/ lucid-security universe
deb http://security.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu/ lucid-security multiverse
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
deb http://download.virtualbox.org/virtualbox/debian lucid contrib
```

---

### Post by mystmaiden on 2011-01-14
No need to apologize, I appreciate the help. I opened etc/apt/source.list and highlighted everything, hit backspace then copied what you had here saved and updated synaptic.  I still got 

E: Couldn't find package linux-backports-modules-net-lucid-generic

I don't know why its being so stubborn...

---

### Post by PatchesTheCaveman on 2011-01-14
Okay, I looked a little deeper and Lucid doesn't have an updated Ethernet drivers package, while Maverick does.  Which is odd because Lucid has every other updated drivers package Maverick does.  My apologies.

However, it does look like there are a few known issues with your Ethernet card that can be corrected.  Please run the following command and copy/paste the output so we can see if any are present:
```
dmesg | grep -i sis
```

---

### Post by mystmaiden on 2011-01-14
Thanks, Patches. For some unknown reason, my internet speed is better today. Here's the output of the command you mentioned, if there are issues with it - I'm all for fixing it now before this happens again.

```
[    0.000000] ACPI: RSDT 2bff0000 0002C (v01 AMIINT SiS740XX 00001000 MSFT 0100000B)
[    0.000000] ACPI: FACP 2bff0030 00081 (v01 AMIINT SiS740XX 00000011 MSFT 0100000B)
[    0.000000] ACPI: DSDT 2bff0120 03300 (v01    SiS      746 00000100 INTL 02002024)
[    0.000000] ACPI: APIC 2bff00c0 0005A (v01 AMIINT SiS740XX 00001000 MSFT 0100000B)
[    0.113331] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.262970] pata_sis 0000:00:02.5: version 0.5.2
[    0.307010] scsi0 : pata_sis
[    0.313218] scsi1 : pata_sis
[    1.797485] sis900.c: v1.08.10 Apr. 2 2006
[    1.797617] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.841556] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:e0:06:09:07:85
[   16.586495] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   17.087479] agpgart-sis 0000:00:00.0: SiS chipset [1039/0741]
[   17.297455] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xd0000000

```

---

