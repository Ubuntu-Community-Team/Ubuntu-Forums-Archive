---
title: "Cannot MOUNT WIN shares"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by griadooss on 2009-11-02
Cannot MOUNT WIN shares over small mixed LAN: XP(x2); PCLinuxOS(x1); FreeBSD(xLAMP) and now Ubuntu 10.9(x1)

Nothing is wrong with XP shares on fileserver 'pc-cme' as not only are they accessible from this workstation via XP itself and PCLinuxOS, but also under Places >> Network >> PC-CME within THIS Ubuntu installation - when doing so the address populating the 'Location' bar in 'File Manager' [Nautilus?] is "smb://pc-cme/foyer/" -- and all sub directories and files are fully accessible.

HOWEVER, i want to MOUNT these samba shares, eventually in fstab, but CANNOT get any sense out of it using the 'sudo mount' directive in a terminal!

I CAN mount NFS shares from my FreeBSD LAMP [FAMP??] local web server, but of course I had to first install the NFS client on my workstation. No sweat!

It would appear SAMBA client is installed as i can see the XP shares under 'Places | Network', as explained above, and the Synaptic output is loaded with Samba related files that are installed. [including samba-client]

SO WHY does the following fail???

"sudo mount -t cifs //pc-cme/foyer /mnt/foyer"

...it returns:

> mount: wrong fs type, bad option, bad superblock on //pc-cme/foyer,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or soand when i look in syslog via:

"sudo dmesg | tail" returns:

...it returns:

> cifs_mount failed w/return code = -22If no joy on a technical solution, maybe somebody would be so kind as to just supply me with an FSTAB listing that works for them ... Ubuntu 10.9 >> WIN XP Share.

I would be most grateful

Thanks

GR

UPDATE: The answer was simple!! ...[aren't they all?] ... install smbfs !!  One might be forgiven to believe that if Samba-Client was installed by default, so might smbfs ... but it is NOT!!  ... thanks for the reply Iowan

---

### Post by Iowan on 2009-11-02
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares...
and [another]("http://ubuntuforums.org/showthread.php?t=1169149") for Windows share mounting problems.

---

