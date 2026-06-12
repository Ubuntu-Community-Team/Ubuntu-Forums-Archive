---
title: "Slow Wifi connection on 11.10 and up"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by msubrayada on 2012-10-09
Hi, I just updated ubuntu 11.04 to 11.10 and now my wifi connection is intermittent, few seconds is good and some seconds it freezes. I had the same problem with 12.04. In 11.04 the connection was ok but I want to know if I can have an updated ubuntu working fine.

Thanks

---

### Post by msubrayada on 2012-10-09
Here is some info of my system:

ifconfig -a
```
eth0      Link encap:Ethernet  direcciónHW 04:7d:7b:aa:e2:e6  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:40 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:96 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:96 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:7448 (7.4 KB)  TX bytes:7448 (7.4 KB)

wlan0     Link encap:Ethernet  direcciónHW 7c:e9:d3:ed:71:52  
          Direc. inet:192.168.1.100  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::7ee9:d3ff:feed:7152/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:8269 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:6917 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:4353199 (4.3 MB)  TX bytes:1207217 (1.2 MB)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Lab Information Retrieval"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:10:CD:53:38   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:647   Missed beacon:0


```
sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 7c:e9:d3:ed:71:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-26-generic-pae firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 04:7d:7b:aa:e2:e6
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:3000(size=256) memory:f0804000-f0804fff memory:f0800000-f0803fff memory:f0820000-f083ffff


```
lsmod
```
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254163  1 
arc4                   12473  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          28358  2 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse                63474  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
rtl8192ce              75448  0 
rtl8192c_common        69519  1 rtl8192ce
intel_ips              17822  0 
rtlwifi                95614  1 rtl8192ce
mac80211              393421  3 rtl8192ce,rtl8192c_common,rtlwifi
i915                  513833  8 
drm_kms_helper         32889  1 i915
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
drm                   196290  4 i915,drm_kms_helper
cfg80211              172427  2 rtlwifi,mac80211
i2c_algo_bit           13199  1 i915
mei                    36466  0 
wmi                    18744  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
nvram                  14029  1 thinkpad_acpi
video                  19069  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
ums_realtek            13096  0 
usb_storage            44172  1 ums_realtek
hid                    77367  1 usbhid
uas                    17829  0 
ahci                   21634  2 
r8169                  47200  0 
libahci                25761  1 ahci

```

---

### Post by will1982 on 2012-10-09
Some WiFi cards aren't compatible with Ubuntu.
Are you on a comp where you can replace the card?

---

### Post by msubrayada on 2012-10-09
> **will1982 said:**
> Some WiFi cards aren't compatible with Ubuntu.
Are you on a comp where you can replace the card?

It is not the card, the problem is just at school, at home it works fine. I used a wireless usb adapter and the problem was the same at school. With cable there is no problem.

---

### Post by NikTh on 2012-10-09
> **msubrayada said:**
> It is not the card, **the problem is just at school**, at home it works fine. **I used a wireless usb adapter and the problem was the same at school**. With cable there is no problem.

Maybe the problem is in school and not yours. What I mean (before you tell me "other guys have not any problems") , maybe the school transmit the Wireless signal from a g or b protocol , and your card not support well these protocols. 

I can see that the driver where is loaded in your system ```
driver=rtl8192ce
``` 
is a wireless driver for 802.11**n** protocol. 

Above is not for sure , it is just a thought.

---

### Post by msubrayada on 2012-10-09
> **NikTh said:**
> Maybe the problem is in school and not yours. What I mean (before you tell me "other guys have not any problems") , maybe the school transmit the Wireless signal from a g or b protocol , and your card not support well these protocols. 

I can see that the driver where is loaded in your system ```
driver=rtl8192ce
```is a wireless driver for 802.11**n** protocol. 

Above is not for sure , it is just a thought.

I'll take a look at the router. I think it is a configuration problem with my laptop because it works in ubuntu 11.04.

---

### Post by msubrayada on 2012-10-10
The router at school is **n**. At home I have **g**/**b** and works better than at school.

---

### Post by NikTh on 2012-10-10
> **msubrayada said:**
> The router at school is **n**. At home I have **g**/**b** and works better than at school.

As I said : Was just a thought (not for sure). 

Another thought : Maybe at school too many connected users "eating" the wireless connection ? 

Another suggestion (related to driver) could be : 
When you be in school try these commands 
```
sudo modprobe -rvf rtl8192ce
sudo modprobe rtl8192ce ips=0
``` 

and see if the behavior is better. 

Thanks

---

### Post by msubrayada on 2012-10-11
> **NikTh said:**
> As I said : Was just a thought (not for sure). 

Another thought : Maybe at school too many connected users "eating" the wireless connection ? 

Another suggestion (related to driver) could be : 
When you be in school try these commands 
```
sudo modprobe -rvf rtl8192ce
sudo modprobe rtl8192ce ips=0
``` 

and see if the behavior is better. 

Thanks

Ok, two things
first, I tryed the commands end the situation was not better;
second, the router at school says N but, because of the bit rate, I think it is working on b/g :P sorry.

Only at most 5 people are using the router.

---

### Post by NikTh on 2012-10-11
OK , 

A last suggestion from me . 

Again , when you are in school and connected , try this command and see if network works better and more stable

```
sudo iwconfig wlan0 bit 12M
``` 
Wait about 30 seconds , check if bit/rate changed with 
```
iwconfig
``` 
and see if network stabilized. 

Thanks

---

### Post by wildmanne39 on 2012-10-11
Hi, I would try this link post 6.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks

---

### Post by msubrayada on 2012-10-16
> 
OK , 

A last suggestion from me . 

Again , when you are in school and connected , try this command and see if network works better and more stable

Code:
sudo iwconfig wlan0 bit 12M
Wait about 30 seconds , check if bit/rate changed with 
Code:
iwconfig
and see if network stabilized. 

Thanks


Hi, I did it and the bit rate did not change.

thanks

---

### Post by msubrayada on 2012-10-18
> **Wild Man said:**
> Hi, I would try this link post 6.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Thanks
I did everything but can not change the router settings, the result: I didn't have internet and when I did a ping to some computer, I could see how it still freezes for some time when I try to go online.

Thanks

---

### Post by msubrayada on 2012-10-29
No more suggestions?

---

### Post by wildmanne39 on 2012-10-29
Hi, no more ideas! the settings being changed in the router are very important.
Thanks

---

