---
title: "Wireless Trouble [hard block]"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by geeko_one on 2012-03-24
I used Lenovo 370, my wireless suddenly not working properly. When I checked in rfkill there's a hardblock in phy0. I already turn on the wireless switch, even tough in BIOS setting. I already unblocked all but the hard block still appears. When booting I was seen the wireless light indicator ON, but the light suddenly OFF in logon screen.

uname -a
```

Linux notebook 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686 i686 i386 GNU/Linux

```

rfkill list
```

0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes


```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ppp0      no wireless extensions.


```

lspci -nnk
```

06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: Lenovo Device [17aa:30a1]
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

---

### Post by bkratz on 2012-03-25
In the terminal look at the output of 

lsmod

(LSMOD in lowercase) and see if a module exists called acer_wmi ( for some reason Lenovo's often seem to have it)

If it is there try

sudo rmmod -f acer-wmi

(don't worry this would only be temporary and would return on reboot).  Without rebooting retry wireless, if it works we can make it permanent with blacklisting the driver.

---

### Post by geeko_one on 2012-03-26
> **bkratz said:**
> In the terminal look at the output of 

lsmod

(LSMOD in lowercase) and see if a module exists called acer_wmi ( for some reason Lenovo's often seem to have it)

If it is there try

sudo rmmod -f acer-wmi

(don't worry this would only be temporary and would return on reboot).  Without rebooting retry wireless, if it works we can make it permanent with blacklisting the driver.

there's no acer_wmi, or this result can be helpful.. 

lsmod | grep ath
```
dm_multipath           22771  0 
ath9k                 111002  0 
mac80211              406860  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              320407  2 ath9k,ath9k_common
ath                    19148  2 ath9k,ath9k_hw
cfg80211              171447  3 ath9k,mac80211,ath
```

---

### Post by Askme Later on 2012-05-27
Try shutting down(if not already off), disconnecting the power, remove  battery(if it is a laptop), press power a few times to release stored  energy, reinsert battery(if it is a laptop), reconnect AC power. Turn on  computer. Worked for me. After trying multiple fixes I found on the  internet I remembered reading this somewhere. My hardware was blocked  via a hardware switch(fn+f8 which doesn't work in ubuntu(works with  windows, but uninstalled windows). rfkill showed 0: phy0: Wireless Lan  as Hard Blocked.

---

### Post by mbraidy on 2012-06-21
try:

gksu rfkill unblock all

---

### Post by geeko_one on 2012-07-27
thanks for all help, my wireless was working done while I turn into default my BIOS setting :)

---

