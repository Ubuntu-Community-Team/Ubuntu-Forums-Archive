---
title: "Ubuntu probing bluetooth /dev/rfcomm? ports for modems?"
date: 2012-09-11
forum: Networking &amp; Wireless
---

### Post by summetj on 2012-09-11
I use a scribbler robot with an IPRE fluke for my classes. It is a bluetooth device running the serial port profile. On Ubuntu, I have a funky situation where the fluke does not work correctly the very first time I connect to it. Dan Walker, of BetterBots has captured all of the bluetooth data and says that Ubuntu is sending “AT+GCAP” data (AT command for a modem to “Request Complete Capabilities List”) to the fluke when first connected. This command gets the fluke into an unstable state and make it not work until rebooted (a possible problem with the fluke…but really, should custom hardware have to anticipate receiving random AT commands?)

The extra data doesn’t happen on subsequent connections to the same /dev/rfcomm* port until the laptop is rebooted. We suspect that the network manager may be the culprit. (I stay logged in until rebooting, so perhaps if a user logged out that would also trigger the network manager to re-probe?) 

Anybody here know how the network manager treats bluetooth serial ports? Any way to tell it to NOT probe the bluetooth serial port when first connected?
Thanks,
Jay

---

### Post by summetj on 2012-10-04
Thanks to Doug Harms who traced this down to the ModemManager service. If you want the ModemManger to NOT probe all of your bluetooth comm ports, you can disable it by renaming/moving the appropriate system-servers file:

```
sudo mv /usr/share/dbus-1/system-services/org.freedesktop.ModemManager.service /usr/share/dbus-1/system-services/org.freedesktop.ModemManager.service.disabled

```

---

### Post by terrapin8 on 2013-02-17
I have the same problem and tried to disable the Modem manager but it didn't make any difference.  

I am using rfcomm to connect to an external bluetooth module.  When testing using minicom, it keeps spitting out "AT+GCAP" every second or so.  I tried the method suggested here to disable the Modem manager, and rebooted the system.  But nothing changed.  Any other suggestions?  I am running Ubuntu 12.10.

---

### Post by aizelauna on 2013-03-30
I had exactly the same problem than you but with an usb device which enumerates like a cdc acm device but that not supports AT commands.

With this post and those pages :
[https://wiki.ubuntu.com/DebuggingModemmanager](https://wiki.ubuntu.com/DebuggingModemmanager)
[https://wiki.kubuntu.org/Kernel/Debugging/USB](https://wiki.kubuntu.org/Kernel/Debugging/USB)
[https://groups.google.com/forum/?fromgroups=#!topic/bugzillagnometelconnect4688-bugzillagnometelconnect4688/5eSff6NH1pk](https://groups.google.com/forum/?fromgroups=#!topic/bugzillagnometelconnect4688-bugzillagnometelconnect4688/5eSff6NH1pk)

I understood and proved that my problem was coming from the modem-manager exactly like with your problems.

But instead of definetly remove it from the system, I tried to found a way to disable its probing process only for my device.
I finally managed to disable it by using udev rules :
[www.reactivated.net/writing_udev_rules.html]("http://www.reactivated.net/writing_udev_rules.html")

I created a udev rule file :
```
sudo touch /etc/udev/rules.d/10-local.rules
```
edited it :
```
sudo gedit /etc/udev/rules.d/10-local.rules &
```
to add this line :
```
ATTRS{idVendor}=="1234", ATTRS{idProduct}=="5678", ENV{ID_MM_DEVICE_IGNORE}="1"
```

And that's it !! The modem manager stopped sending AT commands to my device and I finally managed to use it normally.
I hope it will help someone.

---

### Post by ian-l-williams on 2013-09-01
Above comment worked for me, just had to change the vendor and product ids to match what i was using (can be found using lsusb) and reloaded the rules: sudo udevadm control --reload-rules 

Thanks for the tip

---

