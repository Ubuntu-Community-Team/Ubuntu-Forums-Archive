---
title: "Method needed to share files between Xubuntu and Ubuntu"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-05
Hi.
I need to share files between Xubuntu and Ubuntu. Both are 8.10. My Xubuntu desktop is usb 1.1 so transfering many files via USB is out. I need the most straught forward method.
Should I opt for NFS or Samba? As I dont plan on connecting my Xbuntu to a Windows machine, perhaps I'd be best to try NFS?
I always use Samba for Ubuntu to Ubuntu, however the network GUI in Xubuntu is a bit differant.
Please help. Thanks.

---

### Post by dmizer on 2009-02-05
NFS is easy, I highly suggest it. Please see the fourth link in my sig for the howto on that.

If you want to share files both ways (Xubuntu to Ubuntu as well as Ubuntu to Xubuntu), you will need to configure both Xubunt AND Ubunt as both a server and a client.

---

### Post by Rytron on 2009-02-05
> **dmizer said:**
> NFS is easy, I highly suggest it. Please see the fourth link in my sig for the howto on that.

If you want to share files both ways (Xubuntu to Ubuntu as well as Ubuntu to Xubuntu), you will need to configure both Xubunt AND Ubunt as both a server and a client.

Thank you dmizer. I'll follow your guide. I'd reckon I'll make do with sending files from Ubuntu to Xubuntu only as my Xubuntu pc is not my main computer.

---

### Post by dmizer on 2009-02-05
> **Rytron said:**
> Thank you dmizer. I'll follow your guide.
No problem. Not my guide though ... I just link to it frequently because I found it to be extremely helpful ;)

---

### Post by hannuh on 2009-02-05
> **Rytron said:**
> Hi.
I need to share files between Xubuntu and Ubuntu. Both are 8.10. My Xubuntu desktop is usb 1.1 so transfering many files via USB is out. I need the most straught forward method.
Should I opt for NFS or Samba? As I dont plan on connecting my Xbuntu to a Windows machine, perhaps I'd be best to try NFS?
I always use Samba for Ubuntu to Ubuntu, however the network GUI in Xubuntu is a bit differant.
Please help. Thanks.


NFS is not very safe, Samba will work in your local network, but does not work over routed networks (Internet).
The most uptodate way to do what you want to do is SSHF
It is easier to setup and operate than NFS or Samba, yet encrypted, works over Internet etc.
With SSHFS, you can use a number of programs for file transfer, unison, rsync etc.
Start Googling SSHFS, the required programs, sshfs and fuse are in the Ubuntu repos.
Here is a link to get started with:
[http://www.dd-wrt.com/wiki/index.php/Sshfs](http://www.dd-wrt.com/wiki/index.php/Sshfs)
Hannu

---

### Post by dmizer on 2009-02-05
There's no reason to use SSHFS over a trusted network behind a firewalled internet connection. NFS will do fine for this, and will be slightly faster.

I also do not find SSHFS to be any faster to set up than NFS.

---

### Post by Rytron on 2009-02-06
I eventually went with this method:

Install Samba on both machines
Give both machines static addresses.
i.e. PC#1 = 192.168.1.2 & PC#2 = 192.168.1.3
Right click and share (tick all boxes) folder in Ubuntu
On Xubuntu machines install pyNeighborhood
Go to terminal and type in gksudo pyNeighborhood
In pyNeighborhood Edit>Add Machine then fill in required info.
In pyNeighborhood right click share and mount
The share will be in /mnt/lan/serverPCname/nameofshare

:popcorn:

---

