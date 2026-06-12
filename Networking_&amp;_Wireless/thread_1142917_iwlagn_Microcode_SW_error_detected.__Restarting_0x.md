---
title: "iwlagn: Microcode SW error detected.  Restarting 0x82000000."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by dr_doom on 2009-04-29
Hello,

These days I've tried the new Ubuntu 9.04, but I've found that my Intel PRO/Wireless 5100AGN card is not working with encryption.
If is turn of the encryption on my AP, I'm able to establish a wireless connection, The problem is when I use and encryption I'm getting and error:
iwlagn: Microcode SW error detected.  Restarting 0x82000000.

I see that this error seems quite popular with intel wireless cards.

I am surprised because more than 3 months I was using Kubuntu 8,10 and all the time I've used my wifi with WPA-PSK encryption enabled and never had such kind of problem.

These days I've tried the following versions:
Ubuntu 9.04
Ubuntu 8,10
Kubuntu 9,04
Kubuntu 8,10

The result was that the iwlagn wifi is working perfectly only on Kubuntu 8,10.
At least it should work on Ubuntu 8.10, but I've got the same error there.

When I've upgraded from Kubuntu 8.10 to Kubuntu 9.04, of course the wifi stopped to work again. I've tied even to rollback the 8.10 packages of wpa_supplicant, network-manager and network-manager-kde and also to boot with the kernel build for Kubunto 8.10, but still the same problem.

---

### Post by chili555 on 2009-04-29
I saw this: [https://bugs.launchpad.net/linux/+bug/200509](https://bugs.launchpad.net/linux/+bug/200509) and especially the last post:> 

I had the same issue on Jaunty with every kernel I tried (2.6.28,2.6.29,2.6.30rc3). I found a suggestion given at:

[http://www.fell.it/2009/02/18/microcode-swhw-error/](http://www.fell.it/2009/02/18/microcode-swhw-error/)

My wireless is running smoothly since then. I need to do more testing, but so far so good. To summarize, you need to do:

echo 5 > /sys/bus/pci/drivers/iwlagn/0000\:0c\:00.0/power_level

replacing 0000\:0c\:00.0 with your entry. Please see the above link for the details.
Please try this and let us know the result. In order to echo into /proc, you will probably need to precede the command with 'sudo su' and your password.

---

### Post by Zorael on 2009-04-29
> **chili555 said:**
> In order to echo into /proc, you will probably need to precede the command with 'sudo su' and your password.
Or use tee, to avoid being root any more than absolutely necessary. :3
```
$ echo 5 | sudo tee /sys/bus/pci/drivers/iwlagn/0000\:0c\:00.0/power_level
```

---

### Post by dr_doom on 2009-05-01
Hi,

thanks for the reply.
Unfortunately this didn't solve the problem.
According to the information how the guy has been solved the problem when changing the power I see that at least he is able to connect.
The problem in my case is that I'm not able to connect at all when I use encryption.
For any kind of encryption the NetworkManager in ubuntu use wpa_supplicant.

---

### Post by dr_doom on 2009-05-01
The problem was resolved with the installation of kernel 2.6.29.2.
Now the wireless controller is connected to my AP with WPA-PSK encryption enabled.
I don't see anymore the **Microcode SW error** in syslog.

---

### Post by madomac on 2009-05-15
I experience the same problems over here. How did you upgrade to 2.6.29.2? Compiled the "vanilla" kernel yourself?

Thanks,
Marc

---

### Post by waldeck on 2009-09-19
I have a Sony Vaio VGN-NW130J and it shows the same problem. What seems to help is to let the card manage the power levels on its own, which is done with a command like:
```
iwconfig wlan1 power on
```
I wrote a little script to have this done automatically every time the interface comes up:
```
#!/bin/bash 
if [ "${IFACE}" == "wlan1" ]
then
  if [ "${MODE}" == "start" ]
  then
    # Let the hardware choose the power level instead of using
    # a constant (high) power level, since it is causing the card to overheat
    iwconfig ${IFACE} power on
  fi
fi
``` which I placed in the /etc/network/if-up.d folder. It is a good idea not to forget to issue a chmod +x on the script.

I also did a microcode upgrade from [Intel](http://intellinuxwireless.org/?p=iwlwifi&n=downloads).

Hope this will be helpful.

---

### Post by DantePasquale on 2009-10-05
I am seeing these types of firmware problems, but only when transferring large files -- using imapsync to backup mailboxes to a wireless laptop. But I get Restarting 0x20000000, not 0x82000000.

Dumb question on microcode upgrade. What's best way to determine current microcode? 

modinfo shows:
```
modinfo iwlagn | more
filename:       /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5000-1.ucode
srcversion:     FBAB418B0B80EA1E606EB1E
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.28-15-generic SMP mod_unload modversions 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```

also:
```
modinfo iwlcore
filename:       /lib/modules/2.6.28-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27k
description:    iwl core
srcversion:     0F11AA34166B2C1987F9966
depends:        mac80211,led-class,cfg80211
vermagic:       2.6.28-15-generic SMP mod_unload modversions
```

Thanks, Danté

---

### Post by patelkaushik on 2012-12-25
Hi Team,

I am also facing the same problem of "Microcode SW error detected". 
>uname -a 
Linux <org.specific> 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

> lspci -nn |grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)

I know that the problem is solved with the Kernel version >=3.4 but the problem is that i can not upgrade kernel because most of the software are generalized with this kernel version. 
If i use the following commands then wifi starts working on one router :
>sudo modprobe -r iwlagn;
>sudo modprobe iwlagn 11n_disable=1
But not be able to connect to other router. 
Please help me in solving this issue.

---

### Post by papibe on 2012-12-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

