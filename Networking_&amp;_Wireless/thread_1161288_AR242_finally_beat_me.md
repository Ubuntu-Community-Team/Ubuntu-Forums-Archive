---
title: "AR242 finally beat me"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by nothingspecial on 2009-05-16
Running 9.04, I`ve done no updates.

What I have done today is moved my /home to a different partition. Installed zenwalk 6 on another partition sharing the same /home. Then during my wireless hell removed it and installed 8.04 to it.

Has this cocked up my wireless some how? Can`t see why myself.

I have tried #ing ath_pci in /etc/modprobe.d/blacklist-ath_pci.conf and blacklisting ath5k.

I`ve tried compiling the latest madwifi and using that instead.

I`ve since, as far as possible, put it all back the way it was.

dmesg reads
```

[  108.100249] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  108.447573] ath5k phy0: gain calibration timeout (2412MHz)
[  108.447583] ath5k phy0: can't reset hardware (-11)
[  108.801666] ath5k phy0: gain calibration timeout (2412MHz)
[  108.801676] ath5k phy0: can't reset hardware (-11)
[  127.721957] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  242.700822] Monitor-Mwait will be used to enter C-2 state
[  242.716007] Marking TSC unstable due to TSC halts in idle
[  527.825852] ath5k phy0: gain calibration timeout (2412MHz)
[  527.825869] ath5k phy0: can't reset hardware (-11)
```
 
```
sudo This computer is a ******g ***t make the ******g wireless work now
```
 gives
```
bash: This: command not found
```

I hope to be put firmly in my place as a complete hopeless amateur. Can you do this for me.

Thanks

***EDIT***As I look down the threads in this forum it would seem I am not alone, maybe I did do an update ...... don`t remember doing but then I can`t remember what I had for tea last night.......but that was because the wife was out and I could drink as much beer as I wanted.......oh yeah it was chinese (king prawn something) ........ I still don`t remember updating though.***EDIT***

****EDIT*** It seems adding ath5k to /etc/modules does it, how was I supposed to know that****EDIT****

---

