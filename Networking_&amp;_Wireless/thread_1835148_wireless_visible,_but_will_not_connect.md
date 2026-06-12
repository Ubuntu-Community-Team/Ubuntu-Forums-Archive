---
title: "wireless visible, but will not connect"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by cptnjarhead on 2011-08-28
ubuntu 10.04
inspiron 8200 laptop
problem: my linksys wireless shows available but it will not connect.
wired connection works fine.
i have read way to many post all leading in diff directions. now im confused.
-
damon@damon-laptop:~$ sudo iwconfig
[sudo] password for damon: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=54/70  Signal level=-48 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-
damon@damon-laptop:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3d:af:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x  duplex=full ip=192.168.1.103 latency=32 link=yes maxlatency=10 mingnt=10  multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:eb:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15  firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b
damon@damon-laptop:~$ 


hope this helps.
thank you in advance

---

### Post by cptnjarhead on 2011-08-29
It seems like it just times out. tried a clean install and same thing. I did have xp running on the laptop and the wire less works perfectly. I know the wireless works because if i enter the wrong password it will let me know the password was incorrect. 
My wireless router is a lynksys wrt54g. 
thanks again in advance

---

### Post by wildmanne39 on 2011-08-29
Hi. run these commands please and post the results here:
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
dmesg | grep ori
```
```
lsmod | grep ori
```
Thank you

---

### Post by praseodym on 2011-08-29
Hi,

this

```
eth1 IEEE 802.11b ESSID:"[COLOR="Magenta"]f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0 E\x82tA!=\xDC\x87[/COLOR]" 
```
looks like a hidden network you want to connect to. Hiding ESSIDs is no security advantage (but also no disadvantage) but it can make problems in Ubuntu. Can you try to "broadcast" your ESSID in your router interface?

---

### Post by cptnjarhead on 2011-08-29
> **wildmanne39 said:**
> Hi. run these commands please and post the results here:
```
sudo lshw -C network
``````
lspci -nn | grep 0280
``````
iwconfig
``````
rfkill list all
``````
dmesg | grep ori
``````
lsmod | grep ori
```Thank you

thank you for your response
here you go

  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3d:af:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:eb:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b

lspci -nn | grep 0280 
did nothing? 

damon@damon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:";pd$\x11\x9E\x09\xDC\xAA\xD4\xAC\xF2\x1B\x10\xAF;3\xCD\xE3PHG\x15\\xBBo"\x19\xBA\x9B}\xF5"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-41 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


damon@damon-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


damon@damon-laptop:~$ dmesg | grep ori
[   13.163649] Adding 3005432k swap on /dev/sda5.  Priority:-1 extents:1 across:3005432k 
[   16.870138] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   16.883962] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   16.967082] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   16.967208] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   16.967215] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   17.020353] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   17.161317] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   17.161443] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   17.161449] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   17.161454] orinoco_cs 2.0: Ad-hoc demo mode supported
[   17.161459] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   17.161463] orinoco_cs 2.0: WEP supported, 104-bit key
[   17.161467] orinoco_cs 2.0: WPA-PSK supported


damon@damon-laptop:~$ lsmod | grep ori
orinoco_cs              8782  1 
orinoco                62842  1 orinoco_cs
cfg80211              126144  1 orinoco
pcmcia                 30784  1 orinoco_cs
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by northd_tech on 2011-08-29
If I recall correctly, an "Inspiron" is a somewhat older Dell series.  I seem to recall some Dell laptops having wireless conflicts with the dell 'laptop key' drivers for the volume, wireless 'soft key,' CD/DVD player, power management, etc.  I remember reading that one (or several) Dell laptop modules needed to be blacklisted in /etc/modprobe.d/blacklist.conf to get wireless working properly on certain Dell laptops.

Ubuntuforums member Chili555 is probably the guy to talk to about those- I think he has helped fix many Dell laptops for many people here and might know the 'problem' module names to look for.  I know that the little Dell laptop that I once used at a previous employer was a pretty 'bulletproof' little machine (but unfortunately it ran Windows XP only *per* our company's IT guy's mandate).

It would be a good idea to post the complete results of this terminal command again to see if there are possibly any of these 'laptop' modules interfering with your wireless:

```
lsmod
```

---

### Post by cptnjarhead on 2011-08-29
> **northd_tech said:**
> If I recall correctly, an "Inspiron" is a somewhat older Dell series.  I seem to recall some Dell laptops having wireless conflicts with the dell 'laptop key' drivers for the volume, wireless 'soft key,' CD/DVD player, power management, etc.  I remember reading that one (or several) Dell laptop modules needed to be blacklisted in /etc/modprobe.d/blacklist.conf to get wireless working properly on certain Dell laptops.

Ubuntuforums member Chili555 is probably the guy to talk to about those- I think he has helped fix many Dell laptops for many people here and might know the 'problem' module names to look for.  I know that the little Dell laptop that I once used at a previous employer was a pretty 'bulletproof' little machine (but unfortunately it ran Windows XP only *per* our company's IT guy's mandate).

It would be a good idea to post the complete results of this terminal command again to see if there are possibly any of these 'laptop' modules interfering with your wireless:

```
lsmod
```

thank you for your response

damon@damon-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
michael_mic             1732  4 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
orinoco_cs              8782  1 
orinoco                62842  1 orinoco_cs
cfg80211              126144  1 orinoco
ch7006                 16373  1 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 30784  1 orinoco_cs
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
joydev                  8740  0 
ttm                    50103  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  2 ch7006,nouveau
yenta_socket           20408  5 
dell_wmi                1793  0 
drm                   162377  5 ch7006,nouveau,ttm,drm_kms_helper
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5422  0 
i2c_algo_bit            5028  1 nouveau
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24375  1 
soundcore               6620  1 snd
psmouse                63677  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_rng               2276  0 
agpgart                31724  3 ttm,drm,intel_agp
shpchp                 28835  0 
ppdev                   5259  0 
video                  17375  0 
output                  1871  1 video
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
3c59x                  31839  0 
usb_storage            39841  1 
mii                     4381  1 3c59x
ieee1394               81181  1 ohci1394
floppy                 53016  0

---

### Post by northd_tech on 2011-08-29
> **cptnjarhead said:**
> thank you for your response

damon@damon-laptop:~$ lsmod
Module                  Size  Used by
**dell_wmi**                1793  0 

That "**dell_wmi**" is the module that my 'suspicious eye' is looking at from what I remember reading, and according to this Japanese **dell_wmi** source header page, that is the Dell "hotkey" library/driver, and it does have a WLAN wireless radio control setting:

[http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/platform/x86/dell-wmi.c](http://tomoyo.sourceforge.jp/cgi-bin/lxr/source/drivers/platform/x86/dell-wmi.c)
> ***/**** [B][I] * Dell WMI hotkeys
...
[/I][/B] 69         ***/* This is actually for all *[COLOR=Red][wireless WLAN][/COLOR]***** radios. Although physically a***  
70 ***         * switch, the notification does not provide an indication of***  
71 [B][I]         * state and so it should be reported as a key 
    */[/I][/B]  72         { [KE_KEY]("http://tomoyo.sourceforge.jp/cgi-bin/lxr/ident?i=KE_KEY"), 0xe008, { [KEY_WLAN]("http://tomoyo.sourceforge.jp/cgi-bin/lxr/ident?i=KEY_WLAN") } },
I'm not sure what the **proper** workaround/fix is though, so I'm a little hesitant to recommend blacklisting that **dell_wmi** module just yet, since it might "break" some other hotkey stuff that you might prefer to have under Ubuntu, too.

Here is a blog that describes what I'm thinking of, but it looks like the module "[COLOR=Blue]**dell_laptop**[/COLOR]" was the problem child (blocking the wireless WLAN radio "switch" function) in that case:

Hard blocked wireless kill-switch on Dell laptop
[http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/](http://linuxtrap.wordpress.com/2009/11/25/hard-blocked-wireless-kill-switch-on-dell-laptop/)

---

### Post by wildmanne39 on 2011-08-29
Hi this 
> rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
shows no blocks that is what northd_tech is refering too. Chili is the one I am learning most things from including that.

Did you unhide your network as mentioned by praseodym?

Also please post the results of:
```
sudo pccardctl ident
```
```
sudo iwlist scan
```
```
nm-tool
```
```
dmesg | grep -i -e warn -e error
```
Also there has been problems with the driver you are using and we may need to change it but I need the information I asked for first.
Thank you

---

### Post by northd_tech on 2011-08-29
> **cptnjarhead said:**
> 
  *-network
       description: **TrueMobile 1150 Series PC Card**
       product: Version 01.01
       **vendor: Dell**
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:eb:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes **driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 [COLOR=Red]link=yes[/COLOR]** multicast=yes [COLOR=Red]**wireless=IEEE 802.11b**[/COLOR]

[B]lspci -nn | grep 0280 
did nothing? [/B]

damon@damon-laptop:~$ iwconfig
eth1      [COLOR=Green]**IEEE 802.11b  ESSID:";pd$\x11\x9E\x09\xDC\xAA\xD4\xAC\xF2\x1B\x10\xAF;3\xCD\xE3PHG\x15\\xBBo"\x19\xBA\x9B}\xF5"  **[/COLOR]
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          [COLOR=Green]**Bit Rate:11 Mb/s**[/COLOR]   Sensitivity:1/0  
          Retry limit:8   RTS thr: off   Fragment thr: off
          Power Management: off
          [COLOR=Green]**Link Quality=61/70**[/COLOR]  Signal level=-41 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


damon@damon-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


damon@damon-laptop:~$ dmesg | grep ori
[   16.870138] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   16.883962] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   16.967082] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   16.967208] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   16.967215] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   17.020353] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   17.161317] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   17.161443] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   17.161449] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   17.161454] orinoco_cs 2.0: Ad-hoc demo mode supported
[   17.161459] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   17.161463] orinoco_cs 2.0: WEP supported, 104-bit key
[   17.161467] orinoco_cs 2.0: WPA-PSK supported


damon@damon-laptop:~$ lsmod | grep ori
orinoco_cs              8782  1 
orinoco                62842  1 orinoco_cs
cfg80211              126144  1 orinoco
pcmcia                 30784  1 orinoco_cs
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

Are we certain that the orinoco is the correct driver (**and Lucent firmware?**) for a Dell **TrueMobile 1150 Series PC Card** wireless interface?  Also the[COLOR=Red] red[/COLOR] and [COLOR=Green]green[/COLOR] parts that I linked above look like there is a wireless link [at least partially] established (although it looks like there is some curious 'hidden' SSID or some wireless authentication issues going on).

Can you post the output of the following 2 termnal commands (since the **lspci | grep 0280** command apparently did nothing)?

```
lspci -vvnn | egrep 'etwork|ireless|thernet'
lsusb
```I believe that some of the newer and/or more obscure wireless interfaces sometimes 'hook' a USB interface rather than (or else along with) a PCI interface, and sometimes you get some strange 'hybrid' wireless setups once in a while.  That output of **sudo lswh -C network** above looks a little strange to me with the multiple '*-network" entries...

Also, it might be worth Cpt. Jarhead reading this thread (this is where Chili, I, and others were having 'fun' with all the **rfkill** and hardware/software blocks a few months ago):

[B]wireless is disabled by hardware switch  - natty 11.04
[http://ubuntuforums.org/showthread.php?t=1745681](http://ubuntuforums.org/showthread.php?t=1745681)
 [/B]Off-topic- does the "cptnjarhead" username have a USMC significance?  (I've got a close relative who was in the 22MEU in Afghanistan and who the Pentagon/JTF stationed at GITMO for a while, but he's discharged now.  He was usually 'on loan' to the Pentagon/JTF, USN, or some different USMC unit or battalion though).

---

### Post by wildmanne39 on 2011-08-29
Hi northd_tech, this command I asked for should tell us the card it is a pcmcia card that is why that other command did not work.
```
sudo pccardctl ident
```

---

### Post by northd_tech on 2011-08-29
Ah, those PC/MCIA cards mostly pre-date my Ubuntu days (and they were pretty much a lost cause back in the Slackware/Red Hat days from what I remember).  Back then, it wasn't all that easy to get a PCI Ethernet card working under Linux on a "standard" Desktop PC, if I remember correctly through all those cobwebs. ;)

As many hassles as there are with the various newer USB interfaces, they're much easier than PC/MCIA aren't they?

---

### Post by wildmanne39 on 2011-08-29
Hi, very true! I have only run across two of them recently including this one.

I actually have one myself but I have not used it in at least 5 years.

The driver he is using is known to have issues also, so we will have to wait and see what information he provides so he can see his card.

If his driver is correct it should be a prism card.

---

### Post by cptnjarhead on 2011-08-29
thanks alot for the help, i am new to linux/ubunu and i appreciate your help very much.

damon@damon-laptop:~$ sudo pccardctl ident
[sudo] password for damon: 
Socket 0:
  no product info available
Socket 1:
  no product info available
Socket 2:
  product info: "Dell", "TrueMobile 1150 Series PC Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)



damon@damon-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 68:7F:74:C2:D3:B8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e304c046
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020104
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


damon@damon-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            3c59x
  State:             connected
  Default:           yes
  HW Address:        00:08:74:3D:AF:BB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.247.24.53
    DNS:             24.247.15.53


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:6E:EB:90

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    linksys:         Infra, 68:7F:74:C2:D3:B8, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA


damon@damon-laptop:~$ dmesg | grep -i -e warn -e error
returned nothing?

---

### Post by cptnjarhead on 2011-08-29
[LEFT]thanks again
[/LEFT]


damon@damon-laptop:~$ lspci -vvnn | egrep 'etwork|ireless|thernet'
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
damon@damon-laptop:~$ lsusb
Bus 002 Device 002: ID 03f0:3307 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
damon@damon-laptop:~$ 

damon@damon-laptop:~$ sudo pccardctl ident
[sudo] password for damon: 
Socket 0:
  no product info available
Socket 1:
  no product info available
Socket 2:
  product info: "Dell", "TrueMobile 1150 Series PC Card", "Version 01.01", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)
damon@damon-laptop:~$

---

### Post by wildmanne39 on 2011-08-29
Hi, you are trying to connect to the network called linksys correct?

You made your network visible also correct?

Please run these commands and post the results.
```
dmesg | grep eth1
```
Thank you

---

### Post by cptnjarhead on 2011-08-30
Thanks again!



> **wildmanne39 said:**
> Hi, you are trying to connect to the network called linksys correct?

You made your network visible also correct?

Please run these commands and post the results.
```
dmesg | grep eth1
```Thank you

---[B]yes, linksys is the default name, i only changed default password.
my network is not hidden.[/B]----

damon@damon-laptop:~$ dmesg | grep eth1
[   80.281233] eth1: Lucent/Agere firmware doesn't support manual roaming
[   80.510290] eth1: New link status: Connected (0001)
[  395.636079] eth1: Lucent/Agere firmware doesn't support manual roaming
[  395.765134] eth1: New link status: Connected (0001)
[21226.484103] eth1: Lucent/Agere firmware doesn't support manual roaming
[21230.590515] eth1: New link status: Disconnected (0002)
[21231.813271] eth1: New link status: Connected (0001)
[21249.191562] eth1: Lucent/Agere firmware doesn't support manual roaming
[21300.011381] eth1: New link status: Disconnected (0002)
[21374.164065] eth1: Lucent/Agere firmware doesn't support manual roaming
[21374.343261] eth1: New link status: Connected (0001)
[21957.068063] eth1: Lucent/Agere firmware doesn't support manual roaming
[21957.222433] eth1: New link status: Connected (0001)
damon@damon-laptop:~$

---

### Post by wildmanne39 on 2011-08-30
Hi, I have been researching this issue and one fix was is to install wicd, you can do that by opening synaptic and type wicd into the search box then click on install and apply.

Then uninstall network manager in synaptic, then see if you can connect to your network. 

Try it with encryption off then turn encryption on. 
Thank you

---

### Post by cptnjarhead on 2011-08-30
[QUOTE=Off-topic- does the "cptnjarhead" username have a USMC significance?  (I've got a close relative who was in the 22MEU in Afghanistan and who the Pentagon/JTF stationed at GITMO for a while, but he's discharged now.  He was usually 'on loan' to the Pentagon/JTF, USN, or some different USMC unit or battalion though).[/QUOTE]

sorry didnt see that till just now.
Yes, when i was in boot camp my cousin sent me a letter:
addressed "To: **Captain** Damon Hendrickson"
well as you can guess, my DI's didnt think it was funny, not only did they PT the **** out of me, they called me "**captain jarhead**" all through boot camp. My cousin still laughs about it till this day.
so that name just stuck with me.
thanks again for the help

i was 1394 8th engineers "easy money" by the way.

---

### Post by cptnjarhead on 2011-08-30
> **wildmanne39 said:**
> Hi, I have been researching this issue and one fix was is to install wicd, you can do that by opening synaptic and type wicd into the search box then click on install and apply.

Then uninstall network manager in synaptic, then see if you can connect to your network. 

Try it with encryption off then turn encryption on. 
Thank you

Sweet! i will give-er a go

thanks again

---

### Post by wildmanne39 on 2011-08-30
Hi, Your welcome! Your system is very close to connecting, if that does not work we will move on to the next step.

---

### Post by cptnjarhead on 2011-08-30
> **wildmanne39 said:**
> Hi, Your welcome! Your system is very close to connecting, if that does not work we will move on to the next step.

very close, now im getting bad password. I have entered it several times, i know its correct.
hmmm.

---

### Post by wildmanne39 on 2011-08-30
Ok, I saw a fix for it give me a few minutes to look it up.

---

### Post by northd_tech on 2011-08-30
> **wildmanne39 said:**
> Ok, I saw a fix for it give me a few minutes to look it up.
Was it this one maybe? ;)

**wicd wpa_supplicant "bad password" problem & workaround (wireless connection)**
[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

Or maybe one of these?
[http://ubuntuforums.org/tags.php?tag=bad+password](http://ubuntuforums.org/tags.php?tag=bad+password)

---

### Post by wildmanne39 on 2011-08-30
Hi, try this:
```
gksu gedit /etc/network/interfaces
```
then change to this
```
auto eth1
iface eth1 inet dhcp
wireless yes
wireless-mode managed
wireless-essid youressid
wireless-key restricted yourhexkey
```
change the SSID to your SSID
and myhexkey to your router password.

If this does not work change it back to the way it was before you changed it.

---

### Post by cptnjarhead on 2011-08-30
> **wildmanne39 said:**
> Hi, try this:
```
gksu gedit /etc/network/interfaces
```
then change to this
```
auto eth1
iface eth1 inet dhcp
wireless yes
wireless-mode managed
wireless-essid youressid
wireless-key restricted yourhexkey
```
change the SSID to your SSID
and myhexkey to your router password.

If this does not work change it back to the way it was before you changed it.

on it!

---

### Post by cptnjarhead on 2011-08-30
nope :(

---

### Post by wildmanne39 on 2011-08-30
Hi, did you change it back? run these commands please:
```
dmesg | grep ori
```
```
dmesg | egrep 'ori|firm'
```
```
dmesg | grep eth1
```
Thank you

---

### Post by cptnjarhead on 2011-08-30
> **wildmanne39 said:**
> Hi, did you change it back? run these commands please:
```
dmesg | grep ori
```
```
dmesg | egrep 'ori|firm'
```
```
dmesg | grep eth1
```
Thank you

yes,  i have to connect lan and cut-n-paste
on desktop right now brb

---

### Post by wildmanne39 on 2011-08-30
Hi northd_tech, I looked at this, it is based on his error message before the bad password and there is another fix for it, it seems it has to do with the new firmware for his driver.

I posted this several minutes ago and just realized I posted it in the wrong thread.

I guess that is what happens when you a  have a slight headache.
[http://ubuntuforums.org/archive/inde...t-1257291.html](http://ubuntuforums.org/archive/inde...t-1257291.html)

---

### Post by cptnjarhead on 2011-08-30
> **wildmanne39 said:**
> Hi, did you change it back? run these commands please:
```
dmesg | grep ori
``````
dmesg | egrep 'ori|firm'
``````
dmesg | grep eth1
```Thank you

here ya go

damon@damon-laptop:~$ dmesg | grep ori
[   14.827641] Adding 3005432k swap on /dev/sda5.  Priority:-1 extents:1 across:3005432k 
[   19.469835] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.485219] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.567026] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.567150] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   19.567157] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   19.696060] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   19.821826] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.821952] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   19.821959] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   19.821964] orinoco_cs 2.0: Ad-hoc demo mode supported
[   19.821969] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   19.821973] orinoco_cs 2.0: WEP supported, 104-bit key
[   19.821977] orinoco_cs 2.0: WPA-PSK supported
damon@damon-laptop:~$ dmesg | egrep 'ori|firm'
[   14.827641] Adding 3005432k swap on /dev/sda5.  Priority:-1 extents:1 across:3005432k 
[   19.469835] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.485219] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   19.567026] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.567150] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   19.567157] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   19.696060] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   19.821826] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.821952] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   19.821959] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   19.821964] orinoco_cs 2.0: Ad-hoc demo mode supported
[   19.821969] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   19.821973] orinoco_cs 2.0: WEP supported, 104-bit key
[   19.821977] orinoco_cs 2.0: WPA-PSK supported
damon@damon-laptop:~$ dmesg | grep eth1
damon@damon-laptop:~$ dmesg | grep eth1
damon@damon-laptop:~$
--did nothing?

---

### Post by northd_tech on 2011-08-30
How about running these commands again Cpt.?

```
ifconfig
sudo lshw -C network
```
(To see if we have changed anything in your configuration(s), and apparently "eth1" is no longer your wireless interface "label" from what I'm reading above)

---

### Post by wildmanne39 on 2011-08-30
Hi, something changed run this please:
```
sudo iwlist scan
```
```
cat /etc/network/interfaces
```
post all results here.
Thank you

---

### Post by cptnjarhead on 2011-08-30
crap, now the rig is locking up, no mouse or keyboard.
re-booted couple of times, same thing. 
could go back to XP and take the easy way out, but that aint in my
nature! I am way to stubborn.
Gentlemen I need to get some shuteye, got work at 5:00am 
will check back with ya tomorrow and run those commands, if this rig will stay alive long enough.
thanks again guys, see ya tomorrow :)

---

### Post by wildmanne39 on 2011-08-30
Hi, ok if we need to I will get a friend to help us out.

---

### Post by northd_tech on 2011-08-31
> **cptnjarhead said:**
> crap, now the rig is locking up, no mouse or keyboard.
re-booted couple of times, same thing. 

If it won't boot Ubuntu for you *en la manana o tarde*, I trust that you have a LiveCD/DVD or LiveUSB from your original install?  (That will usually get a "locked" Ubuntu to talk you you again- after a good night's sleep with* you on the couch/floor* and *your laptop in the comfy bed*.... ;) )

If you don't have a "live" CD/DVD/USB mentioned above- I'd consider trying the "old" Ubuntu 10.04 LTS (meaning Long Term Support) live CD/DVD.  The LTS versions don't have nearly so many (or nearly **so drastic**) changes to the kernel & wireless module interfaces- and I've been watching the Ubuntu "upgrades?" since about 8.04 or so.  [Just my personal opinion here though...]

---

### Post by cptnjarhead on 2011-08-31
i'm back and ready for more!

okay, clean install with ubuntu 10.04 LTS (same version as before but this time i have not updated or installed anything except wicd)

installed wicd
un-installed network manager
tried to connect:[B] input password
-connection failed[/B]: [B]unable to get ip address

i think this is better? 

starting over -
[/B]
damon@damon-laptop:~$ sudo lshw -C network
[sudo] password for damon: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3d:af:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6e:eb:90
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
damon@damon-laptop:~$ lspci -nn | grep 0280
damon@damon-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
damon@damon-laptop:~$ dmesg | grep ori
[    4.774551] Adding 3005432k swap on /dev/sda5.  Priority:-1 extents:1 across:3005432k 
[    9.169791] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[    9.229547] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[    9.311350] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[    9.311475] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[    9.311481] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[    9.341153] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[    9.794925] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[    9.795052] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[    9.795059] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[    9.795064] orinoco_cs 2.0: Ad-hoc demo mode supported
[    9.795068] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[    9.795073] orinoco_cs 2.0: WEP supported, 104-bit key
[    9.795077] orinoco_cs 2.0: WPA-PSK supported
damon@damon-laptop:~$ lsmod | grep ori
orinoco_cs              8782  1 
orinoco                62842  1 orinoco_cs
cfg80211              126144  1 orinoco
pcmcia                 30784  1 orinoco_cs
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
damon@damon-laptop:~$

---

### Post by wildmanne39 on 2011-08-31
Hi, lets get to it then:

Run this then disconnect your wired and restart your computer.
```
sudo apt-get purge network-manager network-manager-gnome
```
that command should make sure no part of network manager is installed, sometimes not all of it is removed without getting serious with it. 

If it does not connect then post the results of 
```
sudo iwlist scan
```
```
nm-tool
```
```
dmesg | grep eth1
```
Thank you

---

### Post by cptnjarhead on 2011-08-31
> **wildmanne39 said:**
> Hi, lets get to it then:

Run this then disconnect your wired and restart your computer.
```
sudo apt-get purge network-manager network-manager-gnome
```that command should make sure no part of network manager is installed, sometimes not all of it is removed without getting serious with it. 

If it does not connect then post the results of 
```
sudo iwlist scan
``````
nm-tool
``````
dmesg | grep eth1
```Thank you


thanks 
- connection failed: unable to get ip address 


damon@damon-laptop:~$ sudo iwlist scan
[sudo] password for damon: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 68:7F:74:C2:D3:B8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013b2f75b60
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020504
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

damon@damon-laptop:~$ nm-tool
The program 'nm-tool' is currently not installed.  You can install it by typing:
sudo apt-get install network-manager
damon@damon-laptop:~$ dmesg | grep eth1
[   16.828741] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.232844] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   42.592420] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   44.901090] eth1: Lucent/Agere firmware doesn't support manual roaming
[   45.001704] eth1: Lucent/Agere firmware doesn't support manual roaming
[   45.202286] eth1: New link status: Connected (0001)
[   45.202506] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   55.572096] eth1: no IPv6 routers present
[  117.360517] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  135.924529] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  139.210719] ADDRCONF(NETDEV_UP): eth1: link is not ready

---

### Post by cptnjarhead on 2011-08-31
should i run update manager?

---

### Post by wildmanne39 on 2011-08-31
Hi, yes please do, it is the same problem as before it is a bug with 10.04.

I am looking at more then one possible solution, so give me a few minutes.
Thank you

---

### Post by wildmanne39 on 2011-08-31
Hi, try this and see if it helps.
```
sudo apt-get install pcmciautils
```
Can you see your network with wicd?
Thank you

---

### Post by cptnjarhead on 2011-08-31
> **wildmanne39 said:**
> Hi, yes please do, it is the same problem as before it is a bug with 10.04.

I am looking at more then one possible solution, so give me a few minutes.
Thank you

updates done.
take your time
thanks again for all your help :D

---

### Post by cptnjarhead on 2011-08-31
> **wildmanne39 said:**
> Hi, try this and see if it helps.
```
sudo apt-get install pcmciautils
```Can you see your network with wicd?
Thank you

damon@damon-laptop:~$ sudo apt-get install pcmciautils
[sudo] password for damon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pcmciautils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
damon@damon-laptop:~$ 

yes, wicd sees network perfictly, just fails to connect, cannot get ip address error

---

### Post by wildmanne39 on 2011-08-31
Hi, that is what I thought, I am still researching some people have solved the problem one way and some another and some not at all, so I am trying to be careful.
Thank you

---

### Post by cptnjarhead on 2011-08-31
> **wildmanne39 said:**
> Hi, that is what I thought, I am still researching some people have solved the problem one way and some another and some not at all, so I am trying to be careful.
Thank you

i appreciate all your help.
Im going to bed. i will check back in the morning.
careful and methodical sound good to me. no need to rush.
thanks again

---

### Post by wildmanne39 on 2011-08-31
Hi, we are going to try one method at time and see if we can get it working.

Change the WPA encryption from AES to TKIP if it is not already TKIP.
Thank you

---

### Post by wildmanne39 on 2011-08-31
Hi, I have been doing a lot of reading and the bug is present all the way up to the the new developmental release that is due to come out in October. 

This is another work around if the one I mentioned in my previous post does not work.

It is close to the one we did last night but it is a little different so it just might work.

```
gksu gedit /etc/network/interfaces
```
add
```
auto eth1
iface eth1 inet dhcp
   wireless yes
   wireless-mode managed
   wireless-essid youressid
   wireless-key restricted yourhexkey
```
(on the lines starting with "wireless" there should be a tab or some blank characters at the beginning)

Put you ESSID and wireless key where it says youressid and yourhexkey.

Also just add this do not delete anything out of the file when it opens.
Thank you

---

### Post by cptnjarhead on 2011-09-01
wildmanne39 
tried your last suggestions and it was a no go.
 because my error was: "unable to get ip addres"
i decided to try a static ip and BINGO it worked.
i am posting this via my wireless.
wildmanne39 and northd_tech thanks for all your help.
Im not sure why i have to use static, but it is working.
if you want me to try some other things feel free to post them or send me a message.
I wish to learn all i can and maybe i could help others some day.
thanks again!

\\:D/

---

### Post by wildmanne39 on 2011-09-01
Hi, your welcome! I am glad it is working, do you have your settings to get DHCP automatically?

With the bugs for that card it is great that we managed to get it working at all would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by cptnjarhead on 2011-09-01
> **wildmanne39 said:**
> Hi, your welcome! I am glad it is working, do you have your settings to get DHCP automatically?

With the bugs for that card it is great that we managed to get it working at all would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

looked in settings and didnt see anything for DHCP auto?
did mark as solved though :)

---

### Post by wildmanne39 on 2011-09-01
Hi yes did you see setting in wicd for auto DHCP, that will make it get the IP address itself, but as long as it is working with static IP I do not think I would mess with it.

---

### Post by cptnjarhead on 2011-09-01
ah yes, i see it. it is set to auto.
i am glad its working.
thanks again!

---

### Post by Nemontemi on 2011-10-11
Hi, i don't want to resurrect your post, but i'm having problems with my Truemobile 1150 equipped Dell Latitude; i have installed Ubuntu 10.10, and it does recognices the wireless signal, but if fails over and over when trying to connect. Any help would be appreciated.

---

### Post by praseodym on 2011-10-11
Hi,

please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by Nemontemi on 2011-10-11
Hello, and thank you very much for answering. The truth is, i'm a very new user of Ubuntu (this was my fisrt install). I already like it, but i didn't expect this problem; I hope you can help me. This are the results.


robb@Misfit:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Subsystem: Dell 3C920 Integrated Fast Ethernet Controller [Latitude C640] [1028:012a]
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

robb@Misfit:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


robb@Misfit:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  0
nls_cp437               4931  0
vfat                    9201  0
fat                    48240  1 vfat
usb_storage            40172  0
binfmt_misc             6599  1
michael_mic             1744  4
orinoco_cs              5050  1
orinoco                64558  1 orinoco_cs
cfg80211              144470  1 orinoco
radeon                825934  3
snd_intel8x0           25632  2
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
joydev                  8735  0
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  1 orinoco_cs
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 radeon,ttm,drm_kms_helper
yenta_socket           21518  0
intel_agp              26360  1
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0
ppdev                   5556  0
agpgart                32011  3 ttm,drm,intel_agp
i2c_algo_bit            5168  1 radeon
psmouse                59033  0
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0
serio_raw               4022  0
parport_pc             26058  1
video                  18712  0
output                  1883  1 video
lp                      7342  0
parport                31492  3 ppdev,parport_pc,lp
3c59x                  32011  0
floppy                 54311  0
mii                     4425  1 3c59x


robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"INFINITUM8491"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

robb@Misfit:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


robb@Misfit:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

robb@Misfit:~$ sudo iwlist scan
[sudo] password for robb:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:E4:8C:35:79
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"INFINITUM8491"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000280f97c587
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000D494E46494E4954554D38343931
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100

---

### Post by wildmanne39 on 2011-10-11
Deleted

---

### Post by praseodym on 2011-10-12
If not yet done, please show completely:

```
lspci -nnk | grep -i net -A2
pccardctl info
lsusb
dmesg | grep ori
```
There is an orinoco-module loaded.

---

### Post by Nemontemi on 2011-10-12
@Wildmanne39: what do you mean "deleted"? @Praseodym: Here are the results: 


robb@Misfit:~$ [COLOR="Lime"]**lspci -nnk | grep -i net -A2**[/COLOR]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Subsystem: Dell 3C920 Integrated Fast Ethernet Controller [Latitude C640] [1028:012a]
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

robb@Misfit:~$ [COLOR="lime"]**pccardctl info**[/COLOR]
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="Dell"
PRODID_2="TrueMobile 1150 Series PC Card"
PRODID_3="Version 01.01"
PRODID_4=""
MANFID=0156,0002
FUNCID=6

robb@Misfit:~$ [COLOR="lime"]**lsusb**[/COLOR]
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. Cruszer Blade
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

robb@Misfit:~$ [COLOR="lime"]dmesg | grep ori[/COLOR]
[    0.187372] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[   17.162572] Adding 1147900k swap on /dev/sda5.  Priority:-1 extents:1 across:1147900k
[   20.195701] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   20.223910] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   20.306341] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
[   20.306462] orinoco_cs 1.0: Station identity  001f:0001:0008:000a
[   20.306467] orinoco_cs 1.0: Firmware determined as Lucent/Agere 8.10
[   20.714410] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
[   20.714543] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
[   20.714549] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
[   20.714553] orinoco_cs 1.0: Ad-hoc demo mode supported
[   20.714556] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
[   20.714560] orinoco_cs 1.0: WEP supported, 104-bit key
[   20.714563] orinoco_cs 1.0: WPA-PSK supported

---

### Post by Nemontemi on 2011-10-12
Just in case, i'm posting again the results prom previous commands:


robb@Misfit:~$ **lspci -nnk | grep -iA2 net**
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Subsystem: Dell 3C920 Integrated Fast Ethernet Controller [Latitude C640] [1028:012a]
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

robb@Misfit:~$ **lsusb**
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


robb@Misfit:~$ **lsmod**
Module                  Size  Used by
nls_iso8859_1           3261  0
nls_cp437               4931  0
vfat                    9201  0
fat                    48240  1 vfat
usb_storage            40172  0
binfmt_misc             6599  1
michael_mic             1744  4
orinoco_cs              5050  1
orinoco                64558  1 orinoco_cs
cfg80211              144470  1 orinoco
radeon                825934  3
snd_intel8x0           25632  2
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
joydev                  8735  0
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  1 orinoco_cs
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 radeon,ttm,drm_kms_helper
yenta_socket           21518  0
intel_agp              26360  1
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0
ppdev                   5556  0
agpgart                32011  3 ttm,drm,intel_agp
i2c_algo_bit            5168  1 radeon
psmouse                59033  0
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0
serio_raw               4022  0
parport_pc             26058  1
video                  18712  0
output                  1883  1 video
lp                      7342  0
parport                31492  3 ppdev,parport_pc,lp
3c59x                  32011  0
floppy                 54311  0
mii                     4425  1 3c59x


robb@Misfit:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"INFINITUM8491"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

robb@Misfit:~$ **rfkill list**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


robb@Misfit:~$ **iwlist chan**
lo        no frequency information.

eth0      no frequency information.

eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

robb@Misfit:~$ **sudo iwlist scan**
[sudo] password for robb:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:E4:8C:35:79
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"INFINITUM8491"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000280f97c587
                    Extra: Last beacon: 236ms ago
                    IE: Unknown: 000D494E46494E4954554D38343931
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100


I can only understand that my wireless signal is, in deed, recognized, because the ESSID shows my actual reuter; that means my Truemobile 1150 works, but it won't connect. With Windows XP (my previous OS) that did'nt happen, so i believe the problem is the orinoco driver, from what i can tell from this post:

[http://ubuntuforums.org/showthread.php?t=304217](http://ubuntuforums.org/showthread.php?t=304217)

But since my current version of Ubuntu is Maverick, i couldn't find a real solution there. Once again, thanks for your help.

---

### Post by praseodym on 2011-10-12
> ```
[ 20.714560] orinoco_cs 1.0: WEP supported, [COLOR="Red"]104[/COLOR]-bit key
[ 20.714563] orinoco_cs 1.0: WPA-PSK supported
```

How long is your key? Did you choose 64/128 bit WEP encryption in the NM? It should be 64 bit (max. 63 letters and/or numbers) in this case.

[COLOR="Red"]Edit[/COLOR]: Using WEP can cause trouble if the key is in the wrong format (hex/ASCII)

---

### Post by Nemontemi on 2011-10-12
I didn't set the network up myself, altough i don't really know how to do that. The WEP's supposed to be 10 bits long (caracters, or numbers, in this case) Do you have any idea?

---

### Post by Nemontemi on 2011-10-13
Are you still around?

---

### Post by praseodym on 2011-10-13
Try another driver:

```
sudo modprobe -rf orinoco_cs
sudo modprobe hostap_cs
dmesg | grep hostap
iwconfig
```

---

### Post by Nemontemi on 2011-10-13
@Jasonjason: I've tried changing the network settings in every way i could with the two types of WEP, but none of them worked. What do you think it might be?

@Praseodym: When i try the first command, a fatal error occurs:

FATAL: Module orinoco_cs is in use.

What do i have to do to disable it?

[COLOR="Red"]EDIT[/COLOR]: I  was able to "blacklist" orinoco_cs using:

sudo xdg-open /etc/modprobe.d/blacklist.conf

and adding at the end or the file 

blacklist orinoco_cs

but now i don't know what's the command to activate hostap_cs, since [sudo modprobe hostap_cs] doesn't executes (it sends another line, but no response).

---

### Post by praseodym on 2011-10-13
Reboot, check with

```
lsmod

```
if orinoco is loaded. If not, load the other one:

```
sudo modprobe -v hostap_cs
sudo service network-manager restart
dmesg | grep hostap
iwconfig
```

---

### Post by Nemontemi on 2011-10-13
That doesn't seem to work,  iwconfig shows: "no wireless extensions"; how can i check if hostap_cs is enabled?

Also, now the "status" light on the Truemobile card is off, with orinoco_cs, it was on, altough that wasn't useful. I suppose that's because no driver is running the card, so how should i enable hostap_cs? The code showed above didn't solved it.

---

### Post by praseodym on 2011-10-13
Check with "lsmod" if the module is loaded. If it doesnt work, "un"-blacklist the orinoco and reboot. Maybe an upgrade of the driver helps:

See here (search for the ID 0156:0002):

[http://linuxwireless.org/en/users/Devices/PCMCIA](http://linuxwireless.org/en/users/Devices/PCMCIA)

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```
and reboot. "orinoco" should be listed again in "lsmod"

---

### Post by Nemontemi on 2011-10-13
The problem is, i don't have any means to get an internet connection on that machine; it's a laptop, but i'm working right now on my pc, which has windows 7 and wireless connection, but i can't even get a LAN connection on my laptop, because of my router.

I have read the page you mentioned, but i can't find the ID.

[COLOR="Red"]EDIT[/COLOR]: I have found the driver :P, but my question is, is there any way to download in windows, and pass it to ubuntu on a USB?

---

### Post by praseodym on 2011-10-13
Check with

uname -a

which kernel you have.

---

### Post by Nemontemi on 2011-10-13
It says:

Linux Misfit 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux

Also, i have already restored orinoco_cs driver; same problem, but the light on the PCI card is on again.

---

### Post by praseodym on 2011-10-13
[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.35/linux-backports-modules-wireless-2.6.35-22-generic_2.6.35-22.12_i386.deb)

Installation by double click and reboot. You should update your system, because kernel -30 is the newest one. _After_ the update install the metapackage of the "modules":

```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by Nemontemi on 2011-10-13
It didn't work, the network manager continues asking for the WEP key, and, even when it's the right one, can't get the connection to fulfill.

Did you meant to first update and then install the driver? That's a problem since in have no way of connecting to internet on my laptop.

I'll see if someone could lend me a router whose LAN works, but that's gonna take me at least, today. While i manage to do that, do you want me to try something else?

---

### Post by praseodym on 2011-10-13
Install the.deb package and reboot, just to be sure. The "install" command only after the updates, because the metapackage links to the one for kernel -30.

---

### Post by Nemontemi on 2011-10-13
Now i get it; i'll try updating via ethernet, then i'll post the results. Thanks for helping me so far; see you soon.

---

### Post by Nemontemi on 2011-10-14
I've tried your solution, but no progress happened; i'll try to update the whole system, unless you have any other idea.

---

### Post by wildmanne39 on 2011-10-14
I post this in the wrong thread I guess I should not be on when I an tired.

---

### Post by Nemontemi on 2011-10-14
I have done what you said, but that doesn't helped. I'll try to update the whole Ubuntu system, unless you have any other idea.

---

### Post by Nemontemi on 2011-10-14
@Wildmanne39: Don't worry,  maybe you could help here too. We're running out of ideas.

---

### Post by wildmanne39 on 2011-10-14
Hi, praseodym has a lot more experience then I do in networking that is why when I saw he was helping you I did not get involved.

The reason I posted here by mistake I am subscribe to this thread and I thought that another person had answer my question in that thread but it was you in this one.

You are in great hands him or chili555 is the best in networking I believe and I am still learning.

---

### Post by Nemontemi on 2011-10-14
Ok, thanks however; it's just that my first experience working with Ubuntu has become very problematic. The weird thing is i feel it like a dare; i'm learning to handle this OS at the time i look for answers to the problems that show up, just like i learned to use Windows long time ago. I'm sure that whit the help of experienced people like you all i'm gonna learn very fast. Thanks for the time, people.

---

### Post by praseodym on 2011-10-14
Really strange. Can you get the Windows XP 32 bit driver somewhere?

---

### Post by Nemontemi on 2011-10-14
No problem:

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R69901&SystemID=LAT_PNT_CEL_C510&servicetag=&os=WW1&osl=en&deviceid=2574&devlib=0&typecnt=0&vercnt=2&catid=&impid=&formatcnt=0&libid=5&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=90953](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R69901&SystemID=LAT_PNT_CEL_C510&servicetag=&os=WW1&osl=en&deviceid=2574&devlib=0&typecnt=0&vercnt=2&catid=&impid=&formatcnt=0&libid=5&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=90953)

what's your idea?

Yesterday, i installed what i think was every update available, then reboot. Nothing happened. Also, there is somthing i just noticed, but i don't know if that could be the root of the problem, that 's, the version i installed is the desktop edition; should i try the laptop edition? or just change the version of ubuntu?

Leaving aside my unexperienced deliruim ;), i'll try what you think it's better. Greetings.

---

### Post by praseodym on 2011-10-14
No need to change the desktop version.

Right click on the R69901.exe and open it with the archive manager. Unpack the files into a new folder named **Wireless-driver** in /home and install it with ndiswrapper:

```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo ndiswrapper -i ~/Wireless-driver/WLDEL48B.INF
```

check:

```
ndiswrapper -l # l is a little L
```
If the driver is shown unload the other one and put it onto the blacklist:

```
sudo modprobe -rfv orinoco_cs orinoco
echo "blacklist orinoco_cs" | sudo tee /etc/modprobe.d/blacklist-orinoco.conf
echo "blacklist orinoco" | sudo tee -a /etc/modprobe.d/blacklist-orinoco.conf
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
sudo service network-manager restart
```
Check:

```
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
iwconfig
lsmod
dmesg | grep ndis
```

---

### Post by Nemontemi on 2011-10-14
I can't create the new folder in /home; when i try to do it, it shows "unable to create new folder: permission denied", i have searched on the /home folder properties, and there i found that i'm not the owner, so i'm not allowed to modify permissions.

Why is that happening? is it because of some configuration mistake during the installation? how can i fix this situation?

[COLOR=Red]EDIT: [/COLOR][COLOR=Black]I have now managed to create the folder using first on terminal the codes "chmod" and "chown", so, forget this part.[/COLOR]

---

### Post by Nemontemi on 2011-10-14
Well, i managed to install ndiswrapper, and by using it, also installing WLDEL48B.INF, but when checking, it shows the following answer:

root@Misfit:/home/robb# ndiswrapper -l #
wldel48b : invalid driver!

Should i blacklist orinoco_cs despite of that answer, or does that means that the Dell driver will not work[COLOR=Red]?

[/COLOR]

---

### Post by Nemontemi on 2011-10-16
Anyone?

---

### Post by wildmanne39 on 2011-10-16
Hi, praseodym has not been on the last two days, he will most likely be back on in the morning, but it can be bad to jump into the middle of a thread to help out because he is working on your problem systematically and someone else could mess up the progress he has made.

---

### Post by praseodym on 2011-10-17
Please show the other outputs, too.

---

### Post by Nemontemi on 2011-10-17
Hi, praseodym, here are the results:

robb@Misfit:~$ sudo modprobe -rfv orinoco_cs orinoco
[sudo] password for robb: 
FATAL: Module orinoco_cs is in use.

robb@Misfit:~$ echo "blacklist orinoco_cs" | sudo tee /etc/modprobe.d/blacklist-orinoco.conf
blacklist orinoco_cs

robb@Misfit:~$ echo "blacklist orinoco" | sudo tee -a /etc/modprobe.d/blacklist-orinoco.conf
blacklist orinoco

robb@Misfit:~$ sudo modprobe -v ndiswrapper
insmod /lib/modules/2.6.38-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko 

robb@Misfit:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf

robb@Misfit:~$ sudo service network-manager restart
network-manager start/running, process 2069

robb@Misfit:~$ ndiswrapper -l
wldel48b : invalid driver!

robb@Misfit:~$ cat /etc/modprobe.d/ndiswrapper.conf

robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"INFINITUM2bae"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:9
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

robb@Misfit:~$ lsmod
Module                  Size  Used by
ndiswrapper           192828  0 
binfmt_misc            13213  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
ppdev                  12849  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  1 orinoco_cs
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 radeon,ttm,drm_kms_helper
dcdbas                 14054  0 
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
i2c_algo_bit           13184  1 radeon
parport_pc             32111  1 
serio_raw              12990  0 
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
3c59x                  37398  0 
floppy                 60032  0 

robb@Misfit:~$ dmesg | grep ndis
[  555.120704] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  555.245889] usbcore: registered new interface driver ndiswrapper
robb@Misfit:~$

---

### Post by praseodym on 2011-10-17
Blacklist the orinoco:

```
echo "blacklist orinoco" | sudo tee -a /etc/modprobe.d/blacklist-orinoco.conf
echo "blacklist orinoco_cs" | sudo tee -a /etc/modprobe.d/blacklist-orinoco.conf
```
Reboot and check:

```
iwconfig
lsmod
dmesg | grep ndis
sudo iwlist scan
rfkill list
```

---

### Post by Nemontemi on 2011-10-17
This is all that terminal shows after the codes:


robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

robb@Misfit:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
radeon                900494  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
drm_kms_helper         40745  1 radeon
pcmcia                 39671  0 
ppdev                  12849  0 
drm                   184164  4 radeon,ttm,drm_kms_helper
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14054  0 
psmouse                73312  0 
parport_pc             32111  1 
video                  18951  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
serio_raw              12990  0 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
3c59x                  37398  0 
floppy                 60032  0 

robb@Misfit:~$ dmesg | grep ndis

robb@Misfit:~$ sudo iwlist scan
[sudo] password for robb: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

robb@Misfit:~$ rfkill list
robb@Misfit:~$

With orinoco_cs blacklisted, the Truemobile is off (i mean, the "status" light); not even network manager shows any wireless connection.

---

### Post by praseodym on 2011-10-18
Now load ndiswrapper:

```
sudo modprobe -v ndiswrapper
```

and check again.

---

### Post by Nemontemi on 2011-10-18
Nothing changes, from what i can see:

robb@Misfit:~$ sudo modprobe -v ndiswrapper
[sudo] password for robb: 
insmod /lib/modules/2.6.38-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko 

robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

robb@Misfit:~$ lsmod
Module                  Size  Used by
ndiswrapper           192828  0 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
radeon                900494  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
joydev                 17322  0 
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
pcmcia                 39671  0 
dcdbas                 14054  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm                   184164  4 radeon,ttm,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32111  1 
video                  18951  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
3c59x                  37398  0 

robb@Misfit:~$ dmesg  | grep ndis
[  248.754557] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  249.040430] usbcore: registered new interface driver ndiswrapper

robb@Misfit:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

robb@Misfit:~$ rfkill list
robb@Misfit:~$

---

### Post by praseodym on 2011-10-19
Doesnt seem to work, so remove this config:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo rm /etc/modprobe.d/blacklist-orinoco.conf
sudo depmod -a
sudo update-initramfs -u
```
Reboot. Try Wicd with Add-On instead of the NM:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Check:

```
iwconfig
lsmod
dmesg | grep ori
sudo iwlist scan
```

---

### Post by Nemontemi on 2011-10-19
This is what it shows; i see some changes in the code responses, but still no wireless connection:

robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:2
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

robb@Misfit:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
michael_mic            12540  4 
orinoco_cs             12898  1 
orinoco                69899  1 orinoco_cs
cfg80211              156212  1 orinoco
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
radeon                900494  2 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
joydev                 17322  0 
ppdev                  12849  0 
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  1 orinoco_cs
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 radeon,ttm,drm_kms_helper
dcdbas                 14054  0 
yenta_socket           27230  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
psmouse                73312  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
parport_pc             32111  1 
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 radeon
serio_raw              12990  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
3c59x                  37398  0 

robb@Misfit:~$ dmesg | grep ori
[    0.178500] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[   21.511573] Adding 1147900k swap on /dev/sda5.  Priority:-1 extents:1 across:1147900k 
[   25.659932] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   25.759517] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
[   25.759640] orinoco_cs 1.0: Station identity  001f:0001:0008:000a
[   25.759645] orinoco_cs 1.0: Firmware determined as Lucent/Agere 8.10
[   25.889058] orinoco_cs 1.0: Hardware identity 0001:0004:0005:0000
[   25.889192] orinoco_cs 1.0: Station identity  001f:0002:0009:0030
[   25.889198] orinoco_cs 1.0: Firmware determined as Lucent/Agere 9.48
[   25.889203] orinoco_cs 1.0: Ad-hoc demo mode supported
[   25.889206] orinoco_cs 1.0: IEEE standard IBSS ad-hoc mode supported
[   25.889210] orinoco_cs 1.0: WEP supported, 104-bit key
[   25.889214] orinoco_cs 1.0: WPA-PSK supported

robb@Misfit:~$ sudo iwlist scan
[sudo] password for robb: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: F4:C7:14:F4:0F:5C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"INFINITUM2bae"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000025bc51094
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000D494E46494E4954554D32626165
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050300000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001067A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 07064D5820010B10
                    IE: Unknown: DD1E00904C330E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050300000000000000000000000000000000000000

---

### Post by praseodym on 2011-10-20
Did you set "eth1" as wireless interface and "wext" as driver in Wicd?

---

### Post by Nemontemi on 2011-10-20
Yes, Wicd has eth1 as wireless interface and wext  as WPA Supplicand driver.

---

### Post by praseodym on 2011-10-20
You are using WEP encryption, try no encryption first, if a connection is possible.

---

### Post by praseodym on 2011-10-20
P.S.: Which mode does the router send? b+g? Try b alone if possible.

---

### Post by Nemontemi on 2011-10-20
I try, but a message shows saying: "This network requires encryption to be activated".

---

### Post by Nemontemi on 2011-10-20
I don't know where to change the router mode, could you specify?

---

### Post by praseodym on 2011-10-20
Type the router-IP in your browser while being connected by cable (because you are changing something). In you router interface you should be able to change the channel, the mode and the encryption.

---

### Post by Nemontemi on 2011-10-21
In fact, it was set on "b+g+n" mode; i changed it to "b" alone. No wireless connection , yet.

[COLOR="Red"]EDIT: [/COLOR] Today i was able to connect via wireless, by selecting on the router settigns the "no encryption" option, but now i have two concerns.

The first one is about my connection being stolen by my neighbours, the second one, which i'm going to check soon, is if i'm going to be able to connect to my school's wireless signal, since it requires encryption.

I hope you can help me fix this now; greetings.

---

### Post by Nemontemi on 2011-10-27
I really do not want to bother, but i'm having problems again. 

Yesterday, i was able to get a wireless connection, without encryption, but today, when i tried to do it, without having changed anythig, Wicd gets stuck while "Getting IP Adress". 

I had to go back to my LAN connection, but i can't have this computer attached to my desktop; what do you think the problem may be?

---

### Post by praseodym on 2011-10-28
Check again:

```
iwconfig
sudo iwlist scan
ifconfig -a
rfkill list
```
Check the BIOS settings ("last state", "on", or whatever)

---

### Post by Nemontemi on 2011-10-30
robb@Misfit:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

robb@Misfit:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: F4:C7:14:F4:0F:5C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:off
                    ESSID:"INFINITUM2bae"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009915451a7
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 000D494E46494E4954554D32626165
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050000087A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 07064D5820010B10
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050000000000000000000000000000000000000000
                    IE: Unknown: DD9F0050F204104A0001101044000102103B00010310470010BC329E001DD811B28601F4C714F40F5C1021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000B5472656E64436869704150100800020084103C000100

robb@Misfit:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:08:74:48:12:15  
          Direc. inet:192.168.1.104  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::208:74ff:fe48:1215/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:162737 errores:0 perdidos:0 overruns:1 frame:0
          Paquetes TX:117345 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:204531986 (204.5 MB)  TX bytes:11113973 (11.1 MB)
          Interrupción:11 Dirección base: 0x6c00 

eth1      Link encap:Ethernet  direcciónHW 00:02:2d:67:0e:df  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:6 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:832 (832.0 B)
          Interrupción:3 Dirección base: 0xe100 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

robb@Misfit:~$ rfkill list
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2011-10-30
Try WPA2-AES encryption if possible. Change it in the router interface, remove the wireless profile, and create a new one, do not edit the old one.

---

### Post by Nemontemi on 2011-10-31
[COLOR="Red"]EDIT: [/COLOR] I've changed the type of encryption, but, again, no wireless connection.

P.S: Sorry about the delay, but i've been very busy at school.

---

