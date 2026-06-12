---
title: "Wireless problems"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by brick2 on 2013-07-02
Hello and thank you in advance for any time you could spare to help me out.

Same old story I m having problems with my wirelss connection but there are a couple of really wierd thigs going on.

1. I can install the drivers via additional drivers with no problem and it seams that they are installed. But I cant see any connection nor can I connect to any.
2. After like a billion resets every once in a while they do work.

Device: 08:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)           
dell laptop


Here is what I have done thus far.

1. sudo apt-get install linux-headers-generic bcmwl-kernel-source 
Output was simply that nothing new was installed.

2.iwconfig

eth0      no wireless extensions.

eth2      IEEE 802.11abg  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          
lo        no wireless extensions.


rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | grep wl

[    6.842119] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.873129] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.866782] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   13.133459] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   16.569718] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   33.123180] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   50.923309] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   51.104594] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   71.090510] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  101.063360] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  141.023749] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  190.979853] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  250.924845] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  310.869322] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  370.809782] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  430.759046] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  490.703766] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  550.647547] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  610.591399] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  670.537510] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  730.480251] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  790.426390] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  850.399588] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  910.375182] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  970.349774] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1030.320884] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1090.296809] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1150.274023] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1210.246425] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1270.223494] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1330.197675] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1390.171976] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1450.146792] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1510.121509] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1570.096805] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1630.070868] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1690.045522] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1750.020975] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1809.995417] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1869.969473] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1929.944374] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1989.919417] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2049.893746] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2109.868577] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2170.249170] ERROR @wl_dev_intvar_get : error (-1)
[ 2170.249177] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 2178.970693] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2178.970837] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2198.838945] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2228.861357] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2237.044982] ERROR @wl_dev_intvar_get : error (-1)
[ 2237.044989] ERROR @wl_cfg80211_get_tx_power : error (-1)

3.

sudo apt-get update sudo apt-get upgrade

All is up to date.

4. 
sudo apt-get update sudo apt-get -y upgrade sudo apt-get install --reinstall bcmwl-kernel-source

dmesg | grep wl

[   17.896127] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.933227] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   19.300875] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   19.301052] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   19.944069] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   25.367307] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   25.367494] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   47.484044] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)                 

Could you please help me out here.

---

### Post by brick2 on 2013-07-02
O yeas so sorry for this I am using  ubuntu 12.4

---

### Post by westie457 on 2013-07-02
Hi, the Broadcom STA driver does not work with your card, all being well this should get you up and running.

With an ethernet cable plugged in run these commands in a terminal please.
```
sudo apt-get purge bcmwl-kernel-source
``` to remove the non-working one. Then run ```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer 
```

It might be easier to copy and paste the commands.

When the terminal has finished wait a few seconds for the dust to settle and check the Network-Manager icon at the top of the screen for any available networks.

If none show just reboot the machine and all should be working.

Let us know how it goes.

Thank you.

---

### Post by brick2 on 2013-07-02
Thank you very much, I got it working, well to be exact you got it working.
The response time of people on this forum is ridiculously short how you manage to do it is beyond me.

---

### Post by ajgreeny on 2013-07-02
> The response time of people on this forum is ridiculously short how you manage to do it is beyond me. 						
Because at the moment there are 12596 forum users online.  This forum is about the largest and certainly the most active one that I've ever been a member of, and I have found it to be the most valuable linux learning experience since I started using ubuntu back in 2005 at version 5.04 or 5.10.

---

