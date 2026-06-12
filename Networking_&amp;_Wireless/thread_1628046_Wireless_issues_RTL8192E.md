---
title: "Wireless issues RTL8192E"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by GuitarJim1987 on 2010-11-22
I've recently installed ubuntu 10.10 32 bit on an external HDD in order to use it as a portable operating system.

An issue I have is when running on my laptop (Samsung R580) the wireless connection drops out however the nm-applet still shows it's connected. If I disconnect and reconnect it keeps asking for the access password. The wireless card on the laptop is the RTL8192E (not SE!). I have used the install on a couple of other machines with different wireless cards and no problems.

Linux Kernel version is 2.6.35-22-generic. I have searched around and see that the drivers are in early development.

Does anybody have any advice?

If I tried installing the windows driver via ndiswrapper would this affect the portability of the operating system?

---

### Post by grahammechanical on 2010-11-22
I want to see if I understand what you are doing? It might help others help you.

You plug in an external hard disk and boot from it. Is the installation on this hard disc setup as a Live installation such as found on Ubuntu Live CDs? If not I can imagine all kinds of problems. But then, I am not an expert.

As I understand the Ubuntu installation process, modules are chosen according to the hardware that is specific to the machine the OS is being installed on. So, my installation has drivers loaded at boot up that work the wireless device in my machine. If I was to transfer the hard disc to another machine and that machine had a different make of wireless device, then things will not work as they should. I think that I am correct about this.

This is why I ask about the type of installation that you have put on to this external hard disc. Knowing this information might avoid confusion.

regards.

---

### Post by GuitarJim1987 on 2010-11-22
I completed a full installation on the external hard drive and have used on several different PC's. The newer Kernels (not sure what from) check hardware on boot and load the applicable modules each time it boots, that's according to an experienced member of another forum who has moved installations to completely different computers with no issues.

Provided you don't use any proprietary drivers it runs fine (you can use proprietary drivers you just need to remove them when moving to a different machine). 

The two main PC's I use the installation on are my laptop (samsung R580) and my dad's PC (AMD Athlon II x2 545, onboard graphics, 2gb ram and a [Tenda Wireless N150]("http://www.ebuyer.com/product/149672")). The wireless on my dad's PC works flawlessly out of the box. The wirless on my laptop on the other hand with the RTL8192E has suffered with connection drops since I installed it (I installed ubuntu using the laptop) and before using it on another machine. 

I believe this to be a problem with the default driver in the Kernel and the only way I can think of to sort it is to either wait for a better one to be added or install the windows one via ndiswrapper.

If I use ndiswrapper I am concerned that it will act like a proprietary driver and overide any drivers the kernel loads when I move it to another machine hence causing problems with wireless access on another machine.

---

### Post by am0rphous on 2011-01-11
Hi,

Just replying because I had a very similar problem using wireless on my Samsung R580 (RTL8192E chipset): it would connect to the Internet, but it would often disconnect and sometimes it would need a reboot in order to be able to reconnect to the wireless router. 

  Furthermore, I would have daily (apparently random) crashes, where even the mouse and keyboard got stuck and I would get that lovely sound of stuck audio buffers if music was playing. 

 On the other hand, the wireless works fine if I boot Windows instead of Linux, which points towards a software (driver) problem and not hardware.  After much googling around, there didn't seem to be anyone with exactly the same issues I had (although, yes, there were several people with slightly different issues related to the RTL8192E chipset). 

 I then decided to try a driver that was recommended by someone. I downloaded the install script from [http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz) and downloaded a current snapshot of the wireless driver from [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb). 

 After running the install.sh script as superuser and doing a quick reboot, everything seemed to be automagically fixed. This was one or two weeks ago. Today, I just got my first crash since I have installed this new driver (which is a bummer), but it is still MUCH more stable than the driver that was included by default, so I highly recommend anyone with a Samsung R580 (or any laptop with the same wireless chipset) to try it out, if you're having problems with your current driver setup. 

 Note: I'm running maverick with 2.6.35-24-generic-pae and all the magic voria.org packages for the Samsung R580.

---

### Post by eldergs on 2011-02-23
Hi. I have the same problem. But, readying so many forum and post, I resolved the problem.

Sorry for my bad english.

First, open your terminal.

Run the code:

**lsmod | grep 819**

I think will show:

r8192e_pci
r8192se_pci

This is the conflicting drivers.

Now, run this code (to add r8192se_pci in blacklist):

[B]sudo su
echo "blacklist r8192se_pci" >> /etc/modprobe.d/blacklist.conf
exit[/B]

**Reboot**

Now, Download the newest driver from realtek, they mail me with instructions and file (I post in some servers)

[http://eldergs.4shared.com](http://eldergs.4shared.com)
[http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html](http://hotfile.com/dl/107013470/ed38f5d/rtl8192e_linux_2.6.0015.1013.2010.tar.gz.html)
[http://www.megaupload.com/?d=F2R0S36T](http://www.megaupload.com/?d=F2R0S36T)

Now do what the support from realtek say:

[B]Hi Sir,               
 
Thanks for your email.
 
Please find the attached for latest RTL8192E 32bit and 64bit Linux driver which is the updated one different from the one you used.
 
Just kindly remind, please install by the below steps.
The following is the installing steps:
1. Change to the driver directory
2. sudo su
3. make
4. make install
5.reboot
6. ./wlan0up or ./wlan1up
 
     Note: 1. if permission denied, change perperty with `chmod 777 wlan0up`
           2. or enable driver with `ifconfig wlanx up`(wlanx denote wlan interface name).
 
If your OS is 64bit, maybe there is kernel self driver for RTL8192E, you should delet it first before install:
 
 
    1) cd /lib/modules/2.6.3x.xx.xx/
    2) find -name "r8192e_pci.ko"
    3) delet all the r8192e_pci.ko
    4) install our RTL8192E driver
    5) reboot.
 
 
if there’s still any other problem, please let us know.
   Thanks a lot
 
Regards,
Kidman[/B]

Reboot

Now, You can use your Wireless and have fun.

:)

---

