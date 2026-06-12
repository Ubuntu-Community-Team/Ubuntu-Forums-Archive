---
title: "Newbie: can't connect to wireless"
date: 2012-04-25
forum: Networking &amp; Wireless
---

### Post by jenwren on 2012-04-25
Hey - I am brand new to Ubuntu (and Linux). I installed Ubuntu 11.10 on my home PC and found that I cannot see the internet at all. We are wireless at home and my router works fine under Windows 7 (and other PCs in the house). 

I know Unix a little bit from my work environment so I know some commands at the terminal and file editing, etc. But I am feeling pretty overwhelmed when I read these posts with the level of detail - all just to get my wireless working. This is square one, too. I have not even played with Ubuntu because I got stuck with no internet connection. 

I quoted from a thread last October below. This is as far as I got and I have the exact same Centrino driver and I see the same messages coming from iwconfig. After that, I got lost in the post.

I cannot even download upgrades while I am trouble shooting because I am not on line at the time. Do I need to unplug my router and plug directly into my cable connection if I am needing to pull in packages to update as I go along fixing this driver issue?

HELP, please - I am feeling clueless and over my head. 

The thread below is tagged as "SOLVED" so I am hoping a synopsis of it might get me where I need to be.

Thanks in advance!


######################################
Can't connect to wireless after 11.10 upgrade
11.10 upgrade - can see networks but connection times out
I using an ASUS-U56E netbook. I just upgraded then installed 11.10 and the wireless stopped connecting. I can see all the networks but when I try to connect it just times out. Here is some basic information to start.


Centrino Wireless-N + WiMAX 6150 (Rev 67) -iwlagn driver

#iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on

---

### Post by Ms. Daisy on 2012-04-26
Hello, welcome to the forums.
 
Is this the thread you were referring to?
[http://ubuntuforums.org/showthread.php?t=1862484&highlight=ASUS-U56E+netbook](http://ubuntuforums.org/showthread.php?t=1862484&highlight=ASUS-U56E+netbook)
 
Can you plug your computer into the router with an ethernet cable? That would allow you to download updates?

---

### Post by wildmanne39 on 2012-04-26
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

