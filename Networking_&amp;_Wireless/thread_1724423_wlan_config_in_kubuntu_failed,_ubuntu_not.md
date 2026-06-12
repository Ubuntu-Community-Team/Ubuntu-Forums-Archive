---
title: "wlan config in kubuntu failed, ubuntu not"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by linuxone on 2011-04-08
hi,

I got a new Notebook

   Asus U36J

having an :

   Atheros AR9285 Wlan

I prefer Kubuntu, so I installed Kubuntu 10.10 amd64 on a second partition. Installation was no problem, but network configuration.

Using Network-Manager-KDE I was unable to configure wlan. No wlan, no choice.

Because I had the same problem some time ago on my Asus Eee Netbook, I connected a wired cable nearby my router and installed Ubuntu-Desktop.

Surprisingly Wlan could be successfully configured and activated after booting GNOME Desktop within a minute. Real simple, easy, no problem.

Switching back to KDE again no wlan. No choice.

I need to configure it manually by creating correct /etc/network/interfaces and wpa_suppliant.conf files. (with the old experiences from my Eeee Netbook no big problem)

Now, with the manually created config files, also KDE does use wlan successfully!

I really don't understand this problem. What is the difference between Network-Manager-KDE and -GNOME? Why does it fail in KDE but does work in GNOME?

And this is an old problem, I had the exact same situation about two years ago when installing the netbook.

Thomas

---

### Post by SeijiSensei on 2011-04-08
> **linuxone said:**
> Using Network-Manager-KDE I was unable to configure wlan. No wlan, no choice.

Network-Manager-KDE is not the standard network manager in recent versions; [plasma-widget-networkmanagement]("http://packages.ubuntu.com/maverick/plasma-widget-networkmanagement") is.

Go to System Settings > Network Settings and try configuring things there.  You may need to install the corresponding plasma-widget in the system tray.  Right-click the tray and select Panel Options > Add Widgets; pick the widget with the big N.

I'd run "sudo apt-get purge network-manager-kde" before going any further, or you might end up with conflicts.

---

### Post by linuxone on 2011-04-10
Hi,

thanks for your answer.

> **SeijiSensei said:**
> Network-Manager-KDE is not the standard network manager in recent versions; [plasma-widget-networkmanagement]("http://packages.ubuntu.com/maverick/plasma-widget-networkmanagement") is.

I used the config tool which was available after a standard installation from a DVD. Sorry for the wrong file name - it look to me as the old Network Manager.

Just checked it, network-manager-kde is not installed but the mentioned widget. And I used this "N" widget to configure wlan.

Again, using this widget I am still unable to get wlan running. All settings were correct - I got it running manually and from within Ubuntu/GNOME and on several other devices in my home network.

The KDE widget does show the result from a network scan, including my wlan network with the right MAC address. But I cannot connect to it.

Thomas

---

