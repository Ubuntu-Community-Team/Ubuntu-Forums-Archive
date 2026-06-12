---
title: "RealTek driver problem 8191SE"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by Sandhurst on 2011-03-07
Hi Ubuntu helpers,

I've done a search through the forums for related topics and still cannot find a solution to my wireless woes. I've a new laptop (unbranded, but I suspect it's a Toshiba) with a RealTec 8191SE driver. I've been to the RealTec website and downloaded a driver as well as finding ndiswrapper from the web.

I printed off the Readme file from RealTec and went though the following procedure. If anyone spots a glaring error could you please advise and I will try and fix. 

I changed to superuse using : sudo su
and entered my password. All good so far.

I was already in the directory containing the downloaded RealTec driver. I downloaded RLT8192SE ver 0019 as this was the closest to my hardware version and the latest driver available.

I used the command : make
and then                  : make install

Both these commands ran ok. However when I rebooted and activated wireless using Fn F10 on the laptop I was still disconnected from WIFI.

I then used : iwconfig wlan0 up

but this resulted in an error (see below)

root@Ubuntu:/home/jon/LDD/Drivers/test# iwconfig wlan0 up
iwconfig: unknown command "up"

root@Ubuntu:/home/jon/LDD/Drivers/test# ifconfig wlan0 up
SIOCSIFFLAGS: Operation not permitted

Now I've reached the limit of my abilities and would appreciate a bit of assistance. 

Thanks in advance

Jon

---

### Post by jonah1980 on 2011-05-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758")

---

