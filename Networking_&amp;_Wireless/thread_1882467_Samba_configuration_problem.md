---
title: "Samba configuration problem"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by r_avital on 2011-11-17
Hello,

I need assistance with the following problem:

3 computers are involved, and the problem is all inside my LAN, not on the internet.  Let's call the machines Lucid1, Lucid2, and Win7.

Lucid1 and Lucid2 are both running Lucid 64 Bit, 2.6.32-35-generic, Gnome 2.30.2.
Win7 is running Windows 7, and I have a user account with login/password, and a few shared folders.

On Lucid1
From both nautilus and dolphin, I see the following (trying to represent as a tree):

Network
.Network
.Samba Shares
..WorkGroup
                                                   ...Win7
                                                   ...Lucid1
...Lucid2
.Add Network Folder

On Lucid2, I see:
Network
          .Network
.Samba Shares
                                 ..WorkGroup
                                                   ...Lucid1
...Lucid2
.Add Network folder

In other words, there is a discrepancy because Lucid2 does not connect to Win7.

**However,** on Lucid2, from the Places menu, using Connect to Server, I can enter the IP address of Win7, and I'm immediately prompted for a login (to Win7), and I get access to my shared folders on Win7.  This fails if I enter the server name, but works with the IP address, but this is a side issue.

On both Lucid machines, I've confirmed in Synaptic that the exact same Samba packages are installed.

What am I missing on Lucid2?

It would also be nice to know if I could use the server name (Win7) instead of the IP address, but that's secondary for now.  If I can make the connection from dolphin or nautilus, I probably won't be using the tool in the Places menu.

Please, any ideas.

Thanks in advance.

---

