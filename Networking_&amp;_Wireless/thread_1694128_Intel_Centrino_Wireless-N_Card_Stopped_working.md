---
title: "Intel Centrino Wireless-N Card Stopped working"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by vezinadj on 2011-02-23
I have a new Thinkpad t510 laptop with an intel centrino wireless N card (no bluetooth).

I installed ubuntu a couple weeks ago after I got another hard drive in the expansion bay. I have the drive partitioned into two sections, 250gb for file storage, and 250gb for the linux OS. Currently no other OS is installed on the other harddrive.

I have had everything perfect for the past couple weeks, but once i installed some updates today, my wireless fails to work now. Just some general info that you might ask me,

lspci | grep Network, returns

00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

Furthermore, on the top right of my screen, my wireless is grey'd out and says no network devices available on hover.

iwconfig, returns 


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Im trying to connect to my college wireless network. I have looked a thinkwiki and no one has posted any bugs. Any ideas on getting it working again?

---

### Post by vezinadj on 2011-02-23
The fact that I was acquiring wireless internet about an hour ago, and now mysteriously, my card isnt working makes me lean towards a driver issue. I dont really understand your statement. I attempted to install the backport drivers but it still does not work. Is there a way to reinstall the driver that came with ubuntu when I had the fresh original fresh install?

---

