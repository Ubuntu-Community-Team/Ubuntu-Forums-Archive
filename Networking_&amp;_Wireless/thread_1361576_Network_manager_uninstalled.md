---
title: "Network manager uninstalled"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by gberet on 2009-12-22
I have uninstalled Network manager by mistake, so I've no internet on Ubuntu and now I'm posting this from Windows, so plz some body tell me what to do to repair this problem, otherwise I'll have to reinstall Ubuntu again

---

### Post by ajgreeny on 2009-12-22
You will need to download the package from the appropriate page of [http://packages.ubuntu.com/](http://packages.ubuntu.com/) using windows and then copy it across from there to ubuntu and double click it to install.  Any dependencies you also uninstalled will need the same method.

---

### Post by NoBugs! on 2011-05-04
I have the same problem, a partial-upgrade said network-manager, dhcp-something, and other packages should be removed, and after the partial-upgrade, no networking! I managed to install the network-manager applet by marking the packages in synaptic, then selecting save download script, then downloading on another OS and installing the downloaded packages. But the nm-applet now says Networkmanager is not running. 

I tried the instructions for enabling wired connection [here]("http://ubuntuforums.org/showthread.php?t=772471"), but it always says Unknown interface (I tried eth0, eth1, eth2, eth3.)

---

### Post by mhgsys on 2011-05-04
If you are on a wired connection, and if your ehternet device is eth0 then
in terminal
```
sudo dhclient eth0
```

should get your internet going. (*Change the eth0 to whatever your network device is)

after that; 
```
 sudo apt-get install network-manager-gnome
```

and networkmanager should be back

---

### Post by NoBugs! on 2011-05-04
Network-manager-gnome is already installed, I downloaded the .deb files and reinstalled them. I see the network applet, but when I click it it only says "NetworkManager is not running". I try to restart it with:
```
sudo restart networking
sudo restart network-manager
```
It only shows error:
```
restart: unknown instance:
```

---

### Post by mhgsys on 2011-05-04
it should be; 
```
sudo service network-manager start
```
 sudo restart network-manager works when it's actually started 
:-D

---

### Post by NoBugs! on 2011-05-04
I tried that too, it says start/running, pid some-number, and there's still nothing in the networkmanager applet except "Networkmanager is not running". closing out nm-applet and restarting it didn't help either.

---

### Post by mhgsys on 2011-05-04
running out of idea's for you; 
perhaps try reinstalling network-manager with 
```
sudo apt-get --reinstall install network-manager
```
```
sudo apt-get --reinstall install network-manager-gnome
```

so you are sure you are not missing any dependency's

edit: come to think about it ; it looks like the network-manager-gnome is the applet and that's working.. it's just the network-manager not working out for you
(you need both packages. so above commands should work after you gained on ip adress with the dhclient command we spoke about before)

---

### Post by NoBugs! on 2011-05-04
It's odd that a normal partial-update would mess it up. The problem might be related to the networkmanager daily-trunk ppa I installed earlier. [https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)
I remember it changed some config files, maybe if they were changed back to the default 10.04 configs it would work?

---

### Post by NoBugs! on 2011-05-05
I noticed dhcp-client wasn't installed, and dhcp-common was the nm-trunk version. I uninstalled the nm-trunk package, downloaded dhcp3-client and dhcp3-common packages on another computer, and installed them and it works now :)

---

