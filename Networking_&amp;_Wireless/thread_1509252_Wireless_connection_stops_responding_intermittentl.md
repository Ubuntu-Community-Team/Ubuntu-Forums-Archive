---
title: "Wireless connection stops responding intermittently"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by Lozza1980 on 2010-06-14
Hi,

I have ubuntu (karmic) installed on my Dell Hybrid which is connected to  my Samsung 46" Series 7 LED. I am using a Plexus USB wireless dongle to  connect to my netgear router DG834G using WPA encryption. On first  installation everything is working fine however when I leave the desktop  idle for a while I am unable to ping the machine from my mac:

lawrence-nicholsons-macbook:~ Lozza$ ping 192.168.0.6
PING  192.168.0.6 (192.168.0.6): 56 data bytes
ping: sendto: No route to host
ping: sendto: Host is down
ping:  sendto: Host is down
ping: sendto: Host is down
ping: sendto: Host  is down
ping: sendto: Host is down
ping: sendto: Host is down
^C
---  192.168.0.6 ping statistics ---
12 packets transmitted, 0 packets received, 100% packet loss

However once I turn on my bluetooth keyboard the system springs back to  life:

lawrence-nicholsons-macbook:~ Lozza$ ping 192.168.0.6
PING  192.168.0.6 (192.168.0.6): 56 data bytes
64 bytes from [192.168.0.6]("http://192.168.0.6/"):   icmp_seq=0 ttl=64 time=10.688 ms
64 bytes from [192.168.0.6]("http://192.168.0.6/"):  icmp_seq=1  ttl=64 time=12.643 ms
64 bytes from [192.168.0.6]("http://192.168.0.6/"):  icmp_seq=2 ttl=64 time=8.064 ms
64 bytes from [192.168.0.6]("http://192.168.0.6/"):   icmp_seq=3 ttl=64 time=7.701 ms
64 bytes from [192.168.0.6]("http://192.168.0.6/"):  icmp_seq=4  ttl=64 time=5.632 ms
^C
--- 192.168.0.6 ping statistics ---
5 packets transmitted, 5 packets received, 0% packet loss
round-trip  min/avg/max/stddev = 5.632/8.946/12.643/2.450 ms

Originally I saw the following in dmesg, wlan0 not being ready and then  being ready once the bluetooth keyboard "woke" the system up again.

[   20.053776] type=1505 audit(1276066880.660:21):   operation="profile_replace" pid=1022 name=/usr/sbin/tcpdump
**[   20.248035] ADDRCONF(NETDEV_UP): wlan0: link is not ready**
[     21.248123] [drm] TV-10: set mode NTSC 480i 0
[   21.386571]  Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.386575]  Bluetooth: BNEP filters: protocol multicast
[   21.394441] Bridge firewalling registered
[   21.443217] [drm]  TV-10: set mode NTSC 480i 0
[   22.267395] [drm] TV-10: set mode NTSC  480i 0
[   22.295769] ppdev: user-space parallel port driver
[    22.409507] [drm] TV-10: set mode NTSC 480i 0
[   25.168142] [drm] TV-10: set mode NTSC 480i 0
[   25.310526] [drm]  TV-10: set mode NTSC 480i 0
[   26.134021] [drm] TV-10: set mode  NTSC 480i 0
[   26.275223] [drm] TV-10: set mode NTSC 480i 0
[    27.084860] [drm] TV-10: set mode NTSC 480i 0
[   27.225760] [drm] TV-10: set mode NTSC 480i 0
[   28.312593]  Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   30.916042]  usb 2-3: reset high speed USB device using ehci_hcd and  address 4
[    48.145215] wlan0: authenticate with AP 00:14:6c:ed:d8:56
[   48.149216] wlan0: authenticated
[   48.149219] wlan0: associate  with AP 00:14:6c:ed:d8:56
[   48.153723] wlan0: RX AssocResp from  00:14:6c:ed:d8:56 (capab=0x471  status=0 aid=2)
[   48.153726] wlan0:  associated
**[   48.166637] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready**
[     58.904026] wlan0: no IPv6 routers present
[   61.916038] usb 2-3:  reset high speed USB device using ehci_hcd and  address 4
[    69.928035] usb 2-3: reset high speed USB device using ehci_hcd and   address 4
[ 6293.308517] input: BTKB-691F as  /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input6
[  6293.308623] generic-bluetooth 0005:0DC6:3752.0003: input,hidraw2:   BLUETOOTH HID v1.00 Keyboard [BTKB-691F] on 00:02:72:B3:16:0C

At this stage I checked iwconfig output and it showed power management  "on" so I turned this off but it appears to not resolved the issue.

wlan0     IEEE 802.11bg  ESSID:"pinkyponk"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:ED:grin:8:56   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg now doesnt show up the wlan not ready issue but the problem  persists:

[11596.463586] end_request: I/O error, dev sda, sector 32149778
[11596.463610]  ata1: EH complete
[15701.506001] input: BTKB-691F as  /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input10
[15701.506173]  generic-bluetooth 0005:0DC6:3752.0007: input,hidraw2:  BLUETOOTH HID  v1.00 Keyboard [BTKB-691F] on 00:02:72:B3:16:0C
[15715.052377] [drm] TV-10: set mode NTSC 480i 0
[15715.192636] [drm]  TV-10: set mode NTSC 480i 0
[15716.213361] [drm] TV-10: set mode  NTSC 480i 0
[15716.354086] [drm] TV-10: set mode NTSC 480i 0
[21802.617148]  input: BTKB-691F as  /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input11
[21802.617336] generic-bluetooth 0005:0DC6:3752.0008: input,hidraw2:   BLUETOOTH HID v1.00 Keyboard [BTKB-691F] on 00:02:72:B3:16:0C
[74888.358975]  input: BTKB-691F as  /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:41/input12
[74888.359077] generic-bluetooth 0005:0DC6:3752.0009: input,hidraw2:   BLUETOOTH HID v1.00 Keyboard [BTKB-691F] on 00:02:72:B3:16:0C

I have also checked the obvious network settings like power management  (set to "never").

I have also added this line to /etc/default/acpi-support

# Add to this list network interfaces that you don't want to be stopped
 # during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="wlan0"

Still no luck :sad:

Can anyone help??

lawrence@lawrence-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

### Post by Noob-untu on 2010-06-15
I have the same problem, it disconnects the wireless if I use it for more than for web surfing (torrent, skype, etc), and then it is unable to reconnect, unless I reboot the system. 

But thanks to you I found out a way to solve the disconnection problem: Turning the bluetooth on in my Acer Extensa laptop seems to solve it. Quite weird.

---

### Post by davethewave83 on 2012-01-13
I have the same problem, except I don't run bluetooth. :confused:

---

### Post by lisati on 2012-01-13
Back to sleep, thread!

@davethewave83: Things change in the space of 6 months, what with new releases etc. Please start your own thread.

---

