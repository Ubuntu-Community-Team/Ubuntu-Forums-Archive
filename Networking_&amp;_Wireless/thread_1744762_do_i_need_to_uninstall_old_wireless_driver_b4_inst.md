---
title: "do i need to uninstall old wireless driver b4 install new one ?"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by doron387 on 2011-04-30
hi,
i have asus eeepc 1201N,
wireless worked great after i installed the realtek driver from realtek according to instructions in the forum.

what i did (and i do not really understand what it was) was :
1. downloaded the newest driver for rtl8192se for linux from realtek   
   site.
2. i extracted the folder to my /home.
3. i changed the folder's name to a shorter name (e.g. 'ttt').
4. i typed in the terminal the following :
   sudo su
   password
   cd ttt
   make
   make install
5. after that i opened another terminal and typed the following :
   sudo su
   password
   modprobe r8192se_pci
and it worked great for few months (the driver was of 2009, and my system's kernel was 2.6.35-25 or 2.6.35-26...)

BUT

[COLOR="Blue"][EDIT : the solution was, as stupid as it sounds: my system is dualboot of windows7/ubuntu 10.10,  i had to go to the windows7 os, enable the wireless, shutdown windows7 (reboot) and boot to ubuntu.\
now, would somebody explain to me how is it that there is no physical wireless switch on the asus 1201n and i have togo first to enable it in the win7 ? and what would happen if i had jut ubuntu installed ? how would i enable it then ??? well, at least i have wireless....] [/COLOR]
 
since then, i have upgraded my installation few times using the update manager, and suddenly i have realized that i have no more wireless.


now i have kernel 2.6.35-28.
i have dowloaded the newest driver from realtek, this time it is from 2010.

i tried to do the same as i did few months ago, downloaded the driver, extracted the folder, renamed it ppp, tyoed in the same commands, but it doesn't work as before.

should i have uninstalled the old driver ?        (how to do it?)
shoul'd i have done something wrong this time ?   (how to do it right?)
 
please help me you gurus....

doron387

---

### Post by chili555 on 2011-04-30
Isn't r8192se_pci included in the latest kernel?```
modinfo r8192se_pci
```If it isn't working out of the box, something else is wrong. Please run and post:```
sudo modprobe r8192se_pci
dmesg | grep 819
```Thanks.

---

### Post by doron387 on 2011-04-30
well, thanks for the fast response,
here is the output, and unfortunatelly i don't understand what it means.

output :

[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$ modinfo r8192se_pci
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/r8192se_pci.ko
license:        GPL
version:        0019.1207.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     B35243106478C16B758F56E
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)
doron-netbook@doron-netbook-1201N:~$ [/COLOR]

and

doron-netbook@doron-netbook-1201N:~$ sudo modprobe r8192se_pci
[sudo] password for doron-netbook: 
doron-netbook@doron-netbook-1201N:~$ dmesg | grep 819
[    1.931927] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 42
[    1.931936] ata2: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 42
[    1.931943] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 42
[    1.931950] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 42
[    1.931956] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 42
[    1.931963] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 42
[   21.394199] Linux kernel driver for RTL8192 based WLAN cards
[   21.394297] rtl819xSE 0000:07:00.0: enabling device (0000 -> 0003)
[   21.395889] rtl819xSE 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   21.395909] rtl819xSE 0000:07:00.0: setting latency timer to 64
[   30.326115] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   30.531358] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   32.557757] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[   32.660785] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   38.293415] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   58.009123] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[   58.120144] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   58.295002] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   59.913822] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[   67.805365] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[   67.916350] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   68.071479] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   69.898321] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[   73.842498] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[   73.953506] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   74.122483] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   75.974328] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  110.324440] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  110.435584] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  110.595129] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  111.986354] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  157.282485] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  157.393626] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  157.558677] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  158.073169] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  161.617619] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  161.728639] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  161.902569] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  164.081863] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  181.199196] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  181.310235] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  181.487142] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  181.954002] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=42 qidx=6!!!
[  181.954017] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=42 qidx=6!!!
[  182.220621] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  269.069455] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  269.180473] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  269.342581] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  270.306357] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  380.290453] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  380.401747] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  388.158770] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  388.269815] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  388.470546] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  388.606935] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  389.775566] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  390.613862] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  434.119193] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  434.230227] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  434.391160] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  434.666168] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  448.254748] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  448.365880] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  448.535217] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  450.490512] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=47 qidx=6!!!
[  450.490527] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=47 qidx=6!!!
[  450.758840] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  459.357301] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  459.468338] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  459.634545] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  460.682167] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  472.481907] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  472.593001] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  472.751526] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  474.712681] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  490.617636] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  490.728666] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  490.903080] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  492.768638] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  533.434585] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  533.545641] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  533.706553] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  534.932629] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  733.276932] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  733.387997] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  733.563620] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  735.066640] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=47 qidx=6!!!
[  735.066659] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=47 qidx=6!!!
[  735.330151] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  739.267677] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  739.378727] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  739.539585] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  741.260238] ================>r8192_wx_set_scan(): hwradio off
[  741.300636] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  748.526494] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  748.637592] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  748.799585] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  749.148181] ================>r8192_wx_set_scan(): hwradio off
[  749.282389] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  754.486152] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  754.597230] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  754.763057] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  755.213264] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  878.013437] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  878.124674] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  878.299662] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  879.620646] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
doron-netbook@doron-netbook-1201N:~$ 

any  comment on that ?

---

### Post by chili555 on 2011-04-30
> hw radio offThat suggests the wireless switch is set to 'Off.' Can you please check it? Let's have a look at:```
rfkill list all
```Thanks.

---

### Post by doron387 on 2011-04-30
chili555, i am not sure what u mean :

1. i don't have a wireless physical switch (i am dualbooting with win7, in win7 i use alt+f2 to on/off the wireles)
2. the code you gave me does nothng visible for me :

doron-netbook@doron-netbook-1201N:~$ rfkill list all
doron-netbook@doron-netbook-1201N:~$ 

so ?

---

### Post by chili555 on 2011-04-30
Is rfkill installed?```
sudo dpkg -s rfkill
```It ought to report back:> $ sudo dpkg -s rfkill
Package: rfkill
Status: install ok installed
If not, please temporarily get a wired connection and install it.```
sudo apt-get install rfkill
```Do you have a wireless LED? Does it glow, flicker, pulse, smoke, shoot X-rays, etc.? Does it change if you manipulate the Fn+F2 keys?

---

### Post by doron387 on 2011-04-30
alt+f2 does not show any change in lights/smoke/lazer etc... lol

but this is the output of what u said to type :


[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$[/COLOR] rfkill list all
[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$[/COLOR] sudo dpkg -s rfkill
[sudo] password for doron-netbook: 
Package `rfkill' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$[/COLOR] sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libebml2 libmatroska2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,806B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) maverick/universe rfkill i386 0.4-1 [7,806B]
Fetched 7,806B in 0s (12.1kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 129951 files and directories currently installed.)
Unpacking rfkill (from .../archives/rfkill_0.4-1_i386.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.4-1) ...

	  You have to configure "localepurge" with the command

	      dpkg-reconfigure localepurge

	  to make /usr/sbin/localepurge actually start to function.

	  Nothing to be done, exiting ...

[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$[/COLOR] sudo dpkg -s rfkill
Package: rfkill
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 64
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 0.4-1
Depends: libc6 (>= 2.4)
Description: tool for enabling and disabling wireless devices
 rfkill is a simple tool for accessing the Linux rfkill device interface,
 which is used to enable and disable wireless networking devices, typically
 WLAN, Bluetooth and mobile broadband.
 .
 rfkill uses /dev/rfkill, which is present in Linux kernel 2.6.31 and later.
Original-Maintainer: Darren Salt <linux@youmustbejoking.demon.co.uk>
Homepage: [http://wireless.kernel.org/en/users/Documentation/rfkill](http://wireless.kernel.org/en/users/Documentation/rfkill)
[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$[/COLOR] rfkill list all
[COLOR="Navy"]doron-netbook@doron-netbook-1201N:~$ [/COLOR]

---

### Post by chili555 on 2011-04-30
OK, now show us:```
rfkill list all
```

---

### Post by doron387 on 2011-04-30
doron-netbook@doron-netbook-1201N:~$ rfkill list all
doron-netbook@doron-netbook-1201N:~$ 

what's wrong ?

---

### Post by chili555 on 2011-04-30
> rfkill uses /dev/rfkill, which is present in Linux kernel 2.6.31 and later.I wonder if you have to reboot in order to create a device file; just a guess. Let's see if you have it:```
ls -al /dev/rfkill
```My system reports:> crw-rw-r--+ 1 root root 10, 62 2011-04-28 08:02 /dev/rfkillIf you get a different answer, please reboot and try again.

We're hoping we can unblock and your wireless will come to life. Also let us see:```
lsmod | grep wmi
```

---

### Post by doron387 on 2011-04-30
doron-netbook@doron-netbook-1201N:~$ rfkill list all
doron-netbook@doron-netbook-1201N:~$ ls -al /dev/rfkill
crw-rw-r--+ 1 root root 10, 62 2011-04-30 21:31 /dev/rfkill
doron-netbook@doron-netbook-1201N:~$ lsmod | grep wmi
snd_rawmidi            17783  1 snd_seq_midi
eeepc_wmi               2963  0 
sparse_keymap           3145  1 eeepc_wmi
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
doron-netbook@doron-netbook-1201N:~$ 

so ?
does it help us ?

---

### Post by chili555 on 2011-04-30
What about your LED?

Let's try:```
sudo rmmod -f eeepc_wmi
sudo modprobe r8192se_pci
dmesg | grep 819
```If there are repeats, just give me the last ten or so lines.

I'm mystified why rfkill says nothing. Did you try a reboot?

---

### Post by doron387 on 2011-04-30
hey chili555, this is the output,
i have'nt try a reboot, i will try it while waiting for your response
BTW, the led did not blink nor turned on until now

doron-netbook@doron-netbook-1201N:~$ sudo rmmod -f eeepc_wmi
[sudo] password for doron-netbook: 
doron-netbook@doron-netbook-1201N:~$ sudo modprobe r8192se_pci
doron-netbook@doron-netbook-1201N:~$ dmesg | grep 819
[    1.931927] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 42
[    1.931936] ata2: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76180 irq 42
[    1.931943] ata3: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76200 irq 42
[    1.931950] ata4: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76280 irq 42
[    1.931956] ata5: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76300 irq 42
[    1.931963] ata6: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76380 irq 42
[   21.394199] Linux kernel driver for RTL8192 based WLAN cards
[   21.394297] rtl819xSE 0000:07:00.0: enabling device (0000 -> 0003)
[   21.395889] rtl819xSE 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   21.395909] rtl819xSE 0000:07:00.0: setting latency timer to 64
.
.
.
.
.
id():hw radio off,or Rf state is eRfOff, return
[ 4761.821855] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[ 4761.932930] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 4762.102059] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 4763.372627] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[ 6596.567120] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[ 6596.678172] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 6596.834809] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ 6596.853769] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=42 qidx=6!!!
[ 6596.853784] rtl819xSE:rtl8192_tx: ERR!! Nic is disabled! Can't tx packet len=42 qidx=6!!!
[ 6596.959313] ================>r8192_wx_set_scan(): hwradio off
[ 6597.129119] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
doron-netbook@doron-netbook-1201N:~$

---

### Post by chili555 on 2011-04-30
until now?? Meaning what? When did it blink or flicker? After we did what? After a reboot, what does this tell us:```
sudo rfkill list all
sudo rmmod -f eeepc_wmi
sudo rfkill unblock all
dmesg | grep 819 | tail -n15
```Thanks.

---

### Post by doron387 on 2011-04-30
i am terribly sorry for beng misunderstood.
i meant that the led hasn'nt been blinking at all. 

and for your code :

doron-netbook@doron-netbook-1201N:~$ sudo rfkill list all
doron-netbook@doron-netbook-1201N:~$ sudo rmmod -f eeepc_wmi
doron-netbook@doron-netbook-1201N:~$ sudo rfkill unblock all
doron-netbook@doron-netbook-1201N:~$ dmesg | grep 819 | tail -n15
[   36.445130] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[   37.511644] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   51.116839] rtl819xSE:r8192_wx_set_power():Hw is Radio Off, we can't set Power,return
[   76.447046] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[   76.558110] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   76.731632] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   77.814079] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  100.474140] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  100.585185] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  100.742955] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  101.836568] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
[  128.286935] InitializeAdapter8190(): ==++==> Turn off RF for RfOffReason(1073741824) ----------
[  128.398135] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  128.558198] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[  129.858349] =========>r8192_wx_set_essid():hw radio off,or Rf state is eRfOff, return
doron-netbook@doron-netbook-1201N:~$

---

### Post by greynand on 2011-04-30
i have a hp dv5 ubuntu 10.10 my wireless was working fine when update to 11.04 stop working , help me please

---

### Post by doron387 on 2011-04-30
greynand,
every computer has it's own specifications, advantages and disadvantages.
so is with versions of ubuntu and their's compatability to every computer.
therefore, your question is very important but doesn't have to do anything with this thread.
please search for the key words : hp dv5 upgrade 10.10 11.04 wireless in the forum or in google and you might find a solution.
and also, you better know that always, when you do an upgrade you can't expect everything to work out of the box, especially not when you deal with a very new version of ubuntu.
if i was you, i would reinstall 10.10 and wait few weeks, look for threads about this issue and just after i found an answer to that problem, and good responses for that answer i would upgrade to 11.04
so good luck with your dv5

doron387

---

### Post by chili555 on 2011-04-30
> **greynand said:**
> i have a hp dv5 ubuntu 10.10 my wireless was working fine when update to 11.04 stop working , help me pleasePlease start a new thread. Tell us what wireless device you have:```
lspci -nn
lsusb
```

---

### Post by chili555 on 2011-04-30
@doron387--

Are we sure which driver is being used?```
modinfo r8192se_pci
```I am just about out of ideas.

---

### Post by doron387 on 2011-04-30
hey chili555,
here it is 00:08 , which means night time and tommorrow there is work early in the morning,
so i thank you  a lot for sticking with me to solve this problem.
i will now go to sleep and read your new commentrs tommorrow night,
hopefully we'll solve it soon.
i am working as a tour guide and going to take my ubuntu machine with me to my next 7 days trip, hopefully to be able to connect to wifi.

good night for me and good afternoon/morning to you

doron387

---

### Post by doron387 on 2011-04-30
well, you know how it is with porblems, they never really let you sleep until you solve them...lol

doron-netbook@doron-netbook-1201N:~$ modinfo r8192se_pci
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/r8192se_pci.ko
license:        GPL
version:        0019.1207.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     B35243106478C16B758F56E
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)
doron-netbook@doron-netbook-1201N:~$

---

### Post by chili555 on 2011-04-30
I'm off to another activity myself. See you tomorrow.

---

### Post by doron387 on 2011-05-01
well. i am jumping this thread to the top, if somebody can help...
doron387

---

