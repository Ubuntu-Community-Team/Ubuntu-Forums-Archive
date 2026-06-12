---
title: "BCM4321 and wl driver causes lockups."
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by VeeDubb on 2011-08-20
I've tried searching all over the place, and I'm drowning in outdated and contradictory information.

I have a brand new Netgear WiFi PCI adapter.

The exact model is "WN311B-100NAS N300"

The related output of lspci is
```
03:06.0 Network controller: Broadcom Corporation BCM4321 802.11b/g/n (rev 01)
```

lsmod returns:

```
Module                  Size  Used by
lib80211_crypt_tkip    17387  0 
wl                   2568244  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vmnet                  55734  13 
vmblock                18923  1 
vsock                  47659  0 
vmci                   64490  1 vsock
vmmon                  89333  0 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
snd_usb_audio         112426  1 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_intel          33176  2 
uvcvideo               72195  0 
usb_storage            53538  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
btusb                  18600  2 
uas                    17996  0 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
usbhid                 46956  0 
snd_pcm                96391  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
hid                    91020  1 usbhid
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10709116  50 
snd                    67382  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k10temp                13119  0 
psmouse                73535  0 
sp5100_tco             13744  0 
edac_core              53845  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
serio_raw              13166  0 
edac_mce_amd           23464  0 
lp                     17825  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport                46458  3 parport_pc,ppdev,lp
pata_atiixp            13165  0 
ahci                   25951  3 
libahci                26642  1 ahci

```

So, I know it's using the BCM4321 chipset and wl driver.

Ubuntu detected this card without any trouble, and I was able to use the "Additional Drivers" application to get it running before disconnecting my ethernet.

The card works well, and is very stable until I try to download a file larger than a few MB, or try to play a video stored on my home network.  As soon as I try either of those, my computer locks up hard.  No error messages.  Just a hard lockup that I can't get out of with anything short of holding down the power button on my case until it cuts the power supply.

Where do I begin tracking this down?

---

### Post by VeeDubb on 2011-08-20
More info.

I have purged all of the ubuntu packages associated with this driver, and installed from the hybrid source tarball offered by broadcom and I'm getting the exact same results.

The card establishes a connection that is fast and stable, but causes infrequent random lockup while connected, and downloading a large file or streaming a video on the local network causes a complete system lockup withing 30-60 seconds.

Because the card works for the most part, but locks up under load, I'm inclined to think it's a hardware problem, but I'd really like to find a way to test that theory before I make the 80 mile round trip to Fry's to exchange it.

---

### Post by VeeDubb on 2011-08-21
At this point, I'm not actually expecting anybody to come up with a step by step solution.  Having spent all of my time since the origianl post either working, commuting, sleeping or researching this problem, it's become clear that while broadcom specifically supports this chipset with their linux kernel package, it is a relatively obscure chipset.


At this point, what I'm really looking for is anyone who can help me diagnose whether the problem is the chipset, a software conflict, or if I just got a defective card.

I've never had a wireless card behave like this.  I'm actually using it right now to post this, and things are fine.  But, if I try to download a file larger than a few MB or stream a video from my NAS, it will lock my computer up completely.  All the references I can find about broadcom causing lockups seem to be about very specific models with WiFi and BT on the same card, or they're several years old.



If I bought this here in town I'd just swap it out.  The trouble is that the store I bought it from is about 40 miles up the freeway.  If the model is okay, and I just got a defective one, I'd be happy to go exchange it, but I don't want to go exchange it only to find that I should have returned it completely and bought a different one.  I like this model because it comes with a massive antenna, and none of the others I could find come with much more than some screw-on antennas for the back of the PCI card or a very cheap single external, and they never work well because they have to broadcast through your case.  To get an antenna this size I'd have to pay almost as much for card with a garbage antenna and then shell out more money for an after market antenna.

---

### Post by praseodym on 2011-08-21
Can you post:

```

lspci -nnk | grep -iA2 net
sudo iwlist scan

```
I think you use mixed encryption WPA/WPA2. The network-manager causes troubles with that, you may change to WPA2-AES (CCMP) if possible. Alternatively, you may try Wicd instead including the Add-On from flash63:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart

```
Deactivate the NM in "Autostart". Set **wlan0** as wireless interface and **wext** as driver in Wicd.

---

### Post by VeeDubb on 2011-08-21
```
:~$ lspci -nnk | grep -iA2 net
03:06.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Netgear Device [1385:7d00]
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```


```
lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: C0:3F:0E:AE:58:D0
                    ESSID:"APT207"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-92 dBm
                    IE: Unknown: DD800050F204104A00011010440001021041000100103B000103104700107E4009CB1C59051E6342448F8084E40A1021000D4E4554474541522C20496E632E10230008574E52333530304C10240008574E52333530304C10420004333530301054000800060050F204000110110008574E52333530304C100800020084103C000101
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:24:7B:A5:0A:38
                    ESSID:"myqwest6055"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B000103104700102E3A9D0E1D4DFA087F4E5011E555682E102100025449102300064150444B3731102400043731303010420007313233343332311054000800060050F20400011011001A416374696F6E7465632052656769737472617220504B3530303010080002008C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:26:88:E4:59:74
                    ESSID:"givens"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: C0:C1:C0:1C:44:E1
                    ESSID:"Vinyard"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-48 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B000103104700101D3343790FFEC69FB47A4C3393A050A810210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 05 - Address: 00:24:B2:10:C5:FA
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-54 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 02:13:CE:14:30:37
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency=2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-51 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: F0:7D:68:82:06:46
                    ESSID:"sjaynec"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010C53945155E1712A013E8F07D6882064710210006442D4C696E6B102300074449522D3831351024000830303030303030301042000830303030303030301054000800060050F2040001101100074449522D383135100800020086103C000103
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 08 - Address: C0:C1:C0:1C:44:E3
                    ESSID:"Vinyard-guest"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-49 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 09 - Address: 00:23:33:17:5A:E0
                    ESSID:"\x00"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 10 - Address: 00:26:F2:EF:42:1C
                    ESSID:"wsfp"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD8B0050F204104A0001101044000102103B00010310470010000000000000100000000026F2EF421C1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001B574E5231303030763228576972656C6573732041502D322E344729100800020086103C000103
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

```


As far as encryption, I started out with WPA2 [AES], and I also tried downgrading to good old WEP to see if that helped.  It didn't make any difference.  I skipped over WPA-TKIP because it doesn't support N networks, or at least it doesn't on my router.

I'll give wicd a try if you still think it might help

---

### Post by VeeDubb on 2011-08-21
Just to narrow the problem down a little more, I connected to a neighbor's unencrypted wifi network, and had the same results.  Worked fine for browsing (mostly) but crashed when I tried to download a file.

So, it has nothing to do with encryption, and nothing to do with my router, although I didn't think it would be the router anyway since my router and the WiFi card are the same brand.

---

### Post by praseodym on 2011-08-21
Show additionally:

```
ifconfig -a
rfkill list
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

You may add the nameservers of your provider (or the Google-Public-Nameservers 8.8.8.8 and 8.8.4.4) directly in the NM applet. Change the settings in your wireless setup under "IPv4-settings" to "Automatically (DHCP), adresses only" and add the nameservers. Restart your connection

---

### Post by VeeDubb on 2011-08-21
ifconfig -a

```
eth2      Link encap:Ethernet  HWaddr 00:26:f2:03:66:b8  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:f2ff:fe03:66b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1794 errors:2110 dropped:0 overruns:0 frame:1768
          TX packets:1735 errors:193 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1836237 (1.8 MB)  TX bytes:217432 (217.4 KB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66332 (66.3 KB)  TX bytes:66332 (66.3 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.104.1  Bcast:192.168.104.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


rfkill list

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```It's worth noting that the BT adapter referenced is a completely separate device, and rebooting after removing the BT adapter had no effect.



route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.104.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2

```



cat /etc/resolv.conf

```
# Generated by NetworkManager
nameserver 192.168.1.1
```  192.168.1.1 is my WiFi router.  It has really excellent firmware and does a great job of auto-configuring everything and doing my name-server routing generally.



cat /etc/network/interfaces

```
auto lo
iface lo inet loopback

```


I'll try the nameserver switching next, but I would be shocked if it helped.  The fastest way to cause a lockup is by streaming a large video from my NAS box, and since that's my home net, there's no interaction with any name server.

---

### Post by praseodym on 2011-08-21
Blacklist the module brcm80211:

```
sudo service network-manager stop
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf brcm80211 wl
sudo modprobe -v wl
sudo depmod -a
sudo update-initramfs -u
sudo service network-manager start
```

---

### Post by VeeDubb on 2011-08-21
blackliting brcm80211 didn't seem to make any difference.  The connection is still excellent, browsing is stable for long enough to read and respond to forum posts, and transfering larger volumes of data still causes a total system lockup.

Just in case something else changed along the way, here's the current output of lsmod  ```
Module                  Size  Used by
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vmnet                  55734  13 
vmblock                18923  1 
vsock                  47659  0 
vmci                   64490  1 vsock
vmmon                  89333  0 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
joydev                 17606  0 
snd_hda_codec_realtek   336771  1 
lib80211_crypt_tkip    17387  0 
btusb                  18600  2 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
usbhid                 46956  0 
snd_usb_audio         112426  1 
uvcvideo               72195  0 
hid                    91020  1 usbhid
snd_usbmidi_lib        25139  1 snd_usb_audio
videodev               82052  1 uvcvideo
snd_hda_intel          33176  2 
v4l2_compat_ioctl32    17078  1 videodev
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_pcm                96391  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
wl                   2568244  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
nvidia              10709116  40 
psmouse                73535  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13744  0 
snd                    67382  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14991  2 lib80211_crypt_tkip,wl
soundcore              12680  1 snd
serio_raw              13166  0 
k10temp                13119  0 
i2c_piix4              13303  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53845  0 
edac_mce_amd           23464  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
pata_atiixp            13165  0 
ahci                   25951  3 
libahci                26642  1 ahci

```

---

### Post by westie457 on 2011-08-21
Hi out of curiosity have you tried installing b43-fwcutter as well.

I use a different broadcom chip - 4311. I have that working at full speed with the STA driver and b43-fwcutter.

It might work for you too.

---

### Post by VeeDubb on 2011-08-21
I had b43-fwcutter installed at one point early on and it made no difference.  I had removed it since then because I read a few reports of conflicts between the two drivers.  Just for grins and giggle I went ahead and re-installed it.  It made no difference.

---

### Post by praseodym on 2011-08-21
The chipset [14e4:4329] doesnt work with the module b43, the STA-driver has to be used with this device.

IMHO the problem is the mixed encryption, try WPA2-AES and/or Wicd.

---

### Post by VeeDubb on 2011-08-21
Mixed encryption is not being used.  My router is set to WPA2-PSK (AES) only.  I have also tried WEP, and I've tried connecting to an unencrypted network.

Also, I've tried WiCd.  I encountered the exact same behavior.  I still haven't managed to determine conclusively whether it is a software problem or a hardware problem, but I have managed to determine that it has nothing to do with encryption, network manager or my router.

---

### Post by westie457 on 2011-08-21
Never having had the issue you have I can only make suggestions that may or may not work and with some of them you might think I am insulting your intelligence, which is definitely not the case.

I take at some stage you have looked at this page [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
to work out which driver to use. Also I expect you have tried all of the alternatives to the one suggested by Additional Drivers or 'Jokey' as it is sometimes called along with 'bcmwl-modaliases'.

Other than this I have no suggestions for you. Neither do I have a working solution.

I hope something in this post works or you are going on a long drive to return a faulty piece of equipment.

Just had a strange thought. Do you by any chance dual-boot with Windows using your wireless device. Occasionally giving something like this a kick with Windows then rebooting to Ubuntu while leaving the device plugged in makes it work properly.

---

### Post by VeeDubb on 2011-08-22
Nothing insulting about it at all.  We all need a sanity check once in a while.

My wireless card, according to that site is "partially supported" by b43.  When I modprobe -r wl to clear out the wl driver and then load up b43, the network manager can see that it is a wireless card, but I can't actually get it to find any networks.  WiCd does more or less the same thing.

According to broadcom, my card should be fully supported by wl, and in many respects, it's working great.  It establishes a connection very quickly, picks up my network at full strength, and it can see a surprising large number of networks.  It just causes my system to lock up when I put it under a load.

The only interesting change in behavior, is that instead of going from working great to locking up, it will now sometimes drop from the full 4 bars in the indicator to only 4, followed shortly after by the network failing to respond.  Then, the system will lock.  I'm thinking more and more that this is a piece of defective hardware.  I just really don't want to swap models if I don't have to, but I also don't want to drive to fry's twice.

I did manage to find a forum post here from someone who said that they have this same card, and all they did to get it working was install every broadcom related package they could find in the repos.  Done and done.

Since I'm really liking the antenna, I think I'll exchange it for another of the same model unless somebody comes up with somehting brilliant before I get a day off to drive to Fry's.

---

### Post by VeeDubb on 2011-08-22
Here's my cautionary tale for anybody who reads this looking for their next WiFi card.

Don't buy this card.

Don't buy any card that uses any chipset made by broadcom.  Many of them work, but it's simply not worth the trouble. 

All Orinco chipsets, nearly all Atheros chipsets, and most RAlink chipsets will work with no more hardware configuration than you need with a wired card (which means no configuration at all)

I exchanged this netgear for a Linksys WMP600n, and the network manager had me online before all my Unity indicators had cleared.

When you're shopping, check the list of cards at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and if it doesn't say "Yes" in the "works out of the box" column, just don't buy it.

---

### Post by northd_tech on 2011-08-26
> **VeeDubb said:**
> Here's my cautionary tale for anybody who reads this looking for their next WiFi card.

Don't buy this card.

Don't buy any card that uses any chipset made by broadcom.  Many of them work, but it's simply not worth the trouble. 

All Orinco chipsets, nearly all Atheros chipsets, and most RAlink chipsets will work with no more hardware configuration than you need with a wired card (which means no configuration at all)

I exchanged this netgear for a Linksys WMP600n, and the network manager had me online before all my Unity indicators had cleared.

When you're shopping, check the list of cards at [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and if it doesn't say "Yes" in the "works out of the box" column, just don't buy it.

Ummm, that "WirelessCardsSupported" page claims that a Broadcom "4321" **has a "Yes"** under "Works out of the box..." (using the STA driver):

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

My Broadcom 4321AG/"4328" has been BY FAR the LEAST troublesome, nearly rock-solid wireless interface that I've ever used on **any** laptop under Ubuntu (or several other 'Linuces' for that matter), and I've been using it for 3+ years under Linux (64-bit) across dozens if not hundreds of Updates.

Of course, I started out with ndiswrapper and the Windows drivers, then moved onto compiling Broadcom's "STA" driver once it was available.  After that, I generally just needed to "Activate" the proprietary "STA" driver, and it possibly needed a "wl" added to /etc/modules and a single restart in order to work perfectly.

At one of my former workplaces, I needed to disable IPv6 to correct slow, dropped wireless connections similar to what you describe (and I suspect that was due to an ISP and/or Apple AirPort issue, since my Ubuntu laptop had the most stable connection out of anyone's laptop in the place).  We had MANY issues with the wireless there and the IT "Mac guy" at work was **constantly** 'fiddling' with the passwords and other settings with the 802.11n AirPort for whatever reasons, and he never shared the AP settings with me, so I needed him to type the password(s) for me- often several times a week.  Once Ubuntu encrypted the wireless settings, my Broadcom wireless worked better than most/all? (including the wireless printers).  In fact, we often used my 64-bit Ubuntu 9.xx Broadcom "4328" laptop wireless to diagnose the connection problems since **I was the only one that could get and stay** connected.

My $0.02 (and my cautionary tale) is to stay with the "LTS" (read Long Term Support) versions of Linux, but it does sound like VeeDubb may well have had a hardware problem (which might have been due to BIOS, or motherboard, or "bridge," or power management settings, or a "software switch," or conflicting motherboard and/or laptop modules, or ....)

---

### Post by wildmanne39 on 2011-08-26
Hi, I agree with northd_tech broadcom is a very well supported card, sometimes it takes a little work to get it working, as it does with most cards.

Also 11.04 has problems with the driver that is not present in 10.04 or 10.10 but hopefully will be resolved in the next release.

---

### Post by VeeDubb on 2011-08-27
> **northd_tech said:**
> Ummm, that "WirelessCardsSupported" page claims that a Broadcom "4321" **has a "Yes"** under "Works out of the box..." (using the STA driver)

VeeDubb may well have had a hardware problem (which might have been due to BIOS, or motherboard, or "bridge," or power management settings, or a "software switch," or conflicting motherboard and/or laptop modules, or ....)

Interestingly enough, the Netgear WN311B, which is the model of card, is not listed at all.  As far as other issues, I did manage to narrow the problem down to an extremely small set of possible causes.

[LIST=1]
[*]The card is not adequately supported.
[*]The particular card that I received was defective, and multiple people experienced the exact same defect with this particular card, meaning that netgear had a serious QC issue with this card.
[*]There is a software bug in 11.04 with this driver that has been present in many, but not all versions of Ubuntu, incuding at least one LTS version.
[/LIST]

> **wildmanne39 said:**
> Hi, I agree with northd_tech broadcom is a very well supported card, sometimes it takes a little work to get it working, as it does with most cards.

Also 11.04 has problems with the driver that is not present in 10.04 or 10.10 but hopefully will be resolved in the next release.

I also hope that it will be fixed in a future release, because I'm sure I won't be the last one to buy this card.  It is one of a VERY small number of readily available N cards with an external (i.e. - completely separate) dual channel antenna.  Putting antenna's on the back of your case means that your signal has to bounce around or broadcast through your case.  

As far as most cards requiring a little work to get going, that's simply not accurate.  All Orinco cards are zero configuration, 100% plug n play as far as I know.  Almost all Atheros based cards are 100% plug and play.  Almost all RaLink cards are now 100% plug and play.



At the end of the day, anybody out there is welcome to buy any card they want, and more power to you.  But, there are cards that are 100% plug n play under linux, thanks in large part to manufacturers that have supported the linux community.  If you're in the market for a card, it simply makes sense to buy a card that is guaranteed to work.  Simple as that.

---

### Post by northd_tech on 2011-08-27
I'm assuming that it is now too late for you to run the following commands with that PCI card installed (because it was already returned, VeeDubb?):

```
lspci -vvnn | grep etwork
lspci -vvnn | grep thern
sudo lshw -C network
lsusb
```For others' reference, here are the Netgear page(s) for that WN311B:

[http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#one](http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#one)

[http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#two](http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#two)

[http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#three](http://www.netgear.com/home/products/wireless-adapters/work-and-play/WN311B.aspx#three)

Datasheet
[http://www.netgear.com/images/WN311B_DS_15June1018-5743.pdf](http://www.netgear.com/images/WN311B_DS_15June1018-5743.pdf)

High-res image
[http://www.netgear.com/images/enus_left-hires_product_wn311b18-5746.tif](http://www.netgear.com/images/enus_left-hires_product_wn311b18-5746.tif)

Low-res image
[http://www.netgear.com/images/enus_left-lores_product_wn311b18-5747.jpg](http://www.netgear.com/images/enus_left-lores_product_wn311b18-5747.jpg)

Also, FWIW, here's what my working (under 64-bit Lucid Lynx 10.04.3 LTS) Broadcom "4328" tells us (and it currently is using the "STA" driver or "wl" module):

> **lspci -vvnn | grep etwork**
03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
EDIT:  Also- that "push 'N' connect" feature looks like a WPS (WiFi Protected Setup) mostly-Windows thing that isn't very well supported under Linux yet from my research a few months ago:

[http://linuxwireless.org/en/developers/Brainstorming/WPS-client](http://linuxwireless.org/en/developers/Brainstorming/WPS-client)

[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

EDIT2:  Here is the edited output from a 'full' **lspci -vvnn** command for my "4328":
> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:1366]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f2200000 (64-bit, non-prefetchable) [size=16K]
    Region 2: Memory at f2000000 (64-bit, prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, [COLOR=Blue]**ssb**[/COLOR]
Strangely enough, that "[COLOR=Blue]**ssb**[/COLOR]" module is blacklisted in my **/etc/modprobe.d/blacklist.conf** file to use the** wl** module for the proprietary "STA" driver:

> blacklist [COLOR=Blue]**ssb**[/COLOR]
blacklist b44
blacklist b43legacy
blacklist b43


EDIT3:  Here is what **sudo lspci -vvnn** tells me for that "<access denied>" part below "Region 2:" above:

> Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [d0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
            ClockPM+ Suprise+ LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 01-0a-bb-cf-00-00-b8-ff
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, ssb


---

### Post by northd_tech on 2011-08-27
> **northd_tech said:**
> I'm assuming that it is now too late for you to run the following commands with that PCI card installed (because it was already returned, VeeDubb?):

```
lspci -vvnn | grep etwork
lspci -vvnn | grep thern
sudo lshw -C network
lsusb
```
While tagging a bunch of old Netgear WN311B threads with "netgear wn311b," I did manage to find this old **lspci** output for a WN311B (at post #3):

> 02:0a.0 Network controller: Broadcom Corporation [COLOR=Red]**BCM43XG (rev 01)**[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1604297&highlight=netgear+wn311b](http://ubuntuforums.org/showthread.php?t=1604297&highlight=netgear+wn311b)

[COLOR=Red]**That**[/COLOR] no looky like Broadcom "[COLOR=Blue]**4321**[/COLOR]" to me (but a **lspci -vvnn** command would be VERY helpful here)...

Here is the linuxwireless.org "b43" page for reference:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

and the Broadcom "STA" driver page:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

the Ubuntu Broadcom 43xx Documentation page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and the Ubuntu Broadcom "STA" packages for various versions:
[http://packages.ubuntu.com/search?keywords=broadcom&saearchon=names&section=all](http://packages.ubuntu.com/search?keywords=broadcom&saearchon=names&section=all)

EDIT:  Also see the ndiswrapper instructions & shell script at post #3 on this old thread:

[B]new linux user, need help getting wireless setup
[http://ubuntuforums.org/showthread.php?t=1480323](http://ubuntuforums.org/showthread.php?t=1480323)
[/B]

---

### Post by northd_tech on 2011-08-27
> **northd_tech said:**
> ...I did manage to find this old **lspci** output for a WN311B (at post #3):

[http://ubuntuforums.org/showthread.php?t=1604297&highlight=netgear+wn311b](http://ubuntuforums.org/showthread.php?t=1604297&highlight=netgear+wn311b)

[COLOR=Red]**That**[/COLOR] no looky like Broadcom "[COLOR=Blue]**4321**[/COLOR]" to me (but a **lspci -vvnn** command would be VERY helpful here)...
Still digging through old threads, I did find this at post #3 for a **lspci -nn** command:

> 05:09.0 Network controller [0280]: Broadcom Corporation [COLOR=Red]**BCM43XG **[14e4**:4329] (rev 01)**[/COLOR][http://ubuntuforums.org/showthread.php?t=1437701](http://ubuntuforums.org/showthread.php?t=1437701)

Hopefully someone can eventually post the relevant/edited output for a **Netgear WN311G** wireless PCI card for these commands (there will be a TON of output though, and both working and non-working **Netgear WN311G** output could be informative here):

```
sudo lspci -vvnn
sudo lshw -C network
lsmod
modinfo wl
modinfo b43
modinfo ssb
modinfo b44
modinfo b43legacy

```

---

