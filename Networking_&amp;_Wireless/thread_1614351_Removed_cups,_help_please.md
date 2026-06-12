---
title: "Removed cups, help please"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by b49P23TIvg on 2010-11-05
Summary:
 - ubuntu 10.04 I removed cups.
 - Struggled successfully to restore network.
 - Upgraded to ubuntu 10.10 hoping for repair.
 * Can no longer connect to network.  Help please!
 
(all commands as root)
In gnome ubuntu 10.04:  I don't have a printer.  I aggressively removed cups with a package manager, and then discovered my OS was reduced to PDP-7 1972 era unix.  (A good system---but....)
Using terrific instructions [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html) I recovered my wireless network.
I next installed firefox (apparently I AGGRESSIVELY removed cups)
$ sudo apt-get install firefox
and then was able to
$ DISPLAY=:0.0 xinit $( which firefox )
Thereby discovering that I could run a program in X.  Otherwise installing firefox is irrelevant.
I upgraded to ubuntu 10.10 hoping to recover the system functionality.
Can no longer connect to network.  Please help.
 
Tried  sudo /etc/init.d/networking restart
Also toggling thinkpad's wireless on/off button.
 
$ iwlist wlan0 scan  # does find the local networks
 
 
dhclient -r wlan0    says the network is unreachable.
$ sudo dhclient wlan0
...
No DHCPOFFERES received.
No working leases in persistent database - sleeping
 
Thank you,
Dave

---

### Post by b49P23TIvg on 2010-11-05
I'm giving up.  Maybe changing my hosts file would repair my computer's internet connection but I've swapped between my ubuntu 9 live CD and tests enough times.  I also tried  apt-get install ubuntu-desktop | gawk 'clever program' > windows_ftp.input
transfered the files via usb memory stick, and  dpkg -i *.deb  interspersed with mount and umount.   This had an effect, but insufficient.  If there's a staging area for aptitude I didn't find it.  I'll now try to make a 10.10 live cd hope that   
wodim dev=/dev/cdrw -v -data cd_image.iso
works, otherwise I'll have to upgrade back from version 9.
And first to preserve data elsewhere with
tar cf - /usr/local   /home | gzip -c | split --size=1GB
 
 
Lesson?
The package manager checkboxes showed some as installed, some as both installed and important.  The cups "important" boxes must have included every program that can print.  All the programs with file->print option were removed.

---

