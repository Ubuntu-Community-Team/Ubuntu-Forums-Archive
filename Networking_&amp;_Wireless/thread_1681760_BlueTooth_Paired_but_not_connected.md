---
title: "BlueTooth: Paired but not connected"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by frogotronic on 2011-02-04
Hello,

  Trying to attach my Motorola Bravo (Android 2.1) phone to my Ubuntu 10.04.1 LTS Laptop via Bluetooth.  Can see the phone "pair" to it.  But If I try to do the transfer of files, or browse (using the bluetooth applet), I can't see the phone.

  What's going on?

- CH

-------------------------------------------------------

Where are the configuration files for bluetooth in Lucid?

---

### Post by timjohn7 on 2011-02-11
Same problem with HTC Desire HD. When either machine asks for PIN entry, the connection process appears to break down. Any advice welcome!

---

### Post by frogotronic on 2011-02-11
> **timjohn7 said:**
> Same problem with HTC Desire HD. When either machine asks for PIN entry, the connection process appears to break down. Any advice welcome!

I'm using the Bluetooth PPA packages and have switched to using the "BlueMan" GTK package.

```
sudo add-apt-repository ppa:bluetooth/ppa
sudo apt-get update && upgrade
sudo apt-get install blueman
``` 

And then, **apparently** using this software [PDANet]("http://www.junefabrics.com/android/") and an USB cable **or** bluetooth, one can tether your Android cell phone to your laptop and gain Internet access.  I haven't done this yet.

- CH

---

### Post by mogdad on 2012-01-21
Thanks for this. Now my I-touch Arrow bluetooth headset works with Skype. Nice.

---

