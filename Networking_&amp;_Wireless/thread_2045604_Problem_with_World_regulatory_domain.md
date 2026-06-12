---
title: "Problem with World regulatory domain"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by selinger on 2012-08-21
I am using wicd on Ubuntu 11.10, and I live in Canada. I usually have no problems connecting to any wireless network. However, whenever I visit the U.S., my wireless is unable to connect - it seems to connect briefly and then drops the connection after a second or two.

Upon further investigation, I noticed the following odd behavior. I usually use "dpkg-reconfigure tzdata" to re-configure my time zone when I am travelling. If an American time zone (e.g. America/Los Angeles) is in effect at *boot time*, then I experience the above problem, i.e., unable to connect without dropping the connection. On the other hand, if a Canadian time zone (e.g. America/Vancouver) is in effect at boot time, then I can connect without problems - even if I am actually in the U.S. Note: changing the timezone after booting does not help/hinder - only the timezone that was in effect at boot time seems to affect the wireless connectivity.

Looking at the system logs, I see lines like the following in the case of an unsuccessful connection:

```
Aug 21 09:57:10 firefly kernel: [  465.357185] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:57:10 firefly kernel: [  465.480124] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:57:10 firefly kernel: [  465.699974] r8169 0000:05:00.0: eth0: link down
Aug 21 09:57:10 firefly kernel: [  465.701618] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 09:57:11 firefly kernel: [  466.037220] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:57:13 firefly kernel: [  468.219295] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 21 09:57:14 firefly kernel: [  469.167137] type=1400 audit(1345568234.215:35): apparmor="DENIED" operation="open" parent=6541 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=6573 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 21 09:57:15 firefly kernel: [  470.036427] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 09:57:15 firefly kernel: [  470.044184] cfg80211: World regulatory domain updated:
Aug 21 09:57:15 firefly kernel: [  470.044189] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 09:57:15 firefly kernel: [  470.044197] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:57:15 firefly kernel: [  470.044204] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:57:15 firefly kernel: [  470.044211] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:57:15 firefly kernel: [  470.044218] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:57:15 firefly kernel: [  470.044225] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:57:15 firefly kernel: [  470.165187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:57:15 firefly kernel: [  470.391722] r8169 0000:05:00.0: eth0: link down
Aug 21 09:57:15 firefly kernel: [  470.392677] ADDRCONF(NETDEV_UP): eth0: link is not ready
(end of log)

```I also see lines like the following in case of a successful connection:

```
Aug 21 09:59:00 firefly kernel: [   76.172170] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:59:00 firefly kernel: [   76.352214] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:59:00 firefly kernel: [   76.442933] r8169 0000:05:00.0: eth0: link down
Aug 21 09:59:00 firefly kernel: [   76.443740] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 21 09:59:00 firefly kernel: [   76.683651] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:59:10 firefly kernel: [   86.818388] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 21 09:59:10 firefly kernel: [   86.897517] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 21 09:59:10 firefly kernel: [   86.915088] audit_printk_skb: 30 callbacks suppressed
Aug 21 09:59:10 firefly kernel: [   86.915097] type=1400 audit(1345568350.964:22): apparmor="DENIED" operation="open" parent=2251 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=2289 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 21 09:59:11 firefly kernel: [   87.024406] cfg80211: Calling CRDA to update world regulatory domain
Aug 21 09:59:11 firefly kernel: [   87.032314] cfg80211: World regulatory domain updated:
Aug 21 09:59:11 firefly kernel: [   87.032319] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 21 09:59:11 firefly kernel: [   87.032326] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:59:11 firefly kernel: [   87.032334] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:59:11 firefly kernel: [   87.032340] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:59:11 firefly kernel: [   87.032347] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 21 09:59:11 firefly kernel: [   87.032354] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
(end of log)
```It seems that in either case, the link briefly becomes ready, and then this "World regulatory domain" thingy kicks in and somehow decides to shut down my link, if it thinks I am not in Canada.

Does anybody know what this "World regulatory domain" is supposed to do? And why it is not working properly? My web searches have turned up no useful information. I'd be glad to provide more debugging information. Thanks.

---

### Post by chili555 on 2012-08-21
> cfg80211: Calling [COLOR="Red"]CRDA[/COLOR] to update world regulatory domainThis may be informative: [http://linuxwireless.org/en/developers/Regulatory/CRDA](http://linuxwireless.org/en/developers/Regulatory/CRDA)

As well as this long thread: [http://ubuntuforums.org/showthread.php?t=1978485&highlight=crda](http://ubuntuforums.org/showthread.php?t=1978485&highlight=crda)

Instead of writing a permanent .conf file, you might try:```
sudo modprobe -r <wireless_driver>
sudo modprobe -r cfg80211
sudo modprobe cfg80211 ieee80211_regdom=US
sudo modprobe <wireless_driver>
```

---

### Post by selinger on 2012-08-22
Thanks so much for those helpful links. If I do "iw reg get" after booting, I always get:
```
country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
```regardless of what timezone I had previously set. I guess "00" means "least common denominator of all countries". But if I then do "iw reg set US", the output of "iw reg get" changes to
```
country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)
```and the wireless connection will work fine. Similarly, if I do "iw reg set CA", the output is
```
country CA:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)
```and again the wireless works fine. The setting does not persist after rebooting.

So this solves my immediate problem. I don't want to hardwire a particular regulatory domain in a config file because I actually do travel a fair bit. It would be smart if the driver could somehow figure out what country it's in and do the right thing automatically, or at least fail with some meaningful error rather than disconnecting silently. But meanwhile, I am happy with being able to set it manually.

---

### Post by chili555 on 2012-08-22
> If I do "iw reg get" after booting, I always get:
Code:

country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

regardless of what timezone I had previously set. I guess "00" means "least common denominator of all countries". I'd suggest you set Canada as default and change when necessary as you can do. I might edit /etc/rc.local to add, above exit 0:```
iw reg set CA
```Then you can change as necessary after boot.

It would be wonderful if the router or access point would set the country code as well as the channel, bit-rate, et al. It surely knows based on the IP address it got from the ISP. My three wishes for world governments include working on terrorism, hunger and region domain.

---

