---
title: "Need Faster Speed Then What Samba Can Do..."
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by luna6 on 2006-01-15
Hello...
Is there someway to make Samba have faster transfer speeds and if not would NFS provide faster transfer speeds? Usually on huge (over 1 gigabyte movie files) that is stored on a server Linux Machine copied to the client Linux machine my transfer speed seems to be around 6-8 mbs whereas files transferred locally on either machine from one hard to another hard drive, the speed seems to be about 25-30 mbs. I am using a gigabyte switch with both machines having gigabit nic's so I dont think the bottleneck is in the network setup itself, just Samba. I have High Definition TV recordings stored on the server Linux Machine  (HDTV recordings seem to need over 10-15mbs constant transfer speeds) and when I try to watch HDTV recordings on the client Linux machine streamed via Samba, the video stutters and pauses alot, whereas if it is watched on either machine locally, the playback is smooth. So back to the question is there a setting to make Samba faster for transfer speed and if not would NFS provide faster speeds? Thanks...

---

### Post by luna6 on 2006-01-15
Well to answer my own question...I just went ahead and installed NFS and it gives me almost no overhead, transfer speed is about 28 mbs, about as good as I can get on my local server transferring files from one hard drive to another. I plan on still running Samba for another Windows machine I have in my home network. If I share the same directory on Samba and NFS it should not create a problem correct? TIA

---

### Post by skirkpatrick on 2006-01-15
Your server can share a directory as both/either Samba/NFS.  If you really want, your clients can mount them both too :)

---

### Post by luna6 on 2006-01-15
The one problem I am having with NFS is that it takes a long time from the mount command to actually mounting the drive, a few minutes for each drive it seems, have not rebooted the client computer yet, but think it might take a longggg time to boot because I have added the nfs mounts in my fstab. Would you know why it takes NFS so long to mount a drive? Once it is mounted it works beautifully. (At least now I can now watch hdtv recordings streamed from the linux server to the linux client without stuttering or pauses!)

---

### Post by luna6 on 2006-01-16
Also getting NFS to work with firewall is a little tricky, the part I am stumped at is getting statd, mountd, and lockd to use predefined ports.  How do I make statd, mountd, and lockd use static ports in Breezy, so I can use my firewall? 

The Gentoo Wiki talks about editing "/etc/conf.d/nfs" to accomplish this task but that file does not seem to exist in Breezy, maybe Breezy uses a similar file but named slightly different? If so what is it?

The howto on sourceforge says to issue a command of 
# statd -p 32765 -o 32766
# mountd -p 32767
but when I do that I get an error saying "statd: command not found" and "mountd: command not found"

And finally the ubuntu wiki does not seem to discuss using firewalls with nfs server.

---

### Post by skirkpatrick on 2006-01-16
You're beyond me on Ubuntu.  My server is still running RH8.

---

