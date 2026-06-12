---
title: "wireless link up but no connectivity"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by gsaro on 2013-06-25
I have a core i3 PC with dual boot  Wndows 7 and Ubuntu 12.04. My eth0 is working. but no wlan connectivity.I have a DWA-125 D-linkwireless adaptor. I followed forum posts and have lost track of all modifications. Finally reinstalled Ubuntu by formatting only root. The problem persists. I am posting the outputs i get after following the instuctions on [http://ubuntuforums.orgshowthread.php?t=1425564](http://ubuntuforums.orgshowthread.php?t=1425564).  Any help will be appreciated


```
user:~$sudo modprobe rt3070sta
FATAL: Module rt3070sta not found.

```
```
user:~$ iwconfig
lo        no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off        
eth0      no wireless extensions.

```

```
user:~$ dmesg | grep -e rt2 -e rt3
[   19.627768] Registered led device: rt2800usb-phy0::radio
[   19.627783] Registered led device: rt2800usb-phy0::assoc
[   19.627797] Registered led device: rt2800usb-phy0::quality
[   19.627814] usbcore: registered new interface driver rt2800usb
[   19.821407] rtusb init rt2870 --->
[   19.821440] usbcore: registered new interface driver rt2870
```
```
user:~$ lsusb
......
Bus 001 Device 005: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
......
```

```
user:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [user] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           no
  HW Address:        1C:BD:B9:81:3A:8F

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *user:            Infra, 00:FD:07:9C:78:5B, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WEP

  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.185.0.23
    DNS:             59.179.243.70
    DNS:             203.94.243.70


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        70:71:BC:3C:3D:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.185.0.23
    DNS:             59.179.243.70
    DNS:             203.94.243.70
```

---

### Post by chili555 on 2013-06-25
Please detach the ethernet and try again.> - Device: wlan0  [user] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           no
  HW Address:        1C:BD:B9:81:3A:8F

  Capabilities:
    Speed:           54 Mb/s
    [COLOR="#FF0000"]Wireless Properties[/COLOR]
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *user:            Infra, 00:FD:07:9C:78:5B, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WEP

  IPv4 Settings:
    [COLOR="#FF0000"]Address:         192.168.1.85[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.185.0.23
    DNS:             59.179.243.70
    DNS:             203.94.243.70


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        70:71:BC:3C:3D:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  [COLOR="#FF0000"]Wired Properties[/COLOR]
    Carrier:         on

  IPv4 Settings:
    [COLOR="#FF0000"]Address:         192.168.1.13[/COLOR]
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.185.0.23
    DNS:             59.179.243.70
    DNS:             203.94.243.70It is impossible to troubleshoot wireless connectivity problems when you are connected with ethernet. 

:confused:  :confused:

---

### Post by gsaro on 2013-06-25
:) Ok. The various outputs with ethernet disconnected is given below.

```
user:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"user"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:FD:07:9C:78:5B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:909   Missed beacon:0

eth0      no wireless extensions.
```

```
dmesg | grep -e rt2 -e rt3
[   19.732914] Registered led device: rt2800usb-phy0::radio
[   19.732930] Registered led device: rt2800usb-phy0::assoc
[   19.732944] Registered led device: rt2800usb-phy0::quality
[   19.732959] usbcore: registered new interface driver rt2800usb

```

```
user:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [user] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        1C:BD:B9:81:3A:8F

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *user:            Infra, 00:FD:07:9C:78:5B, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WEP

  IPv4 Settings:
    Address:         192.168.1.85
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.185.0.23
    DNS:             59.179.243.70
    DNS:             203.94.243.70


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        70:71:BC:3C:3D:BC

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off
```

---

### Post by chili555 on 2013-06-25
> wlan0     IEEE 802.11bgn  ESSID:"user"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:FD:07:9C:78:5B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm  *Now* you look well and truly connected! Can you scan?```
sudo iwlist wlan0 scan
```Ping?```
ping -c3 8.8.8.8
ping -c3 192.168.1.1
ping -c3 www.google.com
```

---

### Post by gsaro on 2013-06-25
Thank you for your reply. The outputs for the two commands are given below

   ```
 :~$ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.85 icmp_seq=1 Destination Host Unreachable
From 192.168.1.85 icmp_seq=2 Destination Host Unreachable
From 192.168.1.85 icmp_seq=3 Destination Host Unreachable
```


```
:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:FD:07:9C:78:5B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"mywlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013c8b146d5
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0003706164
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: 00:FD:07:9C:78:5B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013c897775c
                    Extra: Last beacon: 1768ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

---

### Post by chili555 on 2013-06-25
Ahh! You are trying to connect to a hidden network. Is the 192.168.1.85 address one that was assigned by the router or did you set a static IP address? Did it by chance connect and then drop? Are there any clues here?```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n25
```

---

### Post by gsaro on 2013-06-26
> **chili555 said:**
> Ahh! You are trying to connect to a hidden network. Is the 192.168.1.85 address one that was assigned by the router or did you set a static IP address? Did it by chance connect and then drop? Are there any clues here?

Sir,
 I set a static IP. It had connected and dropped when the IP V.6 address was DHCP. Presently I am ignoring IP V6 addressing. I have also recently changed from WPA-WPA2 to WEP 128bit. There is no problem on my laptop running the same version of ubuntu with WEP. I am attaching output for 
```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n25
```

---

### Post by chili555 on 2013-06-26
In syslog, it appears to connect perfectly well. We see no reason why it doesn't connect as expected or any evidence that it connects and drops. With no clues, we don't know what to try to fix! I suggest we dig a bit deeper. Please detach the ethernet cable, reboot so we have a clean slate and before anything else:```
cat /var/log/syslog | egrep  'rt2|cfg8|etwork|wlan' | tail -n100 > gsaro.txt
```Find the file gsaro.txt in your user directory and paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by gsaro on 2013-06-26
Sir,
I have rebooted my PC and executed the following code in my terminal.```
 cat /var/log/syslog | egrep  'rt2|cfg8|etwork|wlan' | tail -n100 > gsaro.txt 
```. The link to gsaro.txt is          [http://paste.ubuntu.com/5801815/](http://paste.ubuntu.com/5801815/) 

I am also not very sure about my /etc/Wireless/RT2870STA/RT2870STA.dat . I am pasting  the contents of the said file at [http://paste.ubuntu.com/5802490/](http://paste.ubuntu.com/5802490/)

Also I rebooted my PC in network recovery mode, and saw the following message displayed twice. 
>  modem-manager[954] : <info>  (ttSy) closed serial port


Thanks for  your help.

---

### Post by chili555 on 2013-06-27
Again, we see it connect seemingly perfectly. We see no disconnect or irregularities. What happens if you attempt to surf the webb immediately after a boot? What does this say?```
nm-tool
```If you can surf, does it eventually disconnect? *That's* the syslog I'd love to read:```
cat /var/log/syslog | egrep  'rt2|cfg8|etwork|wlan' | tail -n100 > gsaro_disconnect.txt
```> I am also not very sure about my /etc/Wireless/RT2870STA/RT2870STA.dat .RT2870STA.dat is not used by the stock in-kernel rt2800usb. It is used by staging versions of rt2870sta which usually need to be compiled from source code? Did you try and fail to do so? Do we have a driver conflict going?

---

### Post by gsaro on 2013-06-27
[FONT=arial]Sir,

The output of nm-tool immediately after boot is at [http://paste.ubuntu.com/5804983/](http://paste.ubuntu.com/5804983/)
I am not able to ping modem  immediately after boot.
[/FONT]
[FONT=arial]The output of  cat /var/log/syslog | egrep  'rt2|cfg8|etwork|wlan' | tail -n100 is at [http://paste.ubuntu.com/5804993/](http://paste.ubuntu.com/5804993/)
Regarding the driver , I had compiled without errors. To enable at boot-time I had pasted [/FONT][COLOR=#0000ff]alias ra0 rt2870sta [/COLOR][FONT=arial]in /etc/modules since I did not have a [/FONT]
[FONT=arial] /etc/modules.conf file. Also I did not find any /etc/sysconfig/network-scripts/ folder so could not  add "DEVICE='ra0'   ONBOOT='yes' " [/FONT]as mentioned in readme. 
[FONT=arial]Here I would like to mention that connectivity was fine after ubuntu installation till this problem occured and that too without installing any driver.
[/FONT]

---

### Post by chili555 on 2013-06-27
Well, that's the trouble with source code downloaded from the manufacturer. It's one size maybe fits all along with the assumption that if you are fiddling around with source code, you probably know that some differences may exist from one Linux distribution to another. The items in the README are very Fedora like which is a different thing from Ubuntu which is Debian-based. > alias ra0 rt2870sta However, it is not in use, since the driver being used is:> usbcore: registered new interface driver [COLOR="#FF0000"]rt2800usb[/COLOR]And the interface in use is not ra0, but:> NetworkManager[893]: <info> ([COLOR="#FF0000"]wlan0[/COLOR]): new 802.11 WiFi device (driver: 'rt2800usb' ifindex: 3)Let's check a little deeper:```
lsmod | grep rt2
iwconfig
```Are you certain your paste is after the wireless drops or does it never surf? It looks perfect.

---

### Post by gsaro on 2013-06-27
```
lsmod | grep rt2
```
The output of above code is 
  ```
[COLOR=#ff0000]rt2[/COLOR]800usb              22373  0 
[COLOR=#ff0000]rt2[/COLOR]800lib              53298  1 [COLOR=#ff0000]rt2[/COLOR]800usb
crc_ccitt              12627  1 [COLOR=#ff0000]rt2[/COLOR]800lib
[COLOR=#ff0000]rt2[/COLOR]x00usb              20099  1 [COLOR=#ff0000]rt2[/COLOR]800usb
[COLOR=#ff0000]rt2[/COLOR]x00lib              48875  3 [COLOR=#ff0000]rt2[/COLOR]800usb,[COLOR=#ff0000]rt2[/COLOR]800lib,[COLOR=#ff0000]rt2[/COLOR]x00usb
mac80211              436493  3 [COLOR=#ff0000]rt2[/COLOR]800lib,[COLOR=#ff0000]rt2[/COLOR]x00usb,[COLOR=#ff0000]rt2[/COLOR]x00lib
cfg80211              178877  2[COLOR=#ff0000] rt2[/COLOR]x00lib,mac80211

```

---

### Post by chili555 on 2013-06-27
As you can see, you only have rt2800usb loaded and not rt2870sta. I suggest you remove the erroneous settings from /etc/modules and reboot.

Again:> What happens if you attempt to surf the web immediately after a boot?
....
Are you certain your paste is after the wireless drops or does it never surf? 

---

### Post by gsaro on 2013-06-27
_and the output of iwconfig is  _==>

[HTML]lo        no wireless extensions.
 
wlan0     IEEE 802.11bgn  ESSID:"mywlan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:FD:07:9C:78:5B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:414   Missed beacon:0
 
eth0      no wireless extensions.[/HTML]

I removed the entry from /etc/modules and rebooted.  Ping to 192.168.1.1 immediately after booting gives  " Destination Host Unreachable".

---

### Post by chili555 on 2013-06-27
> wlan0     IEEE 802.11bgn  ESSID:"mywlan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:FD:07:9C:78:5B   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  [COLOR="#FF0000"]Invalid misc:414[/COLOR]   Missed beacon:0^^^The highest I've seen ever. I'm not at all sure what causes it. Let's try to update the driver the correct way. Get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot without the ethernet cable and let us hear your results.

You have a very sticky problem there!

---

### Post by gsaro on 2013-06-28
> **chili555 said:**
> ^^^The highest I've seen ever. I'm not at all sure what causes it. Let's try to update the driver the correct way. Get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot without the ethernet cable and let us hear your results.

You have a very sticky problem there!
I have done as told and this is the [COLOR=red]o/p of iwconfig[/COLOR]

          ```
wlan0     IEEE 802.11bgn  ESSID:"mywlan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:FD:07:9C:78:5B   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Managementn
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0 [COLOR=red]Invalid misc:22[/COLOR]   Missed beacon:0
```

---

### Post by gsaro on 2013-06-28
Sir,

Finally it has started working. I had uninstalled the driver. still no connection. Then i changed my security to WPA&WPA2 personal. I am able to surf now. 

Thank you for your valuable time. It never occured that encryption must be the problem because I was able to connect.
Thank you once again

---

### Post by chili555 on 2013-06-28
I'm very glad it's working by whatever means. Have fun!

---

