---
title: "Samba transfers lock computer up"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by bond00 on 2006-06-11
This is kind of a weird problem, but for some reason my server locks up whenever I copy files from it through SMB on another computer. I can't seem to isolate the problem any more than that, but it doesn't seem to occur with any other service/protocol. I don't know much about the /var/logs so maybe some insight there could provide a bit more information about the root of the problem. While I'm at it, does anyone have any good tools to make log monitoring a bit eaiser/organized? Thanks in advance.

---

### Post by TigerWolf on 2006-06-12
I also have this problem - it seems as though the computer has problems with more than once connection, it locks up not only on samba (when two people try to access) but also when I upload stuff to it on ftp. This is a big issue as I dont want to have to keep restarting it. Any help on this?

Yes - it seems to be just any 2 seperate connections to the box locks it up and makes it completely useless. Firestarted is not installed on either. Samba connection or ftp connection or vnc connection - any two and computer needs to be restarted.

---

### Post by bond00 on 2006-06-12
I think you're right...that's what my problem is too. I made two SSH connections and after about 5 seconds, the server locked up. Does anyone have any idea what the problem could be? This is very annoying.

---

### Post by TigerWolf on 2006-06-12
Could I get some info on what hardware your using so that we can compare to possibly find out what we both have in common. 

MSI motherboard, AMD Processor, Dont know brand of network card but its currently using the NC100 Network Anywhere Driver (vendor Linksys) - Its a standalone network card.

---

### Post by bond00 on 2006-06-12
Exactly what I was thinking...I'm not at my computer now. I'm out of town and I would log into it...but IT'S LOCKED UP! If I remember correctly:

ASRock Motherboard
Pentium 2.8 Processor
1 GB Ram - I've tried multiple RAM sticks so it's not that
Network Card - entirely unsure, but I would guess a Realtek just because that seems to be the most popular for built on NICs.

I'm not sure what you've tried, but I've reformatted several times. ONE more question though. Do you by chance have a RAID configuration that you're accessing the files from when the computer locks up? I thought maybe that's what my problem was, but not sure. I have a RAID 5 configuration. Thanks for the help...

---

### Post by TigerWolf on 2006-06-13
No it cant be RAID. Im running one HDD on PATA. Doesnt look like a hardware issue as ours are quite different. Are you using any sort of remote desktop utility like VNC? Did you install with live or alternative CD? Are you using an ftp server?

---

### Post by bond00 on 2006-06-14
I wasn't using VNC or any similar tool...besides SSH, which did cause it to lock up. I installed the OS with the live cd and am also not using an FTP server. What else could it be...do you use samba, SSH, or apache? Did you have this problem with breezy? Also do you know the exact conditions that cause your computer to lock up? I haven't been able to narrow it down too much, but I know it locks ALOT and it seems to be when transferring files either through SSH or samba. 

No one else is having this problem? I'm starting to look for other distros because I can't have my server locking up constantly...or maybe i should go back to breezy...

---

### Post by TigerWolf on 2006-06-14
This is what I have found. It doesnt like multiple connnections no matter what it is, be this samba or ftp or any other sort of transfer that uses all of the speed. So seriously no body else has any problems with this at all or can offer any help whatsoever?

---

### Post by stego_s_aurus on 2007-01-18
Greetings!

I Too am having lockup problems with Samba: on Both of the Ubuntu machines that I am working on for that matter! And it seems to be something with Samba' Setup, as both machines are completely different distro versions but are both experiencing the same behavior!

Machine #1: Dell Inspirion 7500, PIII, 256MB Mem. 700mhz, Ubuntu Dapper

Simple machine, fairly old, its a brick, but reliable. The configuration is simple, and matches my configuration that I set up on my 6.06 Ubuntu Server at my office:

> [global]
workgroup = WORKGROUP
netbios name = Computer
server string = Computer
security = SHARE
guest account = myaccount
log file = /var/log/samba/log.%m
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
preferred master = Yes
wins support = no

[Shared]
comment = My Shared Files
path = /home/myaccount/Shared_Folder
read only = no
create mask = 0777
directory mask = 0777
guest only = yes



Machine #2: Gateway Laptop model MA3 (just gotten this month): AMD64 Turion, 512MB Memory, 60GBHDD, Ubuntu Edgy

At first I set this machine up with the exact same setup as mine (changing names to fit the computer, of course). Sadly, It locked up as I tried accessing it from a Windows machine. I just recently followed this post on setting up Samba on the Gateway laptop, in hopes that I was missing something in my setup, but alas it STILL locked up... [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


Its driving me NUTZ!! ](*,) ](*,) ](*,)

---

