---
title: "No remote connection (RDP) on bridge"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by DC80 on 2012-10-10
Hi all,

I would like to know how I can connect to a virtual machine in a local network. I've tried almost anything to solve this. Maybe I overlooked something. I'd like to connect to a windows guest using RDP.

My setup is as follows:

**Server:**
Ubuntu Server 12.04.1 LTS (192.168.0.150)
Installed on it: KVM

**Client:**
Linux Mint 13 (Maya) LTS (192.168.0.155)

**Virtual guest**
Windows 7 (SP1) (192.168.122.148 )

So my network is like this:
Server: 192.168.0.150
Client: 192.168.0.155
Bridge: 192.168.122.1

All of them are in the same subnetmask 255.255.255.0

The virtual guest has an internet connection but it does not allow me to make a RDP connection.

I already disabled both firewalls (client and server), also added a rule to allow port 3389 in both firewalls. Also checked the windows settings (remote desktop and remote assistance are allowed). Still no connection, so can someone help me with this?

I thank u very much in advance!

Kind regards

DC80

---

### Post by daz1uk on 2013-03-05
I'm in exactly the same position, did you figure out how to do this?

---

