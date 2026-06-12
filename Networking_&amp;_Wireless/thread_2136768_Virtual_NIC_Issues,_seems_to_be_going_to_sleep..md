---
title: "Virtual NIC Issues, seems to be going to sleep."
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by tommyfarnworth on 2013-04-18
Very annoying problem with what seems to be a virtual NIC going to sleep.

I have a Ubuntu 12.04 running in a VMware VM on ESXi v5.0, one single virtual NIC.
This runs only Apache2 and PHP5, one single website.

This ran for almost 2 years flawlessly until I moved this VM to a new ESXi server in another datacenter.
In the new datacenter it ran for a month or more fine, then suddenly I would lose SSH access and the web would not respond. Sometimes it would just suddenly all come back on and work fine.
A reboot fixed it, but I need a better solution. 

I've been trying to figure this out for several days now, lots of Googling and searching, but no solutions yet.

Since this is a VM I can log into it from the vCenter console when it becomes inaccessible. Running a simple ping to an external location restores the connectivity.
I put in a simple cron to ping out every 15 minutes for 10 returns to see if that would help and so far it does seem to be helping. It lost connectivity before the 15 minutes came around, but then the cron did bring things back. 

There are a dozen other VMs running on this same ESXi host and they are using the same physical NIC without this issue.

Seems there should be a more basic solution. I would appreciate any help on this.

Thanks,

Tommy

---

### Post by ewren on 2013-05-29
Hi,

Did you ever get to the bottom of this issue?

I have a Ubuntu 12.04 server running in ESX the NIC seems to go to sleep after a couple of minutes of no activity. The only way to bring it back up is to use the VSphere console to access the machine, an then ping an external address. The first few attempts fail and then the network comes back up.

I have several other Ubuntu VM's running and none of them have this issue. Interested to hear if you ever got to the bottom of it.

Thanks!

---

