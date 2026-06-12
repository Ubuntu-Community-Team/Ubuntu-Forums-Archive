---
title: "No network at all after Ubuntu 11.10 upgrade"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by tknobby on 2012-05-19
Upgraded my 11.04 to 11.10 2 days ago.  I have no wired or wireless connection.  Prior to the upgrade I was using a wired set-up which worked flawlwssly.

I have run a few outputs included below:

[ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:72:0d:86:95   
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:72ff:fe0d:8695/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:3742 (3.7 KB)  TX bytes:12907 (12.9 KB) 
          Interrupt:17 Memory:fe3e0000-fe400000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1354 (1.3 KB)  TX bytes:1354 (1.3 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:23:69:dd:0a:ff   
          inet addr:192.168.1.105  Bcast:0.0.0.0  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) ]

[iwconfig wlan0

wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off ]

[iwlist wlan0 scan

 Cell 03 - Address: 00:23:69:7F:67:AB 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=60/70  Signal level=-50 dBm   
                    Encryption key:on 
                    ESSID:"linksys_SES_35732" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000025dceb8189 
                    Extra: Last beacon: 5528ms ago 
                    IE: Unknown: 00116C696E6B7379735F5345535F3335373332 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD06001018020204 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK]

[ishw -C network

*-network                
       description: Ethernet interface 
       product: 82573L Gigabit Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:13:72:0d:86:95 
       size: 100Mbit/s 
       capacity: 1Gbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.4-1 ip=192.168.0.5 latency=0 multicast=yes port=twisted pair speed=100Mbit/s 
       resources: irq:44 memory:fe3e0000-fe3fffff memory:fe400000-fe7fffff ioport:cce0(size=32) 
  *-network 
       description: Wireless interface 
       product: RT2561/RT61 802.11g PCI 
       vendor: Ralink corp. 
       physical id: 2 
       bus info: pci@0000:05:02.0 
       logical name: wlan0 
       version: 00 
       serial: 00:23:69:dd:0a:ff 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci driverversion=3.0.0-19-generic firmware=0.8 ip=192.168.1.105 latency=64 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:18 memory:fe2f8000-fe2fffff ]

Any other data needed to help figure this out?

What is my next step?

Thanks in advance.

Tom...

---

### Post by roelforg on 2012-05-19
The nics are setup fine.
Try pinging 8.8.8.8
I bet it'll work just fine because ubuntu got an ip for both nics just fine.

---

### Post by tknobby on 2012-05-20
> **roelforg said:**
> The nics are setup fine.
Try pinging 8.8.8.8
I bet it'll work just fine because ubuntu got an ip for both nics just fine.

Roelforg,

Tried to ping from network tools in the GUI.  5 packets send but zero returned. 

Next idea?  More data needed?

Tom...

---

### Post by roelforg on 2012-05-22
> **tknobby said:**
> Roelforg,
 
Tried to ping from network tools in the GUI. 5 packets send but zero returned. 
 
Next idea? More data needed?
 
Tom...
 
I meant:
```

ping 8.8.8.8

```
in a terminal (i'm the old-school terminal kind of guy).

---

### Post by tknobby on 2012-05-22
I tried ping from the command line but got no data transmitted. 

Next step?

Thanks,

Tom...

---

### Post by steeldriver on 2012-05-22
try 
```
netstat -r 
```and then see if you can ping the default gateway? also we could check

```
cat /etc/network/interfaces
```

---

### Post by tknobby on 2012-05-22
Here is the output steeldriver,

[netstat -r 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface 
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0 
link-local      *               255.255.0.0     U         0 0          0 wlan0 
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0 
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0 ]


[cat /etc/network/interfaces 
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5). 
 
# The loopback network interface 
auto lo 
iface lo inet loopback 
 
iface eth0 inet dhcp 
 
 
auto eth0 
 
iface wlan0 inet static 
address 192.168.1.105 
netmask 255.255.255.0 
gateway 192.168.1.1 
wpa-psk ******************************************************* 
wpa-driver wext 
wpa-key-mgmt WPA-PSK 
wpa-proto WPA 
wpa-ssid linksys 
 
 
 
 
auto wlan0 ]

Tom...

---

### Post by steeldriver on 2012-05-22
Hi Tom please edit your post to remove/hide your WPA-PSK

Sorry I should have anticipated that

---

### Post by tknobby on 2012-05-22
Here is some more output that might help:


[lspci -nnk | grep -iA2 net 
04:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] (rev 01) 
	Subsystem: Dell Device [1028:01d1] 
	Kernel driver in use: e1000e 
-- 
05:02.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301] 
	Subsystem: Linksys WMP54G ver 4.1 [1737:0055] 
	Kernel driver in use: rt61pci]

[lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub 
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub 
Bus 001 Device 005: ID 1058:0910 Western Digital Technologies, Inc. MyBook Essential External HDD 
Bus 001 Device 006: ID 0781:5406 SanDisk Corp. Cruzer Micro U3 
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard 
Bus 001 Device 007: ID 12f7:1a00 Memorex Products, Inc. TD Classic 003B 
Bus 001 Device 008: ID 05fe:0011 Chic Technology Corp. Browser Mouse]

[lsmod
Module                  Size  Used by 
isofs                  39549  1  
udf                    83826  0  
nls_iso8859_1          12617  3  
nls_cp437              12751  3  
vfat                   17308  3  
fat                    55577  1 vfat 
bnep                   17923  2  
rfcomm                 38408  0  
bluetooth             148869  10 bnep,rfcomm 
parport_pc             32114  0  
ppdev                  12849  0  
dcdbas                 14098  0  
snd_hda_codec_idt      60049  1  
psmouse                73673  0  
serio_raw              12990  0  
snd_hda_intel          24262  2  
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
arc4                   12473  2  
rt61pci                27493  0  
crc_itu_t              12627  2 udf,rt61pci 
rt2x00pci              14202  1 rt61pci 
rt2x00lib              48146  2 rt61pci,rt2x00pci 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec 
usbhid                 41905  0  
hid                    77367  1 usbhid 
snd_seq_midi           13132  0  
mac80211              393421  2 rt2x00pci,rt2x00lib 
snd_rawmidi            25241  1 snd_seq_midi 
binfmt_misc            17292  1  
cfg80211              172427  2 rt2x00lib,mac80211 
eeprom_93cx6           12653  1 rt61pci 
radeon                933705  3  
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
ttm                    65224  1 radeon 
drm_kms_helper         32889  1 radeon 
snd_timer              28932  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
drm                   192194  5 radeon,ttm,drm_kms_helper 
i2c_algo_bit           13199  1 radeon 
soundcore              12600  1 snd 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
lp                     17455  0  
parport                40930  3 parport_pc,ppdev,lp 
usb_storage            44172  6  
uas                    17699  0  
ahci                   21634  2  
libahci                25727  1 ahci 
e1000e                139814  0  
floppy                 60310  0]

[ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:13:72:0d:86:95   
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::213:72ff:fe0d:8695/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:4694 (4.6 KB)  TX bytes:13843 (13.8 KB) 
          Interrupt:17 Memory:fe3e0000-fe400000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1442 (1.4 KB)  TX bytes:1442 (1.4 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:23:69:dd:0a:ff   
          inet addr:192.168.1.105  Bcast:0.0.0.0  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)]

[iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off]


Tom...

---

### Post by steeldriver on 2012-05-22
Hi Tom you have quite a complicated setup there - e.g. your wired interface is on 192.168.0.xxx subnet while your wireless is on 192.168.1.xxx

Since you're troubleshooting the wired interface, you should try pinging 192.168.**0**.1

BTW do you also have NetworkManager installed / running? I thought that was the default these days, in fact I was expecting your /etc/network/interfaces to only contain the loopback interface

```
ps -ef | grep NetworkManager
```If so things might be conflicting

---

### Post by tknobby on 2012-05-22
I am not sure.  I am on my XP boot right now so I can access this forum.  I'll run the next output in just a bit and let you know.

I am troubleshooting both wired and wireless.  I have neither.

Tom...

---

### Post by steeldriver on 2012-05-22
How about you have a look at the router/gateway ip while you are in XP

Start --> Run --> cmd.exe

then

```
ipconfig /a
```

This will give you something to go on when you are back in *nix

---

### Post by tknobby on 2012-05-22
steeldriver,

Here is the XP output:

[ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : DGCWKF91
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : satx.rr.com
                                            satx.rr.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : satx.rr.com
        Description . . . . . . . . . . . : Intel(R) PRO/1000 PL Network Connect
ion
        Physical Address. . . . . . . . . : 00-13-72-0D-86-95
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.0.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1
        DHCP Server . . . . . . . . . . . : 192.168.0.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Tuesday, May 22, 2012 7:08:29 PM
        Lease Expires . . . . . . . . . . : Friday, May 25, 2012 7:08:29 PM

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : satx.rr.com
        Description . . . . . . . . . . . : Linksys Wireless-G PCI Adapter
        Physical Address. . . . . . . . . : 00-23-69-DD-0A-FF
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.104
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.0.1
        Lease Obtained. . . . . . . . . . : Tuesday, May 22, 2012 7:09:55 PM
        Lease Expires . . . . . . . . . . : Wednesday, May 23, 2012 7:09:55 PM]

And here is the *nix output:

[ps -ef | grep NetworkManager 
root       616     1  0 18:11 ?        00:00:00 NetworkManager 
tom       2237  2183  0 19:04 pts/0    00:00:00 grep --color=auto NetworkManager ]

BTW, how do I get this code into the "codebox"?

Tom...

---

### Post by tknobby on 2012-05-22
And when I did ping to the 192.168.0.1 I get 64 bytes received.

Tom...

---

### Post by tknobby on 2012-05-23
Any more ideas?  I really don't want to be stuck w/ XP.

Tom...

---

### Post by steeldriver on 2012-05-23
was the successful ping  192.168.0.1 from Windows or Linux?

---

### Post by tknobby on 2012-05-23
The ping was in *nix.  The network works fine in XP on both wired and wireless.

---

### Post by steeldriver on 2012-05-23
> **tknobby said:**
> The ping was in *nix.  The network works fine in XP on both wired and wireless.

OK well that's encouraging - at least we know packets are getting as far as your router / gateway - but you still can't ping 8.8.8.8 right?

To see if they get any further, you could try

```
$ tracepath 8.8.8.8
```

(you can Ctrl-C to stop it once the hops stop being interesting)

---

### Post by tknobby on 2012-05-23
Do I use the dollar sign too?

---

### Post by steeldriver on 2012-05-23
sorry - no that's just the shell prompt - just

```
ping 8.8.8.8

tracepath 8.8.8.8
```

---

### Post by tknobby on 2012-05-23
1:  ubuntu.local.       0.164ms pmtu 1500
1:  ubuntu.local.        3100.99s  !H
Resume: pmtu 1500


The ping to 8.8.8.8 shows destination unreachable


Tom...

---

### Post by steeldriver on 2012-05-23
Hi Tom, I think I misread your route output earlier, it actually looks like you are NOT getting a gateway address for the subnet that eth0 is picking up (so your tracepath is just showing localhost - your Linux hostname is 'ubuntu'?)

[B]Frankly I'm in over my head here, I can only tell you what I would do next if it was my machine so please take it with a grain or two of salt
[/B] 
I have heard that NetworkManager does not always play nicely with traditional ifupdown stuff specified in /etc/network/interfaces (it *should* work, so long as they agree about 'unmanaging' each others interfaces, but still... ). We could try to troubleshoot that but the quickest thing to try would be simply to disable one or other method. The two possibilities are:

1. disable NetworkManager and revert to just the settings in /etc/network/interfaces

[I]I don't know an elegant way to do this permanently, short of apt-get remove network-manager - this should work until reboot
[/I] 
a) stop network-manager

```
sudo service network-manager stop
```b) bring  both interfaces down and then (for now) just bring eth0 back up
```

sudo ifconfig eth0 down
sudo ifconfig wlan0 down

sudo ifconfig eth0 up

```2. [MY PREFERRED] hand everything over to NetworkManager, as follows:

a) stop network-manager and make sure both interfaces started by ifconfig are down

```
sudo service network-manager stop
sudo ifconfig eth0 down
sudo ifconfig wlan0 down

```b) back up your /etc/network/interfaces file:

```
sudo cp -p /etc/network/interfaces /etc/network/interfaces.old

```c) edit /etc/network/interfaces so it contains ONLY the loopback interface 

```
gksudo gedit /etc/network/interfaces

```then delete everything except

```
auto lo
iface lo inet loopback

```d) restart network-manager

```
sudo service network-manager start
```You can easily revert all this later using the backup copy of /etc/network/interfaces. If it works you should get a default auto-configured wired connection  (called 'Wired connection 1' in the NM applet) - we can then set up a  wireless connection using the credentials saved in the interfaces.old  file.

---

### Post by tknobby on 2012-05-23
I will give this a whirl.  Nothing else has made any sense.

I'll let you know in a bit...

---

### Post by tknobby on 2012-05-23
steeldriver

You are not over your head... the wired network is now online.  I rebooted the system and am now on *nix on this forum.

Thank you very much for taking the time to help.

Now I need to see if the wireless is alive.

Tom...

---

