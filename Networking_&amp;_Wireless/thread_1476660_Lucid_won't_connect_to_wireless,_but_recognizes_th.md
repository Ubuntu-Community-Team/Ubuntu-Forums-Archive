---
title: "Lucid won't connect to wireless, but recognizes the driver"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by samuel.faith on 2010-05-08
Hi folks,

I've recently upgraded to Lucid Lynx last night, and everything went smoothly except a few minor hiccups. The upgrade was via wireless connection, from Update Manager in my previous Karmic installation.

My lappy is Dell Inspiron 1440 and the network card is Dell Wireless 1397 WLAN Mini-card. The chipset is Broadcom 4312.

Now I'm having trouble with wireless connection. Wired works just fine, and in fact I am posting now with wired connection. iPhone tethering works perfectly fine as well.

Network manager recognizes the wireless connections, and the driver, but whenever it tries to connect my home network, it'll take really long time, and it will keep asking for password, which I keyed in correctly but still prompt again for password awhile later.

I've checked my router and stuffs, they're working fine as I also have a few other machines and none of them have problems.

I tried reinstalling b43-fwcutter and reboot but it won't work.

According to lspci -v output, my card is:


```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Dell Device 000c
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6cfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb
```

Below is my lspci -nn output:

```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] [1002:9552]
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```


Below is iwlist scan output:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:58:EA:A1:0F
                    ESSID:"dlink"
                    Mode:Managed
                    Frequency=2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001064C27B3FFA9B31A29D518F358CB01A951021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1C:10:26:D4:23
                    ESSID:"chandra_christine"
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-87 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:09:5B:ED:70:0C
                    ESSID:"CALROOM"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:03:52:AC:F1:40
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:03:52:AD:45:E0
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:1E:E5:57:C0:3B
                    ESSID:"bey77"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 07 - Address: 68:7F:74:2F:13:24
                    ESSID:"FHPL"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B000103104700102ECECAB562C736C58D980978CE238F42102100104C696E6B73797320627920436973636F102300075752543631304E1024000876322E30302E30301042000234321054000800060050F2040001101100075752543631304E100800020084
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 08 - Address: 00:03:52:AD:48:B0
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 09 - Address: 00:03:52:AC:DA:90
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 10 - Address: 00:03:52:AD:2B:10
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 11 - Address: 00:24:56:93:8F:89
                    ESSID:"2WIRE589"
                    Mode:Managed
                    Frequency=2.442 GHz (Channel 7)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:03:52:AC:DB:A0
                    ESSID:"ZeroConfig@FraserSuites"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 13 - Address: 00:1A:A1:5C:DE:80
                    ESSID:"\x00"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

eth3      Interface doesn't support scanning.
```

Below is iwconfig output:


```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:226  Noise level:167
          Rx invalid nwid:0  invalid crypt:20  invalid misc:0

eth3      no wireless extensions.
```


Hope I provided sufficient information to aid you guys in helping me out.

Thanks in advance!

--sfaith

---

### Post by avocadobride on 2010-05-08
Yeah I have the exact same problem, I just installed Lucid yesterday at a friends place on my Eee PC, and it worked fine on his WEP encrypted network (yeah I know, hes poor and its outdated hardware, hes not retarded.) and I was wondering if your wireless network was using WPA/WPA2 encryption because when I disabled that It started working, I tried changing the passwords and reassigning IP addresses. If anyone finds a fix that would be really good, as I really don't want to leave my network unprotected!

Thanks!

(also 1st post evar! heres to a long and wonderful forum experience!)

---

### Post by samuel.faith on 2010-05-08
> **avocadobride said:**
> Yeah I have the exact same problem, I just installed Lucid yesterday at a friends place on my Eee PC, and it worked fine on his WEP encrypted network (yeah I know, hes poor and its outdated hardware, hes not retarded.) and I was wondering if your wireless network was using WPA/WPA2 encryption because when I disabled that It started working, I tried changing the passwords and reassigning IP addresses. If anyone finds a fix that would be really good, as I really don't want to leave my network unprotected!

Thanks!

(also 1st post evar! heres to a long and wonderful forum experience!)

Hi,

Welcome to Ubuntu forum! I'm sure you'll be happy here, with all helpful folks around.

While WEP network is outdated and insecure, there are large number of people still using it. I see there is nothing wrong with that provided you can take the risks. And if it's your home network, and when nobody outside of your home can detect your signal (assuming that, of course), I think that should be just fine.

And to answer your question, yes I am using WPA/WPA2 encryption. While other systems in my house, my previous Karmic installation, and Vista on same lappy work just fine with that. I tried connecting to some public wireless networks that don't use WPA/WPA2 encryption, and guess what? It works just fine. I tried turning off WPA/WPA2 at my home network, and hey it also works!

Right now, I am using wired connection, since I don't want to compromise my network security and I also have other systems in the network.

It's currently set to mixed 802.11n and 802.11g mode. I'll try changing the mode and will update it here.

Good luck for you too!

Samuel Faith

---

### Post by samuel.faith on 2010-05-08
I tried changing the encryption to WPA2 only and AES cipher type, as well as 802.11g only mode, but not working. :(

Anybody have any ideas on this?

---

### Post by samuel.faith on 2010-05-08
It seems there is a bug report for that, but for EEE PC.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443)

---

### Post by Xavier_To on 2010-05-08
I don't know if we have the same problem. I also have a Broadcom 4312 on Dell (though it's the Vostro 1520...). If I boot with the wifi switch at on, I won't be able to connect, as Networkmanager sees my wifi card as off (even though the switch is on). However, if I turn off the wifi switch before booting and turn it on once i'm logged in, i'm able to detect wifi networks and connect to them....

Strange and annoying (who thinks of turning the switch before booting... seriously...) but it works for me.

if anyone has a better fix, I'd be happy to see it

---

### Post by samuel.faith on 2010-05-08
> **Xavier_To said:**
> I don't know if we have the same problem. I also have a Broadcom 4312 on Dell (though it's the Vostro 1520...). If I boot with the wifi switch at on, I won't be able to connect, as Networkmanager sees my wifi card as off (even though the switch is on). However, if I turn off the wifi switch before booting and turn it on once i'm logged in, i'm able to detect wifi networks and connect to them....

Strange and annoying (who thinks of turning the switch before booting... seriously...) but it works for me.

if anyone has a better fix, I'd be happy to see it

I guess it's not really the same. Cos on Inspiron 1440, there is no switch. You can press Fn + F2 to turn on and off the wireless, but that's just it. And Lucid instantly sees my WiFi as on. The issue here is, I can't connect to any networks protected by WPA/WPA2 encryption. Open networks are fine. I haven't tested with WEP yet though.

---

### Post by Xavier_To on 2010-05-11
> **samuel.faith said:**
> I guess it's not really the same. Cos on Inspiron 1440, there is no switch. You can press Fn + F2 to turn on and off the wireless, but that's just it. And Lucid instantly sees my WiFi as on. The issue here is, I can't connect to any networks protected by WPA/WPA2 encryption. Open networks are fine. I haven't tested with WEP yet though.

A guy from work sent me this... it might help you 

[http://ubuntuforums.org/showthread.php?p=9256987](http://ubuntuforums.org/showthread.php?p=9256987)

---

### Post by chlorinekid on 2010-05-11
this might help. i had the same problem. problem was conflicting ralink drives. this thread describes how to blacklist one set allowing the other set to work.

im running 10.04 with wpa2 wireless and all is well...

[http://ubuntuforums.org/showthread.php?t=1472061](http://ubuntuforums.org/showthread.php?t=1472061)

hope it helps

---

### Post by samuel.faith on 2010-09-21
Okay... I am gonna necrothread this thread, since I still can't find a solution yet!

---

### Post by samuel.faith on 2010-09-21
Found a great fix. Check this out, folks.

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx]("http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx")

---

### Post by malcmail on 2011-02-19
After a nightmare with this I chanced upon an answer that worked for me and thought I would share it - if it works for anyone great stuff!  On trying to ping from the system it gave me the address tha had been assigned to the wired connection (which wasnt plugged in). Try sudo ifconfig eth0 down (and I presume any other wired connections showing). After that mine worked just perfectly. Good luck :)

---

### Post by bishblaize on 2011-03-04
Sounds odd, but the solution I found was dead simple. It requires a 13 digit password. Since I put one in, I've never had a problem since.

Dont ask me why, Im no techie, I just came across the answer on a Jollicloud forum. I've had this problem on more than one laptop.

Given the frustration I had I'm just adding this to any threads I see about this problem.

Hope this helps.

---

