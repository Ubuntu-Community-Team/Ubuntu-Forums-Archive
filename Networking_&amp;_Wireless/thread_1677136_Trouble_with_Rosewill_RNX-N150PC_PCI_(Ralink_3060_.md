---
title: "Trouble with Rosewill RNX-N150PC PCI (Ralink 3060 chip)"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by cbutzon on 2011-01-28
I'm a new user of Ubuntu Desktop, but have a little prior experience with Linux. 

I obtained and compiled the driver for my Rosewill RNX-N150PC wireless adapter (using some guidance from [this thread]("http://ubuntuforums.org/showthread.php?t=1608095")) and it appears to be working correctly; however, it does not "see" my wireless access point. (The wireless adapter and the WAP work perfectly in Windows.)

Here's some diagnostic information that may be helpful:

lspci -v | less:

```
05:00.0 Network controller: RaLink Device 3060
        Subsystem: RaLink Device 3060
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci
```iwconfig: 

     ```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```iwlist scanning:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results 
```Any help?

---

### Post by chili555 on 2011-01-28
I noticed this:> 05:00.0 Network controller: RaLink Device 3060
        Subsystem: RaLink Device 3060
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        [COLOR="Red"]Kernel modules: rt3562sta, rt2800pci[/COLOR]You'll probably want to add to /etc/modprobe.d/blacklist.conf the following:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```After you save the changes, reboot and let us have your report.

---

### Post by cbutzon on 2011-01-28
I did what you said to do and it WORKED! After 2+ hours of fooling around with this, I couldn't be happier. Thanks for the help.

---

### Post by teyster2 on 2011-02-07
If you have a problem after this make sure you set 
connection from wlan0 to ra0.  Then it worked for me
:)

---

### Post by surfermk9 on 2011-06-09
Okay so... I have this card in an Ubuntu 11.04 box.  I've been fumbling around with it for a while now and I was wondering if anyone could help.

I've followed the tutorial mentioned above and this thread, but it seems I'm stuck.

when I run lspci -v | less:

```
00:06.0 Network controller: Ralink corp. Device 3060
        Subsystem: Ralink corp. Device 3060
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at eb000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt3562sta, rt2800pci

```

iwconfig:

```
livingroom@livingroom-KM400-8235:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-85 dBm  Noise level:-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwscanning:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 98:2C:BE:AC:E3:E9
                    Protocol:802.11b/g
                    ESSID:"2WIRE587"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 02 - Address: 68:7F:74:6F:B6:9B
                    Protocol:802.11b/g
                    ESSID:"Control"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:50/100  Signal level:-70 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:22:3F:11:67:BB
                    Protocol:802.11b/g
                    ESSID:"Control"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:81/100  Signal level:-58 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD270050F204104A000110104400010210470010168930397DE399573DD83BDCE9EE559E103C000103
          Cell 04 - Address: 68:7F:74:43:8A:D1
                    Protocol:802.11b/g/n
                    ESSID:"dockery"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:55/100  Signal level:-68 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: 68:7F:74:43:8A:D2
                    Protocol:802.11b/g/n
                    ESSID:"dockery-guest"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-90 dBm  Noise level:-85 dBm
                    Encryption key:off
                    Bit Rates:144 Mb/s
          Cell 06 - Address: 00:22:3F:7D:4F:AC
                    Protocol:802.11b/g
                    ESSID:"Spiderhouse"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:10/100  Signal level:-86 dBm  Noise level:-81 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```

Not sure what's going on here since it shows all those networks.  I blacklisted the rt2800pci and it still shows up as a kernel module. I'm not sure if that's normal?

Another thing that I can't figure out is why network manager doesn't show all those networks. I installed wicd and it showed them all, but wouldn't connect sue to some problem it had with my *correct* password...

I'm kind of stuck and confused... anybody have any advice?

---

### Post by chili555 on 2011-06-10
> I blacklisted the rt2800pci and it still shows up as a kernel module. I'm not sure if that's normal?How about we take a peek at:```
lsmod | grep -e rt2 -e rt3
cat /etc/modprobe.d/blacklist.conf
```It looks like you have a conflict here.> I've followed the tutorial mentioned aboveAre you quite sure you modified os/linux/config.mk for being controlled by Network Manager?

---

### Post by kalmos on 2011-08-24
> **chili555 said:**
> I noticed this:You'll probably want to add to /etc/modprobe.d/blacklist.conf the following:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```After you save the changes, reboot and let us have your report.

You can note that I had exactly the same outputs from my commands and this worked for me. Thanks!

---

