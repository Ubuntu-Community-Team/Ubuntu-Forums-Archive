---
title: "No wireless, Network Disabled? - Toshiba Qosmio X505-Q887 Ubuntu 10.04.4 LTS"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by Nolo13 on 2013-07-01
Hello everyone!
I recently reinstalled Ubuntu on my computer, and now I cannot connect to the wireless network. In the past i've had Ubuntu and Mint installed on my machine and everything has worked fine. When I go the the wireless icon on the top right of the screen, it says "Networking Disabled". I've been reading forums and trying to fix it now for a while, but nothing I do seems to work. But then again, I'm not that tech savy.

Thanks for any help and suggestions in advance. 

```


*************** info trace ***************

***** uname -a *****

Linux wintersmute 2.6.32-46-generic #105-Ubuntu SMP Fri Mar 1 00:04:17 UTC 2013 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.4 LTS
Release:    10.04
Codename:    lucid

***** lspci *****

0a:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci
0b:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Kernel driver in use: atl1c
    Kernel modules: atl1c

***** lsusb *****

Bus 002 Device 004: ID 0930:020f Toshiba Corp. 
Bus 002 Device 003: ID 04f2:b130 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** iwconfig *****

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: asleep

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl819xSE
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN-001C4A4A6FF8: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 88 WPA WPA2
    WLAN-001C4A4A6FF8: Infra, <MAC address removed>, Freq 2462 MHz, Rate 44 Mb/s, Strength 87 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=false
WirelessEnabled=true
WWANEnabled=true

***** NetworkManager.conf *****

nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


***** interfaces *****

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"WLAN-001C4A4A6FF8"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-60 dBm  Noise level=-102 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5ms ago
          Cell 02 - Address: <MAC address removed>
                    ESSID:"WLAN-001C4A4A6FF8"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=88/100  Signal level=-60 dBm  Noise level=-114 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3ms ago


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** dmesg *****

[   15.390402] rtllib_crypt: registered algorithm 'NULL'
[   15.390406] rtllib_crypt: registered algorithm 'TKIP'
[   15.390409] rtllib_crypt: registered algorithm 'CCMP'
[   15.390411] rtllib_crypt: registered algorithm 'WEP'
[   15.390463] rtl819xSE 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.390474] rtl819xSE 0000:0a:00.0: setting latency timer to 64
[   15.526741] rtl819xSE 0000:0a:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   15.667434] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   15.677212] ===>rtllib_start_scan()
[   15.682315] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.511061] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   36.539789] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   66.527343] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  106.514133] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  156.488250] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  216.461149] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  276.434752] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  336.408957] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  396.382732] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  456.354334] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  516.329586] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  576.303477] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  636.276988] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  696.250659] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  756.224247] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  816.198057] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  876.170905] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  936.144814] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  996.118929] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1056.091737] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1116.065789] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1176.039951] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1236.013066] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1295.986779] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1355.960773] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1415.934160] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1475.907004] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1535.881577] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1595.854424] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1655.828290] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1715.801698] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1775.775875] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1835.749330] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1895.722785] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 1955.696260] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2015.669660] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2075.643304] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2135.617573] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2195.591109] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2255.564105] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2315.538374] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2375.511391] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2435.485689] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2462.505260] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2488.170592] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2495.459448] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2555.432727] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 2565.252752] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1

****************** done ******************
 
```

---

### Post by praseodym on 2013-07-01
Open this file:
```

gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Change "false" to "true" and save the file. Restart the network-manager.

Alternatively, any button/switch/key or key combination?

---

### Post by Nolo13 on 2013-07-02
Hi praseodym.
I changed the "false" to "true" and restarted the network-manager. I finally have a wireless connection now. Thanks for the help and the speedy reply!

---

### Post by Solomon Sunder on 2013-10-11
Hi praseodym,
I have a similar issue for Toshiba Qosmio F60. There is a dedicated Touch LED Switch for wireless but it works only in Windows. There are in all 7 LED Touch buttons of which only Volume+ and Volume- work. The rest do not create events on xev as well. Any idea?

---

### Post by praseodym on 2013-10-11
Please show
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by Solomon Sunder on 2013-10-29
Hi praseodym,
I had posted the details at the below links some time back. Can you have a look at it?
[http://ubuntuforums.org/showthread.php?t=2150307](http://ubuntuforums.org/showthread.php?t=2150307)
[http://askubuntu.com/questions/291783/led-touch-buttons-touchpad-toggle-not-working-in-toshiba-qosmio-f60](http://askubuntu.com/questions/291783/led-touch-buttons-touchpad-toggle-not-working-in-toshiba-qosmio-f60)
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/228726/+index](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/228726/+index)
I will post the output of the commands you requested in case you do not find the ones in the above links useful. I have found that this is called Direct Application Launch Button in Windows and implemented using PNP0C32. [FONT=Times New Roman][SIZE=3][COLOR=#000000]A driver called quickstart seems to present in Linux but I am not sure it is working in my machine.[/COLOR][/SIZE][/FONT]
[http://quickstart.sourceforge.net/](http://quickstart.sourceforge.net/)   [https://www.fortresslinux.org/download/FL-Docs/flhwlist/kernel.html](https://www.fortresslinux.org/download/FL-Docs/flhwlist/kernel.html)
I had lost hopes of getting this resolved since I found no resolution to this for around 2 years even after searching on the net plenty of times. Quickstart gives me a hope that this probably could be resolved.

---

### Post by varunendra on 2013-10-29
The details you posted don't contain lsmod. It can be useful. And given the weirdness of the issue, probably /var/log/syslog too (from a fresh boot).

Have you checked if an updated BIOS is available for your laptop?

I suggest you post these details on your thread, and continue the updates there. I'm subscribing to it ([http://ubuntuforums.org/showthread.php?t=2150307](http://ubuntuforums.org/showthread.php?t=2150307)).

---

### Post by Solomon Sunder on 2013-10-29
@varun, The link you mentioned has lsmod ([http://paste.ubuntu.com/5813573/](http://paste.ubuntu.com/5813573/)). I have the latest BIOS Version as well. [http://msdn.microsoft.com/en-us/library/windows/hardware/gg463078.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/gg463078.aspx) This is how Microsoft implements it. Will post the /var/log/syslog details once I get back home. By fresh boot did you mean clean install?

---

### Post by varunendra on 2013-10-29
Hmm.. must have missed that link.

Anyway, have you tried blacklisting "toshiba_acpi" and "toshiba_bluetooth"?
Just guessing here, because these are related to wifi and are specific to toshiba, just like your problem is.

Please try if you haven't already -
```
echo -e "blacklist toshiba_acpi\nblacklist toshiba_bluetooth" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..reboot and see what breaks what works.

If it doesn't solve the purpose, remove them again from blacklist -
```
sudo sed -i '/toshiba/ d' /etc/modprobe.d/blacklist.conf
```
(assuming there is no previous entry that contains the word "toshiba")

> By fresh boot did you mean clean install?
Nope, just a reboot, so that syslog doesn't contain unnecessary messages. Although it seems that sometimes (or often?) syslog also contains messages from previous boots.

Interesting messages could be found anywhere from booting of the system (the last appearance of line - "Command line: BOOT_IMAGE=...") upto where the devices are all probed and ready to be used.

---

### Post by Solomon Sunder on 2013-10-29
@Varun, I have posted on the thread ([http://ubuntuforums.org/showthread.php?t=2150307&p=12832289#post12832289](http://ubuntuforums.org/showthread.php?t=2150307&p=12832289#post12832289)). We can post there.

---

