---
title: "Ubuntu 10.04 NIC Bonding with balance-alb causing MAC Flapping"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by smooter on 2010-10-08
Hello all,

I am currently running Ubuntu 10.04, and it is working great. I have setup NIC Bonding, and it to went in without a hitch.

However, I noticed that I am having some "MAC Flapping" issues on my Cisco switch, and some quick research leads me to believe it is due to the Bonding mode I have my NIC's in.

I am running mode=6 or Balance-ALB. This is by far the best mode to run, as it requires no additional configuration on the switch side of the communication. However, after much research I notice that the NIC driver that is running on the host "must support changing the hardware address while the device is open". I am running this Ubuntu Server on a SuperMicro server that I have repurposed, and the NIC's that are running on this server are dual Intel 82546GB Gigabit controllers.

After trying to configure the bonding myself, and failing miserably, I found the following blog post that got me as far as I am now: [http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly](http://blog.brightbox.co.uk/posts/howto-do-ethernet-bonding-on-ubuntu-properly)

As I said, the bond is up and running but I must be missing some other config. I am NOT a Linux guru, but I am not lost either. Bonding is a new thing on the Linux platform for me, I will admit that.

What I am actually trying to do is:

1. Find out what options (if any) I have left out of the configuration that will correct this issue.

2. Figure out how to confirm whether the drivers that are installed support the requirement of "changing the hardware address while the device is open".

3. Provide the completed solution to the community so others can successfully bond their Ubuntu Servers in this mode.

Thanks for your help!

smooter

---

### Post by relay_man on 2010-10-09
I'm not 100% sure what you mean by mac flapping, but as far as getting things configured for bonding in Linux I found this:

[http://www.howtoforge.com/nic_bonding](http://www.howtoforge.com/nic_bonding)

and this:

[http://useopensource.blogspot.com/2010/02/linux-nic-teaming-recommendations.html](http://useopensource.blogspot.com/2010/02/linux-nic-teaming-recommendations.html)

I'm just beginning to learn about this myself.  I hope the links may be of some use to you.

---

### Post by mr_Frank on 2011-02-02
Hi, 

I'm having strange issues with mode 6 too.......

in detail, 
I've  couple of server with 10.04, it's an hp proliant with 6 nics (4 on main bd using broadcomm chipsets, 2 on pcie using intel chipsets)
I've initially configured 2 bonds and a stand alone nic, 
knowing a previously existing problem with intel drivers I've updated the e1000e driver....
the bonding scheme was planned to give best performances and redundancy to the units (it's a cluster with drbd replication providing samba services, apache and mysql based on pacemaker/heartbeat services)
eth0 to eth3 was the main bd nics, eth4 and eth5 was on the pcie card....

the original bonding scheme was 
eth0+eth2+eth5 --> bond0
eth3+eth4 --> bond1
eth1 stand alone for pacemaker/heartbeat

bond1 is configured as mode1 to provide redundancy for drbd replication (someone knows better way to increase performances without loosing stability?!?! suggestins are well accepted!!)
bond0 needs to be  configured as mode6 for performance/redundancy on public network

at server restart, the kernel crashes, the only way to resume is starting with cd in repair mode and change the setting for bond0 back to mode0

i've supposed the driver mixing was the origin, so changed the bonding scheme to meet drivers each other...
eth0+eth2+eth3 --> bond0 (all broadcom cards)
eth4+eth5 --> bond1 (all intel cards)
this setting makes my redundancy go low because both drbd replication channels are on the same card, so in case of bus/card failure i'll loose the channel  redundancy!!!
but the issue is appearing again in a few seconds after reboot, same solution, restart in rapair mode and change bonding mode back to mode0.....

searching on the web i've found this link:
[https://bugs.launchpad.net/bugs/670547](https://bugs.launchpad.net/bugs/670547)

i think my issue may be related......

someone more able than me may help??
thanks in advance, 
regards, 
Francesco

---

### Post by mr_Frank on 2011-02-10
Hi everyone......

problem was solved installing a new kernel as supposed in this article:

> The problem is with the bonding kernel module. I believe that this issue
> has been resolved in 2.6.35 with the following commit:
>
[> http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=d8190dff018ffe932d17cae047c6b3d1c5fc7574]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=d8190dff018ffe932d17cae047c6b3d1c5fc7574")
>

I've done this on the servers:

sudo apt-get update
sudo apt-get install linux-image-2.6.35-23-generic
sudo apt-get install linux-headers-2.6.35-23-genric

then changed the bonding mode setting in /etc/network/interfaces back to 6 (ALB), 
reboot the server.....

all seems to be working fine........
server performances improved in file transfers....

hoping to be helpful for you, 
kind regards, 
francesco

---

