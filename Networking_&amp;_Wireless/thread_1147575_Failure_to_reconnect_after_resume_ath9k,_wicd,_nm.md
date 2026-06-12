---
title: "Failure to reconnect after resume: ath9k, wicd, nm"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Rog-Mahal on 2009-05-03
So I'm running Jaunty in a dual boot with OS X on a MacBook 2,1. Apparently OS X 10.4.11 broke support for wpa2, which was working fine with my new install of Jaunty. I switched to wpa and OS X is working fine, but now I have a problem with wireless connectivity in Ubuntu. 

I searched through some bug reports, and some people had success by installing wicd and using the jaunty-backports package. Unfortunately neither of those options have worked for me. Ubuntu connects fine from a cold boot or restart, but not on waking from suspend. Modprobing the ath9k module does nothing.

In wicd, there are several different wpa supplicant drivers(?) that I can choose from. wext stalls on "validating authorization" and  ralink legacy stalls on "obtaining IP address"

In network-manager I would just be asked repeatedly for the wpa password, and it would never connect. 

Here's the dmesg output from resuming from suspend to failure to connect:

```
[ 7485.113666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7485.168080] sky2 eth0: disabling interface
[ 7485.177998] sky2 eth0: enabling interface
[ 7485.178692] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7493.764814] wlan0: authenticate with AP ffff88007c5d5ac0
[ 7493.964093] wlan0: authenticate with AP ffff88007c5d5ac0
[ 7493.976207] wlan0: authenticated
[ 7493.976213] wlan0: associate with AP ffff88007c5d5ac0
[ 7494.078340] wlan0: RX AssocResp from ffff88007cd9010a (capab=0x431 status=0 aid=4)
[ 7494.078347] wlan0: associated
[ 7494.082886] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7498.300092] wlan0: deauthenticating by local choice (reason=3)
[ 7498.445652] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7498.497066] wlan0: deauthenticating by local choice (reason=3)
[ 7498.573602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7502.383569] wlan0: direct probe to AP ffff88007c5d5ac0 try 1
[ 7502.476222] wlan0 direct probe responded
[ 7502.476228] wlan0: authenticate with AP ffff88007c5d5ac0
[ 7502.576211] wlan0: authenticated
[ 7502.576218] wlan0: associate with AP ffff88007c5d5ac0
[ 7502.676228] wlan0: RX AssocResp from ffff880030c1410a (capab=0x421 status=0 aid=545)

```

Any help would be appreciated, the bug reports haven't offered any help. I also didn't have these problems with 8.10.

---

### Post by pi3832 on 2009-05-03
Not that there's much help to be had from it, but have you seen the Bugzilla bug on this?

[http://bugzilla.kernel.org/show_bug.cgi?id=12958](http://bugzilla.kernel.org/show_bug.cgi?id=12958)

---

### Post by Rog-Mahal on 2009-05-03
Yup, I was trawling on bugzilla and launchpad, that's where I got the suggestion to try wicd and the jaunty-backports package. Unfortunately I haven't found a solution.

Would it make any difference if I am using just WPA as opposed to WPA2?

---

### Post by pi3832 on 2009-05-03
@

---

