---
title: "Intel PRO/Wireless 3945 | UNR 9.04 | MSi Wind U100"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by ichinan on 2009-04-24
Good morning,
 
I am hoping someone here might be able to help me fix a wifi problem I am having on my netbook. I am completely new to Ubuntu, and so I feel rather helpless about this.
 
The netbook an MSi Wind u100. I expanded its RAM to 2gigs. I replaced its wifi card, "Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express", with an "Intel Corporation PRO/Wireless 3945ABG".
 
I dual booted Ubuntu 8.10 and Windows XP. The new wifi card was working great. Then, I decided to do a full installation (no dual booting) of Ubuntu Netbook Remixed 9.04 last night. Installation was successfull, but now I can't detect the wireless network.
 
Network Connections lists "Auto eth0" under the Wired tab. There is nothing under the Wireless tab.
 
In terminal, when i run the lspci command this shows up:
 
Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express
Network Controller: Intel Corporation PRO/Wireless 3945ABG
 
Can anyone help me get this thing working? Its tough for me as I am not at home so I must use a USB stick and my work PC to shuttle files across to the netbook. (I am not an IT person, and so manually switching the network cable from the PC to the netbook doesn't work as its password protected by Cisco.)
 
Thank you so much! T_T
 
Edit:
 
Just saw the thread stating instructions for posting. I have to type these by hand, so I skipped the super long ones... if something is needed I can go and type it out if you're specific.
 
**ifconfig:**
 
lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU: 16436 Metric: 1
RX packets: 8 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 8 errors: 0 dropped: 0 overruns: 0 frame: 0
collisions: 0 txqueuelen: 0
RX bytes: 516 (516:. B) TX bytes: 516 (516.0 B)
 
 
**iwconfig:**
 
lo no wireless extensions.
 
eth0 no wireless extensions.
 
wmaster0 no wireless extensions.
 
wlan0 IEEE 802.11abg ESSID: " "
Mode: Managed Frequence: 2.41 GHz Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit: 7 RTS thr: off Fragment thr=2352 B
Power management: off
Link Quality: 0 Signal level: 0 Noise Level: 0
(all 0)
 
pan0 no wireless extensions
 
**lsmod:**
 
mac80211 iwl3945
led_class iwl3945
cfg80211 iwl3945, mac80211
 
**sudo lshw -C network:**
 
*-network DISABLED
description: Ethernet Interface
product: RTL801E/RTL8102E PCI Express Fast Ethernet Controller
 
*-network DISABLED
description: wireless interface
product: PRO/Wireless 3945ABG [Golan] Network Cnnection
 
*-network DISABLED
description: Ethernet Interface

---

### Post by ichinan on 2009-04-24
No idea why, but after shutting down and restarting a few times the wifi began working again?
 
I'll consider the issue solved for now...

---

