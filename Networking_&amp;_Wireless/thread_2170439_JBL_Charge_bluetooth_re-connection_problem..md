---
title: "JBL Charge bluetooth re-connection problem."
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2013-08-26
I have recently bought a JBL Charge bluetooth/portable speaker. Now I am very very happy with this device, it is awesome, I do have a problem with it too.

At first pairing all goes well, I go through the pairing sequence and behold: It works! But then the next time you turn it on,the blue led starts blinking, it beeps and then the blue led comes on full time, which should mean it is connected, but it's not. It does not show up in sound settings as an option.

The only way I can get it to work with Ubuntu is to: a) remove the JBL Charge in bluetooth settings completely. b) go through the pairing sequence...

Anybody got any tips on settings and files that control this behaviour? It would be nice to have it working every time I turn it on.

Thanks!

---

### Post by Ashrael on 2013-09-01
It works! I tried to connect and it didn't work a couple of times, then all of a sudden I get asked for a pincode, I type 0000 and now it connects every time... Why this pincode was asked of me all of a sudden as opposed to all other previous times I don't know. But it re-affirms my belief that it is/was a linux/ubuntu thing, but I still could be wrong...

---

### Post by Ashrael on 2013-09-16
Well, the joy was short lived... It worked 2 times to be exact. I do not have the same problem with my phone, so it must be an ubuntu/linux problem. The weirdest thing is that the "set up new device" doesn't do the same thing everytime. Is there no-one who knows about this stuff in detail and can help me? 

Is there a file where the settings are stored for each device?

Anyone?

---

### Post by tgalati4 on 2013-09-16
There are lots of bluetooth chips out there.  Some only allow one device to pair.  Others allow 3 devices to pair (like my Jawbone2 headset), others allow even more devices to pair.  So it's possible that your laptop's bluetooth will only allow one pairing at a time and anytime you pair it with another device it will knock off the pairing of other devices.

Of course it's possible that your JBL jambox will only allow one pairing, but since it is a new device, I assume it will allow at least 3 devices to pair with it.

Some reading:  [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

