---
title: "pidgin and Bonjour on jaunty doesnt sees peers"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by nivw on 2009-12-12
Hi,
I am using jaunty and pidgin 1:2.5.5-1ubuntu8.4. I added a bonjour account , but can't see the other pcs in my lan.
When I run avahi zeconf browser I do see a new entry added to the list: iChat Presence along with the user name and the hostname.
I got two other computers running pidgin in my lan, one runs gentoo and pidgin 2.6.3 and the other runs maemo. In the gentoo machine I can see the maemo pidgin client via bonjour, and also the ubuntu client, but when I send messages, I dont get them in ubuntu. same for the maemo computer.
when I quit pidgin and load kopete and use bonjour I see the same problem, as other clients see the ubuntu, but it can't see them. when I send a msg to kopete , it crashes.
How to solve this?
Niv

---

### Post by nivw on 2009-12-13
I tried to update pidgin using the pdgin ppa, so I now have 2.6.3 and still get the same issue.
maybe its avahi?
> $ dpkg -l |grep avahi
ii  avahi-autoipd                              0.6.23-4ubuntu4                                      Avahi IPv4LL network address configuration d
ii  avahi-daemon                               0.6.23-4ubuntu4                                      Avahi mDNS/DNS-SD daemon
ii  avahi-discover                             0.6.23-4ubuntu4                                      Service discover user interface for avahi
ii  avahi-dnsconfd                             0.6.23-4ubuntu4                                      Avahi DNS configuration tool
ii  avahi-utils                                0.6.23-4ubuntu4                                      Avahi browsing, publishing and discovery uti
ii  libavahi-client3                           0.6.23-4ubuntu4                                      Avahi client library
ii  libavahi-common-data                       0.6.23-4ubuntu4                                      Avahi common data files
ii  libavahi-common3                           0.6.23-4ubuntu4                                      Avahi common library
ii  libavahi-compat-libdnssd1                  0.6.23-4ubuntu4                                      Avahi Apple Bonjour compatibility library
ii  libavahi-core5                             0.6.23-4ubuntu4                                      Avahi's embeddable mDNS/DNS-SD library
ii  libavahi-glib1                             0.6.23-4ubuntu4                                      Avahi glib integration library
ii  libavahi-gobject0                          0.6.23-4ubuntu4                                      Avahi GObject library
ii  libavahi-qt3-1                             0.6.23-4ubuntu4                                      Avahi Qt 3 integration library
ii  libavahi-ui0                               0.6.23-4ubuntu4                                      Avahi GTK+ User interface library
ii  libavahi1.0-cil                            0.6.19-3ubuntu1                                      CLI bindings for Avahi
ii  python-avahi                               0.6.23-4ubuntu4                                      Python utility package for Avahi


---

