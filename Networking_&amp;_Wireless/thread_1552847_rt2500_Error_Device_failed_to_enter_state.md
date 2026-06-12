---
title: "rt2500 Error Device failed to enter state"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by Handssolow on 2010-08-14
This is just for information for those searching this error message in the system log concerning the rt2500 based pci network card.
I'm making up a desktop PC for my son as his PC's XP mobo failed, so put back into service an rt2500 pci Belkin network card. It worked from a fresh install of Lucid but got this sort error message-

rt2500pci set device state: Error Device failed to enter state 1

solution found here

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6076](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6076)

Quote:
you can prevent this error by doing 'iwconfig wlan0 power off' to disable powersaving

---

### Post by Handssolow on 2010-08-14
It's not quite solved as a reboot turns power management of wlan0 back on.
How do I make power management off permanent so it doesn't come back after a re-boot?

Edit: Details of the problem with the current Lucid kernel and rt2500 chipset based wlan cards are detailed here-

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539794)

I followed Yeti's suggestion to put 'sudo iwconfig wlan0 power off' into /etc/rc.local and this made power off permanent. It's also improved wifi connectivity, I notice I've got a connection immediately after login.

---

### Post by negora on 2010-09-17
I just wanted to thank you that you provided a link with the solution ;) . It worked for me.

---

