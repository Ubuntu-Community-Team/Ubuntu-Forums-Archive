---
title: "Broadcom 4727 Wireless Card issues: can't connect to any network?"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Helenarth on 2011-06-16
Hi,  I just installed 9.10 and I can't detect any wireless networks. Is the card compatible with 9.10? Do I need to install any drivers? If the card isn't compatible with 9.10 is it compatible with later versions of Ubuntu? Thanks.

Marking this as somewhat urgent as I need to get internet access for some coursework soon, and also because my parents will kill me if they find out I've done anything unusual with the laptop because it's new and they think anything non -MS is a virus.

---

### Post by Helenarth on 2011-06-17
Can anyone help?

---

### Post by DirtyPC on 2011-06-17
I'm on it give me 5 minutes.

---

### Post by DirtyPC on 2011-06-17
first thing is first. Open Applications>Accessories>Terminal and type lspci and copy and paste the output

---

### Post by DirtyPC on 2011-06-17
either connect to internet, or put in your cd and in the terminal type

sudo apt-get install bcmwl-kernel-source. OR get it from synaptic package manager.

---

### Post by Helenarth on 2011-06-17
Right,  will do.  The sudo command tells me that bcmwl-kernel-source is already the latest version. I'll post the lspci in a minute I just need to start up my old computer to use the net (on my phone's 3G right now).

---

### Post by chili555 on 2011-06-17
I hate to step on someone else's thread, but I'd love to see:```
rfkill list all
```

---

### Post by DirtyPC on 2011-06-17
if you've already got the kernel source, then activate the hardware drivers, and unistall the standard bcmxxx driver

---

### Post by Helenarth on 2011-06-17
helena@Helena:~$ sudo apt-get install bcmwl-kernel-source  
 [sudo] password for helena:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 bcmwl-kernel-source is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 

 helena@Helena:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)  
 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)  
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)  
 00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)  
 00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)  
 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)  
 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)  
 04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller  
 06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)  
 

helena@Helena:~$ rfkill list all
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

---

### Post by Helenarth on 2011-06-17
> **harrylucas1 said:**
> if you've already got the kernel source, then activate the hardware drivers, and unistall the standard bcmxxx driver

Sorry to ask, but how do I do this?

---

### Post by chili555 on 2011-06-17
I think my colleagues would now love to see:```
dmesg | grep -e wl -e eth1
iwconfig
sudo iwlist eth1 scan
```When you click the Network Manager icon, do you see networks? Does it try to connect and time out or...what?

---

### Post by DirtyPC on 2011-06-17
System>Administration> Drivers (hardware or additional) Install the bcmwl one and uninstall the bcm43 cutter one. If the bcm43 cutter one is not there, go to synaptic package manager and uninstall it from there

---

### Post by Helenarth on 2011-06-17
Chili555: helena@Helena:~$ dmesg | grep -e wl -e ethl
helena@Helena:~$ iwconfig
lo no wireless extensions
eth0 no wireless extensions
pan0 no wireless extensions
helena~@Helena:~$ sudo iwlist ethl scan
[sudo] password for helena:
ethl Interface doesn't support scanning.

harrylucas1: It says there are no proprietary drivers in use on this system. When I searched for bcm43 under Synaptic Package Manager, it came up with b43-fwcutter. It only gives me the option to mark it for installation.

---

### Post by chili555 on 2011-06-17
Now try:```
sudo modprobe wl
dmesg | grep wl
```Any warnings or errors that are kicked out will be informative.

---

### Post by Helenarth on 2011-06-17
helena@Helena:~$ sudo modprobe wk
[sudo] password for helena:
helena@Helena:~$ dmesg | grep wl
[  4669.963905] wl: module licsense 'MIXED/Proprietary' taints kernel.

And "wl" after the string of numbers was in red.

---

### Post by DirtyPC on 2011-06-17
This is a bug. Your actual driver is BCM-4313.
In synaptics, Re mark the bcmwl-kernel-source driver for reinstallation. And then reboot.
It should work then.

---

### Post by chili555 on 2011-06-17
> $ dmesg | grep wl
[ 4669.963905] wl: module licsense 'MIXED/Proprietary' taints kernel.After the driver loaded, now do you have a wireless interface?```
iwconfig
```

---

### Post by DirtyPC on 2011-06-17
Or just download [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by chili555 on 2011-06-17
> **harrylucas1 said:**
> Or just download [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)I believe the driver is already installed; *wl* loaded without error.

---

### Post by DirtyPC on 2011-06-17
Some people report that reinstalling the driver works. Installing by default sometimes leaves it incorrectly configured.

---

### Post by Helenarth on 2011-06-17
Iwconfig still tells me no wireless extensions for lo, eth0 and pan0. I'll reboot and if it doesn't work then I will download that. Fingers crossed!

---

### Post by DirtyPC on 2011-06-17
It worked for me, running a similar drive

---

### Post by DirtyPC on 2011-06-17
Any luck?

---

### Post by Helenarth on 2011-06-17
...It doesn't seem to have worked. Here's what happens when I go to Network Connections: aka nothing
[IMG]http://i54.tinypic.com/ehkzfd.jpg[/IMG]

---

### Post by superduperlinuxperson on 2011-06-17
run lspci -vnn | grep 14e4 and tell me what the output is
thanks

---

### Post by DirtyPC on 2011-06-17
left click on the wireless icon, see if its enabled and also see what it says about your wireless connection.

---

### Post by DirtyPC on 2011-06-17
Did you install the driver through the link posted?

---

### Post by Helenarth on 2011-06-17
helena@Helena:~$ lspci -vnn | grep 14e4 
06:00.0 Network controller [0290]: Broadcom Corporation Device [14e4:4727] (rev 01)

14e4 was in red.

---

### Post by Helenarth on 2011-06-17
Am about to,  if I download it onto my memory pen and open it on ubuntu that'll work right.

---

### Post by DirtyPC on 2011-06-17
yeah, just copy it to desktop,

then run cd Desktop

---

### Post by superduperlinuxperson on 2011-06-17
you have a very strange and relatively new chip: try going to the additional drivers and see whats there
thanks

---

### Post by DirtyPC on 2011-06-17
> **superduperlinuxperson said:**
> you have a very strange and relatively new chip: try going to the additional drivers and see whats there
thanks
This has been gone through, read the rest of the OP's posts first.

-theres nothing in additional drivers, and its a bcm-4313, its a bug

---

### Post by superduperlinuxperson on 2011-06-17
look at this: [http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211)
thanks

---

### Post by Helenarth on 2011-06-17
Wait so I've copied it to the desktop, then I run cd Desktop? Is that in Terminal or...?
I am so new. -_-

---

### Post by DirtyPC on 2011-06-17
cd Desktop in the terminal, this changes it to the dekstop directory (where the file is)

---

### Post by Helenarth on 2011-06-17
Okay.
helena@Helena:~$ cd Desktop
helena@Helena:~/Desktop$

---

### Post by chili555 on 2011-06-17
> **Helenarth said:**
> helena@Helena:~$ lspci -vnn | grep 14e4 
06:00.0 Network controller [0290]: Broadcom Corporation Device [14e4:4727] (rev 01)

14e4 was in red.I believe wl is correct for your device and you already have it installed:> $ modinfo wl | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*> helena@Helena:~$ sudo modprobe wk
[sudo] password for helena:
helena@Helena:~$ dmesg | grep wl
[ 4669.963905] wl: module licsense 'MIXED/Proprietary' taints kernel.
If you want to install the driver direct from Broadcom, you will get no more than you already have and you will need build-essential and linux-headers.

---

### Post by DirtyPC on 2011-06-17
then in terminal: tar xvf <filename>.tar.gz
then
cd name-of-program

./configure
make
sudo make install

---

### Post by superduperlinuxperson on 2011-06-17
@harrylucas
if it is bcm4313, here is how you install it:
step 1: download these two things from here:[http://downloads.openwrt.org/sources...a-3.130.20.0.o](http://downloads.openwrt.org/sources...a-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2](http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2)
step 2: extract the second one to your home folder, and copy the other one their too
step 3: download b43-fwcutter from the software center
step 4: execute these steps in terminal too get it working:

~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by Helenarth on 2011-06-17
Harrylucas1: How do I find out the name of the program?

superduperlinuxperson: Thank you, I'll give that a shot in a minute.

---

### Post by chili555 on 2011-06-17
> if it is bcm4313, here is how you install it:It is not.

---

### Post by superduperlinuxperson on 2011-06-17
@chili555
thats what i thought, but harrylucas said it was a bug,

---

### Post by Helenarth on 2011-06-17
While downloadng b43-fwcutter:
E: b43-fwcutter subprocess installed post-installation script returned error exit status 1

And then when I input the commands it told me it couldn't open the input file... for both.

---

### Post by Helenarth on 2011-06-17
I'm getting increasingly worried that I'm going to follow one of your instructions wrongly and completely screw up something, since I'll be honest and say I have no idea what I'm doing here. From what I've said, does the problem look like it'll be solved soon?

---

### Post by DirtyPC on 2011-06-17
Right, i'm quite annoyed. Regarding the guy who's tells me i'm wrong with a lot of beans (sig seems pretty adequate here) I've had personal expirience here. A simple browse through google and you'll find it IS infact a 4313. Don't believe me?

Quote from a forum: Title: Re: ASUS Eee PC 1015 - Broadcom 4727 Wireless Problem


I couldn't remember what directory I was in so I tried to rerun the last half of the procedure. The procedure in the Readme.txt for the driver said to run the modprobe and insmod command from the /lib/modules/... But I tried to run them from both there and the /hybrid_wl directory. I got the same result both times. Is it possible i'm barking up the wrong tree? The reason I picked this driver was because when I do the lspci command my pci code was 14e4:4727, which the readme said was the Broadcom 4313. Since my wireless didn't work out of the box, I figured this was the driver I needed.


And what really annoys me, is that on that forum, chilli555 posted on that. Saying exactly the thing I told the op to do

---

### Post by DirtyPC on 2011-06-17
> **Helenarth said:**
> I'm getting increasingly worried that I'm going to follow one of your instructions wrongly and completely screw up something, since I'll be honest and say I have no idea what I'm doing here. From what I've said, does the problem look like it'll be solved soon?
Don't worry, I have expirience with this, it will get solved.
You do not want the b43 driver as they don't work very well.

---

### Post by DirtyPC on 2011-06-17
> **harrylucas1 said:**
> Don't worry, I have expirience with this, it will get solved.
You do not want the b43 driver as they don't work very well.
At original poster.
Open terminal and type: sudo apt-get remove bcmwl-kernel-source
restart then in terminal type: sudo apt-get install bcmwl-kernel-source
That should work.

---

### Post by DirtyPC on 2011-06-17
> **harrylucas1 said:**
> At original poster.
Open terminal and type: sudo apt-get remove bcmwl-kernel-source
restart then in terminal type: sudo apt-get install bcmwl-kernel-source
That should work.
Also from Broadcom's Documentation
4313 2.4 Ghz	    0x14e4	0x4727 

Here, 4313 is the model, 4727 is the vendor id. For some reason the bug lists the vendor id in place of the model

---

### Post by Helenarth on 2011-06-17
> **harrylucas1 said:**
> Don't worry, I have expirience with this, it will get solved.
You do not want the b43 driver as they don't work very well.

Thank you. Now, earlier you said this:
> **harrylucas1 said:**
> then in terminal: tar xvf <filename>.tar.gz
then
cd name-of-program

./configure
make
sudo make install

Executing the first seems to have extracted the tar.gz file onto the desktop. Just wanted to make sure that's right.
What's the name of the program I'm looking for? The files I have on the desktop are tehe tar.gz file with a long name, "lib" folder, "src" folder, "makefile", and "built-in.o". The latter appeared after I put in a different command, and I'm not sure it's supposed to be there.

---

### Post by DirtyPC on 2011-06-17
> **Helenarth said:**
> Thank you. Now, earlier you said this:


Executing the first seems to have extracted the tar.gz file onto the desktop. Just wanted to make sure that's right.
What's the name of the program I'm looking for? The files I have on the desktop are tehe tar.gz file with a long name, "lib" folder, "src" folder, "makefile", and "built-in.o". The latter appeared after I put in a different command, and I'm not sure it's supposed to be there.
it will be 

cd hybrid-portsrc_x86_32-v5_100_82_38

./configure
make
sudo make install


You could do this or

sudo apt-get remove bcmwl-kernel-source
reboot then
sudo apt-get install bcmwl-kernel-source

---

### Post by Helenarth on 2011-06-17
> **harrylucas1 said:**
> At original poster.
Open terminal and type: sudo apt-get remove bcmwl-kernel-source
restart then in terminal type: sudo apt-get install bcmwl-kernel-source
That should work.
 
When I run sudo apt-get remove bcmwl-kernel-source it says:
The following packages were automatically installed and are no longer required: fakeroot dkms patch
Use apt-get autoremove to remove them.

When I confirmed the deletion:
...
Resolving downloads.openwrt.org... failed: Name or service not known. 
wget: unable to resolve host address 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by DirtyPC on 2011-06-17
> **harrylucas1 said:**
> it will be 

cd hybrid-portsrc_x86_32-v5_100_82_38

./configure
make
sudo make install


You could do this or

sudo apt-get remove bcmwl-kernel-source
reboot then
sudo apt-get install bcmwl-kernel-source
I'd recommend this, it's much easier

---

### Post by chili555 on 2011-06-17
Sorry if I annoyed anyone. I believe wl, i.e. bcmwl-kernel-source is correct. I am distressed that rfkill lists bluetooth but not wireless and I am also distressed that the installation of wl doesn't seem to start the usual interface eth1.

I will go have a nap now. Harry will have you fixed in no time.

---

### Post by DirtyPC on 2011-06-17
> **harrylucas1 said:**
> I'd recommend this, it's much easier
run 
apt install -f

---

### Post by DirtyPC on 2011-06-17
> **harrylucas1 said:**
> run 
apt install -f
or remove it from synaptics.

---

### Post by Helenarth on 2011-06-17
After apt install -f:
The program 'apt' can be found in the following packages:
*openjdk-6-jdk
*sun-java-6-jdk
Try: supo apt-get install <selected package>
apt: command not found

---

### Post by Helenarth on 2011-06-17
Synaptic Package Manager says bcmwl-kernel-source is uninstalled.

---

### Post by DirtyPC on 2011-06-17
no you do the in the terminal after doing 
sudo apt-get install bcmwl-kernel-source if it fails.

Try deleting it from synaptics package manager.

---

### Post by DirtyPC on 2011-06-17
also re install dkms from synaptics too.

---

### Post by DirtyPC on 2011-06-17
> **Helenarth said:**
> Synaptic Package Manager says bcmwl-kernel-source is uninstalled.
now, reboot and install bcmwl-kernel-source

---

### Post by Helenarth on 2011-06-17
Okay, uninstalled, rebooted, reinstalled bcmwl-kernel-source and dkms (the first with terminal and the second with Synaptic). Both gave me error messages about b43-fwcutter.

---

### Post by Helenarth on 2011-06-17
Something seems to have happened? Under Wired Network Connections, "Autp eth0" has appeared. I plugged my computer in to the router via cable. It says "Last Used: never" though, and opening an internet browser returns a page not found.

---

### Post by DirtyPC on 2011-06-17
sudo apt-get remove b43-fwcutter

Try that, b43 causes nothing but trouble.

then re install the bcmwl and dkms

---

### Post by Helenarth on 2011-06-17
Right, done that. Nothing's changed - shall I reboot?`

---

### Post by DirtyPC on 2011-06-17
yes reboot, then install dkms and bcmwl-kernel-source. Click on the network icon on the top rightthen see what appears

---

### Post by DirtyPC on 2011-06-17
anyluck?

---

### Post by Helenarth on 2011-06-17
Still no change, nothing's appearing on the wireless connections tab, the icon itself shows "no connection" when the pointer's over it, and the "auto eth0" that appeared isn't doing anything either.

---

### Post by DirtyPC on 2011-06-17
Then, on your laptop.

Hold the FN key and the key that activates your wireless.

---

### Post by DirtyPC on 2011-06-17
if that did not work. Do:

Open Synaptic Pacakage Manager and search: bcmwl
if the bcmwl-kernel-source package is installed remove it.

- Download (you can use the live cd):
fakeroot_1.14.4-1ubuntu1_i386.deb
patch_2.6-2ubuntu1_i386.deb
from Ubuntu packages ([http://packages.ubuntu.com/](http://packages.ubuntu.com/))

- Install the downloaded packages:
$ sudo dpkg -i patch*
$ sudo dpkg -i fakeroot*

- Put the ubuntu 10.04 "live cd" in CD drive and open Synaptic

- Go to: "Settings/Repositories/Ubuntu Software", check the installable from CD-ROM/DVD option and close the "Software Sources" window.

- Click the reload button on Synaptic, search: bcmwl and install the bcmwl-kernel-source package.

- Reboot the computer and go to: System/Administration/Hardware Drivers and activate Broadcom STA wireless driver

---

### Post by Helenarth on 2011-06-17
Right, give me a few minutes and I'll put those in, gotta do something first

---

### Post by Helenarth on 2011-06-17
Okay, I downloaded the fakeroot from that site but I'm having trouble finding the patch one. I installed fakeroot, that went fine. Also I tried FN, the light for the wireless on my laptop is on but it's still not detecting anything.

---

### Post by Helenarth on 2011-06-17
I installed the fakeroot and the path file that was in Synaptic, and I also installed the bcmwl-kernel-source, then rebooted, but it's still not working. Synpatic says they've all been installed, but the driver won't show up on the Hardware Drivers list. :|

---

### Post by DirtyPC on 2011-06-17
did you not install the patch?

---

### Post by DirtyPC on 2011-06-17
[http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/patch_2.6-2ubuntu1_i386.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/patch_2.6-2ubuntu1_i386.deb.html)

---

### Post by Helenarth on 2011-06-17
I installed the file named "patch" that was in the synaptic manager after I changed added the livecd as a repository. I couldn't find that patch file on the website when I searched for it though.

---

### Post by DirtyPC on 2011-06-17
Don't worry, i've finally got it!

Make sure the proprietary broadcom driver is not loaded by the system, open "Additional driver" application in system > administration and disable the driver if it was enabled, restart if necessary.

Open terminal (Applications>Accessories>Terminal) and copy paste these lines one after another.

Install build packages
Code:
sudo apt-get install build-essential git-core

Download the driver and the firmware
Code:
git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
Modify the file to make it work with your kernel
Code:
cd ~/linux-next/drivers/staging/brcm80211
nano Makefile
Add this code at the end
Code:
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
CTRL+X to exit and save


Compile the driver
Code:
make
If it exit with and error then check the UPDATE section at the top.


Copy it in the proper dir
Code:
sudo cp brcm80211.ko /lib/modules/`uname -r`/

Download and copy the device's firmware
Code:
sudo mkdir /lib/firmware/brcm
cd ~/linux-firmware
sudo cp brcm/bcm43xx* /lib/firmware/brcm
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw

Load the driver module
Code:
sudo modprobe mac80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko
At this point the wireless should work correctly in network-manager


Load dependencies
Code:
sudo depmod -a

Add the module to the startup
Code:
sudo nano /etc/modules
Add this lines at the end
Code:
brcm80211
CTRL+X to exit and save


Fix the problem with suspending
Code:
sudo nano /usr/lib/pm-utils/defaults
add after #SUSPEND_MODULES=""
Code:
SUSPEND_MODULES="brcm80211"
CTRL+X to exit and save

---

### Post by DirtyPC on 2011-06-17
That should fix it. It's a bug within the bcmwl driver that fails to load the firmware to the device correctly. The fix above is included in 11.04 !

---

### Post by Helenarth on 2011-06-17
Right away it tells me "couldn't find package git-core" :/
Whoa, thank you for all your work, though.

---

### Post by DirtyPC on 2011-06-17
just copy and paste it. I tried it now and it works fine for me

---

### Post by DirtyPC on 2011-06-17
If none of this works, i'd advise to just install 11.04 as it will work straight away.

---

### Post by Helenarth on 2011-06-17
helena@Helena:~$ sudo apt-get install build-essential git-core
[sudo] password for helena: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package git-core
helena@Helena:~$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
git: command not found
helena@Helena:~$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
git: command not found
helena@Helena:~$ cd ~/linux-next/drivers/staging/brcm80211
bash: cd: /home/helena/linux-next/drivers/staging/brcm80211: No such file or directory
helena@Helena:~$ nano Makefile
helena@Helena:~$ make
Makefile:9: *** missing separator. Stop.
helena@Helena:~$ sudo cp brcm80211.ko /lib/modules/`uname -r`/
cp: cannot stat `brcm80211.ko': No such file or directory
helena@Helena:~$ sudo mkdir /lib/firmware/brcm
mkdir: cannot create directory `/lib/firmware/brcm': File exists
helena@Helena:~$ cd ~/linux-firmware
bash: cd: /home/helena/linux-firmware: No such file or directory
helena@Helena:~$ sudo cp brcm/bcm43xx* /lib/firmware/brcm
cp: cannot stat `brcm/bcm43xx*': No such file or directory
helena@Helena:~$ cd /lib/firmware/brcm
helena@Helena:/lib/firmware/brcm$ sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fwln: creating symbolic link `bcm43xx-0.fw': File exists
helena@Helena:/lib/firmware/brcm$ sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw
ln: creating symbolic link `bcm43xx_hdr-0.fw': File exists
helena@Helena:/lib/firmware/brcm$ sudo modprobe mac80211
helena@Helena:/lib/firmware/brcm$ sudo insmod /lib/modules/`uname -r`/brcm80211.ko
insmod: can't read '/lib/modules/2.6.31-14-generic/brcm80211.ko': No such file or directory
helena@Helena:/lib/firmware/brcm$ sudo depmod -a
helena@Helena:/lib/firmware/brcm$ sudo nano /etc/modules
helena@Helena:/lib/firmware/brcm$ sudo nano /usr/lib/pm-utils/defaults
helena@Helena:/lib/firmware/brcm$ 



This is the output I got. It still hasn't worked, but I'm rebooting.

---

### Post by DirtyPC on 2011-06-17
Ahh, you're running ubuntu 10.04. This works for 10.10

Sorry, if you want it fixed asap upgrade to either 10.10 or 11.04

---

### Post by Helenarth on 2011-06-17
Running 9.10, I think I mentioned it. Thank you SO much for all your help, though, I really appreciate it.

---

### Post by DirtyPC on 2011-06-17
No problem, I probably caused more of a headache then helped. 
System>Administration>Update and to update it should be there.
Or burn Cd image to disc

---

### Post by superduperlinuxperson on 2011-06-17
sorrry for replying late, but helenarth, did you try doing the commands again, except remove the --unsupported part. 
thanks

---

### Post by DirtyPC on 2011-06-18
Think the OP has given up and/or upgraded to a later OS.

---

