---
title: "MSI L1350D Wireless connection issues"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by dvdragond2 on 2011-06-01
hello, im kinda new to this but ill get the ball rolling.
i just recently bought a MSI L1350D netbook, tried installing ubuntu 10.04 netbook remix but it didnt install.

after several different types of linux i finally got 9.10 to work (ubuntu) then updated it to 10.04, and in either distro i couldnt work out how to connect to the wireless.. is it a driver problem? or does the version of ubuntu not support wireless? 

Please help, i need the netbook working for my schooling

---

### Post by chili555 on 2011-06-01
> does the version of ubuntu not support wireless?LOL! No, 10.04 supports wireless quite well. There are a variety of reasons that a wireless card might not work out of the box. Let's gather some information and find out what we need to do. We're going to be using the terminal a bit here; the terminal allows us to get a lot of precise information quickly. Please open Applications > Accessories > Terminal and run and post:```
lspci -nn
```That will produce a lot of output, but feel free to trim away everything that is not your wireless card. Post the result here and we'll proceed.

---

### Post by dvdragond2 on 2011-06-04
you will have to wait for those results, my bro installed xp on it :(

---

### Post by chili555 on 2011-06-04
:( ,indeed! Post back if we can help you further.

---

### Post by dvdragond2 on 2011-06-04
ok, i got it back from him, and finally got the netbook remix to work, but i still have the same problem. i did the command above and here is the result

eli@eli-laptop:~$ lspci -nm
00:00.0 "0600" "8086" "a010" "1462" "1031"
00:02.0 "0300" "8086" "a011" "1462" "1031"
00:02.1 "0380" "8086" "a012" "1462" "1031"
00:1b.0 "0403" "8086" "27d8" -r02 "1462" "1031"
00:1c.0 "0604" "8086" "27d0" -r02 "" ""
00:1c.3 "0604" "8086" "27d6" -r02 "" ""
00:1d.0 "0c03" "8086" "27c8" -r02 "1462" "1031"
00:1d.1 "0c03" "8086" "27c9" -r02 "1462" "1031"
00:1d.2 "0c03" "8086" "27ca" -r02 "1462" "1031"
00:1d.3 "0c03" "8086" "27cb" -r02 "1462" "1031"
00:1d.7 "0c03" "8086" "27cc" -r02 -p20 "1462" "1031"
00:1e.0 "0604" "8086" "2448" -re2 -p01 "" ""
00:1f.0 "0601" "8086" "27bc" -r02 "1462" "1031"
00:1f.2 "0106" "8086" "27c1" -r02 -p01 "1462" "1031"
00:1f.3 "0c05" "8086" "27da" -r02 "1462" "1031"
01:00.0 "0280" "1814" "3090" -rff -pff "" ""
03:00.0 "0200" "10ec" "8136" -r02 "1462" "1031"


does this help in anyway?

---

### Post by dvdragond2 on 2011-06-04
sorry heres the updated version of the result

eli@eli-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090] (rev ff)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

---

### Post by chili555 on 2011-06-04
> Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [[COLOR="Red"]1814:3090[/COLOR]] (rev ff)This device is claimed by the driver rt2860sta in Ubuntu versions 10.10 and later. There is also a driver conflict; rt2800pci needs to be blacklisted.

It seems that your options are to try a little sneaky trick I know of that might or might not work; or download and compile the rt2860sta driver from Ralink; or upgrade to 10.10. Which do you prefer?

---

### Post by dvdragond2 on 2011-06-04
i don't know which is the easiest?

would this help? [http://ubuntuforums.org/showthread.php?t=1314747](http://ubuntuforums.org/showthread.php?t=1314747) because it apparently does?

---

### Post by chili555 on 2011-06-04
There are two different links that are referred to; both are quite old. May 2010 is old by Linux terms. As well, the version available for download has undoubtedly changed a few times since then. The links referred to are the second option:> or download and compile the rt2860sta driver from RalinkDo you have an ethernet connection available temporarily on the machine in question? If so, download the RT2860 package to your desktop and install the prerequisites:```
sudo apt-get install build-essential linux-headers-generic
```I will download the package, too and write up some correct instructions; there are some very serious flaws in the links that are referred to. I'll be back.

---

### Post by chili555 on 2011-06-04
Now that you have the file downloaded to your desktop, let's go to the terminal:```
cd Desktop
tar xvzf 2010
```Press the Tab key; the rest will fill in automagically.```
cd 2010
```Press the Tab key; the rest will fill in automagically.```
gedit os/linux/config.mk
```Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread carefully, save and close gedit.```
sudo su
make
make install
gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us if your wireless is working.

---

### Post by dvdragond2 on 2011-06-04
i completed your method for 1 one the netbooks, and it worked :)

for the other one i used the .deb download file from that link. and that also worked.

thanks mate :)

---

### Post by chili555 on 2011-06-05
Great work, sir (or madam)! I'm glad it's working. You will have helped some searchers, too.

---

