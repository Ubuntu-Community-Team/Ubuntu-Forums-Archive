---
title: "repeating disconnect with edimax ew-7318"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by izar on 2010-08-06
i have a usb wireless card called "edimax ew-7318"
i used it for a year and it was great- worked out of the box.

recently i've been having repeating disconnect problems
every few minutes or seconds it will disconnect and then reconnect again

in system log i get:
```
Aug  6 14:08:57 avi-laptop kernel: [ 3364.190494] usb 1-6: USB disconnect, address 32
Aug  6 14:08:57 avi-laptop kernel: [ 3364.780099] usb 1-6: new high speed USB device using ehci_hcd and address 33
Aug  6 14:09:59 avi-laptop kernel: [ 3426.212066] usb 1-6: new high speed USB device using ehci_hcd and address 35
Aug  6 14:09:59 avi-laptop kernel: [ 3426.744073] usb 2-6: new full speed USB device using ohci_hcd and address 35
Aug  6 14:10:31 avi-laptop kernel: [ 3458.812133] usb 1-6: new high speed USB device using ehci_hcd and address 36
Aug  6 14:10:31 avi-laptop kernel: [ 3459.084406] usb 1-6: configuration #1 chosen from 1 choice
Aug  6 14:10:32 avi-laptop kernel: [ 3459.460157] Registered led device: rt73usb-phy22::radio
Aug  6 14:10:32 avi-laptop kernel: [ 3459.460206] Registered led device: rt73usb-phy22::assoc
Aug  6 14:10:32 avi-laptop kernel: [ 3459.460253] Registered led device: rt73usb-phy22::quality
Aug  6 14:10:32 avi-laptop kernel: [ 3459.498636] rt73usb 1-6:1.0: firmware: requesting rt73.bin
Aug  6 14:10:32 avi-laptop kernel: [ 3459.610110] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  6 14:10:35 avi-laptop kernel: [ 3462.469551] usb 1-6: USB disconnect, address 36
Aug  6 14:10:35 avi-laptop kernel: [ 3462.784097] usb 1-6: new high speed USB device using ehci_hcd and address 37
Aug  6 14:10:37 avi-laptop kernel: [ 3465.104085] usb 1-6: new high speed USB device using ehci_hcd and address 39
Aug  6 14:10:38 avi-laptop kernel: [ 3465.376394] usb 1-6: configuration #1 chosen from 1 choice
Aug  6 14:10:38 avi-laptop kernel: [ 3465.757006] Registered led device: rt73usb-phy24::radio
Aug  6 14:10:38 avi-laptop kernel: [ 3465.758072] Registered led device: rt73usb-phy24::assoc
Aug  6 14:10:38 avi-laptop kernel: [ 3465.758839] Registered led device: rt73usb-phy24::quality
Aug  6 14:10:38 avi-laptop kernel: [ 3465.794022] rt73usb 1-6:1.0: firmware: requesting rt73.bin
Aug  6 14:10:38 avi-laptop kernel: [ 3465.902100] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  6 14:10:46 avi-laptop kernel: [ 3473.456725] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  6 14:10:47 avi-laptop kernel: [ 3474.536069] usb 1-6: USB disconnect, address 39
```etc....

it seams like a physical hardware problem but i cant find any physical fault on the card itself.

any ideas / similar problems?

---

### Post by sosroot on 2011-01-07
Hi,

have same problem since few days. Have you find solution ?

```

Jan  7 20:13:48 younes-desktop kernel: [42250.293645] usb 1-6: USB disconnect, address 38
Jan  7 20:13:50 younes-desktop kernel: [42252.121290] usb 1-6: new high speed USB device using ehci_hcd and address 39
Jan  7 20:13:50 younes-desktop kernel: [42252.279112] usb 1-6: configuration #1 chosen from 1 choice
Jan  7 20:13:51 younes-desktop kernel: [42252.553498] phy36: hwaddr 00:14:34:56:c2:21, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
Jan  7 20:13:51 younes-desktop kernel: [42252.578140] rtl8187: Customer ID is 0x00
Jan  7 20:13:51 younes-desktop kernel: [42252.581919] Registered led device: rtl8187-phy36::tx
Jan  7 20:13:51 younes-desktop kernel: [42252.582756] Registered led device: rtl8187-phy36::rx
Jan  7 20:13:51 younes-desktop kernel: [42252.590887] rtl8187: wireless switch is on
Jan  7 20:13:55 younes-desktop kernel: [42256.454017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 20:14:05 younes-desktop kernel: [42267.052628] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  7 20:14:15 younes-desktop kernel: [42277.018777] usb 1-6: USB disconnect, address 39
Jan  7 20:14:16 younes-desktop kernel: [42277.810045] usb 1-6: new high speed USB device using ehci_hcd and address 40
Jan  7 20:14:16 younes-desktop kernel: [42277.969124] usb 1-6: configuration #1 chosen from 1 choice
Jan  7 20:14:16 younes-desktop kernel: [42278.246239] phy37: hwaddr 00:14:34:56:c2:21, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
Jan  7 20:14:16 younes-desktop kernel: [42278.283829] rtl8187: Customer ID is 0x00
Jan  7 20:14:16 younes-desktop kernel: [42278.283904] Registered led device: rtl8187-phy37::tx
Jan  7 20:14:16 younes-desktop kernel: [42278.283938] Registered led device: rtl8187-phy37::rx
Jan  7 20:14:16 younes-desktop kernel: [42278.285701] rtl8187: wireless switch is on
Jan  7 20:14:20 younes-desktop kernel: [42282.174025] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 20:14:31 younes-desktop kernel: [42292.845453] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  7 20:15:22 younes-desktop kernel: [42343.491637] usb 1-6: USB disconnect, address 40
Jan  7 20:15:23 younes-desktop kernel: [42345.320039] usb 1-6: new high speed USB device using ehci_hcd and address 41
Jan  7 20:15:24 younes-desktop kernel: [42345.467847] usb 1-6: configuration #1 chosen from 1 choice
Jan  7 20:15:24 younes-desktop kernel: [42345.753353] phy38: hwaddr 00:14:34:56:c2:21, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
Jan  7 20:15:24 younes-desktop kernel: [42345.793400] rtl8187: Customer ID is 0x00
Jan  7 20:15:24 younes-desktop kernel: [42345.793476] Registered led device: rtl8187-phy38::tx
Jan  7 20:15:24 younes-desktop kernel: [42345.793510] Registered led device: rtl8187-phy38::rx
Jan  7 20:15:24 younes-desktop kernel: [42345.794527] rtl8187: wireless switch is on
Jan  7 20:15:28 younes-desktop kernel: [42349.683989] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  7 20:15:38 younes-desktop kernel: [42360.250112] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by PatchesTheCaveman on 2011-01-07
Hi sosroot!  Try this:
[http://ubuntuforums.org/showpost.php?p=10317609&postcount=2](http://ubuntuforums.org/showpost.php?p=10317609&postcount=2)

---

### Post by sosroot on 2011-01-08
it treats the symptoms not the disease, but I'll watch.

Thanks [PatchesTheCaveman]("http://ohioloco.ubuntuforums.org/member.php?u=922660").

---

### Post by PatchesTheCaveman on 2011-01-08
If unblocking fixes your problem, add the unblock command to your */etc/rc.local* file right above the *exit 0* line.  That will unblock it every time you start Ubuntu.  Omit the *sudo* because system startup scripts always run as superuser.

---

