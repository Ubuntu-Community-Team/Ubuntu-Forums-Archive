---
title: "no nm-applet, couldn't initialize the D-Bus manager, iwlist scan detects networks"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by czege on 2010-11-14
Hi,

I'm running Ubuntu 10.04 server 64bit. I'm trying to get my ASUS PCE-N13 wireless PCI card working for searching and connecting to wireless networks.

But I have no networks applet appearing in the panel.

system->preferences->sessions has the Network Manager enabled

The Notification Area is added to the panel.

system->preferences-Network Connections-->Wireless[tab] shows a pink box, with no available connections.

```
nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2086): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```iwlist scan detects neighborhood networks when scanning wlan0

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

``````
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Wireless network interface added manually
auto wlan0
iface wlan0 inet dhcp

```What am I missing?

Thanks,

Paul

---

### Post by czege on 2010-11-14
More dorking around on my part. If I do a sudo /etc/init.d/dbus restart the nm-applet will actually appear in the panel with a red exclamation point, and a single greyed out menu option of "NetworkManager is not running".

If I then do sudo NetworkManager I'll get greyed out menu options from the nm-applet for my wired network and wireless network saying "device not managed".

Thanks,

Paul

---

### Post by bitscarre on 2010-11-14
Alt + F2 and type nm-applet

I had a somewhat similar problem to yours, and by starting the applet using that launcher, it always did it for me.

---

### Post by czege on 2010-11-15
> **bitscarre said:**
> Alt + F2 and type nm-applet

I had a somewhat similar problem to yours, and by starting the applet using that launcher, it always did it for me.

Thanks man. But yeah, I get nothing appearing in the panel from that. When I run nm-applet from terminal it gives the "nm-applet is already running....Couldn't initialize the D-Bus manager" output. So the nm-applet is actually already running.

Paul

---

### Post by bitscarre on 2010-11-15
What if you do in a terminal:

```
sudo killall nm-applet
sudo /etc/init.d/networking restart
```and then restart nm-applet with the Alt+F2 menu?

I am no expert, just trying to give you some idea of things you could try.
                                                                  :guitar:

---

### Post by dineshs on 2010-11-15
From my experience if /etc/network/interfaces contains anything other than 
[COLOR="Blue"]auto lo
iface lo inet loopback
[/COLOR]your Network manager icon will disappear (Ref FAQ No d [here]("https://help.ubuntu.com/community/NetworkManager0.7")
So edit /etc/network/interfaces so that it contains only those 2 lines .
Restart your PC.
Once the icon is back,configure your connections(wired,wireless DSL....)using NM (right click the icon then edit connections)

---

### Post by othermale on 2010-11-15
I have had virtually the same symptoms which I think were caused by two separate issues: the icon no longer part of the notification area and some network service or other not starting correctly.
  Doing _all_ the following steps solved it for me:
   
   
    1. in /etc/NetworkManager/nm-system-settings.conf
  changed "managed=false" to "managed=true"
   
  2. restart
   
  3. re-add the notification applet. 
  ie right click panel->add to panel->notification area
  at this point nm-applet appeared gray with a red exclamation point
(interestingly, I also needed to add the indicator applet as well.)

   
  4. click on the nm-applet and connect to any wifi network; whatever caused the red exclam point did not interfere with this.


I won't remotely pretend to understand why this solves anything but it did for me and perhaps it will be of use to the knowledgeable.

   
  [FONT=&quot]
[/FONT]

---

### Post by czege on 2010-11-16
> **dineshs said:**
> From my experience if /etc/network/interfaces contains anything other than 
[COLOR=Blue]auto lo
iface lo inet loopback
[/COLOR]your Network manager icon will disappear (Ref FAQ No d [here]("https://help.ubuntu.com/community/NetworkManager0.7")
So edit /etc/network/interfaces so that it contains only those 2 lines .
Restart your PC.
Once the icon is back,configure your connections(wired,wireless DSL....)using NM (right click the icon then edit connections)

Thank you. That worked for me.

Paul

---

### Post by czege on 2010-11-16
> **othermale said:**
> I have had virtually the same symptoms which I think were caused by two separate issues: the icon no longer part of the notification area and some network service or other not starting correctly.
  Doing _all_ the following steps solved it for me:
   
   
    1. in /etc/NetworkManager/nm-system-settings.conf
  changed "managed=false" to "managed=true"
   
  2. restart
   
  3. re-add the notification applet. 
  ie right click panel->add to panel->notification area
  at this point nm-applet appeared gray with a red exclamation point
(interestingly, I also needed to add the indicator applet as well.)

   
  4. click on the nm-applet and connect to any wifi network; whatever caused the red exclam point did not interfere with this.


I won't remotely pretend to understand why this solves anything but it did for me and perhaps it will be of use to the knowledgeable.


Thanks. dineshs' solution worked for me. But maybe this helps someone else.

Paul

---

### Post by stunder on 2010-12-17
> **othermale said:**
> I have had virtually the same symptoms which I think were caused by two separate issues: the icon no longer part of the notification area and some network service or other not starting correctly.
  Doing _all_ the following steps solved it for me:
   
   
    1. in /etc/NetworkManager/nm-system-settings.conf
  changed "managed=false" to "managed=true"
   
  2. restart
   
  3. re-add the notification applet. 
  ie right click panel->add to panel->notification area
  at this point nm-applet appeared gray with a red exclamation point
(interestingly, I also needed to add the indicator applet as well.)

   
  4. click on the nm-applet and connect to any wifi network; whatever caused the red exclam point did not interfere with this.


I won't remotely pretend to understand why this solves anything but it did for me and perhaps it will be of use to the knowledgeable.

   
  [FONT=&quot]
[/FONT]

This and a the removal of the extra lines in my /etc/network/interfaces file cleared up my issue... Thanks guys

---

### Post by JC Cheloven on 2011-01-13
> **dineshs said:**
> From my experience if /etc/network/interfaces contains anything other than 
[COLOR="Blue"]auto lo
iface lo inet loopback
[/COLOR]your Network manager icon will disappear (Ref FAQ No d [here]("https://help.ubuntu.com/community/NetworkManager0.7")
So edit /etc/network/interfaces so that it contains only those 2 lines .
Restart your PC.
Once the icon is back,configure your connections(wired,wireless DSL....)using NM (right click the icon then edit connections)
That did it for me in Lucid 32 bit. Thanks!

---

### Post by anibalismo on 2012-08-06
> **dineshs said:**
>  ... if /etc/network/interfaces contains anything other than 
[COLOR=Blue]auto lo
iface lo inet loopback
[/COLOR]your Network manager icon will disappear (Ref FAQ No d [here]("https://help.ubuntu.com/community/NetworkManager0.7")
So edit /etc/network/interfaces so that it contains only those 2 lines .
Restart your PC.
...


THANKS! work for me too :guitar:

---

### Post by wildmanne39 on 2012-08-06
Old thread closed.

---

