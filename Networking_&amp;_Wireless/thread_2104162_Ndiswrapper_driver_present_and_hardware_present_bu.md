---
title: "Ndiswrapper driver present and hardware present but doesn't work?"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by ChrisKjellqvist on 2013-01-12
Hey everyone, 
     I just downloaded Ubuntu and installed fine, installed Ndiswrapper for my 050d:6050 device, aaaand it doesn't work. It's not obvious either when I type Ndiswrapper -l because it says, as you can guess from the title....
```
bcmwlhigh6 : driver installed
     Device (050d:6050) present 
```

So if someone could help me out with that, that would be great, Thanks.

---

### Post by praseodym on 2013-01-12
Hi there.

Which Ubuntu-version do you use? There is a bug with ndiswrapper in 12.10. If you are using it, uninstall ndiswrapper completely:
```

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
sudo rm /lib/modules/$(uname -r)/kernel/ubuntu/ndiswrapper/ndiswrapper.ko 
```
and compile it on your own. Instructions here:

[http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662](http://forum.ubuntuusers.de/topic/wlan-pci-wird-nicht-bei-jedem-start-erkannt/#post-3842662)

"Ndiswrapper 1.58rc1 installieren"

You can also compile the GUI "ndisgtk", see there, too. Start with

```
sudo apt-get install python python-glade2 python-gtk2 
```

---

### Post by ChrisKjellqvist on 2013-01-12
I'm using 12.04

---

### Post by praseodym on 2013-01-12
Ok, lets check:
```

dmesg | egrep 'ndis|country'
iwconfig
iwlist chan
sudo iwlist scan
```
Which country do you live?

---

### Post by ChrisKjellqvist on 2013-01-12
I live in the U.S. 
Here's the results of those commands

```
         chris@chris-desktop:~$ dmesg | egrep 'ndis|country'
chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@chris-desktop:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

chris@chris-desktop:~$ sudo iwlist scan
[sudo] password for chris: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

chris@chris-desktop:~$           
```

---

### Post by praseodym on 2013-01-13
The driver is loaded?

```
sudo modprobe -v ndiswrapper
```

---

### Post by ChrisKjellqvist on 2013-01-13
The output was...

```
chris@chris-desktop~$ sudo modprobe -v ndiswrapper
[sudo] password for chris:
insmod /lib/modules/3.2.0-29-generic/misc/ndiswrapper.ko
```

---

### Post by ChrisKjellqvist on 2013-01-13
I have no idea how, but now I have internet??? Haha, just typed in the command, then felt like typing iwconfig, and then I got internet! Thanks so much.

Edit: I guess that's what did it, the sudo modprobe -v ndiswrapper. My only concern now is that it is taking a while to connect... But if it doesn't after a while, I'll just re-edit this.

Edit 2: Yep, well now it can see the networks and try to connect, but it just keeps trying to connect, over and over, and it keeps asking for hte password.

Edit 3: I also tried the Vista drivers with the same results.

---

### Post by praseodym on 2013-01-13
The command loads the driver.

Which encryption mode do you use? I do not know, if the driver supports WPA2. Also try modes without "a" or "n", e.g. "b+g". Check:
```

iwconfig
iwlist chan
sudo iwlist scan
route -n
dmesg | grep ndis
```

---

### Post by ChrisKjellqvist on 2013-01-13
Here you go

```
   chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

chris@chris-desktop:~$ iwlist chan
lo        no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

eth0      no frequency information.

chris@chris-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

route -n
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:21:E5:B1
                    ESSID:"2WIRE615"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100                    Extra:atim=0
                    IE: Unknown: 00083257495245363135
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 02 - Address: B8:8D:12:66:0E:5F
                    ESSID:"Amanda Christmann's Network"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001B416D616E6461204368726973746D616E6E2773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1605001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106B88D12660E5F
          Cell 03 - Address: 00:24:36:A6:05:4B
                    ESSID:"Apple Network a6054c"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00144170706C65204E6574776F726B20613630353463
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A001700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106002436A6054C
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 04 - Address: 06:24:36:A6:05:4B
                    ESSID:"R\xC3\xA9seau d\xE2\x80\x99invit\xC3\xA9s de Papounet"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 002052C3A9736561752064E28099696E766974C3A973206465205061706F756E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A001700000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0208
                    IE: Unknown: DD0E0017F20700010106002436A6054C
          Cell 05 - Address: 00:18:E7:72:75:FA
                    ESSID:"THOMSON-ACG-93d0"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001054484F4D534F4E2D4143472D39336430
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021300
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020000040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

chris@chris-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
chris@chris-desktop:~$ dmesg | grep ndis
[   42.703023] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   42.876082] ndiswrapper: driver bcmwlhigh5 (Belkin International, Inc.,08/26/2009, 5.10.79.30) loaded
[   43.404558] usbcore: registered new interface driver ndiswrapper
chris@chris-desktop:~$    
```

---

### Post by praseodym on 2013-01-13
Which is your network? Is it "hidden"? This is no advantage for network safety, better broadcasting the ESSID and using a fixed channel.

14 channels?! Which country do you live? 14 are normally for Japan. For example, here in Germany it is 13. Please try:
```

sudo apt-get install iw
iw reg get
sudo iw reg set DE
iw reg get
```
Check again with "iwlist chan".

Replace DE for Germany with your country.

---

### Post by ChrisKjellqvist on 2013-01-13
I don't really have any internet right now so sudo apt-get doesn't work. I can tell you which of the 14 networks it is though.

edit: Under"route -n" I'm using Cell 01,, or 2WIRE615. Which is Frequency 2.412 GHz

---

### Post by praseodym on 2013-01-13
So it is mixed encryption WPA/WPA2. Better use pure WPA2, which is more stable with the network-manager and safer than mixed mode.

---

### Post by ChrisKjellqvist on 2013-01-13
Right now, WPA & WPA2 Personal is selected, I don't have any option to just use WPA in the edit connections window.

---

### Post by praseodym on 2013-01-13
You have to change the encryption mode in your router interface, see the manual for it.

---

### Post by ChrisKjellqvist on 2013-01-14
Hey, so I was just letting it try to connect and voila, it does. The only problem, as I've found out after a couple restarts, is that 1) it takes a lot of luck for it to be able to connect. And 2) whenever typing "dmesg", a few statements are repeatedd, such as "no IPv6 routers found" and something like "link is not ready". So if you could help find the problem, that would be great, Thanks.

---

### Post by praseodym on 2013-01-14
What kind of router is that? Do you kave the manual (link)?

---

### Post by ChrisKjellqvist on 2013-01-14
What do you mean by type of router. I can get the manual a little later, so it'll be a few, but I'll post when i get it.

---

### Post by praseodym on 2013-01-14
Manufacturer and model type

---

### Post by ChrisKjellqvist on 2013-01-14
It's a 2Wire 3800HGV B

Also, to add, I've solved the problem (sort of)

It works slowly but once it connects, it is great. So what I do is, unplug it (which may not be necessary), turn on the computer, do a  ```
 sudo modprobe -v ndiswrapper
```I might throw a modprobe ndiswrapper sometimes (another thing that may not be completely necessary). ALSO!!! I made sure in Network Connection editing, iPv6 is turned off. Then I'll let it try to connect a few times, then unplug then reconnect. Yesterday it connected by itself on the second time trying to connect. Today it connected instantly after I replugged it in. So like I said, it's a bit of a hassle connecting it, and I have no idea what exactly is magically causing it to connects, but something in there does.

---

