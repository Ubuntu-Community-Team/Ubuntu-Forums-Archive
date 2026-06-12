---
title: "Can't set up wireless...ndiswrapper? something else?"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by mssever on 2006-07-13
I've never messed with wireless in Linux before--and haven't had such a headache in a long time. ](*,) I have no clue what the problem is, or how to troubleshoot it, hence the mostly useless subject. And, I've been unable to find a useful HOWTO on this.

From lshw:
```
*-network:0 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth1
             version: 02
             serial: 00:0b:cd:56:00:81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-386 link=no multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:d0002000-d0003fff irq:10

```I used ndiswrapper to install the driver from the driver CD that came with my computer.

ndiswrapper -l:
```
Installed ndis drivers:
netwlan         driver present
```The GUI version reports:
```
netwlan
Hardware present: No
```iwconfig:
```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```/var/log/syslog (in part):
```
Jul 13 02:31:18 scott-laptop kernel: [17189045.228000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load
failed.
Jul 13 02:31:18 scott-laptop firmware_helper[15330]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:00:09.0' with driver 'bcm43xx'
Jul 13 02:31:23 scott-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on
device eth1: No such device
Jul 13 02:33:23 scott-laptop kernel: [17189170.256000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load
failed.
Jul 13 02:33:23 scott-laptop firmware_helper[15431]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:00:09.0' with driver 'bcm43xx'
Jul 13 02:33:28 scott-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on
device eth1: No such device
Jul 13 02:35:28 scott-laptop firmware_helper[15546]: main: error loading '/lib/firmware/bcm43xx_microcode4.fw' for device '/class/firmware/0000:00:09.0' with driver 'bcm43xx'
Jul 13 02:35:28 scott-laptop kernel: [17189295.368000] bcm43xx: Error: Microcode "bcm43xx_microcode4.fw" not available or load
failed.
Jul 13 02:35:33 scott-laptop NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on
device eth1: No such device
Jul 13 02:36:17 scott-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jul 13 02:36:17 scott-laptop dhclient: send_packet: Network is down
Jul 13 02:36:20 scott-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jul 13 02:36:20 scott-laptop dhclient: send_packet: Network is down

```Any help? BTW, I'm using WPA, not WEP.

---

### Post by mssever on 2006-07-13
OK, I figured it out, thanks largely to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper). I don't know why I wasn't able to find that last night...too late at night, perhaps.

Here are the steps I took (while using a wired connection):[LIST=1]
[*] $ sudo aptitude install bcm43xx-fwcutter network-manager-gnome
[*] $ sudo rmmod ndiswrapper
[*] edit /etc/modprobe.d/blacklist and add a line with "blacklist ndiswrapper"
[*] $ sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
[*] $ sudo iwlist eth1 scan
[*]nm-applet &
[*] left click on the network connection icon in the system tray and select my network[/LIST]It works now, although at only 11M. I think that this was much more difficult than necessary, but I guess much of the blame goes to Broadcom?

---

### Post by mssever on 2006-10-27
I've confirmed that this works in Edgy, as well as Dapper.

---

### Post by squibT on 2006-10-27
> **mssever said:**
> OK, I figured it out, thanks largely to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper). I don't know why I wasn't able to find that last night...too late at night, perhaps.

Here are the steps I took (while using a wired connection):[LIST=1]
[*] $ sudo aptitude install bcm43xx-fwcutter network-manager-gnome
[*] $ sudo rmmod ndiswrapper
[*] edit /etc/modprobe.d/blacklist and add a line with "blacklist ndiswrapper"
[*] $ sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
[*] $ sudo iwlist eth1 scan
[*]nm-applet &
[*] left click on the network connection icon in the system tray and select my network[/LIST]It works now, although at only 11M. I think that this was much more difficult than necessary, but I guess much of the blame goes to Broadcom?


I used Cutter and wl_apsta.0 driver for my bcm4306 driver and only got 11M. Using the latest drivers and ndiswrapper I get 54 M

Give ndis a try.

---

### Post by mssever on 2006-10-27
> **squibT said:**
> I used Cutter and wl_apsta.0 driver for my bcm4306 driver and only got 11M. Using the latest drivers and ndiswrapper I get 54 M

Give ndis a try.
Thanks for the tip. I wasn't able to get wireless working with ndiswrapper before, but I'll try again when I find some time. Are the instructions in the following links sufficient?
[LIST]
[*] [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
[*][http://ubuntuforums.org/showthread.php?t=284746](http://ubuntuforums.org/showthread.php?t=284746)[/LIST]I don't care for the hackish nature of ndiswrapper (I prefer real Linux drivers), but if I can get 54M with it, I'll use it anyway.

---

### Post by mssever on 2008-05-16
Hardy changed things a bit (and simplified them). Here are the instructions for Hardy:
```
sudo aptitude install b43-fwcutter
sudo iwlist wlan0 scan
```

---

