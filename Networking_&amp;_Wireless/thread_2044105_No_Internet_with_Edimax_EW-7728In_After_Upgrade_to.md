---
title: "No Internet with Edimax EW-7728In After Upgrade to 12.04"
date: 2012-08-18
forum: Networking &amp; Wireless
---

### Post by lalaithan on 2012-08-18
I was upgrading an out of date box last night and now there is no way to utilize the wireless card to connect to wireless. The wireless itself is fine as I am using it now with Windows 7 on my laptop. No Network Management icon shows in the upper right corner with the time, either. I can't really make sense of the solutions out there because they're either out of date or don't really do anything. Anyone know how I can connect to the internet again? I could use it fine pre-upgrade.

---

### Post by chili555 on 2012-08-19
I think your device uses the driver rt2800pci. Let's load it and see what happens and if there are any interesting messages. Please open a terminal and run and post:```
sudo modprobe rt2800pci
dmesg | grep -i rt2
iwconfig
```Thanks.

---

### Post by lalaithan on 2012-08-19
> **chili555 said:**
> I think your device uses the driver rt2800pci. Let's load it and see what happens and if there are any interesting messages. Please open a terminal and run and post:```
sudo modprobe rt2800pci
dmesg | grep -i rt2
iwconfig
```Thanks.

Wow, I made a typo, hold on, I'll run it again.

---

### Post by lalaithan on 2012-08-19
I get this:
```

ashley@fuzzy-squirrel:~$ sudo modprobe rt2800pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove, it will be ignored in a future release.
ashley@fuzzy-squirrel:~$ dmesg | grep -i rt2
[   14.504483] rt2800pci 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.517506] Registered led device: rt2800pci-phy0::radio
[   14.517526] Registered led device: rt2800pci-phy0::assoc
[   14.517547] Registered led device: rt2800pci-phy0::quality
ashley@fuzzy-squirrel:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

---

### Post by chili555 on 2012-08-19
> [   14.504483] rt2800pci 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.517506] Registered led device: rt2800pci-phy0::radioWe see that the module loaded early in the boot process, undoubtedly automatically. We also see you have a wireless interface:> wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offDoes it scan?```
sudo iwlist wlan0 scan
```> No Network Management icon shows in the upper right corner with the time, either.Let's see if we can wake it up:```
nm-applet &
```Let's try to fix this:> WARNING: All config files need .conf: /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove, it will be ignored in a future release.Yikes!! What's in there? The contents will determine what we need to do to fix it:```
cat /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove
```Messy...

---

### Post by lalaithan on 2012-08-19
I get the following messages:

```
wlan0 Interface doesn't support scanning : Network is down
```

```

ashley@fuzzy-squirrel:~$ nm-applet &
[1] 2320
ashley@fuzzy-squirrel:~$ 
** (nm-applet:2320): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:2320): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:2320): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
```

```

ashley@fuzzy-squirrel:~$ cat /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove
# cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
blacklist usblp
```

---

### Post by chili555 on 2012-08-19
> ashley@fuzzy-squirrel:~$ cat /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove
# cups talks to the raw USB devices, so we need to blacklist usblp to avoid
# grabbing them
blacklist usblpPlease do:```
sudo mv /etc/modprobe.d/blacklist-cups-usblp.conf.dpkg-remove /etc/modprobe.d/blacklist-cups-usblp.conf
```That problem will be fixed.> wlan0 Interface doesn't support scanning : Network is downWe wonder why. Let's see if there are warnings or errors here:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
dmesg | grep wlan
```> ** (nm-applet:2320): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area...Googling...

EDIT: Please try:```
sudo apt-get install --reinstall network-manager
sudo apt-get install --reinstall network-manager-gnome
sudo service network-manager start
```Now is it working?

---

### Post by lalaithan on 2012-08-19
Nope, I get the following:

```
ashley@fuzzy-squirrel:~$ sudo apt-get install --reinstall network-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gstreamer0.10-plugins-base:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 ia32-libs-multiarch:i386 : Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: libopenal1:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
 libavcodec53 : Depends: libvpx1 (>= 1.0.0) but it is not going to be installed
 libflac8:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libshout3:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libsndfile1:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libtheora0:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 libvorbis0a:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 libvorbisfile3:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 software-center : Depends: python-apt (>= 0.8.3ubuntu4) but 0.8.0ubuntu9 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ashley@fuzzy-squirrel:~$ sudo apt-get install --reinstall network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gstreamer0.10-plugins-base:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 ia32-libs-multiarch:i386 : Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: libopenal1:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
 libavcodec53 : Depends: libvpx1 (>= 1.0.0) but it is not going to be installed
 libflac8:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libshout3:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libsndfile1:i386 : Depends: libogg0:i386 (>= 1.0rc3) but it is not going to be installed
 libtheora0:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 libvorbis0a:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 libvorbisfile3:i386 : Depends: libogg0:i386 (>= 1.1.0) but it is not going to be installed
 software-center : Depends: python-apt (>= 0.8.3ubuntu4) but 0.8.0ubuntu9 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ashley@fuzzy-squirrel:~$ sudo service network-manager start
network-manager start/running, process 2802
```

---

### Post by chili555 on 2012-08-19
This just gets messier and messier. I think you are at a crossroads. Is it better and less risky to do a backup and reinstall from scratch or is it better to try a repair as suggested:```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall network-manager
sudo apt-get install --reinstall network-manager-gnome
sudo service network-manager start
```There are a lot of problems there and a repair might or might not go perfectly.

Whichever approach you take, I'd back up *NOW!!*

---

### Post by lalaithan on 2012-08-19
I think I'm going to do a fresh reinstall. Thank you for all your help!

---

