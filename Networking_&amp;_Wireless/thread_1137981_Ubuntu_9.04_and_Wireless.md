---
title: "Ubuntu 9.04 and Wireless"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by k0d3k on 2009-04-26
I am attempting to associate my wireless card with my access point. The firmware is from DD-WRT 24 Sp1.  I can associate with the ESSID however, I cannot get the encryption keys to work.  I use WPA2 with AES encryption. 

I do iwconfig wlan0 essid ESSID NAME and I can associate with it.  When I attempt to add the wpa keys, it fails.  Any ideas?  

My error outputs are below:
Model: DELL DIMENSION 8400

lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
04:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
04:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

lsusb
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"SADF98723JFAS98DYFSDAIJFDSA473"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod 
b43                   131484  0 

dmesg
[   22.300363] input: b43-phy0 as /devices/virtual/input/input7
[   22.428304] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.616578] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.649176] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.702628] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   22.828027] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.888561] Registered led device: b43-phy0::tx
[   22.888591] Registered led device: b43-phy0::rx
[   22.888623] Registered led device: b43-phy0::radio
[   22.908276] b43-phy0: Radio turned on by software
[   22.924393] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.678555] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   23.678559] tg3: eth0: Flow control is on for TX and on for RX.
[   23.678695] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.432175] wlan0: authenticate with AP 00:17:9a:48:8c:a1
[   24.436746] wlan0: authenticated
[   24.436751] wlan0: associate with AP 00:17:9a:48:8c:a1
[   24.439555] wlan0: RX AssocResp from 00:17:9a:48:8c:a1 (capab=0x421 status=0 aid=4)
[   24.439559] wlan0: associated
[   24.440207] wlan0: disassociating by local choice (reason=3)
[   24.444586] wlan0: deauthenticated
[   34.340014] eth0: no IPv6 routers present
[  217.076418] wlan: 0.9.4
[  313.224380] wlan0: direct probe to AP 00:17:9a:48:8c:a1 try 1
[  316.496725] input: b43-phy0 as /devices/virtual/input/input8
[  316.684025] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  316.737158] Registered led device: b43-phy0::tx
[  316.738499] Registered led device: b43-phy0::rx
[  316.738546] Registered led device: b43-phy0::radio
[  316.764715] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  316.766433] wlan0: direct probe to AP 00:17:9a:48:8c:a1 try 1
[  316.964029] wlan0: direct probe to AP 00:17:9a:48:8c:a1 try 2
[  317.164015] wlan0: direct probe to AP 00:17:9a:48:8c:a1 try 3
[  317.168649] wlan0 direct probe responded
[  317.168653] wlan0: authenticate with AP 00:17:9a:48:8c:a1
[  317.171572] wlan0: authenticated
[  317.171575] wlan0: associate with AP 00:17:9a:48:8c:a1
[  317.178788] wlan0: RX AssocResp from 00:17:9a:48:8c:a1 (capab=0x421 status=0 aid=2)
[  317.178791] wlan0: associated
[  317.179500] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  317.179643] wlan0: disassociating by local choice (reason=3)
[  325.322187] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  325.342070] input: b43-phy0 as /devices/virtual/input/input9
[  325.500042] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  325.553415] Registered led device: b43-phy0::tx
[  325.554752] Registered led device: b43-phy0::rx
[  325.554799] Registered led device: b43-phy0::radio
[  325.581685] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  325.583612] wlan0: authenticate with AP 00:17:9a:48:8c:a1
[  325.586286] wlan0: authenticated
[  325.586294] wlan0: associate with AP 00:17:9a:48:8c:a1
[  325.589777] wlan0: RX AssocResp from 00:17:9a:48:8c:a1 (capab=0x421 status=0 aid=2)
[  325.589783] wlan0: associated
[  325.590259] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  325.602489] wlan0: disassociating by local choice (reason=3)
[  325.605097] wlan0: deauthenticated
[  327.005911] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  327.005915] tg3: eth0: Flow control is on for TX and on for RX.
[  327.006090] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  336.300011] wlan0: no IPv6 routers present
[  337.312010] eth0: no IPv6 routers present
[  579.631937] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  579.640659] usbcore: registered new interface driver ndiswrapper

lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:c2:5f:64
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.23a ip=192.168.1.139 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:65:81:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:71:46:3b:e9:50
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by k0d3k on 2009-04-26
Anyone have any ideas? Wouldy really like to get this squared away before my wife gets the wire cutters and snips my cat5 cable :(

---

### Post by ittiam on 2009-04-26
How are you adding your wpa2 keys? Any connection manager you use?

---

### Post by k0d3k on 2009-04-26
I was using the command on iwconfig to add the keys but everytime I try to do so, I get errors.  I'm also using the built-in wireless connection manager by default.  Hope that helps

---

### Post by ittiam on 2009-04-27
I know you posted your dmesg output already but I cannot see whether WPA2 is supported from the log you posted.
So, post the output of 

```
iwlist auth
```

and

```
dmesg | grep WPA
```

---

### Post by majamba on 2009-04-27
well i am on macbook i can't get the driver to show up using kubuntu
can't activate or deactivate driver it only says activated and it is not current then if add wl module it says activated and current but still the driver does show up in ifconfig for wireless should i go back to 8.10 or debian

---

### Post by k0d3k on 2009-04-27
The info is:
 iwlist auth
lo        no authentication information.

eth0      no authentication information.

wmaster0  no authentication information.

wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Authentication algorithm :
		open
		shared-key


pan0      no authentication information.

When I do dmesg | grep WPA
nothing appears at all for the results

---

### Post by kevdog on 2009-04-27
Can you post exactly what you are tying to attempt to connect?

For wpa2 you need to use wpa_supplicant.  In may signature is a link to a tutorial how to make a manual network connection from the command line using wpa_supplicant.  Take a look if you are confused :)

---

### Post by rvanderwerf on 2009-04-27
I have the same problem with 2 old dell C400's I just installed. Also a Latitude D820 has the same problem as well. All was well with ubuntu 8.10.

---

### Post by ittiam on 2009-04-27
For wpa2 as kevdog said you need wpa_supplicant to be configured.

1. If the following file does not exist, then create it.
```
sudo vi /etc/wpa_supplicant.conf
```

2. The contents of the file should be the following. Put in your ssid and password at the designated places
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
    ssid="your SSID here in quotes if ASCII"
    scan_ssid=1
    proto=RSN
    key_mgmt=WPA-PSK
    group=TKIP
    pairwise=TKIP
    psk="your password here in quotes if ASCII"
}
```

3.
```
sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -B
```

4.
```
sudo dhclient wlan0
```

---

### Post by k0d3k on 2009-04-29
Okay so I got this to work but now I'm getting disconnected very often and my settings don't seem to work when I reboot so I have to manually re-enter them everytime even though I modified the rc.local as directed and did the change mod.  
My wpa_supplicant is:
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="REMOVED"
scan_ssid=1
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=TKIP CCMP
psk="REMOVED"
}

I originally was using AES encryption but could not get my WPA supplicant to work correctly so I just switched my router to TKIP since the instructions and posts were giving more help with TKIP.  

My rc.local is:
ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid "REMOVED"
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

I am seeing a disconnect when I open a number of tabs in Firefox at the same time.  I do get reconnected but this is rather annoying and was hoping someone had experienced the same setup and has a fix. 

Looking at syslog, I see this everytime I reconnect:
Apr 29 05:43:13 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 29 05:43:13 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 29 05:43:23 localhost kernel: [22614.087043] wlan0: disassociating by local choice (reason=3)
Apr 29 05:43:23 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected 
Apr 29 05:43:23 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
Apr 29 05:43:31 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
Apr 29 05:43:31 localhost kernel: [22622.100208] wlan0: authenticate with AP 00:21:29:8d:f7:86
Apr 29 05:43:31 localhost kernel: [22622.108109] wlan0: authenticate with AP 00:21:29:8d:f7:86
Apr 29 05:43:31 localhost kernel: [22622.109683] wlan0: authenticated
Apr 29 05:43:31 localhost kernel: [22622.109687] wlan0: associate with AP 00:21:29:8d:f7:86
Apr 29 05:43:31 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
Apr 29 05:43:31 localhost kernel: [22622.112689] wlan0: RX ReassocResp from 00:21:29:8d:f7:86 (capab=0x411 status=0 aid=1)
Apr 29 05:43:31 localhost kernel: [22622.112693] wlan0: associated
Apr 29 05:43:31 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake 
Apr 29 05:43:31 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Apr 29 05:43:31 localhost NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Apr 29 05:43:41 localhost kernel: [22632.118796] wlan0: disassociating by local choice (reason=3)

When I reboot, I run these commands to get my wireless working:
sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -B
dhclient wlan0

Any ideas and help would be greatly appreciated :)

---

### Post by ittiam on 2009-04-29
Just a suggestion, I am not sure whether this is the problem. You might be having your NetworkManager running at boot up(NetworkManager also launches wpa_supplicant) and apart from that you might also be launching wpa_supplicant from the command line (For this check your /etc/network/interfaces file) also during boot up. Removing either one from boot up might solve the problem.

---

