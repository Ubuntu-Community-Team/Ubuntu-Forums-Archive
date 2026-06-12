---
title: "no wifi after upgrade to natty speedtouch 121g"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by NattyUser on 2011-04-30
Hi,

i have just upgrade to natty from maverick and my usb wifi dongle doesn't want to work. The usb wifi adapter i use is a Thonsom Speedtouch 121g. When using ubuntu 10.10 it work's fine after installing the package linux-firmware-nonfree, but after upgrading to natty it has stop working (the linux-firmware-nonfree package is installed [don't know if is the same version or an upgraded one]).

The network manager doesn't display available wifi nets. The output for lsusb is:

 Bus 001 Device 004: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle

How can i fix this?

Thanks in advance.

---

### Post by chili555 on 2011-04-30
Please open a terminal and run:```
dmesg | grep p54
```If you find it's missing firmware, get a wired connection and try:```
sudo apt-get install linux-firmware-nonfree
```Reboot and see if the dongle works. Post back if you get stuck.

---

### Post by NattyUser on 2011-04-30
The result of dmesg is:

[   33.242642] ieee80211 phy0: p54 detected a LM87 firmware
[   33.242645] p54: rx_mtu reduced from 3240 to 2384
[   34.274885] Registered led device: p54-phy0::assoc
[   34.274930] Registered led device: p54-phy0::tx
[   34.274972] Registered led device: p54-phy0::rx
[   34.275014] Registered led device: p54-phy0::radio
[   34.275904] usbcore: registered new interface driver p54usb

It seems that the firmware is available. 

The network manager also offer the option to create a new wireless network and it shows it has created one but it's not true (can't see the new network form another laptop).

---

### Post by chili555 on 2011-04-30
> The network manager also offer the option to create a new wireless network and it shows it has created one but it's not true (can't see the new network form another laptop).
???

Are you trying to connect to another computer, that is internet connection sharing? Or are you trying to connect to a router or other wireless access point? What does this tell us?```
iwconfig
ifconfig
sudo iwlist wlan0 scan
```

---

### Post by NattyUser on 2011-05-01
The output for the commands:

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```ifconfig:
```

eth0      Link encap:Ethernet  direcciónHW xx:xx:xx:xx:xx:xx  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:43 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:40 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:40 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:2624 (2.6 KB)  TX bytes:2624 (2.6 KB)

wlan0     Link encap:Ethernet  direcciónHW xx:xx:xx:xx:xx:xx  
          Dirección inet6: fe80::212:bfff:fe37:e808/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:17 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:4168 (4.1 KB)
```sudo iwlist wlan0 scan:

```
wlan0     No scan results
```nm-tool:

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            p54usb
  State:             disconnected
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```sudo lshw -C network:

```
 *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:7
       logical name: wlan0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=p54usb driverversion=2.6.38-8-generic firmware=2.13.24.0 - 5.9 link=yes multicast=yes wireless=IEEE 802.11bg
```> 

[QUOTE]The network manager also offer the option to create a new wireless  network and it shows it has created one but it's not true (can't see the  new network form another laptop). ???

Are you trying to connect to another computer, that is internet  connection sharing? Or are you trying to connect to a router or other  wireless access point? What does this tell us?[/QUOTE]I'm trying to connect a desktop PC to a router. I just mention this because i noticed that the network-indicator is aware of the wireless device (if i unplug the device it doesn't show the option).

---

### Post by chili555 on 2011-05-01
> wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:[COLOR="Red"]Ad-Hoc[/COLOR]  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offThis is typical of computer-to-computer connections. Please right-click the Network Manager icon and Edit Connections, Edit Wireless and then be sure the Mode is set to Infrastructure; *not* ad-hoc. Try to connect to your network again. Post back and let us know.

Please see attached.

---

### Post by NattyUser on 2011-05-01
In the network-indicator show infrastructure mode for my network.

Is there a command line for changing the mode?

---

### Post by chili555 on 2011-05-01
Sure:```
sudo iwconfig wlan0 mode managed
```

---

### Post by NattyUser on 2011-05-01
> **chili555 said:**
> Sure:```
sudo iwconfig wlan0 mode managed
```

Done, says device busy:

```
sudo iwconfig wlan0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
```The interfaces file in /etc/network looks ok:
```

auto lo
iface lo inet loopback
```

---

### Post by chili555 on 2011-05-01
With some drivers, you need to bring the interface down first:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
iwconfig
```Did it stick?

---

### Post by NattyUser on 2011-05-01
The result of sudo iwconfig wlan0 mode managed:

```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```sudo iwlist wlan0 scan

```
wlan0     No scan results
```The wifi network works, i'm currently using it from another pc.

And when setting the mode to monitor (In a desperate attempt)
```

wlan0     IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
  sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Operation not supported
```

---

### Post by NattyUser on 2011-06-03
OK, a solution have been provided to me.

Thanks to chili555 and to Fabio Marconi for the help.

The solution can be read here -> [https://bugs.launchpad.net/ubuntu/+bug/785925](https://bugs.launchpad.net/ubuntu/+bug/785925)

and basically is to install the 2.6.39 kernel.

---

