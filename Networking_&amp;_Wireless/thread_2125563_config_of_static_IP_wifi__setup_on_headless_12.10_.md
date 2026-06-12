---
title: "config of static IP wifi  setup on headless 12.10 lubuntu"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by macartain on 2013-03-14
To unpack that subject line a little...

I installed lubuntu 12.10 on an old P4 with a USB wifi card last week - all good and very easy to use: the wifi worked on my home WPA2 network with no issues after picking up a DHCP address. Once that was done I had to remove the monitor and have since been puttying in to work on it from my main Vista box (lots of entertainment/hassle with X, vino etc but that's another thread).

I then decided to set up a crossover cable Vista<->lubuntu and acheived this by setting a static 10.0.0.x address to the interfaces on each machine. On lubuntu I edited the /etc/network/interfaces file to add an auto static line for etho, did a 'sudo service networking restart' and all seemed good. I can now putty in over an ethernet cable which is nicer.. However, the wlan0 interface then stopped working, giving no route to host for a simple ping to the router... I thought it better anyway to give wlan0 a static IP outside the DHCP range and so created an entry for it too in the interfaces file but I am not having any luck bringing it up.. I can't post the file right now but this has anyway raised a bunch of general questions for me:

- where do I add things like ESSID etc and where can I find the syntax - man iwconfig doesn't seem to cover all options
- should I be using something other than 'service networking' to manage the network (ifup etc)?
- do i need to disable dhcp-client or somehow tell it to leave wlan0 alone?
- do I need to kill the NetworkManager process?
- X is working for me via putty/xming - can I open the NetworkManager GUI over X somehow?
- should i just dig out the monitor?!

A lot of stuff onthe forums has moved me forwards but I can't quite get the WPA2 config stuff right - most forum users seem to be on the GUI. Unfortunately I am not at the machine right now and can't give examples of the issues but can provide any info later to anyone good enough to give some answers...

Cheers!

(BTW - new to ubuntu but worked on linux quite a lot in the past - things have changed!!)

---

### Post by chili555 on 2013-03-14
If you want to run headless; that is, without a monitor and keyboard, it is far preferable to remove Network Manager altogether. Then set up /etc/network/interfaces as here: [http://ubuntuforums.org/showthread.php?t=2125242&p=12557156#post12557156](http://ubuntuforums.org/showthread.php?t=2125242&p=12557156#post12557156)

Once you get it set correctly and can reboot with the interface running and able to ssh to the machine without problem, you are safe to remove the monitor and keyboard and forget it.

---

### Post by macartain on 2013-03-14
Thanks a lot chili555 - that sorted the WPA problem - I modified interfaces and wlan0 came up successfully - the network-manager service is stopped and I haven't seen any more dhcp stuff in syslog. 

However, the interface is only staying up for a minute or two before dropping for a few minutes and then reconnecting... I tailed the syslog while browsing and saw this as the connection dropped:

```
Mar 14 20:44:02 blackbox wpa_supplicant[7957]: wlan0: WPA: EAPOL-Key Replay Counter did not increase - dropping packet
Mar 14 20:44:03 blackbox kernel: [175926.000638] rndis_wlan 1-6:1.0: wlan0: media connect
Mar 14 20:44:03 blackbox wpa_supplicant[7957]: wlan0: Associated with 00:18:f8:4b:d6:23
Mar 14 20:44:03 blackbox wpa_supplicant[7957]: wlan0: WPA: IE in 3/4 msg does not match with IE in Beacon/ProbeResp (src=00:18:f8:4b:d6:23)
Mar 14 20:44:03 blackbox wpa_supplicant[7957]: WPA: RSN IE in Beacon/ProbeResp - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00
Mar 14 20:44:03 blackbox wpa_supplicant[7957]: WPA: RSN IE in 3/4 msg - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
Mar 14 20:44:03 blackbox kernel: [175926.316604] rndis_wlan 1-6:1.0: wlan0: media disconnect
Mar 14 20:44:04 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Mar 14 20:44:04 blackbox kernel: [175926.448546] cfg80211: All devices are disconnected, going to restore regulatory settings
Mar 14 20:44:04 blackbox kernel: [175926.448556] cfg80211: Restoring regulatory settings
Mar 14 20:44:04 blackbox kernel: [175926.448568] cfg80211: Calling CRDA to update world regulatory domain
Mar 14 20:44:04 blackbox kernel: [175926.461591] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:44:04 blackbox kernel: [175926.461599] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```
It then goes into some sort of loop showing ...
```
Mar 14 20:51:34 blackbox kernel: [176377.173642] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Mar 14 20:51:40 blackbox wpa_supplicant[7957]: wlan0: Trying to associate with 00:18:39:6b:b5:8a (SSID='lscam' freq=2462 MHz)
Mar 14 20:51:41 blackbox kernel: [176384.000852] rndis_wlan 1-6:1.0: wlan0: media connect
Mar 14 20:51:41 blackbox wpa_supplicant[7957]: wlan0: Associated with 00:18:f8:4b:d6:23
Mar 14 20:51:41 blackbox wpa_supplicant[7957]: wlan0: WPA: IE in 3/4 msg does not match with IE in Beacon/ProbeResp (src=00:18:f8:4b:d6:23)
Mar 14 20:51:41 blackbox wpa_supplicant[7957]: WPA: RSN IE in Beacon/ProbeResp - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 0c 00
Mar 14 20:51:41 blackbox wpa_supplicant[7957]: WPA: RSN IE in 3/4 msg - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
Mar 14 20:51:41 blackbox kernel: [176384.036140] rndis_wlan 1-6:1.0: wlan0: media disconnect
Mar 14 20:51:41 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Mar 14 20:51:41 blackbox kernel: [176384.167879] cfg80211: All devices are disconnected, going to restore regulatory settings
Mar 14 20:51:41 blackbox kernel: [176384.167888] cfg80211: Restoring regulatory settings
Mar 14 20:51:41 blackbox kernel: [176384.167894] cfg80211: Calling CRDA to update world regulatory domain
Mar 14 20:51:41 blackbox kernel: [176384.176783] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176793] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176797] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176800] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176804] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176807] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176810] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176813] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176820] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176823] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176826] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176829] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176832] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176836] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176839] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176842] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176845] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176848] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176851] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176855] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176858] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176861] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176864] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176868] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176871] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Mar 14 20:51:41 blackbox kernel: [176384.176874] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176879] cfg80211: World regulatory domain updated:
Mar 14 20:51:41 blackbox kernel: [176384.176881] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Mar 14 20:51:41 blackbox kernel: [176384.176885] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176888] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176892] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176895] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:41 blackbox kernel: [176384.176898] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 14 20:51:46 blackbox kernel: [176389.171860] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
```
After a lot of these, I get the following and wifi is back..
```
Mar 14 20:48:37 blackbox kernel: [176200.285687] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Mar 14 20:48:37 blackbox kernel: [176200.285700] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Mar 14 20:48:43 blackbox wpa_supplicant[7957]: wlan0: Trying to associate with 00:18:39:6b:b5:8a (SSID='lscam' freq=2462 MHz)
Mar 14 20:48:45 blackbox kernel: [176208.000696] rndis_wlan 1-6:1.0: wlan0: media connect
Mar 14 20:48:45 blackbox wpa_supplicant[7957]: wlan0: Associated with 00:18:39:6b:b5:8a
Mar 14 20:48:45 blackbox wpa_supplicant[7957]: wlan0: WPA: Key negotiation completed with 00:18:39:6b:b5:8a [PTK=CCMP GTK=CCMP]
Mar 14 20:48:45 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:18:39:6b:b5:8a completed (reauth) [id=0 id_str=]

```
This is all I am seeing for it in lshw:
```
configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b ip=192.168.1.200 link=yes multicast=yes wireless=IEEE 802.11bg

```
And lsusb:
```
Bus 001 Device 003: ID 13b1:0014 Linksys WUSB54GS v2 802.11g Adapter [Broadcom 4320 USB]
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x13b1 Linksys
  idProduct          0x0014 WUSB54GS v2 802.11g Adapter [Broadcom 4320 USB]
  bcdDevice            0.06
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           48
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
```

Anyone have any suggestions as to what is causing this? I'm off to see if the Broadcomn 4320 is supported or not...

---

### Post by chili555 on 2013-03-14
> wlan0: WPA: IE in 3/4 msg does not match with IE in Beacon/ProbeRespGoogling, I see this: [http://code.google.com/p/chromium-os/issues/detail?id=29651](http://code.google.com/p/chromium-os/issues/detail?id=29651)> The client does not associate because the IEs the AP sent during beaconing and probe response differs from the IE encapsulated in the 3/4 message it sent during authentication.  Specifically, the AP sent a Pairwise Cipher Suite Count of 2 during both the beaconing and probe response, but sent a cipher suite count of 3 during authentication. 
....

Please reset the AP back to factory settings and retry the test, since this is probably a bug on the AP.AP means Access Point, usually a router.

How is your router set up? I'd set it to WPA2 only, not some mixed mode WPA and WPA2. Provisionally, just to test, I'd turn off N speeds, preferring B and G only. If your router has an afterburner mode, I'd also test with it disabled. Then try again.

---

### Post by macartain on 2013-03-14
Yes - googling "WPA: EAPOL-Key Replay Counter did not increase - dropping packet" returns lots of stuff - from worrying reports of people buying new wifi cards to ripping out NM and installing wicd?

Router is a WRT54GS running 2006 firmware in mixed mode (options are B-only or G-only) on Channel 11. Allegedly it has a SpeedBooster but I have no idea how to switch this on/off. I thought security was WPA2 Personal/AES only but I see there is a dropdown to choose between Shared Key and Auto - but it is set to Auto and greyed out...

OK, a few things to try - thanks again.

---

### Post by macartain on 2013-03-15
Got back to the machine today to find there have been no more occurences of this since last night when I first managed to bring the interface up. It has been running ever since and currently the wifi is fine.

```

blackbox:~$ uptime
 20:39:00 up 3 days, 47 min,  2 users,  load average: 0.00, 0.01, 0.05
blackbox:~$ sudo grep CTRL-EVENT-DISCONNECTED /var/log/syslog*
/var/log/syslog.1:Mar 14 20:38:02 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
/var/log/syslog.1:Mar 14 20:38:09 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
/var/log/syslog.1:Mar 14 20:38:17 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
...
/var/log/syslog.1:Mar 14 21:35:45 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
/var/log/syslog.1:Mar 14 21:35:57 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
/var/log/syslog.1:Mar 14 21:36:20 blackbox wpa_supplicant[7957]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
blackbox:~$
```
It seems odd that here were a few failures per second until around an hour after it first came up.. I am wondering about something expiring - DHCP-related?

Anyway, thanks for the assistance - I will keep an eye on this...

---

