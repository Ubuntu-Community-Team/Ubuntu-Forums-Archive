---
title: "bluetooth broken upon resume from suspend"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by dutchslab on 2012-07-25
Hi-

I'm on a lenovo thinkpad w520, on ubuntu 12.04, 64bit 3.2.0-26.

When I resume from a suspend, my bluetooth is non-responsive. My BT keyboard and mouse are doa.  Wifi will reconnect, but bluetooth will not.

When this problem is happening, if I click Bluetooth Settings from the BT icon in the systray, it will delay for about 15 seconds before opening the Bluetooth Settings menu. When I click to add a BT device, it will just hang.

The only way to fix this is to reboot, and normally when I try to reboot at this point, it will hang, and I will need to do a power-off reboot.

I've searched a bit, and haven't really been able to notice any modern issues filed on this.

Any help is greatly appreciated.

---

### Post by marsanyi on 2012-08-21
Hi.  When I resume, I see a log message about this, and my Bluetooth is similarly disabled.  I find that I can re-enable it by restarting the bluetooth daemon:

```

sudo killall bluetoothd
sudo bluetoothd --udev

```

Hope this helps.

--rbt

---

