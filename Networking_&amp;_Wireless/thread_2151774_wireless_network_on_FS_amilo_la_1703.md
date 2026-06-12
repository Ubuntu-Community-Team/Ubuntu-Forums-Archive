---
title: "wireless network on FS amilo la 1703"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by omeprazol on 2013-06-05
I have one (actually it is a few, but lets start with this for the time) problem I must ask if any1 can help me with...

I have found a somewhat old computer, originally it was shiped with Windows Vista, but since it only has 512 mb RAM, and the grafic card is even sharing a part of that memory, I decided that it was not quite woth the time it took to even start up a browser... it was horrible!!! After some googleing I found one or two threads mentioning Lubuntu as a operating system worth looking in to.

Finaly I got a opertunity to start using a Linux based system (wich I never have done earlier but allways been somwhat interested in doing) I thought and installed Lubuntu 13.04. And now, as U probably may have guessed, I have found myself with some problems I cant find aswear to on myself...

This first obstickle is that I can not get the wireless connection to work. At first I could not get the system to make any Wi-Fi connection. Guessing it had to do with the system having trouble using the wireless card, I started googleing and learned of ndiswrapper that let U use windowsdrivers to Ur Ubuntu system (sorry if I explain it wrong, am a little bad at english and Im totally new to ubuntu). With that and the driver for the wireless card designed for Win XP from FS, I finally get the system to recognize the networks around me. The somewhat big problem is that when I try to connect to my network, given it the key and all, it starts to process... and then the system craches, every time!!! I have tried to use the drivers designed to Vista, but that doesn work at all.

Can any1 help me with this?

The computer I'm using is a Fujitsu Siemens Amilo La 1703 and the wireless card is a WLAN miniCard D2301, there is some results from a coupple comands some1 posted should contain in such a help request, but I don't seem to understand how to copy the result from the terminal window, and writing if by hand seems to time consuming...

Thx for any help I can get ;)

---

### Post by chili555 on 2013-06-05
You've explained things very well. Also, your English is really very good. No worries there. Let's get a bit more information about your wireless. Please open a terminal and run:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. This will be rather short, so you can simply write it down if you wish. If you'd rather copy from the terminal, you can highlight the text, right-click and select Copy and then paste it in the forum reply box. >  I have tried to use the drivers designed to Vista, but that doesn work at all.That's correct, ndiswrapper uses XP drivers, not Vista or 7 or 8.

Once we know about your wireless card, we'll proceed.

I admire your willingness to rescue an old computer by installing Lubuntu. Great work!

---

### Post by omeprazol on 2013-06-05
> **chili555 said:**
> Let's get a bit more information about your wireless. Please open a terminal and run:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. This will be rather short, so you can simply write it down if you wish. 

It was very short indeed, nothing! but I have tried that command before without any additional command and haven't seen any wireless card info, But if I instead uses ```
lsusb
``` one of the lines looks like this:

Bus 001 Device 002: ID 0bf8:100f Fujitsu Siemens Computers miniCard D2301 802.11 bg Wireless Module [SiS 163U]

> **chili555 said:**
> If you'd rather copy from the terminal, you can highlight the text, right-click and select Copy and then paste it in the forum reply box.

I can highlight it, but I can't right-click it, the only thing happening then is that the high-lightning is just extended/draw-back to the place of the cursor... no menu popping upp

---

### Post by chili555 on 2013-06-05
I believe ndiswrapper is the preferred method and probably the only method. Let's see if there are any clues here:```
dmesg | grep ndis
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```No copy and paste? Please see attached.

You can also output the results to a text document:```
dmesg | grep ndis > omeprazol.txt
sudo iwlist wlan0 scan >> omeprazol.txt
sudo iwlist wlan0 auth >> omeprazol.txt
```Find the file omeprazol.txt in your user directory and either copy and paste it to your reply or simply attach it using the paperclip tool at the top of the reply box.

This may help us: [http://ubuntuforums.org/showthread.php?t=1238204](http://ubuntuforums.org/showthread.php?t=1238204)

---

### Post by omeprazol on 2013-06-06
The result of the commands are:

dmesg | grep ndis

[   13.391514] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   14.350191] ndiswrapper: driver sis163u (Silicon Integrated Systems Corp.(1.08a.01),06/28/2006,5.1.1039.1081) loaded
[   14.791218] usbcore: registered new interface driver ndiswrapper

sudo iwlist wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:8E:13:0E
                    ESSID:"ComHem<3323AD>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000E436F6D48656D3C3333323341443E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180206F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 2C:B0:5D:F3:83:DA
                    ESSID:"SPOTTED"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000753504F54544544
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:17:3F:92:B0:DD
                    ESSID:"Belkin_G_Plus_MIMO_92B0DD"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001942656C6B696E5F475F506C75735F4D494D4F5F393242304444
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD07000C4303000000
          Cell 04 - Address: C0:3F:0E:C0:38:1A
                    ESSID:"ComHem<74CB46>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000E436F6D48656D3C3734434234363E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180202F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 2C:B0:5D:CB:65:B4
                    ESSID:"ComHem<CE0D81>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000E436F6D48656D3C4345304438313E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: CC:5D:4E:E9:6D:34
                    ESSID:"TN_private_EUH7PJ"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0011544E5F707269766174655F45554837504A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706534520010D14
                    IE: Unknown: 050400010004
                    IE: Unknown: 2A0106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 07 - Address: C0:3F:0E:C0:66:29
                    ESSID:"ComHem<750908>"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000E436F6D48656D3C3735303930383E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:16:A6:16:B5:B6
                    ESSID:"3-Dovado-6b5b6"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000E332D446F7661646F2D3662356236
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
          Cell 09 - Address: 20:E5:2A:2C:6E:A5
                    ESSID:"Skalman"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0007536B616C6D616E
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD310050F204104A0001101044000102104700102E418F6C4120FE6B7770595E3A366883103C0001031049000600372A000120
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: 00:1E:2A:7E:69:F7
                    ESSID:"ANDREAS"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0007414E4452454153
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0280000
          Cell 11 - Address: 00:26:5A:FD:48:30
                    ESSID:"BBMB"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000442424D42
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160800190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340800010000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 12 - Address: E0:CB:4E:85:AA:A9
                    ESSID:"totu"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 0004746F7475
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: 00:26:44:37:14:BD
                    ESSID:"TeliaGateway00-26-44-37-14-BD"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001D54656C69614761746577617930302D32362D34342D33372D31342D4244
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020000040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 14 - Address: A0:21:B7:76:2C:08
                    ESSID:"Leo"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
                              12 Mb/s; 11 Mb/s; 9 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00034C656F
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

sudo iwlist wlan0 auth

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        disabled
          Current Key management :
          Current Pairwise cipher :
        none
          Current Pairwise cipher :
        none
          Current Authentication algorithm :
        open

Skalman is "my" network...




> **chili555 said:**
> No copy and paste? Please see attached.

Doesn't work here... Even if I don't know why! the only place in the command window where I can right-click and get a meny is in the windows head, where I can decide the windows behavior etc. odd... So it seems I have to use txt dokuments ;)

> **chili555 said:**
> This may help us: [http://ubuntuforums.org/showthread.php?t=1238204](http://ubuntuforums.org/showthread.php?t=1238204)

don't have the energy to start to search for a windows 98 driver now, maybe later... lets se if things above can lead to anything first :KS

---

### Post by omeprazol on 2013-06-06
I have now tried some other drivers downloaded from sis own web site, got drivers for 98/me NT and some strange map called AMD64... the system crashed trying to install those for 98/me and NT, and when I tried installing the third, it could't search networks...

---

### Post by chili555 on 2013-06-06
I assume this is the network you are trying to connect to:> ESSID:"Skalman"
Protocol:IEEE 802.11g
Mode:Master
Frequency:2.442 GHz (Channel 7)
Quality:89/100 Signal level:-39 dBm Noise level:-96 dBm
Encryption key:on
Bit Rates:54 Mb/s; 48 Mb/s; 36 Mb/s; 24 Mb/s; 18 Mb/s
12 Mb/s; 11 Mb/s; 9 Mb/s
Extra:bcn_int=100
Extra:atim=0
<snip>
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSKIt looks pretty solid. Is the router set for TKIP or AES? I'd try both.

This is quite good:> wlan0 Authentication capabilities :
WPA
WPA2
CIPHER-TKIP
CIPHER-CCMPSome older cards were built before the age of WPA2 and therefore will never connect. Your card purports to do WPA2.>  and some strange map called AMD64.That strange map is for 64-bit systems; that's really not an option for an older, hardware-challenged laptop.

Generally, if it will scan, it will connect. Let's dig deeper for clues as to the crash. Try to connect, let it crash, reboot and then show us:```
cat /var/log/syslog | grep -e wlan -e ndis | tail -n20
```

---

### Post by omeprazol on 2013-06-06
Now were starting to gett somewere...

The router is set to AES, I tried to switch to TKIP, the router didn't like it so much, said that it coudn't deliver the same mode/speed/whatever, didn't understand exaktly what it said... Anyway, I tried it anyway regardless of what the router recommended, and all of a sudden, my lubuntu computer could log in to the wireless without the system crashing. Tried to switch it back to AES to se if it starts crashing again, and voala, it did...

This is the result of the command:

Jun  6 16:01:43 Lubuntu-ftw kernel: [   15.282801] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
Jun  6 16:01:43 Lubuntu-ftw kernel: [   15.283194] usbcore: registered new interface driver ndiswrapper
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0)
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:10.4/usb1/1-5/1-5:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): using WEXT for WiFi device control
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <error> [1370527305.599412] [nm-device-wifi.c:2841] update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): bringing up device.
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): preparing device.
Jun  6 16:01:45 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  6 16:01:45 Lubuntu-ftw kernel: [   26.129532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:01:45 Lubuntu-ftw kernel: [   26.130153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  6 16:01:46 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0) supports 1 scan SSIDs
Jun  6 16:01:46 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  6 16:01:46 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  6 16:01:46 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  6 16:01:46 Lubuntu-ftw NetworkManager[1036]: <info> (wlan0) supports 1 scan SSIDs

Even though I myself start to see where the problem is, I don't understand it, can U explain?

---

### Post by chili555 on 2013-06-06
The router probably won't support 802.11N speeds using TKIP, however, your wireless driver won't use AES without crashing, so you have a dilemma; either be satisfied with TKIP and no N speeds or get a newer, more capable wireless device for ye olde laptop.

When you did this:>  my lubuntu computer could log in to the wireless without the system crashing...were you able to connect, go on line, etc.?

---

### Post by omeprazol on 2013-06-06
yes, I could use internet and all as soon as I change the seting on the router to TKIP... Seems I have to either give up wireless on this computer (since it isn't worth puting out money on something that I more or less use to learn and experement with) or change the settings permanently on the router and get lower speed to my other devices, but I don't think I wanna do that since we streaming movies pretty often... och whait... I might have a reciever that I bought a coupple of years ago, that one might work better, shall se someday if I find it.

Anyway, I think this problem is solved, as solved as it can be at least... Next problem is the sound, but it is another topic, and I haven't had time to check it out yet, so I might return later in another thread with that.

Thx alot for all the help! I have learnd alot, both about ubuntu but also about network! thx man!!!

---

