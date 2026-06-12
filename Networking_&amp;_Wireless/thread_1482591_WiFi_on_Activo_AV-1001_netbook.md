---
title: "WiFi on Activo AV-1001 netbook"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by bscott on 2010-05-13
Just wanted to mention this in case someone else comes across the problem -

I put Ubuntu 10.4 Netbook Remix Edition on a fairly-new model netbook Activo AV-1001-1Y and everything worked well except the wireless networking - it seemed to be available but would not connect.

The wifi is based on the Realtek RA2870 chipset (the supplier says it's the NT2070?) and some searching revealed that's got a few problems in Ubuntu with drivers clashing.  But in the end I had to mix two fixes to get things working - the first was found here [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) and allows me to blacklist the non-rt2870a drivers, while the second at [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6) seems to let you inform the correct driver that it can manage this chipset without having to recompile anything.

I'm about a medium-skilled user so I don't fully understand all of this, but it worked - here's the first part:
```
# part one of fix - blacklist conflicting driver
echo '# fix for Activo wifi' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist rt2x00usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist rt2x00lib' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Now you reboot (because you can't unplug an internal USB device...) and then here's the second part - I've changed the USB ID to match what you find in the Activo:

```
# part 2 - make sure right driver recognizes Wifi chipset as something it should manage
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
# dmesg | egrep 'rt28|usb|Phy'
iwconfig

echo rt2870sta | sudo tee -a /etc/modules
```

Hope this helps someone!

---

