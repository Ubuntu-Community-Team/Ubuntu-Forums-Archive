---
title: "WPA problems on Toshiba Satellite A15"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by codyduncan on 2010-01-10
Anyone feel like helping me to enable WPA encryption on my wireless connection?  Wireless networks are detected and listed, so the wireless card is functional in the most basic sense, however, when going to connect to any particular network, I am not given the option of entering a WPA passphrase, only WEP, and as my router is set to use WPA, this is a problem.  I am trying to get this going on a fresh Karmic install on a Toshiba A15-S157 notebook.  Thus far, I have found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315489](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315489) which would seem to relate to my problem.
I looked in my logs and saw this entry:
Jan 10 16:06:35 cody-laptop firmware.sh[863]: Cannot find  firmware file 'agere_sta_fw.bin', and have since found that file, and have downloaded it to my desktop.  It seems like this may be the solution, but how to exact it, therein lies my (momentary) problem.

---

### Post by codyduncan on 2010-01-11
Basically, I am just looking for where to put the firmware file, as I think that should take care of it.

EDIT:

Okay, I placed the file into my lib firmware file, and it seemed to get me one step closer, but still, no dice.  I checked my log file, and it read this:

Jan 11 19:22:17 cody-laptop NetworkManager: <info>  (eth1): supplicant connection state:  associating -> disconnected
Jan 11 19:22:17 cody-laptop NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Jan 11 19:22:17 cody-laptop wpa_supplicant[776]: CTRL-EVENT-SCAN-RESULTS 
Jan 11 19:22:17 cody-laptop wpa_supplicant[776]: Trying to associate with 00:0c:e5:4a:1e:f6 (SSID='Coca Cola Bottle' freq=2462 MHz)
Jan 11 19:22:17 cody-laptop NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Jan 11 19:22:17 cody-laptop wpa_supplicant[776]: Association request to the driver failed
Jan 11 19:22:17 cody-laptop kernel: [ 2299.713598] eth1: Lucent/Agere firmware doesn't support manual roaming
Jan 11 19:22:22 cody-laptop NetworkManager: <info>  eth1: link timed out.

and so on as I tried multiple times.  What's going on here?

---

### Post by codyduncan on 2010-01-12
I reinstalled ubuntu (this time, I went back to Hardy.  Karmic was an experiment for me, but I rather like being able to change sound schemes, and as such, made the switch back), but am still having the same problem.

---

