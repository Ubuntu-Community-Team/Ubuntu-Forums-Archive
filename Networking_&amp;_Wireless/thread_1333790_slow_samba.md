---
title: "slow samba"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by bryanchicken on 2009-11-21
i can only transfer files from ubuntu -> windows via samba at 1MB/s.
This is causing problems as i'm attempting to use ubuntu as the OS to share HD movies over my lan.
Both ubuntu and windows are connected to the lan at 100Mbps, so by my (possibly incorrect calculations) the max i would get is 12.5MB/s. I'd be well happy with half that right now though.

I've searched and searched for this on google and have tried the following options in my smb.conf
```

socket options = TCP_NODELAY TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192 $
log level = 1
read raw = yes
write raw = yes
oplocks = yes
max xmit = 65535
dead time = 15
getwd cache = yes
lpq = 30
large readwrite = no

```

I was able to stream the HD movies using the same hardware when both were on windows, but i'd really like to use linux for the server.

Can anyone help a non-native please?

---

### Post by bryanchicken on 2009-11-22
sorry to bump but i can't be the only one sharing files from ubuntu to windows with samba. 
What speeds are others getting? And with what settings?

---

### Post by bryanchicken on 2009-11-23
with a bit more testing i have found that between 2 windows machines i can copy a file at a sustainable 11.2MB/s.
Copying the same file on the same network from Linux -> Windows at best is 2.5MB/s.

There has to be something seriously wrong with either my samba setup or samba in general.

If i can't sort this i'll have to resort back to windows :-(

Anyone???

---

### Post by katmeef on 2009-11-24
Is the linux box using 100Mb/s full duplex to your switch/router, or is it possibly using half duplex?  Also, can you transfer from windows to linux at full speed or is that direction also slow?

Edit: for diagnostic, you could also setup an ftp server on the linux and see if it is also slow to the windows.

---

### Post by bryanchicken on 2009-11-24
Hi,
it is slow both ways.

I've tried both half and full duplex using ethtool, no (or little) difference between the 2.

Cheers.

---

### Post by Martiini on 2010-03-03
Samba has never worked for me.

Believe it or not ... 
currently on Ubuntu I get 60-80 kb/sec (!!!!) through 1,5mb linksys wrt54g router (1,5 mb filetransfer speed on windows).
I have been troubleshooting this before and scoured through linux forums with no luck.

no idea where to go to fix this.

---

### Post by ojobson on 2010-03-14
Did you find a fix for this?

I'm having slow read speeds too - writing is about 5 to 6 times faster than reading over samba.

This is in contrast to appletalk shares which my mac can read and write to at about the same speed as writing over samba. Unfortunately I also have windows clients on my network so I can't just use appletalk for all shares.

God knows why this is happening - i've tried all the usual tweaks that I can find on google..

---

### Post by Zathuras on 2010-05-14
Bump.

I've recently been experiencing this with 10.04 on x86-64 hardware. Specifically a linux box and a windows 7 64-bit box both with Realtek 8168 GigE network controllers.

I've attempted to install the vendor 8168 drivers but they didn't seem to help.  I used to easily get 40+MB/s on 9.10 before I upgrade hardware (which is when the new NIC was installed.)

Running out of ideas of what could be the problem...

In the meantime, what other solutions are there for sharing filesystems between windows and linux machines?

---

### Post by ojobson on 2010-05-15
What NIC did you have before? I'm using an intel atom board which has integrated realtek gigabit LAN.

I'm swapping out the OS hard drive later to install windows xp sp3 and see what speeds I get - if it is still crap then it must be a limitation with the hardware. However, if Zathuras is running a PCI card and still getting crap results then I suspect it is more likely  an issue with drivers but I don't know enough about linux and drivers to know where to start fixing this problem.

I get good speeds (25 to 30MBps) reading from the card (although not always and this is writing across the network to MAC's / PC's) but these other network machines (gigabit lan, wired) always write to the ubuntu machine at about 5 to 7 MBps (megabytes/s). Other MAC's/PC's can read write at about 35 to 40 MBps...

I fear I may have to give up my endeavour with ubuntu if I can't fix this. Which is a real shame as I liked the idea of ditching microsoft...

---

### Post by Eiríkr on 2010-05-15
Some questions for folks:

[list][*]Are you sharing between different machines all running some flavor of Linux or other Unix-y OS?
If so, Samba might not be the way to go -- it's designed for heterogeneous networking environments, and carries some overhead as a result.  You might want to explore using NFS instead.

[*]To help the rest of us get a handle on what's going on, please post the following:
[LIST=1]
[*]OS names and versions
[*]Which machine is the fileserver
[*]The contents of your [font="courier new"]smb.conf[/font] file
[/LIST]
[/list]
Cheers,

-- Eiríkr

---

### Post by ojobson on 2010-05-15
Server: Atom330D with 1 OS HD (40gb) 1 File HD (1TB)

Clients:
Macbook Pro (2009 - 5,5) connecting via samba, FTP, AFP
Windows 7 machine (pentium 920D), connecting via samba, ftp
XP SP3 Netbook - samba

Server is in pieces right now, haven't got a copy of the smb.conf (thought I had one in the cloud somewhere) but i have tried many different variations from completely simple to completely complicated including various sizes for SO_KEEPALIVE, SO_RCVBUF=8192, and SO_SNDBUF=8192 etc. and not much ever changes (occasionally it stopped working or went slower).

I get same speeds with afp, smb or ftp so I don't believe it to be an issue with samba configuration - i spent a great deal of time with that. I also turned off ipv6 as i found some threads suggesting that was an issue.

Spent a while messing around with configuring the network interfaces too but that got me nowhere.

---

### Post by Eiríkr on 2010-05-15
Interesting.  Out of curiosity, have you ever had a different OS installed on the file server?  If so, was the throughput any different?  Better, or worse?  

Cheers,

--Eiríkr

---

### Post by ojobson on 2010-05-15
No - unfortunately I didn't have a spare xp license to try, but I acquired one this week which I hope to test out this weekend. Hopefully this should reveal some answers!

---

### Post by Eiríkr on 2010-05-15
If you have the time, it might also be worthwhile to try throwing some other Linux or BSD distro on there and see if that performs any differently.  Might be cheaper (and maybe easier?) than getting Windows.  :)

Cheers,

-- Eiríkr

---

### Post by ojobson on 2010-05-15
Right, well XP gets 25 to 30 MBps speeds in both directions to all machines on the network.

Just to really confuse matters I discovered something really interesting.

I swapped over the drives once more, went back to ubuntu and upgraded to 10.04 in a last ditch attempt to fix things but I did something I don't normally do, I logged on to the other share that I created when I set up ubuntu, but I did this one via the GUI menu's - this one works at full speeds.

Now, when I use the shares that I have defined in smb.conf I only get 7MBps read speeds when accessing from remote clients, unless I use the share I created via the GUI.

Now, this sounds all well and good, but I just tried to create new shares using the GUI but I get the following error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

It is running because I can access the shares!

---

### Post by Zathuras on 2010-05-15
The plot thickens...

The linux server was previously an Athlon X2 2.6ghz running on an EVGA 730a motherboard.  It was upgraded to a Phenom II 940 AM3 with an AM3 compatible motherboard.  Both boards have the exact same networking chipset... the realtek 8168.  I didn't realize this till just now.  I had regrettably assumed that since the 730a was an nvidia nforce design that it had the nvidia networking on it too.

In any case, my network is not homogenous.  I dual boot two other machines (laptop and a gaming capable machine) both of which have windows 7 64-bit and some flavor of Ubunutu/Kubuntu 10.04 right now.

The biggest problem I have for debugging this is I'm really not sure when I started getting the performance issues.  It could have been hardware related or update related.

All of the speed testing I have been doing through windows though.  And both reads and writes from the samba share appear to be around 1.2MB/s tops.  I've got the latest realtek drivers in Windows, and I've installed the realtek drivers for linux on the server.  Nothing seemed to change.

If anybody is a samba guru out there.. which log file would probably have the most useful information?  The individual client log, smbd log or nmbd log?

---

### Post by ojobson on 2010-05-20
B***er it. I've built myself a hackintosh on the atom 330 board and suddenly all is well with the world.

Cheers for the memories Ubuntu.

---

### Post by wkulecz on 2010-05-20
My 10.04 Samba is does not seem slow.

I get about 10 MB/s (540MB media file copied from W2K to Lucid via samba in about 50 seconds).  Using 100BaseTX network, although both cards are GB, the network routers here are not.

Followup:

I just verified its basically symmetrical copying the file back from samba to a different drive on W2K
was essentially the same speed, maybe a few seconds faster.  Playback of the media file on Windows from the samba share was smooth with good seeking (camcorder DV format, requires 3.6MB/s data rate for smooth playback).

---

### Post by Zathuras on 2010-05-20
Interesting.  I'm running on a relatively decent gigabit switch.  My upstream router is pretty slow but shouldn't be impacted by this configuration.

Dropping down to 100mb/s isnt really a great solution, especially if Karmic runs samba just fine at GigE.  I think I'm going to try to reinstall Karmic and see if everything works well there.

---

### Post by Zathuras on 2010-05-31
My issue is resolved.  Bad hardware on the client end.  The Realtek NIC was failing to synchronize at 1Gbps and was falling back to 10Mbs, which would make 1.2MB/s transfers seem about right.

Replaced the NIC with a PCI-E x1 Intel NIC on the client machine and everything is great once again.  10.04, Samba, and Linux in general had nothing to do with the problem.  Wish Windows 7 64 didn't do such a good job of hiding the network status information from you.  I never would have suspected that the NIC was failing to negotiate its best connection.  In the past when I had problems with NICs they usually failed completely.

---

