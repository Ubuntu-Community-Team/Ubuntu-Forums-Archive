---
title: "Possible explanation but no fix"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Pete051 on 2009-11-03
I've been investigating this connection problem and so far I've tried lsmod | grep rt and this tells me:
rt73usb                26336  0
crc_itu_t               1852  1 rt73usb
rt2500usb              21152  0
rt2x00usb              11548  2 rt73usb,rt2500usb
rt2x00lib              29756  3 rt73usb,rt2500usb,rt2x00usb
led_class               4096  1 rt2x00lib
parport                35340  2 ppdev,lp
input_polldev           3716  1 rt2x00lib
mac80211              181236  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
agpgart                34988  2 drm,sis_agp

Hmm lsusb shows thet wifi adapter is a rt73 so whats that rt2500 moduule doing there? this is confirmed by dmesg | grep rt which tells me amongst other things: 

dmesg | grep rt
21.731041] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   21.731049] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   21.731110] usbcore: registered new interface driver rt2500usb

So I tried modprobe -r rt2500usb which did remove it from the kernel but didn't improve the connection.
As shown by iwconfig:

wlan0     IEEE 802.11bg  ESSID:"TalkTalk520"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:E3:DC:9A:59
          Bit Rate=1 Mb/s   Tx-Power=16 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=30/70  Signal level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg | grep rt73 gives:

dmesg | grep rt73

   22.293821] Registered led device: rt73usb-phy1::radio
[   22.293841] Registered led device: rt73usb-phy1::assoc
[   22.293858] Registered led device: rt73usb-phy1::quality
[   22.294666] usbcore: registered new interface driver rt73usb
[   23.779346] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[   23.926024] input: rt73usb as /devices/pci0000:00/0000:00:03.3/usb1/1-1/1-1:1.0/input/input10

So that seems to be ok, I've tried blocking rt2500usb by adding the line blacklist rt2500usb to /etc/modprobe.d/blacklist.conf this had no effect.

so to conclude iwconfig shows the card is working just not very well, it seems to be a conflict between rt73 and rt2500 but I don't know how to resolve this. The laptop works fine through an ethernet connection but thats not too handy.
So does anyone have any ideas? please.
Regards
Pete

---

