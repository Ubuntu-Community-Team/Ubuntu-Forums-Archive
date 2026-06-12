---
title: "Getting Broadcom BCM4306 to work in Ubuntu 11.10"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by SlasherIT on 2011-12-19
Hi guys,

I just jumped ship to Ubuntu 11.10, finally! I'm really enjoying the performance and all that, and its really good overall, just the one problem I am having is with the wireless driver in this laptop. The wireless device is a Broadcom BCM4306. I tried looking for a driver from Broadcom, but of course from their sloppiness, they don't provide one. So I did some more research, and found this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) which supposedly should work on my card. The only problem is, I'm confused on what to do. I tried doing this, but I still get the message under Wireless Networks 'device not ready (firmware missing)'. Can someone help me step by step to get the wireless working? 

Thank you. (BTW, right now I'm using an Ethernet cable).

---

### Post by praseodym on 2011-12-19
Hi,

install the needed firmware via:

```
wget [http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz](http://media.ubuntuusers.de/forum/attachments/2480236/Broadcom_Firmware.tar.gz) 
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by SlasherIT on 2012-01-04
Hi, I did this in the terminal. Now what? It still doesn't work...

---

### Post by SlasherIT on 2012-01-04
Ok scratch that. I did a restart, and it apparently now works. Problem is though, its quite slow when browsing, any fix to that?

Also, before, I tried making the wireless work. I followed this guide, [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43), but I was unsuccessful. I don't know how to uninstall what I did, so could that be interfering with the Wireless in anyway?

---

### Post by praseodym on 2012-01-04
Please show:

```
ifconfig -a
lsmod
rfkill list
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by SlasherIT on 2012-01-04
ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:37:49:f0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe37:49f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141835 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:217856986 (217.8 MB)  TX bytes:9945511 (9.9 MB)
          Interrupt:20 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:4e:ab:9e  
          inet6 addr: fe80::290:4bff:fe4e:ab9e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:271505 (271.5 KB)  TX bytes:11348 (11.3 KB)

lsmod: 

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  3 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
b43legacy             131930  0 
nvidia               7098131  26 
snd_rawmidi            25241  1 snd_seq_midi
mac80211              393459  1 b43legacy
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39822  0 
snd                    55902  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 b43legacy,mac80211
psmouse                73673  0 
serio_raw              12990  0 
soundcore              12600  1 snd
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
irda                  185428  0 
shpchp                 32356  0 
parport_pc             32114  1 
crc_ccitt              12595  1 irda
wmi                    18744  0 
binfmt_misc            17292  1 
video                  18908  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
cb710_mmc              13421  0 
ssb                    50682  1 b43legacy
firewire_ohci          35854  0 
8139too                23283  0 
firewire_core          56937  1 firewire_ohci
8139cp                 22636  0 
crc_itu_t              12627  1 firewire_core
cb710                  13769  1 cb710_mmc

rfkill list:

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

cat /etc/resolv.conf:

# Generated by NetworkManager
domain Family
search Family Network
nameserver 192.168.1.1

cat /etc/network/interfaces:

auto lo
iface lo inet loopback


Thanks.

---

### Post by praseodym on 2012-01-04
Go to the network-manager applet, edit the wireless connection and change in IPv4 settings from

> Automatic (DHCP)

to

> Automatic (DHCP), addresses only

Add the nameservers of your ISP or the Google public NSs 8.8.8.8 and 8.8.4.4 in "DNS-servers", seperated by comma. Restart the network.

---

### Post by SlasherIT on 2012-01-06
Hi,

No good, its still either laggy and slow, or doesn't work. :(. Thanks for helping me so far btw, great job.

---

### Post by SlasherIT on 2012-01-07
Bump, sorry.

---

### Post by praseodym on 2012-01-07
There are three different versions of this card (different chipsets), so please show:

```
lspci -nnk | grep -iA2 net
dmesg | grep b43
```

---

### Post by SlasherIT on 2012-01-07
lspci -nnk | grep -iA2 net:

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company NX9500 [103c:006a]
	Kernel driver in use: 8139too
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Compaq Computer Corporation Device [0e11:00e7]
	Kernel driver in use: b43-pci-bridge

dmesg | grep b43: 

[    1.323131] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   35.004428] b43legacy-phy0: Broadcom 4306 WLAN found
[   35.028062] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   35.028086] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   35.081152] b43legacy-phy0 debug: Radio initialized
[   37.028491] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   37.092626] b43legacy-phy0 debug: Chip initialized
[   37.092919] b43legacy-phy0 debug: 30-bit DMA initialized
[   37.093187] Registered led device: b43legacy-phy0::radio
[   37.093277] b43legacy-phy0 debug: Wireless interface started
[   37.100453] b43legacy-phy0 debug: Adding Interface type 2
[   37.428110] b43legacy-phy0 ERROR: MAC suspend failed
[  152.533503] b43legacy-phy0 ERROR: MAC suspend failed
[  361.468048] b43legacy-phy0 ERROR: MAC suspend failed

---

### Post by praseodym on 2012-01-07
With this device you should be able to use the driver b43 (without "legacy"):

```
sudo modprobe -rfv b43legacy
sudo modprobe -v b43
```

See here, I dont know if the device is version 2 or 3?!

[http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)

Edit: Sorry, its (rev 02), should not work

---

### Post by SlasherIT on 2012-01-07
Uh, I'm confused in what I'm supposed to do. Should I do what you said or not or...? Sorry to sound noobie, linux ain't my thing... I'm an advanced Windows user though...

---

### Post by praseodym on 2012-01-07
Try to deactivate IPv6 system wide:

```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Reboot, and deactivate it also in the network-manager applet (IPv6-settings->Ignore). Restart the Network after that

---

### Post by SlasherIT on 2012-01-19
Didn't help really, internet via Wi-Fi is still jerky, slow ect... :(

---

### Post by praseodym on 2012-01-19
Which encryption mode do you use? I recommend using WPA2-AES if possible. Try a fixed channel in the router instead of "Automatic" (if activated). Check

```
sudo iwlist scan
iwconfig
```

---

### Post by SlasherIT on 2012-01-19
Hi, I use WPA2, the router allows both TKIP and AES, not sure which one its using though. I don't understand what you mean by fixed channel mode... Soz.

sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:77:77:5D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Family Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ba807adc4
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 000E46616D696C79204E6574776F726B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
          Cell 02 - Address: 68:7F:74:77:48:26
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"mohammad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000637fe180
                    Extra: Last beacon: 256ms ago
                    IE: Unknown: 00086D6F68616D6D6164
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F74774826102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30311042000C4A555430304B3433303336341054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Family Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:77:77:5D   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:51   Missed beacon:0

---

### Post by praseodym on 2012-01-20
> ```
IE: [COLOR="Red"]WPA[/COLOR] Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
```
Its mixed WPA/WPA2, try to set it to pure WPA2-AES in your router interface. Also the "pairwise" and "group" settings of WPA(1) with CCMP is strange.

---

### Post by SlasherIT on 2012-01-20
Sorry I can't, I have devices such as the PSP that can not use WPA2, so I keep it at WPA + WPA2 mixed mode, meaning that it can use both. All my other laptops connect via WPA2, the PSP connects via WPA, ect. To be honest, it worked fine the Wi-Fi on Windows with my current router settings... 

Also, I'm confused what you mean by 'pairwise' and 'group' setting... So what should I do next?

---

### Post by praseodym on 2012-01-20
Try Wicd with the Add-on instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager*
sudo service wicd restart
```

Choose "wlan0" as interface name and "wext" as driver. Wicd handles mixed encryptions much better than the NM does.

---

### Post by SlasherIT on 2012-01-22
Two things. One, I did as you said, yet I am not getting any improvements. Two, the network icon disappeared from the Unity bar at the top... :(.

---

### Post by praseodym on 2012-01-22
Try

> nm-applet

from terminal. Also change the channel to 1 or 11.

---

### Post by SlasherIT on 2012-02-17
Hi,

Sorry for replying so late, I've been REALLY busy.

I typed in nm-applet, and this is what I get:

The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>

Also, do you mean changing the wireless channel from the Router?

---

### Post by praseodym on 2012-02-17
Yes, connect via cable and type in the router IP into your browser. The packages **network-manager** and **network-manager-gnome** can be found on [http://packages.ubuntu.com](http://packages.ubuntu.com) . Installation by Double-clicking

---

### Post by SlasherIT on 2012-02-17
Changing the channel from 6 to 11 didn't fix anything, its still the same, choppy and slow :(. What else can I do?

---

### Post by plausible on 2012-03-04
I probably should start a new thread, but I'm also having problems with BCM4306 (version 3, according to one of the lspci commands I used). The adapter is a Linksys WMP54GS (PCI wireless adapter). The card works fine in Windows XP.
Among other things, I've tried:

[INDENT]sudo apt-get install firmware-b43-installer[/INDENT]

In /etc/modprobe.d/blacklist[something].conf (can't remember exact file name), I'm seeing that b43 is blacklisted, ssb is blacklisted, etc. However, "hwinfo --netcard" indicates that the ssb driver? is loaded for this particular card. sudo modprobe -r ssb results in an error indicating module ssb is in use.

I'm simply seeing no indication that the card is even detected by the gui network configuration tool. And the alternate hardware drivers (or somesuch) doesn't list any additional drivers.

Not sure where to go next.

Thank you!

---

### Post by bkratz on 2012-03-05
> **plausible said:**
> I probably should start a new thread, but I'm also having problems with BCM4306 (version 3, according to one of the lspci commands I used). The adapter is a Linksys WMP54GS (PCI wireless adapter). The card works fine in Windows XP.
Among other things, I've tried:
[INDENT]sudo apt-get install firmware-b43-installer[/INDENT]In /etc/modprobe.d/blacklist[something].conf (can't remember exact file name), I'm seeing that b43 is blacklisted, ssb is blacklisted, etc. However, "hwinfo --netcard" indicates that the ssb driver? is loaded for this particular card. sudo modprobe -r ssb results in an error indicating module ssb is in use.

I'm simply seeing no indication that the card is even detected by the gui network configuration tool. And the alternate hardware drivers (or somesuch) doesn't list any additional drivers.

Not sure where to go next.

Thank you!


SSB often loads even when blacklisted-don't worry about it. You will need to remove the B43 blacklist entry (or at least put a # in front of it) to load the module.

try 
sudo modprobe b43    ----- for a temporary fix. It will last until reboot, and see if you wireless works.

this will require your password which will not be echoed to the screen. If it works we can make it permanent by changing the blacklist entry.

---

### Post by SlasherIT on 2012-03-05
Could I get help now please? :(

---

### Post by plausible on 2012-03-05
> **bkratz said:**
> 
try 
sudo modprobe b43    ----- for a temporary fix. It will last until reboot, and see if you wireless works.

...If it works we can make it permanent by changing the blacklist entry.

I've already tried *sudo modprobe b43* (without touching the blacklist entry for b43) with no change. After doing this, *hwinfo --netcard* still indicates that ssb is loaded for the wireless adapter. When I'm home again, I'll try commenting the blacklist line for b43 and see if that makes a difference (your response seems to suggest that it won't). By the way, the file where *blacklist b43* appears has a comment that says the file is autogenerated by bcmwl, and any changes to the file will be overwritten. I don't know what bcmwl is (*man bcmwl* and *man -k bcmwl* aren't helpful) or how frequently this file is autogenerated. I'd prefer to change settings in a way that a reboot or an update to b43-firmware-installer won't require commenting out the blacklist line again.

Thank you!

---

### Post by praseodym on 2012-03-05
Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

### Post by plausible on 2012-03-06
Hmmm...I tried *sudo modprobe b43* again, and now in the connections menu, it shows *Wireless Networks*, and below that (greyed out), *device not ready (firmware missing)*.

You can see the output of the commands at [http://pastebin.com/515vXv9T](http://pastebin.com/515vXv9T).

Thank you!

---

### Post by praseodym on 2012-03-06
Install the firmware by hand:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by praseodym on 2012-03-06
You also need to deactivate the Broadcom-STA driver in "additional drivers", uninstall it via

> sudo apt-get remove --purge bcmwl-kernel-source

and reboot.

---

### Post by plausible on 2012-03-19
Hey, thanks much praseodym! Your last two posts were the ticket for me.

---

### Post by SlasherIT on 2012-03-29
Can anyone continue helping me with my problem? I kind of find it annoying that a person who asked a question on my thread got his solved before me :(.

---

### Post by praseodym on 2012-03-29
Try the following:

1) Check, if your router firmware is up-to-date
2) Change the SSID to something without blank
3) Remove your current profile and set up a new one

---

### Post by lisanels47 on 2012-03-29
I selected "Additional Drivers" from the menu, and it found/installed the drivers for my broadcom wireless... 

But I'm sure you tried that already.

---

### Post by SlasherIT on 2012-04-03
> **praseodym said:**
> Try the following:

1) Check, if your router firmware is up-to-date
2) Change the SSID to something without blank
3) Remove your current profile and set up a new one

Hey,

Sorry for the late reply, it seems I'm not getting email notifications. Anyways,

1. Its updated to the latest
2. Currently, the SSID is Family Network, so I should change to FamilyNetwork?
3. How would I do that/what do you mean by that?

Thanks.

---

### Post by praseodym on 2012-04-03
1) Ok
2) Yes, if possible
3) ```
gksu nm-connection-editor
```
Remove the wireless profile and set up a new one with "FamilyNetwork"

---

### Post by petermg on 2012-04-08
> **praseodym said:**
> Install the firmware by hand:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

THANK YOU!!!!!!!!!!!!!!  This worked for me!! :D

---

### Post by SlasherIT on 2012-04-18
> **praseodym said:**
> 1) Ok
2) Yes, if possible
3) ```
gksu nm-connection-editor
```
Remove the wireless profile and set up a new one with "FamilyNetwork"

Hey, sorry for the late reply, was busy.

Doing what you recommended didn't help, its still really slow. :(.

---

### Post by mang0 on 2012-07-26
Hey. I know this is a bit of a late bump for this thread, but I'm having huge problems with my BCM4306 rev2. I've just updated from 32bit Ubuntu to 64bit Ubuntu, and since then I've not got anything working.

I really need a hand on this, I've spent three days on it already. Any help greatly appreciated! More info can be given as needed.

---

