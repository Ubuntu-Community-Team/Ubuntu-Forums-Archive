---
title: "RTL8187L driver problem in 10.04"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by vipulmahajan on 2012-09-19
Hello,

We are using RadioLabs Wavalite USB Wifi Module which uses RTL8187L chip. To evaluate the performance of the module and driver we used D-ITG, Distributed Internet Traffic Generator ([http://www.grid.unina.it/software/ITG/index.php](http://www.grid.unina.it/software/ITG/index.php)) which is capable of producing traffic (packets) at predefined rate.

The testing was done in Lab environment and distance between two antennas was around 1.5m. The packet size was 1500 with 67 packets per second to effectively achieve 800Kbps bitrate.

1) On testing driver for "Windows <--> Windows" we found 0% packet loss when the duration was 1 min but the losses were 0.14% when the duration was 1 hr.

2) For Ubuntu 10.04 we found that "RadioLabs Universal Driver" downloaded from RadioLabs website contains Realtek version 1038 as it is. We were unable to compile 1038 on Ubuntu 10.04 so we downloaded 1040 version from Realtek's website and tested in "Ubuntu 10.04 <--> Windows" scenario. With same setup and environment the packet loss ratio was 3.5% for 1 min test duration. Why such a difference?

3) On "Ubuntu 10.04 <--> Ubuntu 10.04" we found the packet loss rate accelerating to 7 - 13% for duration of 1 min. It seems like Linux driver lack reliability and performance as compared to Windows counterpart.

We are basically looking for a Linux device driver for kernel version 2.6.32 which is equivalent in terms of reliability and performance to your Windows device driver. The driver provided in Linux kernel lacks Ad-hoc support so we are not using it.

Does anyone has RTL8187L driver working perfectly in Ubuntu 10.04/Linux 2.6.32?

---

