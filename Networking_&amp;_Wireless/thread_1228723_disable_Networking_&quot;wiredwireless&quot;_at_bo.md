---
title: "disable Networking &quot;wired/wireless&quot; at boot"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by walterav on 2009-08-01
I want ubuntu to be connectionless, maybe even not turning on the network hardware at/after boot! I just want to be able to enable manually after booting in the OS when needed, but by default it has to be disabled, at all time!

Network manager let me enable or disable networking, but it can still work from within the terminal, and after a reboot it is still turned on if I forgot to disable it.

So is there some low level init or something else to make sure no network hardware is initialized?

---

### Post by Brandon Williams on 2009-08-02
You can configure that network interfaces in /etc/network/interfaces and start/stop them using ifup and ifdown. First, completely disable network-manager. Then, add the necessary configuration information to /etc/network/interfaces, for example:
```
iface eth0 inet dhcp
iface wlan0 inet dhcp
    wireless-essid   mynetwork
    wireless-mode    managed
```
You'll have to install the wireless-tools package for the wireless part to work. Also, make sure that there is no 'auto eth0' or 'auto wlan0' line in the file, to prevent the interface from coming up automatically at boot.

With this config method, run 'sudo ifup eth0' on the command line to start eth0, and 'sudo ifdown eth0' to stop eth0.

---

### Post by walterav on 2009-08-13
Hi,

How do I disable the network manager "applet"? 
When disabling it under Startup applications, just seems to leave two services with ps -e. Although the icon is gone.

I also would like to know howto enable it again to quickly setup a wifi connection.

I just want to be sure it is all turned off after a fresh boot...
I know I can enable / disable connections with ifup/down when configured in /etc/network/interfaces, but the system is running on a usb-stick so every new/different computer I boot from, has a new network connection interface number eth5/wlan4 etc.

So I rather be able to just enable network manager applet after every reboot...

---

### Post by Fatman_UK on 2009-08-13
How about removing the networking hardware from the system completely? Ubuntu can't control it if it's not present.

If you can't physically remove the networking hardware, can you disable it in your system's BIOS?

When you've removed or disabled the networking hardware, you can introduce a USB network card. You enable the networking by plugging in the card.

Be careful though to choose a network card which is known to work with Linux. The kernel is picky about USB devices. I have a few which still don't work months after I bought them.

---

### Post by walterav on 2009-08-17
> **Fatman_UK said:**
> How about removing the networking hardware from the system completely? Ubuntu can't control it if it's not present.

If you can't physically remove the networking hardware, can you disable it in your system's BIOS?

When you've removed or disabled the networking hardware, you can introduce a USB network card. You enable the networking by plugging in the card.

Be careful though to choose a network card which is known to work with Linux. The kernel is picky about USB devices. I have a few which still don't work months after I bought them.

Thanks for the workaround, but it is not an option...

I think it must be possible all by software! I thought backtrack by default also has his networking hardware disabled...

---

