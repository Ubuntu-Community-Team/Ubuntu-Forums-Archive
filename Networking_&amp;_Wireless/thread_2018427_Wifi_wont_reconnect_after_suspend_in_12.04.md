---
title: "Wifi wont reconnect after suspend in 12.04"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by clivej on 2012-07-06
Every-time I suspend and wake my system, Ubuntu will not reconnect to my AP.  The AP is working fine with other devices and also works under 11.10.  dmesg reports the following :
```

[58636.500095] wlan0: direct probe to <mac address>  (try 1/3)
[58636.700036] wlan0: direct probe to <mac address>  (try 2/3)
[58636.904303] wlan0: direct probe to <mac address> (try 3/3)
[58637.104036] wlan0: direct probe to <mac address>  timed out
```Network Manager also repeatedly asks for the AP passphase.

One clue I've discovered is that if I change the channel number on the AP, 12.04 will reconnect fine, but this is time consuming and hardly a fix!  Anyone any ideas what is wrong?

I'm not sure it ifs related, but Im also seeing huge activity on my wired connection, even though I dont use it and its not plugged in !!

---

### Post by clivej on 2012-07-12
Can anyone help ? It works fine until I suspend and wake.

```
> rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
> lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Toshiba America Info Systems Device [1179:ff50]
    Kernel driver in use: atl1c
--
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8152]
    Kernel driver in use: rtl8192se

```

---

### Post by Kirk Schnable on 2012-07-15
I find suspend is always buggy, no matter what operating system or hardware you're using. I try to stay away from it. 

Nevertheless, let's have a look at your driver and kernel versions. Please post the output of:

```
uname -r
```

```
modinfo rtl8192se
```

Kirk

---

### Post by clivej on 2012-07-22
```
>uname -r
3.2.0-26-generic

```

```
>modinfo rtl8192se
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     DBF9BFEC2956537D0AFADA5
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

```

---

### Post by clivej on 2012-07-22
The module seems to resume fine.  

If I change the channel my AP uses, Ubuntu will connect to my network without any further intervention.

---

### Post by Toz on 2012-07-22
Try unloading the module prior to suspend and reload on resume. To do this automatically using pm-utils, create the file **/etc/pm/config.d/rtl8192se**:
```
sudo gedit /etc/pm/config.d/rtl8192se
```
...add the following content:
```
SUSPEND_MODULES="rtl8192se"
```
...save the file and try again.

---

### Post by clivej on 2012-07-25
Thanks Toz, that does seem to be working.  Three suspends and its connected every time.  Ill mark the thread as solved!

Do you happen to know why eth0 is showing huge amount of traffic even when it is disconnected?  (See image from Firestarter above)

---

### Post by Toz on 2012-07-25
> **clivej said:**
> Thanks Toz, that does seem to be working.  Three suspends and its connected every time.  Ill mark the thread as solved!
Glad to hear it worked. Thanks for marking it solved.

> Do you happen to know why eth0 is showing huge amount of traffic even when it is disconnected?  (See image from Firestarter above)Looks like it might be some sort of bug. What tool are you using to generate those stats?

---

### Post by clivej on 2012-07-25
Spoke too soon, its still doing it!  It works for suspends less than approx 30min, anything longer still wont connect.

That shapshot is from Firestarter

---

### Post by clivej on 2012-07-25
```
>ifconfig eth0
eth0      Link encap:Ethernet  HWaddr *
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:272962351466430 errors:1637774108798580 dropped:545924702932860 overruns:272962351466430 frame:1364811757332150
          TX packets:272962351466430 errors:1091866585734900 dropped:0 overruns:272966646433725 carrier:545933292867450
          collisions:1364833232168625 txqueuelen:1000 
          RX bytes:272962351466430 (272.9 TB)  TX bytes:272962351466430 (272.9 TB)
          Interrupt:48 

```

---

### Post by Toz on 2012-07-25
> **clivej said:**
> Spoke too soon, its still doing it!  It works for suspends less than approx 30min, anything longer still wont connect.

After 30 minutes of suspend, when the driver stops working, try:
```

sudo modprobe -r rtl8192se
sudo modprobe rtl8192se
```

Does this re-initiatize the driver?

-

One more thing to try is after a fresh reboot, re-initialize the rtl8192se driver like this:
```

sudo modprobe -r rtl8192se
sudo modprobe rtl8192se ips=0
```
...then suspend for greater than 30 minutes and see if you get a connection afterwards.

In the same manner, you might also want to try:
```

sudo modprobe -r rtl8192se
sudo modprobe rtl8192se swlps=1
```
...then suspend for greater than 30 minutes and see if you get a connection afterwards.

You can also try them both toegther:
```

sudo modprobe -r rtl8192se
sudo modprobe rtl8192se ips=0 swlps=1
```

---

### Post by clivej on 2012-07-26
Just now, after a reboot to install updates, it failed to connect to my Wifi.  I had to log onto my router via Android phone and change the channel number in order to connect,

---

### Post by clivej on 2012-07-29
Tried all of your suggestions above, still wont reconnect!

---

### Post by Toz on 2012-07-29
Whats interesting is that it takes 30 minutes on suspend before it stops working. It's like there is some timer somewhere. Is there anything in your bios about power saving that might affect this?

---

### Post by Kirk Schnable on 2012-07-29
> **Toz said:**
> Whats interesting is that it takes 30 minutes on suspend before it stops working. It's like there is some timer somewhere. Is there anything in your bios about power saving that might affect this?

I had a similar thought in reading the last batch of posts.  This seems like the most likely possibility, some power saving feature causing the problem.

---

### Post by Toz on 2012-07-30
> **Kirk Schnable said:**
> I had a similar thought in reading the last batch of posts.  This seems like the most likely possibility, some power saving feature causing the problem.

Yeah, I was hoping one of those modprobe options would disable any power-saving features of the chip, but it didn't work. Was thinking maybe something in the bios.....

Here's another thought:

What does the following return?
```
sudo iwconfig
```
Look at the power management setting for wlan0. If it is set to "on", try turning it off with:
```
sudo iwconfig wlan0 power off
```

---

### Post by clivej on 2012-07-30
I've just upgraded my system to 12.10.  Suspend doesn't work for me, so I dont know it its fixed or not!

Thanks for your suggestions though !

---

### Post by clivej on 2012-07-30
> **Toz said:**
> Yeah, I was hoping one of those modprobe options would disable any power-saving features of the chip, but it didn't work. Was thinking maybe something in the bios.....

Here's another thought:

What does the following return?
```
sudo iwconfig
```Look at the power management setting for wlan0. If it is set to "on", try turning it off with:
```
sudo iwconfig wlan0 power off
```

Power management was off

---

### Post by pekkis924 on 2012-07-30
I have the same problem after installing updates 3 days ago. Before i have never experienced this kind of issue, this laptop has been using ubuntu for 2 years. There is something in latest updates that broke wlan reconnect.

Power management is off by default in my laptop.

---

### Post by clivej on 2012-07-30
> **pekkis924 said:**
> I have the same problem after installing updates 3 days ago. Before i have never experienced this kind of issue, this laptop has been using ubuntu for 2 years. There is something in latest updates that broke wlan reconnect.

Power management is off by default in my laptop.

What is your laptop and who manufacturers your wlan ?

---

### Post by pekkis924 on 2012-07-30
This is Ordi ([http://www.ordi.ee/EPood/BrowseDocuments.aspx?DocID=43](http://www.ordi.ee/EPood/BrowseDocuments.aspx?DocID=43))

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

---

### Post by clivej on 2012-07-30
Mine is a Realtek too.  How do you manage to get it to reconnect?  A reboot?

---

### Post by pekkis924 on 2012-07-30
It asks every time the wlan password after waking up from suspend. Then it reconnects.

---

### Post by clivej on 2012-07-30
> **pekkis924 said:**
> It asks every time the wlan password after waking up from suspend. Then it reconnects.

Mine too, but it would never reconnect unless I shutdown (even reboot wouldnt reset it) or changed the channel on my router

---

### Post by clivej on 2012-08-04
I've upgraded to QQ 12.10.  I know its still alpha but I'm finding I have wifi issues now even after a cold start.  It refuses to connect until I change the channel number on the access point/router.

Im getting the following message repeatedly

```
>dmesg
[  104.436855] wlan0: authenticate with **:**:**:**:**:**
[  104.457420] wlan0: direct probe to **:**:**:**:**:** (try 1/3)
[  104.660047] wlan0: direct probe to **:**:**:**:**:** (try 2/3)
[  104.864035] wlan0: direct probe to **:**:**:**:**:** (try 3/3)
[  105.068038] wlan0: authentication with**:**:**:**:**:** timed out

```

---

### Post by freechelmi on 2012-11-09
Do you still have the issue ? there is  new driver from realtek in september that should correct the probleme for 12.04

---

