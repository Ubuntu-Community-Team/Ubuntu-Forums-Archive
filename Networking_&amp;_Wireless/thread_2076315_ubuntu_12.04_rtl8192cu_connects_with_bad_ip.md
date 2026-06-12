---
title: "ubuntu 12.04 rtl8192cu connects with bad ip"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by dwb814 on 2012-10-25
Hi,
I really need some help! 

I just installed a rtl8192cu usb donegal. I setup the information needed and it says it's connected but the ip address isn't correct. Here's the story, I did a fresh install of Ubuntu 12.04 32bit on a hard drive. I had the donegal already in the usb port. When Ubuntu booted, I checked the information on the wireless and everything was good including the ip, subnets etc. But I kept getting the password box. 

So, I decided to do the updates, after the updates were done, the donegal connected to my router, but with a bad ip address, the ip address should be 192.168.1.xx but it keeps showing up as 10.42.0.1

Here are the tests I ran:

sudo /etc/init.d/networking restart
```

$ sudo /etc/init.d/networking restart
[sudo] password for dan: 
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```sudo lspci
```

dan@dan-P23G:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

```sudo lspci | grep -i wireless
```

dan@dan-P23G:~$ sudo lspci | grep -i wireless
dan@dan-P23G:~$ 

```cat /etc/lsb-release; uname -a
```

dan@dan-P23G:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux dan-P23G 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux
dan@dan-P23G:~$ 

```lspci -nnk | grep -iA2 net
```

dan@dan-P23G:~$ lspci -nnk | grep -iA2 net
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
    Subsystem: Elitegroup Computer Systems Device [1019:0102]
    Kernel driver in use: via-rhine

```lsusb
```

dan@dan-P23G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN

```iwconfig
```

dan@dan-P23G:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"godshouse"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 62:59:19:E2:15:80   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions. 

```rfkill list all
```

dan@dan-P23G:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```lsmod
```
 
dan@dan-P23G:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12663  1 
xt_state               12514  1 
ipt_REJECT             12512  2 
xt_tcpudp              12531  4 
iptable_filter         12706  1 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  1 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  4 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
arc4                   12473  2 
snd_via82xx            24718  2 
gameport               15060  1 snd_via82xx
snd_ac97_codec        106082  1 snd_via82xx
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         14108  2 snd_via82xx,snd_pcm
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
rtl8192cu              97722  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                737891  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  2 rtlwifi,mac80211
psmouse                86486  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65344  1 radeon
serio_raw              13027  0 
drm_kms_helper         45466  1 radeon
snd                    62064  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197599  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
i2c_viapro             12969  0 
i2c_algo_bit           13199  1 radeon
shpchp                 32325  0 
bnep                   17830  2 
bluetooth             158438  7 bnep
ppdev                  12849  0 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
via_rhine              27413  0 
sata_via               13495  0 
pata_via               13428  2 
floppy                 60310  0 

```nm-tool
```

dan@dan-P23G:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [godshouse] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           no
  HW Address:        00:0B:81:84:3F:5A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *godshouse:      Ad-Hoc, 0A:52:77:08:AE:02, Freq 2412 MHz, Rate 0 Mb/s, Strength 100 WEP

  IPv4 Settings:
    Address:         10.42.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:19:21:21:65:BB

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75

```lsmod | grep rtl
```

dan@dan-P23G:~$ lsmod | grep rtl
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  2 rtlwifi,mac80211
dan@dan-P23G:~$ 

```dmesg | egrep 'rtl|firm|wpa|etork|wlan0'
```

dan@dan-P23G:~$ dmesg | egrep 'rtl|firm|wpa|etork|wlan0'
[   13.645946] rtl8192cu: MAC address: 00:0b:81:84:3f:5a
[   13.645956] rtl8192cu: Board Type 0
[   14.592444] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   14.685389] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.694102] usbcore: registered new interface driver rtl8192cu
[   14.930024] rtl8192cu: MAC auto ON okay!
[   14.971536] rtl8192cu: Tx queue select: 0x05
[   14.972332] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   15.941981] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.948884] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.087258] rtl8192cu: MAC auto ON okay!
[   16.129658] rtl8192cu: Tx queue select: 0x05
[   16.130421] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
[   24.820083] wlan0: Creating new IBSS network, BSSID 0a:52:77:08:ae:02
[   35.264036] wlan0: no IPv6 routers present
[  356.064022] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  399.839963] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  441.509164] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  473.056062] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  504.032028] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  535.008035] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  566.112094] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  601.056080] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  662.112057] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  708.064036] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)

```


Any and all help would be greatly appreciated.
Thank you.

---

### Post by ahallubuntu on 2012-10-25
Download the latest driver from Realtek from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Open a terminal, then assuming you downloaded it to the Downloads directory in your home directory:

```
cd ~/Downloads
unzip (ZIPFILENAME)
cd (NEWDIRECTORY_CREATED)
chmod 755 ./install.sh
sudo ./install.sh
```


You may need to blacklist your existing driver by adding these three items to the end of the file /etc/modprobe.d/blacklist.conf :

```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

and add the name of the new module "8192cu" to the end of the file /etc/modules so it will be automatically loaded at each boot.

You may need to re-build this each time your kernel is updated by Ubuntu.

---

### Post by dwb814 on 2012-10-25
Thanks for the response. I got an error in the install

```

 chmod 755 ./install.sh
dan@dan-P23G:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405 (2)$ sudo ./install.sh
[sudo] password for dan: 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405.tar.gz
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/autoconf_rtl8712_usb_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/clean
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl8712_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/cmd/rtl871x_cmd.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/config
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/crypto/rtl871x_security.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/debug/rtl871x_debug.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/eeprom/rtl871x_eeprom.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/efuse/rtl8712_efuse.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/hal_init.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_halinit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/hal/rtl8712/usb_ops_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ifcfg-wlan0
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/autoconf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/basic_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/big_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/generic.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/little_endian.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swab.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/byteorder/swabb.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/circ_buf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/cmd_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_conf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/drv_types_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ethernet.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/farray.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/h2clbk.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/hal_init.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ieee80211_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/if_ether.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ioctl_cfg80211.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/ip.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mlme_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/mp_custom_oid.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/nic_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_ce_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_intf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/osdep_service.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/recv_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_efuse.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_cmdctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_debugctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_edcasetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_fifoctrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_gp_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_interrupt_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_macsetting_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_offload_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_powersave_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_ratectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_security_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_syscfg_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_timectrl_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/rtl8712_wmac_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/ioreg_def/vssver.scc
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_bitdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec/sdio_reg/rtl8712_sdio_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_spec.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl8712_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_byteorder.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_cmd.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_debug.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_eeprom.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_event.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ht.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_io.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_query.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_rtl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_ioctl_set.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_led.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mlme_ext.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_ioctl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_mp_phy_regdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_pwrctrl.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_qos.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_recv.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_rf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_security.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_mlme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_wlan_sme.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtl871x_xmit.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/rtw_android.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_ce.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_linux.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_ops_xp.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sdio_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/sta_info.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_hal.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_ops.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_osintf.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/usb_vendor_req.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/version.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wifi.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/wlan_bssdef.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/include/xmit_osdep.h
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl8712_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/io/rtl871x_io.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_query.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_rtl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/ioctl/rtl871x_ioctl_set.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Kconfig
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/led/rtl8712_led.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/Makefile
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/ieee80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mlme/rtl871x_mlme.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/mp/rtl871x_mp_ioctl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/cmd_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/ioctl_cfg80211.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/io_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/mlme_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/recv_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/rtw_android.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_dep/linux/xmit_linux.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/os_intfs.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/linux/usb_intf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/os_intf/osdep_service.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/pwrctrl/rtl871x_pwrctrl.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl8712_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/recv/rtl871x_recv.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl8712_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/rf/rtl871x_rf.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/runwpa
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/sta_mgt/rtl871x_sta_mgt.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wlan0dhcp
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/wpa1.conf
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl8712_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405/xmit/rtl871x_xmit.c
rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405
Authentication requested [root] for make clean:
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
cd cmd ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd crypto ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd debug ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd eeprom ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8712 ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd io ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd ioctl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mlme ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd mp ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_intf/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd pwrctrl ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd recv ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd rf ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd sta_mgt ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd xmit; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd efuse; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-32-generic-pae/build M=/home/dan/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405 (2)/driver/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405  modules
/bin/sh: 1: Syntax error: "(" unexpected
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
dan@dan-P23G:~/Desktop/rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20120405 (2)$ 

```

---

### Post by ahallubuntu on 2012-10-25
I apologize; Realtek's site seems to be a bit flaky about direct links into their website; even though I used the same link I pasted above, I downloaded a different driver file, 

RTL819xC_USB_linux_v3.4.4_4749.20120806.zip

and when unzipped it created a directory 

RTL8188C_8192C_USB_linux_v3.4.4_4749.20120806

I suggest navigating yourself from Realtek's downloads page 

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Through ("Communications Network ICs" - "Wireless LAN ICs" - "WLAN NIC" - "IEEE 802.11b/g/n Single-Chip", "Software,") check the box next to "RTL8192CU," click "Go," and download the Linux/Unix driver from there.  I chose the "HK1" link to get the above.  Make sure the page says "8192cu" at the top before downloading.

---

### Post by dwb814 on 2012-10-25
ahallubuntu,
THANK YOU brother, worked like a charm. :) I really appreciate your time and effort.

---

### Post by waterloo2005 on 2012-12-13
> **ahallubuntu said:**
> Download the latest driver from Realtek from here:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Open a terminal, then assuming you downloaded it to the Downloads directory in your home directory:

```
cd ~/Downloads
unzip (ZIPFILENAME)
cd (NEWDIRECTORY_CREATED)
chmod 755 ./install.sh
sudo ./install.sh
```


You may need to blacklist your existing driver by adding these three items to the end of the file /etc/modprobe.d/blacklist.conf :

```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

and add the name of the new module "8192cu" to the end of the file /etc/modules so it will be automatically loaded at each boot.

You may need to re-build this each time your kernel is updated by Ubuntu.
In RealTek site, I download 8192cu drive which is for Linux Kernel 2.6.18~2.6.38 and Kernel 3.0.8. But now in Ubuntu12.04 my kernel is 3.2.0-34. Every time I plug the usb 8192cu wireless card my system halts.

---

### Post by jaber426 on 2013-03-02
good look

---

### Post by Lars Karlsson on 2013-04-24
This worked like a charm for me!

---

### Post by davidbaumann on 2013-04-24
```
Please select card type(1/2):1) RTL8192cu
2) RTL8192du
#? 1
You have selected RTL8192cu
rtw_version.h has existed!
Authentication requested [root] for make clean:
install.sh: 38: [: unexpected operator
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm .tmp_versions -fr ; rm Module.symvers -fr
rm -fr Module.markers ; rm -fr modules.order
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver:
install.sh: 48: [: unexpected operator
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.8.0-19-generic/build M=/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103  modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.o
In file included from /home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.c:23:0:
/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_service.h: In Funktion »thread_enter«:
/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/osdep_service.h:569:2: Fehler: Implizite Deklaration der Funktion »daemonize« [-Werror=implicit-function-declaration]
In file included from /home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/drv_types.h:69:0,
                 from /home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.c:24:
/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_recv.h: In Funktion »rxmem_to_recvframe«:
/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_recv.h:628:30: Warnung: Typkonvertierung von Zeiger auf Ganzzahl anderer Breite [-Wpointer-to-int-cast]
/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/include/rtw_recv.h:628:9: Warnung: Typkonvertierung in Zeiger von Ganzzahl anderer Breite [-Wint-to-pointer-cast]
cc1: Einige Warnungen werden als Fehler behandelt
make[2]: *** [/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103/core/rtw_cmd.o] Fehler 1
make[1]: *** [_module_/home/david/Downloads/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103/driver/rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.20120103] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-3.8.0-19-generic'
make: *** [modules] Fehler 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```
```
# uname -r
3.8.0-19-generic

```

---

### Post by mörgæs on 2013-04-24
You are posting in a SOLVED thread, which is not likely to be read by people who have advice to offer.

You will be better off by opening a new one, explaining the problem thoroughly including all the steps you have taken to solve it. You may of course link to this one.

---

