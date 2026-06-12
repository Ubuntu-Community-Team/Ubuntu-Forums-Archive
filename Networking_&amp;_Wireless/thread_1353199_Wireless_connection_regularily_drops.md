---
title: "Wireless connection regularily drops"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by Inder on 2009-12-12
Hello,

I use a wireless connection to access the Internet, and lately (since upgrading to ubuntu 9.10 karmic koala) it has started to be a pain in the ***. Every once in a while (loosing count at the end of the day) the connection will simply drop and the network manager no longer detects ANY nearby wireless network (usually, I detect something like 6 different networks). Actually, sometimes it will see the networks, but it will be impossible to reconnect anyhow.
Rebooting the system solves the problem...
Wired connection never fails. Even when my wireless connection fails, I can still get a working wired connection.

Do any of you have an idea as to what could be causing the problem? Or what I can do to solve it?

**_other symptoms which may be related:_**

* When I loose wireless connection, the whole system seems to slow down: Music starts to skip, mouse movement starts to be choppy. This state of slowness seems to persist until I reboot. It is particularily bad while the network manager is trying to reconnect (it always fails, but it still tries once in a while.. valiant at heart)

* The signal strength for my network seems to vary a lot sometimes.

* I recently installed **lm-sensor** and **sersors-applet** to monitor CPU temperatures and the such, in an attempt to see it there was a correlation between high temperature and connection failure. This allowed me to have four new icons displaying temperatures up there next to the battery and NetworkManager icons. Here are the names of each icon: temp1, temp2, CPU, CPU. And their average temperature (as far as I can tell): 60 C, 55 C, 55 C, 60 C, resp. I have no clue what temp1 and temp2 are. Anyways, I have been getting the following message regularily: An error occurred while trying to update the value of the sensor CPU located at /proc/acpi/thermal_zone/TZSO/temperature. Sometimes it says sensor CPU, sometimes it says sensor temp1...

**_log files_** (this section is rather long, sorry)

I had a look in various log files to see if anything strikes me, but of course I don't understand most of what's happening in there...

Here's what I noticed:

in **/var/log/syslog**:
The log file is full of occurences of these lines (where only the time and date changes). 
The times indicated seem to concur with difficulty in loading a webpage (it takes a lot of time, temporary loss of connection).
> 
Dec 13 14:37:44 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Dec 13 14:37:44 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 14:37:45 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Dec 13 14:37:45 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Dec 13 14:37:45 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed


At other places in the log file, I see the following, which concurs with my observing choppy mouse movement and the NetworkManager icon changing to "searching".
> 
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 11)
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 11).
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2196
Dec 13 14:46:50 shawn-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto dlink'
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto dlink' requires no security.  No secrets needed.
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Config: added 'ssid' value 'dlink'
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Dec 13 14:46:50 shawn-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Dec 13 14:47:05 shawn-laptop NetworkManager: <info>  wlan0: link timed out.
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation.
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 11)
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (dlink)
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  Marking connection 'Auto dlink' invalid.
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  Activation (wlan0) failed.
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Dec 13 14:47:50 shawn-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).


The other thing in there that seemed related is a whole lot (really, a lot) of lines concerning ath9k

> 
...
Dec 16 18:30:35 shawn-laptop kernel: [  925.430675] ath9k: Failed to wakeup in 10000us
Dec 16 18:30:35 shawn-laptop kernel: [  925.430680] ath9k: Unable to reset channel (2437 Mhz) reset status -5
Dec 16 18:30:35 shawn-laptop kernel: [  925.430690] ath9k: Unable to set channel
Dec 16 18:30:40 shawn-laptop kernel: [  930.262355] ath9k: Failed to wakeup in 10000us
...

stuff like that

In another log file: /var/log/messages
I can see these lines, the times of which concur with audio and mouse lag and network failure.
> 
Dec 14 19:36:24 shawn-laptop kernel: [18022.982270] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
Dec 14 19:36:24 shawn-laptop kernel: [18022.982271] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff880133e26720), AE_TIME
Dec 14 19:36:26 shawn-laptop kernel: [18025.120059] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
Dec 14 19:36:26 shawn-laptop kernel: [18025.120085] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.GBST] (Node ffff880133e327e0), AE_TIME
Dec 14 19:36:26 shawn-laptop kernel: [18025.120139] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.BAT0._BST] (Node ffff880133e32920), AE_TIME
Dec 14 19:36:26 shawn-laptop kernel: [18025.120261] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385
Dec 14 19:36:28 shawn-laptop pulseaudio[1737]: ratelimit.c: 10 events suppressed


Well, I don't know what to think, so if you have any idea or if you know of a test that could rule out certain possibilities, that would be great!

Thanks very much in advance.

My system:
Acer aspire 5536-5519
AMD Athlon 64 X 2 processor QL 64 (2.1 GHz)
ATI Radeon HD 3200 Graphics Up to 1919 MB HyperMemory
15.6" HD LED LCD
4 GB Memory
320 GB HDD
DVD Super Multi DL drive
Ubuntu 9.10 karmic koala 64 bit version
--is there anything more you need to know?--

---

### Post by lakerssuperman on 2009-12-12
I have the exact same behavior on both a brand new Sony Laptop and a Asus Eee PC.  At first I thought it was just the Sony but then I also got the Asus and it did the exact same thing.  I also noticed that attempting to transfer files from one computer to another across the network will kill the connection every time and I will have to reboot the computer to get it back.

---

### Post by Inder on 2009-12-12
@lakerssuperman: Which operating systems are these computers running? If one of them is not Ubuntu, we're in the wrong forum!
I'm also curious because this problem seems to occur more often since I upgraded from 9.04 jaunty to 9.10 karmic koala, though I'm not quite sure of this because I had other network problems before... Also, do you experience the same symptoms as I do? (varying signal strength and music skipping on and after connection drop, see edited post above)

---

### Post by Inder on 2009-12-16
This is a bump. I think it's legitimate because I just triple the size of my original post based on replies I got over at superuser.com...

Thanks for understanding.. By the way, here is the link to my superuser question:
[http://superuser.com/questions/82461/why-do-i-regularily-lose-my-wireless-connection](http://superuser.com/questions/82461/why-do-i-regularily-lose-my-wireless-connection)

---

### Post by MeBrains on 2009-12-17
same problem here. Ubuntu Karmic with network manager and a Fritzbox AP. 

I have not noticed the problem until I wanted to download a torrent this week. The connection just does not survive having a download only. It has no problems at all when browsing the web. My logs show more or less the same entries mentioned above.

Any help is appreciated.

---

### Post by Inder on 2009-12-17
Ok, well I got another suggestion over at superuser.com which happened to work for me. It was simply to install wicd as a replacement for NetworkManager.
Solved all of my problems.

If it works for you guys as well, come back and tell, just for continuity.

Good luck

Shawn

---

### Post by MeBrains on 2009-12-18
Will try to do so as well and will keep you posted...

---

### Post by xtjacob on 2009-12-18
I have this same problem too. Wireless is slow, but the Ethernet is fast. When i'm downloading large files they seem to stop, and my wireless disconnects, ans reconnects too. Also the signal strength on network manager sometimes goes to 0% then to 100% then to 0% and back to normal. I tried WICD, but that didn't change a thing. >  The other thing in there that seemed related is a whole lot (really, a lot) of lines concerning ath9k My driver is also a Ath9k, is this a bug?

---

### Post by MeBrains on 2009-12-19
wicd seems to have solved my problem as well. Had downloads going overnight; they were still running this morning. Since it used to disconnect after only an hour, this is positive.

One remark still: I also had a website with AJAX refresh open. It could still be that that kept the connection alive. 

For me it is solved now. Should it change - I will update.

---

### Post by Inder on 2009-12-19
Well, I woke up this morning and wicd couldn't find ANY wireless network connection.. It sounds like it's back to drawing board.

---

### Post by varlo on 2009-12-22
I have been struggling with the same problems for some time as well. Installing wicd seemed to work to start with, but soon enough the problems started again. However, last night I installed a backport module:

linux-backports-modules-wireless-karmic-generic    v.2.6.31.16.29

with dependencies and the wireless seem to work pretty smooth from now on. Might be something worth trying if you have not solved it already. 

My machine specs are very similar to Inder's as well:

Acer aspire 5536
AMD Athlon 64 X 2 processor QL 64 (2.1 GHz)
ATI Radeon HD 3200 Graphics Up to 1408 MB HyperMemory
15.6" HD LCD
4 GB Memory
250 GB HDD
DVD Super Multi DL drive
Ubuntu 9.10 karmic koala 64 bit version

---

### Post by Inder on 2009-12-23
I've just installed the linux-backports-modules.. didn't solve anything.. Vario, Are you still using wicd or did you go back to NetworkManager?

---

### Post by varlo on 2009-12-26
I went back to use Network Manager -never really tried it with wicd after installing the backport modules (as I did not get that to work properly in the first place).  That solution still seem to work pretty smoothly for my machine though ...

---

### Post by MeBrains on 2010-01-09
I am still on wicd with no issues yet...

---

### Post by MadnessRed on 2010-03-30
Bumping...

I tried WICD but that didn't not do much.
I have same computer as you Acer Aspire 5536.

edit:
I went back to NM, and so far internet hasn't died. I'll see how long this lasts.

---

### Post by chkneater on 2011-02-28
I'm having this same problem now after I did an upgrade from 9.04 to 9.10. Before upgrading I found a file named compat-wireless-2010-11-14 and another that was similarly named but used letters instead of dates.  I found them as tar.bz2 files and extracted them and followed the readme guide and it fixed my wireless problem at the time.  Try that if you can find it and havent' already tried it. As of now neither Wicd or NM will work, however if I run them at the same time the will simultaneously connect and disconnect at the same time.  I think it has something to do with the connection to Dbus.  check the compat wireless tars out tho, they helped me out the first time.

---

### Post by Inder on 2011-03-18
locate compat-wireless yeilds no results.. Is this normal? Can I get these files elsewhere to try it out?

---

