---
title: "Intel PRO/Wireless 2200BG not always recognized"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by ZioAlfredo on 2011-03-16
Hi everybody,

first of all I'll tell you what kind of machine and O.S. I have:

- Laptop Acer TravelMate 292LCi
- Intel Centrino Pentium M 1.5GHz
- Intel 855PM chipset
- Intel PRO/Wireless 2200BG (802.11 b/g WLAN)

- Ubuntu 9.04 (Jaunty Jackalope)
- Kernel 2.6.28-19-generic

```
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
        Subsystem: Intel Corporation Device 2701
        Flags: bus master, medium devsel, latency 128, IRQ 10
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ipw2200
        Kernel modules: ipw2200
```

At this time, it's working perfectly and I'm connected to the internet with Wi-Fi.



Anyway, I have a very strange problem with my Wi-Fi card: Ubuntu can't recognize it if I shut down the laptop, unplug the AC cable, connect it back and turn the notebook on... But Windows XP can re-activate the Wi-Fi card after such a sequence!

Therefore, in such situation, I have to boot Windows XP first, in order to reactivate the Wi-Fi card, and then, I can reboot the laptop and choose Ubuntu that, this time, will recognize the Wi-Fi card.

What can I do to have Ubuntu recognizing the Wi-Fi card even if the AC cable is unplugged and then plugged back?

Thank you very much,

Alfredo.

---

### Post by Rubi1200 on 2011-03-16
Hi and welcome to the forums :-)

Have you considered upgrading your Ubuntu installation?

9.04 has already reached EOL (End of Life) and is no longer supported with updates.

---

### Post by ZioAlfredo on 2011-03-16
Thanks.
Do you think that upgrading my Ubuntu will solve my problem?

---

### Post by Rubi1200 on 2011-03-16
I cannot say with certainty, and I never used 9.04.

However, I have exactly the same wireless card and it has worked flawlessly on all versions since 9.10.

---

### Post by flash63 on 2011-03-16
Hello,
> - Laptop Acer TravelMate 292LCi
in this case you must install Acer-Hotkeys. Maybe the module **acer_wmi** works too.

Check it:
```
lsmod
```

[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)
> 9.04 has already reached EOL (End of Life) and is no longer supported with updates.
Jep.
> Do you think that upgrading my Ubuntu will solve my problem?
No, not automatically.

---

### Post by ZioAlfredo on 2011-03-16
Hey! It works with the Acer-Hotkeys!!!

The only thing is that I have to execute the following commands at startup:

```
sudo modprobe acerhk force_series=290 usedritek=1 verbose=1 
sudo echo 1 > /proc/driver/acerhk/wirelessled
```

How can I make it automatic at startup?

Thank you so much!

---

### Post by ZioAlfredo on 2011-03-16
Thank you so much flash63, I've solved my problem!
I've appended the two commands in /etc/init.d/rc.local and now they are executed automatically at startup.
Thanks!

Problem SOLVED!!!!!!!

---

### Post by flash63 on 2011-03-16
> How can I make it automatic at startup?
Create the Configfile
```
echo 'options acerhk force_series=290 usedritek=1 verbose=1' | sudo tee /etc/modprobe.d/acerhk.conf
```
Edit **/etc/rc.local** ...
```
echo 1 > /proc/driver/acerhk/wirelessled
exit0
```
and **/etc/modules** as root an add an entry for the module
```

...
acerhk
```

Ups, to late.

---

