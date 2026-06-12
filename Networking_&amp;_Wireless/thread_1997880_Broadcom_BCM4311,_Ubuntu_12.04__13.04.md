---
title: "Broadcom BCM4311, Ubuntu 12.04 / 13.04"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by Josh Rabbitt on 2012-06-05
hi all i just recently installed ubuntu 12.04 and since install i havent been able to get wireless internet to work. when i plug in the ethernet cable it works i just dont have wireless. i have been searching around and have run out of things to do. here is the terminal i was just doing: 


dell@dell-Inspiron-1501:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
dell@dell-Inspiron-1501:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dell@dell-Inspiron-1501:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
dell@dell-Inspiron-1501:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for dell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 14 not upgraded.
Need to get 0 B/1,202 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  bcmwl-kernel-source
Install these packages without verification [y/N]? y
(Reading database ... 169051 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu6.1 (using .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6.1) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

depmod...........

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
dell@dell-Inspiron-1501:~$ sudo modprobe wl

---

### Post by chili555 on 2012-06-05
Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

---

### Post by Josh Rabbitt on 2012-06-05
here is the terminal: 
dell@dell-Inspiron-1501:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for dell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
After this operation, 3,252 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169050 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
dell@dell-Inspiron-1501:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-firmware-nonfree
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 3,947 kB of archives.
After this operation, 8,962 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-firmware-nonfree
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse linux-firmware-nonfree all 1.11ubuntu1 [3,947 kB]
Fetched 3,947 kB in 7s (535 kB/s)                                              
Selecting previously unselected package linux-firmware-nonfree.
(Reading database ... 169001 files and directories currently installed.)
Unpacking linux-firmware-nonfree (from .../linux-firmware-nonfree_1.11ubuntu1_all.deb) ...
Setting up linux-firmware-nonfree (1.11ubuntu1) ...


now i just need to reboot

---

### Post by Josh Rabbitt on 2012-06-05
i now have wireless! Thank you very very much!!

---

### Post by chili555 on 2012-06-05
Would you please use thread tools at the top to mark Solved?

For the searchers: This is the prescribed fix for pci.id [COLOR="Red"]14e4:4311[/COLOR]. If this is not your device, keep searching or start a new thread.

---

### Post by Josh Rabbitt on 2012-06-05
Marked as solved. Thank you again

---

### Post by mmediaman on 2012-09-22
@[chili555]("http://ubuntuforums.org/member.php?u=35909")

I re-registered for the forum just to tell you:

YOU ARE A BOSS!!!

I can't tell you how many other BS posts I read elsewhere on the web about how to solve this issue and your solution does it in 2 simple commands.  I was about to go out and buy a USB Wireless Adapter at Fry's tomorrow.

YOU ARE A BOSS!!!

THANK YOU.


p.s. thanks to  Josh the OP of the thread for starting it :p

---

### Post by chili555 on 2012-09-22
> **mmediaman said:**
> @[chili555]("http://ubuntuforums.org/member.php?u=35909")

I re-registered for the forum just to tell you:

YOU ARE A BOSS!!!

I can't tell you how many other BS posts I read elsewhere on the web about how to solve this issue and your solution does it in 2 simple commands.  I was about to go out and buy a USB Wireless Adapter at Fry's tomorrow.

YOU ARE A BOSS!!!

THANK YOU.


p.s. thanks to  Josh the OP of the thread for starting it :pThank you for your kind words. I'm glad it's working.

---

### Post by 1John on 2012-09-23
:DJust wanted to add my thanks - have spent 4 days trying to get Dell 1501 wireless to work on 12.04. Now everything is great. Thanks again.

---

### Post by 666ABEL999 on 2012-09-23
well my problem is I have a HP 435 notebook, and insert the live cd of Ubuntu 12.04 the wireless would not start and stop good not much ball and when you install Ubuntu 12.04 I realized I did not catch anything and went to investigate until I saw that said the wireless network is turned off by switch treasury do not know how but I need the wifi for my computer in advance thanks to help me
THANKS.

---

### Post by RISHIKESHGAWADE on 2012-09-25
Thank You very very much. I was struggling for two days and then search resulted in your post!!! it works! thanks a lot once again

---

### Post by macks1 on 2012-11-09
I cannot thank you enough for this, I nearly reinstalled my OS until I saw this.

I am jumping for joy!     
:KS:KS:KS:KS:KS

---

### Post by rogersaavedra on 2012-11-14
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

I am new to Linux.  Installed Ubuntu 12.04 on a Dell Latitude D430.   After installing, I was suggested to wire connect the machine to get  Internet, which I did, updated the system, and it works wired.  Wireless  is what's killing me. 

In systems settings, under additional drivers, the driver for the machine is there and active.

I tried 2 two commands: 
sudo apt-get remove --purge bcmwl-kernel-source sudo apt-get install linux-firmware-nonfree



Got the same terminal response as Josh Rabbit, rebooted, I still don't get signal at the hot spot.

One question though, Do I soppose to get a message saying "Networks Available"? like in Windows?

---

### Post by rogersaavedra on 2012-11-14
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.
New to Linux, installed Ubuntu 12.04 on a Latitude D430.  Wired connection works, that is how I updated the system.  wireless is whats killing me.  the driver is there, in additional drivers and active.   I tried this 2 commands, got the same results as Josh Rabbit, rebooted, still don't have signal at a hot spot. It should detect signal as in windows correct?  What do I do next. Heeelp!

---

### Post by chili555 on 2012-11-14
> **rogersaavedra said:**
> New to Linux, installed Ubuntu 12.04 on a Latitude D430.  Wired connection works, that is how I updated the system.  wireless is whats killing me.  the driver is there, in additional drivers and active.   I tried this 2 commands, got the same results as Josh Rabbit, rebooted, still don't have signal at a hot spot. It should detect signal as in windows correct?  What do I do next. Heeelp!Do you have the *exact* same device as the original poster? > Broadcom Corporation BCM4311 802.11b/g WLAN [[COLOR="Red"]14e4:4311[/COLOR]] Please check:```
lspci -nn | grep 0280
```Please post:```
rfkill list all
```

---

### Post by ssk_the_gr8 on 2012-11-20
@chili555

thank you.

---

### Post by pressi on 2013-01-16
@chili555

Thanks.

---

### Post by jackofall1232 on 2013-02-22
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.
Thank you Chili you are the $h!t.. this works great in 12.10 fixed my wifi great!!

I added this to it and my internet is flying now I am getting 30Mbs/6Mbs over wifi:

Disables Ipv6:
```
sudo gedit /etc/modprobe.d/bad_list
```
```
alias net-pf-10 off
```

This adjusts TCP window size:


```
sudo gedit /etc/sysctl.conf
```

If you choose a windows packet size that is too big, you will notice  slower broadband performance (524288 works for me). If you notice a slow  down, then reduce your window size.
 The largest size you can use is 65536, however these are the three settings that seem to work best:
524288
 262144
 131072
 Which are all multiples of 1024 (or 1K).
 Now add the following to the end of the file:
[INDENT] net.core.rmem_default = 524288
 net.core.rmem_max = 524288
 net.core.wmem_default = 524288
 net.core.wmem_max = 524288
 net.ipv4.tcp_wmem = 4096 87380 524288
 net.ipv4.tcp_rmem = 4096 87380 524288
 net.ipv4.tcp_mem = 524288 524288 524288
 net.ipv4.tcp_rfc1337 = 1
 net.ipv4.ip_no_pmtu_disc = 0
 net.ipv4.tcp_sack = 1
 net.ipv4.tcp_fack = 1
 net.ipv4.tcp_window_scaling = 1
 net.ipv4.tcp_timestamps = 1
 net.ipv4.tcp_ecn = 0
 net.ipv4.route.flush = 1


Now save:)

[/INDENT]After adding these line you do not need to reboot, instead just reset the file by issuing this command:
[INDENT] sudo sysctl -p
[/INDENT]After  completing this, you should notice improved web surfing speed. If not,  remember to go back and adjust your TCP window size and try again.

---

### Post by chili555 on 2013-02-22
> sudo gedit /etc/modprobe.d/bad_listEverything in modprobe.d needs to be a conf file, so this will work better as:```
sudo gedit /etc/modprobe.d/bad_list[COLOR="Red"].conf[/COLOR]
```Thanks for your kind (??) comments.

---

### Post by 16jedavis on 2013-03-09
i also have problems but on a inspirion 1545 and my rfkill list says
user@user-Inspiron-1545:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

what do i do

---

### Post by chili555 on 2013-03-09
> **16jedavis said:**
> i also have problems but on a inspirion 1545 and my rfkill list says
user@user-Inspiron-1545:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

what do i doFind out if you have dell-laptop or dell-wmi loaded:```
lsmod
```Whichever on it is, unload it temporarily:```
sudo modprobe -rf dell-laptop [COLOR="#FF0000"]<---or -wmi[/COLOR]
sudo rfkill unblock all
```Does your wireless srping to life? If so, we'll make it permanent.

---

### Post by chaitanya2106 on 2013-03-11
> **chili555 said:**
> Find out if you have dell-laptop or dell-wmi loaded:```
lsmod
```Whichever on it is, unload it temporarily:```
sudo modprobe -rf dell-laptop [COLOR=#FF0000]<---or -wmi[/COLOR]
sudo rfkill unblock all
```Does your wireless srping to life? If so, we'll make it permanent.

hey chili555 , I would be highly obliged if you throw light on my problem which is the same as of other members here i.e., can't get my wireless to work.

I ran some commands that you listed here & they gave me the following results:

[B]chaitanya@CHAITANYA-PC:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
chaitanya@CHAITANYA-PC:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
chaitanya@CHAITANYA-PC:~$ [/B]

---

### Post by chili555 on 2013-03-11
> **chaitanya2106 said:**
> hey chili555 , I would be highly obliged if you throw light on my problem which is the same as of other members here i.e., can't get my wireless to work.

I ran some commands that you listed here & they gave me the following results:

[B]chaitanya@CHAITANYA-PC:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
chaitanya@CHAITANYA-PC:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
chaitanya@CHAITANYA-PC:~$ [/B]This device requires firmware and there is a bit of controversy about the best way to do it. You will be our test pilot! Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Any improvement?

---

### Post by chaitanya2106 on 2013-03-11
> **chili555 said:**
> This device requires firmware and there is a bit of controversy about the best way to do it. You will be our test pilot! Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Any improvement?

Yes, I do have a wired ehternet connection. I ran the commands & here's the result:

chaitanya@CHAITANYA-PC:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for chaitanya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn linux-headers-3.5.0-23
  language-pack-zh-hans-base firefox-locale-zh-hans
  linux-headers-3.5.0-23-generic language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chaitanya@CHAITANYA-PC:~$ sudo modprobe -r b43 && sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.




It's been more than 15 minutes & the cursor is stuck there in the WARNING line.

---

### Post by chili555 on 2013-03-12
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.This is symptomatic of a failed ndiswrapper installation. Let's check a few things:```
ndiswrapper -l
ls /etc/ndiswrapper
cat /etc/modprobe.d/blacklist 
```Thanks.

---

### Post by chaitanya2106 on 2013-03-13
> **chili555 said:**
> This is symptomatic of a failed ndiswrapper installation. Let's check a few things:```
ndiswrapper -l
ls /etc/ndiswrapper
cat /etc/modprobe.d/blacklist 
```Thanks.

hey thanx again for your reply, sorry for taking a bit time. Here are the results:

chaitanya@CHAITANYA-PC:~$ ndiswrapper -l
chaitanya@CHAITANYA-PC:~$ ls /etc/ndiswrapper
chaitanya@CHAITANYA-PC:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xx
chaitanya@CHAITANYA-PC:~$

---

### Post by chili555 on 2013-03-13
> chaitanya@CHAITANYA-PC:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xxThere is no such module:> chili@Think410:~$ modinfo bcm43xx
ERROR: modinfo: could not find module bcm43xxSo you may as well remove the ineffective file:```
sudo rm /etc/modprobe.d/blacklist
```Now let's unload and reload the driver and see if there are any informative messages in the log:```
sudo modprobe -r b43 && sudo modprobe b43
dmesg | grep b43
```Either your wireless will be working or dmesg will tell us why not.

EDIT: I see you are getting excellent help from my friend Hadaka. Please continue with him.

---

### Post by chaitanya2106 on 2013-03-13
> **chili555 said:**
> There is no such module:So you may as well remove the ineffective file:```
sudo rm /etc/modprobe.d/blacklist
```Now let's unload and reload the driver and see if there are any informative messages in the log:```
sudo modprobe -r b43 && sudo modprobe b43
dmesg | grep b43
```Either your wireless will be working or dmesg will tell us why not.

EDIT: I see you are getting excellent help from my friend Hadaka. Please continue with him.

[B]
chaitanya@CHAITANYA-PC:~$ sudo rm /etc/modprobe.d/blacklist
[sudo] password for chaitanya: 
chaitanya@CHAITANYA-PC:~$ sudo modprobe -r b43 && sudo modprobe b43

[/B]

It's stuck there.

---

### Post by chili555 on 2013-03-13
Hadaka is your best resource.

---

### Post by 16jedavis on 2013-03-16
still no wireless

---

### Post by mörgæs on 2013-03-20
Confirming that 
```
sudo apt-get install linux-firmware-nonfree
```
followed by a reboot also works for Lubuntu 13.04 (beta).

---

### Post by chili555 on 2013-03-20
> also works for Lubuntu 13.04 (beta). Eggs cell ant! Thanks!

---

### Post by nanog on 2013-04-01
for me...the binary driver works perfectly with 4311 in 12.10 and 13.04. 
i also find firmware+b43  to be slow and erratic.

```
sudo apt-get install dkms #assuming you do not already have dkms installed
``` 
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

---

### Post by doweeez on 2013-04-07
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

Thank you. This saved my ass

---

### Post by kornelix on 2013-04-07
Thanks. That did the trick for me too.

---

### Post by hthn on 2013-04-26
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.


Thank you! I've been struggling with this for the past two days straight with no luck. This fixed my problem!

My controller:
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```


:D

---

### Post by dandroid13 on 2013-04-26
This makes my bluetooth mouse lag, can I fix it? I'm using Raring with bcmwl from Quantal.

---

### Post by porcupine75 on 2013-04-27
Hey hey! Converted my DEL 1545 Inspiron to Ubuntu 12.04 most recently.
AND THIS THREAD ROCKS. made my wireless work... 
Thanks a Million!

---

### Post by jackofall1232 on 2013-04-30
Chili I have to say you are the man. Can you roll that big ass brain of yours up and mail it to me? I have learned so much from reading your posts. Because of you , I am a nut for Linux now. I used to be scared of it.. Now I look at it like it is not going to beat me. Thanks to you and all the helpful souls on this website!! Thanks a million. please keep coming back.

---

### Post by jackofall1232 on 2013-04-30
> **chili555 said:**
> Eggs cell ant! Thanks!


P.S. works for Mint 14 too  .. Thanks a gain you rock!!

---

### Post by chili555 on 2013-04-30
Thank you all for your very kind comments. You've made my day! I am very gratified when a new user has his/her wireless working and begins to really appreciate Ubuntu Linux.

---

### Post by yeyupa on 2013-05-03
Really really thanks!

---

### Post by sdowney717 on 2013-05-07
> **dandroid13 said:**
> This makes my bluetooth mouse lag, can I fix it? I'm using Raring with bcmwl from Quantal.

is it possible for you to switch channels on either the wireless or the bluetooth ?
maybe there is an overlapping conflict

---

### Post by Implactus on 2013-05-08
Awesome! Worked after I managed to sort out my poor terminal inputs.:lolflag:

---

### Post by vitosmo on 2013-05-12
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

This solved my problem after updating to 13.04 on my Lenovo Thinkpad. Hint: to get to the net, I connected via Ethernet cable to my Fritz!box

---

### Post by Monikandrew on 2013-05-15
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.


THANK YOU SOO MUCH, IT WORKED PERFECTLY...:p:D

---

### Post by StephenWin on 2013-05-16
I have a similar Issue, (Non-working WIFI on a Dell Inspiron 1501 on a new install of Ubuntu) but thought it not proper to piggy back onto another's message thread. So I have started a new thread for my issue here:[SIZE=2][Dell Inspiron 1501 + Ubuntu 13.04 = WIFI doesn't work]("http://ubuntuforums.org/showthread.php?t=2145768")[/SIZE]. If any of you can go there and help me I'd appreciate it.
Best Wishes,
Stephen

---

### Post by tiffya on 2013-05-28
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

Amazing! I have fought so much with trying to get this to work and all I needed to do was this? :confused: The wireless is now working great on my Inspiron 1501 with Linux Mint 14. Thank you so much!

---

### Post by cconner94 on 2013-05-30
I have a Dell Inspiron 1420 with the exact same wireless card as OP.  I've tried:
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
and rebooted, but I still get no wireless signal and no indication that my wireless card is active. 

Any help would be greatly, greatly appreciated!

---

### Post by chili555 on 2013-05-31
> **cconner94 said:**
> I have a Dell Inspiron 1420 with the exact same wireless card as OP.  I've tried:
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
and rebooted, but I still get no wireless signal and no indication that my wireless card is active. 

Any help would be greatly, greatly appreciated!Please show us:```
lspci -nn -d 14e4:
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by cconner94 on 2013-05-31
I am out of the home office for a few hours, but I will post the results ASAP.  Thank you, chili555!

---

### Post by cconner94 on 2013-05-31
> **chili555 said:**
> Please show us:```
lspci -nn -d 14e4:
dmesg | grep b43
rfkill list all
```Thanks.

$ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
$ dmesg | grep b43
$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

That's all that came back.

---

### Post by blakviper on 2013-06-03
you guys rocked, I spent most of my day yesterday searching for an answer, with you in less than 10 minutes it was working. Thanks a lot guys!!!!!!!!!!!

---

### Post by chili555 on 2013-06-03
> **cconner94 said:**
> $ lspci -nn -d 14e4:
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
$ dmesg | grep b43
$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

That's all that came back.Let's poke it a little:```
sudo modprobe b43
dmesg | grep b43
dmesg | grep 0c:00
```Thanks.

---

### Post by NewbieX on 2013-06-13
Thank you chilli555!!!!!


This worked for a Latitude D620

[COLOR=#000000]Code:[TABLE="width: 500"]
[TR]
[TD]sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree[/TD]
[/TR]
[/TABLE]
[FONT=Verdana]Reboot

Wireless yay!


[/FONT][/COLOR]

---

### Post by aciang2 on 2013-08-03
> **chili555 said:**
> Let's poke it a little:```
sudo modprobe b43
dmesg | grep b43
dmesg | grep 0c:00
```Thanks.

i already try all your comment
but i still cant see any wireless yet , help me plss!!

---

### Post by chili555 on 2013-08-03
> **aciang2 said:**
> i already try all your comment
but i still cant see any wireless yet , help me plss!!Please confirm your exact device:```
lspci -nn | grep 0280
```Thanks.

---

### Post by rebrown2 on 2013-08-09
Hi
I have a slightly different - if not weird - problem in helping out a mate with an Acer Aspire 5720 with a BCM4311 wireless device. The b43 module loads ok from either a basic install or using "apt-get install linux-firmware-nonfree" and it connects ok with a couple of wireless routers but will not complete a login with a ZTE MF66 broadband modem. It recognises the MF66 and attempts to connect but fails every time. Before you ask, the connection to the MF66 has been separately verified.
It seems like there is a compatibility issue between the device driver and the MF66 giving some sort of handshake issue.
No joy from dmesg.
Any clues for this one? Just about to revert to a usb device.

---

### Post by mike16 on 2013-08-10
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.


Hi Chili555,

That's impressive and simple to implement.  But will it work for a similar problem on my new Toshiba Sat Pro C850 as well?  

Or, do I need a slightly different (but similar) work around?

Please help.

Mike

---

### Post by chili555 on 2013-08-10
> **mike16 said:**
> Hi Chili555,

That's impressive and simple to implement.  But will it work for a similar problem on my new Toshiba Sat Pro C850 as well?  

Or, do I need a slightly different (but similar) work around?

Please help.

MikeDoes your C850 have the exact, *exact* same device?```
lspci -nn | grep 0280
```Is it 14e4:4311? If so, then yes, indeed. If not, post the result in a new thread and I'll be happy to help.

---

### Post by mike16 on 2013-08-11
I see.  No it's different. 

I'll start a new thread.

Thanks

---

### Post by mike16 on 2013-08-13
@Chili555,  Ive posted this problem in a new thread.  Do you think you might be able to help please?  Im struggling big time.

[http://ubuntuforums.org/showthread.php?t=2166788&p=12755326&posted=1#post12755326](http://ubuntuforums.org/showthread.php?t=2166788&p=12755326&posted=1#post12755326) 

Thanks.

---

### Post by tneiva on 2013-08-13
A weird identification issue. I have here an HP Pavillion dv6149ea with a Broadcom 4311 (at least it says that on the chip:)) and freshly installed Ubuntu 13.04
lspci gives > [COLOR=#333333][FONT=UbuntuMono]Broadcom Corporation **BCM4311** 802.11a/b/g [14e4:**4312**] (rev 01)[/FONT][/COLOR]

your solution worked, with a twist, I had no internet connection!
So I downloaded the .deb package from [http://security.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb)
and installed it with > dpkg -i linux-firmware-nonfree_1.14_all.deb 
reboot and it's working!

---

### Post by greengeek2 on 2014-03-01
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

Please help. I keep hitting a brick wall. I feel like I'm going in circles. :(

Tried: 
sudo-apt-get remove --purge bcmwl-kernel-source

Response: 
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

Tried: lspci -nn | grep 0280
Response: 05:00.0 Network Controller [0280]: Broadcom Corporation BCM4311 802.11 b/g WLAN [1434:4311] (rev 01)

Tried (can't recall if any spaces needed between numbers): lspci -nn | egrep '0200|0280'
Response: 
05:00.0 Network Controller [0280]: Broadcom Corporation BCM4311 802.11 b/g WLAN [1434:4311] (rev 01)
08:00.0 Ethernet Controller [0200]: Broadcom Corporation BCM 4401-BO 100Base-TX [1434:12oc] (rev 02)

Tried: lsmod
Response (compacted answer): 
sparse-keymap 13659 1 dell_wmi
wmi 18745 1 dell_wmi
dcdbas 14099 1 dell_laptop

Background:
1. Dell Inspiron 1501 with Vista Basics*
2. Installed Ubuntu 12.04 LTS* (no more Microsoft...HURRAY!). I get the grey screen of death. Do not have Vista CD to re-install and start over.
3. The only way to get into terminal is to F12 enter and tab down to recovery and get into root.
4. Tried with ethernet cable and without. 
5. Sometimes I can get to Ubuntu desktop but then denied internet access. Says Firefox cannot access server.

*I'm not the owner.
**Will install Lubuntu, read that this OS is better for the Dell Inspiron Series

Thank you in advance.

p.s. I am new to linux/ubuntu.

---

### Post by chili555 on 2014-03-01
> sudo-apt-get remove --purge bcmwl-kernel-sourceI hope you meant and tried:```
sudo  apt-get remove --purge bcmwl-kernel-source
```If not, please try again and tell us what happens.

---

### Post by greengeek2 on 2014-03-01
> **chili555 said:**
> I hope you meant and tried:```
sudo  apt-get remove --purge bcmwl-kernel-source
```If not, please try again and tell us what happens.

Big OOPS! Yes, I tried:

sudo apt-get remove --purge bcmwl-kernel-source

Forgot to mention that the VERY first thing I tried (a week ago) was pppoe.conf and the response was: 

No interface found. Sorry, no working ethernet card could be found. 

Thus starting my week of searching, trying, hitting brick walls and going in circles.

---

### Post by chili555 on 2014-03-02
So if the first step is done, let's check the result and go on to the second step:```
lsmod | grep -e wl -e b4
```Ideally, we see wl not loaded and b43 and b44 are loaded. If that is correct, connect the ethernet and try to connect. Can you?

Is part of the problem PPPOE? Can you let Network Manager handle those details? [http://help.ubuntu.ru/_media/manual/network-manager/nm-edit-dsl.png](http://help.ubuntu.ru/_media/manual/network-manager/nm-edit-dsl.png) In my own situation, it is far easier to handle the user/password authentication in the router. Thereafter, the connected computers need no special configuration. [http://www.networkadmintraining.com/wp-content/uploads/2012/04/linksys2.jpg](http://www.networkadmintraining.com/wp-content/uploads/2012/04/linksys2.jpg)

Once you get connected, install the firmware for the wireless:```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by greengeek2 on 2014-03-02
```
lsmod | grep -e wl -e b4
```

Tried: 
lsmod | grep -e wl -e b4

Response:
wl               3032548 1
cfg80211       181041  1 wl
lib80211          14041 1 wl

Tried:
sudo apt-get install linux-firmware-nonfree

Response: 
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

Questions: 
How do I get into Network Manager via grub/root to handle pppoe? 
Do I have to connect DIRECTLY INTO the router with an ethernet cable?

Thank you for all of your help and patience!

Scratch question 1. I am able to get to ubuntu desktop, saw the "fan" icon on top menu bar and found Network Manager. HOWEVER, how do I find my "connection name"? I have ATT wireless/uverse

---

### Post by chili555 on 2014-03-02
> wl 3032548 1
cfg80211 181041 1 wl
lib80211 14041 1 wl
So you have *still* not removed the incorrect driver???```
sudo  apt-get remove --purge bcmwl-kernel-source
```> Not using locking for read only lock file /var/lib/dpkg/lockPlease try deleting the lock file i.e

```
sudo rm /var/lib/dpkg/lock
```

and then run

```
sudo dpkg --reconfigure -a

```

---

### Post by greengeek2 on 2014-03-02
Tried:
sudo  apt-get remove --purge bcmwl-kernel-source

Last line:
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

With NO blinking cursor underneath. Is cursor stuck? Normal?  Don't want to proceed with next steps, if this is not normal.

THX!

---

### Post by chili555 on 2014-03-02
> **greengeek2 said:**
> Tried:
sudo  apt-get remove --purge bcmwl-kernel-source

Last line:
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic

With NO blinking cursor underneath. Is cursor stuck? Normal?  Don't want to proceed with next steps, if this is not normal.

THX!I would Ctrl+c out of it and try the next steps. Then go back and try again:```
sudo  apt-get remove --purge bcmwl-kernel-source
```You have a very unhappy system there!

I think we need to get the right drivers working correctly before we proceed to PPPOE...or is it PPPPPPPPPPPPPPPPPPPPPOE?

---

### Post by greengeek2 on 2014-03-02
Tried:
sudo dpkg --reconfigure -a

Response:
(first line) dpkg: error: unknown option --reconfigure

(second line) type dpkg --help.......
(sixth line) Options marked 
[*] produce alot of output - pipe it through 'less' or 'more' !

BTW, when you said my system is very unhappy, were you referring to the laptop or me? LOL!

---

### Post by chili555 on 2014-03-02
Oops! Sorry about that. Please try:```
sudo rm /var/lib/dpkg/lock
sudo dpkg-reconfigure -a 
sudo  apt-get remove --purge bcmwl-kernel-source
```> BTW, when you said my system is very unhappy, were you referring to the laptop or me? LOL! All three of us!

---

### Post by greengeek2 on 2014-03-02
> **chili555 said:**
> ```
sudo rm /var/lib/dpkg/lock
sudo dpkg-reconfigure -a 
sudo  apt-get remove --purge bcmwl-kernel-source
```

Tried:
sudo rm /var/lib/dpkg/lock

Response:
normal

Tried:
sudo dpkg-reconfigure -a

Response:
cursor blinks about 10X then freezes.

Tried:
sudo  apt-get remove --purge bcmwl-kernel-source.

Response:
Reading package lists... Done
Building dependency tree
Reading state infomration... done
E: Unable to locate package bcmwl-kernel-source

DOH! 3 unhappy systems is NOT good! LOL!

---

### Post by chili555 on 2014-03-03
We have been at this for days. If it were me, I'd do a backup and reinstall in about 30 minutes. I'd do all the installation without an internet connection and refuse the offer to install additional drivers, aka the dreaded-in-your-case bcmwl-kernel-source, aka the wrong, wrong, wrong driver for your Broadcom 4311, I don't care what Broadcom themselves tell you!

After it's done, I'd walk over to the router, hook up the ethernet and open a terminal; if you install 13.10, which I recommend:```
sudo apt-get install linux-firmware-nonfree
```Or if you install 12.04 LTS:```
sudo apt-get install firmware-b43-installer
```Detach the ethernet and both ethernet and wireless should be working correctly.

I believe these problems often occur when an update is interrupted:> W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
When you get up and running, let Update Manager run to its natural completion. After a fresh install, it may take several minutes, please be patient.

---

### Post by greengeek2 on 2014-03-03
> **chili555 said:**
>  We have been at this for days.  
Welcome to my "groundhog", I've been in it for 8 days. lol!

> If it were me, I'd do a backup and reinstall in about 30 minutes. I'd do  all the installation without an internet connection and refuse the  offer to install additional drivers, aka the dreaded-in-your-case  bcmwl-kernel-source, aka the wrong, wrong, wrong driver for your  Broadcom 4311, I don't care what Broadcom themselves tell you! After it's done, I'd walk over to the router, hook up the ethernet and open a terminal; if you install 13.10, which I recommend.

Didn't do a back up since there was really nothing for me to back up.

Tried:
Installed Lubuntu 13.10 from usb thumbdrive with NO internet connection. 

Connected to internet via wired.

Tried: 
sudo apt-get install linux-firmware-nonfree

Response:
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

Tried:
Installed Lubuntu 13.10 AGAIN with NO interent connection, thinking I didn't do it right the 1st time. BTW, I installed while having a grey screen both times. I didn't know if it was installing in the background which it was because I just stared at the monitor and Lubuntu started the options for me to choose.

Connected to internet via wired.

Tried Again:
sudo apt-get install linux-firmware-nonfree 

Response:
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

Detached the ethernet even though I got the above response.

Tried numerous times with and without a wired connection to get to Lubuntu Desktop. Per your last instructions and me trying to follow your EASY directions, then...TAADAA! (About 3 hours later)...I've gotten to the Lubuntu Desktop! Now I'm afraid to turn off the laptop for fear I might go thru the same problems. lol!

O.K., now what? :D

---

### Post by chili555 on 2014-03-03
> TAADAA! (About 3 hours later)...I've gotten to the Lubuntu Desktop! Now I'm afraid to turn off the laptop for fear I might go thru the same problems. lol!This time, did you also get:> W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
If so, please do:```
sudo rm /var/lib/dpkg/lock
sudo apt-get update
```Tell us what the result is; we don't need miles of code, just that it worked with no errors, or, if not, what the error was.

---

### Post by greengeek2 on 2014-03-03
O.K.  Did as you instructed, figured I had to do them connected via lan...DOH! I am now able to get online. Now what?

---

### Post by chili555 on 2014-03-03
> **greengeek2 said:**
> O.K.  Did as you instructed, figured I had to do them connected via lan...DOH! I am now able to get online. Now what?Connected with wireless? Did the *apt-get update* go without errors, smoke, sparks, screams, etc.? If so, I'd try a reboot.

Fingers crossed!

[http://www.shockwave-sound.com/sound-effects/scream-sounds/cri-d-effroi-scream.wav](http://www.shockwave-sound.com/sound-effects/scream-sounds/cri-d-effroi-scream.wav)

---

### Post by greengeek2 on 2014-03-03
Did the apt-get update with NO errors! YAH! No smoke, sparks, but did scream for joy until I rebooted. I still get the grey screen. The only way for me to get to the Lubuntu desktop is to:

F12 enter (even though I changed bios to start from hard disk NOT usb> tab to Advanced> tab down to recovery mode > in GRUB, I tab to enter normal boot.

FYI: With the lap top connected via ethernet. I click on the up/down arrows, greyed out: Ethernet Network

Fingers crossed didn't seem to work. :(

How did you record my screaming ([http://www.shockwave-sound.com/sound...roi-scream.wav]("http://www.shockwave-sound.com/sound-effects/scream-sounds/cri-d-effroi-scream.wav")) without me seeing you? LOL!

---

### Post by chili555 on 2014-03-04
I am sorry to hear about the grey screen issue. I am not at all sure what's going on there. I'm sort of like a plumber who doesn't know much about electricity except don't touch it! I suggest you try to sort it out here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

When you try to enable the ethernet, what driver(s) are loaded? ```
lsmod | grep -e wl -e b4
```If b44 is not among them, load it:```
sudo modprobe b44
```Now does the ethernet come to life? By the way, if wl is loaded, *I* am going to scream!!!

---

### Post by greengeek2 on 2014-03-04
> **chili555 said:**
> I am sorry to hear about the grey screen issue. I am not at all sure what's going on there. I'm sort of like a plumber who doesn't know much about electricity except don't touch it! I suggest you try to sort it out here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Thanks for the link, will look into it AFTER this wireless issue is solved. I hope soon!

> When you try to enable the ethernet, what driver(s) are loaded? ```
lsmod | grep -e wl -e b4
```If b44 is not among them, load it:```
sudo modprobe b44
```Now does the ethernet come to life? By the way, if wl is loaded, *I* am going to scream!!!

Tried:
lsmod | grep -e wl -e b4

Response:
b43              356429 0
bcma             40966 1 b43
mac80211     517444 1 b43
cfg80211       401762 2 b43, mac80211
b44                31234 0
mii                 13654 1 b44
ssb                51596 3 b43, b44, ssb_hcd

Yes, I can access the internet via the ethernet but not wireless. Is there a process I have to go thru via the network manager for wireless to work?

BTW, during the start up when a lot of [PASS]'s flash on screen, I'm able to see: "Starting reload cups... [FAIL]". I can't catch the rest of what it says because it flashes so fast.

p.s. screaming is optional at this point. lol!

---

### Post by Hadaka on 2014-03-04
Hi , i have the same deiver set...b-44 eth, b-43 wlan
i have NO

mii                 13654 1 b44

this may be left over from an attempt with a different
non broadcom driver...i would suggest commenting it out
or removing it.

---

### Post by chili555 on 2014-03-04
> **Hadaka said:**
> Hi , i have the same deiver set...b-44 eth, b-43 wlan
i have NO

mii                 13654 1 b44

this may be left over from an attempt with a different
non broadcom driver...i would suggest commenting it out
or removing it.Perhaps you are using an earlier version than greengeek2. Here is what modinfo says:```
$ [COLOR="#FF0000"]modinfo b44[/COLOR]
filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/ethernet/broadcom/b44.ko
<snip>
[COLOR="#FF0000"]depends:        ssb,mii[/COLOR]
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           b44_debug:B44 bitmapped debugging message enable value (int)
```

---

### Post by chili555 on 2014-03-04
> **greengeek2 said:**
> Yes, I can access the internet via the ethernet but not wireless. Is there a process I have to go thru via the network manager for wireless to work?Normally, if you detach the ethernet, it will start right up; however, before you do so, let's be sure the firmware is installed:```
sudo apt-get install linux-firmware-nonfree
```It will either report that it's already installed and the latest version, or it will be installed. In either event, detach the ethernet and see if Network Manager doesn't connect.>  I'm able to see: "Starting reload cups... [FAIL]"'cups' is the Common Unix Printing System; check for errors, warnings, etc.here:```
dmesg | grep cups
```For that matter, any warning or error at boot can be seen in dmesg or in /var/log/syslog; usually at or near the end. 

Again, ask the electricians here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by greengeek2 on 2014-03-04
> **chili555 said:**
> Normally, if you detach the ethernet, it will start right up; however, before you do so, let's be sure the firmware is installed:```
sudo apt-get install linux-firmware-nonfree
```It will either report that it's already installed and the latest version, or it will be installed.

Tried:
sudo apt-get install linux-firmware-nonfree

Response:
looks like it installed! 

> In either event, detach the ethernet and see if Network Manager doesn't connect.

Detached from ethernet, get the FAN icon. I even tried moving the laptop closer to the router (btw, battery is completely dead, have to plug in). :mad:

> 'cups' is the Common Unix Printing System; check for errors, warnings, etc.here:```
dmesg | grep cups
```For that matter, any warning or error at boot can be seen in dmesg or in /var/log/syslog; usually at or near the end.

Will NOT worry about this issue for now. It's put on the way, way, way back burner. Will cross this bridge when I have to and if Gov. Christie hasn't shut it down. :lolflag:

> Again, ask the electricians here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Will tackle this once the wifi is solved (if at all possible).

---

### Post by greengeek2 on 2014-03-04
> **Hadaka said:**
> Hi , i have the same deiver set...b-44 eth, b-43 wlan
i have NO

mii                 13654 1 b44

this may be left over from an attempt with a different
non broadcom driver...i would suggest commenting it out
or removing it.

Thanks Hadaka for your input, however, I don't know how to comment it out or remove it. BTW, if I did do as you suggested, would it mess up/interfere with trying to solve the wireless issue?

---

### Post by chili555 on 2014-03-04
I suggest you charge up the battery first. Then click the fan icon. Do you see your network listed? Click on it. You should be challenged for your WPA2 password; fill it in and enjoy! [http://www.techotopia.com/images/c/c9/Ubuntu_11_unity_network_menu.jpg](http://www.techotopia.com/images/c/c9/Ubuntu_11_unity_network_menu.jpg)

---

### Post by greengeek2 on 2014-03-05
Hello Chili555, when I said the battery is dead, I meant DEAD-DEAD,REALLY DEAD, KAPUT! No life in it whatsoever, I have to connect via the power cord. 

Anyways, I'm off on how to fix the grey screen AND upgrading BIOS from 2.4.1 to 2.6.3. (If anybody out there can direct me to a SOLVED link, I would REALLY appreciate it. I haven't had any luck so far. I have 0X01F5, system id?)

Thanks for ALL of your help, patience, and guidance!

Consider this groundhog movie over...or is it? :)

---

### Post by chili555 on 2014-03-05
> **greengeek2 said:**
> Consider this groundhog movie over...or is it? :)Get the grey screen fixed, get *cups *running as expected and I suspect your wireless with be perfect. If not, post back and we'll mend it.

---

### Post by greengeek2 on 2014-03-07
Chili555, GREAT news! Got wifi working. Here's how it happened. First, I threatened laptop that if it does't start working, I'm gonna use it for target practice. I let it think about it over night. Then I fired it up a couple of times with/without ethernet AND toggled fn + f2 . YEE-HAW! I got wireless from 2 blocks away. Must have been the threat that got it to work. :p Still haven't figured out how to log on to own wi-fi because of security key needed. Will figure that out later. 

I'm off to figuring out how to upgade the bios.

Thanks for ALL of your help and patience!

---

### Post by chili555 on 2014-03-07
Glad it's working by whatever means. Have fun!

---

### Post by Luis_Corbalan on 2014-03-09
i&#472;e just install ubuntu 12.04 in my laptop (Dell inspiron 1521) and wired and wireless are not working. It seams the hardware dtected but not working.

---

### Post by westie457 on 2014-03-09
Welcome Luis_Corbalan

Let us see which wireless chip you have. Please open a terminal (Ctrl+Alt+T is the usual shortcut) and copy & paste this command into the terminal ```
lspci -nn | grep network -iA2
```
Then post the output back here.

Be aware that if your chip is different to the one in this thread I will ask for this to be moved to its own thread.

---

### Post by gacb on 2014-03-13
For what it's worth, this is not a universal fix and breaks the wireless connection on some machines. Mine runs fine on the bcmwl-kernel-source but not at all on the nonfree version.

---

### Post by chili555 on 2014-03-13
> **gacb said:**
> For what it's worth, this is not a universal fix and breaks the wireless connection on some machines. Mine runs fine on the bcmwl-kernel-source but not at all on the nonfree version.For what it's worth, is yours a Broadcom 4311?```
lspci -nn | grep 0280
```

---

### Post by hashky on 2014-04-26
I just installed Ubuntu 14.04.  Dell 1501, Broadcom 14e4:4311.  I did not have wire or wireless connection.  I ran the remove purge command.  The install nonfree command would not run. (Duh-no internet.)
Rebooted.

After the reboot, I had a wired connection.  I was the able to run the install nonfree.

Thanks to Chili555.

hashky

---

### Post by FreeScholar on 2014-05-07
> **chili555 said:**
> Please try this:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and let us have your report.

This post really saved me in my hour of need!!! Thank you so much chili555 you are a life saver.

---

