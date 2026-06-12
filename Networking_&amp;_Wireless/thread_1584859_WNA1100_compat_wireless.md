---
title: "WNA1100 compat wireless"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by steven4601 on 2010-09-29
Hello,

I have modified this post to improve the quality of my attempt to help installing the wna1100 drivers.

Please see the** attached file **(open office document). 

Kind Regards,
Steven

---

### Post by Corey4666 on 2010-10-03
```
sudo apt-get install linux-headers-$(uname -r) build-essential  http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2 
cd compat-wireless-2010*
./scripts/driver-select ath9k_htc
```

How can i do this part offline? I have no internet access. I have wireless in my apartment, I cant get my PC online. I am using a laptop with windows right now..

---

### Post by steven4601 on 2010-10-03
Plug your pc into the wifi router ?

or else:
Crosscable!  Sharing internet is not that difficult. I found it by googling.

My situation is / was exactly the same as yours. I had to share internet from my laptop as well in order to install those linux headers.

---

### Post by Corey4666 on 2010-10-03
I can't ICS w/ my laptop and this PC, It refuses to work and trust me I have done it before many times. I can't plug my PC into a router because my apartment has free wireless for the building.....

I actually am on dial up right now.... on my ubuntu system which I am absolutely amazed I was able to make work. It's rather slow, anyways I have done this so far. 

```
eviscerate@evi-main:~$ sudo apt-get install linux-headers-$(uname -r) build-essential  http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
[sudo] password for eviscerate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-7-generic is already the newest version.
linux-headers-2.6.27-7-generic set to manually installed.
E: Couldn't find package build-essential
eviscerate@evi-main:~$ wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
--2010-10-03 12:17:52--  http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
Resolving wireless.kernel.org... 78.46.109.217
Connecting to wireless.kernel.org|78.46.109.217|:80... connected.
HTTP request sent, awaiting response... 307 Temporary Redirect
Location: /en/users/Download [following]
--2010-10-03 12:17:54--  http://wireless.kernel.org/en/users/Download
Reusing existing connection to wireless.kernel.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `Download'

    [           <=>                         ] 29,293      11.3K/s   in 2.5s    

2010-10-03 12:17:57 (11.3 KB/s) - `Download' saved [29293]

eviscerate@evi-main:~$ tar jxvf compat-wireless-2.6.tar.bz2 
tar: compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
eviscerate@evi-main:~$ cd compat-wireless-2010*
bash: cd: compat-wireless-2010*: No such file or directory
eviscerate@evi-main:~$ ./scripts/driver-select ath9k_htc
bash: ./scripts/driver-select: No such file or directory
eviscerate@evi-main:~$ 

```

I am seeing errors, etc I have no idea what I am doing... :confused: I am not good with setting this kind of stuff up. I really need some help here. These commands are over my head. All I know is there to download and auto install things to help my wireless, I have no idea why there not working though. :(

---

### Post by Corey4666 on 2010-10-03
```

compat-wireless-2010-10-02/include/linux/compat-2.6.23.h
compat-wireless-2010-10-02/include/linux/tracepoint.h
compat-wireless-2010-10-02/include/linux/compat-2.6.36.h
compat-wireless-2010-10-02/include/linux/compat-2.6.29.h
compat-wireless-2010-10-02/include/linux/compat_autoconf.h
compat-wireless-2010-10-02/include/linux/compat-2.6.19.h
compat-wireless-2010-10-02/include/linux/ieee80211.h
compat-wireless-2010-10-02/include/linux/compat-2.6.28.h
compat-wireless-2010-10-02/include/linux/compat-2.6.37.h
compat-wireless-2010-10-02/include/linux/wireless.h
compat-wireless-2010-10-02/include/linux/compat-2.6.24.h
compat-wireless-2010-10-02/include/linux/pci-aspm.h
compat-wireless-2010-10-02/include/linux/eeprom_93cx6.h
compat-wireless-2010-10-02/include/linux/compat-2.6.34.h
compat-wireless-2010-10-02/include/linux/compat-2.6.h
compat-wireless-2010-10-02/include/linux/ath9k_platform.h
compat-wireless-2010-10-02/code-metrics.txt
compat-wireless-2010-10-02/linux-next-cherry-picks/
compat-wireless-2010-10-02/linux-next-cherry-picks/README
compat-wireless-2010-10-02/enable-older-kernels/
compat-wireless-2010-10-02/enable-older-kernels/enable-2.6.22.patch
compat-wireless-2010-10-02/enable-older-kernels/enable-2.6.24.patch
compat-wireless-2010-10-02/enable-older-kernels/README
compat-wireless-2010-10-02/enable-older-kernels/enable-2.6.21.patch
compat-wireless-2010-10-02/enable-older-kernels/enable-2.6.23.patch
compat-wireless-2010-10-02/config.mk
compat-wireless-2010-10-02/master-tag
compat-wireless-2010-10-02/compat_version
eviscerate@evi-main:~$ cd compat-wireless-2010*
eviscerate@evi-main:~/compat-wireless-2010-10-02$ ./scripts/driver-select ath9k_htc
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backing up makefile: drivers/net/wireless/ath/Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
Backing up makefile: drivers/misc/eeprom/Makefile.bk
eviscerate@evi-main:~/compat-wireless-2010-10-02$ 
eviscerate@evi-main:~/compat-wireless-2010-10-02$ 
eviscerate@evi-main:~/compat-wireless-2010-10-02$ 

```

I downloaded the wget file on my laptop and transfered it to the home folder on a usb stick.

Okay well I cut out half of the terminal, I guess its "compiling" or installing whichever... What am I supposed to do now?

I am once again lost ><

I don't know what to do for the 3rd step where you say
> vi the file,
I have no idea what that means or how to do it.

```
eviscerate@evi-main:~/compat-wireless-2010-10-02$ ~/wna1100/compat-wireless-2010-09-28/drivers/net/wireless/ath$ vi Makefile
bash: /home/eviscerate/wna1100/compat-wireless-2010-09-28/drivers/net/wireless/ath$: No such file or directory
eviscerate@evi-main:~/compat-wireless-2010-10-02$ 
```

---

### Post by milux_1 on 2010-10-03
Hi Corey4666,  

Please make sure that you have the same chip as steven has (use "lsusb" to list your usb devices, it should say: "Bus 001 Device 002: ID 0846:9030 NetGear, Inc". Otherwise the above instructions may not help.  

It will not be easy when you have no internet connection and are trying to build the drivers yourself because there are a lot of dependencies when you never build a kernel driver on that pc. But nevertheless, it can be done. 

The packages steven mentioned (build-essentials e.o.) can be downloaded from: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Those are *.deb files. There exist a handy search function on that website. *.deb files can be installed by executing "dpkg -i *.deb". It could be that a package could not be installed because of a dependency. The only thing to do then is to get back to your apartment and download the missing dependencies, put them on a usb stick, and try again. That's why it is not _that_ easy ;-). 

Good luck,

---

### Post by Corey4666 on 2010-10-03
```
eviscerate@evi-main:~$ lsbusb
bash: lsbusb: command not found
eviscerate@evi-main:~$ 


```

My build essentials are up to date. I installed them in the terminal. I am on dial up right now following this guide so I do have a active Internet connection.

---

### Post by steven4601 on 2010-10-03
my bad, its lsusb

as in ls for regular directories, lsusb  lists usb devices.

---

### Post by Corey4666 on 2010-10-03
```
eviscerate@evi-main:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 007: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 006 Device 006: ID 0846:9030 NetGear, Inc. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f3:0213 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 004: ID 0d8c:0121 C-Media Electronics, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
eviscerate@evi-main:~$ 

```

My device is not showing up at all?

EDIT: 

Nevermind I see it... is it the same as yours?

---

### Post by steven4601 on 2010-10-03
ID 0846:9030 NetGear, Inc

 that ID string matches with the ID string in one of your USB devices. So thats definitely a Yes.

vi is a nasty command line editor. You can use your favourite gnome text editor too!

---

### Post by Corey4666 on 2010-10-03
Yeah, I just figured out how to edit that file using gedit instead.

Now for this step?

```
make
sudo make install
```

Which file am I supposed to try to make install?


-----------

And for the "ar9271.fw" The file downloaded multiple times as 0 kb in size... I also don't know how to extract it...

---

### Post by milux_1 on 2010-10-03
typ make in the compat-wireless* directory.

You do not have to extract the firmware (*fw) file. Is it exactly 0kb, or just below 1kb?

---

### Post by steven4601 on 2010-10-03
steven@w00tbox:~/wna1100/linux-firmware-HEAD-e9f9e3a$ ls -all | grep ar9271.fw
-rw-r--r--  1 steven steven   **51280** 2010-09-29 05:02 ar9271.fw
steven@w00tbox:~/wna1100/linux-firmware-HEAD-e9f9e3a$ 

its 51280 bytes!

---

### Post by Corey4666 on 2010-10-03
```

eviscerate@evi-main:~$ make compat-wireless*
make: Nothing to be done for `compat-wireless-2010-10-02'.
make: Warning: File `compat-wireless-2.6.tar.bz2' has modification time 1.1e+04 s in the future
make: Nothing to be done for `compat-wireless-2.6.tar.bz2'.
make: warning:  Clock skew detected.  Your build may be incomplete.
eviscerate@evi-main:~$
```

I don't know what that means lol...

Uhh for the ar9271.fw 

in its properties it says "0 bytes" plain txt document.

EDIT: 
Its because I didnt snapshot, ...my bad I am doing so right now! sorry about that.

---

### Post by steven4601 on 2010-10-03
[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=tree)  

it is a webpage, click on snapshot. That should popup with a file-save-as dialog. That file needs to be unpacked.  One file is needed: which is that ar9271.fw file.

---

### Post by Corey4666 on 2010-10-03
Okay, got it extracted and the bytes match up with yours.

I tried copying it to

/lib/firmware

It said permission denied.

---

### Post by steven4601 on 2010-10-03
In one of your previous posts you had errors with make.
Are you certain you ran make IN the compat-wireless folder you extracted? It apeared to me as if you where trying to make the compressed file itself which is ambitious.  :P

After a succesful run of make you have to type "sudo make install".


Copying files to system protected/owned folders requires sudo

---

### Post by Corey4666 on 2010-10-03
What do you mean did I run "make" in the compat-wireless folder? Does that mean I have to have the compat-wireless folder open when I type "make"?

Also I know what sudo does / means. I have no idea how to use it outside of a terminal window though... So using sudo to drag a file into a folder is beyond confusing for me, I also don't know how to make files transfer from my desktop into a destination using the terminal.

What I am trying to do is drag and drop the "ar9271.fw" into the firmware folder.


I am really beyond lost on what I am doing, so I really thank you both for helping me out so much.

EDIT:
Man, I have no idea how to use make, make install work.... what am I supposed to be installing???? you said "compat-wireless" folder.. I directed it to /home/compat-wireless

It said nothing was needed to be ... ugh well

> eviscerate@evi-main:~$ make /home/eviscerate/compat-wireless-2010-10-02
make: Nothing to be done for `/home/eviscerate/compat-wireless-2010-10-02'.
eviscerate@evi-main:~$ 


I don't know what I am supposed to be using the command "make" for?

---

### Post by steven4601 on 2010-10-03
im about to test my bed again. See if its still nice and fluffy.

Take a few steps back as it seems your not understanding what make does and or how it operates.  In the console, you have to change-dir into the compat wireless folder.

in the console, find the compat-wireless folder you extracted. 
cd compat-wireless-2010-10-02
./scripts/driver-select ath9k_htc


then run/ type
make
watch for errors

if none,
run / type
make install   
 in that same directory.


hope it works out, if not
Ill be back tomorrow, ~ in 20hours

---

### Post by Corey4666 on 2010-10-03
oh okay well the make install is done.

I also copied that file into the firmware folder. 

cya tommarows, I am on the last part of your OP.

---

### Post by steven4601 on 2010-10-04
All you have to do now run 

modinfo ath9k_htc


If it shows something similar to the output listed on the start of this tread
type


modprobe ath9k_htc

it should be activated and the blue-led on the usb-stick should light up. :guitar:

---

### Post by l0v3525p0093 on 2010-10-08
Hi, I am very new to Linux and am in the same boat with the same network adapter. Just for ?s clarification, so I'm supposed to put


```

sudo apt-get install linux-headers-$(uname -r) build-essential  http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2 
cd compat-wireless-2010*
./scripts/driver-select ath9k_htc 

```
into a text editor, correct? If so, how am I supposed to save the file to make it executable?


What do you mean by:
 > [COLOR=#141312][FONT=Sans Serif]vi the file, replace  the last line which should say ath-(debug Blahblah) line : 
[/FONT][/COLOR]?

What am I supposed to do exactly with all this code?
> ```

 [COLOR=#141312][FONT=Sans Serif]~/wna1100/compat-wireless-2010-09-28/drivers/net/wireless/ath$ vi Makefile[/FONT][/COLOR]
 
 [COLOR=#141312][FONT=Sans Serif]obj-$(CONFIG_ATH9K_HW)          += ath9k/[/FONT][/COLOR]
 [COLOR=#141312][FONT=Sans Serif]obj-$(CONFIG_ATH_COMMON)        += ath.o[/FONT][/COLOR]
 [COLOR=#141312][FONT=Sans Serif]ath-objs :=     main.o \[/FONT][/COLOR]
 [COLOR=#141312][FONT=Sans Serif]                regd.o \[/FONT][/COLOR]
 [COLOR=#141312][FONT=Sans Serif]                hw.o \[/FONT][/COLOR]
 [COLOR=#141312][FONT=Sans Serif]                key.o[/FONT][/COLOR]

```now make it without the no rule to make target error:
```

make
sudo make install

```

I'll leave it at there for now. I won't be doing any of this until tomorrow since I will have to move my entire PC set up into the living room in order to get the necessary internet access, and I'm not up to doing that tonight. Anyway, I hope you don't mind helping my hopelessly n00b *** through this process, hope to hear from you soon.

---

### Post by steven4601 on 2010-10-08
Hi there,  Im working on a hopefully easier to understand howto, sadly i cant finish it yet today. Ill do my best for tomorrow.

---

### Post by myothernameisreal on 2010-10-15
Thank you so much.  I've had a nightmare of a time trying to get this hardware running on Ubuntu 10.10 (fresh install, fresh linux user for that matter), and this .odt file told me everything I needed to know.  I really can't thank you enough for breaking all of this down for us newbies.

---

### Post by Messier 66 on 2010-10-22
Thanks for sharing this tutorial steve4601. I do whatever I can before going the ndiswrapper way and this is just what i needed. Since Backtrack 4 is based on Ubuntu it works in there too (have to add some lines in the kernel-config-file though).Good stuff.
                                                             =D>

---

### Post by morbidcracker on 2010-11-13
/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k/init.c: In function ‘ath9k_init_device’:
/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k/init.c:762: error: implicit declaration of function ‘pm_qos_add_request’
/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k/init.c: In function ‘ath9k_deinit_device’:
/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k/init.c:820: error: implicit declaration of function ‘pm_qos_remove_request’
make[5]: *** [/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k/init.o] Error 1
make[4]: *** [/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath/ath9k] Error 2
make[3]: *** [/home/eric/compat-wireless-2010-11-09/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/eric/compat-wireless-2010-11-09/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/eric/compat-wireless-2010-11-09] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [modules] Error 2




lawl...ive tried it EVERY way i know to...editing the make file...downgraded to 10.04 its just straight ubuntu but that shouldnt make a diff...latest linux headers...tried it on old linux headers...it ALWAYS gives me the same error on the SAME files
everything matches what u described in your tutorial

---

### Post by NoNameWill on 2010-11-24
I am having the same problem with

```
tar -xf compat-wireless-2.6.tar.bz2
```


I am getting a error

```
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


```

---

### Post by karthikeyan_sw on 2010-12-13
looks like compat-wireless-2.6.tar.bz2 is corrupted, make sure the size is 3.7MB

in the extraction step i was not able to do the following step, but it did not affect my whole process

  	 	 	 	p { margin-bottom: 0.21cm; }  tar xf linux-headers <TAB><ENTER>


I want to make sure will this be a real issue?


~Karthikeyan Sw.

 
[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by Bristol_Green on 2010-12-17
I'm running 10.10 and also trying to install a wna1100. It seems I already have the driver, but the dam thing won't work! After this, no led, nothing. 

stephen@stephen-desktop:~$ modinfo ath9k_htc
filename:       /lib/modules/2.6.35-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D567C77238F6355D88D836E
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,led-class,ath9k_common,ath,cfg80211
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
stephen@stephen-desktop:~$ sudo modprobe ath9k_htc
[sudo] password for stephen: 
stephen@stephen-desktop:~$ 

Does the line

parm:           nohwcrypt:Disable hardware encryption (int)

have any bearing on things? It's not the same as in the .odt file. Otherwise I can't see any significant difference.

---

### Post by jmacleod on 2010-12-31
> **steven4601 said:**
> Hello,

I have modified this post to improve the quality of my attempt to help installing the wna1100 drivers.

Please see the** attached file **(open office document). 

Kind Regards,
Steven

Steven,

Thanks for your excellent tutorial! It worked perfectly for me!

JM

---

### Post by ritsu on 2011-01-17
> **Bristol_Green said:**
> I'm running 10.10 and also trying to install a wna1100. It seems I already have the driver, but the dam thing won't work! After this, no led, nothing. 

stephen@stephen-desktop:~$ modinfo ath9k_htc
filename:       /lib/modules/2.6.35-23-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     D567C77238F6355D88D836E
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,led-class,ath9k_common,ath,cfg80211
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
stephen@stephen-desktop:~$ sudo modprobe ath9k_htc
[sudo] password for stephen: 
stephen@stephen-desktop:~$ 

Does the line

parm:           nohwcrypt:Disable hardware encryption (int)

have any bearing on things? It's not the same as in the .odt file. Otherwise I can't see any significant difference.

I have exactly the same problem on my Dell Studio 1440 running ubuntu 10.10. The built-in wireless module failed so I have to use an external one. I followed every step and everything was good except the card does not blink. However, what is quite weird is it works on my desktop which is also running ubuntu 10.10.

Does anyone have any suggestions about this? Thanks in advance.

---

### Post by koanhead on 2011-02-22
Apparently there's an automated GUI tool to fix this:

[http://ubuntuforums.org/showthread.php?t=1663232](http://ubuntuforums.org/showthread.php?t=1663232)

Usual caveats about installing unsigned packages apply of course.

---

