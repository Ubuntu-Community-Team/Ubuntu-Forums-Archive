---
title: "WiFi inoperative on Lenovo G575"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by tempgrafeio2k10 on 2012-11-29
Dear All,
 
 My case concerns a **Lenovo G575 laptop** that can not see and connect to ANY WLAN.
OS is **Ubuntu 12.04 LTS 64bit**.
In Lenovo's site I could not find any specs for the W-NIC, so I opened the case and it seems it is an **Atheros AR5B95** mini PCI.
Wired Ethernet connectivity works fine.
 
Any help will be greatly appreciated.
 
 
Thank you in advance.

---

### Post by chili555 on 2012-11-29
Instead of opening the case, please open a terminal and run and post here:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by tempgrafeio2k10 on 2012-11-29
> **chili555 said:**
> Instead of opening the case, please open a terminal and run and post here:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.
 
Thank you for the quick response!
 
The output I got was:
 
03:00.0 "0280" "168c" "002b" -r01 "17aa" "30a1"

---

### Post by chili555 on 2012-11-29
I think you typed lspci -nM and not nN, but I get the gist. Please run and post:```
sudo modprobe ath9k
dmesg | grep ath9k
rfkill list all
```Thanks.

---

### Post by tempgrafeio2k10 on 2012-11-29
> **chili555 said:**
> I think you typed lspci -nM and not nN...

Argh! Sorry for the typo. Too little sleep you see!

The correct output is:

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

...I will follow up with the remaining commands immediately.

---

### Post by tempgrafeio2k10 on 2012-11-29
> **chili555 said:**
> 
...
Please run and post: sudo modprobe ath9k
...


modprobe returned nothing.

---

### Post by tempgrafeio2k10 on 2012-11-29
...
dmesg | grep ath9k
...
Returned:

[ 8751.734452] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8751.734479] ath9k 0000:03:00.0: setting latency timer to 64
[ 8751.804807] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 8751.806443] Registered led device: ath9k-phy0

---

### Post by tempgrafeio2k10 on 2012-11-29
> **chili555 said:**
> 
...
rfkill list all
...

This returned:
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

... Please let me know of any other info you require.

---

### Post by chili555 on 2012-11-29
Your wireless should be working perfectly. Let's check:```
iwconfig
sudo iwlist wlan0 scan
```Can you click the Network Manager icon, see your network and connect?

---

### Post by tempgrafeio2k10 on 2012-11-29
> **chili555 said:**
> Your wireless should be working perfectly. Let's check:```
iwconfig
sudo iwlist wlan0 scan
```Can you click the Network Manager icon, see your network and connect?
Hey! It WORKS! Thank you SO very much!

Whenever you got time please tell me what could be the problem?

I can see WLANs now. Tomorrow I'll check with a known one that I can connect to.

I MUST get some sleep. Till tomorrow, good bye everybody.

---

### Post by chili555 on 2012-11-29
We can see by the timestamp here that the driver didn't, for whatever reason, load on boot as expected:> [ [COLOR="Red"]8751[/COLOR].734452] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17Ordinarily, the driver should load in the first 20-25 seconds. I suspect it only loaded when you loaded it.> sudo modprobe ath9kLet's tell the system to load it no matter what, so help me Chili!```
sudo su
echo ath9k >> /etc/modules
exit
```You should be all set.

---

