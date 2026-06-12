---
title: "Bluetooth Headphones Connection"
date: 2020-10-21
forum: Multimedia Software
---

### Post by t0n11 on 2020-10-21
Good morning everyone,


after many years of Linux abstinence I recently came back to the Ubuntu camp and feel very comfortable except for a small problem. I hope you can help me with this problem. I use Ubuntu 20.04 LTS with Gnome Desktop. 


I often use Bluetooth headphones, which cause difficulties in establishing a connection under Ubuntu. It always works like this:



[LIST]
[*]I switch on Bluetooth & headphones.
[*]I move the slider to the right in the Ubuntu settings, an attempt to connect follows.
[*]The graphic suggests that there is a connection, the headphone does nothing.
[*]I switch off Bluetooth & headphones and switch them on again.
[*]Now the connection is established as described above. But I always need the loop on &#8594; off &#8594; on again, then it works.
[/LIST]


I hope I could describe the problem understandably. Please let me know which screenshots or terminal output you need to narrow down the problem. If an upgrade to 20.10 or a switch to another *buntu could help, that would be ok for me, too.


Thanks a lot for your help &#128522;


Translated with [www.DeepL.com/Translator](www.DeepL.com/Translator) (free version)

---

### Post by mIk3_08 on 2020-10-21
Try to run this command in your terminal 
```
dmesg | grep -i 'bluetooth'
```
and paste the result here in this thread wrap with code.

---

### Post by t0n11 on 2020-10-21
Hi [COLOR=#000000]mIk3_08, 

[/COLOR]thanks for your answer. Here we go:

```
toni@toni-Lenovo-V130-15IGM:~$ dmesg | grep -i "bluetooth"[    3.191715] Bluetooth: Core ver 2.22
[    3.191736] Bluetooth: HCI device and connection manager initialized
[    3.191741] Bluetooth: HCI socket layer initialized
[    3.191744] Bluetooth: L2CAP socket layer initialized
[    3.191747] Bluetooth: SCO socket layer initialized
[    3.239293] Bluetooth: hci0: read Intel version: 370810011003110e00
[    3.240060] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    3.566280] Bluetooth: hci0: unexpected event for opcode 0xfc2f
[    3.583318] Bluetooth: hci0: Intel firmware patch completed and activated
[    5.050762] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.050765] Bluetooth: BNEP filters: protocol multicast
[    5.050771] Bluetooth: BNEP socket layer initialized
[   20.973346] Bluetooth: RFCOMM TTY layer initialized
[   20.973354] Bluetooth: RFCOMM socket layer initialized
[   20.973364] Bluetooth: RFCOMM ver 1.11
[  179.668608] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  179.668625] Bluetooth: HIDP socket layer initialized
[  185.986528] input: hi Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-6/1-6:1.0/bluetooth/hci0/hci0:256/0005:05D6:000A.0002/input/input17
[  185.986699] hid-generic 0005:05D6:000A.0002: input,hidraw1: BLUETOOTH HID v2.40 Device [hi] on 0c:7a:15:6a:29:ed



```

---

### Post by mIk3_08 on 2020-10-22
try to Updated /etc/bluetooth/main.conf AutoEnable=false
the main setting was true


Stop and disabled the service 

run this command in your terminal;
```
systemctl stop bluetooth.service 
```
```
systemctl disable bluetooth.service
```
Then logout or restart. 

Then try to use Bluetooth App like BlueMan or anything that best suits your needs.

---

### Post by t0n11 on 2020-10-22
Hello mIk3_08,

thanks again for your help. After doing [FONT=courier new]systemctl stop bluetooth.service[/FONT] and [FONT=courier new]systemctl disable bluetooth.service[/FONT], bluetooth was no more availeble in Gnome Settings after restart. I had to do [FONT=courier new]systemctl start bluetooth.service[/FONT] to get it to work again. So I had no luck with that way.

---

### Post by mIk3_08 on 2020-10-23
Did you try to use any Bluetooth app, to connect with your device?
During your system restart, try to run this command in your terminal when the system starts normally. just make sure your system starts with Bluetooth is off.

```
systemctl --user enable obex
```

---

### Post by t0n11 on 2020-10-23
Will try this. 
I just had to say: The problem occurs only with that one Headphones, with other Bluetoothdevices and Soundbars it works just fine.

---

### Post by mIk3_08 on 2020-10-24
It maybe that headphone had a problem with the compatibility issue.

---

