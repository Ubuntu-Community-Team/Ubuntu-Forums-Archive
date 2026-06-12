---
title: "turning off the dm1 Bluetooth"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by pendragyn on 2011-05-10
Hello from a newbie!

I have the dm1 3020 (the version found in most stores) with the ralink rt5390 wifi/BT card that so many people have been posting about, and would like to know how to make sure the  bluetooth is disabled. Since I don't have any BT stuff to connect and really want  to get all the battery life I can out of this thing :)  I am using Ubuntu 11.04 with KDE,  so any idea if there is a plasma widget I could use to make sure its  disabled? There is no BT icon in the notifications area on the bar.

Any help would be appreciated. Thanks.

---

### Post by josephmills on 2011-05-10
```
rfkill block bluetooth 
``` that should block it. but lets see if it did please post ```
rfkill list all 
``` thanks

---

### Post by pendragyn on 2011-05-10
thanks for replying so fast! I typed in what you suggested and got this:

rfkill list all
0: hci0: Bluetooth
        Soft blocked: yes
        Hard blocked: no

But I also did more searching in synaptic and found more BT stuff that had not been installed, that after install and restart gave me the BT icon in the notifications area. Of course there's always a chance I now have a bunch of redundant stuff installed, but I am happy for now. 

Now, should I get a BT device in the future, how do I undo the rfkill command? thanks!

---

### Post by josephmills on 2011-05-10
to unblock 
```
rfkill unblock bluetooth 
```

---

### Post by pendragyn on 2011-05-10
great thanks!  :D

---

### Post by UBoontuzilla on 2011-05-10
Could you please describe which BT stuff had not been installed? I cannot get the BT icon in notification area. When I go to menu System > Preferences > Bluetooth appears "Bluetooth is disabled". If you select "Turn On Bluetooth" nothing happened.
Thanks in advance.

---

### Post by pendragyn on 2011-05-13
Well what I have installed for bluetooth currently is:

bluedevil
blueman
bluetooth
bluez
bluez-alsa
bluez-cups
bluez-gstreamer
gnome-bluetooth
libbluedevil1
libbluetooth3
libgnome-bluetooth8
obex-data-server
pulseaudio-module-bluetooth
rfkill

This is what came up when I searched in synaptic for "bluetooth" without quotes. I am running KDE currently, which is where the issue of it not showing up in the notifications bar was a problem. And most likely I have redundant ones installed, but so far not an issue.

Hope this helps.  :)

---

### Post by nefan on 2011-05-16
Are you able to connect to bluetooth devices? I have the bluetooth icon and the device shows up with 'hcitool dev'. But if I try searching for bluetooth devices to connected to none shows up. This happens both with the bluetooth gui manager and 'hcitool scan'

---

### Post by pendragyn on 2011-05-16
Sorry but I don't own any BT devices to test it with. :(  I know other people were having issues connecting to their devices, but I don't know if they ever solved the issues. sorry.

---

### Post by nefan on 2011-05-29
A workaround is described here: [http://ubuntuforums.org/showthread.php?t=1584388](http://ubuntuforums.org/showthread.php?t=1584388). Boot in Windows, turn on bluetooth, turn off bluetooth/wifi in hardware with fn-12, and boot in Linux. See also [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/781556](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/781556)

---

### Post by UBoontuzilla on 2011-05-31
> **pendragyn said:**
> Sorry but I don't own any BT devices to test it with. :(  I know other people were having issues connecting to their devices, but I don't know if they ever solved the issues. sorry.

It didn't fix. I hope RT people read ours post :)
I installed another dongle, it detect a mobile but it cannot browse or reach other services. It seems to be a major problem with bluetooth

---

### Post by nefan on 2011-06-01
> **UBoontuzilla said:**
> It didn't fix. I hope RT people read ours post :)


I don't think there's much hope for that. I asked on the rt2x00 mailinglist where they told me to ask at the linux-bluetooth list. I did that but got no answer.

Is your problem still turning bluetooth on or is it the discovery problem? What is the output of 'hcitool dev' and 'hcitool scan'? Is btusb loaded? Sometimes '/etc/init.d/bluetooth restart' is necessary to get mine working.

---

### Post by Redblade20XX on 2011-06-05
> **nefan said:**
> I don't think there's much hope for that. I asked on the rt2x00 mailinglist where they told me to ask at the linux-bluetooth list. I did that but got no answer.

Is your problem still turning bluetooth on or is it the discovery problem? What is the output of 'hcitool dev' and 'hcitool scan'? Is btusb loaded? Sometimes '/etc/init.d/bluetooth restart' is necessary to get mine working.

The problem I have with the dm1z internal bluetooth is not turning on the bluetooth but discovering something.

```

$ hciconfig -a
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 90:00:4E:A4:63:EC  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:1579 acl:0 sco:0 events:45 errors:0
        TX bytes:1874 acl:0 sco:0 commands:43 errors:0
        Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x87
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'user-HP-dm1z-0'
        Class: 0x580100
        Service Classes: Capturing, Object Transfer, Telephony
        Device Class: Computer, Uncategorized
        HCI Version: 3.0 (0x5)  Revision: 0x1aa1
        LMP Version: 3.0 (0x5)  Subversion: 0x1aa1
        Manufacturer: Cambridge Silicon Radio (10)


```

```

$ hcitool dev
Devices:
        hci0    90:00:4E:A4:63:EC

```

```

$ hcitool info 90:00:4E:A4:63:EC
Device is not available or not connected.

```

```

$ hcitool name 90:00:4E:A4:63:EC 
Device is not available.

```

```

$ hcitool scan 
Scanning ...
$

```

Which leads me to believe that the bluez stack can't detect the combo wifi/bluetooth driver. RT5390 for wifi and Motorola BC8 3.0+ Adapter for bluetooth.

---

### Post by nefan on 2011-06-06
> Which leads me to believe that the bluez stack can't detect the combo wifi/bluetooth driver. RT5390 for wifi and Motorola BC8 3.0+ Adapter for bluetooth.

ok, my dm1 has a RT539f wifi/bluetooth combo card which might explain the differences. Apart from that, I experienced exactly the symptoms you describe (including the hcitool info and name output) but the boot in windows workaround has solved it for me.

---

