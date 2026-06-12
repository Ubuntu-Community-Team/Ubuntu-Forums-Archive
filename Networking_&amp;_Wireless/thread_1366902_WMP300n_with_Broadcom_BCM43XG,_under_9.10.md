---
title: "WMP300n with Broadcom BCM43XG, under 9.10"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by SalaryUltraman on 2009-12-28
Hello, I have been trying for quite a while to install my wireless Linksys WMP300n in Ubuntu 9.10. After experimenting with various ways to do so, and following instructions found on many threads, I still can't get the connection to work.

The weird thing is that the wireless access works really well using the STA driver, in Live CD mode or the first time I activate the driver after a fresh installation, but not after. There must be a little something missing...

I tried reinstalling the bmcwl-kernel-source package after the installation, but no success.

I have tried blacklisting the b43-connected modules, and fwcutter is not installed on my machine.

I have tried to manually create an access point using the AP name and the wireless card's MAC address, but couldn't connect.

I post the output of some commands here:

sudo iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth3      IEEE 802.11bgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.
```sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth3      No scan results

eth1      Interface doesn't support scanning.
```lspci -vnn | grep 14e4
```
01:05.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
```Any idea?

Thank you in advance!

---

### Post by SalaryUltraman on 2009-12-29
I was wondering, could it have anything to do with the fact that the device is recognized as eth3, instead of wlan0?

---

### Post by jaysmit9 on 2009-12-29
I have the exact same issue.  Just reinstalled for the 10th time..  Worked perfectly initially installed.  Worked again on the first reboot.  Nothing thereafter.

---

### Post by jaysmit9 on 2009-12-29
I just remembered I setup WEP and it stopped working after that.  I removed WEP but cannot see anything in the wireless list.  I am showing as eth1.  I get this in the dmesg output:

[   14.508515] airo(eth1): set_wep_key: key length to set was zero
[   14.508526] airo(eth1): failed to set WEP key at index 0: -1.
[   14.508647] airo(eth1): set_wep_key: key length to set was zero
[   14.508652] airo(eth1): failed to set WEP key at index 1: -1.
[   14.508682] airo(eth1): set_wep_key: key length to set was zero
[   14.508687] airo(eth1): failed to set WEP key at index 2: -1.
[   14.508715] airo(eth1): set_wep_key: key length to set was zero
[   14.508721] airo(eth1): failed to set WEP key at index 3: -1.
[   14.519719] airo(eth1): cmd:1 status:7f01 rsp0:88 rsp1:ff10 rsp2:a0
[   14.519733] airo(eth1): Bad MAC enable reason=88, rid=ff10, offset=160
[   14.727388] airo(eth1): cmd:103 status:7f03 rsp0:0 rsp1:ff10 rsp2:a0

---

### Post by SalaryUltraman on 2009-12-30
When you say you setup WEP, you mean you chose an access point protected with WEP, and entered a key for it?

---

### Post by SalaryUltraman on 2009-12-31
Anybody has a suggestion of something to try?

---

### Post by SalaryUltraman on 2010-01-06
Went back to use ndiswrapper. It works, but it still doesn't make sense having to rely on it when there is an actual Broadcom driver. (working perfectly in LiveCD mode!)

---

### Post by A4orce84 on 2010-01-14
SalaryUltraman,

Can you post how you did this using NDISWRAPPER?

I'm a linux newbie trying to get my WMP300n adapter working in Ubunutu 9.10 as well. =(


Thanks man!


--Asif

---

### Post by gehzumteufel on 2010-01-19
And here I thought I was the ONLY one with this issue. I have the same problem. Can't detect anything. It never worked from the start. I have tried so many different things, to no avail.

I have yet to go the NDISwrapper route, as I would rather not. That is just asinine that it works in earlier versions, but not 9.10. I am on Kubuntu as opposed to Ubuntu.

---

