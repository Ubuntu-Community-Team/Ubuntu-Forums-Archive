---
title: "Disable wireless activity LED for 12.10"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by bdrieck on 2012-11-25
Brand new to Ubunto. installed it on a dead windows laptop and brought it back to life. I love Ubunto!!  I have NO experience in Ubunto or the terminal.  I'm not afraid to try and learn. the led that shows my wireless adapter is turned on blinks with internet activity. prior to this the light would stay solid blue when on and now it blinks.  It is annoying to me.  I've searched and found countless threads about this issue but with the older versions of Ubunto 12.04 and prior.  My wireless adapter is: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

again as I am as new to this as anyone can get if somone could walk me through trying to fix this I would greatly appreciate it.

thank you !!

---

### Post by chili555 on 2012-11-25
We are going to try a conf file and see if it helps. Please do:```
sudo gedit /etc/modprobe.d/iwlegacy.conf
```A new empty file will open. Add one line:```
options iwlegacy led_mode=1
```Proofread, save and close gedit. Now, let's try it immediately:```
sudo modprobe -r iwl3945
sudo modprobe iwlegacy led_mode=1
sudo modprobe iwl3945
```Any improvement?

---

### Post by bdrieck on 2012-11-26
Thank you Chili! seems to have worked. in laymans terms can you describe what I did by typing the first code and opening up the file and entering the 1 line?  then what happed when I entered the next 3 codes in? after entering the first 2 codes:

sudo modprobe -r iwl3945
sudo modprobe iwlegacy led_mode=1

I got messages warning messages about ignroing lines and options.I don't expect you to teach me Ubunto/linux in this thread. Just curious as to how this works?  

thanks again for your help.

---

### Post by chili555 on 2012-11-26
> I got messages warning messages about ignroing lines and options.We ought to take a look and see if we need to tweak something. Please repeat the sequence and copy and paste the messages in a text editor so you can post them here.

Your wireless driver is iwl3945:> **I**ntel Corporation PRO/**W**ire**l**ess **3945**ABG [Golan] Network Connection (rev 02)I also know because I have one! According to modinfo, it offers no parameter for LED behavior:> chili@LAPTOP410:~$ modinfo iwl3945
filename:       /lib/modules/3.5.0-18-generic/updates/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     80804B2CEB446EB841C50E2
<snip>
[COLOR="Red"]depends:        iwlegacy,cfg80211,mac80211,compat[/COLOR]
vermagic:       3.5.0-18-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)So we check its dependencies, first iwlegacy:> chili@LAPTOP410:~$ modinfo iwlegacy
filename:       /lib/modules/3.5.0-18-generic/updates/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     D6EAA979AA8BED8E604117E
depends:        mac80211,cfg80211
vermagic:       3.5.0-18-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)[/COLOR]
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)Bingo! So we unload the driver iwl3945 with modprobe -r which takes the whole family, including iwlegacy with it. We reload iwlegacy with a driver parameter and reload the driver. It works! 

Our conf file instructs the system to load iwlegacy with the LED parameter automagically every time it's loaded. 

Post those warnings, please and we'll do some housekeeping.

---

