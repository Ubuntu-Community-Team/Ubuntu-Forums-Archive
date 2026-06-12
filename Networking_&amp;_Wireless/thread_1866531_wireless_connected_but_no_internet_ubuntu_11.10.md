---
title: "wireless connected but no internet ubuntu 11.10"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by aljsk8 on 2011-10-21
Good evening

I have been on wired broadband for years (virgin cable)
i got them to send me a wireless router (D-Link DIR-615)

hooked it all up and it connects (i can see it connected in the network settings)

but i cant connect to the Internet - with firefox or chrome

I can plug the modem in wired (its a separate cable modem) and get on the Internet fine
I can also get into the router settings by typing in some numbers in the address bar - ive been through the basic setting wizard but that's not helped.

I dont think its specificly ubuntu 11.10 problem but thats what ive got when i got the router - but ive never had wireless before and ive been using ubuntu since version 8.

ive looked at the page that tells me all the info I need to gather to help solve this problem - so ive saved what i can in a text file but there is a lot there so it might be better if you ask for things individually

i can follow instructions but ive never needed to get into the nitty gritty of linux and i have zero experience with wireless

in summary the computer and router are connected wirelessly but the Internet will not connect - the internet is working ok when its a wired connection

so can anybody help?

thanks in advance!

---

### Post by lightwarrior on 2011-10-21
Well, on any Wifi connection, you begin by selecting your Wifi network and click to connect.  If you see several networks, be sure you know the name of your wifi.  You may see yours, but if you don't select it, it will not connect.

---

### Post by aljsk8 on 2011-10-21
hi - thanks for the reply

my wireless is set to connect automaticly and it does - the wireless is connected - if I got in the network manager it show my router called d-link and tells me im connected to it

see the screenshot attached

my problem is it wont connect to the Internet.

---

### Post by aljsk8 on 2011-10-22
Below is all the information asked for in the thread starter instructions
if its not in the list its because the command didn't work or didn't return anything

hope this helps


aljsk8@AJ:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
aljsk8@AJ:~$ 


aljsk8@AJ:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable Modem
Bus 002 Device 004: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
aljsk8@AJ:~$ 


aljsk8@AJ:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:41:bb:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:0f:9f:c7:13:0a  
          inet addr:92.239.86.206  Bcast:92.239.87.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:9fff:fec7:130a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3088942 (3.0 MB)  TX bytes:544854 (544.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 18:f4:6a:ab:fd:01  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1af4:6aff:feab:fd01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:428751 (428.7 KB)  TX bytes:186719 (186.7 KB)

aljsk8@AJ:~$ 


aljsk8@AJ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:D6:4D:76:78:6A   
          Bit Rate=144.4 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

aljsk8@AJ:~$ 
aljsk8@AJ:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
arc4                   12473  2 
cdc_ether              13312  0 
usbnet                 25214  1 cdc_ether
snd_hda_intel          28358  1 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
snd                    55902  12 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  2 brcmsmac,mac80211
psmouse                63474  0 
serio_raw              12990  0 
i915                  505143  8 
intel_ips              17753  0 
crc_ccitt              12595  1 brcmsmac
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
drm                   196322  4 i915,drm_kms_helper
mei                    36466  0 
i2c_algo_bit           13199  1 i915
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
mxm_wmi                12859  0 
wmi                    18744  2 acer_wmi,mxm_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
hid                    77367  1 usbhid
uas                    17699  0 
ahci                   21634  3 
libahci                25761  1 ahci
tg3                   132972  0 
aljsk8@AJ:~$ 

aljsk8@AJ:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 14:D6:4D:76:78:6A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a137e166
                    Extra: Last beacon: 24568ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606070100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406070100000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001011041000100103B00010310470010F35A8D59B491EC5DD25A14D64D76786A10210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086

eth1      Interface doesn't support scanning.

---

### Post by lightwarrior on 2011-10-22
It seems your wifi is fine.

I think the problem is at the internet modem or DNS.

Before digging further you can try the following:

Power off modem/D-link, wait 30 seconds.  Power on.  Let those get a new IP/DNS data from your ISP.

Try reconnecting again.

If this doesn't work, try hooking via a wire to see if you have internet via wire.

Try pinging 8.8.8.8 it is a DNS server.  If it fails, then you don't have internet at all, call your ISP.

---

### Post by varunendra on 2011-10-22
When you are able to connect to internet (via eth), please run the following commands and post their outputs:
```
ifconfig
route -n
cat /etc/resolv.conf

```
Then disconnect the wired connection, get connected via wireless, enter and post outputs of the same above commands.

Do you connect via a DSL connection (requires ID-Password, saved in Network Manager) or a normal 'Wired' connection (plug-n-play type) in Network Manager?

---

### Post by aljsk8 on 2011-10-22
hi there - thanks for the replies

i have Internet via a usb cable to the (Motorola surfboard) modem and that's how im connected now

im not sure what all these three letter abriviations meam but my cable comes through the wall then plugs into my modem via a chunky round cable then usb cable out of my modem into my pc - i dont need any passwords its just always on

the wireless router is then plugged into the modem via a phone type cable I think that's Ethernet or something

if i take the usb cable out it does say im connected to the router but wont connect to the Internet

interestingly my friend came round to have a look his ipad also couldn't connect and my android phone cant connect although both the phone and ipad can connect to the router

with the Internet on - through the wire - I get the following (it seams the last bit is just flashing with no response)

aljsk8@AJ:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:41:bb:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:0f:9f:c7:13:0a  
          inet addr:92.239.86.206  Bcast:92.239.87.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:9fff:fec7:130a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255142738 (255.1 MB)  TX bytes:7184748 (7.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33712 (33.7 KB)  TX bytes:33712 (33.7 KB)

wlan0     Link encap:Ethernet  HWaddr 18:f4:6a:ab:fd:01  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1af4:6aff:feab:fd01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4336134 (4.3 MB)  TX bytes:1036282 (1.0 MB)

aljsk8@AJ:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         92.239.84.1     0.0.0.0         UG    0      0        0 eth1
92.239.84.0     0.0.0.0         255.255.252.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
aljsk8@AJ:~$ cat /etc/resolv.conf


with the Internet off - connected through the wireless router I get this... (again resolv is just flashing)


aljsk8@AJ:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:41:bb:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33712 (33.7 KB)  TX bytes:33712 (33.7 KB)

wlan0     Link encap:Ethernet  HWaddr 18:f4:6a:ab:fd:01  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1af4:6aff:feab:fd01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4350162 (4.3 MB)  TX bytes:1045714 (1.0 MB)

aljsk8@AJ:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
aljsk8@AJ:~$ cat /etc/resolv.conf


to me the fact that the ipad the phone and the laptop are all getting the same issue suggests its not a Linux / computer issue

so what next?

ive tried resetting everything with no joy
ive no idea how to ping?

thanks again

---

### Post by aljsk8 on 2011-10-22
this screen-shot may be of use

---

### Post by aljsk8 on 2011-10-23
unplugged everything
plugged in and turned on modem then router then pc

all working now!

---

