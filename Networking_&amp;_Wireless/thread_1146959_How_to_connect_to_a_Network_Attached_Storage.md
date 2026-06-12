---
title: "How to connect to a Network Attached Storage?"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by neogeek on 2009-05-03
Hi,

I have a Linksys NAS attached to my wireless router / network. How do I connect to it on Ubuntu/ Linux? I would appreciate any help with this issue. Thank you!

:KS

---

### Post by tonyyarusso on 2009-05-03
The exact process will depend on the protocol you'd like to use (and is supported by your model of NAS), but generally speaking if you're using Gnome you should be able to get at it with Places > Connect to Server, then select the protocol and any authentication details along with the network address assigned to your NAS device.

---

### Post by rgotten on 2009-05-12
what if i am using a server edition of buntu, how do i connect tot he NAS

---

### Post by Carl Hamlin on 2009-05-12
> **rgotten said:**
> what if i am using a server edition of buntu, how do i connect tot he NAS

I'd try telnetting to the IP of the NAS.

---

### Post by tonyyarusso on 2009-05-13
> **rgotten said:**
> what if i am using a server edition of buntu, how do i connect tot he NAS

In that case it would be helpful to know which type of protocol your NAS supports / you wish to use, as the procedure will vary with that.  Your options are probably listed on the box of the NAS device (or in the web control panel for it if that applies).  Alternatively you could guess them by doing an NMAP scan of open ports on the device...but that seems a bit overkill.

SSH or NFS access will by far be the simplest to set up if your device supports it.  Samba will be doable, but is a bit more of a pain to configure.

---

### Post by Peter09 on 2009-05-13
Most  NAS will provide a windows share, which means you will need to access the NAS through Samba. 

A Samba client is normally installed by default in Ubuntu, so you should be able to see your NAS in the network as a windows device.

---

### Post by rgotten on 2009-05-20
> **Carl Hamlin said:**
> I'd try telnetting to the IP of the NAS.

How do i telneeting to the ip address thru putty?

---

### Post by Iowan on 2009-05-20
From PuTTY, Telnet is a radio button. The address goes in the box just above it.

---

### Post by Carl Hamlin on 2009-05-20
> **rgotten said:**
> How do i telneeting to the ip address thru putty?

Just open a terminal and type:

```

telnet 000.000.000.000

```

where 000.000.000.000 is the ip address of the NAS.

---

