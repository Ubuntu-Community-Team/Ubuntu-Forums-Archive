---
title: "Tethering to nokia no-longer connects"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by bacchusmarsh on 2010-09-07
Hey,
I used to tether my nokia 3120 to my eeepc 701 in lucid no worries, but it has stopped connecting.

Now it sometimes seems to connect when i have another network connection active, ie autoeth0 or another wireless broadband modem.

This might have come about from me trying to get the tether to work via bluetooth (which worked about as frequently, so i gave up) where i changed rfcomm in order to connect. Could this be causing me a problem with my usb to phone connection, or is it unrelated?

I have reinstalled network manager and that seemed to work once but then same problem arose. I really don't wont to do a complete reinstall of ubuntu to get this working again... Is there a way to reset all the networking settings so that i can make a fresh start with this usb to phone tether?

---

### Post by bacchusmarsh on 2010-09-07
so just to clarify,
when i plug in the phone via usb it is recognised and i choose PC suite. So the usb connection seems to be ok, but it doesn't create connection like it should.
Also when i connect the same phone via usb cable to another laptop i can establish a network connection through the phone.

---

### Post by bacchusmarsh on 2010-09-07
looking back through my terminal, these are some of the things i have messed around with back when this problem started to arise:
When trying to configure a blootooth dongle to tether to my phone;
gksudo gedit /etc/dhcp3/dhclient.conf
sudo gedit /etc/bluetooth/main.conf
sudo add-apt-repository ppa:blueman/ppa
sudo gedit /etc/bluetooth/rfcomm.conf
sudo gedit /etc/init.d/rc.local

(see [this post]("http://ubuntuforums.org/showthread.php?t=1441364") for more info about the bluetooth process)

and through root terminal, when playing around with suspending power to usb devices (which seemed to work btw), i did;
echo suspend > /sys/bus/usb/devices/2-2/power/level
echo on > /sys/bus/usb/devices/2-2/power/level
(the usbs seem to work now for all other devices)

i don't think any of these should cause a change in my networking, though i wasn't sure about a couple of them

---

### Post by bacchusmarsh on 2010-09-09
Please, some help...

please...

---

