---
title: "x300 rfkill switch not functioning"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by tzaddi on 2009-03-26
I have been running 8.10 (fully patched) on my Lenovo x300 for many months now with no problems.  This morning, I was using my wireless connection as usual.  I shut down the laptop to go home, but when I got home nothing wireless would work anymore, not bluetooth, not wifi (Intel 4965) and not the built-in WWAN module.  dmesg tells me that these things have been disabled by the rfkill swtich:

iwlagn: Radio disabled by HW RF Kill switch

This laptop does not have an analog switch, but rather a key combination (Fn-F5);  however, this key combination will not re-enable my wireless.  In fact, it seems to do nothing at all.  Nor will messing with /sys/class/net/wlan0/device/rfkill/rfkill0/state:

root@mercury:/sys/class/net/wlan0/device/rfkill/rfkill0# echo "1" > state 
-su: echo: write error: Operation not permitted
root@mercury:/sys/class/net/wlan0/device/rfkill/rfkill0# echo "0" > state 
root@mercury:/sys/class/net/wlan0/device/rfkill/rfkill0# echo "2" > state 
-su: echo: write error: Invalid argument

Regardless of what I echo, cat'ing "state" still gives a "2".

I have reset the BIOS, and made sure that the BIOS setting for the wireless is "On".  Any ideas would be appreciated;  this is killing my productivity!

One more relevant tidbit:
root@mercury:/sys/class/net/wlan0/device# cat version 
fw not loaded
EEPROM version: 0x36
Why would the firmware not be loaded?


uname -a:
Linux mercury 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Relevant dmesg output:
[    9.048195] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.048201] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.053507] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.053544] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.053612] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    9.101149] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.264799] iwlagn 0000:03:00.0: PCI INT A disabled
[    9.282420] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   31.023035] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.023221] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   31.023574] firmware: requesting iwlwifi-4965-2.ucode
[   31.038146] iwlagn: Radio disabled by HW RF Kill switch

Let me know if you need anything else.

Thanks,
Kevin

---

### Post by tzaddi on 2009-03-26
More information:

[   10.204481] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   10.204485] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   10.204489] thinkpad_acpi: ThinkPad BIOS 7TET34WW (1.08 ), EC 7THT15WW-1.00c
[   10.204493] thinkpad_acpi: Lenovo ThinkPad X300, model 6476CTO
[   10.205590] thinkpad_acpi: radio switch found; radios are disabled
[   10.205784] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   10.205789] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   10.219698] thinkpad_acpi: Lenovo BIOS switched to ACPI backlight control mode
[   10.219703] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...

---

### Post by tzaddi on 2009-03-27
I just tried the 9.04 beta, and the rfkill key combination Fn-F5 is not recognized there either.  I am a hair's breadth away from installing Windows temporarily just so that I can re-enable wireless.  Someone please stop me!

---

### Post by chili555 on 2009-03-27
> This laptop does not have an analog switchI believe it does. Would you please check it? Item #7 says it's the 'Wireless radio switch.'[IMG]http://farm4.static.flickr.com/3600/3390334454_c235556edc_o.png[/IMG]

---

### Post by tzaddi on 2009-03-27
> **chili555 said:**
> I believe it does. Would you please check it? Item #7 says it's the 'Wireless radio switch.'[IMG]http://farm4.static.flickr.com/3600/3390334454_c235556edc_o.png[/IMG]

D'oh!  My apologies for wasting everyone's time with such a Homer Simpson moment...  That worked.

---

