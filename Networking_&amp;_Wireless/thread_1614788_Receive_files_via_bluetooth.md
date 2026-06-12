---
title: "Receive files via bluetooth"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by vangop on 2010-11-06
Hi,
can't receive files via bluetooth whatever I do. When sending from mobile the file transfer dialog opens, but error pops up "Cannot connect to OBEX device". "Cannot copy file.. The remote system refused the network connection"
I have 
```

$ sudo dpkg -l |grep blue
ii  blueman                               1.21-2ubuntu1                                   A Graphical bluetooth manager
ii  bluetooth                             4.60-0ubuntu8                                   Bluetooth support
ii  bluez                                 4.60-0ubuntu8                                   Bluetooth tools and daemons
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  bluez-cups                            4.60-0ubuntu8                                   Bluetooth printer driver for CUPS
ii  bluez-gstreamer                       4.60-0ubuntu8                                   Bluetooth GStreamer support
ii  bluez-utils                           4.60-0ubuntu8                                   Transitional package
ii  gnome-bluetooth                       2.30.0-0ubuntu3                                 GNOME Bluetooth tools
ii  libbluetooth3                         4.60-0ubuntu8                                   Library to use the BlueZ Linux Bluetooth stack
ii  libgnome-bluetooth7                   2.30.0-0ubuntu3                                 GNOME Bluetooth tools - support library
ii  pulseaudio-module-bluetooth           1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 Bluetooth module for PulseAudio sound server
ii  python-bluez                          0.18-1                                          Python wrappers around BlueZ for rapid bluetooth development


```
Receive is enabled in file sharing
[IMG]http://i11.fastpic.ru/big/2010/1106/db/312999e2bce34f52cf8079537e2a5adb.png[/IMG]

I saw a few threads saying that I need to install obexpushd, but I'm wondering why the heck the above screen option is present in ubuntu if it doesn't work. So I want to figure out if this is possible without it.
Plz suggest.

---

### Post by vangop on 2010-11-07
Anyone?

---

### Post by uncaspi on 2010-11-07
It work for me with usb-stick bluetooth.
Anything to see in /var/log/messages

---

### Post by vangop on 2010-11-11
Update - was able to receive from Nokia phone, but not from HTC. Although HTC can send no problem to Nokia...
I have this in my auth.log
```
dbus-daemon: Rejected send message, 2 matched rules; type="method_return", sender=":1.343" (uid=1000 pid=5212 comm="/usr/bin/python) interface="(unset)" member="(unset)" error name="(unset)" requested_reply=0 destination=":1.93" (uid=0 pid=10300 comm="/usr/sbin/bluetoothd))
```
But I couldn't reproduce - the message won't appear when I send..
Silence in all other  logs.. 
Bluez shows that some data is transferred, by color bars and activity on the status bar, but same error all the time. Actually, 2 errors:
1. Cannot connect to OBEX device
followed by
2. Cannot copy file.. The remote system refused the network connection

---

### Post by sreeharsha.t on 2010-11-18
I too have the same problem with Lucid. I can send files to my Nokia phone and even can browse files in it. However, I can't receive any files phone. It says 'Unable to connect'

---

### Post by sreeharsha.t on 2010-11-18
I just made it to work, you will have to enable 'Personal File Sharing' in the Preferences>>Start up Applications.
OR, you can manually start the gnome-user-share process from:
/usr/lib/gnome-user-share/gnome-user/share

---

### Post by vangop on 2010-12-15
Hi,
Upgraded to 10.10, and tried the solution with gnome-user-share, but it didn't work. The same problem - cannot send files from some phones..

---

