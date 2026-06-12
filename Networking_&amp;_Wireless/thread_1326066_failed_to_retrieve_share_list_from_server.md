---
title: "failed to retrieve share list from server"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by josh_moore on 2009-11-14
I have searched several threads though circumstances of the error seemed different and suggestions in those threads are based on those circumstances and results.

From my netbook running Ubuntu 9.10 Desktop I cannot access my computer running Windows 7x64. However, I have several other systems running either Vista or Ubuntu. All of these systems have shares and my netbook can access them without issue. Those other systems can access the shares on my Windows 7 system

All systems are in the same network
All systems are using static IP
All systems are using hosts file to specify IP/computername
No firewalls are running on any systems

When browsing Network from the places menu, I can see all of my systems, including the Windows 7 system. When I attempt to open that I am asked for user and password. I have the same user/pass on the netbook as I do my Windows 7 system, and also on the other systems, after entering the user/pass I get error
Unable to mount location
Failed to retrieve share list from server

I can ping the system in question
The command smbclient -l <computername> results in the following

Domain=[computername] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D$              Disk      Default share
        Downloads       Disk
        IPC$            IPC       Remote IPC
        Movies          Disk
        Users           Disk
        Z$              Disk      Default 


However, I can edit /etc/fstab and then run mount -a and access a share
//computername/Downloads    /mnt/downloads          smbfs   credentials=<smbpasswd file path>       0 0

Any suggestions would be greatly appreciated

---

### Post by Iowan on 2009-11-14
I presume you've already come across [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To.

---

### Post by josh_moore on 2009-11-15
All of the problems outline in that article do not apply. 
As mentioned in my post, all of the systems are in the same workgroup, I have configured my hosts file and the firewalls are turned off. The Linux system that cannot browse the W7 machine, can browse other Windows and Linux systems, and another Linux system can browse the W7 machine.
Configuring fstab to mount a specific share works, browsing with (i believe) Nautilus is the only place affected.

---

### Post by StuartN on 2009-12-11
> **Iowan said:**
> I presume you've already come across [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To.

Many thanks for this thread, specifically this bit worked for me:

> Open /etc/nsswitch.conf for editing with the following command:
```
gksudo gedit /etc/nsswitch.conf
```
Find the line that looks something like:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
For this line, order IS important. You’ll need to add the “wins” option before dns, so the line reads like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```

I have no idea why, but my system was working absolutely fine without this entry. Then network browsing disappeared. The only recent changes to my system are regular updates, and I have switched DNS servers in my network manager because my ISPs servers have been extremely intermittent recently.

---

### Post by StuartN on 2009-12-13
And this being the way the world works, of course fixing one thing breaks another.

After altering the hosts order to get my network discovery functioning again, I get a segmentation fault in liferea. I just reordered them to **hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 _wins_** per this Launchpad bug report: [https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/215016](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/215016) and have both liferea and network browsing.

---

