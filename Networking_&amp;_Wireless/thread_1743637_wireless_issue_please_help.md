---
title: "wireless issue please help"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by lukas25us on 2011-04-29
I have a dell inspiron 4000 with a lucent MPCI3A-20 wireless lan.
when i had ubuntu 9.04 it worked great besides the fact that everything was huge as i could not fix the display. so i upgraded to 11.04 and it fixed the display problem but my wireless wont work. it sees the networks around me when i click to connect it sits there trying to connect but dont says wireless network disconnected. i tryed it with my router which has a Wpa personal encryption i put the password it and still the same problem. i really like ubuntu and wish to continue to use it but i am ready to pull out hair.lol i have seen many posts about this problem with others and seen the help. i am still a Noob when it comes to this kind of thing. please someone help me.

---

### Post by mörgæs on 2011-04-29
First step: If you do a clean install of 11.04 having wired internet access in the process, does everything work?

---

### Post by lukas25us on 2011-04-29
i used the cd i got from the web ubuntu.com installed with a wired connection. that worked but wireless did not. everything works but the wireless for some reason

---

### Post by lukas25us on 2011-04-29
i did a fresh install the wired connection works but wireless does not. sees the networks but wont connect to them

---

### Post by charles-wolfman on 2011-04-29
I am having the exact same problem wifi worked fine on this laptop under 10.10, not to mention the lovely change to the scrollbars (dont get me started on that one...) and the changes to firefox's UI, if the devs are going to break **** or change the UI around they should include an option to roll back the update.

---

### Post by josephmills on 2011-04-29
hi there could we please see a ```
lspci -nn
``` thanks

---

### Post by charles-wolfman on 2011-04-29
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
02:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev aa)
02:00.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev aa)
02:00.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 02)
02:01.0 Ethernet controller [0200]: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) [8086:101e] (rev 03)
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
03:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
03:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
03:00.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)

---

### Post by josephmills on 2011-04-29
```
rfkill list 
```thanks

---

### Post by charles-wolfman on 2011-04-29
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by josephmills on 2011-04-29
```
sudo lshw -c network
```

---

### Post by charles-wolfman on 2011-04-29
PCI (sysfs)

---

### Post by josephmills on 2011-04-29
```
lsmod | grep dell
```

---

### Post by josephmills on 2011-04-29
> **charles-wolfman said:**
> PCI (sysfs)

you have to let it load

---

### Post by charles-wolfman on 2011-04-29
"you have to let it load"
duh, i feel silly now

 *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:cb:79:bb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.10.102 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8400(size=64) memory:c0240000-c024ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth3
       version: 00
       serial: 00:0e:9b:28:aa:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0210000-c0213fff memory:c0400000-c07fffff memory:c0800000-c09fffff

---

### Post by lukas25us on 2011-04-29
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1420 PC card Cardbus Controller [104c:ac51]
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
00:10.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02)
02:00.0 Ethernet controller [0200]: Xircom Cardbus Ethernet 10/100 [115d:0003] (rev 03)
02:00.1 Serial controller [0700]: Xircom Cardbus Ethernet + 56k Modem [115d:0103] (rev 03)

---

### Post by josephmills on 2011-04-29
@ wolfman you need to start a new thread these are going to be different in the new thread 



```
lsmod | grep airo 
```
```
dmesg | grep airo 
```

---

### Post by lukas25us on 2011-04-29
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


*-network               
       description: Ethernet interface
       product: Cardbus Ethernet 10/100
       vendor: Xircom
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:10:a4:a0:48:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=xircom_cb ip=192.168.1.101 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: irq:11 ioport:1000(size=128) memory:18000000-180007ff memory:18000800-18000fff memory:14000000-14003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:33:83:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-8-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

---

### Post by charles-wolfman on 2011-04-29
"lsmod | grep airo"
airo                   73165  0 

"dmesg | grep airo"
[   20.068597] airo(): Probing for PCI adapters
[   20.068658] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   20.068681] airo(): Found an MPI350 card
[   21.164617] airo(eth1): Firmware version 5.41.00
[   21.164622] airo(eth1): WPA supported.
[   21.164626] airo(eth1): MAC enabled 00:0e:9b:28:aa:3f
[   21.166212] airo(): Finished probing for PCI adapters

---

### Post by josephmills on 2011-04-29
@ lukas please see post 8

---

### Post by lukas25us on 2011-04-29
posted that already with the sudo lshw -C network all in the same reply

---

### Post by josephmills on 2011-04-29
> **josephmills said:**
> ```
rfkill list 
```thanks

post 8

---

### Post by lukas25us on 2011-04-29
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by lukas25us on 2011-04-29
that is what it says when i type rfkill list

---

### Post by josephmills on 2011-04-29
```
rfkill list all 
```
```
lsmod | grep dell
```

---

### Post by lukas25us on 2011-04-29
fyr3@Platinum-Inspiron-4000:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by lukas25us on 2011-04-29
fyr3@Platinum-Inspiron-4000:~$ lsmod | grep dell
fyr3@Platinum-Inspiron-4000:~$ lsmod | grep dell
fyr3@Platinum-Inspiron-4000:~$ 

it lists nothing

---

### Post by josephmills on 2011-04-29
```
lsmod | grep airo
```
```
dmesg | grep airo
```
sorry go two people mixed up :)

---

### Post by lukas25us on 2011-04-29
[FONT=monospace]fyr3@Platinum-Inspiron-4000:~$ lsmod | grep airo
fyr3@Platinum-Inspiron-4000:~$ lsmod | grep airo
fyr3@Platinum-Inspiron-4000:~$ 

still nothing
[/FONT]

---

### Post by josephmills on 2011-04-29
```
lsmod
```
```
dmesg | grep wlan
```

---

### Post by lukas25us on 2011-04-29
Module                  Size  Used by
binfmt_misc            13213  1 
snd_maestro3           22973  2 
snd_ac97_codec        105614  1 snd_maestro3
ac97_bus               12642  1 snd_ac97_codec
michael_mic            12540  4 
snd_pcm                80244  2 snd_maestro3,snd_ac97_codec
orinoco_cs             12898  1 
snd_page_alloc         14073  1 snd_pcm
orinoco                69899  1 orinoco_cs
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
cfg80211              156212  1 orinoco
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia                 39671  1 orinoco_cs
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
xircom_cb              17311  0 
joydev                 17322  0 
yenta_socket           27230  0 
snd                    55295  11 snd_maestro3,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
soundcore              12600  1 snd
ppdev                  12849  0 
pcmcia_core            21505  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14054  0 
parport_pc             32111  1 
i2c_piix4              13095  0 
video                  18951  0 
psmouse                73312  0 
shpchp                 32345  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0

---

### Post by lukas25us on 2011-04-29
does nothing with the dmesg | grep wlan

---

### Post by josephmills on 2011-04-29
```
sudo iwlist scan
``` dont show any ip address or personal information

---

### Post by lukas25us on 2011-04-29
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:22:6B:44:7A:1D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Crystal Rock"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025dc3fc8b5b
                    Extra: Last beacon: 196ms ago
                    IE: Unknown: 000C4372797374616C20526F636B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483833373134301054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: Unknown: DD090010180201F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by josephmills on 2011-04-29
```
dmesg | grep eth
```

---

### Post by lukas25us on 2011-04-29
[    0.846195] i2c-core: driver [adp5520] using legacy suspend method
[    0.846205] i2c-core: driver [adp5520] using legacy resume method
[   13.930822] net eth0: Xircom cardbus revision 3 at irq 11
[   28.547699] xircom_cb: xircom cardbus adaptor found, registering as eth0, using irq 11
[   28.547791] net eth0: Link is 100 mbit
[   28.616703] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.152090] eth0: no IPv6 routers present

---

### Post by josephmills on 2011-04-29
have you ```
sudo apt-get update
```then```
sudo apt-get upgrade
```? I am almost at a loss on this on

---

### Post by lukas25us on 2011-04-29
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Reading package lists... Done

---

### Post by lukas25us on 2011-04-29
what do i do now?

---

### Post by charles-wolfman on 2011-04-29
installed system updates, problem still presists

---

### Post by charles-wolfman on 2011-04-30
So then, ubuntu 11.04 breaks wifi and there is no way to fix it short of reinstalling 10.10? wonderful.

---

