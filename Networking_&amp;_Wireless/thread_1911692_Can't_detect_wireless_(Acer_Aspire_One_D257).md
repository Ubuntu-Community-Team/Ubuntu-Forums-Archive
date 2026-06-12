---
title: "Can't detect wireless (Acer Aspire One D257)"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by andrey94 on 2012-01-19
Hi! I installed Ubuntu 10.10 on my Acer Aspire One D257 and it can't detect wireless (the indicator and FN+F3 aren't working).

The same problem is in Ubuntu 10.04

I'm a novice in Ubuntu and any help would be greatly appreciated.

---

### Post by chili555 on 2012-01-19
Please open a terminal and run and post the results of these commands:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by andrey94 on 2012-01-20
Thank you very much, but I have solved this problem recently.

---

### Post by click170 on 2012-02-14
Please explain how you solved this problem so that other people (Hi there! :) ) can solve it as well.

Thanks!

---

### Post by chili555 on 2012-02-14
Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by SnakeEater on 2012-02-14
> **chili555 said:**
> Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.
i have the same problem but with 10.04 here are the results of the commands


lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Device 08ae
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
woody@woody-laptop:~$ nn
The program 'nn' is currently not installed.  You can install it by typing:
sudo apt-get install nn
woody@woody-laptop:~$ |
bash: syntax error near unexpected token `|'
woody@woody-laptop:~$ grep
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
woody@woody-laptop:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
woody@woody-laptop:~$ list
No command 'list' found, did you mean:
 Command 'dist' from package 'nmh' (universe)
 Command 'slist' from package 'ncpfs' (universe)
 Command 'klist' from package 'heimdal-clients' (universe)
 Command 'klist' from package 'krb5-user' (main)
 Command 'listg' from package 'nauty' (multiverse)
 Command 'hist' from package 'loki' (universe)
 Command 'flist' from package 'nmh' (universe)
 Command 'last' from package 'sysvinit-utils' (main)
 Command 'gist' from package 'yorick' (universe)
 Command 'bist' from package 'bist' (universe)
list: command not found
woody@woody-laptop:~$ all
No command 'all' found, did you mean:
 Command 'ali' from package 'nmh' (universe)
 Command 'ali' from package 'mailutils-mh' (universe)
 Command 'ale' from package 'ale' (universe)
 Command 'alc' from package 'amule-utils-gui' (universe)
 Command 'alc' from package 'amule-adunanza-utils-gui' (universe)
 Command 'al2' from package 'mono-2.0-devel' (main)
 Command 'al1' from package 'mono-1.0-devel' (universe)
 Command 'als' from package 'atool' (universe)
 Command 'wall' from package 'bsdutils' (main)
 Command 'al' from package 'mono-devel' (main)
 Command 'axl' from package 'afnix' (universe)
all: command not found
woody@woody-laptop:~$ ^C
woody@woody-laptop:~$ ^C
woody@woody-laptop:~$ 

when i try to install nn it asks for the password but wont let me type it in

---

### Post by andrey94 on 2012-02-15
Hi!
This is the best sollution from russian forums:

```
cd ~
sudo apt-get install build-essential
wget -c http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2012-02-14.tar.bz2
tar xvf compat-wireless-2012-02-14.tar.bz2
cd compat-wireless-2012-02-14
scrip*/driver-select intel
make
sudo make install
sudo reboot
```

NB: the name of  compat-wireless-2012-02-14.tar.bz2 sometimes changes to new name. You can find it in [http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/)

---

### Post by andrey94 on 2012-02-15
Or just install Ubuntu 11.04 (your can still change this stupid Unity to Gnome there)

---

### Post by SnakeEater on 2012-02-15
i did the commands and when done it rebooted but still doesnt work. i tried it twice

---

### Post by andrey94 on 2012-02-15
Very strange, I checked everything and it helped me last time. If you did everything right and it didn't help maybe it is better to download Ubuntu 11.04 and install it? The nececery driver is in the kernel of this version.

---

### Post by andrey94 on 2012-02-15
Haven't you forgot to press Fn + F3 to run WiFi module?

---

### Post by chili555 on 2012-02-15
> **SnakeEater said:**
> i have the same problem but with 10.04 here are the results of the commands

when i try to install nn it asks for the password but wont let me type it inThose commands are all one command on each line. Please see attached. The pipe symbol | is on the right side of my US keyboard on the same key with \.

Also, for security purposes, your password is not echoed back, even as ****. Just type it in and press Enter. It's there. There is no need to install anything.

Please try again.

---

### Post by chili555 on 2012-02-15
> **andrey94 said:**
> Hi!
This is the best sollution from russian forums:

```
cd ~
sudo apt-get install build-essential
wget -c http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2012-02-14.tar.bz2
tar xvf compat-wireless-2012-02-14.tar.bz2
cd compat-wireless-2012-02-14
scrip*/driver-select intel
make
sudo make install
sudo reboot
```

NB: the name of  compat-wireless-2012-02-14.tar.bz2 sometimes changes to new name. You can find it in [http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/)How could you know, without seeing his lspci that he has an Intel wireless card?

This command is mis-stated:> scrip*/driver-select intelintel is not an available driver group under compat-wireless, even if he  has an Intel card.

Isn't linux-headers-generic also required to compile this?> Very strange, I checked everything I don't think so.> Haven't you forgot to press Fn + F3 to run WiFi module?He said in his first post that it isn't working.

---

### Post by andrey94 on 2012-02-15
Hey, Mr. Einstein, I've written that THIS SOLLUTION HELPED me, even twice. And it was I WHO WROTE FIRST POST and I'm helping the user SnakeEater. If he has the same laptop it shoud help him, if you want to help, better read the posts and users' names more carefully

---

### Post by chili555 on 2012-02-15
Please see PM.

---

### Post by SnakeEater on 2012-02-15
okay after a long day of updating im now using 11.04 and wifi works as well as the hot keys. thanks for the help i appreciate it

---

### Post by andrey94 on 2012-02-16
You are welcome

---

