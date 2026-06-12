---
title: "Wired connection trouble on Linux PC"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2012-05-21
I am having a lot of trouble with the wired ethernet connection on my  Linux PC. It is not distro-specific, kernel specific, or driver  specific. I have had a lot of trouble with the Linux driver in the past,  but I am beginning to suspect a hardware problem. The connection is  established, but the speed varies between 390 kb/s and 800 b/s (bits,  not kbits). The connection slows down and speeds back up fairly  regularly.

Wireless connections are fine. There is only one other  wired connection in the house, my wife's Win7 PC, and it does not have  this problem. So, I do not suspect a DSL problem or a router problem.

The  ethernet controller is on the Gigabyte motherboard. It is a "Realtek  Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet  controller (rev 06)". I have Ubuntu 11.10 and 12.04, and Sabayon 8 and  Arch Linux installed on the PC. All of these distros are using different  kernels. On Ubuntu 12.04, I installed the driver from Realtek, r8168  instead of r8169. This usually fixes any of my connection problems, but  this time it did not.

I have tried powering down the PC and disconnecting it from AC power. It does not help.

There  is a bug on Launchpad, #998200, which seems to be the same problem I am  having. One guy says his connection only works after installing a  network backports package (or powering down and disconnecting from AC). I  installed the network-backports package on my Ubuntu 11.10, after which  I could not connect at all. I uninstalled the backports and now I can  connect again, but it still has these drastic slowdowns.

I am just about out of ideas, except for the idea of buying a new ethernet card.

Tim

---

