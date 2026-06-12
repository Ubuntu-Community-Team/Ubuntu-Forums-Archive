---
title: "SAMBA file copy speed between 2 Ubuntu machines."
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by kamiller42 on 2012-09-14
I have Ubuntu on a notebook and a desktop. With each connected to the same switch, I am seeing transfer rates of 17.5MB/s. All elements in the link are gigabit. 

This speed doesn't seem normal. Am I wrong? How can I speed it up?

The desktop uses a Realtek RTL8111/8168B PCI Express controller.
The notebook uses an Intel Centrino Wireless-N 1000. It's a Dell XPS17.

---

### Post by critin on 2012-09-14
> **kamiller42 said:**
> I have Ubuntu on a notebook and a desktop. With each connected to the same switch, I am seeing transfer rates of 17.5MB/s. All elements in the link are gigabit. 

This speed doesn't seem normal. Am I wrong? How can I speed it up?

The desktop uses a Realtek RTL8111/8168B PCI Express controller.
The notebook uses an Intel Centrino Wireless-N 1000. It's a Dell XPS17.

You're using Samba, so the computers are connected through a lan/wan.  Can't you just move the item from one folder to the other through file manager?

I just moved an iso in about 4 seconds from windows download to ubuntu download.   You're not just moving something, what are you transferring?

Have you checked the wireless connection?  I don't use wireless, (don't like it) it may not be getting good reception.

---

### Post by kamiller42 on 2012-09-14
> **critin said:**
> You're using Samba, so the computers are connected through a lan/wan.  Can't you just move the item from one folder to the other through file manager?

I just moved an iso in about 4 seconds from windows download to ubuntu download.   You're not just moving something, what are you transferring?

Have you checked the wireless connection?  I don't use wireless, (don't like it) it may not be getting good reception.
I copied the files through Nautilus. I have a network share mounted and am copying there.

While the notebook is a Centrino, it is a wired connection to the switch. Both computers are wired through a gigabit switch.

What speed should I see?

---

### Post by cjhabs on 2012-09-14
> **kamiller42 said:**
> I copied the files through Nautilus. I have a network share mounted and am copying there.

While the notebook is a Centrino, it is a wired connection to the switch. Both computers are wired through a gigabit switch.

What speed should I see?

Here are some notes I made a while back when I was testing some file transfer speeds - maybe some of this will be useful to you:
-----
Test 1
From:    Ubuntu - 9.10 - HP Pavilion dv5-1235dx laptop - wireless
To:    XP SP3 - Dell Optiplex 170L - wired
What:    100mb file
Time:    180s
Notes:
Using Netgear router WGR614 v5
-----
Test 2
From:    Ubuntu - 9.10 - HP Pavilion dv5-1235dx laptop - wireless
To:    Solaris 9 - Sun Blade 150 - wired - via smb (Samba)
What:    100mb file
Time:    180s
Notes:
Using Netgear router WGR614 v5
Installed nfs client on the laptop and mounted the nfs filesystem
Exactly the same speed as test 1 - I was expecting faster - should try both with the laptop wired.
-----
Test 3
From:    Ubuntu - 9.10 - HP Pavilion dv5-1235dx laptop - wireless
To:    XP SP3 - Dell Optiplex 170L - wired
What:    100mb file
Time:    110s
Notes:
Using router Linksys WRT54GL
Some as test 1 but with the Linksys router replacing the Netgear router - 39% faster!
-----
Test 4
From:    XP SP3 - Dell Optiplex 170L - wired
To:    Solaris 9 - Sun Blade 150 - wired - via smb (Samba)
What:    100mb file
Time:    238s
Notes:
-----
Test 5
From:    Solaris 9 - Sun Blade 150 - wired - via NFS
To:    Solaris 9 - Sun Blade 150 - wired - via NFS
What:    100mb file
Time:    19s
Notes:
All NFS transfer using scp (secure copy)
-----
Test 6
From:    XP SP3 - Dell Optiplex 170L - wired
To:    Windows Server 2003 - Dell PowerEdge 1800 - wired
What:    100mb file
Time:    360s
Notes:
Using URI destination address - i.e. \\192.168.33.26\share
Slow!
No difference using a mapped drive.
-----
Test 7
From:    XP SP3 - Dell Optiplex 170L - wired
To:    Windows Server R2 - Dell PowerEdge SC1430 - wired
What:    100mb file
Time:    > 360s

---

### Post by SeijiSensei on 2012-09-14
Use rsync from the command prompt instead of samba.  Type "man rsync" at a prompt for details.

If you want to create a permanent share, use [NFS]("https://help.ubuntu.com/community/NFSv4Howto").  For best performance, include the "async" option on the server.

Samba only makes sense between Linux servers and Windows clients.  For *nix-to-*nix transfers use NFS, sshfs, or rsync.

---

