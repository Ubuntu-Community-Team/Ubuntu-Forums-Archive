---
title: "iwconfig error (rtl8188ce) for &quot;Set ESSID&quot;: SET failed"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by gobblehook on 2013-04-27
I've had problems with my wireless card since I got my Toshiba NB505 over a year ago. I downloaded and installed drivers almost a year ago, but had no idea what I was doing, and possibly installed things a little wrong, so wlan0 ended up slow and unpredictable, often not recognizing APs, not connecting, or dropping connections. About 6 months ago somehow wlan0 started working fine in X (right after I threw the damn thing out a window in frustration).

I'm trying to learn how to connect to an AP from tty2 (using ifconfig, iwlist, and iwconfig) without running X, and wlan0's back to the old tricks.

This usually happens:
```
$ iwlist wlan0 scan
wlan0     No scan results
```

Sometimes it gives me my neighbor's essid, and once in a blue moon gives me my own. The AP is fine: I'm online posting to this forum uneventfully on another laptop via my AP.

But when iwlist wlan0 scan does discover my AP and I try to connect to it with the NB505:
```
$ iwconfig wlan0 essid "HOME-A002"
Error for wireless request "Set ESSID" (8B1A) :
     SET failed on device wlan0 ; Operation not permitted.
```

Here's my hardware:
```
$ lspci | grep etwork
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

Here's wlan0's configuration:
```
$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)
```

Here's the drivers etc:
```
$ lsmod | grep rtl
rtl8192ce                55853  0
rtl8192c_common          51783  1 rtl8192ce
rtlwifi                  75150  1 rtl8192ce
mac80211                174452  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211                116717  2 rtlwifi,mac80211
usbcore                 103418  8 rtlwifi,uvcvideo,ums_realtek,usb_storage,uas,uhci_hcd,ehci_hcd
```


Aaaaand from my syslog:

```
$ sudo cat /var/log/syslog | grep etwork | tail -n25
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01). 
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): now managed
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): bringing up device.
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): preparing device.
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): deactivating device (reason: 2).
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): carrier is OFF
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): now managed
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): bringing up device.
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): preparing device.
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (eth0): deactivating device (reason: 2).
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> Added default wired connection 'Auto eth0' for sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/eth0
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <warn> bluez error getting default adapter: the name org.bluez was not provided by any .service files
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> modem-manager is now available
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> Trying to start the supplicant...
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): supplicant manager state: down -> idle
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Apr 26 23:31:29 akcrunchbang NetworkManager[1434]: <info> (wlan0): supplicant interface state:  starting -> ready
```

Can anybody see anything enlightening in all this or tell me where else to look to get this baby running smoothly from a terminal session without the help of X applications or frustrated defenestrations?

---

### Post by chili555 on 2013-04-27
It's been a long time since I wrote a 1200 word think piece on networking. Let me pour a tall coffee and we'll get started. 

First of all, trying to manipulate your wireless interface with the terminal when Network Manager is running is fruitless. NM is so tightly integrated into the system that any efforts to change much using manual methods usually fall short. If you really, REALLY want to use manual methods, remove NM altogether. Pretty radical, eh??

Second, most of the commands you've run require administrative privileges; that is, sudo:```
[COLOR="#FF0000"]sudo[/COLOR] iwlist wlan0 scan
```Here is a quote from *man iwlist*:> Triggering  scanning  is  a privileged operation (root only) and          normal users can only read left-over scan results. However, even if you used sudo to set the ESSID, Network Manager would instantly over-ride your command. Unless you want to remove NM and go old-skool with complete manual methods, it is far better to rely on NM to do its job. If the hardware and driver are working as expected, it does a very fine job. In the majority of cases, including two computers at my house, it's perfect.

Now, here is our next problem:> $ lsmod | grep rtl
[COLOR="#FF0000"]rtl8192ce[/COLOR]                55853  0
rtl8192c_common          51783  1 rtl8192ce
rtlwifi                  75150  1 rtl8192ceCurrently, the rtl81192xx series of drivers are a bit tricky. I read that a big series of bug fixes are on the way but, the last time I checked, they are a couple of weeks away.

Frankly, if this is your current situation:> About 6 months ago somehow wlan0 started working fine...then I'd cross my fingers, hold my breath and step away from the terminal!!

Aside from general knowledge, what are you trying to achieve?

---

### Post by gobblehook on 2013-04-28
> 
Frankly, if this is your current situation:
[QUOTE]
About 6 months ago somehow wlan0 started working fine

...then I'd cross my fingers, hold my breath and step away from the terminal!!

Aside from general knowledge, what are you trying to achieve?
[/QUOTE]

1) I don't like to use things when I don't know how they work. I'm trying to understand networking, command line tools, and the file hierarchy better by messing with this. I've been reading network theory, but I don't really understand until I break things.
2) I try to work primarily at the level of bash, emacs, elinks, and mutt (all of which I'm a novice in), and am learning to automate things with bash scripts and python. ttyx sessions render color in a way that's way easier on my eyes than a terminal emulator in X. I get very distracted by shiny things when working in the GUI, the netbook chokes on said shiny things, and said shiny things rob her of her precious screen real estate. It's annoying to log into tty2, start working, then have to run an X session in tty7 and waste system resources for the sole purpose of accessing wlan.

I think this just means I'm doing the Linux user thing. After a while, I'll probably post some scripts on message boards, learn enough to contribute to the Debian project in some small way, answer people's questions on message boards, tinker with gentoo or arch in a few years, construct a cool pocket terminal emulator on a beagleboard with a 3d-printed case, painstakingly build Linux-from-scratch, and then retire to whatever is easy that people are using at the tail end of my odyssey of Linux discovery.

In the meantime, I bug people with odd questions! :)

---

### Post by gobblehook on 2013-04-28
Thanks Chili! I'm partway there....

Stopping Network Manager was sufficient to get wlan connected:
```
sudo service network-manager stop
```

Because my roommate's AP uses WPA, I created /etc/wpa_supplicant/wpa_supplicant.conf and added this:
```
# WPA-PSK/TKIPupdate_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="MY-SSID"
    psk="MY-PSK-KEY"
}
```

I sudo'ed to scan, connect, etc -- thanks for helping me understand why it's necessary here.
```

$ sudo iplink set wlan0 up               # bring up interface
$ sudo iwlist wlan0 scan | more          # scan for APs
$ sudo iwconfig wlan0 essid MYESSID      # connect to AP
$ sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf
$ sudo iwconfig wlan0                    # make sure I'm connected
$ sudo dhclient wlan0                    # request an IP address

```

(Source: " HowTo: Connect and roam wifi networks with wpasupplicant" [http://crunchbang.org/forums/viewtopic.php?id=16624](http://crunchbang.org/forums/viewtopic.php?id=16624))

That got me online but it's slow and jerky. I don't know many diagnostics. Elinks received about 400 B/s from wikipedia, and Mutt became unresponsive when fetching new emails from gmail. Ping stats say:
```
$ ping ubuntu.com
...
145 packets transmitted, 128 received, 11% packet loss, time 298873ms
rtt min/avg/max/mdev = 105.305/722.475/7681.708/826.545 ms, pipe 4
```

Is there a way to find out if the slow/jerky connection is due to Network-Manager somehow still meddling with things? Or to the rtl81192xx driver? What diagnostics can I run to understand the problem better? Also, does anybody have experience with wpa_cli, wpa_gui's cousin?

---

### Post by chili555 on 2013-04-28
See if NM is running; that is re-spawned, and I suspect it is:```
ps aux | grep etwork
```Check if there are interesting messages about the driver:```
cat /var/log/syslog | grep rtl | tail -n20
```The usual old-skool method to connect to wireless without NM is to fill in /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp
wpa-essid MY-SSID
wpa-psk MY-PSK-KEY
```Then get the system to read and use the file:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```With the 'auto' declaration, it will connect seamlessly, or as seamlessly as rtl8192xx is capable of, on boot.

If you want to be able to ssh, ftp, etc. into the machine, I'd use a static IP address. Further details on request.

My meager money is bet on the flaky and tricky rtl8192xx driver suite as the troublemaker.

---

