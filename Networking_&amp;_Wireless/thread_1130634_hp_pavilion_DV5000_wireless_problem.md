---
title: "hp pavilion DV5000 wireless problem"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by amkjak on 2009-04-20
ok I installed 8.10 64bit on a hp pavilion dv5000 and I can't figure out how to get the internet to work. my light is on for the wifi but the wireless in network manager is greyed out. I need super easy terms since I have no experience in ubuntu and the help is confusing.

---

### Post by amkjak on 2009-04-20
anyone?

---

### Post by MaindotC on 2009-04-20
Please try the wireless troubleshooting guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and tell us where you have problems understanding or following the directions.

---

### Post by amkjak on 2009-04-20
ran lshw and it showed my wireless and ethernet and they were both disabled?

---

### Post by amkjak on 2009-04-20
I have a bcm4318 wireless and terminal showed that it didn't have a driver

---

### Post by MaindotC on 2009-04-20
Regarding the card being disabled - do you have it enabled in your BIOS?  If so, is there a killswitch on your machine and do you have it set to on, or could you turn it off and then turn it back on?  On my T60 I can disable/enable my wireless card using the Fn + F5 keys.  lshw shouldn't be able to detect your wireless card if these issues are present but just in case.

Secondly, find the driver you need for your card.  You may want to check linuxwireless.org or any distribution Hardware Compatibility List.  Once you figure out which driver you need, you should be able to find it for download and then the package you download should have installation instructions with it.

---

### Post by Ayuthia on 2009-04-20
If you have a working internet connection in Ubuntu, you can try going into System->Administration->Hardware Drivers and select the Broadcom b43 option.  If it is not there, you can install b43-fwcutter.  It is the same thing.

---

### Post by ma2k1 on 2010-09-09
> **Ayuthia said:**
> If you have a working internet connection in Ubuntu, you can try going into System->Administration->Hardware Drivers and select the Broadcom b43 option.  If it is not there, you can install b43-fwcutter.  It is the same thing.

Great.

On HP Pavilion DV5000 I had this problem with latest Ubuntu Lucid Lynx 10.04.
My wireless adapter wasn't recognized and is disabled.
Giving in a shell: sudo lshw 
reported (at the end):
*-network DISABLED
and also in the network manager applet wifi is disabled.
Also pressing the switch button on middle top doesn't activate the wifi.

So I have attached my pc to wired network on eth0, then on system>administration>hardware drivers I have enabled the Broadcom B43 wireless driver for my wireless adapter.
Ubuntu downloaded the correct driver and install in just two minutes. Finished I have rebooted the pc and login back on my desktop.
Now pressing the wireless button on the middle top work, blue light appear on middle top led and clicking on network manager applet all wifi connections appear :)

One click on my wifi network, key in my password and I'm on internet.

Other useful info here: [http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless)

---

