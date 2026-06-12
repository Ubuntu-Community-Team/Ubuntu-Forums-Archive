---
title: "Need experts help with wireless connection issue PLZZZ"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by GnarlyWhales on 2011-08-28
I am a new user to Linux OS, have newly installed Ubuntu 11.04 on my laptop and desktop.  In setting up wireless connections I have ran into an array of problems. 
 First, when I installed the new OS on my laptop I had to get the correct drivers and firmware for it to display and connect to any connections, had no problem here connecting to a secure wireless network (WPA or WPA2).
I then installed Ubuntu on my desktop and had to find the correct driver for the Netgear WNDA3100v2 USB adapter, got it all installed with the Windows Wireless Drivers tool or w/e it is.  This made all the available connections come up.  I tried connecting with the WPA password I was given for the network and will not connect.
I had the guy managing the network change the one I connect to, to a WEP Passphrase Shared Key thinking this would solve my issue, still nothing.  And also in doing so, now my laptop will not connect to the wireless network using the Passphrase. 

Any suggestions or solutions to this problem would be greatly appreciated :)
I do not want to go back to Windows, and I will be getting rid of my Lan connection soon so i need a solution to fix this wireless connection problem.

[EMAIL="GnarlyWhales@rocketmail.com"]GnarlyWhales@rocketmail.com[/EMAIL] or reply here

---

### Post by GnarlyWhales on 2011-08-28
^

---

### Post by fdrake on 2011-08-28
In my signature "networking" click the link and post here your results please.

---

### Post by GnarlyWhales on 2011-08-28
where exactly do I put this net.sh file at?  

> 
brandon@Dell-Linux:~$ chmod +x net.sh
chmod: cannot access `net.sh': No such file or directory
brandon@Dell-Linux:~$ 


---

### Post by superduperlinuxperson on 2011-08-28
please list the output of lspci -vnn | grep 14e4
thanks.

---

### Post by GnarlyWhales on 2011-08-28
This is only showing my ethernet connection, all is working fine there.  I connect on my desktop via Netgear WNDA3100v2 USB adapter.
I have to driver for this installed and it shows the wireless connection but will not connect to the secure wireless network even with the correct WEP Shared Key.
> 
brandon@Dell-Linux:~$ lspci -vnn | grep 14e4
04:07.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
brandon@Dell-Linux:~$ 


---

### Post by GnarlyWhales on 2011-08-28
iwconfig
> 
brandon@Dell-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
brandon@Dell-Linux:~$ 


---

### Post by praseodym on 2011-08-28
> ```
wlan0 IEEE 802.11[COLOR="Red"]g[/COLOR] ESSIDff/any
Mode:Managed Frequency:[COLOR="Red"]2.412[/COLOR] GHz Access Point: Not-Associated
Bit Rate:[COLOR="Red"]300[/COLOR] Mb/s
```

g-Mode with 300 Mb/s? Imho thats impossible, especially on channel 1 in the 2.4 GHz band. Please show:

```
lsusb
lsmod
sudo iwlist scan
```
Normally there are two drivers loaded (ar9170usb and carl9170), blacklist the older one:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf ar9170usb carl9170
sudo modprobe -v carl9170
sudo depmod -a
sudo service network-manager restart
```
Then re-plugin your stick

---

### Post by GnarlyWhales on 2011-08-28
results
> 
brandon@Dell-Linux:~$ lsusb
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 1038:0777 Ideazon, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 03f0:9311 Hewlett-Packard 
Bus 001 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n
Bus 001 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
brandon@Dell-Linux:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
nls_utf8               12493  0 
udf                    83795  1 
crc_itu_t              12627  1 udf
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_hdmi     27535  4 
usblp                  17827  0 
snd_hda_codec_idt      60537  1 
nvidia               9766978  40 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
psmouse                59039  0 
nv_tco                 13331  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           192828  0 
hid_logitech           17421  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
dcdbas                 14054  0 
i2c_nforce2            12906  0 
ff_memless             12945  1 hid_logitech
k8temp                 12872  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  1 hid_logitech
hid                    77084  2 hid_logitech,usbhid
usb_storage            43946  0 
b44                    35301  0 
uas                    17676  0 
ssb                    45942  1 b44
sata_nv                23208  3 
brandon@Dell-Linux:~$ sudo iwlist scan
[sudo] password for brandon: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 7C:4F:B5:B8:27:6C
                    ESSID:"MOTOROLA-3D947"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 7E:4F:B5:B8:27:6D
                    ESSID:"Come over to use "
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: E0:91:F5:6B:F6:76
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

brandon@Dell-Linux:~$ 



the connection i need to connect to is the "Come over to use" its a guest network setup on the motorola one

---

### Post by praseodym on 2011-08-28
Ok, forget the carl9170, its a Broadcom chipset, it only works with ndiswrapper. Show the outputs of:

```
ndiswrapper -l #its a small L
cat /etc/modprobe.d/ndiswrapper.conf
dmesg | grep ndis
```

You may try this driver:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2955302/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
```

---

### Post by GnarlyWhales on 2011-08-28
output
> 
brandon@Dell-Linux:~$ ndiswrapper -l #its a small L
bcmwlhigh5 : driver installed
    device (0846:9011) present
brandon@Dell-Linux:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
brandon@Dell-Linux:~$ dmesg | grep ndis
[    6.703832] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    7.983795] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[    9.838023] usbcore: registered new interface driver ndiswrapper
[  714.863049] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)
[  762.310634] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)
[42028.184533] ndiswrapper: device wlan0 removed
[42034.475885] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
brandon@Dell-Linux:~$ 



---

### Post by praseodym on 2011-08-28
Do I get it right? You want to connect via USB to a Motorola cell phone? Sometimes it doesnt work well with Natty and USB, you may try Bluetooth instead. In the NM applet the connection has to be "Ad-Hoc", if it is not, delete the current profile and setup a new one.

---

### Post by GnarlyWhales on 2011-08-28
note that my connections are showing up in the tray icon for the network manager and it will allow me to click and input the wep 128 bit passphrase but it will not connect,  with the  driver bcmwlhigh5, would installing the 43xx broadcom and removing the current make the difference for it to be able to connect? everything i found initially all pointed to the bcmwlhigh5 from the netgear website and installing it with wine.... ect ect.

---

### Post by GnarlyWhales on 2011-08-28
> **praseodym said:**
> Do I get it right? You want to connect via USB to a Motorola cell phone? Sometimes it doesnt work well with Natty and USB, you may try Bluetooth instead. In the NM applet the connection has to be "Ad-Hoc", if it is not, delete the current profile and setup a new one.
no no no lol its a motorola cable modem with wifi, it has a guest network setup for me

---

### Post by GnarlyWhales on 2011-08-28
okay i found something that said that the wicd network manager would work, and removing the built in network manager.  this had no effect and now i dont have a tray icon but it gives me more options for inputing the wep (as a shared/restricted key). comes up as "bad password"

---

### Post by praseodym on 2011-08-28
No, sticks with Broadcom-chipset only work with ndiswrapper.


You may try the Add-On for Wicd:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
choose wlan0 as interface and wext (not ndiswrapper!) as driver.

The driver I posted the link above was optimized for ndiswrapper, you may try that one. Before, remove the current config:

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
```

---

### Post by GnarlyWhales on 2011-08-28
did all and still nothing. comes up as bad password

---

### Post by praseodym on 2011-08-28
Did you copy/paste the key from Windows with "notepad". Did you "mark all", "copy/paste"? If you did so, you also copy the [Byte Order Mark]("http://en.wikipedia.org/wiki/Byte_order_mark") which leads to wrong keys. Did you try to type in the key manually?

---

### Post by GnarlyWhales on 2011-08-28
its just a shared passphrase

---

### Post by praseodym on 2011-08-28
Did you install 64bit Ubuntu? PLZ show:

```
cat /etc/ndiswrapper/bcmn43xx32/0846:9011.F.conf
```

It should look like this:

```
sys_files|bcmn43xx32.sys 
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
driver_version|,08/26/2009, 5.10.79.30
BusType|15
SlotNumber|01
NetCfgInstanceId|{28022A01-1234-5678-ABCDE-123813291A00}

11HNetworks|1
11NPreamble|-1
Afterburner|0
antdiv|-1
ApCompatMode|0
assoc_recreate|1
AssocRoamPref|0
BadFramePreempt|0
band|0
BandPref|0
BTCoexist|0
ccx_rm|1
ccx_rm_limit|300
Chanspec|13
Chanspec|140
DriverDesc|NDIS Network Adapter
EFCEnable|0
EnableAutoConnect|0
EnableSoftAP|0
frag|2346
FrameBursting|0
HelpText|
IBSSAllowed|1
IBSSGProtection|2
IBSSLink|1
IBSSMode|5
Interference_Mode|-1
Intolerant|0
ledbh0|-1
ledbh1|-1
ledbh2|-1
ledbh3|-1
ledblinkfast|-1
ledblinkmed|-1
ledblinkslow|-1
leddc|0
LockWlSettings|0
LOM|0
Managed|1
mimo_antsel|-1
MixedCell|0
MPC|1
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|2
PwrOut|100
RadioState|0
Rate|0
RateA|0
RoamDelta|3
RoamTrigger|3
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
Service|BCM43xx
ShortGI|-1
SSID|
ssid_auto_promote|0
vlan_mode|-1
WakeUpCapabilities|3
WEP|
WME|-1
WowlKeyRot|1
WZCCoexist|0
```

---

### Post by GnarlyWhales on 2011-08-28
no its 32bit.

> 
brandon@Dell-Linux:~$ cat /etc/ndiswrapper/bcmn43xx32/0846:9011.F.conf
cat: /etc/ndiswrapper/bcmn43xx32/0846:9011.F.conf: No such file or directory
brandon@Dell-Linux:~$ 



not finding the file? how can i patch this up

---

### Post by praseodym on 2011-08-28
PLZ show:
```

cd /etc/ndiswrapper/
ls -l
```

---

### Post by GnarlyWhales on 2011-08-28
i feel like im in an endless loop of problems with this :(
> 
brandon@Dell-Linux:~$ cd /etc/ndiswrapper/
brandon@Dell-Linux:/etc/ndiswrapper$ ls -l
total 0
brandon@Dell-Linux:/etc/ndiswrapper$ 


---

### Post by praseodym on 2011-08-28
Ok, obviously the installation didnt work, this can happen with the GUI. Try it via terminal with the driver I attached:

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
```
Installation:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2955302/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
tar xvf Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz
sudo ndiswrapper -i Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
```
Check:
```
ndiswrapper -l
```
If the driver is shown, load the module:

```
sudo depmod -a
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```
You may re-plug in your stick and check the following:

```
cat /etc/modprobe.d/ndiswrapper.conf
ndiswrapper -l
lsmod
dmesg | grep ndis
iwconfig
sudo iwlist scan
cd /etc/ndiswrapper
ls -l
cat /etc/ndiswrapper/bcmn43xx32/0846:9011.F.conf
```

---

### Post by Ohkie on 2011-09-03
praseodym,

I'm in the exact same situation as the original poster. I've attempted the instructions you provided in post #23 but I am still unable to get a connection. Scan works and see's all the networks it should, but network manager just prompts me for my password constantly, and wcid returns "bad password".

Do you have anything else you can suggest/help with? Are there any useful commands/logs I can post?

Thanks.

---

### Post by praseodym on 2011-09-03
Do you use NM and Wicd in parallel? That doesnt work. Stop the NM and restart Wicd:

```
sudo service network-manager stop
sudo service wicd restart
```
and/or un-check the NM in "Autostart" and re-login. Checks:

```
uname -a
lsusb
lsmod
dmesg | grep ndis
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Ohkie on 2011-09-04
Same error with wicd after killing network-manager and restarting wicd - bad password. 

Should be noted I am trying this using the latest Mythbuntu. I've successfully used the dongle on a Windows XP instance on the same machine, so I'm reasonably confident its not a configuration issue with the router.

Thanks for any assistance (from yourself and anyone else out there!)

(any instances of 'xx' below used to protect the innocent (or guilty! :) )
---------

uname -a:

```
Linux Jome-HTPC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

```

lsusb:

```
...
Bus 002 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n
...
```

lsmod:

```
Module                  Size  Used by
vesafb                 13449  1
nfsd                  252397  13
exportfs               12870  1 nfsd
nfs                   282952  0
lockd                  74292  2 nfsd,nfs
fscache                50364  1 nfs
nfs_acl                12771  2 nfsd,nfs
auth_rpcgss            39173  2 nfsd,nfs
nvidia               7098106  24
sunrpc                199096  14 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
ppdev                  12849  0
psmouse                73312  0
serio_raw              12990  0
joydev                 17322  0
parport_pc             32111  1
ndiswrapper           192828  0
lp                     13349  0
parport                36746  3 ppdev,parport_pc,lp
hid_logitech           17421  0
ff_memless             12945  1 hid_logitech
usbhid                 41704  1 hid_logitech
firewire_ohci          31504  0
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
hid                    77084  2 hid_logitech,usbhid
r8169                  42534  0
pata_jmicron           12651  0

```

dmesg | grep ndis:

```
[   11.395000] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   12.071347] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
[   12.342157] usbcore: registered new interface driver ndiswrapper
[  162.820249] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)
```

iwconfig:

```
...

wlan0     IEEE 802.11g  ESSID:off/any 
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated  
          Bit Rate:300 Mb/s   Tx-Power:32 dBm  
          RTS thr:2347 B   Fragment thr:2346 B  
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo iwlist scan:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID: xxxx
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK         

```

I also notice this when running sudo tail -n100 /var/log,syslog (while using network-manager):

```
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Config: added 'scan_ssid' value '1'
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Config: added 'bssid' value 'xx:xx:xx:xx:xx:xx'
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Config: added 'psk' value '<omitted>'
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> Config: set interface ap_scan to 1
Sep  4 12:31:08 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Sep  4 12:31:13 Jome-HTPC wpa_supplicant[847]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxx' freq=2452 MHz)
Sep  4 12:31:13 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  4 12:31:14 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep  4 12:31:14 Jome-HTPC wpa_supplicant[847]: Associated with xx:xx:xx:xx:xx:xx
Sep  4 12:31:14 Jome-HTPC kernel: [  101.214599] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep  4 12:31:14 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Sep  4 12:31:24 Jome-HTPC wpa_supplicant[847]: Authentication with xx:xx:xx:xx:xx:xx timed out.
Sep  4 12:31:24 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  4-way handshake -> disconnected
Sep  4 12:31:24 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  4 12:31:24 Jome-HTPC wpa_supplicant[847]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Sep  4 12:31:24 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Sep  4 12:31:24 Jome-HTPC kernel: [  111.768010] wlan0: no IPv6 routers present
Sep  4 12:31:29 Jome-HTPC wpa_supplicant[847]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxx' freq=2452 MHz)
Sep  4 12:31:29 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  disconnected -> associating
Sep  4 12:31:39 Jome-HTPC wpa_supplicant[847]: Authentication with xx:xx:xx:xx:xx:xx timed out.
Sep  4 12:31:39 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  4 12:31:39 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  4 12:31:44 Jome-HTPC wpa_supplicant[847]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxx' freq=2452 MHz)
Sep  4 12:31:44 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  4 12:31:44 Jome-HTPC wpa_supplicant[847]: Associated with xx:xx:xx:xx:xx:xx
Sep  4 12:31:44 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep  4 12:31:54 Jome-HTPC wpa_supplicant[847]: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=0
Sep  4 12:31:54 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associated -> disconnected
Sep  4 12:31:54 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  4 12:31:54 Jome-HTPC wpa_supplicant[847]: Authentication with 00:00:00:00:00:00 timed out.
Sep  4 12:31:54 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Sep  4 12:31:54 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  4 12:31:54 Jome-HTPC NetworkManager[1780]: <warn> (wlan0): link timed out.
Sep  4 12:31:59 Jome-HTPC wpa_supplicant[847]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxx' freq=2452 MHz)
Sep  4 12:31:59 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  4 12:31:59 Jome-HTPC kernel: [  146.918247] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)
Sep  4 12:32:08 Jome-HTPC NetworkManager[1780]: <warn> Activation (wlan0/wireless): association took too long.
Sep  4 12:32:08 Jome-HTPC NetworkManager[1780]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Sep  4 12:32:08 Jome-HTPC NetworkManager[1780]: <warn> Activation (wlan0/wireless): asking for new secrets
Sep  4 12:32:08 Jome-HTPC NetworkManager[1780]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <warn> Activation (wlan0) failed for access point (xxxx)
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <info> Marking connection 'Auto xxxx' invalid.
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <warn> Activation (wlan0) failed.
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Sep  4 12:32:11 Jome-HTPC NetworkManager[1780]: <info> (wlan0): deactivating device (reason: 0).

```

---

### Post by Ohkie on 2011-09-04
Anyone got any ideas? I'm tempted to return it and get a different dongle but I'm not convinced its not something wrong with ubuntu/my network?

Thanks!

---

### Post by Ohkie on 2011-09-06
Well I'm making progress by myself. Reinstalled Mythbuntu and updated all the drivers, and changed my AP to use WEP with a statically defined IP address.

I now appear to be able to make a somewhat-complete connection, but I think it is failing when it tries to negotiate the IP address. I'm using network manager still as wicd appeared to be a step backwards. I'm happy to try again with someones advice, however.

Hopefully someone with more insight can spot something from the log below.

As per usual, any assistance is greatly appreciated!

Thanks.

```
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0/wireless): connection 'Auto WLAN2' has security, and secrets exist.  No new secrets needed.
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'ssid' value 'WLAN2'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'scan_ssid' value '1'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'key_mgmt' value 'NONE'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'auth_alg' value 'OPEN'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'wep_key0' value '<omitted>'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: added 'wep_tx_keyidx' value '0'
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> Config: set interface ap_scan to 1
Sep  7 00:04:04 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Sep  7 00:04:09 Jome-HTPC wpa_supplicant[793]: Trying to associate with 6a:44:52:80:ae:47 (SSID='WLAN2' freq=2452 MHz)
Sep  7 00:04:09 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 00:04:19 Jome-HTPC wpa_supplicant[793]: Authentication with 6a:44:52:80:ae:47 timed out.
Sep  7 00:04:19 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Sep  7 00:04:19 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 00:04:25 Jome-HTPC wpa_supplicant[793]: Trying to associate with 6a:44:52:80:ae:47 (SSID='WLAN2' freq=2452 MHz)
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep  7 00:04:25 Jome-HTPC wpa_supplicant[793]: Associated with 6a:44:52:80:ae:47
Sep  7 00:04:25 Jome-HTPC wpa_supplicant[793]: CTRL-EVENT-CONNECTED - Connection to 6a:44:52:80:ae:47 completed (auth) [id=0 id_str=]
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  associated -> completed
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'WLAN2'.
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Scheduling stage 5
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Done scheduling stage 5
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  7 00:04:25 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep  7 00:04:25 Jome-HTPC kernel: [   37.796327] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Sep  7 00:04:26 Jome-HTPC NetworkManager[746]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Sep  7 00:04:26 Jome-HTPC NetworkManager[746]: <info> Policy set 'Auto WLAN2' (wlan0) as default for IPv4 routing and DNS.
Sep  7 00:04:26 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) successful, device activated.
Sep  7 00:04:26 Jome-HTPC NetworkManager[746]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  7 00:04:27 Jome-HTPC ntpd[1057]: ntpd exiting on signal 15
Sep  7 00:04:31 Jome-HTPC ntpd_intres[1063]: parent died before we finished, exiting
Sep  7 00:04:35 Jome-HTPC wpa_supplicant[793]: CTRL-EVENT-DISCONNECTED bssid=6a:44:52:80:ae:47 reason=0
Sep  7 00:04:35 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Sep  7 00:04:35 Jome-HTPC NetworkManager[746]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep  7 00:04:35 Jome-HTPC kernel: [   47.952009] wlan0: no IPv6 routers present

```

---

