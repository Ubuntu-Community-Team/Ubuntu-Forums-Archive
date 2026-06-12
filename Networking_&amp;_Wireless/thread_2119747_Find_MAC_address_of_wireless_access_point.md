---
title: "Find MAC address of wireless access point?"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by Roasted on 2013-02-24
I had ran Kubuntu for a short time (still do now and then), but my preference is still with Ubuntu/Unity. On Kubuntu, I could see the MAC address of the wireless access point that I was connected to. On Ubuntu, I don't see anything like that. Is there any equivalent to that feature? Or would it be using some sort of iwlist command?

---

### Post by chili555 on 2013-02-24
```
sudo iwlist wlan0 scan
```...shows me:> wlan0     Scan completed :
          Cell 01 - [COLOR="Red"]Address: 99:13:10:62:8D:77[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
<snip>Some details changed for security reasons.

---

### Post by steeldriver on 2013-02-24
or nmcli

```
nmcli dev wifi list
```(doesn't need sudo) - I don't know a direct way to get ONLY the current MAC, however the BSSID is the 2nd field and the last field is 'yes' if it's the currently active AP, so you could do something like

```
nmcli dev wifi list | awk '$NF ~ /yes/ {print $2}'
```

---

### Post by chili555 on 2013-02-24
> nmcli dev wifi list | awk '$NF ~ /yes/ {print $2}'Awesome and perfect!

---

### Post by Roasted on 2013-02-24
Thank you guys for your responses. They definitely hit the money shot! I'm definitely writing these down for later. :D

EDIT - I know I marked this as solved, but I do have a question in regard to the command:

nmcli dev wifi list

I'm seeing EVERYTHING listed as 54 MB/s. But my router is a wireless N, and the GUI network manager says 117 MB/s now. Does nmcli cap at recognizing anything over 54 MB/s?

---

