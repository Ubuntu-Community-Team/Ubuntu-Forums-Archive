---
title: "DVBSky DVB-S/S2 and T/T2 PCIe Card - can not install"
date: 2014-06-27
forum: Multimedia Software
---

### Post by jonathan-l-harrison on 2014-06-27
I have bought a SkyDVB PCIe DVB-S/S2 and T card, but I am having trouble making it work.  Followed the instructions and installed the drivers and firmweare but it fails to be recognised.  Any help please

---

### Post by Vladlenin5000 on 2014-06-27
What instructions?

---

### Post by jonathan-l-harrison on 2014-06-28
Those on the cd and website.

I tried the CD drivers and firmware and those from the website too which are supposedly more up to date.  It would have been quicker and easier if it had an install script but still it was not too painful to follow.  However it does not work.


 ```
sudo su
```
 ```
apt-get update
```
 ```
apt-get upgrade
```
 

 # Install required build tools 
 ```
apt-get install kernel-package linux-headers-`uname -r`
```
 

   Download DVBSky Media build package (see: [http://www.dvbsky.net/Support.html](http://www.dvbsky.net/Support.html))
 ```
cd /usr/src
```
 ```
wget http://www.dvbsky.net/download/linux/media_build-bst-140128.tar.gz
 tar xf media_build-bst-140128.tar.gz
```

*was a bit confused about this next bit as it is not clear for novices like me....* so I ran ```
make && make install ./v4l/build_x64.sh
``` as mine is a 64-bit system and I weant DVB S/S2 & T/T2 and I think it is meant to be written this way.  There is no example.

 ```
cd media_build-bst
```
 # `build_x86.sh` for any 32-bit system with DVB-S/S2/T/T2 OR `build_dvbc_x86.sh` for DVB-S/S2/C driver
 # _`build_x64.sh` for any 64-bit system with DVB-S/S2/T/T2_ OR `build_dvbc_x64.sh` for DVB-S/S2/C driver
 # Run `uname -a` to determine if 32 or 64-bit (x86_64/amd64/ia64) is required.
  ./v4l/build_x86.sh ~OR~ ./v4l/build_dvbc_x86.sh ~OR~
    ./v4l/build_x64.sh ~OR~ ./v4l/build_dvbc_x64.sh
 ```
make && make install
```
 

 # Download and install firmware
 ```
cd /usr/src
```
 ```
wget http://www.dvbsky.net/download/dvbsky-firmware.zip
```
 ```
unzip dvbsky-firmware.zip
```
 ```
sh ./bst-firmware.sh
```
 

 # Reboot and check DVB devices
 ```
reboot
```

*this I get message /dev/dvb does not exist*
 ```
ls /dev/dvb
```

*this says and does nothing*
 ```
dmesg | grep -i dvb
```



Can you help or anyone, please?

---

