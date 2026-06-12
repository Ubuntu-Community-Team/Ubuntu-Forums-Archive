---
title: "HP pavillion dv5 wireless woes"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by kbk on 2012-03-04
Hello I have been having ongoing problems getting wireless to work on my HP Pavillion Dv5 NR1017 Entertainment Series.  I have a fresh install of Kubuntu and a brand new D-Link DWA121 pico usb wireless adapter.  When I plug the device in, the light does not turn on to indicate it is enabled until I run ```
sudo ifocnfig wlan1 up
```, then the light comes on, but I still cannot detect any wireless networks in Network Manager.  I have tried a number of things to get this going with other cards, the internal wireless and am at a loss as to why none of these things work.  At this point I would like to get this Dlink adapter working as it is presently the most desirable outcome.

Thank you in advance for your help :)

---

### Post by kbk on 2012-03-04
The Dlink is definitely detected, network manager shows it is running rtl8192cu as the driver.  However, network manager's 'enable wireless' box is unclickable, and lists the device as unnavailable.  This happens whether the ethernet cable is plugged in or not.  Any ideas?

---

### Post by kbk on 2012-03-05
Bump.  Also, more relevant info.  I really need some help with this.

At this point I have been following several guides/forum posts which relate to loading the rtl8192cu driver for the device.  I have attempted to load the windows equivalent of the driver using ndiswrapper, it is installed but the device is still showing as using the built in driver.  

I have also installed a newer version of the Linux driver (found [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772]("here") I receive the following when I run:  ```
$ sudo modprobe 8192cu
FATAL: Error inserting 8192cu (/lib/modules/3.0.0-16-generic-pae/kernel/drivers/net/wireless/8192cu.ko): Device or resource busy

```

---

### Post by kbk on 2012-03-05
I appear to have gotten somewhere, running ```
sudo iwlist wlan1 scan
``` it shows me several networks that are in the area.  However, network-manager still does not allow me to check 'enable wireless' and still shows my wlan1 as 'unnavailable'  ANY HELP WOULD BE APPRECIATED.  I know you all don't know this but I have been struggling with this for almost a month now and I am nearly fed up.  I would really appreciate some sort of response, even if it's just pointing me in some direction, doesnt even have to be the right direction, I'm just at my wits end with this.

---

### Post by kbk on 2012-03-06
I fixed the problem.  You can close this thread.  As a service to others I will attempt to explain what I did.  The problem with that is that I did so many things at once that I do not quite know exactly what fixed the problem.  Here goes.

From a fresh install of Kubuntu 11.10 I removed network-manager and install wicd.  wicd was not recognizing my wireless card, however, at this point ```
sudo iwlist wlan1 scan
```
was returning several access points in my area.  Next I edited the /etc/network/interfaces file to include my wifi by adding the line:  ```
auto wlan1
```
and then rebooting.  After this wicd was seeing my wireless card AND displaying some access points.  When I attempted to connect, it hung at 'obtaining ip address'.  I figured this was due to the fact that I did not setup any WPA2 configuration on the wireless card.  For this I used ```
sudo wpa_passphrase "ssid" "psk-key" > /etc/wpakey.conf
```
Note that I had to create the wpakey.conf file before running the command.  Then I ran ```
wpa_supplicat -Dwext -iwlan1 -c/etc/wpakey.conf
``` 
while this was running I was able to open wicd and connect to my network.

I hope others find this information helpful.

---

