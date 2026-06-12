---
title: "USB Wireless works with windows and Ubuntu 9.04-Live  but not 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Bluebirds on 2010-05-07
Help Needed: USB Wireless adapter works with windows and Ubuntu 9.04-Live  but not 10.04
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

This is my first full installation of Linux.

I've been chasing this problem through the forums for the past week.

I had a few issues with the installation (fresh one) but can verify that installation is OK after getting a 20 meter long CAT5 cable today so that I could try a wired connection (not very elegant but it worked and I was able to update the installation and verify that everything else works except the Wireless connection.

I have a desktop PC running XP and have Ubuntu 10.04 installed as a dual boot. My problem also arises however if I run it from a Live 10.4 CD.  Running from a Live 9.04 CD works without problems.

My USB Wireless adapter is a GetNet GN-331U which the manufacturer informs me uses RT3070 chipset.

Problem:  Using a wireless USB connection (or a Live 10.04 CD), when I start 10.04 and try to connect, the network indicator is pulsing but never establishes a connection. Related to this is Firefox starting up in Off-Line mode; resetting this option has no effect on ability to connect.  If I remove the USB connection and connect the ethernet cable everything works fine.
Under windows XP or the Live 9.04 CD both connections work equally well, with no problem.

Here are a few snippets that relate to what's happening.

Any and all suggestions welcomed.

---

### Post by Bluebirds on 2010-05-08
THIS IS WHAT I GET RUNNING 10.04
=================

walt@walt-desktop:~$ tail -f /var/log/messages
May  7 20:31:18 walt-desktop kernel: [   12.584591] usbcore: registered new interface driver rt2800usb
May  7 20:31:18 walt-desktop kernel: [   12.603588] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
May  7 20:31:18 walt-desktop kernel: [   12.614238] rtusb init --->
May  7 20:31:18 walt-desktop kernel: [   12.614303] usbcore: registered new interface driver rt2870
May  7 20:31:18 walt-desktop kernel: [   12.776811] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
May  7 20:31:18 walt-desktop kernel: [   12.902237] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
May  7 20:31:18 walt-desktop kernel: [   12.902755] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
May  7 20:31:19 walt-desktop kernel: [   13.027081] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  7 20:31:27 walt-desktop kernel: [   21.272191] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  7 20:32:19 walt-desktop kernel: [   73.076030] Clocksource tsc unstable (delta = -104697183 ns)
======================================================================

walt@walt-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub-01E6" 
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated  
          Tx-Power=9 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

=====================================================

walt@walt-desktop:~$ sudo iwconfig
[sudo] password for walt:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub-01E6" 
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated  
          Tx-Power=9 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off [NOTE: This changes to key in 4-4-2 format when active]
          Power Management:on

====================================================

walt@walt-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:13:D3:2F:98:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:6A:58:A9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    BTHomeHub-01E6:  Infra, 00:1D:68:7C:A4:57, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WEP

===================================================================

If I attempt to connect the pulses and running nm-tool again produces the following change:

- Device: wlan0  [Auto BTHomeHub-01E6] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:1F:1F:6A:58:A9

then eventually the "connection" drops and it reverts to
State:             disconnected

==================================

walt@walt-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network              
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:2f:98:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:db00(size=256) memory:fdefd000-fdefd0ff memory:fdd00000-fdd0ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:1f:6a:58:a9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

---

### Post by Bluebirds on 2010-05-08
THIS IS WHAT I GET Running 9.04 in LIVE mode
============================

ubuntu@ubuntu:~$ tail -f /var/log/messages
May  7 20:43:23 ubuntu kernel: [  715.384246] sd 5:0:0:0: Attached scsi generic sg8 type 0
May  7 20:44:02 ubuntu kernel: [  754.404173] #
May  7 20:44:06 ubuntu kernel: [  758.316065] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
May  7 20:45:20 ubuntu kernel: [  832.368088] #
May  7 20:45:20 ubuntu kernel: [  832.400093] #
May  7 20:46:02 ubuntu kernel: [  874.384091] #
May  7 20:46:02 ubuntu kernel: [  874.416219] #
May  7 20:46:06 ubuntu kernel: [  878.316066] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 251
May  7 20:46:16 ubuntu kernel: [  888.360198] #
May  7 20:46:16 ubuntu kernel: [  888.392090] #

==============================================

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"BTHomeHub-01E6"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:1D:68:7C:A4:57  
          Bit Rate=54 Mb/s  
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-60 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

==========================

ubuntu@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:13:D3:2F:98:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: ra0  [Auto BTHomeHub-01E6] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           yes
  HW Address:        00:1F:1F:6A:58:A9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *BTHomeHub-01E6: Infra, 00:1D:68:7C:A4:57, Freq 2442 MHz, Rate 54 Mb/s, Strength 70 WEP
    TALKTALK-69D075: Infra, 00:26:5A:69:D0:75, Freq 2412 MHz, Rate 18 Mb/s, Strength 20 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

---

### Post by Bluebirds on 2010-05-08
FURTHER TEST RUNNING 10.04

walt@walt-desktop:~$ lsmod | grep rt.*usb
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
mac80211              204922  2 rt2x00usb,rt2x00lib
crc_ccitt               1339  1 rt2800usb
walt@walt-desktop:~$ 

============

As per similar posts I ran:

sudo gedit /etc/modprobe.d/blacklist.conf

Then added a line:

blacklist rt2800usb

[AFTER A REBOOT]
walt@walt-desktop:~$ lsmod | grep rt.*usb
walt@walt-desktop:~$ 

Result: no effect so I removed the mod.

The Lixux Driver that you download from the RaLink website appear to be the basis of a build-it-yourself solution, which doesn't help me much since it's about 30 years since I last used a compiler.

Really getting desperate and would appreciate any ideas from anyone who can see a way forward other than laying ethernet cables throughout the house.

---

### Post by Bluebirds on 2010-05-13
I've found SOLUTION thanks to Chris Barker's Web Log of Friday, May 07, 2010  
See      [http://www.ctbarker.info/](http://www.ctbarker.info/) 
 
I ran the following code 
 
sudo apt-get install linux-backports-modules-wireless-lucid-generic  
 
Nothing happened ...... 
 
The next time that I booted up, all was working and has been so for two days so far. 

I don'e profess to understand what has happened but it seems to have sorted out the driver for the wifi adapter so that 10.04 now finds the same drivers that worked under 9.04. This may also resolve the raft of similar problems with RaLink chipsets. Mine was RT3070 but seems to use RT2070 drivers or at least parts of them.

=======================================
Running 10.04 as currently working here's what I get in comparison with what is shown in my previous postings:

walt@walt-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"BTHomeHub-01E6"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.442 GHz  Access Point: 00:1D:68:7C:A4:57   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-49 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[NOTE: no change here]
================

walt@walt-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0  [Auto BTHomeHub-01E6] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           yes
  HW Address:        00:1F:1F:6A:58:A9

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *BTHomeHub-01E6: Infra, 00:1D:68:7C:A4:57, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WEP
    TALKTALK-69D075: Infra, 00:26:5A:69:D0:75, Freq 2412 MHz, Rate 18 Mb/s, Strength 26 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.67
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:13:D3:2F:98:6B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

[NOTE: wlan0 has clearly changed settings and now matches what was shown when running the 9.04 Live CD which worked]

===================================

Now a happy bunny with all aspects seemingly working properly.

---

