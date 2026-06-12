---
title: "Wireless Network Management Software"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by azuro on 2006-01-16
I use my laptop at school and home.  Both my home and school had wireless and both uses DHCP.  I want the computer to automatically connect to my home wireless while I'm at home and connect to my school's wireless while I'm at school.  Now, everytime I booted up Ubuntu at school, i have to go to Network monitor and change the wireless settings and change it back when i got home.  Are there any tools that can automatically connect my computer to the wireless network?  I'm using Dell 600m and Intel Wireless Pro 2200.  Thanks.

---

### Post by prizrak on 2006-01-16
There are a few things you can try (neither worked for me, but they seem to work for others)
Wifi-radar (I believe it's in the repos)
OR 
GTK Wi-Fi the link to the DL is here as well as some info on the program [http://ubuntuforums.org/showthread.php?t=34645](http://ubuntuforums.org/showthread.php?t=34645)

---

### Post by toorima on 2006-01-16
apt-get install network-manager is another option that I use

---

### Post by lilolpete on 2006-01-16
Sorry for being a noob, but this is how I went about installing the .deb package.

In Terminal:
sudo dpkg -1 gtkwifi-1.09.deb

I think it installs it... but I'm not sure where it installed to lol. Could someone pretty please walk to me through installation of this and where to find it? haha I can't seem to get this installl thing down... maybe its because I can't get an internet connection off of my Microsoft MN-520 PCMCIA card. ><

---

### Post by toorima on 2006-01-16
rightklick on the taskbar , add to panel, there u will find a wireless thing, that is gtkwifi

---

### Post by lilolpete on 2006-01-16
Awesome lol. Thank you. It says my card doesn't suport scanning? How would i work around that?

---

### Post by jasmuz on 2006-01-16
"Scanning" or Monitor mode as its known is not supported for all wireless card  who use Ndiswrapper.

---

### Post by azuro on 2006-01-17
I installed the GTK WiFi utility and it works pretty good.  One problem though, everytime I boot the computer, it waits for about 20secs when configuring network interface.  How can I eliminates that wait?

---

