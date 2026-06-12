---
title: "Cross-platform network video file transfer. HELP!!"
date: 2008-09-04
forum: Multimedia Software
---

### Post by jesushero on 2008-09-04
I am having a unique situation problem, trying to transfer a big video file over a network.

Details:

The only computer that I could transfer video from a DV tape (firewire needed) runs Windows XP. I transfered the video and now have a 2.5 gigabyte AVI file. I haven't used Windows for a while now, so I'm a bit out of it..

I've tried to transfer the file to an Ubuntu Studio 8.04 machine, situated about 10 meters away, using the FTP program from the MS-Dos command line, and ProFTPd (server, standalone) on the Ubuntu box. I connected, authenticated, set the mode to Binary (I) and used "send file.avi". It starts the transfer but the connection is dropped after 150mb. I then proceeded to transfer the file to an Ubuntu Server 8.04 (server kernel) situated 10 kilometers away, running ProFTPd (standalone) using the same steps. It failed again, but at a different point.

More details: Windows XP has two drives, loads of free space, both drives NTFS. The first linux box, the close-by one, is connected through a LAN to the WinXP box (no firewall), really fast, no transfer limits, one drive, ext3, loads of free space.

The ubuntu server is connected to the WinXP box through the internet, with two firewalls, one on the WinXP side and one on the Server side. One drive, ext3, loads of free space. No transfer limits here either.

I am not allowed to install any software on the Windows XP machine. I need to find a way to get this to a Linuxbox! Preferably without having to buy myself a 4gb flash drive to do it like that. Oh, I can't burn a DVD on that machine either. What do I do? Any ideas?

---

