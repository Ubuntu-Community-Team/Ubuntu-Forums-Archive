---
title: "Asus n10 wireless usb adapter on 10.04 LTS (Lucid Lynx)"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by burnfirewalls on 2011-07-26
Hello,

I recently purchased an Asus n10 wireless usb adapter to use with my media server, running Ubuntu 10.04 LTS (Lucid Lynx).  After spending several hours today with many of the threads (especially [this one]("http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13") about the Asus n13) it seems that I've run out of ideas.

My network is running a hidden (non-broadcast) SSID ("Potato") with wpa2 personal encryption.

Here is the relevant information from lsusb:
```
Bus 001 Device 003: ID 0b05:1786 ASUSTek Computer Inc.
```Iwconfig follows.  The rest of the values, like link quality & etc, are all zero:
```
wlan0   802.11b/g  ESSID:"Potato"
                      Mode: Managed  Access Point: Not-Associated  Bit Rate: 0kb/s

```And the kicker is that the interface doesn't seem to be available, despite the above reports.  ifconfig wlan0 up produces:
```
SIOCSIFFLAGS: Resource temporarily unavailable
```I've been banging my head against this for the better part of today, so any help is appreciated!

---

### Post by wildmanne39 on 2011-07-26
Hi, start with these commands in a terminal please.
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by burnfirewalls on 2011-07-26
Here's the output of the commands:

```
greg@fluffy-ubuntu:~$ sudo lshw -C network
[sudo] password for greg: 
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:18:f3:4f:60:2a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fe9fc000-fe9fffff ioport:a800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:04:04.0
       logical name: eth1
       version: 14
       serial: 00:18:f3:4f:29:5e
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:19 memory:feaf4000-feaf7fff ioport:b800(size=256) memory:feac0000-feadffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: bc:ae:c5:7f:b0:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

greg@fluffy-ubuntu:~$ lspci -nn | grep 0280
greg@fluffy-ubuntu:~$ 


greg@fluffy-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g  ESSID:"GSMusic"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

greg@fluffy-ubuntu:~$ 

greg@fluffy-ubuntu:~$ rfkill list all
greg@fluffy-ubuntu:~$ 

greg@fluffy-ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
isofs                  29250  1 
vfat                    8933  1 
fat                    47767  1 vfat
udf                    78785  0 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_analog    58598  1 
usbhid                 36110  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_intel          22069  1 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  15 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24375  0 
soundcore               6620  1 snd
nvidia               9961216  38 
vga16fb                11385  1 
lp                      7028  0 
hid                    67288  1 usbhid
r8192s_usb            346908  0 
asus_atk0110            9017  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
vgastate                8961  1 vga16fb
agpgart                31724  2 intel_agp,nvidia
parport                32635  2 ppdev,lp
usb_storage            39841  3 
floppy                 53016  0 
ohci1394               26950  0 
skge                   36428  0 
ieee1394               81181  1 ohci1394
sky2                   40807  0 
greg@fluffy-ubuntu:~$ 
```

---

### Post by chili555 on 2011-07-26
The Wild Man now wants to see:```
dmesg | grep 819
modinfo r8192s_usb | grep -e firm -e version
```He suspects that your wireless card wants but lacks firmware.

---

### Post by burnfirewalls on 2011-07-26
Based on the error messages, I think that the Wild Man is on to something!

```
greg@fluffy-ubuntu:~$ dmesg | grep 819
[   11.926455] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   11.938542] Linux kernel driver for RTL8192 based WLAN cards
[   11.978193] type=1505 audit(1311651434.981:6):  operation="profile_replace" pid=602 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.137976] usbcore: registered new interface driver rtl819xU
[   16.883260] rtl819xU: --->FirmwareDownload92S()
[   16.883267] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   16.931262] rtl819xU:request firmware fail!
[   16.931587] rtl819xU:Firmware Download Fail!!a
[   16.938765] rtl819xU: --->FirmwareDownload92S()
[   16.938772] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   16.942026] rtl819xU:request firmware fail!
[   16.942333] rtl819xU:Firmware Download Fail!!a
[   16.942338] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   17.013023] rtl819xU: --->FirmwareDownload92S()
[   17.013032] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   17.014766] rtl819xU:request firmware fail!
[   17.015027] rtl819xU:Firmware Download Fail!!a
[   17.024775] rtl819xU: --->FirmwareDownload92S()
[   17.024783] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   17.032940] rtl819xU:request firmware fail!
[   17.033180] rtl819xU:Firmware Download Fail!!a
[   17.033184] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  343.667402] rtl819xU: --->FirmwareDownload92S()
[  343.667411] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  343.669381] rtl819xU:request firmware fail!
[  343.669534] rtl819xU:Firmware Download Fail!!a
[  343.677154] rtl819xU: --->FirmwareDownload92S()
[  343.677165] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  343.682682] rtl819xU:request firmware fail!
[  343.682991] rtl819xU:Firmware Download Fail!!a
[  343.682996] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  750.539119] rtl819xU: --->FirmwareDownload92S()
[  750.539127] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  750.541238] rtl819xU:request firmware fail!
[  750.541496] rtl819xU:Firmware Download Fail!!a
[  750.549867] rtl819xU: --->FirmwareDownload92S()
[  750.549877] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[  750.553929] rtl819xU:request firmware fail!
[  750.554125] rtl819xU:Firmware Download Fail!!a
[  750.554130] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 2066.988563] rtl819xU: --->FirmwareDownload92S()
[ 2066.988570] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2066.990410] rtl819xU:request firmware fail!
[ 2066.990568] rtl819xU:Firmware Download Fail!!a
[ 2066.998564] rtl819xU: --->FirmwareDownload92S()
[ 2066.998571] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 2067.005043] rtl819xU:request firmware fail!
[ 2067.005202] rtl819xU:Firmware Download Fail!!a
[ 2067.005207] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
greg@fluffy-ubuntu:~$ modinfo r8192s_usb | grep -e firm -e version
version:        V 1.1
srcversion:     F23AAB98A4D0682466A581F
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
greg@fluffy-ubuntu:~$ 
```

---

### Post by chili555 on 2011-07-26
This is wacky! modinfo doesn't mention firmware, but the driver sure wants it. Let's see if rtl8192sfw.bin is on your system.```
sudo updatedb
```This will take a few moments, please be patient.```
locate rtl8192sfw.bin
```Is it in /lib/firmware/RTL8192S[COLOR="Red"]E[/COLOR]? Wherever you find it, copy it over to the location your driver expects to find it:```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192S[COLOR="Red"]E[/COLOR]/rtl8192sfw.bin /lib/firmware/RTL8192SU
```Of course, if you find it elsewhere, substitute that location. Post back if you get stuck. Reboot and let us have your report.

---

### Post by burnfirewalls on 2011-07-26
Your fix worked to get the firmware up and running - my card is able to view networks and
```
ifconfig wlan0 up
```
doesn't come back with that damnable error message.

However, I'm still not cooking on my wifi network - when I try to connect, I keep getting prompted for the wifi passphrase, despite double and triple-checking my typing and the passphrase type.  Is it possible that there is a secondary issue with the encryption handler?

---

### Post by chili555 on 2011-07-26
Certainly. It's also possible your card wants a different version of rtl8192sfw.bin. Please see here: [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/595455)

Please do:```
sudo rm /lib/firmware/RTL8192SU/rtl8192sfw.bin
cd /lib/firmware/RTL8192SU
sudo wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin
```Then unplug the adapter and plug it back in again. Let us have another report.

---

### Post by wildmanne39 on 2011-07-26
I am just going to watch the Doctor work his magic.

---

### Post by burnfirewalls on 2011-07-26
I don't mean to be THAT guy, but is there a way for me to transfer that file from my internet-connected windows box to my ubuntu box via sneakernet?  My ubuntu box is on a different floor of my house than my wired router.  If it's unavoidable, I can haul it down there.  Not sure if wget also does some stuff beyond copying...

---

### Post by chili555 on 2011-07-26
You are not that guy at all. I am assuming 'that guy' is a pain. No worries at all. Just get the file I referred to on any computer, transfer it to a USB key and then to your Ubuntu desktop. Then:```
sudo cp Desktop/rtl8192sfw.bin /lib/firmware/RTL8192SU
```wget just goes out to the specified location and gets the file. You should be able to click the link on any other computer and download it.

---

### Post by burnfirewalls on 2011-07-26
Heh, yeah, I meant the kind of guy who won't actually follow the instructions to fix an issue.  Your understanding is appreciated!

I copied that file over to a thumb drive, did the rm and copied it over.  I'm having the same issue where the passphrase won't take.

The network 'Potato' is configured to use WPA2 Personal/TKIP at the moment, if that matters.

---

### Post by chili555 on 2011-07-26
> The network 'Potato' is configured to use WPA2 Personal/TKIP at the moment, if that matters.Not WPA and WPA2 mixed, I hope. Let's see:```
sudo iwlist wlan0 scan
dmesg | grep 819
```Thanks.

---

### Post by burnfirewalls on 2011-07-26
Here's the output.  I truncated the huge dmesg output to what you see here, as they were all duplicates.

```
greg@fluffy-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:8E:20:07
                    ESSID:"GSMusic"
                    Protocol:IEEE802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=69/100  Signal level=-65 dBm  Noise level=-104 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 93ms ago
          Cell 02 - Address: 0C:D5:02:8E:5B:CC
                    ESSID:"11FX02141354"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-65 dBm  Noise level=-102 dBm
                    Extra: Last beacon: 126ms ago

greg@fluffy-ubuntu:~$ 

[ 8199.596022] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 8199.596028] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 8199.596036] ===>ieee80211_associate_procedure_wq(), chan:6
[ 8199.605649] Association response status code 0xc
[ 8199.633615] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 8199.633616] 
[ 8199.647158] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 8199.647162] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 8199.647167] ===>ieee80211_associate_procedure_wq(), chan:6
[ 8199.653282] Association response status code 0xc
[ 8199.684499] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 8199.684501] 
[ 8199.698040] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 8199.698044] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 8199.698051] ===>ieee80211_associate_procedure_wq(), chan:6
[ 8199.735627] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 8199.735629] 
[ 8199.749168] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 8199.749172] =================>ieee80211_authentication_req():auth->algorithm is 0
greg@fluffy-ubuntu:~$ 


```

---

### Post by chili555 on 2011-07-26
> Is it possible that there is a secondary issue with the encryption handler?I've been resisting this like the Black Plague, but I guess I'm trapped. Have you tried it without a hidden ESSID? Have you tried the live CD for the later version 11.04? I have to go hang my head now...

---

### Post by burnfirewalls on 2011-07-26
Un-hiding the ESSID of the Potato network did the trick!  I can get to the Google homepage!  Do you know the cause of the hidden network problem manifesting as an ecryption issue?

---

### Post by chili555 on 2011-07-26
> **burnfirewalls said:**
> Un-hiding the ESSID of the Potato network did the trick!  I can get to the Google homepage!  Do you know the cause of the hidden network problem manifesting as an ecryption issue?No, I do not. I have seen a few bug reports against Network Manager and they seem to reply that you don't need a hidden network for security, you need WPA2 and a strong password. I am sure that wpa_supplicant is part of the issue and everyone blames the poor hardware and driver. NM is not yet perfect. I'm sorry, I wish I had a better solution.

In any case, I'm glad you're connected.

---

### Post by burnfirewalls on 2011-07-26
Just curious as to the cause.  Security through obscurity isn't the way to go anyhow.

But thanks a bunch for your help!  I'm very glad that we were able to get this working!

---

### Post by wildmanne39 on 2011-07-26
Hi, I am glad you got it working, thank you chili555.

---

### Post by robdashu on 2012-02-01
Bought ASUS N10 USB wlan interface.

Trying to follow instructions!?!

First make went OK.

Make install produced these errors:

root@robsdell:/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8180_93cx6.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_wx.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192S_phy.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192S_rtl6052.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192S_rtl8225.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r819xU_cmdpkt.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_dm.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192SU_HWImg.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192S_firmware.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192S_Efuse.o
  CC [M]  /home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12317: error: ‘struct net_device’ has no member named ‘open’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12318: error: ‘struct net_device’ has no member named ‘stop’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12319: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12320: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12321: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12322: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12323: error: ‘struct net_device’ has no member named ‘get_stats’
/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.c:12324: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2
root@robsdell:/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009# make install
make[1]: Entering directory `/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u'
make -C /lib/modules/2.6.32-21-generic/build M=/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009 CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
install -p -m 644 r8192s_usb.ko  /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install: cannot stat `r8192s_usb.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009/HAL/rtl8192u'
make: *** [install] Error 2
root@robsdell:/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@robsdell:/home/rob/rtl8192su_linux_2.4_2.6.0003.1019.2009# 

Kinda stuck, as I'm trying to avoid the hassle of moving the machine to hard-wired connection.  Running split system windows XP Pro and ubuntu 10.04.  Wireless works fine under windows.

Can't someone create a unix installer for such installs?
Or are there too many variables from ones install to the next?

I've been messing for a couple of days, not getting anywhere...

HELP!

---

### Post by robdashu on 2012-02-01
By the way, the 10.04 dist I got has a pretty shabby packages list. 

NO "ndisxxx" anything, or I'd try to use the Windows driver.

---

### Post by chili555 on 2012-02-01
> Can't someone create a unix installer for such installs?That's exactly what you have!> Or are there too many variables from ones install to the next?There are quite a few kernel versions, gcc versions, etc. out there. I notice the driver version you have is late 2009. Is that the latest you could find? It is probably now called 8712u.

Are you aware that the latest Ubuntu version 11.10 supports your device out of the box?> By the way, the 10.04 dist I got has a pretty shabby packages list.

NO "ndisxxx" anything, or I'd try to use the Windows driver. I think you've missed something. I'm fairly confident ndiswrapper is installed by default or at least included on the install CD.

---

### Post by robdashu on 2012-02-01
> **chili555 said:**
> That's exactly what you have!There are quite a few kernel versions, gcc versions, etc. out there. I notice the driver version you have is late 2009. Is that the latest you could find? It is probably now called 8712u.

Are you aware that the latest Ubuntu version 11.10 supports your device out of the box?I think you've missed something. I'm fairly confident ndiswrapper is installed by default or at least included on the install CD.

Is moving to 11.1from 10.4 usually smooth?

Everytime I mess around I get in trouble.  I know just enough to be a danger to my system!

Can I download an Iso image using windows, then installfrom that?

---

### Post by robdashu on 2012-02-01
Ndiswrapper, ndisgtk, etc. there, bur Synaptic PM didn't know. Had to use gdeb to install after searching.  (Seems there's always these twists and turns -- probably because I keep buying cheap refurbish PCs.  I'm trying to set up a Dell Optiplex gx620 pentiun dual core;  I'm really moving up now :)

Told ubuntu use windows driver thru new menu pick.  Still no wlan0 per iwconfig?
Still no connection.
@
Ubuntu says windows driver installed;i. wconfig. Sees no wlan0.

---

### Post by chili555 on 2012-02-01
Where did you get the Windows driver? The XP .inf file, I hope. What does this tell us?```
dmesg | grep ndis
```

---

### Post by robdashu on 2012-02-02
Here's what it tells me:

----------
rob@robsdell:~$ dmesg | grep ndis
[   18.846032] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   19.783208] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[   19.783304] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
[   19.784109] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'
[   19.784259] usbcore: registered new interface driver ndiswrapper
rob@robsdell:~$ 

--------------------

Apparently I selected the wrong driver? When I look at the windows drivers, I choose XP drivers, as I'm running Windows Xp in my Windows partition.  Seems like the driver s/b/ 32-bit...

---

### Post by chili555 on 2012-02-02
> Seems like the driver s/b/ 32-bit...Yes, indeed. Do you have it on hand? Can you change it?

---

### Post by robdashu on 2012-02-02
It seems that, regardless of the windows driver I choose, it picks the same .inf file;  I tried selecting other windows drivers, and they all seem to point at the same .inf file.

ubuntu then tells me the driver is already installed...

---

### Post by chili555 on 2012-02-02
I'd suggest you read the various .inf files with a text editor and see which ones are x86 and which are 64-bit. Copy the .inf that is x86 and, if there is one, the similarly named .sys file to a folder on your desktop. Next **erase** the old incorrect driver:```
sudo ndiswrapper -**e** net8192su
```Then I'd look around in /etc/ndiswrapper for any .conf files and delete them. Then I'd reboot and install the drivers from your desktop:```
sudo ndiswrapper -i Desktop/driverfolder/8192.inf  <--or whatever the 32-bit is named
```Try it and post back your result.

---

### Post by robdashu on 2012-02-02
Chili:

Now my CD drive is not being recognized by windows or ubuntu - that's where the ASUS drivers are.

Gotta get it working.  I'll be back.

and thanx for you help.

rob

---

### Post by robdashu on 2012-02-02
OK.  Done as you described.  No error messages.

Also, no response or acknowledgement of wireless network.  Restarted after changes, still no go.

---

