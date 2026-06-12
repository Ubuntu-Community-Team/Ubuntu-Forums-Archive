---
title: "Wireless driver question (Rosewill RNX-N180PCe)"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by Subcomfreak on 2012-07-07
I recently installed unbuntu 12.04 in a dual boot with windows 2000. Unbuntu is working fine, and I am very very satisfied with it. However, I think my wireless card is useing the wrong drivers.

I can connect to the Internet through my wireless card in unbuntu fine. It connects and uploads and downloads fine. However, after a certain, seemingly random time, the download speed drops to zero. It doesn't disconnect from the network, it just drops to zero. After a much longer time it disconnects, and reconects and this process starts over. If I manually disconnect and reconnect to the network this process also starts over.

As the Title of this thread suggests, I have a Rosewill RNX-n180PCe card. However, in the terminal (via the lspci -v command) it says I have this card:

```
02:0b.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R
    Flags: bus master, slow devsel, latency 64, IRQ 19
    Memory at f8fe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

```

So I think it may be a driver issue. So here we go... I looked up on the manufactures website and found that it does have linux drivers:

[http://www.rosewill.com/products/1698/ProductDetail_Download.htm](http://www.rosewill.com/products/1698/ProductDetail_Download.htm)

I was wondering if they would work in unbuntu 12.04, and, sense I am sort of new, how to install them. There are windows 7 and windows XP drivers also available. I was wondering if I could "wrap" those. What would the process for that be?

There is also a similar card, made by the same people, that has more up to date drivers:
[http://www.rosewill.com/products/1870/ProductDetail_Overview.htm](http://www.rosewill.com/products/1870/ProductDetail_Overview.htm)

Any help would be very much appreciated!

---

### Post by chili555 on 2012-07-07
> I was wondering if they would work in unbuntu 12.04Very doubtful. Please see attached. It says it's for kernel 2.6.xx. You are running 3.2.xx. 

Perhaps we can load a kernel parameter and help the current driver. Please open a terminal and do:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```Are you certain your problem is caused by the driver and not Network Manager? wpa_supplicant? No? Neither am I.

---

### Post by Subcomfreak on 2012-07-07
All that I know is that it works in windows 2000 with its driver, and in unbuntu it sorta works without its own driver.

trying your command.

EDIT: Appears to be working, I need to test it for some time in order to determine if it fixed the problem.

---

### Post by chili555 on 2012-07-07
If it works, we'll write one quick file and make it permanent.> All that I know is that it works in windows 2000 with its driverA great many devices work perfectly in one but not the other. All that tells us is that the hardware isn't defective.

---

### Post by Subcomfreak on 2012-07-07
Sadly, the problem still persists. Are there any other tweaks that can be made?

---

### Post by chili555 on 2012-07-07
May we see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Subcomfreak on 2012-07-07
```
wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:9B:A2:B3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"RosoRouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000A526F736F526F75746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B00010310470010D8E17EC120B3C9FBB0584A516170A335102100074C696E6B7379731023000D4C696E6B7379732045343230301024000776312E302E30341042000234321054000800060050F20400011011000D4C696E6B737973204534323030100800020084103C000103
                    IE: Unknown: DD090010180206F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 58:6D:8F:9B:A2:B5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:off
                    ESSID:"RosoRouter-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a1e320ab96
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 0010526F736F526F757465722D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by chili555 on 2012-07-07
> Cell 01 - Address: 58:6D:8F:9B:A2:B3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"RosoRouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    <snip>
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    <snip>
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKI expect you might have better luck with WPA2 only and not mixed mode WPA and WPA2. Can you please test?

(*cough* wpa_supplicant!)

---

### Post by Subcomfreak on 2012-07-07
I feel ashamed to ask, How do you do that? :oops:

---

### Post by chili555 on 2012-07-07
I assume you own or have administrative rights to the router  RosoRouter. Log on to the administration pages of the router using the address of the gateway; something like 192.168.1.1 in the address bar of Firefox or any browser. Look for the wireless settings and set the encryption mode to WPA2. Save and close. Please see attached. 

You want WPA2-PSK *only* and not any mixed mode.

---

### Post by Subcomfreak on 2012-07-07
Sadly, it didn't work.

---

### Post by chili555 on 2012-07-08
Is the driver parameter still loaded? If you rebooted, it is not. Please try again:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If the connection is still problematic, I suggest first, that you install:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```OR:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```...depending on whether you have a pae kernel. Find out with:```
uname -r
```Here is an example from my computer:> chili@LAPTOP60:~$ uname -r
3.2.0-26-generic-[COLOR="Red"]pae[/COLOR]There is an updated rt2800pci in that package. Reboot to activate all the changes.

If that doesn't help, I'll be ready to use the Windows XP drivers with ndiswrapper. Your Windows 2000 drivers may be the same.

---

### Post by Subcomfreak on 2012-07-08
I don't think I did NOT correctly apply the setting for the WPS modes. When I went back to reset them it it was still on the split mode.  I do not have enough time today to fiddle with this today, however, I will try to change the modes again, and if that fails I will try your other suggestions. You have been so helpful!!! Thank you for spending time on my issue!!! You linux guys beat the hell out of Microsoft in the tech support area!

---

### Post by Subcomfreak on 2012-07-11
Changing the setting does appear to fix the problem. However, further testing is required.

---

### Post by Subcomfreak on 2012-07-12
Downloaded about a gig without problems. Solved!

---

### Post by chili555 on 2012-07-12
> **Subcomfreak said:**
> Downloaded about a gig without problems. Solved!Awesome. Glad it's working. Would you please use thread tools at the top to mark Solved?

---

