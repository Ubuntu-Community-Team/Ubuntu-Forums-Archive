---
title: "RTL 8185 WIFI card stopped working"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by svebor on 2012-07-24
Hi guys, my wifi card, that was always working flawlessly out of the box, just stopped working.

The only thing I remember out of ordinary, was I updated the MB bios, but I'm not sure that it happened on the following Ubuntu boot.. might have happened a few days later... 

It also doesn't work when I boot openSuse or live Ubuntu, but it does work in Windows 7.. so the card works...

Here are a few things I tried, can't figure out what's wrong:

```
nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        14:DA:E9:B5:7C:05

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        00:11:3B:0F:8A:2C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


iwconfig:
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


sudo iwlist wlan0 scan
wlan0     No scan results


sudo ifconfig wlan0 down
sudo rmmod rtl8180
sudo rfkill block all
sudo rfkill unblock all
sudo modprobe rtl8180
sudo /sbin/ifconfig wlan0 up

```

.. the card still doesn't work... 

I'd appreciate any suggestions or help, tnx!

---

### Post by NikTh on 2012-07-24
Hi , 
lets do some diagnostics. 
```
dmesg | grep -e wl -e work -e NET -e rtl
sudo lshw -C network 
lspci -nnk | grep -iA2 net
lsmod
```Thanks

---

### Post by svebor on 2012-07-24
Hi NikTh, thanks for your help.

Here's the output:

```
sveb@Mukotar:~$ dmesg | grep -e wl -e work -e NET -e rtl
[    0.000018] Security Framework initialized
[    0.496673] NET: Registered protocol family 16
[    0.667853] NET: Registered protocol family 2
[    0.669803] NET: Registered protocol family 1
[    1.371608] NET: Registered protocol family 10
[    1.371833] NET: Registered protocol family 17
[   16.456434] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.542838] type=1400 audit(1343160438.663:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   16.562591] rtl8180 0000:04:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.683439] ieee80211 phy0: hwaddr 00113b0f8a2c, RTL8185vD + rtl8225z2
[   19.049272] NET: Registered protocol family 31
[   19.075516] type=1400 audit(1343160441.199:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1086 comm="apparmor_parser"
[   23.008802] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.009061] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.200356] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.200605] ADDRCONF(NETDEV_UP): eth0: link is not ready
sveb@Mukotar:~$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 20
       serial: 00:11:3b:0f:8a:2c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=3.2.0-27-generic firmware=N/A latency=32 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:d000(size=256) memory:f7d00000-f7d001ff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:da:e9:b5:7c:05
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:b000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
sveb@Mukotar:~$ lspci -nnk | grep -iA2 net
04:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8225]
	Kernel driver in use: rtl8180
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
	Kernel driver in use: r8169
	
sveb@Mukotar:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
vesafb                 13844  1 
video                  19596  0 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  1 
eeepc_wmi              13109  0 
asus_wmi               24456  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
snd_hda_codec_realtek   223962  1 
joydev                 17693  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8180                40710  0 
snd_seq_midi           13324  0 
mac80211              506816  1 rtl8180
snd_rawmidi            30748  1 snd_seq_midi
eeprom_93cx6           12725  1 rtl8180
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              205544  2 rtl8180,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13253  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                3263886  99 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87692  0 
serio_raw              13211  0 
wmi                    19256  1 asus_wmi
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
usbhid                 47199  1 hid_logitech
hid                    99559  2 hid_logitech,usbhid
usb_storage            49198  1 
pata_via               13701  0 
r8169                  62099  0 

```

---

### Post by NikTh on 2012-07-25
Hi , 
i see that now you have 2 ethernet controlers.. Kernel now recognizes wireless network and wired network as ethernet both.
hmmm.. maybe an expert must take care your case. (and i am not expert) 

Post the results of these commands 
```
cat /etc/network/interfaces 
rfkill list all 
cat /etc/NetworkManager/NetworkManager.conf
```Try 1-2 things 
Check the bios and see if something to do with your wireless card is disabled .
Check your Function Keys (Fn+F2,F3 etc) ,maybe you must activate your wireless from there.
Try to add manualy your wireless connection to Network manager.. 
```
gksudo nm-connection-editor
``` click wireless click add and fill the SSID and password there. 
Reboot (without ethernet cable) to see if something happen.

Thanks

---

### Post by svebor on 2012-07-25
Hi, thank you for your help and patience... I finally had the time to try it out.. so, here's the output... 

```
cat /etc/network/interfaces 
auto lo
iface lo inet loopback

sveb@Mukotar:~$ rfkill list all 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
sveb@Mukotar:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```

Unfortunately, I found nothing that would remotely reference my card in bios. 
It can't be turned off either by fn+xx keys because it's a custom built desktop machine, so the keyboard doesn't have them... 

I tried playing around with manually editing the settings and that didn't work... 

The weird thing is that the card works in Win7 as if nothing changed... 

I even tried putting it into another PCI slot, Win detected it and reused the existing driver, no change in Linux.. Really frustrating.. :-(

---

### Post by svebor on 2012-07-26
Bump! I'll probably buy a new card since noone seems to have any idea what to do.. 

This one has had a good run.. Has been in my various desktop computers around 6 years now... :|

---

### Post by redbob on 2012-08-06
Svebor:

I must say that same thing happened to my computer. Suddenly my wireless card stopped working. Same configuration, same specs. see my post:
> [    0.004041] Security Framework initialized
[    0.145834] NET: Registered protocol family 16
[    0.237829] NET: Registered protocol family 2
[    0.242219] NET: Registered protocol family 1
[    0.717944] NET: Registered protocol family 10
[    0.718570] NET: Registered protocol family 17
[   16.239121] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.828799] type=1400 audit(1344306999.587:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 comm="apparmor_parser"
[   17.056315] rtl8180 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   17.452126] ieee80211 phy0: hwaddr 00116b64f08f, RTL8185vD + rtl8225z2
[   19.783856] NET: Registered protocol family 31
[   20.036463] type=1400 audit(1344307002.795:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1006 comm="apparmor_parser"
[  165.984392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  225.688378] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  229.812392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  233.884039] wlan0: authenticate with b0:48:7a:c6:6e:0a (try 1)
[  234.084036] wlan0: authenticate with b0:48:7a:c6:6e:0a (try 2)
[  234.284066] wlan0: authenticate with b0:48:7a:c6:6e:0a (try 3)
[  234.484054] wlan0: authentication with b0:48:7a:c6:6e:0a timed out
[  245.544039] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 1/3)
[  245.744040] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 2/3)
[  245.944053] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 3/3)
[  246.144733] wlan0: direct probe to b0:48:7a:c6:6e:0a timed out
[  257.204040] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 1/3)
[  257.404028] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 2/3)
[  257.604042] wlan0: direct probe to b0:48:7a:c6:6e:0a (try 3/3)
[  257.804038] wlan0: direct probe to b0:48:7a:c6:6e:0a timed out
[  271.468427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  290.855048] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  291.055574] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  291.389437] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  295.163124] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


I think it's due to some ubuntu update that disabled wireless card...

---

