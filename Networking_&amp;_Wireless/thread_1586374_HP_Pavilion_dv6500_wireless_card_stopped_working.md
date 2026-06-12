---
title: "HP Pavilion dv6500 wireless card stopped working"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by gfd_2 on 2010-10-01
On 09/29 the  wireless card in my HP Pavilion dv6500  was working fine. After installing a partial upgrade I shut down for the night and when I started up on 10/01 – no wireless. 

Not knowing how to revert a partial upgrade I looked through the forums and it seems that this isn't an uncommon issue.... LEAVE THE WIRELESS ALONE1

Any way, I found a thread with a similar issue and here's what resolved my problem:

1.)System/ Admin/ Synaptic
2.)Download and mark for installation and install the bcmwl-kernel-source. To ensure you have the latest driver.
3.)System/ Admin/ Hardware Drivers
4.)Inactivate the Broadcom STA wireless driver 
5.)reboot.
6.)System/ Admin/ Hardware Drivers.
7.)Mark the Broadcom STA wireless driver as Active.
8.)Your little orange light should turn blue.
9.)I couldn't force the connection at this time, I rebooted and viola – the wireless connection was established. 
Hope this works for you

---

