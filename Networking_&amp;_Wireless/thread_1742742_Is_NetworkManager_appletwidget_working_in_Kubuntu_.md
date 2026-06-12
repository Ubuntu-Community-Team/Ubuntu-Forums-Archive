---
title: "Is NetworkManager applet/widget working in Kubuntu 11.04?"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by uqbar on 2011-04-29
Until 10.10 the NetworkManager applet/widget has not been able to:
- edit the default "auto eth0" network profile
- create/edit system wide network profiles (wired, wireless, mobile broadband)

The networkmanager itself can do it, of course, since long.
The GNOME/XFCE counterpart also used to work flawlessly since long.

Is there anyone running Kubuntu 11.04 which can provide me with some feedback?
TIA.

---

### Post by uqbar on 2011-05-02
Wooow! There's none using the NetworkManager plasma widget?
This is really incredible, while still possible,

---

### Post by uqbar on 2011-07-12
I checked it by mnyself.
AND IT'S NOT WORKING PROPERLY!
You cannot create/delete/edit any system wide network connection.
And, as mentioned earlier, the GNOME counterpart can.
This is a real shame for KDE devs!

---

### Post by linuksamiko on 2011-07-12
Do you might refer to this?

[Bug747081]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/747081")

I have more or less the same problems. After boot there is no network on my system. I have do disable and enable the network through the widget in order to get started.

---

### Post by lores on 2011-10-12
I'm still experiencing the same problem as the OP. Kubuntu 11.04 installed from Ubuntu with kde-full; fully up-to-date.

---

### Post by lweldon on 2011-10-15
new to ubuntu. I want to use a static IP but the only way I can  find after changing /etc/network/interfaces is sudo ifup eth0
while this does work I need access to the machine from remote and so need the interface up on reboot.

Is this nightmare a part of the kubuntu experience?

Thanks

---

### Post by lores on 2011-10-16
this issue is fixed in kubuntu 11.10
@lweldon: you can always have a command executed as root at boot by inserting it into /etc/rc.local

---

### Post by StiltonSandwich on 2011-11-27
This seems like a good thread to add my recent experience to.

I just upgraded from 10.10 to 11.10, and I had a problem where plasma-widget-networkmanagement did not know there were any network interfaces to use. I run a 64-bit system.

NetworkManager itself was aware of the interfaces and could use them. I was able to connect it successfully by using another client (nm-applet). The problem was clearly contained within the plasma widget.

I solved my problem by removing the existing plasma-widget-networkmanager package and then replacing it with the one from the 12.04 (Precise) repository, by downloading and installing the relevant .deb file from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . After a reboot, this seemed to fix things. Thankfully there were no dependency problems with this approach.

---

