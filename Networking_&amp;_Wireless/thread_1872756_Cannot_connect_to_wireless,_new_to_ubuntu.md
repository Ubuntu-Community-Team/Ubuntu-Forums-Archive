---
title: "Cannot connect to wireless, new to ubuntu"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by Pwens on 2011-10-31
Hi,

I recently fixed an old laptop (all i really did was take out the ram and put it back in).
So i decided to put ubuntu on it because it still had vista. So i did a clean install but now i cannot connect to my wireless network.

The laptop is a couple of years old, it is a HP Pavilion dv6350eu, after looking on the internet, they also have problems with the network card
And i am using ubuntu 11.10 32-bit.
I live in the middle of nowhere, therefore my wireless network is totally unprotected.

It will not find any wireless networks. At a certain point it even said wireless firmware missing (or something like this). I can connect to the internet using a wired connection.
When i first went online, it download some additional drivers, but before this was completely finished the computer froze so i had to reboot. After rebooting, the only new drivers were for the video card.

I already tried to install some drivers myself (the compat-wireless-3 packet?), but i never used linux before and dont know whether i succeeded or not. 

I also tried to figure out if my hardware was functioning, but none of the data the terminal gave was helpful.

Also, my touch pad seems to freeze at random moments untill i reboot, so i have to use a usb mouse which works perfectly.


Please tell me what i am doing wrong, or just tell me what to do next.

Tnx

---

### Post by praseodym on 2011-10-31
Hi,

please show the following terminal outputs:

```
uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsusb
lsmod
rfkill list
sudo iwlist scan
```

---

### Post by Pwens on 2012-07-08
so it has been a while since i last tried to fix my laptop
I since upgraded to ubuntu 12.04 and learned the basics of linux (read can open terminal and input commands)

here is what you asked for

```
pieter@PC-Pieter:~$ uname -a
Linux PC-Pieter 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
pieter@PC-Pieter:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
pieter@PC-Pieter:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

pieter@PC-Pieter:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
pieter@PC-Pieter:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211
vesafb                 13516  1 
joydev                 17393  0 
nvidia               9874792  43 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
snd_timer              28931  2 snd_pcm,snd_seq
uvcvideo               67203  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
bluetooth             158438  10 bnep,rfcomm
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
videodev               86588  1 uvcvideo
r592                   17808  0 
psmouse                87213  0 
memstick               15857  1 r592
serio_raw              13027  0 
snd                    62064  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
binfmt_misc            17292  1 
soundcore              14635  1 snd
nv_tco                 13399  0 
k8temp                 12905  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
sdhci_pci              18324  0 
crc_itu_t              12627  1 firewire_core
sdhci                  28241  1 sdhci_pci
forcedeth              58096  0 
pata_amd               13750  0 
sata_nv                23360  2 
pieter@PC-Pieter:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
pieter@PC-Pieter:~$ sudo iwlist scan
[sudo] password for pieter: 
lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Device or resource busy

eth0      Interface doesn't support scanning.
```so i also got a wifi dongle from dealextreme, driver did not work of course so i tried to install one myself, several trial and errors and different drivers and forums later i am able to see the surrounding wifi's and was able to connect once, but not anymore

If anyone can help me, that would be great

---

### Post by praseodym on 2012-07-08
Which channel does the router send on? Try a fixed channel from 1-11, encryption mode pure WPA2-AES (CCMP), if possible.

Check:

```
iwlist chan
dmesg | egrep 'rtl8|r8|wlan'
cat /etc/udev/rules.d/70-persistent-net.rules
```
You can also try to uninstall the _package_ **resolvconf** and reboot.

---

### Post by Pwens on 2012-07-08
wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
eth0      no frequency information.

pieter@PC-Pieter:~$ dmesg | egrep 'rtl8|r8|wlan'
[   21.685390] r852 0000:07:05.3: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   21.685399] r852 0000:07:05.3: setting latency timer to 64
[   21.703916] r852: Non dma capable device detected, dma disabled
[   21.703936] r852: driver loaded successfully
[  342.083880] rtl8192cu: MAC address: e8:4e:06:05:38:bd
[  342.083898] rtl8192cu: Board Type 0
[  342.143717] usbcore: registered new interface driver rtl8192cu
[  342.216058] Error: Driver 'rtl8192cu' is already registered, aborting...
[  342.265545] udevd[530]: renamed network interface wlan0 to wlan1
[  342.296143] rtl8192cu: MAC auto ON okay!
[  342.343391] rtl8192cu: Tx queue select: 0x05
[  342.344537] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[  342.791064] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  342.791712] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  345.582614] wlan1: authenticate with 94:44:52:22:da:46 (try 1)
[  345.591135] wlan1: authenticated
[  345.614368] wlan1: associate with 94:44:52:22:da:46 (try 1)
[  345.628536] wlan1: RX AssocResp from 94:44:52:22:da:46 (capab=0x411 status=0 aid=2)
[  345.628542] wlan1: associated
[  345.642530] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  355.776068] wlan1: no IPv6 routers present
[  382.986755] wlan1: deauthenticating from 94:44:52:22:da:46 by local choice (reason=3)
pieter@PC-Pieter:~$ cat /etc/udev/rules.d/70-persist.net-rules
cat: /etc/udev/rules.d/70-persist.net-rules: No such file or directory

yes i am using a fixed channel

---

