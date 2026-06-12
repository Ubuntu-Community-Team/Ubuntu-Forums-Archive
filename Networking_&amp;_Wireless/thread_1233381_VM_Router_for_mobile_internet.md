---
title: "VM Router for mobile internet"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by Disco Elephant on 2009-08-06
Hi, I'm new here, and this is my first post (like you haven't heard that before). I'm trying to do something that's a little unusual, and am running into an endless list of difficulties. So I thought I'd ask for some advice here. 

I want to build a router for my mobile internet connection, but I want to run it in a VMWare virtual machine. I want to share the internet connection from my 3 mobile modem to other VM machines, and to a physical network (using the NIC in my laptop).

The modem is a HUAWEI E156G. Ubunutu version 9.04, running on a VMWare Workstation Version 6.5.2. All of this is running on an ASUS A6000 series laptop.

When I first installed ubuntu in a VM, I was able to configure this modem using GNOME, however, after I upgraded the VM using the upgrade tool in GNOME, it nolonger connects to the mobile network. However, what I really want to do is to run the router in text mode, without the overhead of a GUI. I've already worked out how to make the router boot into text mode.

So, my questions are:

1. How can I get the modem to connect to the mobile network from within text mode (preferably when the machine boots)?

2. How can I configure IPTables to route packets from the modem to my network card (which is configured as eth1) and to the virtual network (which hangs off eth0)?

NOTE: I do have a basic understanding of IPTables, and can configure it to route packets from eth0 to eth1, etc. I just don't know how to set the rules for the modem. 

Any help would be much appreciated.

---

### Post by Disco Elephant on 2009-08-07
BUMP.

Anyone able to shed some light here?

---

### Post by Disco Elephant on 2009-08-08
> **Disco Elephant said:**
> BUMP.

Anyone able to shed some light here?

Perhaps if I simplify the question. Can anyone tell me how to get my modem to connect using the command line rather than the GUI?

---

### Post by Disco Elephant on 2009-08-08
Never mind. I worked it out for myself. 

Thanks to all those that responded. :rolleyes:

---

