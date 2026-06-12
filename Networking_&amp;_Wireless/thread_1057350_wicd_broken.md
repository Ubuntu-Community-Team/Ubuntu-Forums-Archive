---
title: "wicd broken"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by ray field on 2009-02-01
wicd broken

since I installed the latest updates -- which mysteriously caused trouble on a kernel they didn't touch -- my wicd is broken.  it used to see 6 or 7 wlans, but now apparently sees nothing.

not really sure how to diagnose/resolve, but I see sometimes the results of "lspci -nnm": can be useful:

00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GME Express Memory Controller Hub [27ac]" -r03 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 945GME Express Integrated Graphics Controller [27ae]" -r03 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [27a6]" -r03 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [834a]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 2 [27d2]" -r02 "" ""
00:1c.2 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 3 [27d4]" -r02 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 4 [27d6]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r02 -p20 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1f.2 "IDE interface [0101]" "Intel Corporation [8086]" "82801GBM/GHM (ICH7 Family) SATA IDE Controller [27c4]" -r02 -p80 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r02 "ASUSTeK Computer Inc. [1043]" "Device [830f]"
01:00.0 "Network controller [0280]" "RaLink [1814]" "Device [0781]" "RaLink [1814]" "Device [2790]"
04:00.0 "Ethernet controller [0200]" "Attansic Technology Corp. [1969]" "L1 Gigabit Ethernet Adapter [1026]" -rb0 "ASUSTeK Computer Inc. [1043]" "Device [8324]"

---

### Post by imdano on 2009-02-02
What's the output of "iwlist scan"?

---

### Post by ray field on 2009-02-02
thanks -- actually I managed to figure out that the drivers weren't being loaded, and downloaded & installed a set for eeePCs that a developer had talked about on the eeePC forum.  with those the card recognized the area wlans, and once I ticked off "AES" for the cipher type in the router setup, everything started working nicely.

---

