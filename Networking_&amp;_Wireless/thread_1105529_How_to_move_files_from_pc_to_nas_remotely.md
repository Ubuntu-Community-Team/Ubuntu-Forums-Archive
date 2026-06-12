---
title: "How to move files from pc to nas remotely"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by rolandrock on 2009-03-24
Hi All,

I can't figure out how to transfer files from my PC to my Worldbook network server from the command line and get transfer speeds as fast as the same operation through Nautilus.  I'll explain the setup.

I have a 1T Worldbook network server (hacked so I can ssh to it but still running Samba because we have a few Windows computers around).

PC mounts server using:
gvfs-mount smb://server/share

On the PC, I have a sort of daemon listening on a fifo that accepts urls to download on to the PC so I can dump file names remotely from my eeepc.  The daemon wgets the files, unpacks them if necessary and puts them in a holding directory.  (I do this to lessen the load on the wireless network and to reduce read/writes on my eeepc's SDD).

If I sit at the PC and cut'n'paste the files from the holding directory to the server using Nautilus, I get transfer speeds around 3.5Mbps.  If I ssh to the PC from my laptop and use:

cp filename ~/.gvfs/share/directoryname

I get transfer rates more like 200Kbps.

I have tried using gvfs-copy but don't really know how.  I can't find any useful docs on the internet and my attempts yield this;

gvfs-copy filename smb://server/share/Videos
Error copying file filename: Operation not supported

I've tried using quotes, changing '/' to '\' (silly I know) and various other things.  The server is working ok and is mounted correctly and Nautilus can transfer files fine.

What does Nautilus execute in the background to get such fast transfers?

How do I do this from the command line?

Many Thanks
Rock

---

### Post by rolandrock on 2010-04-16
Apologies for the overly complicated problem description.  The solution is briefer. 

Use:
> dbus-launch bash
then mount gvfs drive:
> gvfs-mount <path>
then command line use of gvfs-copy gvfs-move gvfs-mkdir works with no errors.
From a script, I'm sure you could find a way to launch gvfs-mount from the dbus-launch command but I haven't tested it.

---

