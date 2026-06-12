---
title: "Accessing drive with SMB and Windows"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by imhotep531 on 2011-08-02
I'd like to setup a drive on my Ubuntu Server (10.04.2 LTS) so two laptops running Windows 7 can read/write to it via the local network.

Can Windows read/write to ext2/3/4, or do I need to format the drive as NTFS?

---

### Post by CyberPingU on 2011-08-02
> I'd like to setup a drive on my Ubuntu Server (10.04.2 LTS) so two laptops running Windows 7 can read/write to it via the local network.

Can Windows read/write to ext2/3/4, or do I need to format the drive as NTFS?

You have to use samba. Just modify the /etc/samba/smb.conf.
You won't need to format anything, since the protocol used will be cifs (new version of smbfs). Keep in mind that file permissions won't be kept unless you mount your shared filesystem with acls on.

---

### Post by imhotep531 on 2011-08-02
I'm a beginner so if I understand what your saying, it doesn't matter what file format is on the drive I want to share because cifs will basically convert on the fly?

In other words, if I want to copy 10GB of photos from a drive that is formatted NTFS to a drive that is formatted ext2, cifs can do this?

---

