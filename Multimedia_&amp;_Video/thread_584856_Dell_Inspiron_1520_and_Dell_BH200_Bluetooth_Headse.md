---
title: "Dell Inspiron 1520 and Dell BH200 Bluetooth Headset"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by jmmkaiser on 2007-10-21
Hi,

I have gutsy installed on my inspiron 1520 and i tried to install bluetooth.
I have a k700i and that's working, but my headset bh200 isn't.
I can connect to it, but after about 30 seconds it disconnects automatically.

I followed this thread: [http://wiki.ubuntuusers.de/Bluetooth_Headset](http://wiki.ubuntuusers.de/Bluetooth_Headset)
but executing 
     hciconfig hci0 revision
in a terminal, gives me:
     hci0:   Type: USB
        BD Address: 00:19:7E: DC:F9:67 ACL MTU: 1017:8 SCO MTU: 64:8
        Firmware 40.65 / 216

but they say there should be "SCO mapping: HCI", or i should take another adapter, but i have an intern adapter.

also:
     modprobe snd-bt-sco
gives:
     FATAL: Error inserting snd_bt_sco (/lib/modules/2.6.22-14-generic/ubuntu/snd-bt-sco.ko): 
     Unknown symbol in module, or unknown parameter (see dmesg)
also:
     modprobe btsco
gives:
     FATAL: Module btsco not found.
but when i search the files with nautilus it finds it under /usr/local/bin

I've been searching and trying for two days, day and night, so please help me...:confused:

thx,
jmmk

---

