---
title: "Multicast forwarding between 2 NIC adapter and Linux Kernel issue"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by mirandien on 2011-06-03
I am trying to receive multicast data packets from a multicast router to my Linux Ubuntu Desktop Workstation. The Linux Desktop has an Intel 82576 dual NIC adapter. Each NIC is configured to receive IP data from 2 different subnet. One from 172.30.8.xx and another one from 10.0.xx.xx. Multicast IP data can only be received from 172.30.8.xx since there is no multicast source on subnet 10.0.xx.xx and IT that administrates the subnet 10.0.xx.xx disabled multicast capability of the switches and routers sitting on that subnet. The subnet 172.30.8.xx has a multicast source broadcasting on multicast group 239.255.200.200:8000. 

I am using the application mreceived (version 2.2) from : [http://www.cs.virginia.edu/~mngroup/software/]("http://www.cs.virginia.edu/%7Emngroup/software/") to test the network multicast set-up and capability of my Ubuntu Desktop Workstation. 

I open a first console and I use mreceive to join multicast group 239.255.200.200:8000 to receive multicast data from subnet 10.0.xx.xx using the console command : ./mreceive -g 239.255.200.200 -p 8000 -i 10.0.9.164 to the eth0 adapter of my workstation. The application is idle and no multicast data is received. This is the expected behaviour.

I open a second console and I use mreceive to join the same multicast group 239.255.200.200:8000 to receive multicast data from subnet 172.30.8.xx using the console command : ./mreceive -g 239.255.200.200 -p 8000 -i 172.30.8.31 to the eth1 adapter of my workstation. The application start to receive multicast data and advertises the data received. This is also the expected behaviour.

Now this is where the problem begins. As soon as the multicast data begin to be received on the eth1 adapter the first console begins to advertise multicast data received on eth0 adapter. I am well aware that the Linux kernel implements a multicast level 2 routing capability. Thus at first glance this seems to be the expected behaviour. However... I have forwarding disabled as well as mc_forwarding disabled and rp_filter is enabled for both adapter. Thus the kernel shouldn't forward the multicast data from eth1 to eth0. 

At this point I am more inclined to think that the 2.6.35 Linux kernel might have an issue? I might have missing a configuration setting but at this point I am baffled. Any Linux network expert doing multicast could point me to my issue ?

Thanks
GB

---

