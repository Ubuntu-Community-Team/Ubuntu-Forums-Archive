---
title: "nm-applet missing while booting"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Kanna2412 on 2010-10-04
Hello guys,

I removed Network Management applet from top panel. I tried nm-applet command. It worked. The icon is missing each time I start my Ubuntu 10.04.

Please help me solve this problem. I need the nm-applet automatically added to the panel each time I start my computer.


Kanna

---

### Post by dineshs on 2010-10-05
1)system-preferences-startup applications
tick network manager
2)Right click on the top panel-click add to panel-select notification area -click add

---

### Post by Kanna2412 on 2010-10-10
Thank you for your prompt reply Dinesh.
 
I did the above but it didn't work. I added Network Area to top panel. It looks like 3 small horizonal lines. Nothing happens when I click on it.
 
Is there any command to fix this? This is very important to me. Please.........

---

### Post by dineshs on 2010-10-10
please post the outputs of the following terminal commands(applications-accessories-terminal)
```
gksudo gedit /etc/network/interfaces
```
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
```
note:try making```
managed=true
```in */etc/NetworkManager/nm-system-settings.conf* You may have to restart

---

### Post by Kanna2412 on 2010-10-11
I opened the file and changed the false to true. Now it reads:

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
**# /etc/default/NetworkManager**
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:27:0e:0b:89:86,

[ifupdown]
managed=true

I went to check **NetworkManager** file in /etc/default. But there is no file named NetworkManager. Is that the problem?

Please help.........

---

### Post by dineshs on 2010-10-11
Did you get your icon back after restarting ?
Did you edit /etc/network/interfaces?
What exactly is your problem after doing the above steps?

---

### Post by rla on 2010-11-23
The same issues just started on my Maverick (64bit) box. On Boot there is no network icon in the notification area, but there is an actual network connection. When I "Alt-F2" and run "nm-applet --sm-disable", The icon appears and I can change network settings,etc. If I run from terminal then terminal must remain open for the icon to remain. This started happening after I got a new monitor and changed video resolutions...strange.

Is there a way to force start this applet on boot or something?

---

### Post by ElVirolo on 2010-11-28
Hi, I had exactly the same problem and I solved it by choosing "Gnome" instead of "Gnome-failsafe" in GDM. I have no idea why it was set like that.

Hope it'll help you out.

---

### Post by xscd on 2011-01-24
Thank you very much, Dineshs. Your tips about editing the two configuration files as root (using sudo) worked perfectly for this particular problem (nm-applet disappearing from top panel) on my machine. In my case, the wlan0 device was missing from /etc/network/interfaces (I added wlan0 to the "auto lo" line, so that it said "auto lo wlan0" and then added a line below that: "iface wlan0 inet dhcp" (without the double quotes), and in /etc/NetworkManager/nm-system-settings.conf, I changed "managed=false" to "manage=true" (without the double quotes), and now the nm-applet appears in the panel and the wireless interfaces are searched for automatically at Gnome login.

Thank you for sharing your time and expertise! :)

---

### Post by drwatson_droid on 2011-08-05
> **xscd said:**
> Thank you very much, Dineshs. Your tips about editing the two configuration files as root (using sudo) worked perfectly for this particular problem (nm-applet disappearing from top panel) on my machine. In my case, the wlan0 device was missing from /etc/network/interfaces (I added wlan0 to the "auto lo" line, so that it said "auto lo wlan0" and then added a line below that: "iface wlan0 inet dhcp" (without the double quotes), and in /etc/NetworkManager/nm-system-settings.conf, I changed "managed=false" to "manage=true" (without the double quotes), and now the nm-applet appears in the panel and the wireless interfaces are searched for automatically at Gnome login.

Thank you for sharing your time and expertise! :)

thanks **changing "managed=false" to "manage=true" worked for me**

---

