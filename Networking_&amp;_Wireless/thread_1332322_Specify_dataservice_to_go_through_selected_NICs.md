---
title: "Specify data/service to go through selected NICs"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Crashinit6 on 2009-11-20
Hi everyone.

I was wondering if this scenario is possible.

I have Ubuntu server installed with two Nics. Backuppc is installed on it. 
The way backuppc is meant to be used is to store the backups on a local partition but the server's drive capacity is not large enough so I want to use the NAS server as the backup drive. I will be mounting this share on the backuppc server with fstab.

I want to backup data from the file server to the NAS server which is separate to the Backuppc. I was just wondering if it was possible to only allow incoming traffic from the file server on Nic 1 and tell backuppc to use Nic 2 to connect to the NAS server thereby preventing saturating the bandwidth by just using one NIC.

Is this a viable option?
Any help will be much appreciated.

Thanx

---

### Post by t0mppa on 2009-11-20
> **Crashinit6 said:**
> I was just wondering if it was possible to only allow incoming traffic from the file server on Nic 1 and tell backuppc to use Nic 2 to connect to the NAS server

Yes, this is possible to achieve. And a fairly simple configuration in itself. However, what adds up the complexity is if you also want other network transactions to take place as well. So, perhaps you could share a bit more of your idea towards the general network topology. Do you also need access to local network and/or Internet and if so, through which NIC would that happen?

> **Crashinit6 said:**
> thereby preventing saturating the bandwidth by just using one NIC

Also would both NIC's be connected to the file server through a local network? If so, then simply having traffic in on one NIC and out on the other doesn't really make things any faster, if you're reaching max throughput of the network. That is, you can't both receive traffic on one NIC at 10 Mb/s and send on another at 10 Mb/s, if your switch can only handle 10 Mb/s of traffic (and not the 20 Mb/s, you'd need to achieve the above). If your switch can handle 100 Mb/s and the NICs only 10 Mb/s each, then it naturally speeds things up.

---

### Post by Crashinit6 on 2009-11-20
Hi t0mppa,

Thanx for the quick responce.

It seems with my current configuration it would not have made a big difference as the File server and Backuppc Server are on our gigabit backbone, each with gigabit Nics while the NAS unit is running at 100Mb/s. So the bottle neck would in anycase be the NAS server. The Gb Nick would be able to then handle this without any problems. 

As you also mentioned what other services would be needed for the backuppc server? Short answer is a lot.

Thanx again for the reply.
It is much appreciated.

---

