---
title: "Linux  Won't  Recognize Realtek WLan (2)"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by bogan on 2011-10-30
Re: Linux Won't recognize Realtek WLan(2)
I have had, for two years, a Medion MD8341 with Windows7, an Intel i3-530, 3GB of DDR3 Ram, an nVidia G210, and a Realtek RTL8191SU WLan adapter.
Although the latter works well with Win7, I have never been able to get Linux to recognize it.
Eventually, with a great deal of help from Chili555, got an Internet connection working in Linux 9.1, with a Getnet Ralink RT3070 USB dongle.
 [ See thread: 'Linux Won't recognize Realtek' Feb16th-21st 2010, in the Networks forum. ] Edit: Year added.
That dongle has got broken physically and I have bought a new one, A** Nano Realtek RTL8188SU USB mini dongle**.( It works well with Win7. and on another computer with a RALINK RT73 Wlan card Linux 11.10 runs both OK)** Edit: note re 11.10 corrected**
Unfortunately, Linux 10.10  will not connect with it; though  it does recognize it. The WiFi icon scans and after keyring requests for my password, and  long delays, repeatedly displays a request for the network authentication, but, given it does not connect; clicking on the icon shows the name of the network; eventually, it gives up and the WiFi icon stops scanning and shows a vertical red line. ( As does 10.10 from the start with the **Realtek RTL8191SU WLan adapter card.**
With the RTL8191SU, `lshw -c network` gives no wireless network entry, only ones for lo, Firewire and EtherNet.
 With the RTL8188SU, I get```
:lshw _c network
....
*-network
    description: Wireless interface
    physical id: 1
    logical name: wlan0
    serial: 00:02:72:9c:18:b8
    cabilities: ethernet physical wireless
    configuration:broadcast=yes multicast=yes wireless=802.11b/g/n...
``````
lsusb
....
Bus 002 Device 007: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
``` With RTL8191SU, iwconfig gives no return.
With the RTL8188SU, I get:
```
iwconfig
....
wlan0  802.11b/g/n ... ESSID:"CYBERGRANS"
....
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
````lspci -nn | grep network` and `lsmod | grep wlan0` both give no return.
**Edit**: I had not heard of dmesg, this is what it gave:
Code:
> dmesg
[  520.205969] usbcore: registered new interface driver rtl819xU
[  520.266053] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize: c808, sram size: 9290
[  520.268118] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[  520.272731] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[  520.272954] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[  520.274752] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[  520.275832] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[  520.276096] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[  520.276100] rtl819xU:FirmwareDownload92S(): Firmware Download Success
[  522.943785] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Linking with CYBERGRANS,channel:6, qos:0, myHT:1 networkkHT:0, mode:6
--->ieee80211 associate_proceedure wq(), chan:6
rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20NHz bandwidth
==================ieee80211_authentication_req():auth->algorithm is 0(Last part repeats dozens of times)

Can someone offer any suggestions to get either adapter, or both, working.

Edit:** Edit: note re 11.10 deleted** here.
I am having to copy the code to another machine by hand, so I have picked out the bits I thought relevant.
Hopefully, bogan.

---

### Post by chili555 on 2011-11-01
May I assume our task is to connect this device:> I have bought a new one, A Nano Realtek RTL8188SU USB mini dongle.And may I assume its difficulty is:> The WiFi icon scans and after keyring requests for my password, and long delays, repeatedly displays a request for the network authentication, but, given it does not connect; Let's concentrate on one device and one version of Ubuntu; let's not hop around between versions and wireless devices. I'm old and my wife, ole whatshername, says I confuse easily.

Does your device scan and see the router correctly?```
sudo iwlist wlan0 scan
```Is the router set up for WPA2 only or mixed mode WPA and WPA2? If it's mixed mode, please change it to WPA2 only.

Have you double- and triple-checked the password? It is case sensitive and the slightest difference will not allow connection.

Is there any clue here?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```May I see:```
lsmod | grep 819
```You can copy and paste from the terminal to a text document and transfer the text document on a USB key to post here. Thanks.

---

### Post by bogan on 2011-11-01
Hi! **Chili555**,  Am I glad to see your Avatar! I had begun to feel a bit left behind.
 You posted:> May I assume our task is to connect this device: I have bought a new one,   A Nano Realtek RT8188SU USB mini dongle.Correct, that is the main task, as getting the installed Wlan card to work, is apparently not on the cards.
  > And may I assume its difficulty is: The WiFi icon scans and after keyring requests for my password, and long delays, repeatedly displays a request for the network authentication, but, given it does not connect;  Correct: But, just occasionally, it does connect, works OK at 20MHz, but then drops the connection, unpredictably.
 > Let's concentrate on one device and one version of Ubuntu; Ok! In that case, ignore Wlan0,  the installed Wlan card  and Wlan1, which is the GetNet Ralink card you got to work in Feb 2011. Which I have to use to get a connection on this Win7 computer.
 > I'm old and my wife, ole whatshername, says I confuse easily. *Bet you are not as old as I, but at least I don`t have a wife to confuse me.*** Edit: I seem to have done it myself!**

 The Nano is Wlan2. It is on my Win7 machine, with 11.10 3.0.0-30-generic, installed by update from 11.04 on sda8. ( 10.04 is on sd6.)
 **Edit: 2/11/11 This is wrong! see next post.**
 > Does your device scan and see the router correctly?It scans wlan0, but not correctly, I think; wlan1 correctly, but not wlan2.  That says:>  Interface doesn`t support scanning. I have not managed to catch it when it has connected, which is very rarely.
 
```
root@alan-MS-7616:/home/alan# iwlist wlan0 scan            # With GetNet
 wlan0     Scan completed :
           Cell 01 - Address: 00:12:BF:09:3D:7C
                     ESSID:"CYBERGRANS"
                     Protocol:IEEE802.11bg
                     Mode:Master
                     Channel:6
                     Encryption key:on
                     Bit Rates:54 Mb/s
                     Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54  
                     Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     Extra: Last beacon: 6ms ago
  
root@alan-MS-7616:/home/alan# iwlist wlan1 scan                 # With GetNet
 wlan1     Scan completed :
           Cell 01 - Address: 00:12:BF:09:3D:7C
 
                   Protocol:802.11b/g
                     ESSID:"CYBERGRANS"
                     Mode:Managed
                     Channel:6
                     Quality:100/100  Signal level:-41 dBm  Noise level:-83 dBm
                     Encryption key:on
                     Bit Rates:22 Mb/s
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
  root@alan-MS-7616:/home/alan# 

``````
root@alan-MS-7616:/home/alan# iwlist wlan0 scan      # Without GetNet
 wlan0     Scan completed :
           Cell 01 - Address: 00:12:BF:09:3D:7C
                     ESSID:"CYBERGRANS"
                     Protocol:IEEE802.11bg
                     Mode:Master
                     Channel:6
                     Encryption key:on
                     Bit Rates:54 Mb/s
                     Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54  
                     Quality=86/100  Signal level=-84 dBm  Noise level=-113 dBm
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     Extra: Last beacon: 86ms ago
 

 root@alan-MS-7616:/home/alan# iwlist wlan1 scan                       # Without GetNet
 wlan1     Interface doesn't support scanning.
 root@alan-MS-7616:/home/alan# iwlist wlan2 scan                       # Without GetNet
 wlan2     Interface doesn't support scanning.

``` [ Note: When only the Nano is plugged in, a left click on the WiFi Icon shows neither device; when the GetNet is also plugged in, both are listed , as if connected.] Sorry, I know you said keep to one, but this seemed to me to be significant. Just ignore the Wlan0 & 1 bits.]
 > Is the router set up for WPA2 only or mixed mode WPA and WPA2? If it's mixed mode, please change it to WPA2 only. The Password Requester shows:>   WPA and WPA2Personal. I assume, to alter it, I would need access to the router; which I do not have. I could take the PC to a friend’s house and use his, but I do not know what it is set to,  or if he would alter it.
 > Have you double- and triple-checked the password?  !**WOW**! I thought you had found the answer.
 When I checked it with the Show Password button, I found that it had got altered to"Signature". I changed it to the correct form, but it made no difference at all. One of the repeated Requesters must have opened under my cursor when I was looking at the keyboard. But I had only typed that word a few minutes previously.  
> Is there any clue here?  
  Code:
 sudo cat /var/log/syslog | grep etwork | tail -n20  ```
root@alan-MS-7616:/home/alan# cat /var/log/syslog | grep etwork | tail -n20
 Nov  1 20:41:38 alan-MS-7616 kernel: [ 1745.754410] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/net/wlan0, iface: wlan0)
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): now unmanaged
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): device state change: 3 -> 1 (reason 36)
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): cleaning up...
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
 Nov  1 20:41:40 alan-MS-7616 NetworkManager[1062]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0)
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <error> [1320180120.125638] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl819xU' ifindex: 4)
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): now managed
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
 Nov  1 20:42:00 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): bringing up device.
 Nov  1 20:42:02 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): preparing device.
 Nov  1 20:42:02 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): deactivating device (reason: 2).
 Nov  1 20:42:02 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): supplicant interface state:  starting -> ready
 Nov  1 20:42:02 alan-MS-7616 NetworkManager[1062]: <info> (wlan0): device state change: 2 -> 3 (reason 42)

```> May I see:
  Code:
 lsmod | grep 819 
```
root@alan-MS-7616:/home/alan# lsmod | grep 819
 r8192s_usb            287404  0  
 eeprom_93cx6            1345  1 r8192s_usb
 root@alan-MS-7616:/home/alan#

```[FONT=Courier New, monospace][SIZE=2]I thought nm-tool might help but it only shows Wlan0:[/SIZE][/FONT]
```
root@alan-MS-7616:/home/alan# nm-tool
 NetworkManager Tool
 State: disconnected
 - Device: eth0 -----------------------------------------------------------------
   Type:              Wired
   Driver:            r8169
   State:             unavailable
   Default:           no
   HW Address:        40:61:86:60:6A:48
   Capabilities:Carrier Detect: yes Speed: 10 Mb/s
   Wired Properties
     Carrier:         off
 
 
- Device: wlan0 ---------------------------------------------------------------- 
  Type:              802.11 WiFi
   **Driver:            rtl819xU**
   State:             disconnected
   Default:           no
   HW Address:        00:02:72:9C:18:B8
   Capabilities:
   Wireless Properties
     WEP Encryption:  yes
     WPA Encryption:  yes
     WPA2 Encryption: yes
   Wireless Access Point: CYBERGRANS: Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 86 WPA
 root@alan-MS-7616:/home/alan# 

``` [FONT=Courier New, monospace][SIZE=2]The above driver despite my having blacklisted as below, to try and force it to find another driver.[/SIZE][/FONT]
```
root@alan-MS-7616:/home/alan# gedit /etc/modprobe.d
 # This file lists those modules which we don't want to be loaded by
 # alias expansion, usually so some other driver will be loaded for the
 # device instead.
 

 #Added by alan 30/10/11 for Wlan rt adapters; edited 1/11/11
 #blacklist rt2800usb
 #blacklist rt2x00usb
 blacklist rtl8192u
 blacklist rtl8192U
 blacklist rtl819xU
 ....

```  **[FONT=Courier New, monospace][SIZE=2]Whao![/SIZE][/FONT]**
 [FONT=Courier New, monospace][SIZE=2]The WiFi scanning suddenly stopped and a window opened saying:[/SIZE][/FONT][CODE] CYBERGRANS Connected[/CODE[FONT=Courier New, monospace][SIZE=2]]When I clicked on the WiFi Icon it showed all three devices connected. By the time I opened a terminal and entered a command, it had dropped out. It`s just connected again, now it shows four devices, but nm-tool only shows wlan0 and Wlan1. This is frustrating.[/SIZE][/FONT] [ **Edit: The word "devices" should read "Networks":** though they all have the same name (ssid). Two of them show the device ghosted.
[FONT=Courier New, monospace][SIZE=2][ I*t`*s midnight here and I am off to snooze.][/SIZE][/FONT]


[FONT=Courier New, monospace][SIZE=2]Chao! **bogan**.
[/SIZE][/FONT]

---

### Post by bogan on 2011-11-02
H! **Chili555**.
I posted:> The Nano is Wlan2. It is on my Win7 machine, with 11.10 3.0.0-30-generic, installed by update from 11.04 on sda8.**This is wrong!**
I had always assumed that on 10.10,  Wlan0 was the installed Realtek RTL8191SUWlan 802.11n USB 2.0 Card, as it is on 11.10. In fact 10.10 does not recognize it, apparently.

This morning I booted with the Nano dongle plugged in and the WiFi connection was made almost at once. the window opened saying:> CYBERGRANS  established But the WiFi Icon showed only one dot and the strip said:> Wireless connection `CYBERGRANS`active: CYBERGRANS (30%) A right click showed two CYBERGRANS networks. A further right click on the first caused it  to disconnect, but it immediately reconnected, now with four strength bars and showed: (86%)
However, in both states, Firefox was unable to find a server!

A right click on the second network, put things into the previous repetative mode, ending with a red bar in the WiFi Icon, and needing a reboot to reactivate the scanning.
Taking out the Nano and rebooting resulting in all the commands you asked for to fail to show any Wlan info at all.
I repeated the sequence, rebooting several times and it repeated exactly, although, as far as I know, nothing has been changed in the last few days .
 I have not run Update Manager in that period, and will not do so, unless you say.

**So it would appear that everything in the previous post that refers to Wlan0, comes from the Nano RTL8188SU.**

Syslog now showed:
```
root@alan-MS-7616:/home/alan# cat /var/log/syslog | grep etwork | tail -n20
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 53 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 53 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 67 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 67 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --jump REJECT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface wlan0 --jump REJECT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --out-interface wlan0 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan0 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Starting dnsmasq...
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) successful, device activated.
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
root@alan-MS-7616:/home/alan# 
```Sorry for the confusion, and I guess the above info does not help much, but makes the confusion even thicker, for me anyrate.

CHAO! **bogan**

---

### Post by chili555 on 2011-11-02
Obviously, wlan0 is connecting. I'm sure that the presence of the external USB device is confusing Network Manager. At least for the moment, detach it and reboot so that we start with a clean slate. Now, please show me:```
lspci -nn | grep 0280
lsmod | grep 819
dmesg | grep -e wlan -e 819
iwconfig
```I'm fairly confident that the internal is going to work just fine.

---

### Post by bogan on 2011-11-02
H! **Chili555**.
  You posted:> Obviously, wlan0 is connecting. I'm sure that the presence of the  external USB device is confusing Network Manager. At least for the  moment, detach it and reboot so that we start with a clean slate. Now,  please show me:     Code:     Code:
     lspci -nn | grep 0280 lsmod | grep 819 dmesg | grep -e wlan -e 819 iwconfig 
I'm fairly confident that the internal is going to work just fine.
T am very certain that it will not even scan.
I ran your commands with and without the Nano plugged in. Assuming that:"detach it" meant unplug  `the  external USB device`, and not: "detach Network Manager".
Both ways lspci -nn | grep 0280 gave no response.
Without it, lsmod  | grep 819 also gave no response
dmesg | grep -e wlan -e 819 gave> [    4.32**819**0] usbhid: USB HID core driver and > iwconfig
 lo        no wireless extensions
 eth0   no wireless extensionsWith Nano plugged in:         **Edit: Sorry, this first batch is a repeat of the previous post**, > root@alan-MS-7616:/home/alan# cat /var/log/syslog | grep etwork | tail -n20
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  2 08:27:18 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 53 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 53 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 67 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 67 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --jump REJECT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface wlan0 --jump REJECT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --out-interface wlan0 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan0 --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Starting dnsmasq...
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) successful, device activated.
Nov  2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
root@alan-MS-7616:/home/alan# 

2/11 with Nano.**                      Edit: the next bit is the new one.**
root@alan-MS-7616:/home/alan# dmesg | grep -e wlan -e 819
[    0.768192] cpuidle: using governor ladder
[   14.030740] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   14.033988] Linux kernel driver for RTL8192 based WLAN cards
[   14.203039] usbcore: registered new interface driver rtl819xU
[   15.695384] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize: c808, sram size: 9290
[   15.697419] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[   15.701908] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[   15.702154] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[   15.703901] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[   15.704894] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[   15.705148] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[   15.705152] rtl819xU:FirmwareDownload92S(): Firmware Download Success
[   18.371593] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.348828] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 5, SECR_value: f
[   39.348969] rtl819xU:setKey(): dev: f21c0000, EntryNo: 0, KeyIndex: 0, KeyType: 5, MacAddr: 00:00:00:00:00:00
[   40.025998] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[   41.624343] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.265118] wlan0: no IPv6 routers present
[  108.641423] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
[  108.656348] rtl819xU:EnableHWSecurityConfig8192(): hwsec: 1, pairwise_key: 5, SECR_value: f
[  108.656543] rtl819xU:setKey(): dev: f21c0000, EntryNo: 0, KeyIndex: 0, KeyType: 5, MacAddr: 00:00:00:00:00:00
[  109.335150] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
root@alan-MS-7616:/home/alan# 
Wihout Nano, on booting it went direct to the WiFi aborted condition, with a red line on the WiFi Icon, and no way to get it to scan.
It appears that the presence of a USB dongle, actually makes the system able to get further with the installed card, and two of them is even better, as it then displays the names of the devices for each of the networks as well as the name of the latter..
Chao!** bogan**

---

### Post by chili555 on 2011-11-02
Clearly, wlan0 is trying to connect:> Nov 2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Nov 2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) successful, device activated.
Nov 2 08:27:19 alan-MS-7616 NetworkManager[1063]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.> am very certain that it will not even scan.Really.> [COLOR="Red"]wlan0     Scan completed :
           Cell 01 - Address: 00:12:BF:09:3D:7C
                     ESSID:"CYBERGRANS"[/COLOR]
                     Protocol:IEEE802.11bg
                     Mode:Master
                     Channel:6
                     Encryption key:on
                     Bit Rates:54 Mb/s
                     Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54  
                     Quality=88/100  Signal level=-53 dBm  Noise level=-114 dBm
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     Extra: Last beacon: 6ms agoYour device is attempting to connect to an ad-hoc; that is, computer-to-computer network:> NetworkManager[1063]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! [COLOR="Red"]10.42.43.0[/COLOR]/255.255.255.0 Did you edit connections in Network Manager to Create New Wireless Network? That's what is meant, an ad-hoc computer-to-computer network. Is that what you intended? No? I didn't think so. Please remove all those settings and save and close Network Manager's edit feature. Then do:```
sudo ifconfig wlan0 mode managed
```So we can identify the internal correctly, please post:```
lspci -nn
sudo lshw -C network
rfkill list all
```> Wihout Nano, on booting it went direct to the WiFi aborted condition, with a red line on the WiFi Icon, and no way to get it to scan.
It appears that the presence of a USB dongle, actually makes the system able to get further with the installed card, and two of them is even better, as it then displays the names of the devices for each of the networks as well as the name of the latter..Again, we are getting nowhere switching devices. Put the USB in the drawer in the basement and let's troubleshoot the internal and get it going.

---

### Post by bogan on 2011-11-02
H1! Chili555,
I messed up the downloads, sending a copy of a previous post and not sending the one of importance.
 Plus I should have made the identity and conditions more clear. 
I fear some of the Wlan0 entries you quote are from runs when a dongle was plugged in. Currently, the output of'>  iwlist wlan0 scan' is:
 " wlan0   Interface does not support scanning"
I am happy to to change our  agreed main task from the Nano Usb device to getting the installed card to work.
Here is the one with both dongles removed, newly taken.```
02/11/11 1900hrs Win7 m/c Linux 10.10 without any Wlan Usb device, before deleting network entries.

root@alan-MS-7616:/home/alan# cat /var/log/syslog | grep etwork | tail -n30
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): preparing device.
Nov  2 18:53:28 alan-MS-7616 avahi-daemon[1071]: Network interface enumeration completed.
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): deactivating device (reason: 2).
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> modem-manager is now available
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> Trying to start the supplicant...
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): supplicant manager state:  down -> idle
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Nov  2 18:53:28 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): supplicant interface state:  starting -> ready
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) starting connection 'CYBERGRANS'
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0/wireless): access point 'CYBERGRANS' has security, but secrets are required.
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Nov  2 18:53:33 alan-MS-7616 NetworkManager[1073]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  2 18:53:35 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): supplicant connection state:  inactive -> disconnected
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): now unmanaged
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): device state change: 6 -> 1 (reason 36)
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): deactivating device (reason: 36).
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> (wlan0): cleaning up...
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  2 18:55:43 alan-MS-7616 NetworkManager[1073]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/net/wlan0, iface: wlan0)
root@alan-MS-7616:/home/alan#
```I assume that by Network Manager you mean the "Edit Connections" item on the WiFi Icon`s drop-down menu. There was one with mode set to " Ad-Hoc" so I suppose that is the cause of what you detailed.
**Edit**: Note added:
 I checked the Networks I had in 10.04, there were six of them for  use in different places, different SSID`s and Passwords. The one with  Mode=Ad-Hoc was put there by the Administrator for a Computer club. When  I was having trouble in Feb 2010 I copied it across and just altered  the  SSID and Password. It worked then and it works now. It was only the  Realtek cards that took exception, as far as i could tell.
 With fingers crossed, I deleted them, and ran your commands. The **'ifconfig wlan0 mode managed' gave: " mode:  Unknown host!** so I do not suppose the effect is as you intended; the dmesg output was quite different, let me know if you wish me to post it.```
02/11/11 2100hrs Win7 m/c Linux 10.10 without any Wlan Usb device, after deleting Network entries.

root@alan-MS-7616:/home/alan# ifconfig wlan0 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.
``````
root@alan-MS-7616:/home/alan# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0041] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b22] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce G210] [10de:0a60] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
``````
root@alan-MS-7616:/home/alan# lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:60:6a:48
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:d800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:fbee0000-fbefffff
``````
root@alan-MS-7616:/home/alan# rfkill list all
root@alan-MS-7616:/home/alan#
```Hope we can clear up some of the confusion.
Chao!, **bogan**

---

### Post by chili555 on 2011-11-03
> root@alan-MS-7616:/home/alan# ifconfig wlan0 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.Curses! I was off by one letter; I meant:```
sudo i[COLOR="Red"]w[/COLOR]config wlan0 mode managed
```Sorry about the mis-step.

Your lspci and lshw only show an internal ethernet device, not wireless. Therefor, let's concentrate all our magic powers on your **Nano Realtek RTL8188SU USB mini dongle**. Please plug it in and show me:```
lsusb
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/network/interfaces

```We may edit net.rules to expunge any details from the previous (broken??) device.

Also, please do:```
sudo gedit /etc/NetworkManager/NetworkManager.conf 
```If managed=false, change it to managed=true; proofread, save and close gedit. Reboot.

---

### Post by bogan on 2011-11-03
Hi! **Chili555**,
**First:** unsurprisingly, ( to me at any rate ) **without any USB dongles**:```
  sudo iwconfig wlan0 mode managed
Error for wireless request "Set Mode" (8806)  :
SET failed on device wlan0  : No such device.

``` **Second**: I had rescued the **Getnet Ralink USB Wlan Adapter** from the  virtual basement, in order to update 10.04 on sda6 - only to find it is  no longer supported, so I am going to have to do something about that,  sooner or later. Next morning, I  rebooted into 10.10, forgetting that  the GetNet was still plugged-in, and of course it booted up and connected, straight  away.
Eventually, I realized what had happened and took the GetNet out.  The GUI immediately went back to the aborted WiFi condition and a " Connection disestablished" advisory opened. ***So back to 'normal'?    Wrong!***
It had created a new Network entry for "Auto CYBERGRANS" with `mode=interface' and the security tab replaced with a red-highlighted "802.1x Security". 
Clicking on that, gave:" |-| Use 802.1x  Security for this", red-highlighted, with the tick box unticked and the rest of the page, including Password, ghosted.
 I do not know if this  has any significance, but it seems to work OK with the GetNet. Should I alter these settings**? Please  advise.**
[B]
Third:[/B]```
  03/11/11 10.10, With Getnet, (it shows as wlan0.)
root@alan-MS-7616:# nm-tool
,,,,,,
-Device:  wlan0   [Auto CYBERGRANS]
Type                        802,11 WiFi
Driver:                     usb
State:                      connected               
Default:                   yes
Speed:                    54 Mb/s
,,,,,,
```**Fourth**:  So I reran your commands:```
:03/11/2011 Win7 m/c. Linux 10.10, GetNet Ralink Usb plugged in, RE-booted, after 'Mode managed' command.

**root@alan-MS-7616:#** iwconfig wlan0 mode managed
**root@alan-MS-7616:n#** lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0041] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b22] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce G210] [10de:0a60] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
**root@alan-MS-7616:#**
*( I cannot understand why the Ralink adapter does not show, it is definitely working and so is Firefox.)*
**root@alan-MS-7616:#** lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:60:6a:48
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:d800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:fbee0000-fbefffff
  *-network
       description:** Wireless interface**
       physical id: 1
       logical name:** wlan0**
       serial: 00:1f:1f:75:bc:45
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.7 multicast=yes wireless=Ralink STA
**root@alan-MS-7616:#** rfkill list all[B]
root@alan-MS-7616:[/B]# 
```Sending **GetNe**t back to the dungeon and will reboot with **Nano** in the morning to run your other commands.
**Edit:** Sending **GetNe**t back to the dungeon and will reboot with **Nano** in the morning to run your other commands.

Chao!  **bogan**,
Chao!  **bogan**,

---

### Post by bogan on 2011-11-04
Hi!, **Chili555**.
  0600 Hrs. Before running your other commands, two queries:
 **First:   **In another Post also about a Realtek RTL8188, but a CE, not an SU, **Jonob**r posted:> 
**Re: Cannot connect to internet**  
       One other thing I would do if it was my box,  I would disable IPV6
To check IPv6 status:
          Code:
      cat /proc/sys/net/ipv6/conf/all/disable_ipv6
EndCode
 a returned 0 means it’s enabled and a 1 – disabled.. if you get     the 1, leave as is.
To disable IPv6, go to the command line paste     this in a terminal:
          Code:
      echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
 echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf 
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
 echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf     
EndCode
(PASTE IN EACH LINE ONE AT A TIME!!!!)
reboot and check IPv6 has     been disabled     Mine is not disabled, it returns:'0'.  Is this possibly significant? My Network entry shows "Ignore". Should I run the above code, first?.
 
**Second**,     Should I reinstate the blacklists you advised in Feb 2010? ?
 I set them as they are because of what Nano used, running OK  in Ubuntu 11.10, but they do not seem to have had any effect.
 Currently. 04/11 it holds:
  #Added by alan 30/10/11 for Wlan rtl adapters; edited 1/11/11
 #blacklist rt2800usb
 #blacklist rt2x00usb
 blacklist rtl8192u
 blacklist rtl8192U
 blacklist rtl819xU  .... 

 ***Trouble***! Although I shut Windows7 down normally, and later Linux also; when I booted into Win7 this morning, 04/11, it hung on the Microsoft Logo Screen for two minutes, with the logo stable without the normal pulsing; it then went into the blue “...a problem has been detected ….” screen, followed quickly by the dreaded Black Screen of Death.  
 I shut down and did a 'cold finger re-boot,' but it repeated exactly.
 With bated breath,  I booted to Ubuntu 10.10, with the** Nano USB Wlan** plugged in.  
 ***!!PHEW!!* **it worked exactly as before, except that WiFi went into its five cycles of scanning and permission requests, instead of directly to the aborted: “ Connection Disconnected" condition as it did when last run; but I think, with some confidence, that is the effect of the Nano being present.
 **So Hooray!, Linux is doing what I installed it for**, making all the hassle worth while. I was able to mount Win7 and go to the error logs and got a message:” NVIDIA GRAPHICS Driver has stopped working 4time(s)....”. So it’s not as bad as it at first looked.
 Funny thing! Since I installed the 285 nVidia driver, in both Win7 and Linux, the Ubuntu boot sequence has been interrupted by a momentary full-screen green nVidia logo.
 
Output of your requested command:```
  [FONT=Courier New, monospace][SIZE=2]04/11/11 08:50Hrs. Win7 m/c, with Nano USB, after Windows crash.

[/SIZE][/FONT] root@alan-MS-7616:/home/alan#** cd**
 root@alan-MS-7616:~#** lsusb**
 Bus 002 Device 006: ID 13d3:3306 IMC Networks  
 Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
 Bus 002 Device 004: ID 0461:4d0f Primax Electronics, Ltd  
 Bus 002 Device 003: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 003: ID 0bda:8171** Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter**
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 root@alan-MS-7616:~#** nm-tool**
 NetworkManager Tool
     State: disconnected
  **- Device: wlan0  **
**  Type:              802.11 WiFi**
**  Driver:            rtl819xU**
**  State:             disconnected**
   Default:           no
   HW Address:        00:02:72:9C:18:B8
  Capabilities:
   Wireless Properties
     WEP Encryption:  yes   WPA Encryption:  yes     WPA2 Encryption: yes
 Wireless Access Points: CYBERGRANS:      Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA
  
  - Device: eth0  
   Type:              Wired
   Driver:            r8169
   State:             unavailable
.....   ( *No cable connected* )
  root@alan-MS-7616:~#** cat /etc/udev/rules.d/70-persistent-net.rules**
 # Entries are automatically added by the 75-persistent-net-generator.rules 
  # PCI device 0x10ec:0x8168 (r8169)
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="40:61:86:60:6a:48",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
  
 #** USB device 0x0bda:0x8171 (usb)**
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:72:9c:18:b8", ATTR{dev_id}=="0x0", ATTR{type}=="1", **KERNEL=="wlan*", NAME="wlan0"**
 root@alan-MS-7616:~#** cat /etc/network/interfaces**
 auto lo
 iface lo inet loopback
 root@alan-MS-7616:~#** gedit /etc/NetWorkManager/NetworkManager.conf**
 root@alan-MS-7616:~#
 [ *Opened empty file, no such file*.]
  root@alan-MS-7616:/etc/NetWorkManager/#** dir**
 dispatcher.d nm-system-settings.conf  system-connections VPN

``` [FONT=Courier New, monospace][SIZE=2]Do you want me to 'apt-get install NetWorkManager' ??
**More trouble!** A Fire Alarm! gotogo! Cjao! **bogan**
 [/SIZE][/FONT]

---

### Post by bogan on 2011-11-04
Hi! again **Chili555**.
You Posted, this Thread, Post 7:> [COLOR=Red]wlan0     Scan completed :
           Cell 01 - Address: 00:12:BF:09:3D:7C
                     ESSID:"CYBERGRANS"[/COLOR]
                     Protocol:IEEE802.11bg
                     Mode:Master
                     Channel:6
                     Encryption key:on
                     Bit Rates:54 Mb/s
                     Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54  
                     Quality=88/100    Signal level=-53 dBm    Noise level=-114 dBm
                     IE: WPA Version 1
                         Group Cipher : TKIP
                         Pairwise Ciphers (1) : TKIP
                         Authentication Suites (1) : PSK
                     Extra: Last beacon: 6ms ago      believing wlan0 to be the installed Realtek WLAN Card.
Currently, with the Realtek Nano Card installed, an iwlist scan gives exactly the same; except only for:> "Quality=79/100  Signal level=-56 dBm  Noise level=-109 "
and:" Last beacon: 89ms ago"  Barely different, and undoubtedly from the Nano, even though 'nm-tool' shows it as' disconnected'.    *[ How can a device get a Signal Quality of 79%, when it is disconnected?? ]*
Part of the confusion comes from both cards being ( in places ) named the same as: " Type: 802.11(xx)WiFi", but named differently, elsewhere. eg Network Manager names the Nano, in full, as: "Wireless Network (Manufacturer Realtek RTL8188S Wlan Adapter)" [leaving off the "U"!]

I have found a way to force a rescan from the GUI; if unplugging and re-plugging-in does not have that effect, and the Network(s) is (are) not shown in the WiFi drop box. Go into 'Suspend'. Wait for the "NO Signal" message and press 'return'.    Hey Presto!

---

### Post by chili555 on 2011-11-04
> 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN AdapterThe correct driver for your device is *rtl8192se*. Let me take some of your questions one at a time.> Should I reinstate the blacklists you advised in Feb 2010? ?No. Why? I don't understand why you have attempted to blacklist everything in sight that might actually correctly drive your device. By the way, none of the blacklists you have are doing anything:> chili@LAPTOP60:~$ modinfo rtl8192u
ERROR: modinfo: could not find module rtl8192u
chili@LAPTOP60:~$ modinfo rtl8192U
ERROR: modinfo: could not find module rtl8192U
chili@LAPTOP60:~$ modinfo rtl8192xU
ERROR: modinfo: could not find module rtl8192xUIf you want to be tidy, you can simply remove those lines.> Do you want me to 'apt-get install NetWorkManager' ??Why? It's already installed and working correctly, as far as I can see.> Second: I had rescued the Getnet Ralink USB Wlan Adapter from the virtual basement,Unless you feel we need to change directions, I suggest you return it to its virtual basement:> I'm old and my wife, ole whatshername, says I confuse easily.Please detach it, plug in the Nano and let's stay on target.> How can a device get a Signal Quality of 79%, when it is disconnected?? ]It sees it; it doesn't need to be connected to see it. I saw a cute waitress this morning. That doesn't mean we kissed and got married.

If you set up a network connection in Network Manager, you set up an ad-hoc, computer-to-computer connection. Does it show as ad-hoc or infrastructure? What does this tell us?```
sudo modprobe rtl8192se
iwconfig
dmesg | grep wlan
```> My Network entry shows "Ignore".Perfectly adequate, it's just another way to do the same thing.

I hope, in order to preserve my diminishing supply of hair, that we will not see the Getnet again. Please???

---

### Post by bogan on 2011-11-04
Hi!,Chili555,
You Posted:> 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
The correct driver for your device is rtl8192se.nm-tool showed Driver = rtl819xU, which I assumed to be the wrong driver as Nano worked correctly 11.11 with the 8172 driver.
 Hence I blacklisted the 8192u drivers to try and force it to use another driver, as suggested in the text in blacklist.conf. Obviously, it did not work, so I thought I should remove them. But you asked me not to change things, so I asked if I should.
 I have now done so. and restored the two you originally advised me to install. As you suggested, it does not seem to have made any difference.
modprobe rtl8192se & rt8192U both gave:>  Fatal: Module rtlxxxxx not found as did rtl8172 and all the variations of number endings I could think of.
In iwconfig, Wlan0 is now 'managed':```
** iwconfig**
lo        no wireless extensions.
eth0    no wireless extensions.
wlan0   802.11b/g/n ... ESSID:"CYBERGRANS"
Mode:managed Frequency=2.437 Ghz  Access Point: 00:12:BF:09:3D:7C
Bit Rate=130 Mb/s
retry min limit:7   RTS thr:off    Fragment thr:off
Encription key:off 
Power Management:off
Link Quality=0/100 Signal=0 dBm   Noise level= 0 dBm
Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
Tx excessive rtries:0  Invalid misc:0   Missed beacon:0
```In /lib/firmware/, there are Folders for RTL8192SE & RTL8192SU, both containing sfwxx.bin files, if that is of any importance.
Also in /lib/modules/2.6.35-30-generic/kernal/drivers/net/wireless/ there is a folder for rtl8188x, but not for rtl8192x, nor is there an rtlwifi folder.> ** |**  Do you want me to 'apt-get install NetWorkManager' ??
Why? It's already installed and working correctly, as far as I can see. From my point of view I could not find it, either in GUI or a terminal - I got a Command unknown message, and there is no NetworkManager.conf file'; so I could not carry out the commands you wanted, hence my question.
Now when I enter it in a terminal I get> : NetworkManager is already running (pid 1025). So you are quite correct'!
 My most humble and guilt-ridden apologies. But should there be a .conf file, anyway? [ Note the upper case 'W' in the quote.]> If you set up a network connection in Network Manager, you set up an ad-hoc, computer-to-computer connection. Does it show as ad-hoc or infrastructure?You have miss-read my account, I did not set it up, in NetworkManager, nor any other way. It was set up automatically when, by mistake, I booted into Ubuntu 10.10 after removing all the Network connection settings, with the Edit Connections Menu item, with GetNet still plugged-in, after using it to update 10.04.
I posted:> It had created a new Network entry for "Auto CYBERGRANS" with `mode=interface' and the security tab replaced with a red-highlighted "802.1x Security". I was worried about the latter, in view of your asking for security settings to be altered to WPA.
I had, unintentionally, altered something, although you had asked me not to. 
So I thought it significant enough that I should let you know. Wish now I had`nt.

I am 100% behind concentrating on Nano, as we agreed.

I`ll get you some hair-restorer for Xmas -- or should that be Thanksgiving?
Chao!  bogan.

---

### Post by bogan on 2011-11-05
Hi!** Chili555**,
 Sorry, I left off the dmesg bit.
When run after  WiFi scan aborted:```

**dmesg | grep wlan**
 gave no response 

``` When run as soon as GUI fully established and Password entered after first scan sequence:```
:[.....] ADDCONF(NETDEV): wlan0: link is not ready.
``` Also:
```
4/11 10.10 with Nano after editing blacklist, after Win7 crash. WiFi scan aborted.
 

**dmesg | grep -e wlan -e 819**
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
  
    [* Repeated 6 screens full, then whole sequence repeats, ending: *]
  ........
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
 [&#8230;...]  Linking with CYBERGRANS,channel:6,  qos:0,  myHT:1,  network:0,   mode:6   
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth

```Also:```
**cat  /var/log/syslog | grep etwork | tail -n20 **
[&#8230;...]  alan-MS-7616 kernal: [Linking with CYBERGRANS,channel:6,  qos:0,  myHT:1,  network:0,   mode:6
  [*Repeats all 20 line*s ]

```Hope this helps.
 The cd, LM006, that came with the Nano has, as Linux driver>  rtl8712_8188_8191_8192SU_usb_linux_v2.6.005.20091112.p4.zip It contains more than 150 files, including two incomprehensible [ to me ] Read-Me files.
 

 It just occurred to me that you are probably thinking:> &#8221; Why does he keep on dragging up that blasted GetNet thingi??  He just needs to use a wired eth0 connection!" Answer: To do so, I would need to drag all my stuff a couple of miles to my friend&#8217;s house and  use his Power Line Home Plug system, then drag it back in the evening, I do not have access to an Ethernet connection here.
 Hoping we are no longer at crossed purposes!

 Chao! **bogan**.
[ PS. How do you get a** red** highlight??]

---

### Post by chili555 on 2011-11-05
I'm confused beyond all belief. You have variously referred to several versions of Ubuntu and I asked to stick to one. You have referred to several wireless devices and I asked to stick to one. I now see:> /lib/modules/[COLOR="Red"]2.6.35[/COLOR]-30-generic/kernal/Is that Ubuntu 10.04? Is that what we're sticking to? As far as I recall, rtl8192se is not included by default, raising the question, what, exactly is driving the device?```
lsmod | grep 819
```> wlan0   802.11b/g/n ... ESSID:"CYBERGRANS"
Mode:managed Frequency=2.437 Ghz  [COLOR="Red"]Access Point: 00:12:BF:09:3D:7C[/COLOR]
Bit Rate=130 Mb/s
retry min limit:7   RTS thr: off    Fragment thr: off
Encription key: off 
Power Management: off
[COLOR="Red"]Link Quality=0[/COLOR]/100 Signal=0 dBm   Noise level= 0 dBm
Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
Tx excessive rtries:0  Invalid misc:0   Missed beacon:0This implies you have a connection to an access point, but the link quality is mysterious.

I don't think firmware is the issue:> dmesg
[ 520.205969] usbcore: registered new interface driver rtl819xU
[ 520.266053] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize: c808, sram size: 9290
[ 520.268118] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[ 520.272731] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[ 520.272954] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[ 520.274752] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[ 520.275832] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[ 520.276096] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[ 520.276100] rtl819xU:FirmwareDownload92S(): [COLOR="Red"]Firmware Download Success[/COLOR]
[ 522.943785] ADDRCONF(NETDEV_UP): wlan0: link is not readyOr was that a different device and a different version??? Do you see now why it's hard to hit a moving target?

Why did you abandon 11.10?

:confused: :confused: :confused:

---

### Post by bogan on 2011-11-05
Hi! Chili555,
[ Edited before sending ]

 The most important part of this is the last section and code. For details and explanation see my next Post.

You posted:> I'm confused beyond all belief.  Yes, I imagine it** is** confusing to you.
 Believe me, In fact the reality is even more complex than you know.
 There is also  Dell Laptop on Vista that runs its internal Wlan card with no troubles at all, another Dell Laptop running Xp that has no WiFi at all, and will not run the GetNet, but for which I bought the Nano, and it ran first try; without my having to do anything.!! Added to which is a Dell Inspiron One 19T, with 64bit WIN7, which is what I typing on and Posting this from. I will not list the various versions of Linux they use. And that is ignoring the Commodore Amiga 1500Plus, which still runs, and its ancient copy of RedHat Linux.
 You Posted:> 
                                                      /lib/modules/[COLOR=#ff0000]2.6.35[/COLOR]-30-generic/kernal/ 
Is that what we're sticking to?
  Yes It is, and has been all the time, it is installed on sd8 on an external HDD attached to the computer I call my Win7 m/c.
 > Is that Ubuntu 10.04? No! It is 10.10. as you will see from the heading of my more recent Code postings.
 I0.04 is **2.6.31**-22-generic (on/dev/sda6) also on the same external HDD.>  what, exactly is driving the device? Good Question!! One I have been asking myself ever since Feb 2010 > Why did you abandon 11.10?Where did you get that idea?
  I have not abandoned 11.04 or 11.10. That is on another computer, my Vista m/c, until some of the ghastly bugs and unworkedness has been worked out. I myself had a horrible experience updating to the first, only for it to be repeated with 10.10. I was very glad I did not abandon 10.10, which, for me, has been faultless, except for this one Wlan problem. Nonetheless, I will probably have to update sda6, from 10.04 to 11.10, as the former is no longer supported.
 > [COLOR=#ff0000]Link Quality=0[/COLOR]/100                 Signal=0 dBm Noise level= 0 dBm
Rx invalid nwid:0 Rx invalid                 crypt:0 Rx invalid frag:0
Tx excessive rtries:0 Invalid misc:0                 Missed beacon:0                  
                              This implies you have a connection to an access point, but the link quality is mysterious.  
Where is the mystery??       0% means Zero/Nothing,  like Signal=0 and Noise=0 also mean nothing.
 That is exactly what it gives.
 > I don't think firmware is the issue: OK, then why is there nothing relevant in the Firmware folders?  [ See, I can ask unanswerable questions, too.]
 I assume the dmesg you quoted was this: from Post 6:```


  2/11 with Nano. Edit: the next bit is the new one.

 root@alan-MS-7616:#** dmesg | grep -e wlan -e 819**
[ 0.768192] cpuidle: using governor ladder
[ 14.030740] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[ 14.033988] Linux kernel driver for RTL8192 based WLAN cards
[ 14.203039] usbcore: registered new interface driver **rtl819xU**
[ 15.695384] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize: c808, sram size: 9290
[ 15.697419] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
[ 15.701908] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
[ 15.702154] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
[ 15.703901] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
[ 15.704894] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[ 15.705148] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
[ 15.705152] rtl819xU:FirmwareDownload92S(): Firmware Download Success  

[ 18.371593] ADDRCONF(NETDEV_UP): wlan0: link is not ready
  &#8230;......

```> Or was that a different device and a different version???It would help in answering your questions if, when quoting code like  this, you would include the Post number as well as the command that  produced it.>  Do you see now why it's hard to hit a moving target?   Or one you can not locate or remember exactly which of many uses of a command was the one quoted.
 As you can see there, I had by then remembered the importance of labeling things with date and any unusual important set conditions. Were it not for that, I could not have answered your question with any certainty; now I can: It was definitely Ubuntu 10.10 and, as noted, with the Nano; [ but without the GetNet.]
 In addition to the head-note, I posted:
[QUOTE]Without Nano, on booting it went direct to the WiFi aborted condition, with a red line on the WiFi Icon, and no [ Edit: obvious ] way to get it to scan.
It appears that the presence of a USB dongle, actually makes the system able to get further with the installed card, and two of them is even better, as it then displays the names of the devices for each of the networks as well as the name of the latter.
 I was then, and, to a certain extent, still am, uncertain whether Nano, or the installed card, get to be Wlan0, in any particular instance.
 There must, surely, be some procedure that decides which will get priority, or if they were both working, would both scan at the same time?. Or is it possible that both are attempting to connect in turn as Wlan0. so we do not see Wlan1, and can not tell one from the other.

I seem to remember from another Thread, a command to de-activate the installed card, or one of them; could we try that? or would that only work on a Laptop?

 Part of this uncertainty, and of the confusion, is that the outputs from some commands are inconsistent, as was with the cases of the dmseg output, quoted above and in my previous post.
[*Edited before Posting , added, not edited for errors.]*

  I think I have found the answer to this, and it is important enough, in my opinion, to send it in a separate Post. Basically, it depends on exactly when in the scanning process the dmesg output is recorded. Both Posts, however different, are valid, and I have captured a couple that include elements of both. I include one example of code here```


5/11 10.10 Win7 m/c, Nano plugged into face sockets, after first rescan sequence
 
root@alan-MS-7616:# **dmesg | grep -e wlan -e 819**
   .....rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
   .....rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
   ===>ieee80211_associate_procedure_wq(), chan:6
   .....rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 

    [ Repeats this line for 6 screens full ]
 

   .....rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
   =================>ieee80211_authentication_req():auth->algorithm is 0
   ===>ieee80211_associate_procedure_wq(), chan:6
  ..... rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 

   [ Repeats this line for 2 screens full ]
 

 [ 1147.458172] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
  746.381902] ===>ieee80211_associate_procedure_wq(), chan:6
 [ 1147.458172] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 [ 1147.458172] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 [ 1150.967898] rtl819xU:==========>rtl8192_down()
 [ 1150.977837] rtl819xU:<==========rtl8192_down()
 [ 1151.025518] rtl819xU:=============>**wlan driver to be removed**
 [ 1151.035733] rtl819xU:**wlan driver removed**
 [ 1156.179514] rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize: c808, sram size: 9290
 [ 1156.181683] rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
 [ 1156.186523] rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
 [ 1156.186764] rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
 [ 1156.188544] rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
 [ 1156.189541] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
 [ 1156.189785] rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
 [ 1156.189790] rtl819xU:FirmwareDownload92S(): **Firmware Download Success**
 [ 1158.851325] ADDRCONF(NETDEV_UP):** wlan0: link is not ready**
 [ 1191.259639] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 [ 1193.809516] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 root@alan-MS-7616:#

```

---

### Post by bogan on 2011-11-05
Hi!** Chili555**
 The first part of this is much the same as in my previous Post No.17.

 The second part is a fuller description of the conditions under which the data was captured, and of how and why the conditions arose, and the problem that triggered these particular tests. [ *Which I regard as significant, even though they introduce - and dismiss - yet another variable*.]
I have attempted to write it so that anyone coming afresh to the issue can understand it, without recourse to Post Crawling in search of gold.
 [ My mindset is clearly different from yours, so feel free to ignore what seems to you, redundant, or does not fit with your approach to problem-solving.]

 I posted in Post17:> &#8230;... The outputs from some commands are inconsistent, as they were with the cases of the dmseg outputs, quoted above [ Chill555, Post16] and in my previous post [ Post15.] Where the first contained important data, whereas the later held only six screens full of a single repeated line.
 Yet both were similar, ostensibly captured under identical conditions.

 Chili555 Posted:```
    wlan0 802.11b/g/n ...   ESSID:"CYBERGRANS"
Mode:managed Frequency=2.437 Ghz      Access Point: 00:12:BF:09:3D:7C
BitRate=130 Mb/s
retry min limit: 7        RTS thr: off            Fragment thr :off
Encription key: off 
Power Management: off
Link  Quality=0/100    Signal=0 dBm          Noise level= 0 dBm
Rxinvalid nwid:0         Rx invalid crypt:0     Rx invalid frag:0
Txexcessive rtries:0    Invalid misc:0         Missed beacon:0   
``` And: [ Edited for readability.]```
  ** dmesg**
  usbcore: registered new interface driver rtl819xU
  rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30, imemsize:  c808, sram size: 9290
  rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
  rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success
  rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
  rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff)
  rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
  rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success
  rtl819xU:FirmwareDownload92S(): Firmware  Download Success
  ADDRCONF(NETDEV_UP):  wlan0: link is not ready   
``` I Posted:Code:
 ```

4/11,Ubuntu 10.10 with Nano after editing blacklist, after Win7 crash. WiFi scan aborted.

 root@alan-MS-7616:# **dmesg | grep -e wlan -e 819**
 [&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth

 [ This Line Repeated 6 Screens-full, then whole sequence repeats, ending: ]
 ........
[&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
[&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth 
[&#8230;...]  Linking with CYBERGRANS,channel:6,  qos:0,  myHT:1,  network:0,   mode:6
[&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
[&#8230;...]  rtl919xU: SetBWModeCallback819SUsbWorkItem(): Switch to 20MHz bandwidth
root@alan-MS-7616:/home/alan#
```Also, I posted, in Post15:>  I think I have found the answer to this, and it is important enough, in my opinion, ..... Basically, it depends on exactly when in the scanning process the dmesg output is recorded. Both Posts, however different, are valid, and I have captured a couple that include elements of both. ```

5/11 10.10 Win7 m/c, Nano plugged into face sockets, after first re-scan sequence.   

root@alan-MS-7616:# **dmesg | grep -e wlan -e 819**
 ........
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
 ===>ieee80211_associate_procedure_wq(), chan:6
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 

    [   Repeats this line for 6 screens-full  ]

...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
=================>ieee80211_authentication_req():auth->algorithm is 0
===>ieee80211_associate_procedure_wq(), chan:6 
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
 
    [  Repeats this line for 2 screens full ]   

...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
...  ===>ieee80211_associate_procedure_wq(), chan:6
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
...rtl819xU:==========>rtl8192_down() 
...rtl819xU:<==========rtl8192_down() 
...rtl819xU:=============>**wlan driver to be removed **
...rtl819xU:**wlan driver removed **
...rtl819xU:FirmwareRequest92S(): signature: 8192, version: 903f, size: 30,
 imemsize: c808, sram size: 9290
...rtl819xU:FirmwareCheckReady(): LoadFWStatus(1), success
...rtl819xU:FirmwareCheckReady(): LoadFWStatus(2), success 
...rtl819xU:FirmwareCheckReady(): DMEM code download success, CPUStatus(0x3f)
...rtl819xU:FirmwareCheckReady(): polling load firmware ready, CPUStatus(ff) 
...rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e) 
...rtl819xU:FirmwareCheckReady(): LoadFWStatus(3), success 
...rtl819xU:FirmwareDownload92S(): **Firmware Download Success **
...ADDRCONF(NETDEV_UP): **wlan0: link is not ready** 
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
...rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
root@alan-MS-7616:#
```**Summary:**
Thus the confusion was resolved, both were valid parts of a very long sequence, of which only a part was displayed,  producing the impression of contradictory unpredictability. Which part was captured depended on exactly when the command was executed.
 **Situation:**
 Searching for a possible explanation for the starling difference, it occurred to me that the NANO Realtek RTL8188SU Wlan 802/11/b/g/n USB 2.0 Wireless Adapter might have been knocked , misplaced or not fully engaged in the rear USB socket, which is a bit vulnerable. But it was quite OK.
 I then recalled that I had previously plugged it into one of the front-face sockets, and some devices are critical to which USB socket or bank they are in.

 In the current situation, on booting into the Ubuntu 10.10 Gui screen, before the   Authentication and keyring 'Default` Passwords have been entered, the WiFi icon is either not displayed, or is not active and has a red line through it; as it does if the scanning and Network connection fail.
  When they have been correctly accepted, the WiFi Icon appears as a shell-like image or a number of rays in a fan, and series of white cords rise repeatedly through it, indicating scanning is continuing.
 After 50 passes, a further Password requester appears, and as long as the password  is not correctly entered, the scanning will continue. After four of these sequences are complete, the scanning is aborted, the Icon stays inactive and the red line reappears.
**Action**:
  To checkout if the state and position of the NANO USB dongle was a cause of the problem, I rebooted many times, and ran the dmesg commands again, making certain that I did so in exactly the same stage in the process, for each condition. Even a few seconds can mean several full screen of data difference in the display.
**Result:**
 The results clearly established that the USB socket used had no influence on the output.
 This section suggests why the rtl8292 driver gets used but is then ditched when it fails, and hence cannot be located:
```
...rtl819xU:==========>rtl8192_down()
...rtl819xU:<==========rtl8192_down()
...rtl819xU:=============>**wlan driver to be remove**d
...rtl819xU:**wlan driver removed** 
``` :-({|=   **bogan.**

---

### Post by chili555 on 2011-11-06
> I seem to remember from another Thread, a command to de-activate the installed card, or one of them; could we try that? What installed card? Did we not determine that there is no other installed card here? Please see posts #8 where you listed all your PCI devices and determined that none were wireless; and post #9 where I said:> Your lspci and lshw only show an internal ethernet device, not wireless. 
> Quote:
I don't think firmware is the issue:
OK, then why is there nothing relevant in the Firmware folders?Which folders are those? How do you know what firmware is required and therefor present or missing if you don't know what driver is driving the Nano? Please run and post:```
lsmod | grep 819
```> It appears that the presence of a USB dongle, actually makes the system able to get further with the installed card, and two of them is even better, as it then displays the names of the devices for each of the networks as well as the name of the latter.What two? The Nano and...what?? When we examined /etc/udev/rules.d/70-persistent-net.rules in post #11, we see the ethernet and the Nano; nothing else. Are you saying that networking gets started correctly for the wireless if and only if the ethernet is plugged in?

---

### Post by bogan on 2011-11-06
H!, **Chili555**.
 Immediate reaction to your very prompt response: 

First: Win 7 says 6hat there is a &#8220;RealtekRTL8191SU Wireless LAN 802.11n USB 2.0 Network Adapter&#8221; installed on this Medion MD 8341 computer, finds it, connects and operates without any problems in Windows.
 ERGO: I conclude that one **is** correctly installed, ** is** accessible, **is **in working order, and can be relied on:  no matter what Linux may, or may not, report.
Second, Correct me     if I am mistaken &#8211; as far as I am concerned, You are, without any     question, the expert one, not me &#8211; Surely, there is a distinction,     that must be maintained, between a physical material device such as     an HDD,  a Network Adapter Card or a dongle, and on the other  hand,     a digital name or identity; in effect a 'virtual' device such as sda6 or     wlan0.
 Somehow, I have no idea how, the system allocates a** priority** and a suitable     device name to every physical - or virtual &#8211; device it encounters,     and can identify as of a particular class; also gives it a number,     presumably, in the order it was recognised. [ There is some doubt in     my mind on that last point, as I am pretty sure I have seen wlan0     and wlan2 in a  m/c when wlan1 was not there.]      
 So I am suggesting     that logically, the fact that wlan0 is not found, or at least not     reported; does not say anything about the presence of a card;     whereas, if wlan0 **is** found and reported as in use, there is,     obviously, a definite certainty that an adapter card, or some equivalent, is present.
 Equally, the presence of wlan0 and     the absence of a network, can not be taken a evidence that a card is     not present.
 Something similar occurs with networks. Just because no     network is found, does not mean neither the physical card or dongle,     nor  the virtual devices. are absent: though, presumably, if a network **is** established there is a reasonable assumption that both are also preent.
 Though one could make a case for saying: "Until data is actually passed in  each direction, nothing is certain." For example: tonight, the WiFi icon became stable, a window opened saying>  CYBERGRENS: Connection established, and the drop-down showed it with a Disconnect message confirming the connected state.
 So I opened Firefox and it displayed a normal screen. But when I tried to connect to BT-Yahoo, it showed a "Could not find server at xxxx", and " Firefox is off-line". It was another 10 seconds, or so, before the screen display caught up. Or to put all that filosify aside: "Aint working right, dont mean aint there."!
Edit: note added:
Or to borrow your own metaphor: If you did not see today, the sexy waitress you saw, but did not kiss, the other day, that would not mean she was not there!

Second. { On a personal     note:[I] I apologize if I appear to be laboring things, or trying     to teach my teacher an elementary lesson, but I have served 50 years     as a fault-finder and trouble-shooter on the world's railways and      with aircraft operators. A  fairly typical experience, for me, was to     be sent somewhere staffed by people who did not know what a      high-school was, let alone pass-out from one; who spoke a language I     did not; and being presented with a non-functioning train or     aircraft, I had never seen before. 
I was expected, not only to get it     running, but also to teach the local staff to do the same, and     maintain it, after I had left.[/I][I]
So I do know a bit     about dealing with intermittent and apparently inexplicable faults:

Stick to first principles, alter things one at a time, if possible     identify what happened immediately before the failure; work to** a     strict sequential process of elimination**; compare what happens     with the failed unit or system, with what does in a working one;     check out the processes from start to finish, do not try to     short-circuit things by working backwards from the failure; replace     suspected components with known working ones, one at a time[/I]. Of which, the underlined bit is the most important, and was the underlying motive for most of my questions and suggestions. What I will plead guilty to, is that the result was to overload you beyond any reasonable capacity.

Third: >  I Posted:"...it then displays     the names of the devices for each of the networks as well as the     name of the later."

 What two? The Nano and...what??  Part of the     confusion comes from both cards being ( in places ) named the same     as: " Type: 802.11(xx)WiFi", but named differently,     elsewhere. eg Network Manager names the Nano, in full, as:>  "Wireless     Network (Manufacturer Realtek RTL8188Sb/g/n Wlan Adapter)"     [leaving off the "U"!].
While the Get Net  [*     as far as I remember, **inserting the GetNet being a  no,no* ]  Showed as:  ***Edit:** **This  next bit was Wrong,** my memory failed me. I should have noticed  *the conflict between "RTL," "RT" and " Realtek", and the fact the GetNet is a Ralink device. It should have read:>      &#8220;RalinkRT2870SU Wireless LAN 802.11n USB 2.0 Network Adapter&#8221;     But elsewhere it gets referred to as RT3970SU, or Nickname="RT2870SU". Wereas I had guessed:**&#8220;Realtek RTL2870SU Wireless LAN 802.11n USB 2.0 Network Adapter&#8221; **. Sorry, if this caused any confusion.

Four:> Your lspci and     lshw only show an internal ethernet device, not wireless. Yes!, and No!.  With     the Nano, lspci shows the RTL8111/8168B PCI Ethernet controller, but     lists  nothing that relates to a Network Adapter wireless. ie. It is     the same as in Post8.
&#8221;Currently, 06/11 22Hrs Gmt. With the Nano                 plugged in, but, the Mouse the only other Usb device installed,                  lshw shows, as the last item in the list, following disks 0 to 2,                 a  ***-network** item like this:> [B]*-network
[/B] description:  Wireless interface
 physical id:  1           logical name: wlan0
 serial: 00:02:72:9c:18:b8
 capabilities:     ethernet physical wireless
 configuration:   broadcast=yes       multicast=yes    wireless=802.11b/g/n ...[B]
Yet lshw | grep xxxxx,   where     xxxxx  equals in turn:
 network,
 *[/B]-network,
 wlan0,
 wireless,
 ethernet    and
 -e ethernet all produced zero/nothing.**.**..Unplug the     Nano and the wireless **lshw** entry disappears[B].
 [/B]The item is basically     similar the one of my original posting, Post4 in Feb 2010,  when it     was the GetNet that would not connect[B]

Important Edit:
  
Using instead: "lshw  -numeric  | grep  wlan0" gives: " logical name: wlan0" !! and[/B]> **: root@alan-MS-7616:~# ****lshw  -numeric  | grep  network      *-network**
**    *-network**
**root@alan-MS-7616:~#****EndEdit**.
 4.So were you reverting to the     installed card?
 I thought we had agreed that was the priority.
 I was     only concerned to ensure there was no interference between them, as      happens in laptops with two video cards.[B]

5.
 Currently, lsmod | grep     819 gives:
 r8192s_usb                  287404  0  
eeprom_93cx6            1345       1      r8192s_usb.[/B] .[/QUOTE]

Five:> When we examined     /etc/udev/rules.d/70-persistent-net.rules in post #11, we see the     ethernet and the Nano; nothing else.  Here you are back to the &#8220;     Aint working means it aint there&#8221; argument .
 I have no idea of the     significance of an entry in that file. But I do not like the sound     of &#8220;persistent &#8220;.

Six:>  Are you saying that networking gets started     correctly for the wireless if and only if the ethernet is plugged     in? . I do not know where you got this idea from, I do not have an     ethernet connection, and have not connected this m/c by ethernet for a year at least.    {See note below: 7}.

What I **am** saying, is that the     WiFi drop-down display,( which is absent without a USB dongle), with     one Usb dongle, just shows a single line with the SSID, without any     device name or device state.
When I had both dongles plugged  in at the same     time, the display showed_ three_ SSID lines with one carrying     the ghosted full name of the Nano RTL8188S device and &#8220; disconnected &#8220;     in black; one showing: "(Ralink802.11n WLAN)  and `Disconnect&#8221; in     white ( the GetNet ) the third just showed  the SSID with no state info. *[*     [I]Sorry to bring GetNet in again, but Wlan1, worked, even if it is     physically bust.]

Seven:  [/I]Strangely, I had arranged to take my equipment down to my friend`s house, specifically to check out the Ethernet connection, and if it did have any effect on the Wireless process. I cannot imagine that it will.

**Edi**t:The Editor crashed 2/3 of the way through editing this , would not bring up the text cursor, I have done what I could to tidy up, apologies for the mess it is in.

Chao! **bogan**,

---

### Post by chili555 on 2011-11-07
> I conclude that one is correctly installed, is accessible, is in working order, and can be relied on: no matter what Linux may, or may not, report.I imagine it is installed; it is sticking right out of the USB port, isn't it? The fact that Windows and Ubuntu describe them a bit differently is of no concern. I am quite confident that both operating systems are seeing the exact same device, the Nano.> Somehow, I have no idea how, the system allocates a priority and a suitable device name to every physical - or virtual – device it encounters, and can identify as of a particular class; also gives it a number, presumably, in the order it was recognised. That is correct, if there is a driver installed; either because it's native in the kernel or because one was added after installation. If there is no driver, it has no mechanism to know what exactly to do with a device. It will probably be able to read the device description from the chip in the device.> So I am suggesting that logically, the fact that wlan0 is not found, or at least not reported; does not say anything about the presence of a card;Correct; the device may be there but without a driver as I stated above.> whereas, if wlan0 is found and reported as in use, there is, obviously, a definite certainty that an adapter card, or some equivalent, is present.Correct.> Equally, the presence of wlan0 and the absence of a network, can not be taken a evidence that a card is not present.Correct.> Or to borrow your own metaphor: If you did not see today, the sexy waitress you saw, but did not kiss, the other day, that would not mean she was not there!Correct; she *was *there, not just connected.> Part of the confusion comes from both cards being ( in places ) named the same as: " Type: 802.11(xx)WiFi", but named differently, elsewhere. eg Network Manager names the Nano, in full, as:That's not confusing at all; a great many devices are called 802.11 wifi; USB, PCI, PCMCIA, etc.> Your lspci and lshw only show an internal ethernet device, not wireless.
Yes!, and No!. With the Nano, lspci shows the RTL8111/8168B PCI Ethernet controller, but lists nothing that relates to a Network Adapter wireless. ie. It is the same as in Post8.
”Currently, 06/11 22Hrs Gmt. With the Nano plugged in, but, the Mouse the only other Usb device installed, lshw shows, as the last item in the list, following disks 0 to 2, a *-network item like this:
Quote:
*-network
description: Wireless interface
physical id: 1 logical name: wlan0
serial: 00:02:72:9c:18:b8
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=802.11b/g/n ...

Correct! As I stated, you have an internal ethernet device and the Nano. There is no other internal device as you implied here in post #17:> It appears that the presence of a USB dongle, actually makes the system able to get further with the installed card, and two of them is even better, as it then displays the names of the devices for each of the networks as well as the name of the latter.My question for you, again, it, what installed card? What installed card facilitates the Nano?> 5.
Currently, lsmod | grep 819 gives:
r8192s_usb 287404 0
eeprom_93cx6 1345 1 r8192s_usbNow we're getting somewhere! Although I am quite confident you do not have a firmware problem, because you see networks and can, at least, intermittently connect, let's see if the firmware is in place; please run and post:```
ls /lib/firmware/RTL8192SU
```> What I am saying, is that the WiFi drop-down display,( which is absent without a USB dongle), with one Usb dongle, just shows a single line with the SSID, without any device name or device state.Perfectly normal. It's telling you that these are the networks I see that are available; click on me and if you have any required passwords; I'll connect. If you have so indicated in Network Manager, it will connect automatically.> Here you are back to the “ Aint working means it aint there” argument .No, sir; I am at the "we have searched every place we can search, every way we can search, and we only find the Nano" argument. I am trying to get you past this mis-conception, expressed in post #17:> It appears that the presence of a USB dongle, actually makes the system able to ***get further with the installed card, and two of them is even better,*** Even your readings from Windows completely support the finding that there is ***only*** the Nano wireless device.

Let's see why Network Manager connects and then drops. Please post:```
cat /etc/resolv.conf
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by bogan on 2011-11-07
H1, Chil555,
Thanks for your very clear and full response.

Thank Peter! we are at last in agreement about **some** -to me- important issues.

Unfortunately, about the most important one, we are 100% in opposition.

Hence, this quick response, about just this one point; I will return as soon as possible, to cover your other points.
{* In the following, I have identified my posts with : " **B >>**" & the post No. if needed. Similarly, Yours I have marked with :  "** C >>**".*}
 I Posted:
B >> P20
> Win 7 says that there is a &#8220;RealtekRTL8191SU Wireless LAN 802.11n USB  2.0 Network Adapter&#8221; installed on this Medion MD 8341 computer, finds  it, connects and operates without any problems in Windows.&#8220;RealtekRTL8191SU Wireless LAN 802.11n USB  2.0 Network Adapter&#8221; 
is a direct quote from Win7 Device Manager without Nano, with the Mouse the only  external USB device. ie 1t is connected to a USB port on the mother board.
When the Nano is plugged in,  Win7 Device Manager lists both.
 To ensure I had not made a mistake, I have just booted into Win7. The CYBERGRANS network connection is shown as 100%, Firefox runs and I have downloaded a Windows up-date.
 B >>> I  conclude that one is correctly installed, is accessible, is in working  order, and can be relied on: no matter what Linux may, or may not,  report. C >> P21>  I imagine it is installed; it is sticking right out of the USB port, isn't it? No, No, and no! It is plugged into my other PC, my Vista m/c, upstairs in my apartment; it is running, connecting to BT-OpenZone -- There is no WiFi access to CYBERGRANS up there.
 C >>>  ..... both operating systems are seeing the exact same device, the Nano.....  Correct, when it** is** plugged in.
 C >>>  The fact that Windows and Ubuntu describe them a bit differently is of  no concern.I still (sometimes) have some doubts about which device is being referred to, by Ubuntu, in any specific instance. Hence my suggestion to force a deactivation of any internal device, to eliminate the possibility they are mutually incompatible, or interfering with each other.
What **does** concern** me,** is that Ubuntu apparently cannot recognize a card plugged into a PCI port that Win7 has no difficulty with.
 C >>>  I am quite confident that both operating systems are seeing  the exact same device, the Nano. I too think they do, but I wish I were equally assured that they do, all the  time.

I think this issue has been the source of most of our seeming to be at cross purposes; and until it** is** resolved I doubt any other things we do, will bear fruit.

Close your eyes before your read this bit!  :
Upstairs, Ubuntu does not list a WLAN Adapter either, whether Nano in in or out, and even though both Nano as Wlan2, and the internal card as Wlan0, connected to BT-OpenZone. [ I include this info, not to annoy or confuse you, but as an important item eliminating doubt about where the fault might lie. ]
Chao! bogan.

---

### Post by chili555 on 2011-11-07
On the computer in question, with the Nano *detached* and safely in your shirt pocket, please run and post:```
lspci -nn
sudo lshw -C network
lsusb
```We shall see what we shall see!

---

### Post by bogan on 2011-11-07
Hi!, **Chili555**, we progress!

First a question from ignorance:

    As both the Nano, as an external dongle, and the internal RTL8191SU, are USB controllers, ( the latter, for all I know, may be connected to a USB port on the Motherboard, or even be incorporated in it ) they do not, or may not, occupy any PCI slots. So should either, or both, be expected to show on a list of PCI items, such as lspci ?? (* I do not have a clue about what function lshw serves.* )

Now your code requests:   [  I assume that by:> ...the computer in question,  in P21, you meant the one which is the agreed focus of our main task. ]```

 08/11/1. 00.45 Hrs. Win7 m/c, No USB Dongle, after cold finger re-boot.
 Ubuntu 10.10 updated to: 2.6.35-30-3-generic.
 ([ A Medion MD8431 m/c in which Win Device Manager  (without Nano or GetNet ) 
recognizes a Realtek RTL8191SU USB Wireless Adapter. ]

root@alan-MS-7616:~#** lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 12)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0041] (rev 12)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b22] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce G210] [10de:0a60] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
root@alan-MS-7616:~# 
``````
root@alan-MS-7616:~#** lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:60:6a:48
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:d800(size=256) memory:f8fff000-f8ffffff memory:f8ff8000-f8ffbfff memory:fbee0000-fbefffff
root@alan-MS-7616:~# 
``````
root@alan-MS-7616:~#** lsusb**
Bus 002 Device 006: ID 13d3:3306 IMC Networks 
Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 002 Device 004: ID 0461:4d0f Primax Electronics, Ltd ( ?Mouse Controller?  )
Bus 002 Device 003: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@alan-MS-7616:~# 
```I am also including:

```
root@alan-MS-7616:~#** lsmod | grep -e rt2 -e r8 -e rt**l
**r8**169                  36553  0 
mii                     4425  1 **r8**169
root@alan-MS-7616:~# 
```That Waitress is still waiting.!!

Chao! **bogan**.

---

### Post by chili555 on 2011-11-07
> they do not, or may not, occupy any PCI slots. So should either, or both, be expected to show on a list of PCI items, such as lspci ??Quite correct, if the elusive, so far mythical internal is, indeed a USB device.> I do not have a clue about what function lshw serves. List HardWare; specifically, in our test case, of the Class 'network.'> [ I assume that by:
Quote:
...the computer in question,
in P21, you meant the one which is the agreed focus of our main task. ]Yes, please.> root@alan-MS-7616:~# lsusb
Bus 002 Device 006: ID [COLOR="Red"]13d3:3306[/COLOR] IMC Networks Well, look at her! The correct driver, at least in 11.10, is r8712u. In my wife's 10.10 install, r8712u doesn't exist. Since there is no native driver, we can either ignore the internal device or build a driver for it by intricate but eminently do-able techniques.

Instead, I suggest we return to troubleshooting why the Nano seems to connect and drop.

What do you prefer?

---

### Post by bogan on 2011-11-08
H!, **Chili555**,
I quite understand that it is difficult to let go of a hard-won certainty; a mysterious one at that.
May I remind you that in a few days, you have gone from :

> fully confident the internal card can easily be got going .To the very existance of an internal USB card being a " mis-conception
At the risk of you thinking I am saying: &#8220; Told you so&#8221;, may I also remind you of how I started this thread, wanting to install the correct RealTek driver, but scared to do so, then being diverted info fixing the GetNet instead{ reminding myself that, for you, my thread is only one of many, to try and keep track of. It amazes me that you do so, as well as you do, }

You Posted: C >> P21> ** the device may be there but without a driver as I stated above.** **Great!** Please stick with that position and quit trying to convince me that to believe it might just be there, is a Mis-conception. From that position we can go forward and sort out the Nano first.

B >> P 22>  I think this issue has been the source of most of our seeming to be at cross purposes; and until it is resolved, I doubt any other things we do, will bear fruit.I believe that is still, at this moment, where we are stalled at, and the current position between us.

&#8220; at this moment,&#8221; is 22.22 Hrs. and I have been up a this till 3 am the last three nights and am seriously tired, and averaging 20 typos per sentence . This reply was intended to be short, but it kinda grew, like Topsy. So I am adding the bits you asked for, and will leave sending the others from your previous posts, till tomorrow.

I am curled up laughing;** LOL **indeed, My touch screen suddenly started drawing thick circles, about an inch in diameter and they then started moving around jerkily. My mouse pointer was nowhere near. When I moved it nearer, a fruit fly did a vertical take off.!! Sensitive, yeah.

C >> P25 You quoted from my posting, though I do not know which:

  >   root@alan-MS-7616:~# **lsusb**
    Bus 002 Device 006: ID 13d3:3306 IMC NetworksNow I get:> o8/11/11 Win7 m/c. Ubuntu 10.10. With Nano.

root@alan-MS-7616:/home/alan#** lsusb**
Bus 002 Device 006: ID 13d3:3306 IMC Networks
Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 002 Device 004: ID 0461:4d0f Primax Electronics, Ltd
Bus 002 Device 003: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 **Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter**
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@alan-MS-7616:/home/alan#root@alan-MS-7616:/home/alan#** nm-tool**
NetworkManager Tool State: connecting
- Device: **wlan0** [Auto CYBERGRANS]
Type: 802.11 WiFi
Driver: rtl819xU
State: connecting (need authentication)
Default: no
HW Address: 00:02:72:9C:18:B8
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points CYBERGRANS:Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 88 WPA
,,,,
    Device: eth0
    &#8230;....................&#8211;
root@alan-MS-7616:/home/alan#

Not laughing so much now. The forum editor crashed again and I have lost more than six hours work. This will have  to go as-is, hoping for the best
**Edit:** Next line " dmesg output" should read " cat syslog output".
Three examples of_ dmesg _output follow on next Post but one,( or two ) very revealing.
I have Just grabbed another looking for the bit where it switched  from the r8192s to the usb driver. I am adding this out of sequence.
> 9/11. Win7 m/c. With Nano. grabbed as soon as posible after Req given
{Excerpt from previous grab:}
root@alan-MS-7616:/home/alan# cat /var/log/syslog | grep usb  tail -n48
Nov  8 23:02:41 alan-MS-7616 kernel: [ 1222.424132] usb 2-1.8: new high speed USB device using ehci_hcd and address 7
Nov  8 23:02:41 alan-MS-7616 kernel: [ 1222.517661] scsi7 : usb-storage 2-1.8:1.0
Nov  8 23:03:36 alan-MS-7616 kernel: [ 1277.121531] usb 2-1.8: USB disconnect, address 7
Nov  8 23:28:20 alan-MS-7616 kernel: [ 2757.422419] usb 2-1.8: new high speed USB device using ehci_hcd and address 8
Nov  8 23:28:20 alan-MS-7616 kernel: [ 2757.515915] scsi8 : usb-storage 2-1.8:1.0
Nov  8 23:34:37 alan-MS-7616 kernel: [ 3133.314767] usb 2-1.8: USB disconnect, address 8
root@alan-MS-7616:~#

root@alan-MS-7616:~# cat /var/log/syslog |grep etwork |** -e usb**  | tail -n48 
Nov  9 11:30:19 alan-MS-7616 kernel: [    0.558078] usbcore: registered new interface driver usbfs
Nov  9 11:30:19 alan-MS-7616 kernel: [    0.558087] usbcore: registered new interface driver hub
Nov  9 11:30:19 alan-MS-7616 kernel: [    0.558108] usbcore:** registered new device driver usb**
Nov  9 11:30:19 alan-MS-7616 kernel: [    1.054427] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov  9 11:30:19 alan-MS-7616 kernel: [    1.302476] usb 2-1: new high speed USB device using ehci_hcd and address 2
Nov  9 11:30:19 alan-MS-7616 kernel: [    1.506129] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
Nov  9 11:30:19 alan-MS-7616 kernel: [    1.706105] usb 2-1.4: new high speed USB device using ehci_hcd and address 3
Nov  9 11:30:19 alan-MS-7616 kernel: [    1.869315] usb 2-1.5: new low speed USB device using ehci_hcd and address 4
Nov  9 11:30:19 alan-MS-7616 kernel: [    2.072656] usb 2-1.4.1: new high speed USB device using ehci_hcd and address 5
Nov  9 11:30:19 alan-MS-7616 kernel: [    2.264927] scsi6 : usb-storage 2-1.4.1:1.0
Nov  9 11:30:19 alan-MS-7616 kernel: [    2.265150] usbcore: registered new interface driver usb-storage
Nov  9 11:30:19 alan-MS-7616 kernel: [    2.344408] usb 2-1.4.2: new high speed USB device using ehci_hcd and address 6
Nov  9 11:30:19 alan-MS-7616 kernel: [    4.299654] usbcore: registered new interface driver hiddev
Nov  9 11:30:19 alan-MS-7616 kernel: [    4.301888] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
Nov  9 11:30:19 alan-MS-7616 kernel: [    4.301977] generic-usb 0003:0461:4D0F.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.5/input0
Nov  9 11:30:19 alan-MS-7616 kernel: [    4.301994] usbcore: registered new interface driver usbhid
Nov  9 11:30:19 alan-MS-7616 kernel: [    4.301996] usbhid: USB HID core driver
Nov  9 11:30:19 alan-MS-7616 kernel: [   13.787544]** r8192s**_usb: module is from the staging directory, the quality is unknown, you have been warned.
Nov  9 11:30:19 alan-MS-7616 kernel: [   14.069212] usbcore: registered new interface driver rtl819xU
Nov  9 11:30:19 alan-MS-7616 NetworkManager[1065]:**    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0)**
Nov  9 11:30:19 alan-MS-7616 NetworkManager[1065]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0**/usb1**/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0):** no ifupdown configuration found.**
Nov  9 12:48:32 alan-MS-7616 kernel: [    0.557973] usbcore: registered new interface driver usbfs
Nov  9 12:48:32 alan-MS-7616 kernel: [    0.557980] usbcore: registered new interface driver hub
Nov  9 12:48:32 alan-MS-7616 kernel: [    0.558004] usbcore: **registered new device driver usb**
Nov  9 12:48:32 alan-MS-7616 kernel: [    1.054427] **usb 1-1: new high speed USB device using ehci_hcd and address 2**
Nov  9 12:48:32 alan-MS-7616 kernel: [    1.298534] usb 2-1: new high speed USB device using ehci_hcd and address 2
Nov  9 12:48:32 alan-MS-7616 kernel: [    1.502100] usb 1-1.4: new high speed USB device using ehci_hcd and address 3
Nov  9 12:48:32 alan-MS-7616 kernel: [    1.706203] usb 2-1.4: new high speed USB device using ehci_hcd and address 3
Nov  9 12:48:32 alan-MS-7616 kernel: [    1.869263] usb 2-1.5: new low speed USB device using ehci_hcd and address 4
Nov  9 12:48:32 alan-MS-7616 kernel: [    2.068735] usb 2-1.4.1: new high speed USB device using ehci_hcd and address 5
Nov  9 12:48:32 alan-MS-7616 kernel: [    2.261003] scsi6 : usb-storage 2-1.4.1:1.0
Nov  9 12:48:32 alan-MS-7616 kernel: [    2.261098] usbcore: registered new interface driver usb-storage
Nov  9 12:48:32 alan-MS-7616 kernel: [    2.328549] usb 2-1.4.2: new high speed USB device using ehci_hcd and address 6
Nov  9 12:48:32 alan-MS-7616 kernel: [    4.313484] usbcore: registered new interface driver hiddev
Nov  9 12:48:32 alan-MS-7616 kernel: [    4.315484] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input3
Nov  9 12:48:32 alan-MS-7616 kernel: [    4.315576]** generic-usb **0003:0461:4D0F.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.5/input0
Nov  9 12:48:32 alan-MS-7616 kernel: [    4.315592] usbcore: registered new interface driver usbhid
Nov  9 12:48:32 alan-MS-7616 kernel: [    4.315594] usbhid: USB HID core driver
Nov  9 12:48:32 alan-MS-7616 kernel: [   13.659656] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
Nov  9 12:48:32 alan-MS-7616 kernel: [   13.911911] usbcore: registered new interface driver rtl819xU
Nov  9 12:48:32 alan-MS-7616 NetworkManager[1061]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0)
Nov  9 12:48:32 alan-MS-7616 NetworkManager[1061]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: **wlan0): no ifupdown configuration found**.
**Edit: Next line " dmesg dump" should read " cat syslog dump".**
root@alan-MS-7616:/home/alan# 13.50 Hrs. No Reason for edit: Add _dmseg_ dump.

Chao!** bogan**.{ Reason for eddit: alter emphsis}

---

### Post by chili555 on 2011-11-09
All I can say has been said:> we can either ignore the internal device or build a driver for it by intricate but eminently do-able techniques.

Instead, I suggest we return to troubleshooting why the Nano seems to connect and drop.

What do you prefer? So; which do you prefer?

By the way, the internal, which needs the driver module r8712u, should work out of the box with Ubuntu 11.10. Have you tried the live CD? Did it work?

---

### Post by bogan on 2011-11-09
H!, **Chili555**,
You Posted:  C >> 24> Instead, I suggest we return to troubleshooting why the Nano seems to connect and drop.

What do you prefer?Stick to the Nano RTL8188SU.
I am in no doubt that is the easier choice, in fact, frankly, I never thought we should have left it .  I accepted your guidance.

Tonight I ran WIN7 without any external USB. The Device Manager showed the Realtek RTL8191SU as the only Network Adapter: Realtek RTL8191SU Wireless LAN 802.11n USB 2.0 Network Adapter.

I then inserted the Nano with Win7 still running. In less than a second, the display updated to show above it, a second Network Adapter: RealtekRTL8191SU Wireless LAN 802.11n USB 2.0 Network Adapter.
 They both use the same network driver, and they both work.

As far as I am concerned that is a clear  QED.> All I can say has been said:
 I fully agree:
 There really **is** nothing more to be said.> By the way, the internal, which needs the driver module r8712u, should  work out of the box with Ubuntu 11.10. Have you tried the live CD?
I have not tried any of the versions of the LiveCd that I accumulated, as far as going on line is concerned. My 11.04 and 11.10 were both upgrade installations, worse luck, so the need did not arise.
Both the Internal card,a Ralink C73 ( 0r something like that) and the GetNet,al so a Ralink, worked with both 11.04 & 11.11 without problems. The Nano worked with the r8172_usb driver, but not very well at first;  took a long time to connect, was very slow, and the connection sometimes dropped out. ( We blamed BT.)
Once the problems with the installation were put right; Nano worked as well as GetNet, maybe a good deal faster, though both claim 150mB/s.
 [ This was reported in my very first opening Post for this thread,P1 ]

Chao!,** bogan.**

---

### Post by bogan on 2011-11-09
H!,** Chill555**,
Part 3:
These are freshly taken , not old ones dated back to when you first asked for them.
```
09/11. WIN7 M/C. 10.10. With Nano ( plus Mouse and Ram Stick)
 the only external USB items.  Edit: WiFi not scaning, WiFi `Red-Lined.

root@alan-MS-7616:~# lsusb
................
Bus 001 Device 003: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

root@alan-MS-7616:~#

root@alan-MS-7616:~#** lshw -numeric | grep wlan0**     logical name: **wlan0**
root@alan-MS-7616:~#
``````
root@alan-MS-7616:~# lshw** -numeric**
 .......... *-disk:2
.......... 
 *-**network**
   description: Wireless interface     physical id: 1        logical name:** wlan0**      
  serial: 00:02:72:9c:18:b8
  capabilities: ethernet physical wireless    
  configuration: broadcast=yes multicast=yes wireless=802.11b/g/n ... 
root@alan-MS-7616:~# 
``````
root@alan-MS-7616:~# ls /lib/firmware/RTL8192
ls: cannot access /lib/firmware/RTL8192: No such file or directory
 root@alan-MS-7616:~#** ls /lib/firmware/RTL8192***
 /lib/firmware/RTL8192E:   boot.img  data.img  main.img 
 /lib/firmware/RTL8192SE: rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin
  /lib/firmware/RTL8192SU: rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin
root@alan-MS-7616:~# 
```More of your outstanding code requests follow tomorrow, if you still need them.

Chao!, **bogan**.

---

### Post by chili555 on 2011-11-09
> root@alan-MS-7616:~# ls /lib/firmware/RTL8192
ls: cannot access /lib/firmware/RTL8192: No such file or directoryThat's not what I asked for. Please see post #21:> let's see if the firmware is in place; please run and post:
```
ls /lib/firmware/RTL8192SU

```
In fact, you do have the required firmware:```
root@alan-MS-7616:~# ls /lib/firmware/RTL8192*
 /lib/firmware/RTL8192E:   boot.img  data.img  main.img 
 /lib/firmware/RTL8192SE: rtl8192sfw492.bin  rtl8192sfw74.bin  rtl8192sfw.bin
  [COLOR="Red"]/lib/firmware/RTL8192SU[/COLOR]: rtl8192sfw492.bin  rtl8192sfw74.bin  [COLOR="Red"]rtl8192sfw.bin[/COLOR]
```> lshw -numeric | grep wlan0     logical name: wlan0The correct command is:```
sudo lshw -C network
```We don't need to see it; we know it's there. What we would like to see is:```
sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n25
```Thanks.

---

### Post by bogan on 2011-11-10
Hi!,** Chili555**,
I posted a response to your Post 30, last night - actually this morning, - about 0030 GMT.
However, it does not appear on my computer at the moment, 23.30. I am going to log off and reboot, to see if that makes a difference; hoping I do not loose this, in the process.
I have had this happen a lot in the past, but not recently.
I have the content saved on my other computer, but spread around several files, and at the moment I am too exhausted to get through the complexities, and, if not there, it will have to wait till the morning.
Chao! **bogan.**

---

### Post by chili555 on 2011-11-11
> I posted a response to your Post 30, last night - actually this morning, - about 0030 GMT.
However, it does not appear on my computer at the moment, Mine neither.

---

### Post by bogan on 2011-11-11
Hi!,**Chili555**,   {re-building post31,}    See end-note.
 You Posted, C << P30 > root@alan-MS-7616:~# ls /lib/firmware/RTL8192
 ls: cannot access /lib/firmware/RTL8192: No such file or directory That's not what I asked for.
 Please see post #21:I know, that is why I did not highlight it.
If I were 100% perfect, 100% of the time, I would have edited it out.
In the terminal I could not do so. But I missed it.
 Thus, to avoid scrolling several screens to check in your P21, I added
 the "*".
 Which had the advantage of sending all the "RTL8192xx files, which I thought might also be relevant, and to prove there were not any other "RTL8192xx" files there.
 { For the life of me, I do not know why I am devoting so much space,
 and time, on what was, after all just a silly `Typo`.}
 
You must be a very good " Let's Make Daddy Angry" Player.
 
I posted,  B >> P 26:```
root@alan-MS-7616:~#** nm-too**l
NetworkManager Tool  State: connecting
- Device: wlan0 [Auto CYBERGRANS]
Type: 802.11 WiFi
**Driver: rtl819xU**
State: connecting (need authentication)
Default: no
HW Address: 00:02:72:9C:18:B8
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points CYBERGRANS:Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz,
 Rate 54 Mb/s, Strength 88 WPA 
``` As far as I know, 'rtl819xU' is the correct driver for the Internal Card, the RTL8191 WLAN USB Adaptor; but, if you are correct that wlan0 is the Nano, then that is what is using it.
 The driver that came with Nano is old - 2009 &#8211; and the 8172 driver Realtek recommended for the RTL818x_usb Adapter, bares a warning that it is only for** Linux versions <2.6.35.** { it is not clear whether that means:&#8220; Less Than &#8220;, or &#8220; Equal to, or Less Than &#8220;
I e-mailed Realtek asking clarification, and for a copy for a version for 10.10, 11.04 & 11.10; but got no response.
 Perhaps you would have more skill &#8211; and luck &#8211; in locating one.

You quoted C >> > ```
  lshw -numeric | grep wlan0       logical name: wlan0
``` The correct command is: Code: sudo lshw -C network[/CODE]  We don't need to see it;
 we know it's there.!  Well there`s a turn-up!
Edit: The next line, clarified.
The command: 'lshw network', asked for at a time, did not work for me, nor for a lot of Clients in other  threads. who were also mislead similarly.
 I looked for a solution and found that using the `-numeric' option did do the essential bit.
 When the Nano is out, that command shows only one `*-network' ( eth0 ). When the Nano is plugged in it shows two ( eth0  & wlan0 ).  

Sorry, I have no choice now, but to leave this Post that I was re-constructing from the data that should have appeared as Post #31.

 Some nasty things have happened, which mean I will not have normal access to my Win7 machine, for an indefinite period.

 A friend has been involved in a head-on collision, I have lost my mobile, and the wife of another is newly recovering from a serious operation; whilst his business computer, a Medion identical to mine, has gone down, to a &#8220;Black Screen Of Death&#8221;: only working in a text shell, in safe mode.
 So I will be helping him to sort it out, and will be lending him my machine.
 
I will be checking Posts and my e-mail each day, and will try to find time to extract and Post the data you have requested, from what I have on my external HDD, Ram Flash drives, or on the communal Win7 Dell.

 Chao!, for now,** bogan**

---

### Post by chili555 on 2011-11-12
> As far as I know, 'rtl819xU' is the correct driver for the Internal Card, the RTL8191 WLAN USB Adaptor; but, if you are correct that wlan0 is the Nano, then that is what is using it.rtl819xU is an alias for a number of Realtek products. The driver itself mis-reports the name as *rtl819xU*. There is no such thing. Please open a terminal and do:```
modinfo rtl819xU
```You will see there is no such module. The real name of your Nano driver is r8192s_usb.

The correct driver for the internal card is r8712u which doesn't exist in Ubuntu 10.10, unless you compile it. If you want to switch tasks and do so, please let me know.

I am very sorry about your issues. I will look forward to your further posts once things settle down. Take care.

---

### Post by bogan on 2011-11-12
Hi!, **Chili555**,
You Posted:
  >> P 34 > The correct driver for the internal card is r8712u which doesn't exist  in Ubuntu 10.10, unless you compile it. If you want to switch tasks and  do so, please let me know. No! that is not at all what I want at this stage.
Let`s leave that until we have sorted out the problem with Nano in </= 11.04.  { Or, at least 10.10, our current agreed target. }
Or, worst case, we are forced to accept that this one is insoluble, and I will need to buy another GetNet, or upgrade to 11.10.

Thanks for your message; much appreciated. The good news is: my mobile has been found. The bad news is: It does not work any more.

Chao!,** bogan**.

---

### Post by chili555 on 2011-11-12
> until we have sorted out the problem with Nano Very well! Then may we see:```
sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n25
```Let's try to pin down why Network Manager and/or the driver is misbehaving.> The good news is: my mobile has been found. The bad news is: It does not work any more.Bummer. I hope things will look up for you.

---

### Post by bogan on 2011-11-13
Hi!, **Chilli555**,
You Posted,  C >> P36:> Quote:
                                                 until we have sorted out the problem with Nano                                 
Very well! Then may we see:     Code:
     sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n25 
Let's try to pin down why Network Manager and/or the driver is misbehaving. At the moment I do not have access, but will post as requested, ASAP.

In the mean time, if I can find them, I have a number of dumps using: ```

sudo cat /var/log/syslog | grep -e etwork | tail -n48 
```Please let me know if that would be of any useful help.

{  This is the third try at sending a reply, the last two were lost when I clicked the Send button under the Quick Reply box. 
So, this far, It has taken me half an hour with no result. Lets hope it is Third time lucky. At leas,t as a New Reply, I can see what sort of a mess I have produced. }

Chao!, **bogan**

---

### Post by chili555 on 2011-11-13
> Please let me know if that would be of any useful help.Probably. Let's take a look.

---

### Post by bogan on 2011-11-14
Hi!,**Chilli555,**
 I fixed my friend’s computer, or at least saved his disk and data, because I recognized the symptoms had to result from a failing nVidia 7650 GS card and not the C: disk as it at first appeared.
 Linux booted to the ` little man ` screen, apparently normally, but then the Ubuntu logo was on top of a series of widely separated,  broad dotted lines; evidently a distorted version of the boot text lines.
 I swapped my video card for his and, after a bit of juggling with the settings, all is well.
 Linux had earned its keep, again.
 So I got some access with a new video card fitted in his m/c, and mine back where it came from.
 Rather than searching out the cat syslog dumps, saved from previous, sessions,  I made a lot of new ones, using your requested syntax,  but with `-n25` replaced by `-n52`; and then picked out the most promising.
 The ones which seemed, to me, to best capture the widest range of meaningful content., at the expense of a lot of repetitive lines, though not nearly as many as in some of the rest.
 I include two, to give you some idea of the degree of consistency.
 Without studying them closely, it seems I have failed to capture the bit I noticed previously, where the system decides the 819x driver will not be successful; ditches it  and loads a driver called `usb`; which then fails as well.
I will keep looking.
 I decided not to edit the repetitions out, just to make the files smaller and more tidy. ```
 14:12:11. 17.20 Hrs. Win7 m/c, Ubuntu 10.10, With Nano. 
       Grabbed just before end of repeated scan sequence.

root@alan-MS-7616:~# **cat /var/log/syslog | grep -e etwork -e 819 | tail -n52** 
Nov 14 17:25:06 alan-MS-7616 kernel: [  203.166349] **rtl819xU:** SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:08 alan-MS-7616 kernel: [  205.677179] Linking with CYBERGRANS, channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:08 alan-MS-7616 kernel: [  205.715632] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
Nov 14 17:25:10 alan-MS-7616 NetworkManager[1064]:<warn> (**wlan0**): link timed out. Nov 14 17:25:11 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  **disconnected **-> scanning 
Nov 14 17:25:11 alan-MS-7616 kernel: [  208.226702] Linking with CYBERGRANS, channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:12 alan-MS-7616 kernel: [  209.701974] **rtl819xU: **SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:15 alan-MS-7616 kernel: [  212.212603] Linking with CYBERGRANS, channel: 6, qos:0, myHT:1, networkHT:0, mode:6 #
Nov 14 17:25:15 alan-MS-7616 kernel: [  212.250878] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:17 alan-MS-7616 NetworkManager[1064]: <info> (wlan0): supplicant connection state:  scanning -> associating 
Nov 14 17:25:17 alan-MS-7616 kernel: [  214.656637] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:17 alan-MS-7616 kernel: [  214.656658] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:17 alan-MS-7616 NetworkManager[1064]: <info> (wlan0): supplicant connection state:  associating -> disconnected 
Nov 14 17:25:17 alan-MS-7616 kernel: [  214.697029] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
Nov 14 17:25:20 alan-MS-7616 kernel: [  217.208004] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:20 alan-MS-7616 kernel: [  217.246992] rtl819xU:SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:22 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  disconnected -> scanning 
Nov 14 17:25:23 alan-MS-7616 kernel: [  219.757502] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:24 alan-MS-7616 kernel: [  221.228524] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:25 alan-MS-7616 NetworkManager[1064]: **<warn> Activation (wlan0/wireless): association took too long. **
Nov 14 17:25:25 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): device state change: 5 -> 6 (reason 0) 
Nov 14 17:25:25 alan-MS-7616 NetworkManager[1064]: <**warn> Activation** (**wlan0/wireless)**: asking for new secrets 
Nov 14 17:25:25 alan-MS-7616 NetworkManager[1064]: <info> (wlan0): supplicant connection state:  scanning -> **disconnected **
Nov 14 17:25:27 alan-MS-7616 kernel: [  223.739453] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:27 alan-MS-7616 kernel: [  223.778692] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:29 alan-MS-7616 kernel: [  226.288999] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:29 alan-MS-7616 kernel: [  226.327242] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:32 alan-MS-7616 kernel: [  228.838540] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:32 alan-MS-7616 kernel: [  228.877014] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:34 alan-MS-7616 kernel: [  231.388108] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:34 alan-MS-7616 kernel: [  231.426345] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:37 alan-MS-7616 kernel: [  233.937619] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:37 alan-MS-7616 kernel: [  233.976226] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:39 alan-MS-7616 kernel: [  236.487924] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:39 alan-MS-7616 kernel: [  236.526522] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:40 alan-MS-7616 NetworkManager[1064]:**<warn> (wlan0): link timed out.** 
Nov 14 17:25:42 alan-MS-7616 kernel: [  239.036750] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:42 alan-MS-7616 kernel: [  239.075531]** rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:44 alan-MS-7616 kernel: [  241.586271] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:44 alan-MS-7616 kernel: [  241.625335] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:47 alan-MS-7616 kernel: [  244.135838] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:47 alan-MS-7616 kernel: [  244.174422] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth
Nov 14 17:25:50 alan-MS-7616 kernel: [  246.685342] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:50 alan-MS-7616 kernel: [  246.723498]** rtl819x**U: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:52 alan-MS-7616 kernel: [  249.234903] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:52 alan-MS-7616 kernel: [  249.273375] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth N
ov 14 17:25:55 alan-MS-7616 kernel: [  251.784657] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:55 alan-MS-7616 kernel: [  251.822966] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:25:57 alan-MS-7616 kernel: [  254.334004] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:25:57 alan-MS-7616 kernel: [  254.372747] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:26:00 alan-MS-7616 kernel: [  256.883525] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:26:00 alan-MS-7616 kernel: [  256.922048] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
root@alan-MS-7616:~# 
``````
root@alan-MS-7616:~# **nm-tool** 
NetworkManager Tool
 State: connecting
- Device: **wlan0**  [Auto CYBERGRANS] --------------------------------------------- 
   Type:   802.11 WiFi    Driver:     **rtl819xU**  
  State:  **connecting (need  authentication**)
    Default:           no    HW Address:        00:02:72:9C:18:B8     
  Capabilities:   Wireless Properties:  
    WEP Encryption:  yes      WPA Encryption:  yes      WPA2 Encryption: yes
  Wireless Access Points    CYBERGRANS: Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz, Rate 54 Mb/s, Strength 88  WPA 
 - Device:   ** eth0** -----------------------------------------------------------------  
  Type:   Wired    Driver:     r8169    State:    unavailable  
  Default:     no    HW Address:      40:61:86:60:6A:48
  Capabilities:     Carrier Detect:  yes        Speed:  10 Mb/s
 Wired Properties :            Carrier:  off
 root@alan-MS-7616:~#
``````
 
14:12:11. 17.40 Hrs. Win& m/c. 10.10. With NANO 

root@alan-MS-7616:~# **cat /var/log/syslog | grep -e  etwork -e 819 | tail -n52** 
Nov 14 17:40:53 alan-MS-7616 NetworkManager[1064]: <warn> Activation (wlan0/wireless):  association took too long. 
Nov 14 17:40:53 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): device state change: 5 -> 6 (reason 0) 
Nov 14 17:40:53 alan-MS-7616 NetworkManager[1064]: <warn> Activation (**wlan0/wireless**): asking for new secrets 
Nov 14 17:40:53 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  scanning -> disconnected 
Nov 14 17:40:54 alan-MS-7616 kernel: [ 1148.877386] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:40:54 alan-MS-7616 kernel: [ 1148.915662]** rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:40:57 alan-MS-7616 kernel: [ 1151.426867] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:40:57 alan-MS-7616 kernel: [ 1151.465159] **rtl819x**U: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 1 of 5 (Device Prepare) started... 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): 
device state change: 6 -> 4 (reason 0) 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 2 of 5 (Device Configure) scheduled... 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 1 of 5 (Device Prepare) complete. 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 2 of 5 (Device Configure) starting... 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): device state change: 4 -> 5 (reason 0) 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0/wireless**): connection 'Auto CYBERGRANS'
 has security, and secrets exist.  No new secrets needed.
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Config: added 'ssid' value 'CYBERGRANS' 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Config: added 'scan_ssid' value '1' 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Config: added 'key_mgmt' value 'WPA-PSK' 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Config: added 'psk' value '<omitted>' 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: nm_setting_802_1x_get_pkcs11_engine_path: assertion
 **`NM_IS_SETTING_802_1X (setting)' failed **
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: nm_setting_802_1x_get_pkcs11_module_path: assertion
 **`NM_IS_SETTING_802_1X (setting)' failed** 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Activation (**wlan0**) Stage 2 of 5 (Device Configure) complete. 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> Config: set interface ap_scan to 1 
Nov 14 17:40:58 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  disconnected -> scanning 
Nov 14 17:40:59 alan-MS-7616 kernel: [ 1153.976843] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:40:59 alan-MS-7616 kernel: [ 1154.146438] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:02 alan-MS-7616 kernel: [ 1156.657585] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:02 alan-MS-7616 kernel: [ 1156.696219]** rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:04 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  scanning -> associating 
Nov 14 17:41:04 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  associating -> disconnected 
Nov 14 17:41:04 alan-MS-7616 kernel: [ 1159.101323] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:04 alan-MS-7616 kernel: [ 1159.101335] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:04 alan-MS-7616 kernel: [ 1159.141072]** rtl819xU:** SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:07 alan-MS-7616 kernel: [ 1161.652971] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:07 alan-MS-7616 kernel: [ 1161.691899] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:09 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  disconnected -> scanning 
Nov 14 17:41:09 alan-MS-7616 kernel: [ 1164.202505] Linking with CYBERGRANS,channel:6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:11 alan-MS-7616 kernel: [ 1165.670015] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:13 alan-MS-7616 kernel: [ 1168.180431] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:13 alan-MS-7616 kernel: [ 1168.218951]** rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:16 alan-MS-7616 NetworkManager[1064]: <info> **(wlan**0): supplicant connection state:  scanning -> associating 
Nov 14 17:41:16 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state:  associating -> **disconnecte**d 
Nov 14 17:41:16 alan-MS-7616 kernel: [ 1170.624144] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6
Nov 14 17:41:16 alan-MS-7616 kernel: [ 1170.624157] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6
Nov 14 17:41:16 alan-MS-7616 kernel: [ 1170.663972] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:18 alan-MS-7616 kernel: [ 1173.176489] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:18 alan-MS-7616 kernel: [ 1173.214947] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
Nov 14 17:41:20 alan-MS-7616 NetworkManager[1064]: 
**<warn> (wlan0): link timed out.** 
Nov 14 17:41:21 alan-MS-7616 NetworkManager[1064]: <info> (**wlan0**): supplicant connection state: ** disconnected **-> scanning 
Nov 14 17:41:21 alan-MS-7616 kernel: [ 1175.725323] Linking with CYBERGRANS,channel: 6, qos:0, myHT:1, networkHT:0, mode:6 
Nov 14 17:41:22 alan-MS-7616 kernel: [ 1177.192223] **rtl819xU**: SetBWModeCallback8192SUsbWorkItem(): Switch to 20MHz bandwidth 
root@alan-MS-7616:~# 
``` So, your request finally fulfilled,  if somewhat tardily. 

 CHAO!,  bogan.

---

### Post by chili555 on 2011-11-14
Please check here: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

It seems identical to your problem. The driver is r8192s_usb, it sees networks but doesn't actually connect. Let's try the alternative firmware. Download this file on a CD or USB key and then get it to the desktop on your subject computer: [http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz](http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz)

Right click it and select Extract Here.

Now let's put it in the correct place:```
cd Desktop
cp rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Now let's reboot. Any improvements?

---

### Post by bogan on 2011-11-15
Hi! , Chilli555,
 You Posted:   C >>P40> The driver is r8192s_usb, it sees networks but doesn't actually connect. Let's try the alternative firmware. Download this file on a CD or USB key and then get it to the desktop on your subject computer: [http://launchpadlibrarian.net/373876...8192sfw.bin.gz]("http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz") I copied and pasted your link, to the Yahoo Title bar and pressed return; all It gave me was> 
**No Such Resource**

 No such resource
I added the www. And then I got:>  **ERROR**

      **The requested URL could not be retrieved**

 
       The following error was encountered while trying     to retrieve the URL:     [http://www.launchpadlibrarian.net:443/373876...8192sfw.bin.gz](http://www.launchpadlibrarian.net:443/373876...8192sfw.bin.gz)
     [INDENT]**Access Denied.**[/INDENT]    Access control configuration prevents your     request from being allowed at this time. Please contact your service     provider if you feel this is incorrect.
     Your cache administrator is webmaster.
     


    
 
       Generated Tue, 15 Nov 2011 22:11:08 GMT by     nutmeg.canonical.com (squid/2.7.STABLE7)

Was there a typo? 

 or do I have to re-register to launchpad to get access ??

Edit, added :
This is not the first time I have been refused access to Launchpad, even to access a file I uploaded myself.
 

 **bogan**,

---

### Post by chili555 on 2011-11-15
The forum abbreviates URLs in order to keep from having huge long lines in posts. Simply click the link and save the file. Drag and drop it to your desktop if it doesn't end up there.

---

### Post by bogan on 2011-11-15
Hi again!, **Chilli555**,
 Right, I did the first part and it downloaded exactly the same file I downloaded from the REALTEK Site 11/10/2011, and mentioned in my first Posts. It was listed as for ubuntu  < 2.6.6 -35 only.
  I already had the download and the extracted file in my Download folder. The later is called: “ RTL8712_8188_8191_8192SU_usb_linux_,2.6.6.0.20110401.
 

 So, having carried out your instructions on the Desktop, not surprisingly, the cp command produces a” no such file or directory “ response.
 

 What is on the Desktop is shown in the file manager as a  “**driver**”  folder that contains yet another folder with the same name as the original extracted folder, mentioned above, but this one is a tar.gz folder: extracting which shows no less than 19 folders and 9 files; none of the names of which, bare any resemblance to the file your referred to.
 There is a 3,4 Kb `**Cheader**` file and a 7.0 Kb ` **makefile**`, the rest are all small, and listed as  type = unknown.  None of the folder’s names strike any bells for me; but all those I have looked into, contain files with same name as the folder, preceded by “ **rtl871x_ **“; which is encouraging, as that is the driver that works in 11.04 and 11.10.


 Perhaps you can now appreciate why, in my first Post of this Thread, I found this appalling confusion frightening.  
 

 After 40 Posts, I am right back where I was before I started,.
 

 What now ??
 

 **bogan**.

---

### Post by bogan on 2011-11-16
Hi!, **Chilli555**,
 Back again after a few hours sleep.
 
I Posted: B >> P43> I already had the download and the extracted file in my Download folder. The later is called: [QUOTE]“ RTL8712_8188_8191_8192SU_usb_linux_,2.6.6.0.201104 01 ".
So, having carried out your instructions on the Desktop, not surprisingly, the cp command produces a ” no such file or directory “ response.

What is on the Desktop is shown in the file manager as a “**driver**” folder that contains yet another folder with the same name as the original extracted folder, mentioned above, but this one is a tar.gz folder: extracting which shows no less than 19 folders and 9 files; none of the names of which, bare any resemblance to the file you referred to.[/QUOTE]That is note quite accurate, and, as I am, and as, probably, you also are, a bit confused. 
 The folder in Desktop at the 1st level of extraction,  is indeed called the same, as noted above, but, importantly, the letters: “RTL” are in lower case.  
 When I Right-Click on it, there no Extract option, but a compress one. Selecting the `Open` option, 
 opens a file manager window listing, amongst others, a `driver` folder: the details about which I  posted, and partly quote above, are correct.
 

 Returning to it this morning, the other folders at the 1st. level, in addition to `driver`, are: `document` and `wpa_supplicant`; also a readme.txt and a ReleaseNotes.doc file.
 The latter, despite the RealTek warning about " only for < 2.6-35 " contain, in the 2011 update, a reference to “kernal2.6.37.
 

 After all of which, I notice that in the Download bar of Firefox, is a file called> ” **rtl8192sfw.bin.gz** “ **!!!**
 Was that what I should have downloaded** and **saved???
 

 In any case I am copy-pasting it to the Desktop, and we shall see what we shall see.
 

 Chao! For now, **bogan**

---

### Post by bogan on 2011-11-16
HI !!! **Chili555**,  H1  ***H1 *** [COLOR=SeaGreen]**H1** [/COLOR]   [COLOR=Purple] Eureka! [/COLOR] It Worked.**  !!!**

At lest for the Nan0. if not for the internal card.

Nano scanned for only a few seconds and connected after less than 10 scans.

Will return with more details later.

CHAO !!      HOORAY    and many thanks for stage one !  [B]bogan
[/B]

---

### Post by chili555 on 2011-11-16
> CHAO !! HOORAY and many thanks for stage one !Hooray indeed! Glad it's working.

Dare I ask what stage two might be?

---

### Post by bogan on 2011-11-16
> **chili555 said:**
> Hooray indeed! Glad it's working.

Dare I ask what stage two might be?
Hi! , **Chilli555**,
You Posted:  C >> P46
> Hooray indeed! Glad it's working.

Dare I ask what stage two might be?* I thought we were in agreement that getting the internal USB WLAN card to work, would be delayed until the Nano was working, and there would be direct connection to the web, making the whole process easier - for me, at least*.
Whilst I had some notion of what was required to cure the Nano problem, right from the start, but had no idea how to do it; for the internal card, that will not even recognize Nano, I do not have any fresh notion of either.

Herewith, - well after lunch, it needs some editing - some fresh data I imagined you would ask for: the Syslog dump, at the end, is especially interesting as, for what little I have learnt about the process, it seems to be AOK: but no hint of the presence of the internal card.

Hoping you have some inspiration,  CHAO! and thanks again,  **bogan**.

---

### Post by chili555 on 2011-11-16
> **bogan said:**
> Hi! , **Chilli555**,
You Posted:  C >> P46
* I thought we were in agreement that getting the internal USB WLAN card to work, would be delayed until the Nano was working, and there would be direct connection to the web, making the whole process easier - for me, at least*.
Whilst I had some notion of what was required to cure the Nano problem, right from the start, but had no idea how to do it; for the internal card, that will not even recognize Nano, I do not have any fresh notion of either.

Herewith, - well after lunch, it needs some editing - some fresh data I imagined you would ask for: the Syslog dump, at the end, is especially interesting as, for what little I have learnt about the process, it seems to be AOK: but no hint of the presence of the internal card.

Hoping you have some inspiration,  CHAO! and thanks again,  **bogan**.Is this a round-about way of simply saying that stage two is to get the internal working? Please see post #25:> The correct driver, at least in 11.10, is r8712u. In my wife's 10.10 install, r8712u doesn't exist. Since there is no native driver, we can either ignore the internal device or build a driver for it by intricate but eminently do-able techniques.If you'd like to proceed, please say so and we'll get going.

---

### Post by marcelezaaa on 2011-11-16
Hi!
First of all, I am not native English speaker and "native" Linux user, and this is my first post.. (please guide me if I should be doing it differently)
My story is very similar with bogan's one: I had a wireless usb adapter that with a great help from Chili555 in another thread in this forum I could manage to get it working... but it also ended breaking and I bought a PLANEX GW-USNano which seems to need the rtl819x module to work. 
I am using Crunchbang "Statler" (based on Debian Squeeze). (but all the problems I had with this distro could be solved following steps on this forum.)

I tried to follow the steps on this wiki: [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) but it did not work.

I would really appreciate any help!!

Thank you very much,

Marcelo

---

### Post by chili555 on 2011-11-16
> **marcelezaaa said:**
> Hi!
First of all, I am not native English speaker and "native" Linux user, and this is my first post.. (please guide me if I should be doing it differently)
My story is very similar with bogan's one: I had a wireless usb adapter that with a great help from Chili555 in another thread in this forum I could manage to get it working... but it also ended breaking and I bought a PLANEX GW-USNano which seems to need the rtl819x module to work. 
I am using Crunchbang "Statler" (based on Debian Squeeze). (but all the problems I had with this distro could be solved following steps on this forum.)

I tried to follow the steps on this wiki: [http://wiki.debian.org/rtl819x](http://wiki.debian.org/rtl819x) but it did not work.

I would really appreciate any help!!

Thank you very much,

MarceloPlease start your own new thread and reference rtl819x and I'll try to help.

---

### Post by SlaneBoy on 2011-11-16
Good afternoon from Philadelphia PA . I recently dual booted the Oneiric Ocelot 11.10
distro onto my XP3 mainframe and have come to the inescapable conclusion that it was one of the single biggest mistakes in judgment I've ever stumbled across. I've been attempting to enable my WLAN that uses a Realtek RTL 8188CUS chipset onto the Linux v3.0.0.12 generic kernel with less than no success! Ndiswrapper seems to be a complete waste of productive time with the Windows driver that automatically connected me to the Internet with my XP3. It takes the  net8192cu.inf  file and immediately spits it out with an Invalid Driver response and a big red X . Imagine that! The driver drives the hardware with absolute stability on Windows but gets spit out on Ubuntu. I've tried loading a Linux v3.0 - 3.1 recent driver for my Realtek 8188CUS using make/make install and I've never(ever) seen so many errors in my entire life! I understand that a module for Wireless is supposed to be built in to recent Linux applications like Ocelot. I see no evidence of it! If it hads been Microsoft, it would've been automatically loaded into place by contact with the Internet. Doesn't happen like that with Linux, does it? It's an empty kernel that does less than nothing. How do these people exist in the real world with a product like this? It's gotta be the Damndest thing I"ve seen in a very long time. I'm an Electronics Tech and a Quick Study and it's clear that 19 of 20 people would've given up on this junk. Perhaps you can prepare a big bowl of Chili before I become violent on this one. I have the patience of God for Tech issues like this but it's like trying to learn Chinese in a short space of time. Virtually impossible! Get back to me at your convenience and perhaps you can guide me over the hurdles like a Track Star. I'll be standing by. Thanks again!

---

### Post by chili555 on 2011-11-16
> **SlaneBoy said:**
> Good afternoon from Philadelphia PA . I recently dual booted the Oneiric Ocelot 11.10
distro onto my XP3 mainframe and have come to the inescapable conclusion that it was one of the single biggest mistakes in judgment I've ever stumbled across. I've been attempting to enable my WLAN that uses a Realtek RTL 8188CUS chipset onto the Linux v3.0.0.12 generic kernel with less than no success! Ndiswrapper seems to be a complete waste of productive time with the Windows driver that automatically connected me to the Internet with my XP3. It takes the  net8192cu.inf  file and immediately spits it out with an Invalid Driver response and a big red X . Imagine that! The driver drives the hardware with absolute stability on Windows but gets spit out on Ubuntu. I've tried loading a Linux v3.0 - 3.1 recent driver for my Realtek 8188CUS using make/make install and I've never(ever) seen so many errors in my entire life! I understand that a module for Wireless is supposed to be built in to recent Linux applications like Ocelot. I see no evidence of it! If it hads been Microsoft, it would've been automatically loaded into place by contact with the Internet. Doesn't happen like that with Linux, does it? It's an empty kernel that does less than nothing. How do these people exist in the real world with a product like this? It's gotta be the Damndest thing I"ve seen in a very long time. I'm an Electronics Tech and a Quick Study and it's clear that 19 of 20 people would've given up on this junk. Perhaps you can prepare a big bowl of Chili before I become violent on this one. I have the patience of God for Tech issues like this but it's like trying to learn Chinese in a short space of time. Virtually impossible! Get back to me at your convenience and perhaps you can guide me over the hurdles like a Track Star. I'll be standing by. Thanks again!Please start your own new thread without a rant and I'll be very happy to make a believer out of you. If I don't catch it right away, feel free to send me a private message. Thanks.

---

### Post by SlaneBoy on 2011-11-16
Okay. Please excuse the tantrum but I'm usually the one taking the lead as you're now doing. You're in control. If you can make a believer out of me, God bless. Where do we begin?

---

### Post by chili555 on 2011-11-16
> Where do we begin?As I said, please start your own new thread.

---

### Post by bogan on 2011-11-16
H1!, once more, **Chilli555**, 
 To confirm that the Realtek RTL8188SU Nano USB WLAN Wireless Adapter is working OK, with the r8192xU driver installed in my Win7 computer, running LINUX UBUNTU 10.10 v 2.6.35-30-generic, I am Posting some data that I imagine you would want to receive.
On booting to the Gnome/Unity graphics screen, with the Nano already plugged-in, the WiFi Icon is still, with a red vertical line through it, until the Default Ring permission Requester password is approved.
Once it has been, the Icon becomes active and after just nine sweeps the connection is signaled as: `Established`.
 This has been consistent over at least 30 starts or re-starts; as it also is, if the Nano is inserted after Linux has booted up. 
That is to say, what is confirmed by the data included, that the Realtek RTL8191SU USB WLAN Wireless Adapter Card , installed internally, is not recognized by Linux: despite that device type being included in the complex title of  the folder holding the new firmware file.

 A question arising from this data:
                       An 'iwlist' scan shows:  ....   .... .... ....                  wlan0 in Cell 01     Address: 00:12:BF:09:3D:7C 
Whereas 'nm-tool' shows Device wlan0 with an HW Address: 00:02:72:9C:18:B8. 
Is this significant?
That is: are these two quite different values for two distinct positions ?
 Or is there a possibility that these entries are for two different devices with titles or Logical Names confused.?

  All the following code was grabbed in the same session, under the same conditions. ```
 16/11/11 Win7. 10.10. **With Nano.**  [I]Rebooted with Nano already in,  after 
rtl8188xusb driver was installed.[/I]

root@alan-MS-7616:~# [B]nm-tool
[/B] NetworkManager Tool      State: connected
 - Device: eth0 -----------------------------------------------------------------
    Type:              Wired 
   Driver:            r8169
    State:             unavailable 
   Default:           no
    HW Address:        40:61:86:60:6A:48 
  Capabilities:                 Carrier Detect:  yes               Speed:           10 Mb/s 
  Wired Properties               Carrier:         off
 - **Device: wlan0**        [Auto CYBERGRANS] --------------------------------------------- 
  Type:              802.11 WiFi 
   **Driver:**          **  rtl819xU **
   State:             connected 
   Default:           yes 
   HW Address:        00:02:72:9C:18:B8
   Capabilities:        Speed:           54 Mb/s
     Wireless Properties        WEP Encryption:  yes          WPA Encryption:  yes  WPA2 
 Encryption: yes 
   Wireless Access Points (* = current AP) 
 BTFON:           Infra, 12:CD:72:CB:6A:32, Freq 2437 MHz, Rate 16 Mb/s, Strength 65   
 BTOpenzone:      Infra, 02:CD:72:CB:6A:32, Freq 2437 MHz, Rate 16 Mb/s, Strength 69     
 BTHub3-5W6K:     Infra, 00:CD:72:CB:6A:32, Freq 2437 MHz, Rate 16 Mb/s, Strength 68 
WPA WPA2     *CYBERGRANS:  Infra, 00:12:BF:09:3D:7C, Freq 2437 MHz, Rate 54 b/s, Strength 84 
 WPA   IPv4 Settings:     Address: 192.168.2.8     Prefix:  24 (255.255.255.0)
 Gateway:   192.168.2.1     DNS:   192.168.2.1 
root@alan-MS-7616:~# 
``````
root@alan-MS-7616:~# [B]lshw -C network 
   *-network              
           [/B]description           Ethernet interface
           product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0 
           bus info: pci@0000:02:00.0 
           logical name: eth0 
           version: 03
           serial: 40:61:86:60:6a:48 
           size: 10MB/s
           capacity: 1GB/s 
           width: 64 bits 
           clock: 33MHz 
           capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical  tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
            resources: irq:43 ioport:d800(size=256) memory: f8fff000-f8ffffff memory: f8ff8000-f8ffbfff memory: fbee0000-fbefffff
 *-network        description: Wireless interface 
        physical id: 1 
        logical name: wlan0 
        serial: 00:02:72:9c:18:b8
        capabilities: ethernet physical wireless        
        configuration: broadcast=yes  ip=192.168.2.8  multicast=yes wireless=802.11b/g  link
root@alan-MS-7616:~#
``````
root@alan-MS-7616:~#** lsmod | grep -e r81 -e rt2 -e rtl **

r8192s_usb                    287404  0
eeprom_93cx6                   1345  1 r8192s_usb 
r8169                                     36553  0 
mii                                             4425  1 r8169 
root@alan-MS-7616:~#
``````
root@alan-MS-7616:~# **ifconfig wlan0 **
wlan0       Link encap:Ethernet  HWaddr 00:02:72:9c:18:b8
                 inet addr:192.168.2.8  Bcast:192.168.2.255  Mask:255.255.255.0 
                 inet6 addr: fe80::202:72ff:fe9c:18b8/64 Scope:Link 
                 UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
                 RX packets:3193 errors:0 dropped:135 overruns:0 frame:0 
                 TX packets:83 errors:0 dropped:0 overruns:0 carrier:0 
                 collisions:0 txqueuelen:1000 
                 RX bytes:1059381 (1.0 MB)  TX bytes:8488 (8.4 KB) 
root@alan-MS-7616:~#


``````
 root@alan-MS-7616:~# **iwconfig wlan0 **
wlan0            802.11b/g  link  ESSID:"CYBERGRANS"             
                  Mode:Managed  Frequency=2.437 GHz  Access Point: 00:12:BF:09:3D:7C
                              Bit Rate=54 Mb/s              
                  Retry min limit:7   RTS thr:off   Fragment thr:off           
                  Encryption key:EDEA-837A-96C0-E5EF-B311-44B2-986B-87BD-B52D-FFB7-F523-6BE4-BFBD-45CE-16ED-FC8D   
                 Security mode:open 
                 Power Management:off 
                 Link Quality=82/100   Signal level=-59 dBm   Noise level=-111 dBm           
                 Rx invalid nwid:0    Rx invalid crypt:0    Rx invalid frag:0           
                Tx excessive retries:0   Invalid misc:0     Missed beacon:0 
root@alan-MS-7616:~#
``````
root@alan-MS-7616:~#** lsusb** 
Bus 002 Device 007: ID 0781:5567 SanDisk Corp. Cruszer Blade 
Bus 002 Device 006: ID 13d3:3306 IMC Networks 
Bus 002 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader 
Bus 002 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter 
Bus 002 Device 003: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 04f3:0103 Elan Microelectronics Corp.  
Bus 001 Device 003: ID 04f2:0718 Chicony Electronics Co., Ltd  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
root@alan-MS-7616:~#
``````

**16/11/11 Win7. 10.10. With Nano.  reboot with Nano already in. after the  rtl8188xusb driver was installed.**

root@alan-MS-7616:~#** cat /var/log/syslog | grep -e wlan0 -e r81 -e usb | tail -n52 **
Nov 16 13:28:24 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 4 -> 5 (reason 0) 
Nov 16 13:28:24 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0/ wireless): access point 'Auto CYBERGRANS' has security,
 but secrets are required. 
Nov 16 13:28:24 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 5 -> 6 (reason 0) 
Nov 16 13:28:24 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 6 -> 4 (reason 0) 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 4 -> 5 (reason 0) 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0/wireless): connection 'Auto CYBERGRANS' has security, 
and secrets exist.  No new secrets needed. 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 16 13:30:03 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  inactive -> scanning 
Nov 16 13:30:10 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  scanning -> associating 
Nov 16 13:30:10 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  associating -> disconnected 
Nov 16 13:30:10 alan-MS-7616 kernel: [  271.921662] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
Nov 16 13:30:10 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  disconnected -> associated 
Nov 16 13:30:10 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake 
Nov 16 13:30:10 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): supplicant connection state:  group handshake -> completed 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful. 
 Connected to wireless network 'CYBERGRANS'. 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 5 -> 7 (reason 0) 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds) 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): DHCPv4 state changed nbi -> preinit 
Nov 16 13:30:11 alan-MS-7616 dhclient: Listening on LPF/wlan0/00:02:72:9c:18:b8 
Nov 16 13:30:11 alan-MS-7616 dhclient: Sending on   LPF/wlan0/00:02:72:9c:18:b8 
Nov 16 13:30:11 alan-MS-7616 dhclient: DHCPREQUEST of 192.168.2.8 on wlan0 to 255.255.255.255 port 67 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: Joining mDNS multicast group on 
interface wlan0.IPv6 with address fe80::202:72ff:fe9c:18b8. 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: New relevant interface wlan0.IPv6 for mDNS. 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: Registering new address record for fe80::202:72ff:fe9c:18b8 on wlan0.*. 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): DHCPv4 state changed preinit -> reboot 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled... 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started... 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete. 
Nov 16 13:30:11 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: Joining mDNS multicast group on 
interface wlan0.IPv4 with address 192.168.2.8. 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: New relevant interface wlan0.IPv4 for mDNS. 
Nov 16 13:30:11 alan-MS-7616 avahi-daemon[1119]: Registering new address record for 192.168.2.8 on wlan0.IPv4. 
Nov 16 13:30:12 alan-MS-7616 NetworkManager[1116]: <info> (wlan0): device state change: 7 -> 8 (reason 0) 
Nov 16 13:30:12 alan-MS-7616 NetworkManager[1116]: <info> Policy set 'Auto CYBERGRANS' (wlan0) as default for IPv4 routing and DNS. 
Nov 16 13:30:12 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) successful, device activated. 
Nov 16 13:30:12 alan-MS-7616 NetworkManager[1116]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 16 13:30:20 alan-MS-7616 kernel: [  282.267348] wlan0: no IPv6 routers present
Nov 16 13:43:04 alan-MS-7616 kernel: [ 1043.439106] usb 2-1.7: new high speed USB device using ehci_hcd and address 7
Nov 16 13:43:04 alan-MS-7616 kernel: [ 1043.532030] scsi7 : usb-storage 2-1.7:1.0
Nov 16 13:43:04 alan-MS-7616 init: Handling usb-device-added event 
Nov 16 13:43:04 alan-MS-7616 init: Handling usb-device-added event 
root@alan-MS-7616:~# 
```
Chao!, from a very grateful **bogan**.

---

### Post by chili555 on 2011-11-16
> An 'iwlist' scan shows: .... .... .... .... wlan0 in Cell 01 Address: 00:12:BF:09:3D:7C
Whereas 'nm-tool' shows Device wlan0 with an HW Address: 00:02:72:9C:18:B8.
Is this significant?No. nm-tool is showing the MAC address of the Nano. iwlist scanning is showing the MAC address of the router/access point it sees across the room. Entirely normal and expected.

Your settings look perfectly awesome. Please let me know what, if anything, you'd like to tackle next.

---

### Post by bogan on 2011-11-17
Hi!, **Chilli555**,

You Posted:  C >> P25:
> The correct driver, at least in 11.10, is r8712u. In my wife's 10.10 install, r8712u 
doesn't exist. Since there is no native driver, we can either ignore the internal device 
or build a driver for it by intricate but eminently do-able techniques...
... What do you prefer ?Answer: Now that the Nano is working, I prefer to go back to the internal device and deal with that.
> Dare I ask what stage two might be? Answer:  You dare. To get the internal drive working.
> Is this a round-about way of simply saying that stage two is to get the internal working? Answer: It does not seem round-about to me, merely politely avoiding being rude.
> If you'd like to proceed, please say so and we'll get going.Answer: I would like to proceed with the internal drive, so yes, let`s stop discussing it and let`s get going. 
> Please let me know what, if anything, you'd like to tackle next.Answer: If you do not know by now, I do not know how to be more clear, in English. We could try Spanish or German, or even Urdu but my [m]other tongues are rather limited to technical instruction.
What I'd like to tackle next is getting the internal RealTek WLAN USB Adapter recognized by Linux Ubuntu 10.10, and used to connect to the Cybergrans network.

I hope that clears any confusion, if not......well, what if?

Chao! bogan.                                                                    :lolflag:

---

### Post by chili555 on 2011-11-17
This is our lucky day. I wrote a tutorial about 8712u just a few moments ago: [http://ubuntuforums.org/showpost.php?p=11465180&postcount=4](http://ubuntuforums.org/showpost.php?p=11465180&postcount=4)

To install the headers, all you need to do is open a terminal and with an internet connection, do:```
sudo apt-get install linux-headers-generic build-essential
```Then proceed as outlined in my post.

---

### Post by bogan on 2011-11-17
H1! **Chilli**, from **bogan**,
I followed your link instructions to the point before the make command.
On pressing `Enter` I get: bash:  driver/rtl8712_8818_etc.....20110401/: is a directory
In the driver folder there is the tar.gz File and the folder referred to  by bash, which came from Extracting the tar.gz file there.
There is no file in that folder with a name starting with "rtl". - not in the root folder, at least.
```

17/11/11 from 10.10. Chilli555`s link executed:.

root@alan-MS-7616:/home/alan# cd Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/
root@alan-MS-7616:/home/alan/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401#  driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/
bash: driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/: is a directory
root@alan-MS-7616:/home/alan/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401# 

```So have I done something wrong?
I selected ` Extract here. `  Should I have extracted it elsewhere ?
Please advise. ** bogan**

---

### Post by chili555 on 2011-11-17
> root@alan-MS-7616:/home/alan/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401#  driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/
bash: driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/: is a directoryThis line should be:> root@alan-MS-7616:/home/alan/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401#[COLOR="Red"]**cd**[/COLOR]  driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20110401/Please try again.

---

### Post by bogan on 2011-11-17
Hi!, Chilli555,

Your link instruction, you posted:
> Re: Trying to get Planex GW-USNano (module r8712u or rtl819x)             
        .............  Now open a terminal and do:     
    ```
 cd Desktop/rtl 
```Press Tab and the remainder of the file name will fill in. Press Enter. Type:   
    ```
 driver/rtl 
```Press Tab and the remainder of the file name will fill in. Press Enter. Now do:     
    ```
 make 
make install 
modprobe 8712u 
```Please post back if you get stuck.There is no way that code is going to produce a `cd` where you indicated.

* I tried again, and was not surprised to get the same result*.

 So I repeated the procedure as if the second Code was :```
 cd driver/rtl
```I then entered the make and makefile lines,  a lot of very similar lines scrolled down the screen.
After a pause, the WiFi advisor showed " CYBERGRANS disconnected" and started scanning; after a short gap the Nano re-connected.

But, the good news, the WiFi drop-down now showed both the Nano **and**, for the first time, the 8191 internal Adapter, but disconnected.
Strangely, it is listed as:>  "Wireless Network (Manufacturer Realtek RTL8191S WLAN Adapter)".  Not RTL8191SU.

I clicked on the 8191 network entry and after a similar gap it showed `connected'.
SO , fingers crossed. I am sending this and then I am going to reboot without the Nano.

I suggest you edit the" Trying to get Planex" file. I wondered why Marcelezaaa wrote that she/he could CD to the .tar.gz file, as that is what works, but your instruction does not.

Back soon, **bogan.**

                               ):P

---

### Post by chili555 on 2011-11-17
> I suggest you edit the" Trying to get Planex" file.I appreciate your heads up. Mr. Planex is all done and connected.

Fingers crossed!

---

### Post by bogan on 2011-11-17
H1!, **Chilli555,** with stage two completed, the problem now is:  How do I mark the thread as `Solved`.  ?

I rebooted with and without Nano and the internal card connected quite quickly, but only shows one or two bars on the WIFi Icon, 38%. The Nano shows a full strength signal 87%.

The 8191 card shows up as wlan1,  but is set to default.
Both are shown in nm-tool  as using driver: "r871x_usb_drv".

Let me know if you want any other info posted.

Thanks for all your help an extreme patience. Another HOORAY !!

Chao!, **bogan**.

---

### Post by chili555 on 2011-11-18
> How do I mark the thread as `Solved`. ?There is an option up at the top under Thread Tools to Mark Solved.> without Nano and the internal card connected quite quickly, Excellent. Glad it's working!

---

### Post by bogan on 2011-11-19
H1!, **Chilli555**,

Just as well you kept your fingers crossed, the next morning things were not so rosy.

They  are however very complex and appear unpredictably and inconsistent; as  intermittent faults often are: but it is not uncommon for complex  situations to mimic both inconsistency and intermittent faults.

So,  knowing how much you dislike situations that involve multiple  computers, multiple operating systems and multiple devices, which is  what I am faced with, I have hesitated before Posting about it: so much  so that I have delayed before even composing s Post, to make sure that I  do understand what is occurring.

So leaving marking this thread  as ` Solved ` for the time being, let me ask a few questions for a basis  on which to mount a reasonable assessment of what is happening.
[I]
First.  Is it normal, unusual or very uncommon, for one of several computers  side by side, connected to, or trying to connect to the same network[/I],  to interact, causing another to drop its connection, or, for instance,  once connection has been established, for the other computer to be able  to re-establish its connection??

In parallel with that, would the  same considerations apply to a single computer with two Wlan Adapters,  possibly interfering with  - or even assisting - each other??

Second.  I assume they would have to share the available bandwidth, so would it  follow that such interference would only occur when there is a very poor  connection.??

Third. If the signal is healthy, but one computer  is more prone to cause or to sustain such interference; would that be a  sound reason to infer some definite fault as the cause, or is it the  case that some set ups are just incompatible with others.?
For  example: would it be unusual for one computer, or adapter on its own to  show a connection strength of 80-100%, and another on its own 60-80%,  when operating together showing only 60% and 34%, respectively??

Fourth.  I am sure, from the nature of my questions, that you will have inferred  a good idea of what is troubling me. Therefore, should I Post about it  in this thread, or should I open a new one,??

Looking forward to getting your experienced view and advice.

Chao! **bogan**.

---

### Post by chili555 on 2011-11-20
> First. Is it normal, unusual or very uncommon, for one of several computers side by side, connected to, or trying to connect to the same network, to interact, causing another to drop its connection, or, for instance, once connection has been established, for the other computer to be able to re-establish its connection??I have personally experienced this behavior. My sister visited and, when sitting five feet from me with her (newer, better; I'm jealous!) laptop, I couldn't stay connected. Sitting 10-12 feet away, I was fine. I tried to troubleshoot it to the fullest extent of my limited wireless ability and never came to a solution. I have a different modem-router combination waiting for her next visit.> In parallel with that, would the same considerations apply to a single computer with two Wlan Adapters, possibly interfering with - or even assisting - each other??This is an entirely unexpected behavior. Network Manager, in particular, expects that you will have one connection and one IP address. What happens when you intentionally have two is anyones guess. I have no idea why you would even attempt it. I strongly suggest that your issues will be lessened and, perhaps, easier to resolve with but one operating wireless device per computer.

DISCLAIMER: It is possible to set up two connections, for instance one in a LAN and the other in a WAN; or one managed and one bridged for connection sharing, but usually *not* with Network Manager.> Second. I assume they would have to share the available bandwidth, so would it follow that such interference would only occur when there is a very poor connection.??They would share the bandwidth, but, as I learned, the quality of the connection doesn't seem to be a factor.> Third. If the signal is healthy, but one computer is more prone to cause or to sustain such interference; would that be a sound reason to infer some definite fault as the cause, or is it the case that some set ups are just incompatible with others.?
For example: would it be unusual for one computer, or adapter on its own to show a connection strength of 80-100%, and another on its own 60-80%, when operating together showing only 60% and 34%, respectively??Probably. As I found out myself, the reasons or fix is unknown, except to ask Sis to move!> should I Post about it in this threadGo right ahead. What is there to say that you haven't covered?

As I said, the next time Sis visits, I will try a different wireless router and I will also try different channels aside from the default channel 6. From post #26:> - Device: wlan0 [Auto CYBERGRANS]
Type: 802.11 WiFi
Driver: rtl819xU
State: connecting (need authentication)
Default: no
HW Address: 00:02:72:9C:18:B8
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points CYBERGRANS:Infra, 00:12:BF:09:3D:7C, [COLOR="Red"]Freq 2437[/COLOR] MHz, Rate 54 Mb/s, Strength 88 WPA2.437 GHz is channel 6. If you get the same behavior with two different wireless routers and on channels 1, 6 and 11, then I am out of ideas/talent/mojo.

---

### Post by bogan on 2011-11-20
Hi! **Chilli555**, 

 Thanks for your revealing and instructive response to my queries about interference between computers networking.
 [LEFT]Although I have been working with my computer set up alongside the communal Dell 64bit 19T, running Windows 7, whenever I needed to update or download from the Net, for the last two years, I had not previously noticed any interference.

[/LEFT]
 Dropped connections were a fairly common occurrence in this rural area and we blamed the long land line and external interference.


 After we got both the Realtek Nano RT8188 dongle, and the Realtek RTL8191SU internal card working, I first noticed the connection between Linux long time  connecting and the Dell dropping its connection. I had therefore supposed that the interference had its cause in those changes.
 Your response puts a quite different inference on matters.
  
You Posted, C >> P66:
 > Network Manager, in particular, expects that you will have one connection and one IP address. What happens when you intentionally have two is anyone&#8217;s guess. I have no idea why you would even attempt it. I strongly suggest that your issues will be lessened and, perhaps, easier to resolve with but one operating wireless device per computer. The main reason I have used the Ralink GetNet dongle in the past, and the Nano currently, apart from the installed card not being recognized by Linux, is that both are much faster. The second reason being that the RTL8191SU card is more likely to connect at the first attempt, when a dongle is plugged in.


 However. I have now found a better way of achieving that in a more predictable way.
 

To explain it, in a way that might make sense, I need to describe what occurs in some detail.
 When I boot into Linux with the Dell  not switched on, or with its network connection temporarily disconnected,  there is no WiFi Icon showing until after entering the `Default`keyring password; when it is accepted the scanning starts and after nine or ten sweeps show on the Icon, the RTL8191SU connects.
 The Dell will then re-connect automatically, after about 30 seconds.


 If the Dell is switched on, and has its network connected, the RTL8191SU has difficulty connecting. If it succeeds in less than 20 seconds there is no problem; if it takes more the Dell drops its connection and will not re-connect until 30 seconds after the RTL8191 connection is either made or the attempt is abandoned.


 That is without the Nano or GetNet; with either, the sequence is quite different, the Red-lined WifI Icon is present from the start and an authorization password is requested in addition. When it is accepted I select the network entries in turn and  both the dongle and the internal card are connected, usually after 9 sweeps each.  
 There is not a lot of point in my going further into the details, sufficient to say I now either boot up my computer to Linux before starting the Dell, or alternatively, temporarily disconnect its network.
 
If however, I try to re-connect the Dell whilst the Realtek RTL8192SU is still scanning, and it takes the Dell more than 20 seconds to connect, then it is the Linux m/c that drops its connection.
 When both machines are running Windows there is no noticeable problem, I suspect because the connection is nearly always a lot faster.
 You also Posted: > What is there to say that you haven't covered? In fact there would have been a lot more, had your answer confirmed my suspicions, as it did not, I will leave it there.
 


  Chao! With my sincere appreciation and thanks,  **bogan**.

---

