---
title: "bluetooth not working in kubuntu"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by gagansinghjarry on 2009-05-16
well the thing is when ever i try and launch kdebluetooth4 from kmenu nothing happens i am told that i am supposed to see a tray icon i dont see anything not even a window when i run it from a terminal here is what it says 
sony@sony-vaio:~$ sudo kbluetooth4
Error: "/var/tmp/kdecache-sony" is owned by uid 1000 instead of uid 0.
kbluetooth4(10727) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "BlueZ"
kbluetooth4(10727) KBlueTray::offlineMode: offline Mode

here is what my pc says on the command hciconfig

sony@sony-vaio:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:19:C1:9D:87:92 ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING PSCAN
        RX bytes:1083 acl:0 sco:0 events:42 errors:0
        TX bytes:428 acl:0 sco:0 commands:42 errors:0

oh and when i open system activity to check for it it appears to be running there appears to be an entry by the name kbluetooth4
so i think it gets launched but it doesn't show i already have the necessary bluez packages

---

### Post by AlanR8 on 2009-05-16
I have an interest in this thread as well. Sony VGN-FZ21S but unlike you I get the icon that allows me to name the device and search for devices. This is as far as I get. The search for devices produces nothing!

Here's the contents of my hciconfig:

> Type: USB
        BD Address: 00:1B:FB:58:C5:F8 ACL MTU: 1021:6 SCO MTU: 64:1
        UP RUNNING
        RX bytes:187 acl:0 sco:0 events:23 errors:0
        TX bytes:580 acl:0 sco:0 commands:23 errors:0

Any ideas?

---

### Post by gagansinghjarry on 2009-05-16
well anybody got any ideas

---

### Post by AlanR8 on 2009-05-30
Odd

Have just managed to connect my Nokia Navigator by blue tooth! The Phone did the pairing and I CAN'T see the phone from the computer, yet I can, and did transfer files from both.

Then rebooted and it won't reconnect! 

The blue tooth icon in the task tray gives the option to name the adapter and state it's state, hidden or discoverable. It defaults to hidden so I changed it to discoverable, clicked OK and all seemed well. However, going back into the adapter page, the change has NOT been saved.

How can I do that? is there a .conf file to edit?

---

