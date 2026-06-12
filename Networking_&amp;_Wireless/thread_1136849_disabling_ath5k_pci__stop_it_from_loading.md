---
title: "disabling ath5k_pci / stop it from loading"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by planetLars on 2009-04-25
Hello,

where can I disable the ath5k_pci driver so that it doesn't start?

My AP can be connected to but data transfer rates are low. No website is displayed, the best I get after 5 minutes is the HTML Head Title being displayed.

I have an AR2425 (Atheros 5007EG) wifi chipset in my notebook. The MadWifi 0.10.56 snapshot used to work for me in Ubuntu 8.04.

Happy New Year Jaunty! Welcome to the masses.


Lars

---

### Post by t0mppa on 2009-04-25
For me, I actually had the same snapshot installed in 8.10 and when I upgraded, it still continued functional. lsmod showed both ath5k and it being loaded on first boot, but wireless still worked without trouble.

If you still have the MadWifi snapshot file lying around, you'll find a scripts directory inside the archive with the following content: ```
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ ls
find-madwifi-modules.sh  hal_unmangle.sed         make-release.bash
get_arch.mk              if_ath_hal_generator.pl  update_hal_unmangle
hal_unmangle_log         madwifi-indent
hal_unmangle.objcopy     madwifi-unload

```

The find-madwifi-modules.sh and madwifi-unload should clean up your kernel of any madwifi traces, of course that means you'll have to install something new to do the job of wireless drivers.

---

### Post by puller on 2009-04-25
> **t0mppa said:**
> For me, I actually had the same snapshot installed in 8.10 and when I upgraded, it still continued functional. lsmod showed both ath5k and it being loaded on first boot, but wireless still worked without trouble.

If you still have the MadWifi snapshot file lying around, you'll find a scripts directory inside the archive with the following content: ```
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ ls
find-madwifi-modules.sh  hal_unmangle.sed         make-release.bash
get_arch.mk              if_ath_hal_generator.pl  update_hal_unmangle
hal_unmangle_log         madwifi-indent
hal_unmangle.objcopy     madwifi-unload

```

The find-madwifi-modules.sh and madwifi-unload should clean up your kernel of any madwifi traces, of course that means you'll have to install something new to do the job of wireless drivers.


Could it be the solution for this issue ( [http://ubuntuforums.org/showthread.php?t=1136870](http://ubuntuforums.org/showthread.php?t=1136870) ) too?

---

### Post by planetLars on 2009-04-25
Hi,

I did as you suggested (it's the same as described in the MadWifi How-To). I did this several times too in the past because every now and then the driver lost some dependancies or sth. like this.

ath5k_pci still loads and is used by Ubuntu Jaunty I'm using.

Even if I cannot avoid ath5k_pci loading, how can I instruct Ubuntu to use ath_pci?

I'm using the April 2009 snapshot of .56. Seems they are still updating it though they not plan to release another MadWifi stable. I don't have my August 2008 or whenever it was .56 snapshot anymore.

Thanks!


Lars

---

### Post by planetLars on 2009-04-25
update:

blacklisting ath5k_pci didn't stop ath5k_pci from loading.

de-blacklisting ath_pci wouldn't haven been necessary as it loaded already but I did that too: no difference.

Lars

---

