---
title: "Configure wireless from commandline"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by sundar22in on 2010-03-09
How can we configure a wireless network from commandline in Ubuntu?

I understand iwlist will give us the list of access points.

Next using iwconfig it is possible to connect to a wireless network without network manager. Could you please help with details of the step to connect to a wireless network using commandline?

---

### Post by chili555 on 2010-03-09
First, it is difficult to do with Network Manager working or even installed. If you have NM removed, please read on!

Confirm your wireless card has a driver associated with it. Is there a wireless interface in *iwconfig*? If so, find the exact name of your access point with:```
sudo iwlist wlan0 scan
```Substitute your wireless interface, if it's not wlan0. You will get a result similar to this:> wlan0     Scan completed :
          Cell 01 - Address: 99:24:56:2Z:D7:89
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"

Ask your wireless interface to associate with the access point:```
sudo iwconfig wlan0 essid mylilrouter
```If there is any encryption, supply those details. Here is an example for WEP:```
sudo iwconfig wlan0 key 0123456abcd
```Now ask for an IP address:```
sudo dhclient wlan0
```WPA encryption is a bit more complex.

You can set your details in */etc/network/intefaces*:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid mylilrouter
wireless-key 0123456abcd

#auto eth0
iface eth0 inet dhcp
```

---

### Post by sundar22in on 2010-03-09
Hello,

Thank you very much for the response.

I tried the above steps.. but the DHCP client did not run successful.

I use WPA Personal encryption, so I tried editing the /etc/network/interfaces file mentioned above. Should we give the key in hexadecimal value? I gave as normal text:

wireless-key MY_KEY_AS_TEXT


Is this correct?

---

### Post by chili555 on 2010-03-09
> I use WPA Personal encryption,Remember I said WPA is a bit more complex? Please see: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by roydrager on 2010-07-21
Many thanks to Chili555 for this fix to connect wireless from the command line.  Uninstalling the network-manager package did the trick.  With network-manager installed and the NetworkManager process running in the background, all my configuration commands had no effect or resulted in crazy output.

My /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid linksys
wireless-key xxxx-xxxx-xxxx
wireless-mode Managed
auto wlan0

```

On this router it turns out I have to write the WEP key with dashes after every four characters.  Was warned about that trick in this helpful wifi doc:
  [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")  

and iwconfig showed the key formated that way when network manager was running the wifi.)

My command line commands:

```

sudo apt-get remove network-manager
sudo invoke-rc.d networking restart
iwlist wlan0 scan
sudo iwconfig wlan0 essid "linksys" mode Managed key xxxx-xxxx-xxxx
sudo dhclient wlan0

``` 

I don't know if the mode Managed was necessary but many tutorials included a mode option and iwconfig had mode Managed when NetworkManager was running it.

Anyway much simpler than many confusing older "ifupdown" methods from old documentation!  Thanks again to Chili.

---

