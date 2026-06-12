---
title: "Bluetooth has disappeared"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by asharpham on 2010-04-04
I have a Dell Inspiron 6400 Notebook. Even though the bluetooth light is on on the machine itself, the bluetooth icon at the top of the screen has been greyed out. Now, after trying to fix the problem, the icon has disappeared altogether.

Before the icon disappeared, while the icon was greyed out, I was unable to enable it. If I clicked on the greyed-out icon, it told me bluetooth was on but disabled.

Now I need to know how to get the icon back and to enable bluetooth.

Alan

---

### Post by byStanderone on 2010-04-04
...do you still recall what you did to fix your bluetooth problem, and try to retrace it? does the bluetooth remains non-functional after a system reboot?

---

### Post by asharpham on 2010-04-04
The bluetooth has been greyed out for a couple of days. I have no idea how that happened as it was working fine before. However, it could have something to do with running WinXP in virtualbox. It doesn't work there either.

The bluetooth icon disdappeared after I followed a "fix" I found somewhere in Ubuntu forums that first removed bluez and then reinstalled it (both using Terminal). I can't remember the exact procedure but it was as root. Bluez does appear to be installed but made no difference to the operation of bluetooth.

While the bluetooth icon was visible but greyed out in Ubuntu, clicking said that bluetooth was on but disabled. I couldn't work out how to enable it.

System reboot makes no difference.

---

### Post by byStanderone on 2010-04-05
...well perhaps you can check the following files in synaptic manager,
bluetooth related files that are intalled by default in karmic:

bluetooth
libgnome-bluetooth7
gnome-bluetooth
pulseaudio-module-bluetooth
bluez
bluez-cups
libbluetooth3
bluez-gstreamer
bluez-alsa
obex-data-server
totem-plugins

---

### Post by asharpham on 2010-04-05
The following from your list are installed:
libgnome-bluetooth7
pulseaudio-module-bluetooth
bluez
bluez-cups
libbluetooth3
bluez-gstreamer
bluez-alsa
obex-data-server
totem-plugins

Is there anything else I should have?

---

### Post by asharpham on 2010-04-05
Bluetooth is enabled in the WinXP virtualbox. I have no idea how this happened. It still doesn't work in Ubuntu.

---

### Post by byStanderone on 2010-04-05
...is bluetooth listed in karmic synaptic? if so, can't you install it? if it is not listed, you may do an update and see if it becomes listed...or perhaps you can download the package from ubuntu, by doing a package search.

---

### Post by asharpham on 2010-04-07
I'm afraid I succumbed and reinstalled Ubuntu. Not only did I lose Bluetooth but the wifi stopped working also. There seemed no other way to deal with it as I had no connection to my wireless router and nothing worked for getting it running again. Unfortunately I have no idea what happened. The only thing I've learnt is - DON'T TWEAK!

---

### Post by byStanderone on 2010-04-07
...lol, comes the next time around, i believe you will, but have a virgin ubuntu install, just in case. good day.

---

### Post by terrybbarton on 2011-02-11
I am also having the problem that my bluetooth disappeared and I don't even know why. I want to get it working again. I went to the Ubuntu Software Center and installed it "Bluetooth". All of the other above listed components were installed. so now Blutooth is once again found in system>preferences however the icon is not back in the is it called a "tool tray"? When I pair my phone and then choose my computer from my phone's bluetooth menu I get "This device has no supported service" and it used to work before my computer lost it's bluetooth.

Any help is appreciated. I am desperately trying to get away from a proprietary OS developed by a nameless company that treats their legitimate paying customers as though they were their enemys. However I have built up years of expertise so problem solving is so much more difficult for me in Ubuntu as a newbie that doesn't know anything, rather than an OS whose lineage I have used for thousands of hours over decades.

---

