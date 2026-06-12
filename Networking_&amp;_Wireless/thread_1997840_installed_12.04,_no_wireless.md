---
title: "installed 12.04, no wireless"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by thunderhouse on 2012-06-05
I installed unbuntu 12.04 and have no wireless. I am currently plugged into an ethernet cable but need wireless. I am a fairly new user and do not know how to do many things, so I apologize ahead of time. I have tried reading what other people did to solve this problem but was unable to get anywhere. 

Both the installer package for b43 firmware and broadband STA wireless driver appear in my additional drives. Both are unable to be activated saying:  /var/log/jockey.log

To someones suggestion, I typed the following into a terminal:  lspci -nn | grep 0208 nothing happened. Before I tried downloading a package onto a flash drive and putting it on my desktop but could not extract anthing off my flashdrive due to a mounting error.  I tried to type something else earlier and my terminal kept asking for a password to which I was unable to type anything.  Ahh! 

Any help would be wonderful.  Thanks in advance.

---

### Post by chili555 on 2012-06-05
> typed the following into a terminal: lspci -nn | grep 0208 nothing happened. They should have suggested:```
lspci -nn | grep [COLOR="Red"]0280[/COLOR]
```Please run and post it.

---

### Post by thunderhouse on 2012-06-05
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
tina@tina-Inspiron-1564:~$

---

### Post by chili555 on 2012-06-05
You have the same card and need the same fix: [http://ubuntuforums.org/showthread.php?t=1969761&highlight=4315](http://ubuntuforums.org/showthread.php?t=1969761&highlight=4315)

---

### Post by thunderhouse on 2012-06-05
i must be doing something wrong : (  the terminal is asking for a password.  do i type in the first line and hit enter and then the second line? or altogether?

---

### Post by chili555 on 2012-06-05
I don't think you have a password with two lines. Just type in the password and press Enter. For security reasons, the password is not echoed back; not even ****. Just enter it.

---

### Post by thunderhouse on 2012-06-05
my apologies, i was referring to the code not password. Got the password part to work and then the terminal did its thing.  Should I be able to access wireless right away? 
If needed...here is the entire terminal. 

tina@tina-Inspiron-1564:~$ ls -nn | grep 0280
tina@tina-Inspiron-1564:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
tina@tina-Inspiron-1564:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for tina: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 246 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 172681 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
sudo modprobe wl
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 2.6.35-32-generic and 3.2.0-23-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.2.0-23-generic-pae
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
tina@tina-Inspiron-1564:~$ 

thanks

---

### Post by chili555 on 2012-06-05
> tina@tina-Inspiron-1564:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for tina:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 246 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 172681 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
[COLOR="Red"]sudo modprobe wl[/COLOR]
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...You needed to wait until the first command was done before you started the second. Please do:```
sudo modprobe wl
```Any errors or warnings? Can you click the Network Manager icon, see networks and connect?

---

### Post by thunderhouse on 2012-06-05
> **chili555 said:**
> You needed to wait until the first command was done before you started the second. Please do:```
sudo modprobe wl
```Any errors or warnings? Can you click the Network Manager icon, see networks and connect?

FATAL: Could not load /lib/modules/2.6.35-32-generic/modules.dep: No such file or directory

icon at top of screen still only shows the wired connection option.

---

### Post by thunderhouse on 2012-06-05
should I redo the first steps? 

	sudo apt-get install --reinstall bcmwl-kernel-source sudo modprobe wl

---

### Post by chili555 on 2012-06-05
> Loading new bcmwl-5.100.82.38+bdcom DKMS files...
[COLOR="Red"]Building for 2.6.35-32-generic[/COLOR] and [COLOR="Red"]3.2.0-23-generic-pae[/COLOR]
Building for architecture i686
[COLOR="Red"]Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.[/COLOR]
Building initial module for 3.2.0-23-generic-pae> FATAL: Could not load /lib/modules/[COLOR="Red"]2.6.35-32-generic[/COLOR]/modules.dep: No such file or directory
I thought you wanted it for 12.04. You seem to be running 10.10 or some such. :confused:

---

### Post by chili555 on 2012-06-05
> **thunderhouse said:**
> should I redo the first steps? 

	sudo apt-get install --reinstall bcmwl-kernel-source sudo modprobe wlPlease see my next post.

---

### Post by thunderhouse on 2012-06-05
hmm. I had 10.10, tried to upgrade to 12.04, failed. So then I installed 12.04 off a liveCD. When i start my computer, it says 12.04 and the interface looks like 12.04 : /:confused:

---

### Post by chili555 on 2012-06-06
At the GRUB menu, do you have the option to boot into different kernels? Can you please select 3.2.0-23-generic-pae? I suspect your wireless will work perfectly.

---

### Post by thunderhouse on 2012-06-06
In the grub menu i only have the  option to run in 2.6.35-32-generic

---

### Post by thunderhouse on 2012-06-06
Or 2.6.35-22

---

### Post by thunderhouse on 2012-06-22
hi [chili555]("http://ubuntuforums.org/member.php?u=35909")... I was moving the past two weeks and not able to work on my computer. Are you, or someone else out there : ) , still able to help?

wireless router (as well as mouse touchpad which is not a concern of mine now) is not working. Trying to figure out what to do! 

Thank you

---

### Post by chili555 on 2012-06-22
> **thunderhouse said:**
> hi [chili555]("http://ubuntuforums.org/member.php?u=35909")... I was moving the past two weeks and not able to work on my computer. Are you, or someone else out there : ) , still able to help?

wireless router (as well as mouse touchpad which is not a concern of mine now) is not working. Trying to figure out what to do! 

Thank youAlways willing to help. Please refer to post #14. Does it help?

---

### Post by thunderhouse on 2012-06-22
see post #15 and #16, same options. Unless I went into the grub menu wrong...  I held down the shift key to access menu

---

### Post by chili555 on 2012-06-22
> **thunderhouse said:**
> see post #15 and #16, same options. Unless I went into the grub menu wrong...  I held down the shift key to access menuThen we are wondering why we see:> Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building for 2.6.35-32-generic and 3.2.0-23-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for [COLOR="Red"]3.2.0-23-generic-pae[/COLOR] You might try:```
sudo apt-get install --reinstall linux-image-3.2.0-23-generic-pae
sudo apt-get install --reinstall linux-headers-generic-pae
```If all goes well, reboot and select 3.2.0-23 which ought to be at the top of the list. Then do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```

---

### Post by thunderhouse on 2012-06-22
> **chili555 said:**
> then we are wondering why we see:you might try:```
sudo apt-get install --reinstall linux-image-3.2.0-23-generic-pae
sudo apt-get install --reinstall linux-headers-generic-pae
```
 
 i did the above step and all seems to be well! The touch pad and wireless router is working!!! I did not enter the grub menu, just let the computer book automatically. Do i still need to do the following step?
 
If all goes well, reboot and select 3.2.0-23 which ought to be at the top of the list. Then do:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
 
thank you!

---

