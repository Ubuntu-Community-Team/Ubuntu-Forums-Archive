---
title: "restart afther upgrade to 11.04 failed"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by masodin on 2011-03-26
hello all,

i am an ubuntu nooby, out of curiosity i installed ubuntu 11.04 alpha3 last night.
Frankly said, i first installed 386 version on a notebook which runs  just fine. So I thought why not install the 64 bit version on my pc.

Unfortunately, the system did not finish  the first reboot in order to complete the installation. First it always  stopped at "checking battery state". There, I read that this bug is  already fixed:

[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/735805]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/735805")

So I pressed Alt +F2 in order to log in and performed sudo apt-get  update followed by sudo apt-get upgrade. Everytime there was a new  update I hoped, that this will fix the issue. But when I shutdown the system with sudo shutdown now -h and restart again there is no progress.

There will be a black screen where a lot of checks are performed
In particular there is one check that is not marked [ok]:

"Starting load fallback graphics devices [fail]" (fail appears in red)

I have just installed ubuntu 10.04.02 LTS on the same HD but a different partition, which works just fine.


According to 
lspci | grep VGA
cat /proc/cpuinfo | head -10
free -m

I use a Radon HD 4850, Intel Core2Duo CPU E8500 @ 3.16 GHz and have definitely enough memory left to run ubuntu 11.04. Can anyone of you PLEASE tell me what to do in order make ubuntu 11.04 alpha3 running? As a said I am a nooby and have absolutely no idea. 

If its not possible to make 11.04 running I would also be very happy to just move my home folder, my tex distibution and my Cran R from 11.04. to 10.04. Once this is achieved I would simply delete the 11.04 partion and never touch an alpha version again until I know what i am doing ;-)

Thanks.

masodin

---

### Post by kansasnoob on 2011-03-26
This is only a guess as I don't use a Radeon graphics chip, but from the release notes:

[http://www.ubuntu.com/testing/natty/alpha3#Graphics%20and%20Display](http://www.ubuntu.com/testing/natty/alpha3#Graphics%20and%20Display)

> The binary video drivers -fglrx and -nvidia do not have XServer 1.10 compatibility, so do not function in Alpha 3. We anticipate receiving an updated driver with this support from NVIDIA in the coming weeks, and an updated -fglrx from AMD at some point prior to Natty's release, but do not know their exact ETAs.   

Someone here may know of a work-around though.

---

### Post by cariboo on 2011-03-26
It would be helpful if you pasted the actual output of the commands you were given. It's not that I'm doubting you, but there might be something there that is helpful.

---

### Post by nystire on 2011-03-27
If you are using the proprietary driver, then the simplest work-around may be to run an 'apt-get purge fglrx fglrx-amdcccle', delete /etc/X11/xorg.conf and then reboot again. That will remove the proprietary driver and allow your system to use the open source one.

---

### Post by Harry33 on 2011-03-27
> **kansasnoob said:**
> This is only a guess as I don't use a Radeon graphics chip, but from the release notes:
[http://www.ubuntu.com/testing/natty/alpha3#Graphics%20and%20Display](http://www.ubuntu.com/testing/natty/alpha3#Graphics%20and%20Display)
> The binary video drivers -fglrx and -nvidia do not have XServer 1.10 compatibility, so do not function in Alpha 3. We anticipate receiving an updated driver with this support from NVIDIA in the coming weeks, and an updated -fglrx from AMD at some point prior to Natty's release, but do not know their exact ETAs.

Someone here may know of a work-around though.

Just to be clear, this incompatibility issue does not concern Nvidia proprietary drivers anymore. The driver version 270.30 works very well with the new xserver 1.10.
But, as far as ATI proprieatry drivers are concerned, they do not work with it, not yet.

So, definitely if the OP has fglrx installed, these drivers must be removed first.
They do break the X.

---

### Post by masodin on 2011-03-27
thanks for all your comments!!!

------------------------------------------------------------------------------------------------------------------------

@cariboo907

now, i figured out how to save terminal output and here it is:

lspci returns

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Network controller: Ralink corp. RT2800 802.11n PCI

cat /proc/cpu/cpuinfo | head -10 returns

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz
stepping    : 6
cpu MHz        : 2003.000
cache size    : 6144 KB
physical id    : 0
siblings    : 2

free -m returns

                     total       used       free     shared    buffers     cached
Mem:          8003          401       7601            0           29            118
-/+ buffers/cache:        254       7749
Swap:        23444          0      23444

----------------------------------------------------------------------------------------------------------------------------

Can anybody please tell me why 11.04 does not boot properly?
Is it really the Radeon?
How can I find out if I use a propritary driver? I do not want to delete files which will be regreted afterwards ;-)

Thanks in advance

---

### Post by masodin on 2011-03-27
> nystire              **Re: restart afther upgrade to 11.04 failed**
         If you are using the proprietary driver, then the simplest work-around  may be to run an 'apt-get purge fglrx fglrx-amdcccle', delete  /etc/X11/xorg.conf and then reboot again. That will remove the  proprietary driver and allow your system to use the open source one.           8 Hours Ago 08:10 PM

ok, I followed the suggestions by nystire but things are worse now as natty only shows a black screen, i.e. no checks are performed anymore. Guess, that removing xorg.conf-dist-upgrade-201103252315 was wrong. In the directory /etc/X11 there is also a file called xorg.conf which i have deleted as well. Still Natty does not boot. All i get is a black screen.

Anyone, please help?

---

### Post by ronparent on 2011-03-27
Natty is unfortunately much a work in progress. One of my own systems with an ATI HD card currently won't boot at all! I can boot to an earlier kernal (2.5.38-6 and earlier) with the 'nomodeset' boot parameter. This is not a satisfactory situation but might work if the block to booting involves the video drivers. Other than that you may need to wait for an update that fixes the problem for you.

---

### Post by Harry33 on 2011-03-27
> **ronparent said:**
> Natty is unfortunately much a work in progress. One of my own systems with an ATI HD card currently won't boot at all! I can boot to an earlier kernal (2.5.38-6 and earlier) with the 'nomodeset' boot parameter. This is not a satisfactory situation but might work if the block to booting involves the video drivers. Other than that you may need to wait for an update that fixes the problem for you.

You have Radeon HD5770, which may still be a bit unsupported by open source ati drivers.
However, Masodin has Radeon HD4850, which should work out of the box.
I remember using Radeon HD4870 with Intrepid Ibex, and open source drivers worked well even then (no boot problems).

---

### Post by Harry33 on 2011-03-27
> **masodin said:**
> ok, I followed the suggestions by nystire but things are worse now as natty only shows a black screen, i.e. no checks are performed anymore. Guess, that removing xorg.conf-dist-upgrade-201103252315 was wrong. In the directory /etc/X11 there is also a file called xorg.conf which i have deleted as well. Still Natty does not boot. All i get is a black screen.
Anyone, please help?

Try first booting with recovery mode from grub menu. Then from the small window (whiptail) choose failsafe boot and you have low graphics mode in use.
Then check, that you do not have file /etc/X11/xorg.conf installed or that it is empty.
After that, check that you have xserver-xorg-video-ati installed.

Sometimes upgrading from previous version is not successfull. It is better to install directly from Natty-alfa3-ISO.

---

### Post by unuu on 2011-03-29
Thanks this helped a lot and got it to work perfectly after upgrading from 10.10.

ALT + F2
sudo apt-get update
sudo apt-get upgrade
sudo su
apt-get purge fglrx fglrx-amdcccle
(found the /etc/X11/xorg.conf)
rm xorg.conf

reboot

and worked well. ATI HD 4850

---

