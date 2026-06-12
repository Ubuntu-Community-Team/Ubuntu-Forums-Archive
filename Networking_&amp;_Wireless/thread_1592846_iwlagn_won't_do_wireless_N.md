---
title: "iwlagn won't do wireless N"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by abeowitz on 2010-10-11
I've got an Intel 1000 Wireless N chip:

```
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
```

It connects to G networks just fine.  But will not connect to a Wireless N AP.

iwconfig suggests it's only doing b/g:

```

wlan0     IEEE **[COLOR="DarkRed"]802.11bg[/COLOR]**  ESSID:"abeowitz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:9A:F1:30   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

Firmware is up to date.

```

md5sum iwlwifi-1000-3.ucode

df79176a88147862c5fe2b7f81c11711  iwlwifi-1000-3.ucode

```

I tried Arch-Linux on this same laptop and got it to do N just fine.  Even got up to 130Mb/s in iwconfig output!

So, 

1)  Firmware is good, same as Arch linux
2)  AP is good, others connect fine at N speeds
3)  G connects fine, so not authentication or other logical problem...

What should I look for?

Ubuntu 10.10 64 bit

2.6.35-22-generic

---

### Post by abeowitz on 2010-10-11
```

root@abe-U43Jc:~# dmesg | grep -i iwl
[    3.620032] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.620035] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    3.620150] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.620189] iwlagn 0000:03:00.0: setting latency timer to 64
[    3.620290] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    3.644059] iwlagn 0000:03:00.0: **Tunable channels: 13 802.11bg, 0 802.11a channels**
[    3.644433] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[    3.687821] iwlagn 0000:03:00.0: loaded firmware version 128.50.3.1 build 13488
[    3.719619] phy0: Selected rate control algorithm 'iwl-agn-rs'


```

---

### Post by Mobidoy on 2010-10-11
I have the same issue with a Intel(R) WiFi Link 5100 AGN, it will connect on mixed mode but not on N only :(

---

### Post by ABCC on 2010-10-11
I've encountered the same problem on an Intel 5100, once I'd switched my access point to both N and G allowed me to atleast connect again.

Looking through some old messages from 10.04 I found that a similar note about configurable channels appeared:

```
~ # zgrep iwl /var/log/messages.3.gz
...
kernel: [   28.670384] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
kernel: [   28.728369] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
kernel: [   31.370171] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
kernel: [   31.413115] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12

```

Again no N channels mentioned, yet my AP was set to N only and everything worked as expected. It seems that not listing N under "tunable channels" doesn't preclude it from working.

---

### Post by abeowitz on 2010-10-11
GOT IT!!!!

The iwlagn module might have 'n' disabled by accident...

```

rmmod iwlagn

modprobe iwlagn 11n_disable=0

```

```

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     **IEEE 802.11bgn**  ESSID:"abeowitz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:9A:F1:30   
          **Bit Rate=135 Mb/s**   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by abeowitz on 2010-10-11
Looks like /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf is our culprit.

Delete or move this file.

```
wlan0     IEEE 802.11bgn  ESSID:"abeowitz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:9A:F1:30   
          Bit Rate=[COLOR="DarkRed"]**150**[/COLOR] Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Mobidoy on 2010-10-11
Awesome, it works for me too :) I have set my router to N only and I connect :)

So deleting this file makes it a permanent fix ?

---

### Post by abeowitz on 2010-10-11
Mobidoy,

Yes, deleting the file is a permanent fix.

Not sure why it's there to begin with, perhaps cruft leftover from testing or a bug with the 5300.

-Abe

---

### Post by sumerland on 2010-10-11
Yes, it's a feature and not a bug:

"802.11n support for the iwlagn driver has been temporarily disabled.  Intel is actively working to get this properly fixed up in the firmware.  This workaround should be reverted once updated firmware is available."

Or visit this link: [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

---

### Post by abeowitz on 2010-10-11
> **sumerland said:**
> Yes, it's a feature and not a bug:

"802.11n support for the iwlagn driver has been temporarily disabled.  Intel is actively working to get this properly fixed up in the firmware.  This workaround should be reverted once updated firmware is available."

Or visit this link: [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

Awesome!  Thanks for the info!  If I have problems with N, I'll know how to disable then.

---

### Post by abeowitz on 2010-10-11
> **sumerland said:**
> Yes, it's a feature and not a bug:

"802.11n support for the iwlagn driver has been temporarily disabled.  Intel is actively working to get this properly fixed up in the firmware.  This workaround should be reverted once updated firmware is available."

Or visit this link: [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

Actually, I had this problem with my other laptop using an Intel 5350.  The connection would go bad every 30 min or so.  Reloading the module worked.  Happened at work where we have N AP's, but not at home where I had only a G at the time.

N seems stable on this Intel 1000 right now... :)

---

### Post by Gausian on 2010-10-11
This solved my problem.  Thank you!

---

### Post by ABCC on 2010-10-11
I've noted a few significant network slowdowns when watching video files over nfs. On files with low bitrates (avi) there was some choppiness, high bitrate mkv's became unwatchable due to the many dropped frames. After reverting the work around and reconnecting with G all stutter cleared up.

Although the fix may be for an Intel 5300 the bug seems to hit 5100s too.

---

### Post by abeowitz on 2010-10-11
> **ABCC said:**
> I've noted a few significant network slowdowns when watching video files over nfs. On files with low bitrates (avi) there was some choppiness, high bitrate mkv's became unwatchable due to the many dropped frames. After reverting the work around and reconnecting with G all stutter cleared up.

Although the fix may be for an Intel 5300 the bug seems to hit 5100s too.

Well, hopefully Intel will come up with a firmware solution soon.  It's not Ubuntu's fault.  I had trouble with that 5350 in Gentoo Linux.

If I learn more, or Intel updates, I'll update this thread.

---

### Post by agrisv on 2010-10-14
[QUOTE=abeowitz;9953554]GOT IT!!!!

The iwlagn module might have 'n' disabled by accident...

```

rmmod iwlagn

modprobe iwlagn 11n_disable=0

```

thanks it worked for mee too--- Detected Intel(R) Wireless WiFi Link 4965AGN
ubutnu 10.10

---

### Post by magnetpest2k7 on 2010-10-15
Hello my laptop is TOSHIBA L505D and even I am not able to connect to the wireless N network

 when I run 

lspci

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I find realtek to be my wireless driver can any one tell me how to go about fixing this problem for my driver? 

I get the following message when I run

rmmod iwlagn
ERROR: Module iwlagn does not exist in /proc/modules

Thanks
Vin

---

### Post by peepingtom on 2010-10-17
iwlagn is a driver for intel wireless chipsets. Since you have a realtek wifi chipset rather than an intel one, you should start a new thread or ask for help on IRC via #ubuntu on irc.freenode.net

---

### Post by sritacco on 2010-10-18
this works... sort of

The bad news is on Intel 5100 AGN any N connections are unstable and eventually
lock up.

This was fixed in recent releases of 10.04 but is broken again in 10.10

---

### Post by makaros on 2010-10-22
High!After deleting intel-5300-iwlagn-disable11n.conf i'm experiencing some problems.Is there any way to restore it?

---

### Post by ABCC on 2010-10-22
Sure, just create a new one with the following contents:

```

options iwlagn 11n_disable=1

```

To reenable it you'll also need to reload the driver:

```

sudo modprobe -r iwlagn
sudo modprobe iwlagn

```

Although you can use any name you like for the file it's best to use the same one. That way whenever the fix is commited apt should be able to remove it for you.

---

### Post by makaros on 2010-10-23
Thanks a lot!Works like a charm!

---

### Post by Kixtosh on 2010-12-08
> **abeowitz said:**
> Looks like /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf is our culprit.

Delete or move this file.Hmmm. That file was not in that folder on my laptop, but I have the same issues: limited to wireless G only, with an Intel wireless card:

```
kex@Kex-R500:~$ dmesg | grep -i iwl
[    5.247232] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    5.247237] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    5.247372] iwlagn 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.247411] iwlagn 0000:02:00.0: setting latency timer to 64
[    5.247487] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    5.359211] iwlagn 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels

```

---

### Post by cprofitt on 2010-12-26
Any update on the update from Intel?

---

### Post by HankB on 2010-12-30
:confused:

I just discovered today that I had my AP set for G only. I set it to N also and for the rest of the day, I've had very uneven results. At times throughput is stellar - even better than my 100baseT LAN. But more recently the WiFi connection has been down more than up. I frequently can't even load a web page before it stops working again. I don't see any messages hinting at the problem in the logs.

I'm running 10.04 which uses firmware /lib/firmware/iwlwifi-5000-2.ucode.

I've added the file listed above (/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf) with contents: 
```
options iwlagn 11n_disable=1
```
to revert to G only.

... Actually, that did not work. Neither did the following commands:

```
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
```


I guess I'll need to disable N on the router again. :(

I wonder what the fix for 10.04 was and if I'm experiencing the same issue.

-hank

---

### Post by seenthelite on 2010-12-31
```
# options iwlagn 11n_disable=1
```

This works for me, my network is set to N only, no G. Without # it sees the network but will not connect.

---

### Post by ThomasNovin on 2011-01-10
I had some problems with the driver supplied with Ubuntu 10.10 but after switching to the latest developer version (by installing [apt://linux-backports-modules-wireless-maverick-generic]("apt://linux-backports-modules-wireless-maverick-generic")) it works fine!


wlan0     IEEE 802.11abgn  ESSID:"XXX"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1A:70:XX:XX:XX   
          Bit Rate=144.4 Mb/s   Tx-Power=15 dBm

---

### Post by cariyawa on 2011-02-10
I don't believe they disable it by accident. I have 4965AGN card in my laptop and I tried to enable it by deleting that .conf file. It was fine for a while, but I had intermittent lock downs. I disabled N again, no problems.. runs smoothly..

---

### Post by ergosteur on 2011-03-15
Thanks for this, I was pulling my hair out trying to figure this out.

---

### Post by markp1989 on 2011-03-19
thanks for this thread, I have tried loading the module like described in page 1 "sudo modprobe iwlagn 11n_disable=0" and it is definitely faster if I do an internet speed test at [www.speedtest.net](www.speedtest.net) i get roughly 40mbs down speed, where when I was on G only I would get about 10mbs down speed

dont know how "stable" its going to be as its only been 10 minutes so far, but its nice to be able to use most of my 50mbs broadband connection when on the laptop.

anyone know if Intel have released a updated revision of this firmware? and if they have will it be in 11.04?

currently I have 2 access points in the house, one that is B/G mixed and the other that is N only, because if I had the main router running NG mixed as soon as a G device would make all connections G speed.

---

### Post by compuguy1088 on 2011-03-22
Great news *Sarcasm*. Apparently intel will not fix the issues with wireless n with "legacy devices", including the 4965agn:

> (In reply to comment #131)
> In reference to the splitting of the iwlagn driver with a legacy branch, will
> the 4965agn get a similar fix. These network cards have similar issues,
> including the "Received BA when not expected" errors.

It will be very difficult to add the same firmware fix for legacy devices
including 4965. I am really sorry about it.

Thanks
Wey
[https://bugzilla.kernel.org/show_bug.cgi?id=16691#c132](https://bugzilla.kernel.org/show_bug.cgi?id=16691#c132)


All I can say in response....epic fail Intel, epic fail!

---

### Post by psypher on 2011-04-21
Hi All,

I have got the Intel Advanced-N 6200 in my laptop. Enabling N seems to be working so far, copy went from 2MB/s to 5.3/MB/s, iwconfig now states 802.11abgn, Bit rate=144.4 Mb/s (insted of 54mb). Although I have a 300mb AP and wireless card. Anyone know how to get it to run at 300mb?

Thanks

---

### Post by haidoura on 2011-05-05
This solved my problem:

cat /etc/modprobe.d/iwlagn.conf
options iwlagn 11n_disable50=1 11n_disable=1

the file iwlagn.conf was not available under that directory, so I added it and then reloded the iwlagn module by:

sudo modeprobe -r iwlagn
sudo modeprobe iwlagn

---

### Post by awm086 on 2012-12-04
I feel like I may be having a similar problem on Ubuntu 12.10. At home I can connect to the wireless with no problem. At work, I cannot connect to the access point with highest signal, which I find using nm-tool:
```
Infra, 00:24:6C:80:D7:40, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
```

 I know that, because when I boot in Mac OS x, it connects just fine. I tried specifying the MAC address of the access point, but network manager refuses to connect to it. Here is the sys [log ]("http://pastebin.com/e5324Z0m"). 
My card is ```
Broadcom Corporation BCM4331 802.11a/b/g/n
```

Can anyone help?

---

### Post by wildmanne39 on 2012-12-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

