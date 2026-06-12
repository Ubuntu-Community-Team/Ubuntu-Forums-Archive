---
title: "Intel 6205  wireless not working with Lenovo W520"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by sparhk on 2011-04-25
Loving the new W520... very fast, if only the wireless would work.  Unable to get wireless interface functioning, won't even show up in ifconfig.  I've appended requested wireless information, thanks in advance for any assistance. 


1) Machine Brand and Model (PC/Laptop):
Lenovo W520
Intel Centrino Advanced-N 6205
Note:  Wireless switch on lefthand side enabled,  bluetooth led lights up but wireless does not.

2) Wireless Brand, Model and Wireless Chipset:
$ lspci -nn

03:00.0 Network controller [0280]: Intel Corporation 6000 Series Gen2 [8086:0085] (rev 34)

3 ) check interface:
ifconfig does not show wireless

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

4 ) Check for modules:
$ lsmod
...
iwlagn                215351  0
iwlcore               139688  1 iwlagn
mac80211              269644  2 iwlagn,iwlcore
cfg80211              167809  3 iwlagn,iwlcore,mac80211
...
5) Kernel boot messages
$ dmesg
....
[   13.497936] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.497938] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   13.498058] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.498089] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.498181] iwlagn 0000:03:00.0: Detected 6000 Series 2x2 AGN Gen2a, REV=0xB0
[   13.499187] lp: driver loaded but no devices found
[   13.502642]   alloc irq_desc for 22 on node -1
[   13.502645]   alloc kstat_irqs on node -1
....

6 ) Network configuration
$  sudo lshw -C network
*-network UNCLAIMED
       description: Network controller
       product: 6000 Series Gen2
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d5300000-d5301fff

7 ) Scan for networks:
not relevant as no wireless interface appears

8 ) Ubuntu Version:
Ubuntu 10.10

9 ) Kernel/architecture (including 32 vs. 64 bit):
2.6.35-28-generic x86_64

10 ) Restarting the network:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

Additionally, modinfo shows the following:
$ modinfo iwlagn
filename:       /lib/modules/2.6.35-28-generic/updates/compat-wireless-2.6.36/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6000g2b-4.ucode
firmware:       iwlwifi-6000g2a-4.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     8F7F4C6196599FCA596C837

---

### Post by ivanovnegro on 2011-04-25
Check first if you have a button to activate Wireless on your Lenovo.

---

### Post by sparhk on 2011-04-25
> **ivanovnegro said:**
> Check first if you have a button to activate Wireless on your Lenovo.

There is a switch on the lefthand side of laptop, this is in the on position.  Additionally, there is an fn+F5 key combo that should toggle wireless.  The key combo appears to have no impact.  The wireless switch on the left hand side of laptop appears to turn off bluetooth, but does not light the wireless led (nor does ifconfig show wireless in either position).  If I've missed something, please let me know... would love a simple fix:)

---

### Post by ivanovnegro on 2011-04-25
Ok, now you could test to install additional drivers, System-> Additional drivers or something like this, Im on Kubuntu, so its different. Try to see if you can install some drivers maybe.
Im not the expert for Wireless but maybe this site could also help: [https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)

---

### Post by sparhk on 2011-04-25
> **ivanovnegro said:**
> Ok, now you could test to install additional drivers, System-> Additional drivers or something like this, Im on Kubuntu, so its different. Try to see if you can install some drivers maybe.
Im not the expert for Wireless but maybe this site could also help: [https://help.ubuntu.com/10.10/index.html](https://help.ubuntu.com/10.10/index.html)

Could have sworn that was what iwlwifi provided.  At least that was what the intel driver site led me to believe.  I double checked the drivers offered on [http://intellinuxwireless.org/?n=downloads](http://intellinuxwireless.org/?n=downloads) and was able to confirm that the driver is already present in /lib/firmware and a diff confirmed it was the exact same version.  i.e. I think ubuntu managed to pull down the proper drivers, and that a manual installation was unnecessary.

---

### Post by sparhk on 2011-04-25
I suspect the drivers I have came from running this install

sudo apt-get install linux-backports-modules-wireless-maverick-generic

Should I have used a different set of drivers?

---

### Post by ivanovnegro on 2011-04-25
Why do you have a backports driver?
I have also Intel and it worked out of the box on Ubuntu 10.10, maybe thats the problem.
When you installed the first time do you mean you did not have Wireless and then installed from the backports?

---

### Post by sparhk on 2011-04-25
> **ivanovnegro said:**
> Why do you have a backports driver?
I have also Intel and it worked out of the box on Ubuntu 10.10, maybe thats the problem.
When you installed the first time do you mean you did not have Wireless and then installed from the backports?

With a fresh 10.10 install the wireless drivers did not work.  I have roughly 5 years experience using ubuntu and with the exception of a broadcom card I've had little trouble with wireless cards and ubuntu.  Unfortunately, with the **Intel 6205 and the Lenovo W520 laptop I ran into some difficulties.  After some research I found many suggested installing the backport drivers, so I gave that a try.**

---

### Post by chili555 on 2011-04-25
Please let an old fan of Intel see:```
dmesg | grep iwl
rfkill list all
```Thanks.

---

### Post by sparhk on 2011-04-25
Here you go!

$ dmesg | grep iwl
[   12.545642] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.545644] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.545710] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.545738] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.545820] iwlagn 0000:03:00.0: Detected 6000 Series 2x2 AGN Gen2a, REV=0xB0
[   12.556240] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   12.556255] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.556387] iwlagn 0000:03:00.0: irq 48 for MSI/MSI-X
[   12.570025] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[   12.570029] iwlagn 0000:03:00.0: no suitable firmware found!
[   12.570233] iwlagn 0000:03:00.0: PCI INT A disabled


$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by sparhk on 2011-04-25
BTW in /lib/firmware/ I can see 
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2b-5.ucode

but the firmware requested 'iwlwifi-6000g2a-4.ucode' is not there.

---

### Post by chili555 on 2011-04-25
Indeed. We need to resolve a driver vs. firmware mismatch. First I suggest you *remove* linux-backports-modules-wireless* and then reboot. Run:```
dmesg | grep iwl
```Any improvement?

If not, I'll be swapping my harddrive to get back to Maverick; I'm testing Natty at the moment.

---

### Post by sparhk on 2011-04-25
With the added information chili555 requested am wondering if this issue is related to another thread: 
[http://ubuntuforums.org/showthread.php?p=10705940](http://ubuntuforums.org/showthread.php?p=10705940)

If so... is it really necessary to upgrade to 11.4, this laptop is my dev box and I would prefer to stick to the more stable release if possible.

---

### Post by sparhk on 2011-04-25
Removed and restarted.

$ dmesg | grep iwl

returns nothing and wireless has not begun to work.

---

### Post by chili555 on 2011-04-25
Please try:```
sudo modprobe iwlagn
dmesg | greo iwl
```Thanks.

---

### Post by sparhk on 2011-04-25
> **chili555 said:**
> Please try:```
sudo modprobe iwlagn
dmesg | greo iwl
```Thanks.


$ sudo modprobe iwlagn

returns nothing

$ dmesg | grep iwl
[ 7973.964260] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 7973.964262] iwlagn: Copyright(c) 2003-2010 Intel Corporation

---

### Post by sparhk on 2011-04-26
chili555, since it appears that I now have no drivers installed, which steps do you recommend next?

---

### Post by ivanovnegro on 2011-04-26
Could you try maybe to connect you to the internet with a LAN cable and update your system, maybe after that you could have the drivers working for Wireless. I had such case once with an Ubuntu install.

---

### Post by chili555 on 2011-04-26
Can you open Synaptic and look for and install the compat-wireless package? linux-backports-modules-[COLOR="Red"]compat-wireless[/COLOR]-2.6.36-maverick-generic

---

### Post by sparhk on 2011-04-26
> **ivanovnegro said:**
> Could you try maybe to connect you to the internet with a LAN cable and update your system, maybe after that you could have the drivers working for Wireless. I had such case once with an Ubuntu install.

I tried that last night after chili555's suggestions, unfortunately it did not work.

---

### Post by sparhk on 2011-04-26
> **chili555 said:**
> Can you open Synaptic and look for and install the compat-wireless package? linux-backports-modules-[COLOR=Red]compat-wireless[/COLOR]-2.6.36-maverick-generic

Completed, upon restart wireless was not working.

$ sudo modprobe iwlagn
no results

$ dmesg | grep iwl
[   12.672806] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.672809] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.672880] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.672908] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.672991] iwlagn 0000:03:00.0: Detected 6000 Series 2x2 AGN Gen2a, REV=0xB0
[   12.684670] iwlagn 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   12.685170] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.685315] iwlagn 0000:03:00.0: irq 48 for MSI/MSI-X
[   12.690812] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.
[   12.690965] iwlagn 0000:03:00.0: no suitable firmware found!
[   12.691463] iwlagn 0000:03:00.0: PCI INT A disabled

$ ls /lib/firmware/ | grep iwl*
iwlwifi-1000-3.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2b-5.ucode
iwlwifi-6050-4.ucode
iwlwifi-6050-5.ucode

Seems we have come full circle... any further suggestions?

---

### Post by sparhk on 2011-04-26
Dare I create a link for iwlwifi-6000g2a-4.ucode that points to the newer version of the firmware?  

Should do as this thread suggests and upgrade to the ubuntu 11.4?

[http://ubuntuforums.org/showthread.php?p=10705940](http://ubuntuforums.org/showthread.php?p=10705940)

---

### Post by jawilljr on 2011-04-26
What you could try is downloading [Compat-wireless]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2")

That is the version I am using...it fixed both of my Ralink and Intel wireless cards.

[Here are the instructions]("http://wireless.kernel.org/en/users/Download#Building_and_installing") to build and install it.

Jerry

---

### Post by chili555 on 2011-04-26
You certainly could try compiling the compat package. Note that you will need linux-headers-generic and build-essential. I am not confident that it's an improvement on the package you just installed.

---

### Post by sparhk on 2011-04-26
[jawilljr]("http://ubuntuforums.org/member.php?u=1006445")'s suggestion to download [Compat-wireless]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") and build/install worked.  After following the build/install instructions I had to uninstall the linux-backports-modules-[COLOR=Red]compat-wireless[/COLOR]-2.6.36-maverick-generic using synaptic, and restart.  Wireless is working well, am posting this using the wireless connection.  Thanks for all the help!

---

### Post by jawilljr on 2011-04-26
> **sparhk said:**
> [jawilljr]("http://ubuntuforums.org/member.php?u=1006445")'s suggestion to download [Compat-wireless]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") and build/install worked.  After following the build/install instructions I had to uninstall the linux-backports-modules-[COLOR=Red]compat-wireless[/COLOR]-2.6.36-maverick-generic using synaptic, and restart.  Wireless is working well, am posting this using the wireless connection.  Thanks for all the help!

New it would... IMO if you are using either Ralink or a newer Intel wireless chipset the compat-wireless is the way to go... especially in Maverick.

Glad to help.

Jerry

---

### Post by Elliot Williams on 2011-06-04
> **sparhk said:**
> [jawilljr]("http://ubuntuforums.org/member.php?u=1006445")'s suggestion to download [Compat-wireless]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") and build/install worked.  After following the build/install instructions I had to uninstall the linux-backports-modules-[COLOR=Red]compat-wireless[/COLOR]-2.6.36-maverick-generic using synaptic, and restart.  Wireless is working well, am posting this using the wireless connection.  Thanks for all the help!

More thanks!

Compat-wireless worked for me with kernel 2.6.37 on Natty.

[http://ubuntuforums.org/showthread.php?p=10900847#post10900847](http://ubuntuforums.org/showthread.php?p=10900847#post10900847)

---

### Post by jeffdyke on 2011-06-19
The compat-wireless build also worked for me on Meerkat with a Dell e6520 Intel 6000 Series Gen2

tar xjvf  compat-wireless-2011-03-31.tar.bz2
cd  compat-wireless-2011-03-31
make
sudo make install
shutdown -r now

---

### Post by freehome on 2011-07-20
Hi sparhk,

I have exactly the same wifi card (laptop Dell E5520) and I have problems to make wifi work. Could you please answer a few questions in order to find how to fix it?

I am on the same state as you on comment 16 ([http://ubuntuforums.org/showpost.php?p=10720184&postcount=16](http://ubuntuforums.org/showpost.php?p=10720184&postcount=16)).

$> dmesg | grep iwl
[ 1526.680195] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 1526.680197] iwlagn: Copyright(c) 2003-2009 Intel Corporation

$> ls /lib/firmware/
iwlwifi-1000-3.ucode  iwlwifi-3945-2.ucode  iwlwifi-4965-2.ucode  iwlwifi-5000-2.ucode    iwlwifi-6000-4.ucode     iwlwifi-6000g2b-5.ucode  iwlwifi-6050-5.ucode
iwlwifi-3945-1.ucode  iwlwifi-4965-1.ucode  iwlwifi-5000-1.ucode  iwlwifi-5150-2.ucode    iwlwifi-6000g2a-5.ucode  iwlwifi-6050-4.ucode

I have downloaded and install compat-wireless-2.6.32.16 but no success.

I cannot understand how from comment 16 you go to comment 21 ([http://ubuntuforums.org/showpost.php?p=10722508&postcount=21](http://ubuntuforums.org/showpost.php?p=10722508&postcount=21)), where when you try "modprobe iwlagn" you get "request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.". I guess  this is what I missing. What actions did you did to get this error message??

When I do "modprobe iwlagn" I get these messages on /var/log/messages:
Jul 20 19:04:50 icomadd kernel: [ 1526.623884] cfg80211: Using static regulatory domain info
Jul 20 19:04:50 icomadd kernel: [ 1526.623887] cfg80211: Regulatory domain: US
Jul 20 19:04:50 icomadd kernel: [ 1526.623888]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 20 19:04:50 icomadd kernel: [ 1526.623890]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623893]  (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623894]  (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623896]  (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623898]  (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623900]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
Jul 20 19:04:50 icomadd kernel: [ 1526.623906] cfg80211: Calling CRDA for country: US
Jul 20 19:04:50 icomadd kernel: [ 1526.680195] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Jul 20 19:04:50 icomadd kernel: [ 1526.680197] iwlagn: Copyright(c) 2003-2009 Intel Corporation


Thanks in advance.

---

### Post by sparhk on 2011-07-20
jawilljir's post 23 was the turning point for me.  Until I tried those steps nothing worked.  I'm still using 10.10, and recently successfully reused those same steps when another upgrade broke wireless.

---

### Post by freehome on 2011-07-20
I see a big difference between posts 16 and 21. On post 16 you get from dmesg exactly what I get now. But on post 21 you get an error message which says "[   12.690812] iwlagn 0000:03:00.0: request for firmware file 'iwlwifi-6000g2a-4.ucode' failed.". 
What did you change and got this error message?
 
After you got this error message, which describes you that you do not have a file, then you go to post 23 and download a specific version of Compat-wireless (which was not the latest at the time of post 23) and install it. After that your wifi is working.

Do I have to download and install the specific version of Compat-wireless ([http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2)) or can I install the latest?

My kernel is 2.6.32.

Sorry for the trouble and thanks for any info.

---

### Post by RadiantPhoenix on 2011-08-03
Compiling and installing that specific version seems to have worked for me, I haven't tried any others.

---

### Post by pederbruusgaard on 2011-09-03
> **sparhk said:**
> [jawilljr]("http://ubuntuforums.org/member.php?u=1006445")'s suggestion to download [Compat-wireless]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2011/03/compat-wireless-2011-03-31.tar.bz2") and build/install worked.  After following the build/install instructions I had to uninstall the linux-backports-modules-[COLOR=Red]compat-wireless[/COLOR]-2.6.36-maverick-generic using synaptic, and restart.  Wireless is working well, am posting this using the wireless connection.  Thanks for all the help!

Hi,
I came across this thread now as I have a very similar issue with my Intel 6205 wireless card. It was working the first couple of days on my brand new x220, but now it seems the card is not even recognized anymore. I don't exactly know when it stopped, because I'm mostly using wired internet, but it wasn't for long.

I was very glad to see that the issue could be resolved, however, I'm really completely new to Ubuntu (11.04), so I had some trouble installing the Compat-wireless. I downloaded the file from the link, and extracted the files to a folder, but from there I don't know what to do.

I'm really sorry for this noob-ish question, but if someone could help me out with this one I'd be very thankful!

---

### Post by SN8P on 2012-01-17
look for an kernel upgrade, if so the driver is probably not copied to the new location so just try a modprobe again or redo the installation process.

---

### Post by chefebe on 2012-08-20
Followed the steps to download, make, install compat-wireless and it fixed my wireless on T420.  Thanks!

---

