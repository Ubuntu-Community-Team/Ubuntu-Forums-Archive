---
title: "bluetooth-applet does not show in systray"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2009-10-24
It was there after I installed Karmic, but I think I screwed it up. Rhythmbox hung so I used XKill to try and kill it. Instead, I killed systray and when it reloaded bluetooth-applet was gone an I can't get it back. It appears to be running:

$ ps -e|grep -i blue
   29 ?        00:00:00 bluetooth
 2317 ?        00:00:00 bluetooth-apple

but it does not show in systray. If I try System>Preferences>Bluetooth the box is checked to show the icon. That app says no adapters present. If I kill bluetooth-applet and attempt to restart it, I get the following:

$ bluetooth-applet
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

and it hangs there without displaying the icon. If I use bluetooth-applet & it starts but does not display the icon. The device is an Everun Note. Relevant dmesg entries are as follows:

$ dmesg|grep -i bluetooth
[    0.204013] Bluetooth: Core ver 2.15
[    0.204043] Bluetooth: HCI device and connection manager initialized
[    0.204043] Bluetooth: HCI socket layer initialized
[    0.908821] Bluetooth: L2CAP ver 2.13
[    0.908824] Bluetooth: L2CAP socket layer initialized
[    0.908828] Bluetooth: SCO (Voice Link) ver 0.6
[    0.908831] Bluetooth: SCO socket layer initialized
[    0.908894] Bluetooth: RFCOMM TTY layer initialized
[    0.908899] Bluetooth: RFCOMM socket layer initialized
[    0.908902] Bluetooth: RFCOMM ver 1.11

When I do an hcitool scan or dev it says no devices found. I was thinking that if the app would show up in systray I could change to the correct device in preferences and get BT going. Also, FWIW, BT works under Win XP and I can connect a BT mouse. Thanks.

**UPDATE. I found that BT was switched off. Fn+3 switched it back on and the bluetooth-applet reappeared in systray

---

