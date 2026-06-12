---
title: "ubuntu meerkat 10.10 32-bit regression: freezes on wireless atheros ath9k"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by sam_vde on 2011-01-11
I have been running Ubuntu 10.04 without any issue on a Compaq 311 Mini with an Atheros wireless adapter.

From lspci:
> 03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

After upgrading (fresh install) to 10.10 I noticed my system became unstable:
- boot process randomly freezes just before X starts
- shutdown process hangs
- suspend/resume freezes system, mostly on resume but also on suspend
- sometimes random freezes when working on the netbook

It seems the key moment where things go bad is always the point where the wireless adapter changes state. I read in various posts on the internet I am not the only one having these issues (e.g. on of the later ones: [https://bugs.launchpad.net/fedora/+bug/426130](https://bugs.launchpad.net/fedora/+bug/426130)) but somehow I couldn't trace anyone really working this bug.

As I fear to end up with corrupted filesystems one day, I think this issue should be adressed.

At this moment I installed the backport wireless modules for Meerkat: 
> sudo aptitude install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
which does not solve the issue, but makes it better. My system does not freeze anymore unless I suspend it.

To prove it uses the newer driver, a modinfo extract:
> $ modinfo ath9k
filename:       /lib/modules/2.6.35-24-generic/updates/compat-wireless-2.6.36/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     863149DA40B3001B11EB9F6
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,led-class,ath,cfg80211,ath9k_common
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)


A snippet from syslog the last time it froze because I tried to suspend it (anonymised the stuff in **bold**):
> Jan 11 04:00:05 dartagnan NetworkManager[1333]: <info> (wlan0): taking down device.
Jan 11 04:00:05 dartagnan avahi-daemon[1336]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 11 04:00:05 dartagnan avahi-daemon[1336]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c617:**0000:0000:0048**.
Jan 11 04:00:05 dartagnan avahi-daemon[1336]: Withdrawing address record for fe80::c617:**0000:0000:0048** on wlan0.
Jan 11 04:00:05 dartagnan NetworkManager[1333]: <info> (18:86:AC:25:**00:33**): now unmanaged
Jan 11 04:00:05 dartagnan NetworkManager[1333]: <info> (18:86:AC:25:**00:33**): device state change: 3 -> 1 (reason 37)
Jan 11 04:00:05 dartagnan NetworkManager[1333]: <info> (18:86:AC:25:**00:33**): cleaning up...
Jan 11 04:00:05 dartagnan NetworkManager[1333]: <info> (18:86:AC:25:**00:33**): taking down device.
and at that point it basically died (syslog stops) and I had to do a hard reset.

Same with kern.log:
> Jan 11 04:00:05 dartagnan kernel: [  120.856234] wlan0: deauthenticating from 00:23:ed:**00:00:00** by local choice (reason=3)
Jan 11 04:00:05 dartagnan kernel: [  120.885409] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan 11 04:00:05 dartagnan kernel: [  120.885435] cfg80211: Restoring regulatory settings
Jan 11 04:00:05 dartagnan kernel: [  120.885452] cfg80211: Calling CRDA to update world regulatory domain
Jan 11 04:00:05 dartagnan kernel: [  120.906568] cfg80211: World regulatory domain updated:
Jan 11 04:00:05 dartagnan kernel: [  120.906579]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 11 04:00:05 dartagnan kernel: [  120.906591]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 11 04:00:05 dartagnan kernel: [  120.906600]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 11 04:00:05 dartagnan kernel: [  120.906610]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 11 04:00:05 dartagnan kernel: [  120.906620]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 11 04:00:05 dartagnan kernel: [  120.906629]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


I am not a developer, but I can deploy a second instance of meerkat on this machine. I am willing to do any tests on this machine needed to pin down and fix this issue and work together with whoever is able to do it.

Anyone up for this?

---

### Post by acharseth on 2011-01-16
Hi!

Did you get any response?
I seem to have a similar problem.
I upgraded a lap top to Ubuntu 10.10 and after this it randomly freezes with no response.
Looking at the logs it seems like it always freezes after a WLAN event and doing a IPv6 lookup (which fails because there are no IPv6 functionality in my network).

I now have a situation where this laptop always freezes when I start Firefox so I would love if someone could help me solving this and I am glad to help debugging this.

Br.
Arne

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by sam_vde on 2011-01-19
No reply.

Try the backport wireless packages I mentioned above. If you do not suspend/resume, things should already be better.

---

### Post by acharseth on 2011-02-07
For me it solved the problem by doing a complete reinstallation (from CD) of Ubuntu 10.10.

Arne

---

