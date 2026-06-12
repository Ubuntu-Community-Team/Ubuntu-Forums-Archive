---
title: "Bluetooth dongle issues"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by lex0r on 2010-01-13
Hi!
I'm trying to make my new bluetooth dongle ([see its specs at http://dealextreme.com/details.dx/sku.11866]("http://dealextreme.com/details.dx/sku.11866")) work with the latest Ubuntu. When I plug it in Ubuntu launches the standard configuration / management applet but I cant start the device. Popup menu shows just two options - Turn off and Preferences. In the preferences I start bluetooth by pushing the big Turn on Bluetooth button but absolutely nothing happens.

hcitool dev gives
```

Devices:
    hci0    00:1F:81:00:02:50

```and 
sudo hciconfig hci0 reset gives no result as well. I've tried many variants proposed by community, but alas... :(

Any ideas?

---

### Post by lilkdub503 on 2010-02-01
I have the same dongle and problems, but now I can't even get into my Bluetooth settings. I just get one prompt of when to display some icon, then nothing. Can anyone help either of us out? I tried Synaptic, and didn't know what to do.

---

### Post by nushoin on 2011-11-07
Try this in a terminal window (or press Alt-F2 then type that):

```
sudo /etc/init.d/bluetooth restart
```

---

