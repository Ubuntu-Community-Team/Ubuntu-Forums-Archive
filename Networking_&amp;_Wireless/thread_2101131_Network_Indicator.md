---
title: "Network Indicator"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by bman on 2013-01-03
I want to get rid of the indicator for the network information.

I am on Ubuntu 12.04.

I found this command

```
sudo apt-get remove network-manager-gnome
```

Found this information,

Networking: Provided by package network-manager-gnome. DO NOT remove unless you have a desktop with one wired ethernet connection and do not use VPNs.

Which is true, I only have one wired connection. Though if I do this, am I still able to go into System Settings and get to the Network options?

---

### Post by efflandt on 2013-01-03
If you remove Network Manager you will not have anything in any menus to configure networking. You would need to manually configure /etc/network/interfaces.  See **man interfaces**.

---

### Post by bman on 2013-01-03
So there is no way to get rid of that indicator without causing other problems?

---

### Post by steeldriver on 2013-01-03
well you can kill the nm-applet process

```
$ pkill -u $USER nm-applet
```I don't actually know how to prevent it from starting... there must be a way...

EDIT: no idea why you'd want to though - don't fall into the trap of thinking it prevents the user from accessing the underlying network-manager service (the same functionality is available via nm-tool / nmcli or via dbus)

---

### Post by steeldriver on 2013-01-04
so fwiw the answer (for Unity) seems to be to edit the autostart file and add Unity to the list of desktops that the applet is NotShownIn:

[FONT=Courier New]/etc/xdg/autostart/nm-applet.desktop[/FONT] :
```
[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;[COLOR=Red]**Unity;**[/COLOR]
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet
```

---

### Post by bman on 2013-01-04
Thanks man, will give that a try.

Which I just realised I don't know how to do..

---

### Post by steeldriver on 2013-01-04
You would need to open the file in a text editor with root permission

```
sudo nano /etc/xdg/autostart/nm-applet.desktop
```or

```
gksudo gedit /etc/xdg/autostart/nm-applet.desktop
```and edit as indicated or just a one-shot with 'sed'

```
sudo sed -i 's/NotShowIn.*$/&Unity;/' /etc/xdg/autostart/nm-applet.desktop
```Would it be impolite to ask why you want to do this? As noted above, disabling / removing the applet doesn't do anything to secure the connection

---

### Post by bman on 2013-01-04
I don't use it, it gives me no benefit of being on that bar. I like cleaning things up, getting rid of things not needed.

If I need to change something, which I don't, I can go into the settings.

---

### Post by bman on 2013-01-04
And also, thanks, that worked like a charm!

---

### Post by steeldriver on 2013-01-04
Glad to help - tbh I had to do some searching to find that, it bugged me that there wasn't an 'obvious' answer

Also afaik that will disable it for **all** users - if that's not what you want, there *may* be a per-user equivalent - maybe somewhere in ~/.config ?



EDIT: for **per-user** disable:

0. revert any changes you made in /etc/xdg/autostart/nm-applet.desktop

1. create a ~/.config/autostart directory if it does not already exist

```
 [ -d ~/.config/autostart ] || mkdir -pv ~/.config/autostart
```2. copy the /etc/xdg version with the appropriate modification

```
sed 's/NotShowIn.*$/&Unity;/' /etc/xdg/autostart/nm-applet.desktop > ~/.config/autostart/nm-applet.desktop
```3. log out and back in

Tested on my 12.04 laptop.

---

