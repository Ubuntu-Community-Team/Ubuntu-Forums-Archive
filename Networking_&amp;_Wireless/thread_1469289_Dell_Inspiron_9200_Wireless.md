---
title: "Dell Inspiron 9200 Wireless"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Jamkel on 2010-05-02
Hi all,

I'm new to Linux and wanted to try this new version of Ubuntu, the installation went perfect and fast! The only issue that i seem to be getting is with my wireless. I updated drivers which found the card and downloaded the drivers. I checked this by going into System > Administration > Hardware Drivers > Broadcom B43 wireless driver is shown with a green circle.
I can see the wireless icon show up if I have no network cable connected but no matter what I try I cant connect, I have downloaded wifiradar and WICD Network Manager which also cannot show me any wireless networks! The short cut on the keyboard to start the wireless does not work however the network icon on the top right will allow me to turn it off or on again.

If I run IWCONFIG i receive the following:

james@james-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

With the wireless enabled I typed IWLIST WLAN0 SCAN into terminal I get:

james@james-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

The only other thing I can add is that my wireless network at home runs from a BT home hub 2.0 (the black one) The SSID is not hidden and has a WPA access key.

Hopefully someone has an idea which can help me out! 
Thanks in advance for your help!

James



EDIT:

Ok so reading through google I found a few Terminal commands to try!

I ran sudo ifconfig wlan0 down which obviously took my WiFi light down, then i waited a few seconds and type sudo ifconfig wlan0 up which brought it back to life then as by magic i started to be able to view wireless networks around me! I then attempted to remove the WICD network manager to see if i needed it, however upon doing so it borked the WiFi again reinstalling it fixed it again!

I'm just wondering now if anyone has any idea why i need this application to sit alongside the build it connection manager?

like before thanks in advance!

---

