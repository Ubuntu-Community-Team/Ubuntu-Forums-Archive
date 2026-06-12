---
title: "Intel 5300 wont install with either 9.01 or 9.1"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by dzuchowski on 2009-08-21
I ordered the intel 5300 and it works great for windows 7.
I tried it with both Ubuntu 9.01 and beta 9.1 and it wont be seen when i click on the area to connect to a network on the upper toolbar to the right side. 

I also for the heck of it tried it with SUSE 11.1 and beta 11.2 Milestone 5 release and no luck with the wifi. Also the Suse 11.1 and beta 11.2 has issues with my nvidia gtx260m video card. I have an Asus G71gx-RX05 from Best Buy. Currently I am running Ubuntu with the enabled drivers working for video.... Just like to try both and learn the differences....

on a side note the intel 5300 rocks with windows 7 i had low signal in my bathroom on the 2nd level with the standard ar928x that came with my laptop. i then tried a gigbyte one with mimo and it had the same issue with low signal... i do have a linksys wrt600n....
also how is the intel 5350 with wimax.... i am thinking of getting that one i have a asus g71gx-rx05  from best buy..... i just thought for future useage. also anyone know of a dual band (2.4 and 5 ghz) with bluetooth ..... intel perhaps?
\

anyone?

---

### Post by dzuchowski on 2009-08-24
Anyone have any ideas on how to get the intel 5300 to work. I am using the 64bit versions of Ubuntu and Kubuntu. I have tried both in regular release and the bets releases being 64 bit versions. Please help.../.


I upgraded the wifi which was an Atheros unit. I went with an Intel 5300 that has dual radio channel supper and mimo technology as i have a Linksys wrt-600n router. I do not use the 5ghz radio but still like to have the option.... that is why i got this card and because i had poor reception with the original Atheros card.... However now linux unbuntu 9.0 and 9.1 beta and also Linux Mint and Open Suse 11.1 and 11.2 beta will not "see" the wifi card. It works in Windows 7 just fine. I do to the network manager and select wireless but it is grayed out and can not select it. I tried the betas of Open Suse and Ubuntu and Kbuntu because of the updated kernals that as i thought have support ffor this card the intel 5300. any ideas on how to get it working. I am using linux 64 bit versions as i have a 64bit core 2 duo processor.
[URL="http://www.bestbuy.com/site/olspage.jsp?skuId=9366615&type=product&id=1218092150740"]
http://www.bestbuy.com/site/olspage.jsp?skuId=9366615&type=product&id=1218092150740[/URL]

[IMG]http://pemmzgadget.com/images/g71gxr-x05.jpg[/IMG]  [IMG]http://i.i.com.com/cnwk.1d/sc/33695862-2-440-0.gif[/IMG]

---

### Post by chili555 on 2009-08-24
This is supposed to work with the module *iwlagn*. Please make sure the hardware wireless switch is on and then open a terminal and do:```
sudo modprobe iwlagn
sudo cat /var/log/messages | grep iwlagn
```Any signs of life?

---

### Post by dzuchowski on 2009-08-24
> **chili555 said:**
> This is supposed to work with the module *iwlagn*. Please make sure the hardware wireless switch is on and then open a terminal and do:```
sudo modprobe iwlagn
sudo cat /var/log/messages | grep iwlagn
```Any signs of life?

I have the intel 5300 wifi card.....

[SIZE=4][COLOR=Red]I booted with the live cd of kbuntu 9.1 beta and got this[/COLOR][/SIZE][SIZE=4]
[/SIZE] 
sudo cat /var/log/messages | grep iwlagn
ubuntu@ubuntu:~$ sudo modprobe iwlagn
ubuntu@ubuntu:~$ sudo cat /var/log/messages | grep iwlagn
Aug 24 16:07:12 ubuntu kernel: [   47.119347] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Aug 24 16:07:12 ubuntu kernel: [   47.119350] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Aug 24 16:07:12 ubuntu kernel: [   47.119486] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 24 16:07:12 ubuntu kernel: [   47.119522] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Aug 24 16:07:12 ubuntu kernel: [   47.156086] iwlagn 0000:07:00.0: PCI INT A disabled
Aug 24 16:07:12 ubuntu kernel: [   47.156206] iwlagn: probe of 0000:07:00.0 failed with error -22

______________________________________________________________________________________________________________


[SIZE=4][COLOR=Lime]Here is what I got after a fresh install of kbuntu 9.1 beta[/COLOR][/SIZE]

donald@Frogsnot:~$ sudo modprobe iwlagn
[sudo] password for donald:
donald@Frogsnot:~$ sudo cat /var/log/messages | grep iwlagn
Aug 24 17:01:26 Frogsnot kernel: [   10.526812] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Aug 24 17:01:26 Frogsnot kernel: [   10.526814] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Aug 24 17:01:26 Frogsnot kernel: [   10.526995] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug 24 17:01:26 Frogsnot kernel: [   10.527024] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Aug 24 17:01:26 Frogsnot kernel: [   10.563343] iwlagn 0000:07:00.0: PCI INT A disabled
Aug 24 17:01:26 Frogsnot kernel: [   10.563358] iwlagn: probe of 0000:07:00.0 failed with error -22
donald@Frogsnot:~$


_____________________________________

Also do you think i should install ubuntu 9.1 with gnome and then also install kde 4.3? Also what do you think of open suse

---

### Post by chili555 on 2009-08-24
> Also do you think i should install ubuntu 9.1 with gnome and then also install kde 4.3?No. First, we need to figure out and correct this:> iwlagn: probe of 0000:07:00.0 [COLOR="Red"]failed with error -22[/COLOR]
Since you have seen this in both a live CD and a fresh install, another fresh install is not likely to make it any better.

I have googled this quite a bit and, so far, come up with nothing; I will keep trying. I suggest you search for it, too.> Also what do you think of open suseI have never tried it.

---

### Post by dzuchowski on 2009-08-24
> **chili555 said:**
> No. First, we need to figure out and correct this:Since you have seen this in both a live CD and a fresh install, another fresh install is not likely to make it any better.

I have googled this quite a bit and, so far, come up with nothing; I will keep trying. I suggest you search for it, too.I have never tried it.

Thanks for the help. I will also continue to google as well. I cant get much other then the latest kernal has it in it after .24 release.

---

### Post by dzuchowski on 2009-08-26
I tried to copy the firmware to the /lib/firmware directory but cant find out how to copy the directory over to that or does it only need the file from the archieve.

however i have read several people saying it works out the box with linux like ubuntu 8.1 but why does it not work with 9.04 or 9.1 beta?

---

### Post by jward3010 on 2009-10-03
I want to keep this alive.

I've just installed Karmic BETA and although the card is detected by the kernel and the system, under network manager it is appearing as "wireless is disabled".

I have done "modprobe" stuff above, here's my output:
```
**john@vostro:~$ sudo cat /var/log/messages | grep iwlagn**
Oct  3 18:40:32 vostro kernel: [   11.688555] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 18:40:32 vostro kernel: [   11.688558] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 18:40:32 vostro kernel: [   11.688609] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 18:40:32 vostro kernel: [   11.688636] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 18:40:32 vostro kernel: [   11.727997] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:31:59 vostro kernel: [    8.105604] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:31:59 vostro kernel: [    8.105607] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:31:59 vostro kernel: [    8.105690] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:31:59 vostro kernel: [    8.105767] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:31:59 vostro kernel: [    8.147288] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:40:21 vostro kernel: [    9.349489] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:40:21 vostro kernel: [    9.349492] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:40:21 vostro kernel: [    9.349587] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:40:21 vostro kernel: [    9.349665] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:40:21 vostro kernel: [    9.389659] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:49:39 vostro kernel: [    7.921189] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:49:39 vostro kernel: [    7.921191] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:49:39 vostro kernel: [    7.921274] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:49:39 vostro kernel: [    7.921351] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:49:39 vostro kernel: [    7.960941] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
```

Here's the output of "sudo iwlist scanning"
```
**john@vostro:~$ sudo iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

---

### Post by dzuchowski on 2009-10-03
> **jward3010 said:**
> I want to keep this alive.

I've just installed Karmic BETA and although the card is detected by the kernel and the system, under network manager it is appearing as "wireless is disabled".

I have done "modprobe" stuff above, here's my output:
```
**john@vostro:~$ sudo cat /var/log/messages | grep iwlagn**
Oct  3 18:40:32 vostro kernel: [   11.688555] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 18:40:32 vostro kernel: [   11.688558] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 18:40:32 vostro kernel: [   11.688609] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 18:40:32 vostro kernel: [   11.688636] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 18:40:32 vostro kernel: [   11.727997] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:31:59 vostro kernel: [    8.105604] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:31:59 vostro kernel: [    8.105607] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:31:59 vostro kernel: [    8.105690] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:31:59 vostro kernel: [    8.105767] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:31:59 vostro kernel: [    8.147288] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:40:21 vostro kernel: [    9.349489] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:40:21 vostro kernel: [    9.349492] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:40:21 vostro kernel: [    9.349587] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:40:21 vostro kernel: [    9.349665] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:40:21 vostro kernel: [    9.389659] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Oct  3 19:49:39 vostro kernel: [    7.921189] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Oct  3 19:49:39 vostro kernel: [    7.921191] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Oct  3 19:49:39 vostro kernel: [    7.921274] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct  3 19:49:39 vostro kernel: [    7.921351] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Oct  3 19:49:39 vostro kernel: [    7.960941] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
```Here's the output of "sudo iwlist scanning"
```
**john@vostro:~$ sudo iwlist scanning**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```


upgrade to the intel 5350 wimax card that should work... even though it is the same wifi part to it for some reason it works...

---

### Post by jward3010 on 2009-10-04
Well, rather than upgrade hardware I'll just have to stick with Jaunty which is a fine OS anyway. I've filed a bug report and hopefully there will be a fix.

Or of course use WICD, which is what I'm currently doing.

---

### Post by rizay on 2010-01-22
Thank jward3010.  Was having this problem for a couple of weeks.  Installing wicd and rebooting worked for me.  I'm using a 64-bit version of Kubuntu Karmic myself on a Dell Precision m2400.  It has a 5300 AGN wireless card.

---

