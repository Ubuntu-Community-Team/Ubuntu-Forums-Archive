---
title: "Broadcom BCM43xx Wireless (Fix)"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by NiGhtMarEs0nWax on 2010-08-15
Hi guys, i recently ran into problems with a BCM43xx wireless adapter on a Dell inspiron 1300 and since it took me a few hours to figure it out by piecing random bits of info; i thought i would post my findings.

This was done on lucid but will work on any 2.6 kernel afaik, since the drivers are built in as standard.

the problem for me wasn't a driver issue, it was that the card would not go into an active state. iwconfig would show my wireless adapter as enabled, but i couldn't scan for any networks.

the problem lies with the firmware on the card (or rather the lack of it), but there is a quick and easy solution. as described [**_[COLOR="Blue"]here[/COLOR]_**]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware"), firmware is required to be loaded onto the card before it can be of any use. so to do this, you need to extract the firmware from the proprietary drivers and install it. there is a tool in the repositories to do it all for you.

> sudo apt-get install b43-fwcutter

run it, it should download the proprietary driver for you, extract the firmware and install it.
**only some cards are supported**, so be sure to check, there is a list on the page i linked above. i would advise you give the whole thing a read.



i will also suggest that you uninstall network-manager and install wicd from the repositories, it seems more capable for handling wireless connections. i also had issues with wifi-radar, maybe you will have a different experience.

once network-manager has been removed and wicd installed, you will have to edit 

> /etc/network/interfaces

so that only

```

auto lo
iface lo inet loopback
```

is present. this will disable a manual configuration for your devices but still allow the loopback device. **be sure to back it up before you start changing things!**

then do.

> sudo /etc/init.d/networking restart

to restart the network service.

once that is done you can enable your device with 

> sudo ifconfig wlan0 up

assuming that wlan0 is the name of your wireless device. you can find that out with

> iwconfig


after that, you are ready to use wicd and connect to your WAP.

i hope this saves someone the trouble i had to get my card working.

GL. :)

---

