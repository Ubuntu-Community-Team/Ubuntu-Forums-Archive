---
title: "Two wireless card, how do I disable one of them?"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by Herber on 2013-04-09
I have a Sony Vaio with an intel Pro/wireless 2200BG (calexico2) card that is broken.  In windows I disabled this card and installed a USB wireless device (Realtek 802.11n WLAN adapter) which makes wireless connection possible.  I cannot get a wireless connection in LUBUNTU because the computer keeps on trying to connect through the original (broken) hardware.  How can I disable that original hardware.  I tried blacklisting the driver for the Intel hardware in /etc/modprobe.d but unfortunately that seems to interfere with any wireless connection.

---

### Post by chili555 on 2013-04-09
>  I tried blacklisting the driver for the Intel hardware in /etc/modprobe.d Please show us.

That's actually the best way to disable the built-in, if done correctly.

---

### Post by fyfe54 on 2013-04-09
Can you remove the offending card?  Then the system can't find it.

---

### Post by Herber on 2013-04-09
The computer I am using is a vaio laptop with a known bad internal hardware intel pro/Wireless 2200 BG, and a USB 802.11n edimax EW-7811Un from Realtek.  It is a dual boot system and when running windows I turn off the physical switch for wireless and the computer uses the edimax EW-7811Un USB wireless.  In Lubuntu, when I turn off the switch the Networking GUI show no options for wireless connections (which Makes sense).  When I have the switch turned to the "on" position the Networking GUI shows my router available to both wireless sources (the intel card and the edimax EW-7811Un).  The network manager then repeatedly tries to connect to the correct network, and occasionally show a connection only to fail when used.  When I blacklisted the Intel driver, the network manager no longer showed both cards, but continued to fail at obtaining a connection.  Now I am thinking that the edimax EW-7811Un USB device is not working properly in Linux.  Oh, a wired connection to the computer works fine and I am running 12.04 Lubuntu.

Realtek Kernel Module rtl8192cu
Intel Kernel Module IPW2200


Thank you for any help.

---

### Post by chili555 on 2013-04-09
Please show us the file where you did this:>  I tried blacklisting the driver for the Intel hardware in /etc/modprobe.d I suspect there is a slight error we can easily correct but I have to see the exact wording first.

---

### Post by Herber on 2013-04-09
I have not previously posted output in the forums but this is a copy of my modprobe.b

b@b-VGN-S360:/etc/modprobe.d$ cat blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

#stopping driver to intel wireless 
blacklist ipw2200


It is obviously the last entry.

---

### Post by chili555 on 2013-04-09
Looks perfect to me. Let's double-check a few other things:```
lspci -nn | grep 0280
cat /etc/modules
lsmod | grep ipw
```

---

### Post by Herber on 2013-04-09
b@b-VGN-S360:~$ lspci -nn | grep 0280
02:0b.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
b@b-VGN-S360:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b@b-VGN-S360:~$ lsmod | grep ipw
b@b-VGN-S360:~$ lsmod | grep ipw
b@b-VGN-S360:~$ 

The Realtek USB device just seems to search for the nework over and over, although with the blacklist, the intel card disappears.

---

### Post by chili555 on 2013-04-09
> although with the blacklist, the intel card disappears. Well, then the question is solved, correct? Are you ready to troubleshoot the USB? Please try a driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```Is the behavior improved, no change or worse?

---

### Post by Herber on 2013-04-09
The computer is unchanged after the above sudo modprobe commands.  I became suspicious earlier that the problem was the USB device and not the presence of the intel card.

---

### Post by chili555 on 2013-04-10
Let's try the updated driver suite compat-wireless. Please get a temporary ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-[COLOR="#FF0000"]xxx[/COLOR]-generic
```For the xxx, substitute your Ubuntu version here:```
lsb_release -a
```For example, on my machine, I get:> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantalSo I would need  linux-backports-modules-cw-3.6-[COLOR="#FF0000"]quantal[/COLOR]-generic. If you have quantal or precise, please proceed. If some other version, post back and we'll help.

Reboot. Does it connect? If not, try again:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```Now does it connect?

---

### Post by Herber on 2013-04-10
Unfortunately after I updated the modules (I am running precise) the behavior is unchanged.  Multiple reboots and the modprobe commands did not alter the outcome.  If this is any help, this is the behavior that made me decide the original laptop Intel Pci card was bad (it would find the correct SSID, but could never connect).  When I installed the USB wireless on widows boot that solved the problem.  When I started this thread I thought that it was the presence of both cards that caused the wireless failure on boot to the LUBUNTU partition.  But in reality it is the Realtek USB wireless that is now recognizing the correct SSID but unable to connect.

---

### Post by chili555 on 2013-04-10
> **Herber said:**
> Unfortunately after I updated the modules (I am running precise) the behavior is unchanged.  Multiple reboots and the modprobe commands did not alter the outcome.  If this is any help, this is the behavior that made me decide the original laptop Intel Pci card was bad (it would find the correct SSID, but could never connect).  When I installed the USB wireless on widows boot that solved the problem.  When I started this thread I thought that it was the presence of both cards that caused the wireless failure on boot to the LUBUNTU partition.  But in reality it is the Realtek USB wireless that is now recognizing the correct SSID but unable to connect.May I see:```
nm-tool
```Does the internal work in Windows?

---

### Post by Herber on 2013-04-10
The internal wireless does not even recognize any wireless access points in windows anymore (just checked).  The Realtek USB still works in windows, in Lubuntu it recognizes my home network and cycles through several attempts at connecting prior to (for lack of a better description) "giving up" and then it shows in the network manager GUI as "disconnected".

The output you asked about:
b@b-VGN-S360:~$ sudo nm-tool
[sudo] password for b: 

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        80:1F:02:9B:EA:E8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        08:00:46:F4:7C:A5

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             75.75.75.75


b@b-VGN-S360:~$

---

### Post by chili555 on 2013-04-10
I hate to say this in public, but  Realtek (rtl) drivers are in flux right now. I understand that there are quite a few (20+) bug fixes in the pipeline. That doesn't help us today. Since you are running 12.04, there is a pretty good chance we could compile the driver from Realtek. You could also give the device to some Windows friend and get another anything-but-Realtek device. I assume you could also keep the ethernet connected.

You might also download and try the 13.04 DVD to see if you connect as expected. If so, I'd install it.

Which do you prefer?

---

### Post by Herber on 2013-04-10
I really do appreciate all the time and effort you have given my problem here.  I would try the 13.04 beta, but my machine is a "non-pae" machine and the kernel in use is apparently incompatible (that is why I am running LUBUNTU).  I have a CD from the manufacturer with a linux driver on it, but I am suspicious that driver is the same one I am using currently (it is named rtl8192cu ver. 2.0.939.20200726.tar.gz).  I think when you say compile the realtek you mean something to do with NDSWRAPPER and the windows driver?  I would try that if you thought it might be useful. I think there may be a tutorial on the ubuntu site isn't there? 

And again thank you so much for your help here!!

---

### Post by chili555 on 2013-04-10
>  I think when you say compile the realtek you mean something to do with NDSWRAPPERNot quite. I mean build the Realtek provided one-size-fits-all driver against your currently running kernel. Since you have the driver on the CD, we can explore that path easily. Please drag and drop rtl8192cu ver. 2.0.939.20200726.tar.gz from the CD to your desktop. Right click it and select 'Extract Here.' Look inside the resulting folder and see if anything, a README perhaps or a changelog, suggests when this was created. I doubt it is July 26, 2020. If it is relatively recent, 2011 or so, we can try to compile it. In anticipation of that, install the prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Let me know what you find in the driver file.

---

### Post by Herber on 2013-04-10
Other than the build information I don't see a date for the driver release, and a quick internet search didn't reveal a date either.  I have extracted the .tar.gz and I have installed the build-essential.

---

### Post by chili555 on 2013-04-10
> **Herber said:**
> Other than the build information I don't see a date for the driver release, and a quick internet search didn't reveal a date either.  I have extracted the .tar.gz and I have installed the build-essential.When you open the folder in the file browser Nautilus (it may be something else in Lubuntu), what does the 'date modified' say? Here is an example.

---

### Post by Herber on 2013-04-10
7/27/2010 is the date on the .tar.gz on the CD.

---

### Post by chili555 on 2013-04-11
I'm pretty skeptical that it's going to compile, but it only takes a few moments to find out. You have the folder you extracted on your desktop, so open a terminal and do:```
cd Desktop/rtl8192cu...  [COLOR="#FF0000"]<--whatever the extracted folder is named[/COLOR]
sudo su
make
```At this point, one of three things can happen; it can end in ERROR, it can 'make' albeit with a few warnings, or it can 'make' with no warnings at all. If it ends in an error, post it here and we may be able to fix it. If it ends in a warning or no warning at all (fat chance), proceed:```
make install
modprobe -r rtl8192cu
modprobe rtl8192cu
exit
```I will be very interested in the outcome.

---

### Post by Herber on 2013-04-11
Hello,
Well you were right about the make command:
brasero.desktop     rtl8192CU_8188CU_linux_v2.0.939.20100726
firefox.desktop     rtl8192CU_linux_v2.0.939.20100726
lxterminal.desktop  vlc.desktop
b@b-VGN-S360:~/Desktop$ cd rtl8192CU_linux_v2.0.939.20100726
b@b-VGN-S360:~/Desktop/rtl8192CU_linux_v2.0.939.20100726$ sudo su
[sudo] password for b: 
root@b-VGN-S360:/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726# make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-40-generic/build M=/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-40-generic'
  CC [M]  /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o
In file included from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:60:0,
                 from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/rtw_xmit.h:318:24: error: field &#8216;xmit_tasklet&#8217; has incomplete type
In file included from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:61:0,
                 from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/rtw_recv.h:189:24: error: field &#8216;recv_tasklet&#8217; has incomplete type
In file included from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/drv_types.h:66:0,
                 from /home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.c:22:
/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/include/rtw_io.h:17:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-40-generic'
make: *** [modules] Error 2
root@b-VGN-S360:/home/b/Desktop/rtl8192CU_linux_v2.0.939.20100726# 


That is what I got.

---

### Post by chili555 on 2013-04-11
> fatal error: linux/smp_lock.h: No such file or directoryPlease see here: [http://unix.stackexchange.com/questions/46540/fatal-error-linux-smp-lock-h-no-such-file-or-directory](http://unix.stackexchange.com/questions/46540/fatal-error-linux-smp-lock-h-no-such-file-or-directory)> <linux/smp_lock.h> is the header file for the "Big Kernel Lock", which no longer exists as of 2.6.39. The author of this driver needs to do some work to modernize it.2.6.39??? Oh, my!!! Please note that you are on kernel version 3.2.0-xx. In other words, we no longer use wooden wheels on our sleek new BMWs!

Please try this from my own Dropbox: [https://dl.dropbox.com/u/58267392/RTL819xCU_USB_linux_%20v3%5B1%5D.3.2_3192.zip](https://dl.dropbox.com/u/58267392/RTL819xCU_USB_linux_%20v3%5B1%5D.3.2_3192.zip)

The process is not quite the same. Download it to your desktop. Right-click and 'Extract Here.' Open a terminal and do:```
cd Desktop/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103
sudo su
sh install.sh
```Note any errors. Warnings are probably OK. ```
modprobe -r rtl8192cu
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
modprobe 8192cu
exit
```Fingers crossed!

---

### Post by Herber on 2013-04-11
That is amazing you are a Linux God.  I am guessing that you had me compile and install an updated driver; but I looked on the web page for the product, and the one on the CD, was the same as the one in the kernel.  Thank you so much for all the help.

:D


Original question solved with blacklist driver, problem solved with the new driver you just gave me!!!

---

### Post by chili555 on 2013-04-11
> **Herber said:**
> Original question solved with blacklist driver, problem solved with the new driver you just gave me!!!As with any driver compiled from source code, every time an update installs a later kernel version, known in Ubuntu as linux-image, after you reboot, you'll need to re-compile:```
cd Desktop/RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103
sudo su
sh install.sh
modprobe 8192cu
exit
```Glad it's working. Have fun!

---

### Post by dottorepc on 2013-05-03
> **Herber said:**
> Original question solved with blacklist driver, problem solved with the new driver you just gave me!!!

Hi everyone!

Can I go back the original thread? I read through the misterious story, but I have the same problem as the original question was. The laptop (Acer Aspire 1356LMi) has got a WiFi card (Realtek RTL8180L 802.11b MAC), but weak, it is not able to connect either in Windows XP. I installed Lubuntu 12.04 and put another USB-WiFi antenna (TL-WN422G with ATHEROS USB2.0 WLAN in it). The USB adapter is working properly, connects, etc, but the old one annoys me. Allways puts up an authentication window and never connects, so I need to kill him.:D

How can I disable this old, built-in device?

The lspci -nn command gives me this line (and others of course, but this is the important one):
00:09.0 Ethernet controller [0200]: Realtek Semiconductor Co.,Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)

What should I add to the blacklist.conf file?
 
Thanks in advance!

---

### Post by Herber on 2013-05-03
Hello:
    In the file "/etc/modprobe/blacklist.conf" you need to list the name of the driver that you want to disable.  I am not a Linux expert, but you need to learn the name of the driver you are using for the non-functional card and then list it here.

---

### Post by chili555 on 2013-05-03
> Realtek Semiconductor Co.,Ltd. RTL8180L 802.11b MAC [[COLOR="#FF0000"]10ec:8180[/COLOR]]The native driver for your device is rtl8180. Let's blacklist and unload it:```
sudo su
echo "blacklist rtl8180" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8180
exit
```You should be all set.

---

### Post by dottorepc on 2013-05-03
I am not either, that was the reason I asked what should I put in that file!:D 

Never mind, I have resolved it already! With [help]("http://ubuntuforums.org/showthread.php?t=2082040") of course.:D Thanks chili555!!!

Here comes, how:

As I wrote it before, I thought so, this device is a Realtek WiFi antenna (because the other one is Atheros).

Command: ```
lscpi -nn | grep Realtek
```
Answer: ```
00:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
```

The next command at terminal gave me some more detailed info on it:
Command: 
```
lscpi -knn | grep rtl
```

Answer:```

    Kernel driver in use: rtl8180
    Kernel modules: rtl8180
```

Command:
```
lsmod | grep rtl 

```
Answer:
```
rtl8180                35880  0 
mac80211              436493  1 rtl8180
eeprom_93cx6           12687  1 rtl8180
cfg80211              178877  2 rtl8180,mac80211


```
Command:```

lsb_release -d

```
Answer:```

Description:    Ubuntu 12.04.2 LTS

```
So, at this point I was sure, what i need to add to blacklist.conf. So I did it.

```
# DISABLE DRIVER OF WEAK BUILT-IN WIFI ANTENNA
blacklist rtl8180



```

Restart, test, all went ok!

Thanks anyway!

---

### Post by dottorepc on 2013-05-03
Ooops, I was late...

---

