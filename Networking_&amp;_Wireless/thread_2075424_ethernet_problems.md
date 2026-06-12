---
title: "ethernet problems"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by lorena86 on 2012-10-23
Dear Ubuntu experts,

I have Ubuntu 12.04 LTS and Windows 7 as a dual boot on my ASUS K53S laptop. Connecting to wireless works just fine within both Windows and Ubuntu. Connecting to the ethernet, however, only works fine with windows and does not work with Ubuntu.

Do you have any idea what could be going on?

Any help is greatly appreciated!!!

Cheers,

Lorena
-----------------------------------------------------------------------
Here are the results of:
lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 100 [8086:08ae]
    Subsystem: Intel Corporation Centrino Wireless-N 100 BGN [8086:1005]
    Kernel driver in use: iwlwifi
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
    Kernel modules: r8169

---

