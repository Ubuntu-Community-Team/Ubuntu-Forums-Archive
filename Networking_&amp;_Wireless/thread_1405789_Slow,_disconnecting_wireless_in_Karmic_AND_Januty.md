---
title: "Slow, disconnecting wireless in Karmic AND Januty"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by Ponches on 2010-02-13
Hey guys, I got a good one for ya!

I have a hodge-podge of a machine, a desktop I assembled.  I recently wiped XP and set the system up dual-boot with Karmic.  Everything works...except for the internet.  (Wireless)  After the system boots, I have a few minutes of decent wireless performance (the speed I would expect.)  After that, the wireless speed drops to 1.5kbps or less, intermittently, then disconnects.  I get a prompt for my wireless password, and entering it does not reestablish the connection.

I know there has been a lot of noise about networking problems in Karmic.  I disabled IPv6 in Firefox and Network settings.  The house network works beautifully for XP and on my laptop (EEE PC with Karmic Netbook Remix) so I don't think it's the router.  As a last resort, I downgraded to Jaunty.  I got the same results.

I'm back to running karmic and hoping that somebody has a suggestion that helps!  I'm about to give up on Ubuntu on this desktop.

$lspci
03:05.0 Network controller: RaLink RT2561/RT61 802.11g PCI

phobos@phobos-desktop:~$ sudo ifconfig wlan0
[sudo] password for phobos: 
wlan0     Link encap:Ethernet  HWaddr 00:1c:10:6d:2d:6d  
          inet6 addr: fe80::21c:10ff:fe6d:2d6d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51176121 (51.1 MB)  TX bytes:2693746 (2.6 MB)

phobos@phobos-desktop:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Hazelwood"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


phobos@phobos-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for phobos: 
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by Ponches on 2010-02-13
Bump for hope!  I am totally stumped... :-(

---

### Post by gdonwallace on 2010-02-14
Wish I had an answer, but I am experiencing the same problem.  It connects at a decent speed, what I am used to getting; then the speed drops to nothing and then ramps back up.  It will hit as low as 15% sometimes then jump up to 75%.  I have tried booting into an older kernel for Karmic, but that does not seem to be helping either.

I hope something gets done soon, this is really annoying.

BUMP for answer.

---

### Post by northd_tech on 2010-02-19
Hi Ponches,

I think you must be missing a line from lspci above (about the ethernet interface and what kind you have).  Can you post the results of the following terminal commands:

```
sudo lshw -C network

lspci 
```As far as the IPv6 thing, I just did that tonight and it gave me about 10x better speed at home (2-4 times better at work earlier today, which has a #*@@% ISP).  Others have mentioned using OpenDNS or pointing your name servers at Google's servers.

I didn't make a note of which thread, but it is on at least one of these:

[http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6&page=3](http://ubuntuforums.org/showthread.php?t=1195755&highlight=slow+internet+IPv6&page=3)

[http://ubuntuforums.org/showthread.php?t=1405129&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1405129&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1407910&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1407910&highlight=slow+internet+IPv6)

[http://ubuntuforums.org/showthread.php?t=1406817&highlight=slow+internet+IPv6](http://ubuntuforums.org/showthread.php?t=1406817&highlight=slow+internet+IPv6)
-------------------------------------------------------------------------------------
You can check whether your ISP & router are doing IPv4 or IPv6 here:

[http://www.ip4.me](http://www.ip4.me)
[http://www.ip6.me](http://www.ip6.me)
whatismyv6.com
wantismyipv6address.com
-------------------------------------
Finally, here are some sources for internet speed testing:

[http://www.bandwidthplace.com/](http://www.bandwidthplace.com/)

[http://speed.kify.com/](http://speed.kify.com/)

[http://www.gambitdesign.com/bandwidthmeter/](http://www.gambitdesign.com/bandwidthmeter/)

[http://www.dsl-speedtest.us/bandwidthmeter/meter.php](http://www.dsl-speedtest.us/bandwidthmeter/meter.php)

And a plugin for Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/178](https://addons.mozilla.org/en-US/firefox/addon/178)

---

