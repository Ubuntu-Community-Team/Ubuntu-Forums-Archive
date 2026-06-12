---
title: "Help on setting up an Ad-Hoc Wireless Connection with ICS through ethernet"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by SilverGold on 2009-05-20
Hello.

I have a HP NC8430 Laptop with Ubuntu Jaunty with the 2.6.30-rc6 kernel.
I also installed Wicd because it is more stable than gnome-network-manager.
When I plug a cable into the ethernet port, my wireless is disabled automatically.
I would like to know how to set it up so that I would have a working wireless while the ethernet cable is plugged in.
I want to do this because I want to share my ethernet connection (Static IP) through a wireless dhcp ad-hoc connection.

My ethernet device is a "Broadcom NetExtreme Gigabit Ethernet" and my wireless card is an "Intel(R) PRO/Wireless 3945ABG Net"

I am quite new in the world of Tux, but I am not afraid of the terminal.

Any help will be appreciated. Thanks in advance.

---

### Post by SilverGold on 2009-05-25
I can see how helpful this forum is. :(

Thank you for your support. :(

Geez ... you could at least have said something! :(

That's why people stick to Windoze. They don't have any kind of support from the Linux world. :(

---

### Post by five_13 on 2009-05-25
Hi Silver,
I am also new here (by posts) and have found interest in your problem, as I too tried to hook up to a friend's laptop with mine so that I could use his I-net connection.
I connected through cable, while he was using Wlan to access the school's network.

Theoretically the "host" should maybe bridge the two connections, right?

---

### Post by kevdog on 2009-05-25
Use google to tell me if your intel chipset -- you've provided that above -- does monitor mode.  Monitor mode is basically a way to have your card act more like an access point, rather than a client -- which is referred to as Managed Mode.  If your card can do this, then its simple to make a few rules within iptables to allow for forwarding of packets within the gateway machine.

Im no expert with intel chipsets since Ive never owned this particular chipset.

---

### Post by SilverGold on 2009-05-25
I just checked the terminal.

```
silvery-corgan@Silvery-Corgan-Laptop:~$ iwconfig -h
Usage: iwconfig [interface]
                interface essid {NNN|any|on|off}
                interface mode {**[COLOR="Red"]managed[/COLOR]**|ad-hoc|master|...}

```

And I just ran a ```
sudo iwconfig wlan0 mode managed
``` and it had no output (guess that means it works).

I don't have any idea how to test this any more but if this is not the thing I need then I will have to install the ipwraw-ng driver to enable Packet Insertion.

But My main problem is that my wireless gets deactivated when I plug in an ethernet cable and I cannot activate it. I suppose this is some kind of software limitation as I have seen other laptops with eth and wlan working at the same time.

---

### Post by five_13 on 2009-05-25
Actually the Managed mode is the default mode running. At least with my card anyway.

And yes, on my laptop, the wireless runs while the ethernet cable is also plugged in.
Try bringing the wireless up again after plugging the ethernet cable in:

```
sudo ifup wlan0
```

---

### Post by kevdog on 2009-05-25
iwconfig is part of the wireless tools package and really gives no indication of the capabilities of the underlying hardware.  Just an FYI

---

### Post by SilverGold on 2009-05-25
Tried that. The output was:

```
silvery-corgan@Silvery-Corgan-Laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

After I plug in my ethernet I cannot use the wireless module any more. Only after I plug it out I can use it.

---

