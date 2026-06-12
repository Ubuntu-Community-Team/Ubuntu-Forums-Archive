---
title: "wifi dropouts aspire one A150"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by kellyhardinguk on 2009-07-03
Having installed Netbook Remix, 9.04 on my Aspire One A150, my wifi seems under heavy load to drop out constantly.

Tried adding acer_wmi to blacklist, but had no effect (as recommended here: [https://help.ubuntu.com/community/AspireOneDiscussion](https://help.ubuntu.com/community/AspireOneDiscussion)).

Any ideas?

Further information Added:
linux-backports-modules-jaunty
lspci gives the card as a Atheros AR242x.

I'm using WPA2/TKIP, Wirelss G using a Linksys WRT54GC router.

Am using the 2.6.28-13 kernel.

Modules related to wifi (ath5k driver) seem to be (according to lsmod):

ath5k
lbm_cw_mac80211
led_class

As recommened elsewhere to get the LED working I installed the package: linux-backports-modules-jaunty

Can provide further information as needed.

---

### Post by whorobj on 2009-07-03
in for this

---

### Post by kellyhardinguk on 2009-07-04
Going back to 2.6.28-11 didn't fix it.

Neither did blacklisting ath_pci or ath_hall.

Get 'Currupted MAC on input' also when transferring by SFTP, not sure if thats related.

---

### Post by superprash2003 on 2009-07-04
read this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by kellyhardinguk on 2009-07-04
> **superprash2003 said:**
> read this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

Thanks, a few pointers there, will try a few of them and see if it fixes my problems.

---

### Post by kellyhardinguk on 2009-07-04
Tried the pointers on that post, none so far seem to resolve this.

Tried .31-rc1 kernel, as well as .30 and .29 kernels, and none of those fix the problems (.29 and .30 make it worse!).

So now I think I'm going to try seeing if madwifi will work and fix the issue. Failing that other suggestion seems to be Wicd.

---

### Post by kellyhardinguk on 2009-07-04
madwifi-hal seems to have mostly solved problems. Rest of problems I now suspect might be range/signal related.

---

