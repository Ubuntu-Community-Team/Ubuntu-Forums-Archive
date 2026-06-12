---
title: "Slow transfer to mounted CIFS Share"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by adam814 on 2010-05-02
Ok, here's the situation:

I have a Hitachi SimpleNET adapter (entry-level NAS device) on a Seagate FreeAgent 1TB external HDD (formatted ext3).  The NAS device is connected over 100MB/s ethernet to a Netgear Wireless G router.  All other devices connect using Wireless G.  The NAS runs embedded Linux on an ARM processor and it runs vsftpd and Samba for file transfers.

If I transfer a large file using an FTP client the transfer maxes out at around 2.5MB/s.  For my purposes that's good enough, especially considering the Wireless G bottleneck.  If I transfer a file from a Windows 7 client (using samba) I get around 2.2MB/s.  I know the CIFS protocol has more overhead than FTP and the difference in speed isn't that noticeable.

Any combination of Ubuntu and Samba results in me getting less than 1MB/s.  I've tried mounting it through Nautilus (GVFS) and /etc/fstab.  FTP from this same Ubuntu client gets around 2.5MB/s.

I don't have root access on the SimpleNET to change the smb.conf.  I've made a few adjustments to the mount options with no success.

Does anyone have any suggestions for how to either speed up 10.04 as a Samba client or mount a folder on an FTP server locally?  I've tried both curlftpfs and FUSEFTP.  With curlftpfs any write operation results in an I/O error and it crashes intermittently.  With FUSEFTP I never got that far and couldn't even browse the folder.

Any help with this would be appreciated.

Thanks.

---

### Post by adam814 on 2010-05-02
Well, now I have root access.  It turns out the default password for it is buried in the manual.

I didn't find anything out of order in the smb.conf that would be causing the issue.  It had all the socket options set the way I've read they should be (i.e. TCP_NODELAY SO_RCVBUF=8192, etc.)

That leads me to believe the problem has to lie with the samba "client" on the Ubuntu end.

---

### Post by gfx on 2010-06-20
I have a diskstation and a htpc with a shared folder and cifs is slower in ubuntu 10.04 with the same settings I used in previous versions.

After playing around a bit, using the network icon in the places menu to mount a windows directory like c$ gives much better performance while copying... (approx. 3x)

---

