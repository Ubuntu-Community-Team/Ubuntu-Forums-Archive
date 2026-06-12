---
title: "IBM NetVista 8307-73G Networking problem"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by lagipallero on 2011-07-19
Hi there!
Do you guys have any clue why the wired network does not work on my NetVista? I have tried several different Ethernet cards with no luck. But when i tried my wlan-usb stick there was no problem at all! 

In the network connections menu it says that "Device not managed" or just "Disconnected" 

The MB has a Intel 845G chipset. Does (X)Ubuntu need some drivers for that?

Please help me! 

Ps: I'm running Xubuntu 11.04 with all the updates installed.

---

### Post by jmoorse on 2011-07-19
Check out post 9 here:

[http://ubuntuforums.org/showthread.php?t=1741775](http://ubuntuforums.org/showthread.php?t=1741775)

Let us know if that doesn't help, cheers!

---

### Post by lagipallero on 2011-07-20
Thanks for the tip, but changing the "managed=false" to "true" didn't help. 
When i restarted networking ("init.d/networking restart"), the terminal said that i should change it back to "false" or else the interface could not be started.

I also tried to enter all the dhcp info to the interfaces file but... nothing happened.

---

### Post by jmoorse on 2011-07-20
Drat, I was hoping that would fix it.  Can you post the output of the following please:

```

ifconfig -a
sudo lspci -v | grep -i ether
lsmod

```

Thanks!

---

