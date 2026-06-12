---
title: "TEW-423PI almost working!"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by e*clipse on 2006-06-13
By using the instructions in the ndiswrapper [WIKI]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto"), I iwas able to get my Trendnet TEW-423PI to show up in the "Network settings" window.

At this point, you can only use WEP encryption, so more work is necessary:

I found excellent help in [this]("http://www.ubuntuforums.org/showthread.php?t=179643") thread, which details how to get WPA working.  The instructions are, in a nutshell:

1. install wpa_supplicant
2. install Network-manager-gnome
3. Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5. Reboot
6. Select your network in the NM icon
7. Follow the prompts for password, type, etc.
8. Choose password for keyring (you'll be prompted).
9. Away you go!

1) wpa_supplicant is installed and recognized.
3) I commented out everything but the "lo" entries.  Now the card doesn't show up in the "Network settings" window.
4) I created the wpasupplicant file.

My problem is:  when I tried to install Network-manager-gnome I encountered many dependancy issues.  Files including bind9, dhcdbd, libdbus, libdbus-dlib, libnm-util0 and network-manager were all required, but some conflicted with each other.

Help!

---

### Post by u-blunt-2 on 2007-01-19
are you using i386 or AMD64 ?

---

