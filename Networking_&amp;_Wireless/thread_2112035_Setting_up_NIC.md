---
title: "Setting up NIC"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by devasia1000 on 2013-02-03
Hello,

I'm having trouble getting optimal bandwidth out of a Niagara 32066 Multi-port NIC ([http://www.interfacemasters.com/products/32066.html]("http://www.interfacemasters.com/products/32066.html")) with Ubuntu 12.04. The most frustrating thing is that the NIC works perfectly on Windows!

The NIC supports a bandwidth of 1G on each of the six ports. However, in Ubuntu, the bandwidth seems to be shared between all the ports. For example, if I use two ports, then the bandwidth is 500Mbps on each port, if I use three ports, it becomes 333Mbps. Ideally, this should not be happening, each port should have a bandwidth of 1G. If it makes any difference, I'm using 'iperf' to test the bandwidth.

This is what I've tried so far:
1) The NIC uses Intel's 85276 driver, I've installed the latest version of this driver. I've verified it by 'dmesg'
2) I've plugged the NIC into a PCIe 3.0 slot 
3) Tried the same setup on Red Hat Enterprise Linux 6.0...same issue
4) Contacted Interface Masters tech support, they couldn't help me either. They have never experienced this problem before and suggested that there was an issue with the OS
5) Re-installed Ubuntu multiple times
6) Borrowed a different 4 port Intel NIC from a friend...same issue. My friend said that he had encountered the problem before and was never able to get around it!
7) Tried it on Windows 8 with iperf. It worked perfectly!

Any help would be very much appreciated...

Thanks in advance!

---

### Post by devasia1000 on 2013-02-04
Bump...

---

