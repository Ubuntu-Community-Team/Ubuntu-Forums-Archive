---
title: "Thinkpad X220 no Wi-Fi on boot after update to 13.04"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by igorsh on 2013-05-07
I have Thinkpad X220i with Centrino Wireless-N 1000 wi-fi card and 64-bit version of Ubuntu.
Wi-Fi stop working after boot after update to Ubuntu 13.04 until I manually reload driver.
What I have immediatly after boot (without working wi-fi):
*dmesg | grep iwlwifi* :
```

    [    2.096616] iwlwifi 0000:03:00.0: irq 42 for MSI/MSI-X
    [    2.099998] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138

```
*iwconfig* and *rfkill list* don't see interface at all, for example output from *iwconfig*:
```

    eth0      no wireless extensions.
    lo        no wireless extensions.
    virbr0    no wireless extensions.

```
but *lshw* see wireless card correctly (sorry for fieldnames in russian, but you get the point):
```

 *-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: Network controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Centrino Wireless-N 1000 [Condor Peak]
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corporation
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       &#1089;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1086; &#1096;&#1080;&#1085;&#1077;: pci@0000:03:00.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress bus_master cap_list
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=iwlwifi latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:42 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f2400000-f2401fff

```
I simply do **sudo modprobe -r iwlwifi && sudo modprobe iwlwifi** and everything start work normal.
*dmesg | grep iwlwifi* become complete:
```

    [  487.933893] iwlwifi 0000:03:00.0: irq 42 for MSI/MSI-X
    [  487.938878] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
    [  487.969885] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
    [  487.969891] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
    [  487.969894] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
    [  487.969896] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
    [  487.969899] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
    [  487.969902] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
    [  487.969995] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
    [  488.021674] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
    [  488.029668] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3
    [  488.157453] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
    [  488.164869] iwlwifi 0000:03:00.0: Radio type=0x0-0x0-0x3

```
and *lshw -c network* become more informative:
```

*-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Centrino Wireless-N 1000 [Condor Peak]
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Intel Corporation
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       &#1089;&#1074;&#1077;&#1076;&#1077;&#1085;&#1080;&#1103; &#1086; &#1096;&#1080;&#1085;&#1077;: pci@0000:03:00.0
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: wlan0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 8c:a9:82:6d:80:8a
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm msi pciexpress bus_master cap_list ethernet physical wireless
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=iwlwifi driverversion=3.9.0-030900-generic firmware=39.31.5.1 build 35138 ip=10.11.253.97 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:42 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f2400000-f2401fff

```
What I already try and it doesn't help:
- enable different module parameters for iwlwifi: fw_restart, 11n_disable, bt_coex_active
- install mainline kernel 3.9 instead of default 3.8 (you can see it in last lshw output)
- install compat-drivers from compat-drivers-2013-03-28-5-u
- reset BIOS settings to default
- update BIOS to newest version

Is it race condition on boot? Is it problem in driver? Help me with solving that problem.

---

### Post by igorsh on 2013-05-08
I try boot from LiveCD and everything works correctly out of the box.
It seems my system collect too many garbage libs, drivers, etc. in 2 years of updates, experimenting and such.
I will make clean install.

---

