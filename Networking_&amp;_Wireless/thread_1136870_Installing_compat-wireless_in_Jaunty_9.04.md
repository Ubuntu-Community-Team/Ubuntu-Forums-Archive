---
title: "Installing compat-wireless in Jaunty 9.04"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by puller on 2009-04-25
Hi everybody,
I have a DELL Inspiron 1520 notebook with an Intel 3945abg wireless adapter.
Everyone who has this card knows that there is a bug for which the speed becomes capped at 100KB/s after a very short time of networking (with iwl3945 drivers).

This issue seems to be solved with compat-wireless package ( [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) ).

So I'd like to install this package in Ubuntu 9.04 Jaunty Jackalope.

If I try to install 2009-04-20 version, I cannot build it, as I get this error:

```
SDIO_DEVICE_ID_MARVELL_8688WLAN’ undeclared here
```

So I downloaded 2009-04-13 version which compiles well, but cannot install.

As I run

```
sudo make install
```

after some output, I get a message that loops infinitely:

```

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...mv: impossibile eseguire stat di "volatile/ath_pci.ko": Nessun file o directory
[ERROR]	Module is still being detected:
volatile/ath_pci.ko
```

Sorry for the Italian output, I think it can be easily understood.

I think everything could be solved disabling this module.

I hope someone could help me,
thanks.

---

### Post by puller on 2009-04-25
New details: the issue is not caused by compat-wireless install process, as if I run the command

```
sudo athenable madwifi
```

I get the same exact result, that is, this messages looping:

```
2 ath5k modules found we'll disable all of them
Disabling ath5k (1) ...mv: impossibile eseguire stat di "updates/drivers/net/wireless/ath5k/ath5k.ko": Nessun file o directory
[ERROR]	Module is still being detected:
updates/drivers/net/wireless/ath5k/ath5k.ko
Disabling ath5k (2) ...mv: impossibile eseguire stat di "updates/drivers/net/wireless/ath5k/ath5k.ko": Nessun file o directory
[ERROR]	Module is still being detected:
updates/drivers/net/wireless/ath5k/ath5k.ko
Disabling ath5k (3) ...mv: impossibile eseguire stat di "updates/drivers/net/wireless/ath5k/ath5k.ko": Nessun file o directory
[ERROR]	Module is still being detected:
updates/drivers/net/wireless/ath5k/ath5k.ko
Disabling ath5k (4) ...mv: impossibile eseguire stat di "updates/drivers/net/wireless/ath5k/ath5k.ko": Nessun file o directory

```

So what I need is disabling madwifi.
Will this cause errors?

It seems it is related to this topic: [http://ubuntuforums.org/showthread.php?t=1136849](http://ubuntuforums.org/showthread.php?t=1136849)

Output of modinfo ath_pci:
```

filename: /lib/modules/2.6.28-11-generic/volatile/ath_pci.ko
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

```

---

### Post by puller on 2009-04-25
Please, someone help!
I am capped at 100KB/s on a 8 Mbit/s connection.
It's frustrating!
Thanks.

---

### Post by chili555 on 2009-04-25
> Everyone who has this card knows that there is a bug for which the speed becomes capped at 100KB/s after a very short time of networking (with iwl3945 drivers).Everyone? I have this card and I don't know this. I've downloaded many an .iso, including Jaunty, and never experienced a slowdown, depending, of course, on the speed of the server.

Citation, please?

---

### Post by puller on 2009-04-25
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1570](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1570)

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1592](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1592)

These are the "official" topics, plus there are tons of forum posts about iwl3945 capping the download rate at 100 KB/s.

It has always happened to me since iwl3945 were introduced (since hardy).

For some periods I have used ndiswrapper to solve that.
Then I discovered that switching my ap to 802.11g only helped.

But I use my pc in two locations and where I am now, I cannot switch the access point to G mode only (I have B and G mixed).

The solutions seems to be compat-wireless, but I cannot install it.

The worst thing is not only I download files at 100 KB/s, but also that when I download something, any other networking operation becomes frustrating. Opening [www.google.com](www.google.com) lasts a decade.

Anyway, thank you very much for taking interest into it, I hope I could disable madwifi so the installation progress of compat-wireless continues!
Thanks.

---

### Post by chili555 on 2009-04-25
> These are the "official" topicsI apologize in advance if I missing the obvious, however, the bug reports you've linked are on the website of *intellinuxwireless.org*, the developer of the compat-wireless package itself. Aren't these bug reports concerning their own code? Why would you find bug reports there concerning the stock Ubuntu code? Moreover, the bug reports concern version 1.2.24 of the module; stock in the Jaunty install with *linux-backports-modules-jaunty-generic* installed is 1.2.26. Have you tried *backports*?

I am certainly not implying you don't have an issue; you surely do. However, I would try backports first.

I tried compat-wireless myself and managed to get past your error by fiddling, somewhat blindly, with the Makefile. However, when I tried to unload the old iwl3945 and load the compat-wireless, I got 'unresolved symbols' errors.

---

### Post by puller on 2009-04-26
> **chili555 said:**
> I apologize in advance if I missing the obvious, however, the bug reports you've linked are on the website of *intellinuxwireless.org*, the developer of the compat-wireless package itself. Aren't these bug reports concerning their own code? Why would you find bug reports there concerning the stock Ubuntu code? Moreover, the bug reports concern version 1.2.24 of the module; stock in the Jaunty install with *linux-backports-modules-jaunty-generic* installed is 1.2.26. Have you tried *backports*?

I am certainly not implying you don't have an issue; you surely do. However, I would try backports first.

I tried compat-wireless myself and managed to get past your error by fiddling, somewhat blindly, with the Makefile. However, when I tried to unload the old iwl3945 and load the compat-wireless, I got 'unresolved symbols' errors.

If I am not wrong, the bug is related with iwl3945 and comes in certain conditions (for example if at least once the link with the access point goes at 1 Mb/s). It may be that someone (as you), has never run into these conditions.

I tried linux-backports-modules-jaunty, but as I reboot, my wireless card (wlan0) disappears and I am not able to load the iwl3945 modules. It complaints about the wrong format of the file iwl3945.ko (or something similar).

If I uninstall backports and restart, than my wireless card works again with iwl3945 modules.

Maybe I had to load different modules from iwl3945 after installing backports?

When you tried compat-wireless, before editing the makefile, did you receive the same errors as I did?

Thank you very much for helping, I really appreciate!
V.

---

### Post by puller on 2009-04-26
I installed backports again to capture the error messages when loading modules.
Here it is:

```
puller@puller-laptop:~$ sudo modprobe iwl3945 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
WARNING: Error inserting iwlcore (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.28-11-generic/updates/lbm_cw-mac80211.ko): Invalid module format
FATAL: Error inserting iwl3945 (/lib/modules/2.6.28-11-generic/updates/iwl3945.ko): Invalid module format
```

It happens also with ath5k, ath_pci and maybe others!

---

### Post by puller on 2009-04-27
Installed ndiswrapper, networking works like a charm.
Cpu load always near maximun when downloading :(.

Worst solution as possible, but at least I can browse pages while downloading.

---

### Post by alkach on 2009-04-27
> **puller said:**
> ''''

Running athenable ath5k...
Disabling ath_pci ...mv: impossibile eseguire stat di "volatile/ath_pci.ko": Nessun file o directory
[ERROR]    Module is still being detected:
volatile/ath_pci.ko[/code]Sorry for the Italian output, I think it can be easily understood.

...

I've just renamed manually ath_pci.ko to ath_pci.ko.ignore in /lib/modules/2.6.28-11-generic/volatile then issued 'sudo make install'.

Don't forget to comment out 'blacklist ath5k' but leave uncommented 'blacklist ath_pci' in files located in '/etc/modprobe.d'.

You also may issue 'sudo depmod -a'.

Reboot.

Now ath5k works for me and (probably) you creating wlan0 and wmaster0 devices.

---

### Post by puller on 2009-04-27
> **alkach said:**
> I've just renamed manually ath_pci.ko to ath_pci.ko.ignore in /lib/modules/2.6.28-11-generic/volatile then issued 'sudo make install'.

Don't forget to comment out 'blacklist ath5k' but leave uncommented 'blacklist ath_pci' in files located in '/etc/modprobe.d'.

You also may issue 'sudo depmod -a'.

Reboot.

Now ath5k works for me and (probably) you creating wlan0 and wmaster0 devices.

Thank you very much, I managed to install it correctly!
The module to load with the 3945 card is ath5k?
Because if I load it the interface doesn't activate!
I have to load iwl3945 to activate it!

---

### Post by coolriver on 2009-05-11
> **puller said:**
> Thank you very much, I managed to install it correctly!
The module to load with the 3945 card is ath5k?
Because if I load it the interface doesn't activate!
I have to load iwl3945 to activate it!

I got the same error when "make install" compat-wireless,  (but I would use the driver zd1211rw).
Could you tell me how you managed to install it correctly? Thank you!

---

### Post by puller on 2009-05-11
> **coolriver said:**
> I got the same error when "make install" compat-wireless,  (but I would use the driver zd1211rw).
Could you tell me how you managed to install it correctly? Thank you!

I did exactly what alkach suggested to!
Anyway I didn't have this error using the latest compat-wireless package (I installed 2009-05-08).
So, if you are getting the error using the latest package, you should try alkach procedure.
You have to consider that if you rename that file, and then reboot, the file will get back its old name.
If you rename it, and then run make install, you shouldn't have issues!
Bye.

---

### Post by db260179 on 2009-05-11
Make sure the backports is not installed.

I've noticed a bug in the install script of compat-wireless, affects intrepid. NOT Jaunty

First edit this file scripts/modlib.sh - change the line

mv -f /lib/modules/$VER/$CHECK /lib/modules/$VER/${CHECK}${IGNORE_SUFFIX}

to

mv -f $CHECK ${CHECK}${IGNORE_SUFFIX}

The install script also doesnt detect the conflict of modules of mac80211.ko with lbm_cw-mac80211.ko and cfg80211.ko with lbm_cw-cfg80211.ko - remove the original mac80211.ko cfg80211.ko, then depmod -a

You will find it works after that!

> **puller said:**
> If I am not wrong, the bug is related with iwl3945 and comes in certain conditions (for example if at least once the link with the access point goes at 1 Mb/s). It may be that someone (as you), has never run into these conditions.

I tried linux-backports-modules-jaunty, but as I reboot, my wireless card (wlan0) disappears and I am not able to load the iwl3945 modules. It complaints about the wrong format of the file iwl3945.ko (or something similar).

If I uninstall backports and restart, than my wireless card works again with iwl3945 modules.

Maybe I had to load different modules from iwl3945 after installing backports?

When you tried compat-wireless, before editing the makefile, did you receive the same errors as I did?

Thank you very much for helping, I really appreciate!
V.

---

### Post by puller on 2009-05-11
> **db260179 said:**
> 

[...]

The install script also doesnt detect the conflict of modules of mac80211.ko with lbm_cw-mac80211.ko and cfg80211.ko with lbm_cw-cfg80211.ko - remove the original mac80211.ko cfg80211.ko, then depmod -a

[...]



First, thanks for the reply :)!
To translate in code what I quoted, I should type:

```

sudo rmmod mac80211
sudo rmmod cfg80211
sudo depmod -a

```

before running the installation?

Than at reboot I should use iwl3945 and it will be automatically the newly installed compat-wireless version?
Thanks.

---

### Post by db260179 on 2009-05-12
sudo rm -f /lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko
then
sudo rm -f /lib/modules/2.6.28-11-generic/kernel/net/wireless/cfg80211.ko

then

sudo rmmod mac80211
sudo rmmod cfg80211
sudo depmod -a
sudo modprobe iwl3945
To see if it works

> **puller said:**
> First, thanks for the reply :)!
To translate in code what I quoted, I should type:

```

sudo rmmod mac80211
sudo rmmod cfg80211
sudo depmod -a

```

before running the installation?

Than at reboot I should use iwl3945 and it will be automatically the newly installed compat-wireless version?
Thanks.

---

