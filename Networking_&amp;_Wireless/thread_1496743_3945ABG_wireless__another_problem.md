---
title: "3945ABG wireless  another problem"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by Mudsucks on 2010-05-29
Hi, Please help me get my wireless network to work with Ubuntu 8.04 -desktop-emc2-aj13-i386. Wireles card is **intel 3945AB**

Tried:
mcnc@mcnc-laptop:~$ dmesg | grep iwl
[   46.209430] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   46.209433] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   46.209622] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   47.540426] iwl3945: Radio Frequency Kill Switch is On:
[   47.545643] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   47.555686] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   47.575624] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   47.603047] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   47.643557] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
mcnc@mcnc-laptop:~$ rfkill list all
bash: rfkill: command not found

What's with the Kill Switch On and the rfkill command not found. ](*,)

---

