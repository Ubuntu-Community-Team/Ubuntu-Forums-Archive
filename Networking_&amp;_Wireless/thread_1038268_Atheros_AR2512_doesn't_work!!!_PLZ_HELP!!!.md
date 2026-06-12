---
title: "Atheros AR2512 doesn't work!!! PLZ HELP!!!"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by tee4cute on 2009-01-12
I upgraded ubuntu from 8.04 to 8.10. First, I used madwifi driver in ubuntu 8.04 and everything is fine (except that wireles LED does not work, I'd worked around for installing backports modules and it is better). Then I upgraded ubuntu to 8.10 and everything is OK!.

I found that ubuntu 8.10 has built-in driver named "ath5k" and I prefer to use it. So I uninstall the madwifi driver by run the script "make uninstall" in madwifi source package and "script/find-madwifi-modules -r" to remove all madwifi modules from system.

I googled around and found that I had to fixed some modprobe blacklist in "/etc/modprobe.d". Then, I uncommented the "blacklist ath5k" and commented out the "ath_pci" and "ath_hal" for not loading the madwifi module.

I added "ath5k" at the end of file "/etc/modules" to automatically load everytime I reboot.

Here's my lsmod :

lsmod | grep "ath5k"
ath5k                 106496  0 
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 ath5k,thinkpad_acpi

But I can't access the wireless because the system does not found the wireless card. (lshw & lspci does not show the wireless card in there!)

Anyone can help me?? plz!!!

---

### Post by tee4cute on 2009-01-12
I'm sorry for mistake in the topic. The wireless card is "Atheros AR5212" not "Atheros AR2512".

blame me >.<.

---

