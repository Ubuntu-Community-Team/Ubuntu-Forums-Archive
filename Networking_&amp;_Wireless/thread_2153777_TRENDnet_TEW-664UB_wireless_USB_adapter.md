---
title: "TRENDnet TEW-664UB wireless USB adapter"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by Nate Hofmann on 2013-06-12
[COLOR=#333333][FONT=arial]Now how do I make it work. I ordered a TRENDnet TEW-664UB v2.0r to use for wireless wifi on my desktop, I downloaded the necessary driver from RealTek ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102)) for Ubuntu 13.04. Should it start automatically or what do you do to make it work? The OS is not even picking up the USB adapter too.[/FONT][/COLOR]

---

### Post by chili555 on 2013-06-12
> The OS is not even picking up the USB adapter too.Let's start here first. Please insert the device, open a terminal and run and post:```
lsusb
```How did you determine the driver you linked is appropriate for your device? You are probably correct, but I'm trying to learn.

EDIT: The Windows XP .inf file suggests it may possibly be an rtl8192cu device. That driver is included in 13.04 by default. It requires firmware which you may or may not have. We will know a whole lot more when we see the details of your device.

---

### Post by Nate Hofmann on 2013-06-12
[QUOTE=chili555;12688079]How did you determine the driver you linked is appropriate for your device? You are probably correct, but I'm trying to learn.

I used this site ([http://wikidevi.com/wiki/TRENDnet_TEW-664UB_v2](http://wikidevi.com/wiki/TRENDnet_TEW-664UB_v2)) to find the usb and followed the link to the RealTek Linux download for it ([http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102z](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102z)).


The terminal read this after entering it
 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 003: ID 20f4:664b TRENDnet

---

### Post by chili555 on 2013-06-12
> ID 20f4:664b TRENDnet Ooooh! I love new devices. It's always a challenge to find a workable way to get them going. The file you downloaded isn't the workable way. It won't build on my 13.04 system.

Fortunately, I believe there is a way. Please get a working ethernet connection and copy and paste these commands, each one at a time.```
sudo apt-get install build-essential linux-headers-generic git
git clone https://github.com/lwfinger/rtl8192du.git
cd rtl8192du
make
sudo make install
sudo modprobe 8192du
```Is it working now?

---

### Post by chili555 on 2013-06-12
> **ahallubuntu said:**
> 
I suspect you will get an error in 13.04, though.  Other Realtek drivers for similar devices also error out in 13.04 (even though they would build in 12.04 and 12.10).Yes, indeed. Since 13.04 is what he has, I recommend he not waste his effort.

---

### Post by Nate Hofmann on 2013-06-12
Thank you so MUCH!!! I ave been trying for over two weeks to get wireless up and runnin on my computer! Thanks you!

---

### Post by chili555 on 2013-06-12
> **Nate Hofmann said:**
> It installed through the terminal, though how can I telll if it is working, because my computer is still not picking up anything under network connections. Did I miss something?Let's do some checking. Was a wireless interface created, ideally wlan0 or maybe ra0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan  [COLOR="#FF0000"]<--Or ra0 as appropriate[/COLOR]
```Are there any interesting clues in the message log?```
dmesg | grep -e wlan -e 8192
```

EDIT: I assume it's working now?

When a newer kernel version, also known as linux-image, is installed by Update Manager, you will need to re-compile:```
cd rtl8192du
make clean
make
sudo make install
sudo modprobe 8192du
```

---

### Post by dosodavis on 2013-09-21
When I do this: git clone [https://github.com/lwfinger/rtl8192du.git](https://github.com/lwfinger/rtl8192du.git) 
I get an error:Failed connect to github.com:8000; Connection timed out while accessing
[https://github.com/lwfinger/rtl8192du.git/info/refs?service=git-upload-pack](https://github.com/lwfinger/rtl8192du.git/info/refs?service=git-upload-pack)
fatal:HTTP request failed

Can anyone help?

PS I'm using 13.04

---

### Post by Jonathan Precise on 2013-09-21
@ dosodavis: Please start a new thread for this.
***
Maybe the internet was down while you were accessing it? Try again, with firefox (or whatever browser you have) on one page while you have the command running.

If it works, then the site was probably down for maintenance.
[HR][/HR]@ Nate Hofmann: Please mark this thread as solved by going to thread tools.

---

### Post by evan8 on 2014-04-10
SUper old thread. But I just bought this USB adaptor today and wouldnt work on any f my machines. I was lucky and found this thread. kudos

sadly it's not getting any better spped than my 150 mbps. but all is well. now it can go on my other machine.
I have a PCI card in desktop. but since it's it th eback on computer and against the wall. i get horrible signal with that heh

---

### Post by chad14 on 2014-11-15
I followed the instructions on ubuntu 14.04 LTS, got this:

```

choodah@Scrapyd:~/Desktop/rtl8192du$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.13.0-39-generic/build M=/home/choodah/Desktop/rtl8192du  modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-39-generic'
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_cmd.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_security.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_debug.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_io.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_ioctl_set.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_ieee80211.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_mlme.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_mlme_ext.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_wlan_util.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_pwrctrl.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_rf.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_recv.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_sta_mgt.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_ap.o
  CC [M]  /home/choodah/Desktop/rtl8192du/core/rtw_xmit.o
/home/choodah/Desktop/rtl8192du/core/rtw_xmit.c: In function ‘update_attrib’:
/home/choodah/Desktop/rtl8192du/core/rtw_xmit.c:441:2: error: implicit declaration of function ‘ether_addr_copy’ [-Werror=implicit-function-declaration]
  ether_addr_copy(pattrib->dst, ehdr->h_dest);
  ^
cc1: some warnings being treated as errors
make[2]: *** [/home/choodah/Desktop/rtl8192du/core/rtw_xmit.o] Error 1
make[1]: *** [_module_/home/choodah/Desktop/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-39-generic'
make: *** [modules] Error 2

```

---

### Post by chili555 on 2014-11-15
Please check here: [https://github.com/lwfinger/rtl8192du](https://github.com/lwfinger/rtl8192du) Please notice there are two branches. Click on 'branches' and select kernel-version. On the right, click 'Download ZIP.' Downloads usually go to the folder Downloads. Next:```
cd ~/Downloads
unzip rtl8192du*.zip
cd rtl8192du-kernel-version
make
sudo make install
sudo modprobe 8192du
```Is it working now?

---

### Post by Graysun on 2015-02-13
You're the bomb. This worked for my BelkinF9L1108-TG Usb wireless adapter. Thank you for the assistance!

---

