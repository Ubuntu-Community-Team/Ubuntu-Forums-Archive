---
title: "Bluetooth AVRCP with Blueman and Sony DR-BT100CX"
date: 2010-09-10
forum: Multimedia Software
---

### Post by FishFoot on 2010-09-10
Hello,

I have a Sony DR-BT100CX paired and running well on Karmic 9.10 using Blueman 1.21 and the latest Bluez package.

When I try to connect the input service I get "failed to connect" as an error message.  Initially I discovered output in the syslog that lead me to realize that I needed to use the uinput module.  I used modprobe to insert it.  Now I get the same error but no message in the syslog anymore.

I'm not certain where the error messages may be being logged or if anybody knows how to fix this.  I had a pair of Motorola headphones a while back and I believe the AVRCP controls worked correctly.

Thanks
Fishfoot

---

### Post by FishFoot on 2010-09-10
I shut off the running bluetooth service
> 
 # /etc/init.d/bluetooth stop

and ran the bluetooth daemon manually, this is the output:
> 
# bluetoothd -n
bluetoothd[15149]: Bluetooth daemon 4.61
bluetoothd[15149]: Starting SDP server
bluetoothd[15149]: Starting experimental netlink support
bluetoothd[15149]: Failed to find Bluetooth netlink family
bluetoothd[15149]: Failed to init netlink plugin
bluetoothd[15149]: bridge pan0 created
bluetoothd[15149]: HCI dev 0 registered
bluetoothd[15149]: HCI dev 0 up
bluetoothd[15149]: Starting security manager 0
bluetoothd[15149]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
bluetoothd[15149]: probe failed with driver input-headset for device /org/bluez/15149/hci0/dev_00_1B_DC_0F_58_35
bluetoothd[15149]: Adapter /org/bluez/15149/hci0 has been enabled


---

### Post by FishFoot on 2010-09-10
It looks like without me being aware, this was already working.  The "input" service that was failing was not related to AVRCP.  It appears that when I connect the a2dp service the buttons were working.

Since I'm using amarok 1.4 I needed this script:

[http://kde-apps.org/content/show.php?content=60910](http://kde-apps.org/content/show.php?content=60910)

To enable Amarok to use the multimedia keys as defined by gnome.  I need this for my multimedia keyboard as well.  Once I installed this script everything "Just works".

YAY!

---

