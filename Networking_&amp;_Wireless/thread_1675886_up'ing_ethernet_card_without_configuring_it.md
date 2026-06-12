---
title: "up'ing ethernet card without configuring it"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by Brazilian Joe on 2011-01-26
Hi all,

I have a machine running Ubuntu 8.04 with several VMs which I want to migrate to a 10.10

My network infrastructure is virtualized. 

In the old system I have two NICs which I turn up but do not configure on the host, to let the virtual machines use exclusively for my PPPoE connections. 

I use the following code on  /etc/network/interfaces:

```
...
auto eth1
iface eth1 inet manual
auto eth2
iface eth2 inet manual
...
```

The NICs come up without any IP addresses and show up on ifconfig without problems. As the VMs come up, they dial the PPPoE and I have internet.

In Ubuntu 10.10, this does not work. eth1 and eth2 never come up, and thus my VMs can't do the PPPoE connection, despite having this same config in /etc/network/interfaces.

I can 'ifconfig eth1 up' and then my VMs will dial PPPoE in 10.10, but that's a manual thing, I need it to happen automagically. 

If anyone can share some insight on how to do it in 10.10, I'd appreciate it. I would like to configure it from the CLI, not using the GUI Network Manager.

Thanks

---

### Post by dmizer on 2011-01-26
If you are trying to do this from the CLI with /etc/network/interfaces, then you'll have to remove the "network-manager" package, as the GUI configuration tool interferes with the CLI tools.

---

### Post by Brazilian Joe on 2011-02-03
Well, I have removed network-manager and dependencies, but the cards are still not coming up. any ideas?

---

### Post by SeijiSensei on 2011-02-03
Remove the entries from the interfaces file and add these lines to /etc/rc.local:

ifconfig eth1 up
ifconfig eth2 up

They should be there when the boot is finished.

---

### Post by dmizer on 2011-02-04
> **Brazilian Joe said:**
> Well, I have removed network-manager and dependencies, but the cards are still not coming up. any ideas?

It could be that your interface names have changed. Please post the output of:
```
lshw -C network
```

---

