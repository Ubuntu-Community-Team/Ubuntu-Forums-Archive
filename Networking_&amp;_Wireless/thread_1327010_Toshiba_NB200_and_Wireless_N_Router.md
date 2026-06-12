---
title: "Toshiba NB200 and Wireless N Router"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2009-11-15
I've been frustrated over the last day or so trying to get a [Toshiba NB200 and HP 1033 netbook]("http://ubuntuforums.org/showthread.php?t=1325887&highlight=NB200") to connect to our home and my office's network. Both  of these are on fairly recent Belkin "N" routers.

Despite the hardware being present and the networks clearly visible to the computers I could not coax them to connect, even with the network open and unsecured. Under WinXP there is no issue.

Anyway, using the lowest common denominator tactic, I thought maybe the wireless "N" routers were the problem.

So I revived an older wireless "g" network router.

Bingo. Both netbooks connected almost instantly.

So, is that the way it is? I mean, there is no way that we're going back to wireless "g" routers, especially in the office.

NB: Most of the office PCs use Windows or Macbooks. Linux is the exclusive domain of masochistic idiots like yours truly ;)

ANy suggestions for another cure?

---

### Post by Fir3chi3f on 2009-11-15
I was thinking maybe the drivers your using with your netbook might not support wireless N standard. If you go to System -> Administration -> Hardware Drivers what is listed? other wireless drivers?

If you use the new router but set it to wireless g only does it help any?

---

### Post by GuiGuy on 2009-11-15
> **Fir3chi3f said:**
> I was thinking maybe the drivers your using with your netbook might not support wireless N standard. If you go to System -> Administration -> Hardware Drivers what is listed? other wireless drivers?

That doesn't list any drivers, but the NB200 uses an atheros  AR9285 adaptor.

In any case, the  Belkin router tells me it is in 802.1b&802.1g&892.1n transmission mode. Other wireless g based PCs have no trouble connecting to it.


> 
If you use the new router but set it to wireless g only does it help any?

No.I've tried 'b' as well with no luck.

---

### Post by GuiGuy on 2009-11-15
As a further update, dmesg is giving me this on wlan0
> 
[   14.113956] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.374734] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[   69.378070] wlan0: authenticated
[   69.378081] wlan0: associate with AP 00:1b:2f:78:cc:42
[   69.381677] wlan0: RX AssocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[   69.381688] wlan0: associated
[   69.382584] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.048111] wlan0: no IPv6 routers present
[  147.829111] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[  149.030320] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[  149.034164] wlan0: authenticated
[  149.034178] wlan0: associate with AP 00:1b:2f:78:cc:42
[  149.039580] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[  149.039592] wlan0: associated
[  162.988116] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[  164.169351] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[  164.173754] wlan0: authenticated
[  164.173772] wlan0: associate with AP 00:1b:2f:78:cc:42
[  164.177929] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[  164.177946] wlan0: associated
[  172.824111] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[  174.023279] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[  174.029076] wlan0: authenticated
[  174.029093] wlan0: associate with AP 00:1b:2f:78:cc:42
[  174.033883] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[  174.033900] wlan0: associated
[  182.824142] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[  184.013352] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[  184.016820] wlan0: authenticated
[  184.016836] wlan0: associate with AP 00:1b:2f:78:cc:42
[  184.022628] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[  184.022646] wlan0: associated
[ 4962.996124] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[ 4964.181881] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[ 4964.185383] wlan0: authenticated
[ 4964.185401] wlan0: associate with AP 00:1b:2f:78:cc:42
[ 4964.191496] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[ 4964.191514] wlan0: associated
[ 5273.084102] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[ 5274.264184] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[ 5274.266837] wlan0: authenticated
[ 5274.266854] wlan0: associate with AP 00:1b:2f:78:cc:42
[ 5274.270378] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[ 5274.270394] wlan0: associated
[ 7673.008173] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[ 7674.201812] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[ 7674.400054] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[ 7674.402054] wlan0: authenticated
[ 7674.402066] wlan0: associate with AP 00:1b:2f:78:cc:42
[ 7674.405164] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[ 7674.405177] wlan0: associated
[ 9772.988142] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[ 9774.166476] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[ 9774.169454] wlan0: authenticated
[ 9774.169465] wlan0: associate with AP 00:1b:2f:78:cc:42
[ 9774.174812] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[ 9774.174823] wlan0: associated
[10399.537081] wlan0: no probe response from AP 00:1b:2f:78:cc:42 - disassociating
[10400.714801] wlan0: authenticate with AP 00:1b:2f:78:cc:42
[10400.716813] wlan0: authenticated
[10400.716831] wlan0: associate with AP 00:1b:2f:78:cc:42
[10400.719623] wlan0: RX ReassocResp from 00:1b:2f:78:cc:42 (capab=0x471 status=0 aid=1)
[10400.719641] wlan0: associated


Is this normal?

---

