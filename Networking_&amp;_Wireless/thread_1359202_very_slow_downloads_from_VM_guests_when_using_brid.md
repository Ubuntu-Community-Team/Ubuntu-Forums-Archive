---
title: "very slow downloads from VM guests when using bridged networking"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by mrtwice99 on 2009-12-19
I have an xubuntu 9.10 machine running as a virtualization host. I am having problems when network clients download from the guest. This only happens when the VMs use bridged mode networking. If I use NAT, then the speeds are fine.

Note that its only network clients downloading from the guest that is slow. Everything else has expected speeds. Speeds are ("net" = client computer on the local gigabit network):

host <- guest: 66 MB/s
guest <- host: 36 MB/s
host <- net: 63.4 MB/s
net <- host: 50 MB/s
guest <- net: 25 MB/s
net <- guest: 1 MB/s

This problem occurs with vmware guests and virtualbox guests, which makes me think this is some kind of problem with my networking setup/hardware than a problem with my VMs.

I have tried the following, all without any change in the problem:

* multiple network clients
* added a different gigabit NIC to the host and bound vm bridged network to that interface
* tried doing the transfer on port 8080 instead
* tried briding the VM nic to a different NIC than what the host is using for most communications (i.e. I had two network cables plugged in)

I also tried installing an ubuntu server guest.  When I did that, download speeds from the guest were correct.

---

### Post by mrtwice99 on 2009-12-20
After installing multiple flavors of ubuntu as well as slackware on three different machines and seeing the same problem occur each time, I finally hit on something. The problem was only apparent when it is a Windows 7 guest and a windows network client. If either the guest or network client is linux, then I don't have the problem.

Not sure what else to do, so I filed a bug with virtualbox:

[http://www.virtualbox.org/ticket/5812](http://www.virtualbox.org/ticket/5812)

Although I think it quite odd that vmware has the same problem. Throughput between native windows clients on my network is not that slow.

---

