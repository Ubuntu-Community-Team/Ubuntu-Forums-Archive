---
title: "Intel 3945ABG (iwl3945 driver) slow as hell."
date: 2010-06-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-06-29
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932)
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1592](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1592)
[https://bugs.launchpad.net/linux/+bug/581936](https://bugs.launchpad.net/linux/+bug/581936)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418)
[https://bugzilla.kernel.org/show_bug.cgi?id=16132](https://bugzilla.kernel.org/show_bug.cgi?id=16132)

Neither of those bugs are actually resolved and the iwl3945 driver is still fundamentally broken.

I'm sitting right next to the router.

Windows: 1536 KB/s downstream
Ubuntu: 150 KB/s downstream

I've had this problem with both a Netgear WNDR3300 and a Linksys WRT54G v5 and I've been experiencing it for around for at least 2 or 3 years. None of the things that mitigated in the past work anymore.

---

### Post by dagrump on 2010-06-29
Turning power saving off doesn't help? I know for a while a couple of my boxes I had to disable power saving.

---

### Post by Bucky Ball on 2010-06-29
Are you using Network Manager? Try Wicd. It made the world of difference for some reason.

---

### Post by Starks on 2010-06-30
Don't you think I've tried both of those ideas already to no avail?

Besides, this is a DRIVER issue.

It's bad enough that I can't get ndiswrapper to work on Lucid or Maverick.

---

### Post by Bucky Ball on 2010-06-30
Right then. I've been told. Leave you to it. Good luck.

---

### Post by Starks on 2010-06-30
Hmm. Got ndiswrapper working.

I'd rather use Windows drivers on Linux than RF kill and reset my 3945abg every hour or so using iwl3945 to regain full speed.

---

### Post by jfernyhough on 2010-06-30
I have issues* with the 3945abg in my work laptop - and that's running Windows XP. Of course, when I try to update the driver the software management kicks in and reinstalls the old one. Pain in the backside.

*after transferring 50-80MB of data I have to disable and enable the card to get it working again.

---

### Post by MacUntu on 2010-06-30
> **Starks said:**
> [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932)
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1592](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1592)
and the iwl3945 driver is still fundamentally broken
It isn't for all cards. My iwl3945 works like a charm.

---

### Post by joske on 2010-07-01
my laptop with same chipset doesn't even connect to my wifi (WPA2 PSK). I can see it associates, but never connects.

---

### Post by koso on 2010-07-02
> **joske said:**
> my laptop with same chipset doesn't even connect to my wifi (WPA2 PSK). I can see it associates, but never connects.

There is another bug in kernel ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016)) which causes problems with multicast and DHCP, and that is probably your problem with connection to network. You can use static ip configuration, or wait for kernel fix.

---

### Post by joske on 2010-07-05
> **koso said:**
> There is another bug in kernel ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016)) which causes problems with multicast and DHCP, and that is probably your problem with connection to network. You can use static ip configuration, or wait for kernel fix.

test kernel in bug report works for me. Thx!

---

### Post by Starks on 2010-07-05
Can we get back to discussing the real issue and stop interjecting unrelated ones?

---

### Post by Mr. Picklesworth on 2010-07-05
> **koso said:**
> There is another bug in kernel ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591016)) which causes problems with multicast and DHCP, and that is probably your problem with connection to network. You can use static ip configuration, or wait for kernel fix.

> **joske said:**
> test kernel in bug report works for me. Thx!

> **Starks said:**
> Can we get back to discussing the real issue and stop interjecting unrelated ones?

So I guess you already know the solution?

---

### Post by Starks on 2010-07-05
No, I don't. But the DHCP issue almost certainly has nothing to do with my speed problems that have existed for years.

If people want to discuss that issue, they should've made a new topic.

---

### Post by boontz on 2010-07-12
No matter what wireless network I try to connect to, whether it is secured with WEP, WPA, WPA2 or unsecured, dhclient fails to allow me to do so. I can connect to my wireless network using iwconfig if I turn off network-manager, but then I cannot configure my dhcp so it doesn't matter. If I turn off dhcp in network-manager, I can also connect, but again I cannot use dhcp. Wired internet with eth0 works perfectly (b44 driver) so I'm not sure if this is a dhclient issue or iwl3945 issue.

dmesg output:
```
[   87.478612] wlan0: authenticate with 00:xx:xx:xx:xx:xx (try 1)
[   87.480371] wlan0: authenticated
[   87.480990] wlan0: associate with 00:xx:xx:xx:xx:xx (try 1)
[   87.484120] wlan0: RX AssocResp from 00:xx:xx:xx:xx:xx (capab=0x421 status=0 aid=5)
[   87.484125] wlan0: associated
[   87.485958] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.499428] type=1400 audit(1278983197.082:27):  operation="getattr" pid=1834 parent=1010 profile="/sbin/dhclient3" name="/lib/" pid=1834 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   87.499458] type=1400 audit(1278983197.082:28):  operation="getattr" pid=1834 parent=1010 profile="/sbin/dhclient3" name="/usr/lib/" pid=1834 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   98.340028] wlan0: no IPv6 routers present
[  132.650164] wlan0: deauthenticating from 00:xx:xx:xx:xx:xx by local choice (reason=3)
[  132.674021] cfg80211: All devices are disconnected, going to restore regulatory settings
[  132.674032] cfg80211: Restoring regulatory settings
[  132.674038] cfg80211: Calling CRDA to update world regulatory domain
[  132.678072] cfg80211: World regulatory domain updated:
[  132.678079]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  132.678086]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  132.678092]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  132.678098]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  132.678103]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  132.678109]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

also, this old bug seems to be related, and that suggests apparmor may be the culprit: [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/400349](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/400349)

---

### Post by cariboo on 2010-07-13
There was an iwl3945 thread already, merged.

---

### Post by Starks on 2010-07-14
btw, here's the launchpad bugs

[https://bugs.launchpad.net/linux/+bug/581936](https://bugs.launchpad.net/linux/+bug/581936)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418)
[]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418")

---

### Post by Starks on 2010-09-17
The intel linux wireless devs have no interest in this bug. How disgusting.

What good is a driver if it limits you to 1/1 speeds from the moment of connection?

I'm sick of relying on ndiswrapper and its minute-long connection waits.

---

### Post by MacUntu on 2010-09-18
Would be interesting to know why some modules work and others don't.

FWIW, on my module it says:```
Model: WM3945ABG  MOW2
Intel(R) PRO/Wireless 3945ABG Network Connection
Serial No: ******286CX#########
Mfg Date: 07/14/06          TA: ######-###
Made in China            MAC: 001302******
```

I have no problems with this card.

---

### Post by Starks on 2010-09-18
For almost every 3945 owner I've talked who said that, it turned out that their ISP speeds weren't fast enough for them to notice the driver throttling, didn't compare the speeds to those of ndiswrapper+netw4x32 or Windows, or couldn't bother to hook up to a router to test.

I sincerely hope you're an exception.

---

### Post by MacUntu on 2010-09-18
> **Starks said:**
> For almost every 3945 owner I've talked who said that, it turned out that their ISP speeds weren't fast enough for them to notice the driver throttling, didn't compare the speeds to those of ndiswrapper+netw4x32 or Windows, or couldn't bother to hook up to a router to test.

I sincerely hope you're an exception.

Of course I am. ):P

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1932), #48 is me. ;)

---

### Post by Starks on 2010-09-18
So, you're no longer affected?

---

### Post by MacUntu on 2010-09-18
As I said, my module works flawlessly.

---

### Post by FuturePilot on 2010-10-04
I upgraded my laptop to Maverick and encountered this problem. It has an Intel 3945ABG card in it. I see it's been around for a while. It's odd that I've never run into this bug until now. I'm disappointed because this basically makes Maverick unusable for me. Anything network related is painfully slow. I have currently reverted back to Lucid and moved my Maverick install over to another hard drive to try and debug this. Unfortunately I haven't had any luck with the things I've tried so far. :(

---

### Post by Muflon on 2010-10-05
I am using a Dell laptop with a 'Intel® Pro Wireless 3945 802.11a/b/g Mini-PCI Card EUR' wireless card and it works brilliantly.

Muflon

---

### Post by FuturePilot on 2010-10-05
> **Muflon said:**
> I am using a Dell laptop with a 'Intel® Pro Wireless 3945 802.11a/b/g Mini-PCI Card EUR' wireless card and it works brilliantly.

Muflon

What kind of router do you have and what firmware is it running?

---

### Post by el_smurfo on 2010-10-07
Had the same issue until last night's updates, now getting the full 3M that I pay for rather than the 150k I was getting on all other 10.10 builds.

---

### Post by Starks on 2010-10-08
Issue still here with latest updates.

iwl3945: 3 Mbps/3 Mbps
ndiswrapper: 17 Mbps/5 Mbps

---

### Post by Muflon on 2010-10-08
> **FuturePilot said:**
> What kind of router do you have and what firmware is it running?

I am using a stock BT Homehub router.

Muflon

---

### Post by FuturePilot on 2010-10-08
Yep, still painfully slow. Updates haven't changed anything.

---

### Post by Starks on 2010-10-08
Well, Intel doesn't care.

[https://bugzilla.kernel.org/show_bug.cgi?id=16132#c5](https://bugzilla.kernel.org/show_bug.cgi?id=16132#c5)

---

### Post by MacUntu on 2010-10-08
Seriously, what do you expect? That they build a task force to fix an issue with a five year old product? Besides, they obviously have problems reproducing the bug, because it's NOT affecting every module/user/environment.

Did you try rebuilding the kernel with unsetting CONFIG_CFG80211_DEFAULT_PS?

---

