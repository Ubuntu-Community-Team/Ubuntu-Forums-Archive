---
title: "Slow performance over SMB"
date: 2011-08-08
forum: Mythbuntu
---

### Post by hakras on 2011-08-08
I recently build a Mythbuntu server.  The Myth side of things is working great.  However, I'm having a performance issue with Samba.  I have a share with videos in it that my kids use to watch videos on their Windows XP system.  Browsing the folder seems fine, but when they execute the mkv file it takes about 30 seconds to start playing and occassionally stutters.  I used to have Windows 2008 on this same server and it played back fine.  I even had OpenSUSE on this same server for a while and didn't have this issue.  This issue also exists on my Vista laptop and my wife's Windows 7 netbook.  I don't have a linux workstation to test with.  I guess I could use a live cd to see if it happens on that too.  Here is the relevant part of my current smb.conf file:

```

[global]
netbios name = server
workgroup = workgroup
server string = %h server (Samba, Mythbuntu)
name resolve order = lmhosts host bcast

security = user

log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0

load printers = no
printing = bsd
printcap name = /dev/null
disable spoolss = yes

[videos]
path = /mnt/lvm/videos
comment = Videos

```

I left it as minimal as possible to see if that would speed things up, but it hasn't.  The issue is not isolated to this share either.  Every share browses fine, but is slow when you want to open/save/copy to it.  I copied 15GB to the videos share tonight (from my Vista system) and it took almost 3 hours.  It copied at about 1.3 MB/sec.  I then copied files to another Samba share (Popcorn Hour A-100) (from my Vista system) and it copied at 4.3 MB/sec.  I was thinking that maybe it was the logical volume, but I also have a share on a raid array having slowness as well.  Any idea why it's slow?

---

### Post by hakras on 2011-08-09
I installed/configure NFS and shared the same videos folder that I'm having trouble with SMB.  The share works flawless with NFS.  What is wrong with my SAMBA setup?  I need it for my Windows desktops.

---

### Post by thatguruguy on 2011-08-09
Have you tried installing XBMC on your windows computers? I think XBMC can use your mythbox as a upnp server without dealing with samba.

---

### Post by nickrout on 2011-08-09
What has this to do with mythtv?

If NFS is working then use it. Windows has nfs support.

---

### Post by ian dobson on 2011-08-11
Hi,

Try optimizing your tcp parameters in the global section in smb.conf

I'm using the following line in my file:

```
socket options = TCP_NODELAY SO_RCVBUF=262144 SO_SNDBUF=262144 rlimit_max=16384 IPTOS_LOWDELAY SO_KEEPALIVE
```

Without it I'm getting about 15Mbyte/sec with it about 33Mbyte/sec between my backend server and a Quad core windows7 box over a GByte network connection. Note your optimal values for socket options might be different to my, but it's a starting point.

Regards
Ian Dobson

---

