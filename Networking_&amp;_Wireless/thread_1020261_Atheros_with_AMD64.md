---
title: "Atheros with AMD64"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by efledderman on 2008-12-23
[SIZE=3]**Hardware**[/SIZE]:
Toshiba A215-5818
*Special Note: Atheros Wireless / AMD64*

[SIZE=3]**Ubuntu Versions**[/SIZE]:
Intrepid Ibex (Wubi Installation)
Intrepid Ibex (CD Distribution)
Hardy Heron (Wubi Installation)

[SIZE=3]**Problem**[/SIZE]:
I have tried a couple different versions and installation types.  Each one has had it's issues.  Fixing either Intrepid installation would be great, because Hardy Heron does not run very stable on this machine.  Thanks in advance.

[INDENT]**Intrepid (Wubi)**
Wireless works, but is very unstable (frequent disconnects and latency), after following these instructions:
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load
```
*Source: [Ubuntu Forums - Thread #964836]("http://ubuntuforums.org/showthread.php?t=964836")*

**Intrepid (CD)**
This installation has the best performance, and is obviously the one I would prefer to fix.  However, I get an error message stating "Unable to detect if Hardware is present" from the ndisgtk window after following these instructions:
```
**For AMD64 Users**:
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
sudo aptitude update
sudo aptitude install linux-headers-$(uname -r) build-essential
Install ndisgtk
sudo apt-get install ndisgtk
sudo ndiswrapper -i net5211.inf
sudo modprobe ndiswrapper
echo “ndiswrapper” | sudo tee -a /etc/modules
sudo reboot
sudo iwlist scan
```
*Source: [UbuntuGeek.com]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")*

**Hardy Heron (Wubi)**
Wireless works flawlessly after following the latter set of instructions, however, as mentioned aboe, this version runs very unstable on my machine.

[/INDENT]Any suggestions would be great.  Thanks again.

---

### Post by efledderman on 2008-12-24
Bump (post edited)

---

