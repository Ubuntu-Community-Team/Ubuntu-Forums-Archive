---
title: "networking stops working when downloading"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by ksteuber on 2013-01-17
I just got a new computer that I want to use as (among other things) a network hard drive. I put it together, installed Ubuntu server via USB and setup Samba. It all seems to be working, so i started copying data from my existing network hard drive, first by mounting it and copying the data, next by using wget -r to retrieve it by ftp. Both methods seem to cause the networking to go down. If I restart networking, it starts working again, but until then, I cannot ping anything including the router. I can however ping localhost. The problem reoccurs seemingly randomly when I restart the transfer.
I cannot even figure out how to troubleshoot this problem. Can someone give me some pointers?

---

### Post by ksteuber on 2013-01-19
I have been trying to troubleshoot by moving a PCI Ethernet card from another computer into this one to see if the same problem happens on it. It is an Intel PRO 1000 GT, so I installed linux-backports-modules-net-precise-server and linux-backports-modules-cw-3.6-precise-generic. I believe the card is now using the e1000 driver. It doesn't seem to be working however. When I turn on the computer with the network cable plugged into the PCI card, the network does not seem to want to start during boot (it keeps waiting for the network and eventually gives up). After it booted up, it spewed this text onto the screen and into syslog:
```
[  108.357023] e1000 0000:03:06.0: eth1: Detected Tx Unit Hang
Jan 19 17:13:03 Sparky kernel: [  108.357025]   Tx Queue             <0>
Jan 19 17:13:03 Sparky kernel: [  108.357025]   TDH                  <6a>
Jan 19 17:13:03 Sparky kernel: [  108.357026]   TDT                  <6c>
Jan 19 17:13:03 Sparky kernel: [  108.357026]   next_to_use          <6c>
Jan 19 17:13:03 Sparky kernel: [  108.357027]   next_to_clean        <6a>
Jan 19 17:13:03 Sparky kernel: [  108.357027] buffer_info[next_to_clean]
Jan 19 17:13:03 Sparky kernel: [  108.357028]   time_stamp           <ffff43a7>
Jan 19 17:13:03 Sparky kernel: [  108.357029]   next_to_watch        <6a>
Jan 19 17:13:03 Sparky kernel: [  108.357029]   jiffies              <ffff44d9>
Jan 19 17:13:03 Sparky kernel: [  108.357030]   next_to_watch.status <0>
Jan 19 17:13:05 Sparky kernel: [  110.360285] e1000 0000:03:06.0: eth1: Detected Tx Unit Hang
Jan 19 17:13:05 Sparky kernel: [  110.360286]   Tx Queue             <0>
Jan 19 17:13:05 Sparky kernel: [  110.360287]   TDH                  <6a>
Jan 19 17:13:05 Sparky kernel: [  110.360288]   TDT                  <6c>
Jan 19 17:13:05 Sparky kernel: [  110.360288]   next_to_use          <6c>
Jan 19 17:13:05 Sparky kernel: [  110.360289]   next_to_clean        <6a>
Jan 19 17:13:05 Sparky kernel: [  110.360289] buffer_info[next_to_clean]
Jan 19 17:13:05 Sparky kernel: [  110.360290]   time_stamp           <ffff43a7>
Jan 19 17:13:05 Sparky kernel: [  110.360290]   next_to_watch        <6a>
Jan 19 17:13:05 Sparky kernel: [  110.360291]   jiffies              <ffff46ce>
Jan 19 17:13:05 Sparky kernel: [  110.360291]   next_to_watch.status <0>
Jan 19 17:13:07 Sparky kernel: [  112.364240] e1000 0000:03:06.0: eth1: Detected Tx Unit Hang
Jan 19 17:13:07 Sparky kernel: [  112.364241]   Tx Queue             <0>
Jan 19 17:13:07 Sparky kernel: [  112.364242]   TDH                  <6a>
Jan 19 17:13:07 Sparky kernel: [  112.364243]   TDT                  <6c>
Jan 19 17:13:07 Sparky kernel: [  112.364243]   next_to_use          <6c>
Jan 19 17:13:07 Sparky kernel: [  112.364244]   next_to_clean        <6a>
Jan 19 17:13:07 Sparky kernel: [  112.364244] buffer_info[next_to_clean]
Jan 19 17:13:07 Sparky kernel: [  112.364245]   time_stamp           <ffff43a7>
Jan 19 17:13:07 Sparky kernel: [  112.364245]   next_to_watch        <6a>
Jan 19 17:13:07 Sparky kernel: [  112.364246]   jiffies              <ffff48c3>
Jan 19 17:13:07 Sparky kernel: [  112.364246]   next_to_watch.status <0>
Jan 19 17:13:08 Sparky kernel: [  114.368326] e1000 0000:03:06.0: eth1: Detected Tx Unit Hang
Jan 19 17:13:08 Sparky kernel: [  114.368327]   Tx Queue             <0>
Jan 19 17:13:08 Sparky kernel: [  114.368327]   TDH                  <6a>
Jan 19 17:13:08 Sparky kernel: [  114.368328]   TDT                  <6c>
Jan 19 17:13:08 Sparky kernel: [  114.368329]   next_to_use          <6c>
Jan 19 17:13:08 Sparky kernel: [  114.368329]   next_to_clean        <6a>
Jan 19 17:13:08 Sparky kernel: [  114.368330] buffer_info[next_to_clean]
Jan 19 17:13:08 Sparky kernel: [  114.368330]   time_stamp           <ffff43a7>
Jan 19 17:13:08 Sparky kernel: [  114.368331]   next_to_watch        <6a>
Jan 19 17:13:08 Sparky kernel: [  114.368331]   jiffies              <ffff4ab8>
Jan 19 17:13:08 Sparky kernel: [  114.368332]   next_to_watch.status <0>
Jan 19 17:13:10 Sparky kernel: [  116.372232] e1000 0000:03:06.0: eth1: Detected Tx Unit Hang
Jan 19 17:13:10 Sparky kernel: [  116.372233]   Tx Queue             <0>
Jan 19 17:13:10 Sparky kernel: [  116.372234]   TDH                  <6a>
Jan 19 17:13:10 Sparky kernel: [  116.372234]   TDT                  <6c>
Jan 19 17:13:10 Sparky kernel: [  116.372235]   next_to_use          <6c>
Jan 19 17:13:10 Sparky kernel: [  116.372235]   next_to_clean        <6a>
Jan 19 17:13:10 Sparky kernel: [  116.372236] buffer_info[next_to_clean]
Jan 19 17:13:10 Sparky kernel: [  116.372236]   time_stamp           <ffff43a7>
Jan 19 17:13:10 Sparky kernel: [  116.372237]   next_to_watch        <6a>
Jan 19 17:13:10 Sparky kernel: [  116.372237]   jiffies              <ffff4cad>
Jan 19 17:13:10 Sparky kernel: [  116.372238]   next_to_watch.status <0>
```

Does anyone have any ideas for how I could get either device to work?

---

