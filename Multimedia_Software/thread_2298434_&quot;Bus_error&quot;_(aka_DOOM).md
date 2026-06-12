---
title: "&quot;Bus error&quot; (aka DOOM)"
date: 2015-10-11
forum: Multimedia Software
---

### Post by quequotion on 2015-10-11
Yesterday, I experienced a nightmare upgrade failure with apt-get. It removed a few dozen packages, including the ubuntukylin-desktop package, and installed numerous (~80) unrelated, unrequested perl and python packages in their place. I was able to restore most of the proper package suite by setting the auto/manual flags for each of 2000+ pakages one by one. The installation boots and runs smoothly, except for one huge problem:

I'm getting "Bus error" crashes before any media player (music or video, ffmpeg or gstreamer, doesn't seems to matter at all) will start ***and*** when ever updates/installations/removals trigger libc-bin.  (Re)Installing libc-bin on it's own does not throw the error, only when other packages cause apt to process triggers for it.

I've been at this for the last 14 hours, and I've been through dozens of threads here and across the internet. I've deleted caches, checked for free space in /tmp/, purged many configuration files, removed and reinstalled every multi-media library and program, etc. None of these solutions work because the problem is quite obviously elsewhere. It isn't a hardware problem either--it only affects very specific programs: any kind of media player, and libc-bin's triggers (everything else is fine--grub is fine, pulseaudio is fine, epiphany is fine, etc).

What bus is being referred to? Dbus? the PCI Bus? a school bus?

I tried running gdb on some of the crashing programs, *gdb crashed with them*. strace says they are killed with "SIGBUS" but doesn't say which process killed them or anything about the "bus". What other tools could I use to debug this? Is there something that can monitor the "bus" while the programs attempt to load? What do libc-bin's triggers have in common with media players?

I need a solution ***other than*** reinstalling Ubuntu or creating a new user. I'm looking for helpful advice on debugging the "Bus error". I don't want to work around it, I want to get to the bottom of it and fix this once and for all. I will make a bug report when I have some clue what is going on.

In the meantime, I'll do a memtest and a fsck [s]just to prove that this is not hardware related[/s].

EDIT: Never got around to those tests, ran Spinrite instead. Turns out Ubuntu is killing hard drives.

---

### Post by quequotion on 2015-10-11
This is what happens to libc-bin during installation/removal of packages:```
 Processing triggers for libc-bin (2.21-0ubuntu4) ...Bus error
/sbin/ldconfig.real: Path `/lib/i386-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/i386-linux-gnu' given more than once
/usr/lib/i386-linux-gnu/libfakeroot:
    libfakeroot-0.so -> libfakeroot-tcp.so
/lib/i386-linux-gnu:
    libnss_mdns_minimal.so.2 -> libnss_mdns_minimal.so.2
    libsepol.so.1 -> libsepol.so.1
    libnss_mdns.so.2 -> libnss_mdns.so.2
    libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
    libhistory.so.6 -> libhistory.so.6.3
    libmount.so.1 -> libmount.so.1.1.0
    libcrypt.so.1 -> libcrypt-2.21.so
    libpthread.so.0 -> libpthread-2.21.so
    libnewt.so.0.52 -> libnewt.so.0.52.18
    librt.so.1 -> librt-2.21.so
    libgcc_s.so.1 -> libgcc_s.so.1
    libBrokenLocale.so.1 -> libBrokenLocale-2.21.so
    libkeyutils.so.1 -> libkeyutils.so.1.5
    libcom_err.so.2 -> libcom_err.so.2.1
    libnss_dns.so.2 -> libnss_dns-2.21.so
    libgpg-error.so.0 -> libgpg-error.so.0.15.0
    libmnl.so.0 -> libmnl.so.0.1.0
    libgcrypt.so.20 -> libgcrypt.so.20.0.3
    libnss_mdns4_minimal.so.2 -> libnss_mdns4_minimal.so.2
    libcgmanager.so.0 -> libcgmanager.so.0.0.0
    libacl.so.1 -> libacl.so.1.1.0
    libreadline.so.6 -> libreadline.so.6.3
    libnih.so.1 -> libnih.so.1.0.0
    libncursesw.so.5 -> libncursesw.so.5.9
    libnss_nisplus.so.2 -> libnss_nisplus-2.21.so
    liblzo2.so.2 -> liblzo2.so.2.0.0
    libpng12.so.0 -> libpng12.so.0.51.0
    libmemusage.so -> libmemusage.so
    libx86.so.1 -> libx86.so.1
    libncurses.so.5 -> libncurses.so.5.9
    libparted.so.2 -> libparted.so.2.0.1
    libtinfo.so.5 -> libtinfo.so.5.9
    libcidn.so.1 -> libcidn-2.21.so
    libnl-genl-3.so.200 -> libnl-genl-3.so.200.21.0
    libnss_files.so.2 -> libnss_files-2.21.so
    libpopt.so.0 -> libpopt.so.0.0.0
    libpcprofile.so -> libpcprofile.so
    libply-splash-graphics.so.4 -> libply-splash-graphics.so.4.0.0
    libblkid.so.1 -> libblkid.so.1.1.0
    libnl-3.so.200 -> libnl-3.so.200.21.0
    libirs-export.so.91 -> libirs-export.so.91.0.0
    libresolv.so.2 -> libresolv-2.21.so
    libntfs-3g.so.853 -> libntfs-3g.so.853.0.0
    libdbus-1.so.3 -> libdbus-1.so.3.14.3
    libattr.so.1 -> libattr.so.1.1.0
    libdevmapper.so.1.02.1 -> libdevmapper.so.1.02.1
    libseccomp.so.2 -> libseccomp.so.2.2.3
    libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
    libpamc.so.0 -> libpamc.so.0.82.1
    libisc-export.so.95 -> libisc-export.so.95.5.0
    libm.so.6 -> libm-2.21.so
    libfdisk.so.1 -> libfdisk.so.1.1.0
    libiw.so.30 -> libiw.so.30
    libext2fs.so.2 -> libext2fs.so.2.4
    libdl.so.2 -> libdl-2.21.so
    libthread_db.so.1 -> libthread_db-1.0.so
    libdns-export.so.100 -> libdns-export.so.100.2.2
    libbz2.so.1.0 -> libbz2.so.1.0.4
/sbin/ldconfig.real: /lib/i386-linux-gnu/ld-2.21.so is the dynamic linker, ignoring


    ld-linux.so.2 -> ld-2.21.so
    libply-splash-core.so.4 -> libply-splash-core.so.4.0.0
    libwrap.so.0 -> libwrap.so.0.7.6
    libnss_mdns4.so.2 -> libnss_mdns4.so.2
    libcryptsetup.so.4 -> libcryptsetup.so.4.6.0
    libsysfs.so.2 -> libsysfs.so.2.0.1
    libutil.so.1 -> libutil-2.21.so
    libnss_mdns6.so.2 -> libnss_mdns6.so.2
    libselinux.so.1 -> libselinux.so.1
    libsystemd.so.0 -> libsystemd.so.0.10.2
    libexpat.so.1 -> libexpat.so.1.6.0
    libpam.so.0 -> libpam.so.0.83.1
    liblzma.so.5 -> liblzma.so.5.0.0
    libply-boot-client.so.4 -> libply-boot-client.so.4.0.0
    libnsl.so.1 -> libnsl-2.21.so
    libisccfg-export.so.90 -> libisccfg-export.so.90.1.0
    libcap.so.2 -> libcap.so.2.24
    libc.so.6 -> libc-2.21.so
    libapparmor.so.1 -> libapparmor.so.1.3.0
    libanl.so.1 -> libanl-2.21.so
    libprocps.so.3 -> libprocps.so.3.0.0
    libudev.so.1 -> libudev.so.1.6.4
    libglib-2.0.so.0 -> libglib-2.0.so.0.4600.0
    libpam_misc.so.0 -> libpam_misc.so.0.82.0
    libss.so.2 -> libss.so.2.0
    libfuse.so.2 -> libfuse.so.2.9.4
    libuuid.so.1 -> libuuid.so.1.3.0
    libz.so.1 -> libz.so.1.2.8
    libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
    libulockmgr.so.1 -> libulockmgr.so.1.0.1
    libssl.so.1.0.0 -> libssl.so.1.0.0
    libsmartcols.so.1 -> libsmartcols.so.1.1.0
    libbsd.so.0 -> libbsd.so.0.7.0
    libpcsclite.so.1 -> libpcsclite.so.1.0.0
    libatasmart.so.4 -> libatasmart.so.4.0.5
    libpcre.so.3 -> libpcre.so.3.13.1
    libaudit.so.1 -> libaudit.so.1.0.0
    libply.so.4 -> libply.so.4.0.0
    libnss_nis.so.2 -> libnss_nis-2.21.so
    libkmod.so.2 -> libkmod.so.2.2.11
    libpci.so.3 -> libpci.so.3.3.1
    libSegFault.so -> libSegFault.so
    libbrlapi.so.0.6 -> libbrlapi.so.0.6.2
    libjson-c.so.2 -> libjson-c.so.2.0.0
    libnss_mdns6_minimal.so.2 -> libnss_mdns6_minimal.so.2
    libslang.so.2 -> libslang.so.2.3.0
    libnss_hesiod.so.2 -> libnss_hesiod-2.21.so
    libnss_compat.so.2 -> libnss_compat-2.21.so
    libusb-1.0.so.0 -> libusb-1.0.so.0.1.0
    libe2p.so.2 -> libe2p.so.2.3
/usr/lib/i386-linux-gnu:
Bus error
dpkg: error processing package libc-bin (--purge):
 subprocess installed post-installation script returned error exit status 135
Errors were encountered while processing:
 libc-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Then I have to reconfigure:```
dpkg --configure -a
``` At this point dpkg appears to pick up where it left off and finish without any trouble, or output.

---

### Post by quequotion on 2015-10-11
> **quequotion said:**
> What do libc-bin's triggers have in common with media players?ldconfig is what they have in common.

I downloaded the source package for libc-bin, and poked around in the debian pakaging. libc-bin.triggers contains only:```
interest ldconfig
```

There's another post out there somewhere that mentions ldconfig, but nothing ever came of it. Several threads note that certain media players will work when run as root but not as a normal user. That does not apply to me (they never work), but it does apply to ldconfig: I can run it as root, running it as a normal user gets an immediate "Bus error"

No solution yet, but now I have enough material for a bug report.

---

### Post by quequotion on 2015-10-18
Solution: Don't install Ubuntu under any circumstances.

The issue was indeed hard disk corruption--caused by software. Spinrite was able to correct the error. Given the number of reports of this problem related to media players in Ubuntu, I think it's a safe bet that some multimedia packages in Ubuntu are mis-configured and causing hard disk corruption. I can't afford to risk having such software installed on any computer.

---

