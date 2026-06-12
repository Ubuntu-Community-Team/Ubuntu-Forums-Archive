---
title: "Problem with BCM 4313 after upgrade to 12.04 with Dell n4010"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by severinodigio on 2012-09-02
After upgrading from Ubuntu 11.10 to 12.04 my wirelees stopped working. I tried a lot of solutions but I can't fix it. Sometimes the wireless stars working, but when I reboot the wireless doesn't work anymore. My ethernet connection is doing fine.

When I try to activate it in additional hardware I get 

"Sorry, installation of this driver failed.
Please have a look at the log file for details:/var/log/jockey.log"



lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 **Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller** (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

iwconfig

```
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```

ifconfig

```
eth0      Link encap:Ethernet  direcciónHW f0:4d:a2:69:4a:4b  
          Direc. inet:192.168.1.137  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::f24d:a2ff:fe69:4a4b/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3935 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3827 errores:0 perdidos:0 overruns:0 carrier:1
          colisiones:0 long.colaTX:1000 
          Bytes RX:2899748 (2.8 MB)  TX bytes:470111 (470.1 KB)
          Interrupción:44 

eth1      Link encap:Ethernet  direcciónHW 1c:65:9d:e9:00:f9  
          Dirección inet6: fe80::1e65:9dff:fee9:f9/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:78
          Paquetes TX:0 errores:12 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:629 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:629 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:57600 (57.6 KB)  TX bytes:57600 (57.6 KB)

```

lsmod

```
Module                  Size  Used by
wl                   2646601  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174222  1 
lib80211_crypt_tkip    17275  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 dell_wmi
lib80211               14040  2 wl,lib80211_crypt_tkip
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17822  0 
uvcvideo               67203  0 
i915                  414739  9 
videodev               86588  1 uvcvideo
mac_hid                13077  0 
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
drm_kms_helper         45466  1 i915
drm                   197692  5 i915,drm_kms_helper
serio_raw              13027  0 
i2c_algo_bit           13199  1 i915
mei                    36570  0 
video                  19068  1 i915
coretemp               13269  0 
lp                     17455  0 
soundcore              14635  1 snd
parport                40930  3 parport_pc,ppdev,lp
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
usbhid                 41906  0 
hid                    77367  1 usbhid
atl1c                  36718  0 

```


Network config

```
 *-network               
       descripción: Interfaz inalámbrica
       producto: BCM4313 802.11b/g/n Wireless LAN Controller
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: eth1
       versión: 01
       serie: 1c:65:9d:e9:00:f9
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=wl1 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       recursos: irq:17 memoria:f0500000-f0503fff
  *-network
       descripción: Ethernet interface
       producto: AR8152 v1.1 Fast Ethernet
       fabricante: Atheros Communications Inc.
       id físico: 0
       información del bus: pci@0000:04:00.0
       nombre lógico: eth0
       versión: c1
       serie: f0:4d:a2:69:4a:4b
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.137 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       recursos: irq:44 memoria:f0400000-f043ffff ioport:2000(size=128)

```

Thank you!

---

### Post by chili555 on 2012-09-02
As a temporary measure, please try:```
sudo ifconfig eth1 down
sudo modprobe -r wl
sudo modprobe -r lib80211  [COLOR="Red"]<--it may or may not still be loaded[/COLOR]
sudo modprobe brcmsmac
iwconfig
```Any change?

---

### Post by severinodigio on 2012-09-02
Thank you for the reply!

I tried that and there are no changes


When I ran "sudo modprobe -r lib80211" 

I got "FATAL: Module lib80211 is in use"

iwconfig


```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-09-02
> I tried that and there are no changesReally? Before:> [COLOR="Red"]eth1[/COLOR]      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:244
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0...and after:> [COLOR="Red"]wlan0 [/COLOR]    IEEE 802.11[COLOR="Red"]bgn[/COLOR]  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offDoes it scan?```
sudo iwlist wlan0 scan
```Let's see some additional diagnostics:```
dmesg | grep brcm
lspci -nn | grep 0280
```Thanks.

---

### Post by severinodigio on 2012-09-02
Scan

```
wlan0     No scan results

```



dmesg | grep brcm

```

[ 1266.571200] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:8241 brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]()
[ 1266.571210] Modules linked in: arc4 brcmsmac mac80211 brcmutil cfg80211 crc8 cordic rfcomm bnep bluetooth parport_pc ppdev binfmt_misc joydev snd_hda_codec_hdmi snd_hda_codec_realtek lib80211_crypt_tkip dell_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event lib80211 snd_seq snd_timer snd_seq_device wmi snd i915 dell_laptop dcdbas psmouse serio_raw mac_hid drm_kms_helper coretemp drm uvcvideo i2c_algo_bit videodev video soundcore snd_page_alloc mei(C) intel_ips lp parport usbhid hid ums_realtek usb_storage uas atl1c [last unloaded: wl]
[ 1266.571363]  [<f90226fa>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[ 1266.571387]  [<f90226fa>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[ 1266.571419]  [<f90226fa>] brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[ 1266.571437]  [<f9012180>] brcms_ops_flush+0x30/0x50 [brcmsmac]

```

lspci -nn | grep 0280

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

---

### Post by chili555 on 2012-09-02
I think our friend lib80211 is at work here. Another temporary measure:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit
```Reboot and let us see:```
iwconfig
dmesg | grep brcm
```This device is tricky!> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]]

---

### Post by severinodigio on 2012-09-02
I rebooted and now wireless is working

iwconfig


```
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:208  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```


"dmesg | grep brcm" doesn't show anything

---

### Post by chili555 on 2012-09-02
> I rebooted and now wireless is workingWeird, actually. Please post:```
lsmod | grep -e wl -e brcm
cat /etc/modprobe.d/blacklist.conf | tail -n5
```Weird, I tell ya!!

---

### Post by severinodigio on 2012-09-02
lsmod | grep -e wl -e brcm
```

brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
wl                   2646601  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
```

cat /etc/modprobe.d/blacklist.conf | tail -n5
```
blacklist bcma
blacklist brcmsmac
blacklist bcma
blacklist wl
blacklist wl
```

---

### Post by chili555 on 2012-09-02
Wow! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines I've highlighted:```
[COLOR="Red"]blacklist bcma
blacklist brcmsmac
blacklist bcma[/COLOR]
blacklist wl
blacklist wl
```I notice there are repeats here. If bcma or brcmsmac is blacklisted above these lines, remove those entries, too. Proofread, save and close gedit. Now do:```
sudo gedit /etc/modules
```It should include brcmsmac and *NOT* include wl. Amend as needed. Proofread, save and close gedit.

Reboot and let us see:```
lsmod | grep -e wl -e brcm
```We'll get it!

---

### Post by severinodigio on 2012-09-02
haha thanks for all the help!

Let's see:

In blacklist.conf on the bottom appeared this ones blacklisted:
```

blacklist mac80211
blacklist brcm80211
blacklist cfg80211
blacklist wl
blacklist lib80211_crypt_tkip
blacklist lib80211
[COLOR="Red"]blacklist bcma
blacklist brcmsmac
blacklist bcma[/COLOR]
blacklist wl
blacklist wl

```
I deleted the ones on red.


grep -e wl -e brcm
```
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
```

---

### Post by chili555 on 2012-09-02
Ahh! Much better. Now, how about:```
iwconfig
```Network Manager will probably not activate wlan0, your Broadcom, with the ethernet attached. I suggest you detach it and see if NM sees your network and connects.

---

### Post by severinodigio on 2012-09-02
iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Lynksys E2500"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:AA:4B:42:89:5C   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:52   Missed beacon:0

eth0      no wireless extensions.
```


I tried booting with ethernet detached two times and wireless is still working fine. Now I am experiencing only one problem haha. When I log for the first time, the applet of NM on the superior bar shows that I'm connected, but when I press it, it only shows to enable networkin, enable wireless, information of the connection, and edit connections. I can't see if there are any wireless networks available. But if I go to System settings/Network/Wireless. I can see the networks available, and chose anyone, and then appears all the information on the applet.

---

### Post by chili555 on 2012-09-02
Can you enable wireless and networking? Do your networks then appear?> wireless is still working fine. Awesome! Let's dump the STA driver altogether:```
sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by severinodigio on 2012-09-02
I removed bcmwl-kernel-source, and now?

---

### Post by chili555 on 2012-09-02
> **severinodigio said:**
> I removed bcmwl-kernel-source, and now?Can you click the Network Manager icon, enable networking, enable wireless and then properly see your available networks?

---

### Post by severinodigio on 2012-09-02
> **chili555 said:**
> Can you click the Network Manager icon, enable networking, enable wireless and then properly see your available networks?

Yes. When I reboot, I can only see: enable networking and enable wirelees. I am connected to my router but I can't see the available networks. If I disable and then enable the wireless I can see all the available networks.

---

### Post by chili555 on 2012-09-02
Let's have a look at:```
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by severinodigio on 2012-09-02
> **chili555 said:**
> Let's have a look at:```
cat /etc/NetworkManager/nm-system-settings.conf
```

I don't have that file.

I can see 

NetworkManager.conf

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```

---

### Post by chili555 on 2012-09-03
> I can see

NetworkManager.conf

```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```
That looks pretty normal depending on:```
cat /etc/network/interfaces
```Thanks.

---

### Post by severinodigio on 2012-09-03
cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2012-09-03
Still looks normal in every respect. When you click the NM icon and select Network Settings, Wireless and Options, are both the boxes checked for Available to All Users and Connect Automatically?

Thanks.

---

### Post by severinodigio on 2012-09-04
Yes, both boxes were checked.

Today I turned on the computer and it was fixed alone!

Thank you very much for all your help chili!!!

---

### Post by chili555 on 2012-09-04
Awesome! I'm glad it's working by whatever means.

---

