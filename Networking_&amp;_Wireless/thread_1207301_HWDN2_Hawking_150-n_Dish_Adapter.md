---
title: "HWDN2 Hawking 150-n Dish Adapter"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by jualin on 2009-07-08
I just got this HWDN2 Hawking 150-n Dish USB Adapter yesterday and I have been trying to install it on Jaunty. This is my output of lsusb
> lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
**Bus 004 Device 003: ID 0e66:000b Hawking **
Bus 004 Device 002: ID 064e:a101 Suyin Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

The one in bold is what I am interested on.
I have tried using Ndiswrapper with the Windows XP and Windows Vista drivers included on the installation CD but they didn't work. Ndiswrapper recognizes that the device is present but it doesn't show on the network manager or in iwlist scan.
Any ideas of how to install this USB adapter? 
Thank you in advance

---

### Post by jualin on 2009-07-13
Anybody knows how to install this dish adapter? :lol:

---

### Post by jualin on 2009-07-26
I am still working on this. Any ideas?

---

### Post by jualin on 2009-10-10
Any ideas?

---

### Post by brianjemail on 2009-11-06
I got mines working just fine.

I used the windows XP drivers. To acquire them, I went to the Hawking's setup CD (NOT RALINK!), right-clicked on the drivers/setup.exe and selected/set "compatibility" to run as Windows XP sp2 (from a windows 7 machine). Ran the setup and snatched the drivers on Program Files\Hawking\HWDN2 Wireless LAN Card\Driver... (uninstalled from windows) copied said drivers to a thumb drive.

I followed the instructions found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Note I use "Wicd" as the wireless applet since it makes this easier. At least to set "supplicant" driver and the wireless interface. The above doc link also suggest using ndisgtk, that dint hurt either.

So follow the steps in the above doc link. By the time you get to section 3.5 (most important) the interface will come up. In my case I tailed /var/log/ messages and syslog to check it and it loaded fine. It did bring it up as "wlan1" instead of wlan0, but a quick click on Wicd Preferences will let you set change that setting. While youre in the Wicd Preferences make sure the WPA supplicant driver is set to ndiswrapper.

I will attach the drivers file to this post and send to ndiswrapper site in sourceforge.

Buena Suerte!

Brian

---

### Post by m_a on 2009-12-22
I had similar problem as original post. I have a HWDN2 rev E model, solved it with different driver (net8192su.inf).
See [http://ubuntuforums.org/showthread.php?p=8540641#post8540641](http://ubuntuforums.org/showthread.php?p=8540641#post8540641)

---

### Post by Dutedute2 on 2010-10-21
I'm using ndiswrapper to install the net8192su.inf driver. It installs properly it seems.

ndiswrapper -l
net8192su : driver installed
    device (0E66:0015) present (alternate driver: r8192s_usb)


 but iwconfig gives me this 
wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

.... and I obviously don't see any networks

and ....
sudo ifdown wlan0
ifdown: interface wlan0 not configured

 sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.


Anyone got any ideas? Please need help ... I have very little idea what to do.
I have the HWDN2 rev E

---

### Post by jualin on 2011-01-29
> **Dutedute2 said:**
> I'm using ndiswrapper to install the net8192su.inf driver. It installs properly it seems.

ndiswrapper -l
net8192su : driver installed
    device (0E66:0015) present (alternate driver: r8192s_usb)


 but iwconfig gives me this 
wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

.... and I obviously don't see any networks

and ....
sudo ifdown wlan0
ifdown: interface wlan0 not configured

 sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.


Anyone got any ideas? Please need help ... I have very little idea what to do.
I have the HWDN2 rev E

Maybe this is too late but when using the Ndiswrapper module you need to "blacklist" the alternate driver(module) "r8192s_usb."
To do this just go to the terminal and type ```
sudo gedit /etc/modprobe.d/blacklist
```

And add the following to the file : ```
blacklist r8192s_usb
```
This will disable the alternate driver and let you use the Ndiswrapper module.
Hope this helps!

---

