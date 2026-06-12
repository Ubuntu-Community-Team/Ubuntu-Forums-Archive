---
title: "Syanptic WPAsupplicant"
date: 2006-02-26
forum: Networking &amp; Wireless
---

### Post by One Eyed Mack on 2006-02-26
I just installed ubuntu 5.10 on a system that has a Linksys PCI Wifi card.  I was able to install the Linksys driver using ndiswrapper without a problem.  Read the WPA how-to and realized I needed to install wpasupplicant to get WPA support.  Following the howto instructions, I tried to get the package with apt-get but could not find it...  Used the search function in Synaptic... also did not show up in the results.  Finally, I dowloaded the .deb package directly (twice), tried to open it and received a message from the archive manager, "archive type not supported".

Any recommendations on how to resolve my problem would be greatly appreciated.

Thanks,
One Eyed Mack

---

### Post by ape on 2006-02-26
So, to be able to install it through synaptic or apt-get, you need to enable the universe repositories in your /etc/apt/sources.list file.  Once you've done this, run `sudo apt-get update` to refresh the available packages list.  You should now be able to install the wpasupplicant package.

To install a downloaded .deb file, you need to go to a shell and issue the command `sudo dpkg -i <.deb filename>`.

---

