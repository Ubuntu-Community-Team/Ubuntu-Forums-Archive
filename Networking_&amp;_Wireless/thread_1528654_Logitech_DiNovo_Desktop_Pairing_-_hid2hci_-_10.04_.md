---
title: "Logitech DiNovo Desktop Pairing - hid2hci - 10.04 - Howto"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by slipdipper on 2010-07-11
I have and old(er) logitech dinovo desktop keyboard, mouse and mediapad. i love it! but the problem is that it was always running in hid mode. For those who dont know, your bluetooth input devices have a couple operating modes. One is hid mode where only a limited number of services are available and NO encryption is set up and the other is the more official mode where the device is actually paired to the master and encryption is set up. 

Well when you boot your computer, the BIOS doesnt have a bluetooth stack loaded up, so in order to make the keyboard/mouse usable, the system goes into this unencrypted HID mode. (Think about how secure your hard disk encryption passphrase is now). When ubuntu boots, udev is supposed to call a script called hid2hci which tells your bluetooth adapter to switch from hid mode to whats called hci mode (and pair etc..). 

If you have a logitech dinovo desktop, thats not happening cause the udev rule is broken. To make it work do the following

You may have to first install bluez and all that crap. 
```

sudo apt-get install bluetooth bluez-utils

```

copy the existing udev rule and modify it. the rules in /etc/udev/rules.d/ take precedence over the ones in /lib/udev. also if you update udev, your changes to /lib/udev will be wiped. 

```

sudo cp /lib/udev/rules.d/70-hid2hci.rules /etc/udev/rules.d/70-hid2hci.rules
sudo vi /etc/udev/rules.d/70-hid2hci.rules

```

now change this line (14) under the Logitech Devices) section:
```

KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \

```

to be:
```

ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \

```

Your life will be easier if you connect a wired keyboard at this moment, you can disconnect it when your done

i dont think you need this but:

```

echo HID2HCI_ENABLE=true >> /etc/default/bluetooth

```

Start your bluetooth daemon:
```

sudo /etc/init.d/bluetooth start

```

Once you do that you can just reload udev with:

```

sudo service udev restart
sudo udevadm trigger --verbose --subsystem-match=usb

```

after you do that, you should be able to see your bluetooth base station (or whatever) as an actual bluetooth adapter with

```

hciconfig -a

```

You may also notice ubuntu pop up with a bluetooth connect dialog, you cant use your bluetooth devices at this moment.

Using a wired keyboard (if you have a mouse, that'll help more) tab over and add your mouse, keyboard, and media pad one by one by pressing the white connect buttons on the devices and following the directions on the screen

---

