---
title: "Jaunty Ubunut 9.04 does not auto pair bluetooth ps3 keyboard after restart"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by jerez76 on 2009-07-02
bluez set up does pair up the ps3 keyboard but if it times out or the keyboard switch is turned off then it will not auto connect. So then I have to replug a usb mouse in and delete keyboard in order for it to pair up once again. If the system is rebooted then is no bt keyboard control during login. 

I've tried this with Win XP it works fine 

 I have seen how to's on older version but hcid.conf does not exist or has been deprecated.
 
So my question is how do you auto connect to  any bt device at boot up with Ubuntu 9.04?

$ locate bluetooth
/etc/bluetooth
/etc/bluetooth/audio.conf
/etc/bluetooth/input.conf
/etc/bluetooth/main.conf
/etc/bluetooth/network.conf
/etc/bluetooth/rfcomm.conf
/etc/dbus-1/system.d/bluetooth.conf
/etc/default/bluetooth
/etc/init.d/bluetooth
/etc/laptop-mode/conf.d/bluetooth.conf
...

$ gedit /etc/default/bluetooth
```

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497
HID2HCI_ENABLED=1
HID2HCI_UNDO=1

```

---

### Post by jerez76 on 2009-07-02
REQ: Jaunty BLUEZ 4.42 update!

[http://www.bluez.org/download/](http://www.bluez.org/download/)

---

### Post by jerez76 on 2009-07-03
compiling and installing bluez 4.43 and other tars definitely fixed the problems.

I recommend complaining/requesting a .deb synaptic update.

the icon bluetooth-applet is still 1.8 fedoras applet has a refresh button

after you install 4.43 other tars do a 
$ bluetoothd -n
it should say the pid and 4.43

then do 

$ bluetooth -u
this is to put it the the rules area

PS3 keyboard works at 
restart log in
relog log in
switch off and switch on it takes about 5 seconds

 AUTO CONNECT FIXED WITH Bluez 4.43

---

### Post by Elviswind on 2009-07-15
I have just about the same setup:  jaunty on a PS3 and trying to setup a PS3 keyboard.

I have a couple questions:

(1)  Are you using the Logitech MediaBoard Pro keyboard?
(2)  Do you use the Gnome Bluetooth applet to setup the keyboard?

I can pair the keyboard with the Gnome applet (using Xubuntu) but the keyboard doesn't work.  I can turn the keyboard on and off, and the connected icon in the applet will turn on and off, but the keyboard has no control over the system.

Any suggestions?  Where should I be looking for documentation?  hciconfig?  I haven't found any documentation for bluez.

---

### Post by Alfiegerner on 2009-08-30
> **Elviswind said:**
> I have just about the same setup:  jaunty on a PS3 and trying to setup a PS3 keyboard.

I have a couple questions:

(1)  Are you using the Logitech MediaBoard Pro keyboard?
(2)  Do you use the Gnome Bluetooth applet to setup the keyboard?

I can pair the keyboard with the Gnome applet (using Xubuntu) but the keyboard doesn't work.  I can turn the keyboard on and off, and the connected icon in the applet will turn on and off, but the keyboard has no control over the system.

Any suggestions?  Where should I be looking for documentation?  hciconfig?  I haven't found any documentation for bluez.


Did you get anywhere with this?  I have the same problem I think.  I've tried using blueman and I can get it to connect automattically, however I need to select connect input device every time.

I've compiled from the 4.5 version of Bluez which installed to /usr/local/sbin/bluetoothd and edited the /etc/init.d/bluetooth to point to that location.

Have I missed anything?

---

### Post by Elviswind on 2009-08-30
No, I honestly wasn't sure what I'd do with Linux on my PS3 anyways (apart from web surfing from the couch) so I set this project aside.

I guess the updated PS3 won't have the option through the OS to install a second OS.  I wonder if these means a future firmware update will remove this option from the older models as well.

---

### Post by Alfiegerner on 2009-08-31
Okay, what I did to get this working.

Updated my /etc/default/bluetooth to include the line HIDD_ENABLED=1.

Added a file /etc/bluetooth/hcid.conf with following content:

device MAC_ADDRESS {
name "Logitech Media Keyboard";
auth enable;
encrypt enable;
}

I saw a bunch of information suggesting using the program hidd to connect, which I didn't have.  I apt-get installed bluez-compat to get it.

All of the above leads to a working keyboard that comes on automatically when you touch a key / move the mouse.  

Some of the above may not be necessary.

---

### Post by jatarn on 2009-09-26
I am still having issues getting my ps3 mediaboard to connect after disconnecting and/or rebooting. I can connect using hidd --connect <address> and it is fully functioning but whenever I reboot my system it won't connect again until I call that hidd line again. I've compiled the new  bluez binaries and put the HIDD_ENABLED=1 line in /etc/default/bluetooth. I also pointed the init script to use /usr/local/sbin/bluetoothd. And following the last post I added the hcid.conf file to /etc/bluetooth/. 

Any clues to what I am missing? Do I need to modify rfcomm.conf? 

thanks for the help

---

### Post by brummbaer456 on 2009-09-27
I'm experiencing similar issues in Jaunty with a Logitech MX5500 Keyboard/Mouse Combo. They're able to connect and work great if bluetooth service is disabled, (possibly via hci2hid?) but if i start the bluetooth daemon to pair with my blackberry, i quit being able to connect. i've tried all the suggestions here (except manually upgrading bluez to new release) and tried all the modifications suggested here: [http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html) with no luck. has anyone found a solid solution to this?

---

### Post by jackolucca on 2009-10-15
I have the same problem. I try to download the last version of bluez from the site but when i try to ./configure the system say:
```
no D-Bus
```I try:
```
apt-get install dbus
```but i have already installed the last version of dbus. My ubuntu is the 9.04.
Can anybody help me?
Thanks and sorry for my english and  my question :)

---

### Post by Unkie on 2009-10-27
Hi Guys,

I wrote a script that checks every 10 seconds if there is any bluetooth device active.  This means when my Logitech Mediaboard Pro keyboard is sleeping i only have to press my RESET button and it automatically reconnect.

Howto:

[LIST]
[*]Create the keyaboard.sh file with the following command:
"*sudo nano /etc/keyboard.sh*"
[*]Put the following code in the file:
[I]while (sleep 10)
do
 sudo hidd --search > /dev/null
done[/I]
[*]Close and save the file
[*]sudo nano /etc/init.d/keyboard
[*]Put the following code in /etc/init.d/keyboard
[I]#!/bin/sh

        /etc/keyboard.sh &

exit 0[/I]
[*]Close and save the file
[*]Give both files chmod +X with chmod +x {filename}
[*]and at last: sudo update-rc.d keyboard defaults
[/LIST]
Reboot and check if it works

---

### Post by Plantface on 2010-01-28
[ deleted ]

---

### Post by Plantface on 2010-01-28
Awesome that works. It's terribly slow however even if you'd set the sleep time to 3 seconds or whatever.

Instead of:
*sudo hidd --search > /dev/null*

use:
*sudo hidd --connect AA:BB:CC:DD:EE:FF > /dev/null*

Much quicker.

---

### Post by Plantface on 2010-01-28
> **Plantface said:**
> Awesome that works. It's terribly slow however even if you'd set the sleep time to 3 seconds or whatever.

Instead of:
*sudo hidd --search > /dev/null*

use:
*sudo hidd --connect AA:BB:CC:DD:EE:FF > /dev/null*

Much quicker.
[http://blog.projectnibble.org/2010/01/28/how-to-connect-a-bluetooth-keyboard-in-ubuntu-9-04-jaunty-workaround/](http://blog.projectnibble.org/2010/01/28/how-to-connect-a-bluetooth-keyboard-in-ubuntu-9-04-jaunty-workaround/)

---

