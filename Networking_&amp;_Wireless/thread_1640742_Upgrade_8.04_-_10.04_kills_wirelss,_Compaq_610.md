---
title: "Upgrade 8.04 - 10.04 kills wirelss, Compaq 610"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-12-08
Hi all,

Strange. I upgraded today from 8.04 to 10.04 using the update manager. I'd never done it this way before, always just reinstalled, but everything worked fantastically, except for this anomoly.

Wireless was working faultlessly in 8.04. After the upgrade, cable works fine and lspci gives me this:

Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

So the system can still see the card. But have a look at this:

```
anna@katie:~$ sudo /etc/init.d/networking restart 
 [sudo] password for anna:  
  * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0. 
 wlan0: ERROR while getting interface flags: No such device 
 Error for wireless request "Set Encode" (8B2A) : 
     SET failed on device wlan0 ; No such device. 
 Error for wireless request "Set ESSID" (8B1A) : 
     SET failed on device wlan0 ; No such device. 
 SIOCSIFADDR: No such device 
 wlan0: ERROR while getting interface flags: No such device 
 SIOCSIFNETMASK: No such device 
 wlan0: ERROR while getting interface flags: No such device 
 Failed to bring up wlan0. 
```



... and this:


                      ```
anna@katie:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

... and Network Tools show no sign of wlan0 either.


So, using Network Manager (wicd no diff), running exactly the static IPs I had before but nothing. Doesn't see any access points, not just mine.

---

### Post by chili555 on 2010-12-08
Hey there, Bucky!

Let's do some diagnostics. Does the wireless card appear with a driver and an interface?```
sudo lshw -C network
```>  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: [COLOR="Red"]wlan0[/COLOR]
       version: 02
       serial: **:19:d2:c2:1b:**
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR]Is the awful word DISABLED there? If so, is it because the hardware switch is switched to 'Off?'```
rfkill list all
```Or is this a Dell?```
lsmod | grep dell
```

---

### Post by Bucky Ball on 2010-12-08
Hey there. Compaq 610.

```
anna@katie:~$ sudo lshw -C network
[sudo] password for anna: 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-e8000fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth0
       version: 10
       serial: 00:26:55:c3:96:66
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.0.109 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:e0000000-e0003fff ioport:2000(size=256)
```Yep, there it is. 'UNCLAIMED' and no driver; dead. Hmm. Has a single button for wireless and that is on and blue, as per normal. No response to:

```
rfkill list all
```

---

### Post by chili555 on 2010-12-08
The driver ought to grab the card automagically; if it's not, there may be something else wrong. Let's see what result of:```
sudo modprobe iwl3945
dmesg | grep iwl
```Thanks.

---

### Post by Bucky Ball on 2010-12-08
Good morning! I'm back. Here we go ...

```
anna@katie:~$ sudo modprobe iwl3945
WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Error inserting iwl3945 (/lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```I had a look for all the files listed here and they are all present and correct.

```
anna@katie:~$ dmesg | grep iwl
[   18.278520] iwl3945: Unknown parameter `hwcrypto'
[   18.625802] iwl3945: Unknown parameter `hwcrypto'
[   20.122039] iwl3945: Unknown parameter `hwcrypto'
[   20.164456] iwl3945: Unknown parameter `hwcrypto'
[   20.202010] iwl3945: Unknown parameter `hwcrypto'
[   20.233619] iwl3945: Unknown parameter `hwcrypto'
[   20.271092] iwl3945: Unknown parameter `hwcrypto'
[   20.308435] iwl3945: Unknown parameter `hwcrypto'
[   20.341217] iwl3945: Unknown parameter `hwcrypto'
[   20.381255] iwl3945: Unknown parameter `hwcrypto'
[   20.411573] iwl3945: Unknown parameter `hwcrypto'
[  138.661073] iwl3945: Unknown parameter `hwcrypto'
[  151.491207] iwl3945: Unknown parameter `hwcrypto'
```This has been popping up as an error message at boot, but then all goes okay. Actually, cold boot is fine, fan works great (better than 8.04) but on a restart fan blasts off and I have to switch machine off as really hot and fan going crazy. Related? Probably not.

BTW, thanks for the help Chilli555. ;)

---

### Post by chili555 on 2010-12-08
> All config files need .conf: /etc/modprobe.d/[COLOR="Red"]iwl3945[/COLOR], it will be ignored in a future release.
Uh, oh! What have you done to the poor little driver? Let's have a peek. Please post:```
cat /etc/modprobe.d/iwl3945
```Thanks.

---

### Post by Bucky Ball on 2010-12-08
From post #4 here:

[http://ubuntuforums.org/showthread.php?t=642524&highlight=4965](http://ubuntuforums.org/showthread.php?t=642524&highlight=4965)

In /etc/modules:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
snd-hda-intel
iwl3945
```

... and in /etc/modprobe.d I find:

```
iwl3945
```

Not 

```
blacklist-iwl3945
```

---

### Post by Bucky Ball on 2010-12-08
> **chili555 said:**
> Uh, oh! What have you done to the poor little driver? 

Nothing, honest! :) I just upgraded through the Update Manager in 8.04 ... the upgrade did the rest.

It was like this when I found it, honest!!! lol

```
anna@katie:/etc/modprobe.d$ cat /etc/modprobe.d/iwl3945
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```Ah, ha! That looks like clues. hwcrypto should = 0? Should disable_hw_scan=0 also?

* EDIT: Hold on. This page:

[http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/](http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/)

... reckons the above is right and I should enable '*linux-backports-modules-hardy-generic'. *Is there another way? The post is from 2008 ...

In Software Sources there are a few that have been disabled with the upgrade (it tells me so).

---

### Post by chili555 on 2010-12-08
It may have been correct in 2008, but not now.> $ modinfo iwl3945
filename:       /lib/modules/2.6.35-23-generic/updates/compat-wireless-2.6.36/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     948AADC82A55752A4D177C0
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           fw_restart3945:restart firmware in case of error (int)As you can see, hwcrypto is not a loadable parameter. What were you trying to fix with these parameters? If it were my computer, and I do have an Intel 3945ABG, I'd remove the file altogether and see what the result is. If needed, we can add the correct parameters to fix an issue later on.```
sudo rm /etc/modprobe.d/iwl3945
```Reboot and give me yor report.

---

### Post by Bucky Ball on 2010-12-08
> **chili555 said:**
> ... As you can see, hwcrypto is not a loadable parameter. What were you trying to fix with these parameters? 

Nothing. Haven't touched 'em. Only reporting what I see. Have changed nothing.

I will try removing file as suggested.

---

### Post by Bucky Ball on 2010-12-08
You, chilli555, are a legend! That worked!

Removed iwl3945, rebooted and first time just sat there at the 'Ubuntu' splash screen. Shutdown, reboot, all systems go!
Connected to my wireless without me doing anything and I post to you now via the wireless connection. Maybe the upgrade threw that file in there. Who knows?

Thanks a billion. Will give it a few hours just to make sure then mark this thread as solved. Ubuntu community is the best! ;)

I have to say, this machine is running a treat after the upgrade. Fan was always on at a constant speed. Now it seems to have control and goes on and off appropriately, steady, low temp.
Strange though, as I mentioned earlier: Forget the restart. When I restart the fan runs flat out but I can live with that for now. Just shutdown rather than restart. The upgrade is on my wife's machine while she is away for a week (the only time to do it) and everything is working good and she doesn't tweak at all so not much cause for restarts anyhow.

Thanks one more time (and probably not the last).

---

### Post by chili555 on 2010-12-08
Glad to help! Call on us any time. I'm glad it's working.

---

### Post by Bucky Ball on 2010-12-08
Cheers, mate. :)

---

### Post by Bucky Ball on 2010-12-09
Skype is now totally non-functional I discover. Fresh install in future. These upgrades seem to be problematic; the reason I have avoided after attempting it once a couple of years ago. Will post a new thread regarding Skype and see how I go. Thanks again, chilli man. :)

---

### Post by chili555 on 2010-12-09
You might try completely removing, including configuration files, and then re-install. You may lose your contacts.

---

### Post by Bucky Ball on 2010-12-10
Was thinking of that. I figure maybe new version in 10.04 not happening with old config files. Cheers. Off for some lawn bowls and beers now but will report back.

---

### Post by Bucky Ball on 2010-12-15
Just a note re. sound on Skype. The sound didn't work on anything. But ... system showing no signs of a problem; eg sound recorder or Skype test call. So I unplug the USB headset and sound in and out fine through external speakers and mic. Plug in my regular mini-jack headset and all working perfectly.

The USB headset prob was the same I was having in 8.04 but got that working. With the updated Pulse etc., the goalposts have changed and that fix isn't working anymore. Anyway, it's do-able, but will do some more research and perhaps post with more detail when I get around to it. You might have a few clues.

Just thought I'd mention it ...

---

