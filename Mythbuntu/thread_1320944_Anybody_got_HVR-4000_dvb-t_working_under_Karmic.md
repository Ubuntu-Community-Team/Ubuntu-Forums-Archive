---
title: "Anybody got HVR-4000 dvb-t working under Karmic?"
date: 2009-11-09
forum: Mythbuntu
---

### Post by jensk on 2009-11-09
I have tried to upgrade my 9.04 backend til 9.10. The upgrade was Ok. Afterwards i could scan for channels etc so i though all was well. Unfortunately showing mpeg2 video is very errant. Video shows two pictures overlapping or greatly distorted pictures.

I have tried all thre major versions of firmware (CX24116)

Until further i stay with 9.04 and mythtv 0.21.

So i am interested to hear if anybody got the HVR-4000 card working with dvb-t  under 9.10 and mythtv 0.22 and how they did et it to work.

/jk

---

### Post by fussler on 2009-11-10
Hello. 
Same problem here. 
I have been trying to get it to work now over a week.
Tried the 3 firmwares and different programs.
Any help would be very much appreciated

---

### Post by fussler on 2009-11-10
It now works DVB-T
Im happy with my 5 swiss channels :0

:popcorn:

---

### Post by joshoekstra on 2009-11-11
Maybe you could tell how you did it? That way the search-function really helps instead of finding other people with trouble ;)
Much appreciated :)

---

### Post by jensk on 2009-11-13
> **fussler said:**
> It now works DVB-T
Im happy with my 5 swiss channels :0

:popcorn:

I sure would like to hear how you got it working. 

I have tried with thre three known working firwamre versions. I tried upgrading from 9.04 and I tried a clean install of 9.10.

In both cases it installed very well, I could scan channels etc. but when i tried to watch the recorded shows or livetv i had the picture show twice upshifted in the screen.

So i am very interested in how you did.
/jensk

---

### Post by jensk on 2009-11-15
I have tried to make a clean 9.10 install - parallel to my exiting 9.04 install.

Mythbuntu installs ok and i start the backend setup.

I can install the DVB-t part as an adaptor in the backend.

When I try to scan for channels Mythsetup dosn't find any. I have tried to enter the transports as they are setup in my 9.40 and scan existing transports - no channels found.

When i boot to my 9.04 partition everything is working again.

When i make a > dmesg | grep cx88 or > dmesg | grep firmware i can se no firmware being loaded to the card.

If I look at /lib/firmware there is no firmware file (dvb-fe-cx24116.fw) for the card. I have copied the version 1.20.xx.xx firmware file to /lib/firmware renamed to dvb-fe-cx24116.fw but it is still not loaded. Actually it is not requested.

Is the firmware not needed under the new kernel versions or is the missing load of firmware the reason why i can't find any channels.

Any help would be very welcome
/Jens

---

### Post by jensk on 2009-11-15
Well finally i solved this issue. My 9.10 server with a HVR-4000 and a PVR-500 card is working - both MPEG2, MPEG4 and HD om DVB-T here in Denmark.

My primary source if inf was this posting:
[https://bugs.launchpad.net/mythbuntu/+bug/439163](https://bugs.launchpad.net/mythbuntu/+bug/439163)
look at post #61.

It didn't work quite that way for me because the hg clone command didn't work. My way was this:

```
1. add repository deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe main restricted multiverse
2. sudo apt-get install build-essential mercurial linux-headers-generic libncurses5-dev
3. download [http://hg.kewl.org/v4l-dvb-20091103/archive/tip.tar.gz](http://hg.kewl.org/v4l-dvb-20091103/archive/tip.tar.gz)
4. Unpack
5. cd into the created dir v4l-dvb-fixes-f44........
6. make menuconfig
# -> Multimedia Support -> DVB/ATSC adapters -> disable FireDTV and FloppyDTV
7. make
8. sudo make install
9. reboot

```
Now go into the backend-setup and set everything as required. Scan for channels etc. Everything is working ok.

/jk

---

### Post by Jogdur on 2010-03-05
Hello

An updated version of Jensk recipe, including the latest v4l driver and firmware. It seems you also need this for lucid (2.6.32). Kernel 2.6.33 works fine as far as I can tell, but I haven't tested the scanning part of this kernel:

**Firmware:**
```
wget [http://www.wintvcd.co.uk/drivers/88x_2_124_27191_1_WHQL.zip](http://www.wintvcd.co.uk/drivers/88x_2_124_27191_1_WHQL.zip)
unzip -jo 88x_2_124_27191_1_WHQL.zip Driver88/hcw88bda.sys
sudo dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116-1.26.90.0.fw  skip=105768 bs=1 count=32674
sudo ln -s /lib/firmware/dvb-fe-cx24116-1.26.90.0.fw  /lib/firmware/dvb-fe-cx24116.fw

```**v4l driver:**

 add repository deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe main restricted multiverse
```
sudo su
apt-get install build-essential
apt-get install mercurial cvs subversion libncurses-dev
cd /usr/local/src
hg clone [http://hg.kewl.org/v4l-dvb-20100130/](http://hg.kewl.org/v4l-dvb-20100130/)
cd v4l-dvb-20100130
cd linux/include/linux
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h  ./
cd ../../../
make menuconfig
```-->Multimedia Support -> DVB/ATSC adapters  -> disable FireDTV and FloppyDTV. Otherwise the compiling will fail
 ```
make
make install
depmod -a
reboot
```Jog

---

### Post by xCAFEBABE on 2010-03-13
It works pretty well !!! Thanks...

But for me did not work the remote control... You can confirm that remote control of the HVR-4000 works for you in karmic.

I opened a question on the forum for some help thanks [http://ubuntuforums.org/showthread.php?t=1424325](http://ubuntuforums.org/showthread.php?t=1424325)

---

