---
title: "Samba network transfer SLOW..."
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by Nicolice on 2010-12-14
Before that, yes I've google/search throughout this forum...can't, tried changed the duplex, everything...still the same, even reconfigured the samba config...doesn't change...

The problem:

- File transfers throughout went ok at first 10 seconds...then it drops to ...56KiB/s or slower...and that's on LAN!
- Files transfer via LAN, WIFI all the same...SLOW!

I reformatted this computer to Ubuntu 10.10, since I'm fedup with Windows XP error this that this and yeah..you know, Winbooze...anyway...

Previous configuration
[Windows XP]
- throughout network transfer [up] - 2.5MiB/s for wireless, and 11MiB/s for LAN

Current configurations
[Ubuntu 10.10]
- throughout network transfer [up] - 1.5MiB/s..for 10 seconds..then drop to 19KiB/s, for both wireless and LAN..


Any helps? Quite irritated with the problems, and I don't want to go back to Winbooz again...

Even tried setup FTP server, still the same output.

Here's my lshw -C network output
```
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0c:61:00:00:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.123.100 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e400(size=256) memory:dff00000-dff000ff


```
Any helps? :(

---

### Post by Nicolice on 2010-12-14
*bump*

---

### Post by distortedecho on 2011-01-15
I'm finding this issue also.

Samba is transferring across my LAN at 2.5mb/s
When you're working in the GB's - that's too slow! 1.8gb took 15 minutes for crying out loud :(

---

### Post by lunatico on 2011-01-17
Same here. :(

---

### Post by MikeyDL on 2011-01-27
I've noticed the same thing.  Network file transfers on my ubuntu system are 1 to 2MB versus 15MB p/sec on any of my windows systems.

---

### Post by ByteTraveler on 2011-02-10
I'm having what appears to be the same problem here. Just getting my feet wet with Ubuntu on a Windows (7) network with four Windows (7) machines, which can move files amongst themselves at an impressive pace.

Transfers to/from the Ubuntu box, however, always hover around 1M/sec... Horrendously slow.

The Ubuntu box is running the same Linksys wireless card as the Windows boxes, so there's really no networking hardware differnce.

Hoping someone chimes-in with some suggestions.

---

### Post by mikewhatever on 2011-02-10
[https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

Thanks google, how wonderful.

---

### Post by kookies on 2011-02-21
I've been experiencing the same problem (like 1000's of others according to google) I tried all of the advice internet searches had to offer to no avail. What i've found out is that if i leave the ubuntu server at the login prompt i get 50mb/sec+ transfer rate over smb. If however I login on the server the transfer rate tops out around 1mb/sec. This obviously isn't a "fix" it is an acceptable workaround for me, but a piece of the puzzle for anyone actually working on the problem.

---

### Post by lunatico on 2011-02-22
> **kookies said:**
> I've been experiencing the same problem (like 1000's of others according to google) I tried all of the advice internet searches had to offer to no avail. What i've found out is that if i leave the ubuntu server at the login prompt i get 50mb/sec+ transfer rate over smb. If however I login on the server the transfer rate tops out around 1mb/sec. This obviously isn't a "fix" it is an acceptable workaround for me, but a piece of the puzzle for anyone actually working on the problem.

Lucky you! I would be perfectly happy with that workaround... but doesn't seem to be working for me.
If I leave it at the login screen or even if I stop GDM I still get slow speeds. This is what I get:

Download from samba
~150KB/sec

Upload to samba
~700KB/sec

Me sad. :(

---

### Post by dmizer on 2011-02-22
How are you connecting to your samba shares?

Using /etc/fstab will significantly improve speeds. If you're interested in attempting that, please see the 2nd link in my sig. You may also find better results if you follow the fixes posted in the 6th link in my sig.

---

### Post by kookies on 2011-02-22
> **lunatico said:**
> Lucky you! I would be perfectly happy with that workaround... but doesn't seem to be working for me.
If I leave it at the login screen or even if I stop GDM I still get slow speeds. This is what I get:

Download from samba
~150KB/sec

Upload to samba
~700KB/sec

Me sad. :(

I should have added I'm using a command line only installation.

---

### Post by lunatico on 2011-02-23
> **dmizer said:**
> How are you connecting to your samba shares?

Using /etc/fstab will significantly improve speeds. If you're interested in attempting that, please see the 2nd link in my sig. You may also find better results if you follow the fixes posted in the 6th link in my sig.

Sorry, I didn't explain enough.

I have an Ubuntu 10.10 which has a few shares, it acts as a file server. I connect to this shares from other computers (Windows and Linux).
I needed password-less read/write shares and the only way I managed to get this working was simply by right-clicking the folder to share -> Sharing Options -> Share this folder and selecting the two options for read/write and guest access.
I spent an entire day trying to configure samba via it's config file (both in Ubuntu and Fedora) but couldn't ever get it to work properly.

So I connect to this file server from all over the network, no specific workgroup and no specific domain (it's a big and complex network with many vlans, workgroups and domains). But I always get this unusable slow speeds.... I while ago this used to be ok, I think it was back in the 9.04 days...

---

### Post by lozt.again on 2011-02-28
> **mikewhatever said:**
> [https://calomel.org/samba_optimize.html](https://calomel.org/samba_optimize.html)

Thanks google, how wonderful.

Although you can also use google to find out that isn't the fix. Cheers!

> **kookies said:**
> I've been experiencing the same problem (like  1000's of others according to google) I tried all of the advice internet  searches had to offer to no avail. What i've found out is that if i  leave the ubuntu server at the login prompt i get 50mb/sec+ transfer  rate over smb. If however I login on the server the transfer rate tops  out around 1mb/sec. This obviously isn't a "fix" it is an acceptable  workaround for me, but a piece of the puzzle for anyone actually working  on the problem.

That's interesting... off to try! Not a fix for me either, as other people on my network will not be willing to go that route.

EDIT: Yeah... not for me, still starts promising, then creeps down to 6mBps.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-28
Hi,
 what speed network are you using?
 54mbps?
 100mbps?
 Gigabit?

Theres several options in smb.conf to help speed samba access up, but they vary between different setups.

---

### Post by lozt.again on 2011-02-28
1gigglebit!!!

---

### Post by teandryk on 2011-11-02
got same problem, I almost try all "solutions" I found on net none of them working :(
any update on that since February, any general solution without going into details of my system?

---

### Post by RottenMutt on 2013-02-15
i was hoping this thread would end with a solution. 

my NAS only chugs along at 24MB/s, the raid5 array only gets hit about every 30 seconds at about 175MB/s.  so problem isn't the drives, almost seems like their is load sharing going on...

---

### Post by Sef on 2013-02-15
closed. Necromancy. Start a new thread and link to here, if you want to reference this thread.

---

