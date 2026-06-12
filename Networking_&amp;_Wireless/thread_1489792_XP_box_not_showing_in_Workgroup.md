---
title: "XP box not showing in Workgroup"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by dkh503 on 2010-05-21
Trying to get my XP machine (hostname muddy) to show up on my network. The machine is clearly on the network and communicating  with my Ubuntu 10.04 machines and my Vista machine, I just can't get an icon to appear to represent the XP box the like the other boxes do. This isn't killing me, I can share files, connect to it as a server, etc,  its just annoying that it is not showing up in nautilus like the other machines.  

Not sure if this has something to do with it, but I noticed that when I run

sudo smbclient -L muddy

it reports 'Domain=[MUDDY]'. All my machines are set to be a member of [WORKGROUP], and I have double and triple checked, as administrator, to be sure that muddy has also been assigned to my workgroup called WORKGROUP. When I run smbclient -L to search for any of my other boxes, it reports 'Domain=[WORKGROUP] for all of them, including my Vista laptop.

My XP box is on SP3 and I even installed the LLTD hotfix from MS that was supposed to solve this problem, but to no avail. Any advice appreciated.

dkh

---

