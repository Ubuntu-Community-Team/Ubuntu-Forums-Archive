---
title: "packages have been unpacked but not yet configured"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by addictive on 2013-05-20
Hi all - I am stuck with this weired issue. I am running Ubuntu 12.04

Sudo dpkg --audit 

Output is 

> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 network-manager-dbg:i386 network management framework (debugging symbols)
 network-manager:i386 network management framework (daemon and userspace tools)
 network-manager-gnome:i386 network management framework (GNOME frontend)

Not sure what to do.

I have also tried apt-get -f install

Output is 

> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 network-manager-dbg:i386 network management framework (debugging symbols)
 network-manager:i386 network management framework (daemon and userspace tools)
 network-manager-gnome:i386 network management framework (GNOME frontend)


Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... failed.
The following packages have unmet dependencies:
 gnome-bluetooth : Breaks: network-manager-gnome:i386 (< 0.9.0-3) but 0.8-0ubuntu3.1 is installed
 libnm-gtk-common : Breaks: network-manager-gnome:i386 (< 0.9.1.90-0ubuntu2) but 0.8-0ubuntu3.1 is installed
 libnm-gtk0 : Recommends: network-manager (>= 0.9.4) but it is not installed
              Breaks: network-manager-gnome:i386 (< 0.9.1.90-0ubuntu2) but 0.8-0ubuntu3.1 is installed
 network-manager:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
                        Depends: libdbus-1-3:i386 (>= 1.0.2) but it is not installed
                        Depends: libdbus-glib-1-2:i386 (>= 0.88) but it is not installed
                        Depends: libglib2.0-0:i386 (>= 2.31.8) but it is not installed
                        Depends: libgudev-1.0-0:i386 (>= 147) but it is not installed
                        Depends: libnl-3-200:i386 (>= 3.2.3) but it is not installed
                        Depends: libnl-genl-3-200:i386 (>= 3.2.3) but it is not installed
                        Depends: libnl-route-3-200:i386 but it is not installed
                        Depends: libnm-glib4:i386 (>= 0.9.4.0~git201203162258.69247a0) but it is not installed
                        Depends: libnm-util2:i386 (>= 0.9.3.995+git201203081848.bba834f) but it is not installed
                        Depends: libpolkit-gobject-1-0:i386 (>= 0.99) but it is not installed
                        Depends: wpasupplicant:i386 (>= 0.7.3-1) but it is not installed
                        Depends: isc-dhcp-client:i386 (>= 4.1.1-P1-4) but it is not installed
                        Depends: dnsmasq-base:i386 but it is not installed
                        Depends: iputils-arping:i386 but it is not installed
                        Recommends: network-manager-pptp:i386 but it is not installed
                        Recommends: ppp:i386 (>= 2.4.5) but it is not installed
                        Recommends: iptables:i386 but it is not installed
                        Recommends: modemmanager:i386 but it is not installed
                        Breaks: network-manager-gnome:i386 (< 0.8.99) but 0.8-0ubuntu3.1 is installed
 network-manager-gnome:i386 : Depends: libatk1.0-0:i386 (>= 1.29.3) but it is not installed
                              Depends: libc6:i386 (>= 2.4) but it is not installed
                              Depends: libcairo2:i386 (>= 1.2.4) but it is not installed
                              Depends: libdbus-1-3:i386 (>= 1.0.2) but it is not installed
                              Depends: libdbus-glib-1-2:i386 (>= 0.78) but it is not installed
                              Depends: libfontconfig1:i386 (>= 2.8.0) but it is not installed
                              Depends: libfreetype6:i386 (>= 2.2.1) but it is not installed
                              Depends: libgconf2-4:i386 (>= 2.27.0) but it is not installed
                              Depends: libglade2-0:i386 (>= 1:2.6.1) but it is not installed
                              Depends: libglib2.0-0:i386 (>= 2.18.0) but it is not installed
                              Depends: libgnome-bluetooth7:i386 (>= 2.27.8) but it is not installable
                              Depends: libgnome-keyring0:i386 (>= 2.20.3) but it is not installed
                              Depends: libgtk2.0-0:i386 (>= 2.16.0) but it is not installed
                              Depends: libnm-glib2:i386 (>= 0.8~rc2~git.20091229t135236.302e62d) but it is not installable
                              Depends: libnm-util1:i386 (>= 0.8~a~git.20090930t162132.866d48b) but it is not installable
                              Depends: libnotify1:i386 (>= 0.4.5) but it is not installable
                              Depends: libnotify1-gtk2.10:i386 but it is not installable
                              Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not installed
                              Depends: libxml2:i386 (>= 2.6.27) but it is not installed
                              Depends: zlib1g:i386 (>= 1:1.1.4) but it is not installed
                              Depends: gksu:i386 but it is not installed
                              Depends: mobile-broadband-provider-info:i386 (>= 20090622) but it is not installable
                              Recommends: notification-daemon:i386




Any help will be much appreciated

---

