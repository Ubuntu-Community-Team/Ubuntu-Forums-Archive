---
title: "Sony Vaio SVE1711C5E Wireless Lan Driver on Ubuntu 12.04"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by torteloni on 2013-08-04
SOLVED! Hi Board! First of all I want to say that I love the new SSO! Again some unique passwords less for me to remember. :)

But some of you may have guessed: I did not post in the support forums only to praise the SSO. In fact I have a problem with my Laptop Computer, the exact model name is "Sony Vaio SVE1711C5E". (You can find detail information about that computer here: [http://www.sony.co.uk/support/en/product/SVE1711C5E](http://www.sony.co.uk/support/en/product/SVE1711C5E))

Ethernet is available already during installation. However I am unable to use WLAN. Ofcourse I did not expect WLAN to work out of the box. And even though I did not install any additional driver, I have no clue what I can do to make WLAN work after all. On the Sony Homepage all offered drivers are Windows only and Ubuntu is not a supported OS.

I am still a Ubuntu Newbie, so I cannot tell you much more of my problem with my own words. I will rather present you with all the information suggested in [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?t=982880"):

```
luise@luise-SVE1711C5E:~$ lspci00:00.0 Host bridge: Intel Corporation2nd Generation Core Processor Family DRAM Controller (rev 09) 
00:02.0 VGA compatible controller:Intel Corporation 2nd Generation Core Processor Family IntegratedGraphics Controller (rev 09) 
00:14.0 USB controller: IntelCorporation Panther Point USB xHCI Host Controller (rev 04) 
00:16.0 Communication controller: IntelCorporation Panther Point MEI Controller #1 (rev 04) 
00:1a.0 USB controller: IntelCorporation Panther Point USB Enhanced Host Controller #2 (rev 04) 
00:1b.0 Audio device: Intel CorporationPanther Point High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel CorporationPanther Point PCI Express Root Port 1 (rev c4) 
00:1c.1 PCI bridge: Intel CorporationPanther Point PCI Express Root Port 2 (rev c4) 
00:1c.2 PCI bridge: Intel CorporationPanther Point PCI Express Root Port 3 (rev c4) 
00:1d.0 USB controller: IntelCorporation Panther Point USB Enhanced Host Controller #1 (rev 04) 
00:1f.0 ISA bridge: Intel CorporationPanther Point LPC Controller (rev 04) 
00:1f.2 SATA controller: IntelCorporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel CorporationPanther Point SMBus Controller (rev 04) 
02:00.0 Network controller: AtherosCommunications Inc. AR9485 Wireless Network Adapter (rev 01) 
08:00.0 Unassigned class [ff00]:Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev01) 
0e:00.0 Ethernet controller: RealtekSemiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernetcontroller (rev 07)  
```


```
luise@luise-SVE1711C5E:~$ lsusbBus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0003 LinuxFoundation 3.0 root hub 
Bus 001 Device 002: ID 8087:0024 IntelCorp. Integrated Rate Matching Hub 
Bus 002 Device 002: ID 8087:0024 IntelCorp. Integrated Rate Matching Hub 
Bus 001 Device 003: ID 0489:e036Foxconn / Hon Hai 
Bus 001 Device 004: ID 05ca:18c5 RicohCo., Ltd  
```

```
luise@luise-SVE1711C5E:~$ ifconfigeth0      Link encap:Ethernet  HardwareAdresse 54:53:ed:26:87:36  
          inet Adresse:192.168.1.41 Bcast:192.168.1.255  Maske:255.255.255.0 
          inet6-Adresse:fe80::5653:edff:fe26:8736/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST RUNNINGMULTICAST  MTU:1500  Metrik:1 
          RX packets:244 errors:0dropped:0 overruns:0 frame:0 
          TX packets:148 errors:0dropped:0 overruns:0 carrier:0 
          Kollisionen:0Sendewarteschlangenlänge:1000 
          RX-Bytes:39848 (39.8 KB) TX-Bytes:17394 (17.3 KB) 
          Interrupt:42Basisadresse:0xc000 


lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1 Maske:255.0.0.0 
          inet6-Adresse: ::1/128Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING MTU:16436  Metrik:1 
          RX packets:56 errors:0dropped:0 overruns:0 frame:0 
          TX packets:56 errors:0dropped:0 overruns:0 carrier:0 
          Kollisionen:0Sendewarteschlangenlänge:0 
          RX-Bytes:4560 (4.5 KB) TX-Bytes:4560 (4.5 KB) 


wlan0     Link encap:Ethernet  HardwareAdresse 08:3e:8e:cc:5b:4f  
          UP BROADCAST MULTICAST MTU:1500  Metrik:1 
          RX packets:0 errors:0dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0 
          Kollisionen:0Sendewarteschlangenlänge:1000 
RX-Bytes:0 (0.0 B) TX-Bytes:0 (0.0 B)  
```


```
luise@luise-SVE1711C5E:~$ iwconfiglo        no wireless extensions. 


wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point:Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTSthr:off   Fragment thr:off 
          Power Management:off 
          
eth0      no wireless extensions.  
```

```
luise@luise-SVE1711C5E:~$ lsmodModule                  Size  Used by 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
uvcvideo               72627  0 
videodev               98259  1uvcvideo 
v4l2_compat_ioctl32    17128  1videodev 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep              13668  1snd_hda_codec 
snd_pcm                97188  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
arc4                   12529  2 
snd_seq_midi           13324  0 
ath9k                 132390  0 
mac80211              506816  1 ath9k 
snd_rawmidi            30748  1snd_seq_midi 
snd_seq_midi_event     14899  1snd_seq_midi 
joydev                 17693  0 
snd_seq                61896  2snd_seq_midi,snd_seq_midi_event 
snd_timer              29990  2snd_pcm,snd_seq 
snd_seq_device         14540  3snd_seq_midi,snd_rawmidi,snd_seq 
ath9k_common           14053  1 ath9k 
btusb                  18288  2 
ath9k_hw              411151  2ath9k,ath9k_common 
bluetooth             180104  23bnep,rfcomm,btusb 
snd                    78855  16snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                    24067  3ath9k,ath9k_common,ath9k_hw 
soundcore              15091  1 snd 
cfg80211              205544  3ath9k,mac80211,ath 
snd_page_alloc         18529  2snd_hda_intel,snd_pcm 
psmouse                87692  0 
i915                  472941  3 
drm_kms_helper         46978  1 i915 
drm                   242038  4i915,drm_kms_helper 
rts_pstor             445196  0 
i2c_algo_bit           13423  1 i915 
mac_hid                13253  0 
mei                    41616  0 
acer_wmi               28418  0 
sparse_keymap          13890  1acer_wmi 
sony_laptop            45393  0 
serio_raw              13211  0 
wmi                    19256  1acer_wmi 
video                  19596  1 i915 
lp                     17799  0 
parport                46562  3parport_pc,ppdev,lp 
r8169                  62099  0  
```

```
luise@luise-SVE1711C5E:~$ dmesg | grep"wlan"[   16.885439] ADDRCONF(NETDEV_UP):wlan0: link is not ready 
[   16.888537] ADDRCONF(NETDEV_UP):wlan0: link is not ready  
```

```
luise@luise-SVE1711C5E:~$ sudo lshw -Cnetwork[sudo] password for luise: 
  *-network               
       Beschreibung: KabelloseVerbindung 
       Produkt: AR9485 Wireless NetworkAdapter 
       Hersteller: AtherosCommunications Inc. 
       Physische ID: 0 
       Bus-Informationen:pci@0000:02:00.0 
       Logischer Name: wlan0 
       Version: 01 
       Seriennummer: 08:3e:8e:cc:5b:4f 
       Breite: 64 bits 
       Takt: 33MHz 
       Fähigkeiten: pm msi pciexpressbus_master cap_list rom ethernet physical wireless 
       Konfiguration: broadcast=yesdriver=ath9k driverversion=3.2.0-29-generic firmware=N/A latency=0link=no multicast=yes wireless=IEEE 802.11bgn 
       Ressourcen: irq:16memory:c3000000-c307ffff memory:c0000000-c000ffff 
  *-network 
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168B PCIExpress Gigabit Ethernet controller 
       Hersteller: RealtekSemiconductor Co., Ltd. 
       Physische ID: 0 
       Bus-Informationen:pci@0000:0e:00.0 
       Logischer Name: eth0 
       Version: 07 
       Seriennummer: 54:53:ed:26:87:36 
       Größe: 100Mbit/s 
       Kapazität: 1Gbit/s 
       Breite: 64 bits 
       Takt: 33MHz 
       Fähigkeiten: pm msi pciexpressmsix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       Konfiguration:autonegotiation=on broadcast=yes driver=r8169driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.403/27/12 ip=192.168.1.41 latency=0 link=yes multicast=yes port=MIIspeed=100Mbit/s 
       Ressourcen: irq:42ioport:2000(Größe=256) memory:c4404000-c4404fffmemory:c4400000-c4403fff
```

```
luise@luise-SVE1711C5E:~$ lsb_release-d 
Description:    Ubuntu 12.04.1 LTS  
```

```
luise@luise-SVE1711C5E:~$ uname -mr3.2.0-29-generic x86_64
```

```
luise@luise-SVE1711C5E:~$ sudo/etc/init.d/networking restart
 * Running /etc/init.d/networkingrestart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces...     
```

And one last note: While Ubuntuforums was down I posted on the German Sony Support forums. You can find that post here: [http://community.sony.de/t5/Computer-Zubeh%C3%B6r/Sony-Vaio-SVE1711C5E-WLAN-Treiber/m-p/1275282/highlight/false#M28765](http://community.sony.de/t5/Computer-Zubeh%C3%B6r/Sony-Vaio-SVE1711C5E-WLAN-Treiber/m-p/1275282/highlight/false#M28765). But that thread only contains some information on driver installation under windows and helps nothing for Ubuntu.

So I really hope you guys can help me - thanks a lot! :)

---

### Post by torteloni on 2013-08-04
Okay, this is probably the most embarassing thread of all times, but the problem is solved. I just reinstalled Ubuntu 12.04 and all updates and suddenly WLAN works like a charm. I will ask no other questions but rather enjoy the gift of automated WLAN setup. Thank you guys anyways. ;)

---

