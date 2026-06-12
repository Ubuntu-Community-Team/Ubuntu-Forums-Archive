---
title: "Wifi issues with Atheros AR8162"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by iprolonged on 2012-11-19
Hi there,

Just did a clean install of 12.04 on a brand new Lenovo notebook. During the install I was unable to connect to my wifi, so just ignored and continued. Once the install was complete I clicked on the wifi symbol from the desktop, but couldn't see any networks. I tried connecting to a hidden network using SSID of my local wifi, and seemed to connect after requesting credentials.

I fired up Firefox and actually managed to hit the Firefox/Ubuntu start page, but then I saw the network disconnect, and after a few seconds it asked me for the wifi password again. That's the last I've seen of Internet connectivity! FWIW, I also don't seem to have a wired connection?

lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)

rfkill list all
0: ideapad_wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
1: ideapad_bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

iwconfig
lo no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:off/any Mode:Managed Access Point: Not-Associated Tx-Power=19 dBm Retry long limit:7 RTS thr:off Fragment thr:off Power Management:off

To my (uneducated) eyes this seems to be an issue between Ubuntu and my wireless router, but I don't really know where to begin tbh! Appreciate any and all suggestions.

Many thanks.

Dave

---

### Post by ahallubuntu on 2012-11-19
First of all, you need to figure out which wireless card/chipset you have.  The Atheros AR8162 is not your wireless card, it's the wired ethernet card.

Try this:

```
sudo lshw -C network
```

and show the results here.

Make sure the wireless card is enabled - there's usually either a hardware toggle switch for that or a function key combo to toggle between enabled/disabled.

Also, what's the exact model of the Lenovo?

---

### Post by iprolonged on 2012-11-20
Hi ahallubuntu, thanks for the response. Output is attached.

The machine is a Lenovo G580.

---

### Post by ahallubuntu on 2012-11-20
You have a Broadcom BCM4313 wireless chipset.

There are some known remedies for Broadcom cards (see the "sticky" about Broadcom cards at the top of the Network threads here).  

There are also these threads specifically tagged with your card:

[http://ubuntuforums.org/tags.php?tag=bcm4313](http://ubuntuforums.org/tags.php?tag=bcm4313)

and this thread might do it:

[http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)

---

### Post by iprolonged on 2012-11-20
Thanks again ahallubuntu.

The steps seem straightforward, but I have the additional difficulty of having no Internet access on the new machine: is it possible to download the required packages to a Windows machine, then transfer them via USB?

Alternatively, if you had any suggestions on fixing the wired connection that would be great as well! :)

---

### Post by ahallubuntu on 2012-11-20
First of all, read this (go to answer #4).  It addresses an almost identical Lenovo laptop (same network devices):

[http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126)

The poster there suggests your WiFi switch may be "off" because the driver is in fact loaded.  There's also some help offered for your wired card, once you get online (somehow).

You can alternately try this - scroll down to the section titled "No Internet Access."

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

I normally recommend new users stick with the LTS version (12.04) when starting out, but in this case I might recommend you try 12.10 - at least try booting the live CD - and hope all is working in that newer version, just because that's probably a lot less hassle if so.  The downside is: 12.10 is only supported until April 2014.

---

### Post by iprolonged on 2012-11-20
Will give 12.10 a whirl and hope for the best!

Thanks for all your assistance.

---

### Post by iprolonged on 2012-11-20
12.10 didn't work, but I gave the "STA - No Internet access" instructions a go and IT WORKED :)

Thanks again!

---

