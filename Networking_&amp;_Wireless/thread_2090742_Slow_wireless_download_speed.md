---
title: "Slow wireless download speed"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by ciaran1980 on 2012-12-03
Whenever I boot up my computer, speedtest.net shows an internet speed in excess of 20 Mbps. After around five minutes it consistently drops down to just over 1 Mbps and stays at that download speed. The upload speed remains unchanged at around 3 Mbps. I checked Glasnot just to check if my ISP was somehow throttling my internet but this doesn't seem to be the case. My other laptop and those of my housemates all show download speeds of over 20 Mbps.

I have a system76 Lemur Ultra laptop. I have tried restoring the system and also installing the latest drivers from system76 (Driver Version 3.2.3).

Here are the specs I get when I run the following command:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
``````
ciaran@ciaran-Lemur-Ultra:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux ciaran-Lemur-Ultra 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ciaran@ciaran-Lemur-Ultra:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9196]
    Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:4140]
    Kernel driver in use: jme
ciaran@ciaran-Lemur-Ultra:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BlackFish"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:25:B8:76   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18929   Missed beacon:0

ciaran@ciaran-Lemur-Ultra:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ciaran@ciaran-Lemur-Ultra:~$
```I saw the following fix used a lot in this forum and decided to give it a try:

```
sudo ifconfig wlan0 down
sudo rmmod -f rtl8192ce
sudo modprobe rtl8192ce nohwcrypt=1
sudo ifconfig wlan0 up
```When I run the third command I get the following error and I cannot reconnect to the wireless.

```
FATAL: Error inserting rtl8192ce (/lib/modules/3.5.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): Invalid argument
```I am not sure if this problem has something to do with the specific Realtek rtl8192ce kernal driver that system76 use. At this point, I am at a loss with what to do. Any help would be greatly appreciated.

---

### Post by TheFu on 2012-12-03
Residential ISPs have to share bandwidth across thousands and perhaps millions of customers.  If you want 100% guaranteed bandwidth, get a telecom-quality line with continuous line conditioning.

What you are seeing is extremely common for all residential ISPs though seeing the max upload for which you pay (assuming 3Mbps is what you pay for) is extremely good.

To offset the costs and attempting to find the best good for the most customers, ISPs have been throttling different types of bandwidth for decades.  Torrent traffic and usenet traffic do not have the same requirements for low-latency as VoIP traffic or interactive web surfing.  These are prioritized higher to keep most customers happy.

Also, many servers on the internet throttle bandwidth to a single IP as a way to prevent hogs from disrupting service to other client connections.

The troubleshooting that you've performed does not necessarily say that there is anything wrong with your laptop at all.  It just shows that at some points in time, it appears to be slower than you'd like.

First, gather consistent facts and data.  That means you need to make reproducible tests that can be run on all the devices in the house.
Second, test the wired connection for all the devices AND test the wireless connections. Is there a difference in performance?
Third, test transfers only inside the house, on the LAN.  This removes the ISP from the issue. Transfer very large files around (in both directions) and time them using the computer, not a stopwatch.  Large files means larger than the amount of RAM in either system connected. We want to test more than the caching of the OS, after all.

Personally, I avoid using wifi when performance matters. There are hundreds of things that can impact wifi performance, most of which do have ZERO control over.  When it comes to wifi performance, sometimes inches make a huge difference, plus the total number of wifi devices and wifi networks and overlapping wifi channels makes it nearly impossible to predict what bandwidth any device should get.  A rule of thumb is that every added device on a wifi network halves the bandwidth available.  So on a 54Mbps wifi network, 1 device drops that to 37Mbps, 2 devices drops both to about 18Mbps, 3 devices drops it again to about 9Mbps for each ... and so on.  So if there are 3 PCs and 3 smartphones or tablets all connecting via wifi, that is 6 devices on the network.  You can do the math - what amount of bandwidth would be available for each?
Also, if the devices all mix - N, G, B, then the lowest performance basically becomes the highest bandwidth available for all of them. Vendors claim this isn't true anymore between N and G - sure, I believe them ... NOT.  If there is 1 G device on the network, the theory starts at 54Mbps, not 150 or 300Mbps.  If overlapping channels are involved, all bets are off. Different countries have different rules for wifi channels allowed. In the USA, only channels 1, 6, and 11 do not overlap.  When I see channel 3 used by my neighbors, I get pissed off - they are impacting ch1-ch7-ish - basically reducing the available bandwidth for everyone.  Using wired connections is so much easier when testing bandwidth.

I don't know why disabling hardware encryption would help performance, if that is what that driver option does.

Facts and data. That is the most important tasks for today. Limit what you are testing by working only within your LAN and use wired connections to help determine if the wifi driver is actually the primary issue first.

---

### Post by ciaran1980 on 2012-12-03
Thanks TheFu for your detailed reply. Unfortunately, since I live in  shared accommodation, I have little control over the internet connection  here. Our internet bundle is for 50 Mb download speed. At any one time  there are up to six devices connected to the internet but for most of  the day, there is only my laptop. I understand that the more devices  there are connected to the wireless network, the less bandwidth there  will be available. 

However, I don't believe this to be the cause  of my problems. The internet woes that I mentioned above happen only to my Ubuntu machine and they occur on a consistent basis. After I  wake the machine from sleep or reboot it, I have download speeds in  excess of 20 Mbps for between five to ten minutes. Then, they just fall  off rapidly to just over 1 Mbps and stay that way. This happens every  single time. 

While, I haven't done any formal testing, the  patterns I've seen have been occurring consistently for some weeks now.  My iPad registers a download speed averaging about 16 Mbps (the lowest  I've seen is 11 Mbps) using the speedtest.net app. I consistently get  download speeds of around 22 Mbps on my Macbook Pro with it very rarely  dropping below 20 Mbps. None of my housemates have noticed any drop off  in their download speeds. 

I do not believe that this is a  problem with the ISP. The LAN connection works like a dream. I get download  speeds in the region of 28 Mbps. When I disconnect the cable and run  wireless again, I'm back down to 1 Mbps. Tests I've ran on Glasnost also seem  to indicate that my ISP is not throttling my speeds.

I didn't notice any particular problems with my internet speed when I was using 12.04. The problems I'm seeing now have only started occurring with 12.10. I cannot pinpoint exactly when the problem started but it has been going on for at least a month now.

I hope this additional information helps.

---

### Post by TheFu on 2012-12-04
I think you should stop testing outside the local network when troubleshooting.  You need to nail down the exact problem first.  Assuming that your really are convinced this is only a wifi issue and not a networking issue in general.

Have you tried slightly different wifi drivers?
Have you tried building them yourself?

I'd also point out that 22Mbps download speeds suck over wired ethernet.  Wired ethernet should get 650-800Mbps for GigE connected devices and around 85-90Mbps for 100-baseTx connections.

When using wifi for your testing, it is critical that you know, **ABSOLUTELY KNOW, **how many devices are on the connection. Without that data, we are just pissing into the wind guessing the bandwidth - even more than we would be just with the normal uncertainty that wifi brings.

Your housemates probably can't tell the difference between 256Kbps and 256Mbps.

Again - facts AND data.  Use some tools like bonnie++ for disks and netperf for networking.

Knowing the exact versions of the wifi drivers would be helpful too.

I'd also recommend allocating 5GB and a new partition on the HDD to load 12.04 again so you can run the same benchmarks.  Facts and data.

Compare the results between the 2 different installs and perhaps you'll determine the exact issue?

---

### Post by ciaran1980 on 2012-12-05
TheFu, thanks again but I think you might be over estimating my level of knowledge. I would not know where to start with trying similar drivers, much less building them myself.  I've installed bonnie++ and netperf but I am not sure how I should use them. 

I liked the idea of putting a second installation of Ubuntu on the HDD but I've run into a problem here. When I open up GParted, I get the following error:

```
Error informing the kernel about modifications to partition /dev/sda2 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
```I have no idea what this means but rebooting the system doesn't seem to help. I am not sure whether this could be related to the main problem I am experiencing.

---

### Post by TheFu on 2012-12-06
If you wish to avoid most of the issues like this network performance thing, stay with an LTS release. I think Canonical oversells ¨new¨ as an upgrade.

That error is not part of the initial problem. Don´t worry.

It is not advisable to change partitions on a currently ¨active¨ HDD. Basically, if you are running from the HDD, you don´t want to change the partitions. Boot off any other device - CDROM, DVD, USB Flash drive, run gparted and make the partition changes. The new partition only needs to be 10-15GB and it doesn´t matter if primary or logical partitions are created. Linux will boot from either.

I´d also like to point out that we all learned new skills through problem solving. Very few people learn to compile drivers ¨for the fun of it¨. We all had some issue that needed solving and rebuilding a driver was the most likely solution. You can learn to do it too, if you really want to fix it. If you just want something that works, now, drop back to the last LTS release.

To learn to use any program, use the man page.  **man netperf**

---

### Post by ciaran1980 on 2012-12-06
I think I've solved my wireless problems. I downloaded Boot Repair and ran the default settings. I rebooted but it made no difference. I decided to run Boot Repair again with the following advanced options selected:


[LIST]
[*]Purge GRUB before reinstalling it.
[/LIST]

[LIST]
[*] Purge kernels then reinstall last kernel.
[/LIST]
 
After running the commands in the terminal, I rebooted. Since then I've been getting speeds of around 20 Mbps. 

I couldn't agree more about sticking with the LTS. 12.10 has been nothing but one problem after another. I upgraded because I was excited about the prospect of using web apps. Instead, I haven't been able to get them to work and I've had to deal with a whole slew of new problems. I haven't had to compile a driver yet but I have had my fair share of problems to troubleshoot. I'll be sticking with 14.04 when it comes out.

---

