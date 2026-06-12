---
title: "Huawei K4510 and Ubuntu 12.04 LTS"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by gjvdhazel on 2013-05-23
Hi all,

I am trying to get a Huawei K4510 usb-modem working on 12.04 LTS. The modem is recognized by the os and networkmanager, as it ask for the setup of a new mobile internet connection. Setting up the apn and username + password works as it should work, however, when trying to connect it fails. 

I have searched for a solution, as problems with Huawei modems and linux are known, but so far have not found a solution. Most known problems are on the fact that the modem has multiple modes, but as the network manager recognizes it right away, I dare say that's not the problem here. Below is a section of syslog from the moment I try to make a connection untill it spits back that it failed to connect.....

```
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> Activation (ttyUSB2) starting connection 'Vodafone connection'
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <warn> GSM connection failed: (32) Sending command failed: device is not enabled
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'unknown') [40 120 1]
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <warn> Activation (ttyUSB2) failed.
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
May 23 09:09:45 sysop-DS61 NetworkManager[808]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
May 23 09:09:45 sysop-DS61 NetworkManager[808]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
May 23 09:09:45 sysop-DS61 modem-manager[789]: <info>  Modem /org/freedesktop/ModemManager/Modems/4: state changed (connected -> disconnecting)
May 23 09:09:45 sysop-DS61 modem-manager[789]: <info>  Modem /org/freedesktop/ModemManager/Modems/4: state changed (disconnecting -> connected)
May 23 09:09:45 sysop-DS61 NetworkManager[808]: <info> disconnect failed: (32) The serial port is not open.

```

Obviously some things do not work as they should, but starting to solve this is beyond my capabilities at the moment, so any help would be great.....

Gert-Jan

---

### Post by praseodym on 2013-05-23
Please show the outputs of:
```

lsusb
usb-devices
lsmod
ifconfig -a
cat /etc/resolv.conf
```
Did you install "usb-modeswitch"?

---

### Post by gjvdhazel on 2013-05-23
Here you go......

```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 001 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 002 Device 003: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 004: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 002 Device 005: ID 12d1:14cb Huawei Technologies Co., Ltd. 
```
```
$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0723 Rev=94.54
S:  Manufacturer=Generic 
S:  Product=USB Storage
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5151 Rev=00.10
S:  Manufacturer=SanDisk Corporation
S:  Product=Cruzer Micro
S:  SerialNumber=20044317611B77A2CE66
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04d9 ProdID=1603 Rev=03.10
S:  Manufacturer= 
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c050 Rev=27.20
S:  Manufacturer=Logitech
S:  Product=USB-PS/2 Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14cb Rev=00.00
S:  Manufacturer=Vodafone Group (Huawei) 
S:  Product=Vodafone Mobile Broadband (Huawei) 
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=31 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=39 Driver=cdc_wdm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=38 Driver=qmi_wwan
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=33 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=32 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```
```
$ lsmod
Module                  Size  Used by
ppp_deflate            12879  0 
zlib_deflate           26623  1 ppp_deflate
bsd_comp               12843  0 
ppp_async              17308  0 
crc_ccitt              12628  1 ppp_async
nls_iso8859_1          12618  1 
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_realtek    64876  1 
option                 25700  1 
qmi_wwan               13022  0 
usb_wwan               19532  1 option
usbnet                 25247  1 qmi_wwan
usbserial              36882  4 option,usb_wwan
cdc_wdm                17664  1 qmi_wwan
rfcomm                 38104  0 
bnep                   17791  2 
bluetooth             189585  10 rfcomm,bnep
parport_pc             32115  0 
ppdev                  12850  0 
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
xt_hl                  12466  6 
ip6t_rt                12474  3 
nf_conntrack_ipv6      13750  7 
nf_defrag_ipv6         13176  1 nf_conntrack_ipv6
ipt_REJECT             12513  1 
xt_LOG                 17238  9 
xt_limit               12542  12 
xt_tcpudp              12532  22 
xt_addrtype            12597  4 
xt_state               12515  14 
ip6table_filter        12712  1 
ip6_tables             22382  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12586  0 
nf_conntrack_broadcast    12542  1 nf_conntrack_netbios_ns
nf_nat_ftp             12596  0 
nf_nat                 24741  1 nf_nat_ftp
nf_conntrack_ipv4      14123  9 nf_nat
uas                    17745  0 
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
nf_conntrack_ftp       13184  1 nf_nat_ftp
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365556  1 kvm_intel
usb_storage            39720  1 
nf_conntrack           66862  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_hda_intel          33029  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iptable_filter         12707  1 
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ip_tables              18107  1 iptable_filter
x_tables               22012  12 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_midi           13133  0 
microcode              18396  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
lpc_ich                16993  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13078  0 
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  470823  3 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
mei                    36404  0 
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19070  1 i915
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
r8169                  56853  0 
```
```
$ifconfig -a
eth0      Link encap:Ethernet  HWaddr 80:ee:73:5c:88:41  
          inet addr:*****  Bcast:******  Mask:255.255.255.0
          inet6 addr: ******** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12578548 (12.5 MB)  TX bytes:995167 (995.1 KB)

eth1      Link encap:Ethernet  HWaddr 80:ee:73:5c:88:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11355475 (11.3 MB)  TX bytes:11355475 (11.3 MB)

wwan0     Link encap:Ethernet  HWaddr 02:50:f3:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
```
$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search *****

```
```
$ which usb_modeswitch
/usr/sbin/usb_modeswitch
```

I don't think usb-modeswitch is the problem, as network-manager sees it as a mobile broadband connection......but could be wrong here

Gert-Jan

---

### Post by praseodym on 2013-05-23
Obviously, 12d1:14cb is one the modem modes. A "new" one for the module cdc_ether and an "old" one without these interfaces. Try:
```

gksu gedit /etc/usb_modeswitch.d/12d1:14cb
```

Enter these lines:
```

# Huawei K4510

TargetVendor=  0x12d1
TargetProduct= 0x14cb

MessageContent="55534243123456780000000000000011060000000000000000000000000000"
```

Save and close the editor. After re-plugging the stick, please show
```

usb-devices

```
again.

---

### Post by gjvdhazel on 2013-05-23
done

```
$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0723 Rev=94.54
S:  Manufacturer=Generic 
S:  Product=USB Storage
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5151 Rev=00.10
S:  Manufacturer=SanDisk Corporation
S:  Product=Cruzer Micro
S:  SerialNumber=20044317611B77A2CE66
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04d9 ProdID=1603 Rev=03.10
S:  Manufacturer= 
S:  Product=USB Keyboard
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c050 Rev=27.20
S:  Manufacturer=Logitech
S:  Product=USB-PS/2 Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=02 Lev=02 Prnt=02 Port=05 Cnt=03 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=14cb Rev=00.00
S:  Manufacturer=Vodafone Group (Huawei) 
S:  Product=Vodafone Mobile Broadband (Huawei) 
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=31 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=39 Driver=cdc_wdm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=38 Driver=qmi_wwan
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=33 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=32 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.05
S:  Manufacturer=Linux 3.5.0-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

---

### Post by praseodym on 2013-05-23
Ok, now reinstall the network-manager and reboot:
```

sudo apt-get install --reinstall network-manager network-manager-gnome
```

---

### Post by gjvdhazel on 2013-05-23
done, although same version was installed.....doesn't change my connection problem

---

### Post by praseodym on 2013-05-23
Check this thread:

[http://ubuntuforums.org/showthread.php?t=1831649](http://ubuntuforums.org/showthread.php?t=1831649)

---

### Post by gjvdhazel on 2013-05-23
OK, will try and check the checklist and see if anything helps solving my problem. For now, thanks for your help. I will report back if I get it working....

---

