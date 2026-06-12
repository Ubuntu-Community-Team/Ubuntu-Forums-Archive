---
title: "RTL8187SE Not Working"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by Lowenstein on 2010-08-07
Hi
I'm running Ubuntu 10.4 on a Toshiba L500-00U Laptop, with a Realtek RTL8187SE wireless network card.
The hotkey to turn on the wireless card doesn't work, when I click on the networking icon on the top panel of my screen the Wireless Networks section is grayed out. The only proprietary driver 'Hardware Drivers' could find was a driver for my integrated graphics chip. NDISwrapper didn't help. I don't have a windows partition from which to turn on the wireless card.

Ideas?

---

### Post by varunendra on 2010-08-11
3 days may be too late for a response, but if you are still looking for a fix, you may try these-

[LIST=1]
[*]Make sure the wifi is switched on physically & in the BIOS.
[*]If above is already ok, try a previous version of ubuntu (not a good suggestion, but may solve your current problem without creating a new one).
[/LIST]
For an older version, you may try [Karmik]("http://releases.ubuntu.com/9.10/") (9.10) or [Jaunty]("http://releases.ubuntu.com/jaunty/") (9.04).

A quick search suggests that the new kernel in Lucid has some problems with realtek wifi cards:
[http://ubuntuforums.org/shoiwthread.php?p=9253780](http://ubuntuforums.org/shoiwthread.php?p=9253780)
[http://ubuntuforums.org/showthread.php?p=9136000](http://ubuntuforums.org/showthread.php?p=9136000)


You may also try [Slax Live CD]("http://www.slax.org/get_slax.php") to see if wifi works in it (may not connect to secured network, but I've found [Slax]("http://www.slax.org/") so far so good at detecting & handling network devices including wifi adapters).

---

### Post by hermit on 2010-08-30
I also use the Realtek RTL8187. I have a Dell Latitude 810 and am on Ubuntu 10.4. The card was automatically detected *if* the wireless networking switch was turned on. This is totally different from Windoze where the wireless networking switch is for bluetooth and the internal wireless networking card but is not necessary for the Realtek RTL8187 as it is a USB2 hookup. My laptop has a hotkey to turn on the wireless and it works the same under Ubuntu as it does with windoze.

---

### Post by hermit on 2010-08-30
Wireless networking can be tricky if the source is very far away. I live about a mile from the source of my signal and, even though this card is a killer, the connection can be flaky.

If anyone knows how to change the settings for this Realtek RTL8187 card so that it receives and sends at its maximum capacity, I would love to hear about it.

---

