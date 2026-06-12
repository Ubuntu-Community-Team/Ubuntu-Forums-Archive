---
title: "can't get the bc4312 driver to work in xubuntu 10.04"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by Absol on 2011-09-24
Hi i realized a week after installing xubuntu 10.04 that wlan doesn't work and now i have a bunch of installed and configured things that would be very annoying to download install and configure after reinstalling ubuntu.

I installed and enabled the driver using this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
"restricted drivers" utility doesn't work by the way, it doesn't show both drivers now and the STA one doesn't activate but i installed and enabled the b43 driver using terminal commands. now it shows in iwconfig and ifconfig as wlan0.

I messed a bunch of things reinstalling, uninstalling and installing the drivers so the wlan0 adapter didn't show for a while, it shows now but i'm as i started.

In xfce4 i don't have the gnome wlan applet so i try to connect to wi-fi using iwconfig as follows:

```
sudo iwconfig wlan0 essid "linksys" key 1234567890
```
```
sudo iwconfig wlan0 essid linksys key 1234567890
```
```
sudo iwconfig wlan0 essid "linksys" key 1234-5678-90
```

none works because ap shows not associated.

```
absol@Frigg:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

furthermore the command: 

```
sudo dhclient wlan0
```

doen't grant me an ip, lynksis ap was set by me using ethernet cable and i set the wep key and the dhcp server on, i tried connecting to a bunch of other ap without success, i installed **wifi-radar** and it didn't work either.

Something else, i had in this computer ubuntu 10.04 with gnome and wlan worked poorly but still worked.

Any ideas? Anything else i can try? I really want to avoid reinstallation.

---

### Post by mörgæs on 2011-09-25
Have you tried this:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Absol on 2011-09-25
> **mörgæs said:**
> Have you tried this:
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

hi thanks for replying, i looked at it but the first solution seems to be for a newer ubuntu since i couldn't find the package and the second one is the link from my first post, it installs the driver but still it doesn't seem to work

---

### Post by mörgæs on 2011-09-25
Feel free to read further than the first post in the thread... :-)

I suggest that you take a little space from the hard drive and install 11.04 here, then use this one for experimenting.

---

