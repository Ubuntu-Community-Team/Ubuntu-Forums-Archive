---
title: "strange issue (bug?) with WiFi in 9.10 Karmic"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by htismaqe on 2009-11-01
I have a weird issue with my wireless after a fresh install of 9.10.  I've tested this wireless with 9.04 using both ndiswrapper and the included kernel drivers, as well as with compiled upstream drivers from wireless.kernel.org.

The problem doesn't occur that I've noticed in 9.04 but only in 9.10.

Here's the output for the physical device and driver in 9.10.

lsusb
```

Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

```lsmod
```

rtl8187                50624  0 
mac80211              181236  1 rtl8187
led_class               4096  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211

```

Now for the issue.  The link comes up just fine using WPA2 in both Network Manager and WICD.  But the bit rate is reported at anywhere from 1M to 12M.  Setting the bit rate to 54M, for example, via **sudo iwconfig wlan0 rate 54M** doesn't disconnect the wireless, but IP connectivity drops.  I started a ping to my gateway address and set bit rate to 54M - pings time out.  Set the bit rate to 11M via **sudo iwconfig wlan0 rate 11M** and pings resume immediately even though no change in wireless connection status is reported via iwconfig.  If I set the bit rate to 54M prior to connecting the wireless, it simply doesn't connect because it's can't pull an IP address.

The reason why I put the word "bug" in the title is two tidbits that I found in the iwlist and iwconfig output.  Signal strength according to both Network Manager and WICD is 100%, but check the red text:

iwlist scanning
```

wlan0     Scan completed :
          Cell 01 - Address: 00:13:49:89:61:67
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR=Red]***Quality=70/70***[/COLOR]  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"parkernet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000040253119b
                    Extra: Last beacon: 104400ms ago
                    IE: Unknown: 00097061726B65726E6574
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300
```iwconfig
```

wlan0     IEEE 802.11bg  ESSID:"parkernet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:49:89:61:67   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          [COLOR=Red]***Link Quality=70/70***[/COLOR]  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I booted Xubuntu 9.04 LiveCD and checked it there - link quality is 70/100 out of the box.

So it appears to me that my connection is suffering a performance loss due to link quality but not the ACTUAL link quality, but because the OS thinks the MAXIMUM link quality availlable is 70.

---

### Post by htismaqe on 2009-11-01
Anybody?

---

### Post by SteveDee on 2009-11-02
I've been investigating the same issue using wavemon. The illustration shows my test system running 9.04. Everything looks healthy and the bitrate is 54Mbit/s.

But when running 9.10 the Link Quality bar falls to 28% and the bitrate is only 1Mbit/s.

I feel this must be a problem with the kernel, rather than a higher level Ubuntu issue, since the tools we are using are distribution independant. It would be interesting to check this on another distribution that uses the same kernel.

---

### Post by SteveDee on 2009-11-02
I carried out some further tests using Puppy Linux:-

 - Puppy with Linux kernel 2.6.21.7 gives same Wifi Link quality as Ubuntu with kernel 2.6.28-15 (95-100%)

 - Puppy with kernel 2.6.30.5 gives same Link quality as Ubuntu with kernel 2.6.31-14 (25-30%)

...I think its the Linux kernel!


>>>>Additional:-

In the Linux kernel changelog here: [http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.32-rc5](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.32-rc5)
there is some mention of a problem relating to wifi computational gain. So maybe we need to wait until kernel 2.6.32-xx is released?

---

### Post by htismaqe on 2009-11-02
From the research I've done, there seems to be issues with the kernel driver for the RTL8187B chipset specifically.

[http://ubuntuforums.org/showthread.php?t=1303542](http://ubuntuforums.org/showthread.php?t=1303542)

---

### Post by SteveDee on 2009-11-02
> **htismaqe said:**
> From the research I've done, there seems to be issues with the kernel driver for the RTL8187B chipset specifically.

[http://ubuntuforums.org/showthread.php?t=1303542](http://ubuntuforums.org/showthread.php?t=1303542)

I'm using the zd1211rw driver, but I think the problem is at a level below the driver.

---

### Post by htismaqe on 2009-11-02
Interesting.

---

### Post by htismaqe on 2009-11-03
I've done some more testing by moving the antenna closer to (and further away from) the wireless AP.

Link quality is pretty much always 70/70 under **iwconfig** but the bit rate fluctuates up and down randomly.  It seems better the closer I get, which leads me to believe it's a range/power issue.  

I did some more research on the System76 driver situation in the thread I posted earlier ([http://ubuntuforums.org/showthread.php?t=1303542](http://ubuntuforums.org/showthread.php?t=1303542)) and it looks like Realtek sent them an OEM driver.  Their testing seems to indicate that the effective range of this adapter, using the existing kernel driver, is about 30 feet.  The OEM driver increases it to 120 feet.

So it definitely sounds to me like an attenuation issue.  I guess I'll hard set to 11M and wait for a fix to come out.

---

### Post by SteveDee on 2009-11-03
I'm confused about the driver issue, given that I'm not using Realtek, but maybe there are several problems.

I spent some time today trying to compile kernel 2.6.32-rc5 but after a couple of hours buzzing away, it failed. Maybe I should have applied the kernel patch first!

---

### Post by htismaqe on 2009-11-03
> **SteveDee said:**
> I'm confused about the driver issue, given that I'm not using Realtek, but maybe there are several problems.

I spent some time today trying to compile kernel 2.6.32-rc5 but after a couple of hours buzzing away, it failed. Maybe I should have applied the kernel patch first!

I'm not sure what in the kernel, outside of the wireless drivers could be contributing.  Power management maybe?

Sorry, I'm confusing you, I do understand you have a different card than me.  At least in my situation, the problem appears to be the wireless driver.  Although, it would appear from a quick Google search that are lots of issues with wireless in 9.10.

---

### Post by SteveDee on 2009-11-04
> **htismaqe said:**
> ...Sorry, I'm confusing you...

Please don't apologize, this forum is about gaining knowledge, and I'm very hungry for it! :popcorn: ...and already very confused!

There must be a few people "out there" that know exactly what the problem is. So the longer we discuss it, the more chance we have of catching the eye of a guru.

I'm also not afraid to be provocative to entice others to share their knowledge. So here is my grand kernel/wifi/driver theory which may provoke some responses.

*The Linux kernel uses a selection of modules & drivers as appropriate for the running system. So when I plug in my SafeCom wifi stick, the zd1211rw driver is loaded (whereas on your system the RealTek driver is used). So the kernel has to work with a range of wifi drivers with which it communicates via a common set of methods and properties. If the problem was with only 1 driver, it would only affect related wifi hardware. If the problem is with the kernel software that calls the wifi driver, all systems with wifi will be affected. From reading a changelog on [www.kernel.org](www.kernel.org) I got the impression that the signal gain/scaling was now incorrect, because a return value that should have been treated as a Long data type was being treated as an Integer (...or possibly the other way around). So I think the problem is in the kernel code rather than a specific wifi driver. If I'm right, then presumably all wifi equipped systems using kernel 2.6.31 are affected (and certainly a lot people have noticed this problem). Also if it were just the driver, it should be possible to build the kernel with the old driver, unless (heavens forbid) the kernel code is not backwards compatible.*

Its unfortunate that I could not build 2.6.32-rc5, but from what I can gather, this is due to script errors associated with Google's Android. And the Google team seem to be too busy at the moment (probably acquiring more companies) to fix this.

Now tell me I'm wrong :lolflag:

---

### Post by htismaqe on 2009-11-04
> **SteveDee said:**
> Please don't apologize, this forum is about gaining knowledge, and I'm very hungry for it! :popcorn: ...and already very confused!

There must be a few people "out there" that know exactly what the problem is. So the longer we discuss it, the more chance we have of catching the eye of a guru.

I'm also not afraid to be provocative to entice others to share their knowledge. So here is my grand kernel/wifi/driver theory which may provoke some responses.

*The Linux kernel uses a selection of modules & drivers as appropriate for the running system. So when I plug in my SafeCom wifi stick, the zd1211rw driver is loaded (whereas on your system the RealTek driver is used). So the kernel has to work with a range of wifi drivers with which it communicates via a common set of methods and properties. If the problem was with only 1 driver, it would only affect related wifi hardware. If the problem is with the kernel software that calls the wifi driver, all systems with wifi will be affected. From reading a changelog on [www.kernel.org]("http://www.kernel.org") I got the impression that the signal gain/scaling was now incorrect, because a return value that should have been treated as a Long data type was being treated as an Integer (...or possibly the other way around). So I think the problem is in the kernel code rather than a specific wifi driver. If I'm right, then presumably all wifi equipped systems using kernel 2.6.31 are affected (and certainly a lot people have noticed this problem). Also if it were just the driver, it should be possible to build the kernel with the old driver, unless (heavens forbid) the kernel code is not backwards compatible.*

Its unfortunate that I could not build 2.6.32-rc5, but from what I can gather, this is due to script errors associated with Google's Android. And the Google team seem to be too busy at the moment (probably acquiring more companies) to fix this.

Now tell me I'm wrong :lolflag:

It's definitely true that there could be problems with the kernel itself.  More often than not though, those issues come to light because the kernel is trying to do things that a certain driver or subset of drivers can't handle.  I read some stuff the other day about WICD crashing because **iwconfig** reports standard parameters and this certain driver didn't recognize one of them (ie. **Rx invalid frag**).  MANY of the wireless kernel drivers are simply incomplete at this time and that's probably the biggest problem, IMO.

I'm sure you'll find this interesting.

Last night, I ran 9.04 again and compiled the upstream kernel drivers from wireless.kernel.org.

9.04 is doing the SAME THING now.  So it can't be just the kernel.

---

### Post by SteveDee on 2009-11-04
Your experiment with 9.04 backs up your argument nicely. And your link eventually took me here: [http://kernelnewbies.org/Linux_2_6_31#head-799157cd8729eba8ee5bc1ff0290d7414f366ef2](http://kernelnewbies.org/Linux_2_6_31#head-799157cd8729eba8ee5bc1ff0290d7414f366ef2) which shows extensive changes to both the kernel and many, many drivers including my zd1211. Before I started looking at this I naively assumed that a kernel version up-issue from 2.6.30 to 2.6.31 would just indicate bug fixes. But I now get the impression there are detail changes which would justify the second digit being incremented.

Additional: I've just run lsusb on both a 9.04 and a 9.10 system. The key wifi drivers/files zd1211rw, mac80211 & cfg80211 show tremendous differences in file size (some newer are bigger, some are smaller).

---

### Post by htismaqe on 2009-11-04
> **SteveDee said:**
> Your experiment with 9.04 backs up your argument nicely. And your link eventually took me here: [http://kernelnewbies.org/Linux_2_6_31#head-799157cd8729eba8ee5bc1ff0290d7414f366ef2](http://kernelnewbies.org/Linux_2_6_31#head-799157cd8729eba8ee5bc1ff0290d7414f366ef2) which shows extensive changes to both the kernel and many, many drivers including my zd1211. Before I started looking at this I naively assumed that a kernel version up-issue from 2.6.30 to 2.6.31 would just indicate bug fixes. But I now get the impression there are detail changes which would justify the second digit being incremented.

Additional: I've just run lsusb on both a 9.04 and a 9.10 system. The key wifi drivers/files zd1211rw, mac80211 & cfg80211 show tremendous differences in file size (some newer are bigger, some are smaller).

Check this out too.

[http://ubuntuforums.org/showpost.php?p=8243103&postcount=26](http://ubuntuforums.org/showpost.php?p=8243103&postcount=26)

This guy upped the gain on his router and it temporarily fixed the problem...

---

### Post by sensay on 2009-11-30
Hi, have a problem i think may be related..

My wireless dish for Desktop2 uses the zydas chipset and the zd1211rw driver. I have a home network running between my 3 machines (see sig) and desktop2 cant stream any media off of my other machines, it goes at about 100 kb.s. This is using samba to connect. The internet connection for that machine is about 4MB (much less than it should be but still enough to stream some media my other computers)

Could this be related to the problems in the latest ubuntu release/latest kernel?

Im almost certainly going to roll that machine back to 9.04 but would like to try and troubleshoot it first.

Thanks

---

