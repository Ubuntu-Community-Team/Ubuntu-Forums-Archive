---
title: "Recent software update broke WPA networks"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by ManiacDan on 2013-02-04
Sometime on Wednesday of last week I did a software update while at work.  I got a new kernel and a handful of other items that looked innocuous.  

Thursday when I came into work I couldn't connect to to the corporate network.  I discovered that Windows worked fine.  I also can't connect to my home networks on Ubuntu.  My laptop is essentially useless until I can get WPA working again.

It doesn't seem like this is a common problem, though it was definitely triggered by a software update of some sort.  Three networks in three buildings, all WPA2 Personal PSK, all stopped being accessible from this one device.  Since I can't work away from a hard wired connection, this is a deal breaker for me.

Anyone have any ideas?

---

### Post by jacobmar1ey on 2013-02-04
I'm having the same issue, running 12.04. I can get onto my neighbor's unencrypted "NETGEAR" network, but my own WPA2-PSK is unavailable. I'm on an ASUS EeePC and wonder if it has something to do with cfg80211 as it spits out a ton of crap on dmesg. Anyone else? Is this related to it being a Broadcom BCM43xx chip? I'm going to check older kernels that are installed on here and be back in a bit.

```
robert@zirconium ~ $ uname -a
Linux zirconium 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
``````
robert@zirconium ~ $ dmesg | tail -n 50
[  107.233225] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233233] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  107.233244] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233253] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[  107.233263] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233272] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  107.233283] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233292] cfg80211: Disabling freq 5260 MHz
[  107.233299] cfg80211: Disabling freq 5280 MHz
[  107.233307] cfg80211: Disabling freq 5300 MHz
[  107.233314] cfg80211: Disabling freq 5320 MHz
[  107.233321] cfg80211: Disabling freq 5500 MHz
[  107.233329] cfg80211: Disabling freq 5520 MHz
[  107.233336] cfg80211: Disabling freq 5540 MHz
[  107.233342] cfg80211: Disabling freq 5560 MHz
[  107.233348] cfg80211: Disabling freq 5580 MHz
[  107.233354] cfg80211: Disabling freq 5600 MHz
[  107.233361] cfg80211: Disabling freq 5620 MHz
[  107.233367] cfg80211: Disabling freq 5640 MHz
[  107.233373] cfg80211: Disabling freq 5660 MHz
[  107.233379] cfg80211: Disabling freq 5680 MHz
[  107.233386] cfg80211: Disabling freq 5700 MHz
[  107.233395] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  107.233407] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233416] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  107.233427] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233437] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  107.233448] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233457] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  107.233467] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233477] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  107.233487] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233495] cfg80211: Disabling freq 5920 MHz
[  107.233501] cfg80211: Disabling freq 5940 MHz
[  107.233507] cfg80211: Disabling freq 5960 MHz
[  107.233513] cfg80211: Disabling freq 5980 MHz
[  107.233519] cfg80211: Disabling freq 6000 MHz
[  107.233524] cfg80211: Disabling freq 6020 MHz
[  107.233530] cfg80211: Disabling freq 6040 MHz
[  107.233536] cfg80211: Disabling freq 6060 MHz
[  107.233542] cfg80211: Disabling freq 6080 MHz
[  107.233558] cfg80211: World regulatory domain updated:
[  107.233565] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  107.233575] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233586] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  107.233595] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  107.233606] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  107.233616] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.088064] eth1: no IPv6 routers present

``````
robert@zirconium ~ $ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

---

### Post by ManiacDan on 2013-02-04
Yeah I don't have any older images to test on this particular machine.  It literally just happened overnight last Wednesday.

---

### Post by jacobmar1ey on 2013-02-04
I was able to log into two older kernels, but the wl driver wasn't installed on them, and since I couldn't get online to install it, it was a no go. heh.

---

### Post by jacobmar1ey on 2013-02-04
This worked for me, but I use aptitude for package management. If you use something else like synaptic or the Software Center the commands will be different, but the process should be the same:

```

robert@zirconium ~ $ aptitude remove bcmwl-kernel-source 

robert@zirconium ~ $ aptitude install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6

robert@zirconium ~ $ aptitude forbid-version bcmwl-kernel-source=6.20.155.1+bdcom-0ubuntu0.0.1

```

This uninstalls the current version of the driver, installs the old version, and blacklists the current version. aptitude will install the next new version that does NOT match the blacklisted one.

I'm sure you can find ways to do this using synaptic, apt-get, or the Software Center. For a quick workaround, just uninstall the package, then install the one for download [here]("http://pkgs.org/ubuntu-12.04/ubuntu-restricted-amd64/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb/download/"). You'll have to be careful updating in the future however.

---

### Post by SeijiSensei on 2013-02-04
There are now dozens of threads here about problems with recent updates on machines with Broadcom wifi adapters.  I suggest you browse around and see what solutions others have come up with.

Alternatively, try booting the previous kernel image when you get the grub boot screen.  If you don't see that, hold down Shift while booting.

---

### Post by drbin on 2013-02-04
> **jacobmar1ey said:**
> This worked for me, but I use aptitude for package management. If you use something else like synaptic or the Software Center the commands will be different, but the process should be the same:

```

robert@zirconium ~ $ aptitude remove bcmwl-kernel-source 

robert@zirconium ~ $ aptitude install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6

robert@zirconium ~ $ aptitude forbid-version bcmwl-kernel-source=6.20.155.1+bdcom-0ubuntu0.0.1

```This uninstalls the current version of the driver, installs the old version, and blacklists the current version. aptitude will install the next new version that does NOT match the blacklisted one.

I'm sure you can find ways to do this using synaptic, apt-get, or the Software Center. For a quick workaround, just uninstall the package, then install the one for download [here]("http://pkgs.org/ubuntu-12.04/ubuntu-restricted-amd64/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb/download/"). You'll have to be careful updating in the future however.


**Absolutely worked** for me. Thank you  :wink:

---

### Post by varunendra on 2013-02-04
There is a bug report regarding this (thanks to [mikewhatever for the heads up]("http://ubuntuforums.org/showthread.php?p=12489624"))-
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/923809)

A possible workaround is in post #25 there, almost same as what jacobmar1ey suggested above.

---

### Post by ManiacDan on 2013-02-05
Well I'm glad this is getting some traction at least.  The workaround above didn't help me, sadly.  Ubuntu tries to connect to wifi for nearly a minute, then disconnects, waits 5 seconds, and tries again.  I have to turn the wifi off using the hardware switch if I want to stop getting the connection failure messages. 

I'll wait for the bug report to be resolved.  Until then, I have to work in Windows.

---

### Post by varunendra on 2013-02-05
> **ManiacDan said:**
> The workaround above didn't help me, sadly.

Could you please follow the solution suggested by mikewhatever in this thread and let us know how it goes -
[http://ubuntuforums.org/showthread.php?t=2111403](http://ubuntuforums.org/showthread.php?t=2111403)

If it doesn't help, please follow the "Wireless Script" link in my signature and post back its result here. Apart from that, also the output of -
```
modinfo wl
```

---

### Post by Cyclops_ on 2013-02-05
varunendra:  would it be bad if modinfo wl reports that the module could not be found?

---

### Post by sabersong on 2013-02-05
I was having the same problem, and following the instructions by jacobmar1ey solved it, mostly. Thing is, I can't account for an update causing the problem. We have two identical laptops, both with Broadcom 4313 adapters. Yesterday morning they both worked fine. Then I drove 800 miles, tried to connect to the LAN at our destination, and my wife's  laptop couldn't connect to the network. Mine had no trouble.

I followed the instructions by jacobmar1ey on this thread and got hers to connect to the LAN, but it still won't load any web pages, and none of her messaging clients are able to connect to their servers. And I can't ping the router or my laptop across the LAN, or any web sites. But ifconfig shows the correct access point and the ip address is in the correct range.

---

### Post by varunendra on 2013-02-06
> **Cyclops_ said:**
> varunendra:  would it be bad if modinfo wl reports that the module could not be found?
Not if you are using a different chip that uses a different driver.

I just looked at your [other thread]("http://ubuntuforums.org/showthread.php?t=2112407"), and you clearly have a different chip (intel's), so your problem was not related. Glad you got it solved there.

As a side note (a friendly one) regarding something I noticed there - posting multiple posts in a row, unless it is absolutely necessary, is frowned upon here. You even received a warning for that by mörgæs in that thread. I'd advise you against doing so else you may end up getting an infraction from one of the mods/admins. :(


> **sabersong said:**
> I followed the instructions by jacobmar1ey on this thread and got hers to connect to the LAN, but it still won't load any web pages....
sabersong,

Although network problems may often look same from outside, there are so many bits and pieces involved that usually it is best to post your question in its own thread unless you are absolutely sure that yours is the same problem with same chip/driver as being discussed in a thread.

So if you are still having the problem, please start a new thread in this (Networking & Wireless) section and post as much details of the problem as possible there.

For a summary of technical details to post there, please follow the "Wireless Script" link in my signature.

Thank you.

---

### Post by ManiacDan on 2013-02-06
Sorry for the delay, I actually was working in windows all day.  I hated it.

I followed jacobmar1ey's instructions (and translated them for my system) and that did nothing.  Then I followed mikewhatever's steps (nearly identical commands), and after a reboot (?) I appear to be on the wifi here at work.  

I'll leave the thread open since sabersong seems to have a different problem, unless you want to split the thread.

Thanks varunendra for pointing me at mikewhatever's solution.  I swear I googled like mad, but it was the day of the issue so there wasn't much to go on.

As a final note: when the next update comes out which actually fixes this issue, do I have to un-blacklist this driver?

---

### Post by sabersong on 2013-02-06
Thanks, Dan, but the problem seems to have fixed itself while I wasn't looking. If it pops up again, I'll start a new thread on it.

---

### Post by varunendra on 2013-02-06
> **ManiacDan said:**
> 
Thanks varunendra for pointing me at mikewhatever's solution.  I swear I googled like mad, but it was the day of the issue so there wasn't much to go on.
All hail mike then! :)

> As a final note: when the next update comes out which actually fixes this issue, do I have to un-blacklist this driver?
I'd quote a popular advice (for anything linux/bsd) - *"Don't fix it if it ain't broken"*

Although it shouldn't be followed too strictly, and it won't hurt trying as long as you can do it easily.;)

To be more precise, if it gets fixed and you do wish to use the newer version, then yes, you'd have to un-blacklist it manually (or 'undo' the changes you made in the '/etc/apt/preferences.d' directory, that is - delete or move the file if you manually created it.)


*@ sabersong,*
You are always welcome to start a new thread if the problem comes back. If you do, it'd be a good idea to follow the advice in my previous post.

Hope you won't need it though!

---

### Post by landersohn on 2013-02-07
The driver version in post #5 doesn't build for me
([https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176))

even in the "....ubuntu6" version

---

### Post by ManiacDan on 2013-02-07
> **landersohn said:**
> The driver version in post #5 doesn't build for me
([https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176))

even in the "....ubuntu6" version

Did you follow MikeWhatever's solution [here on askubuntu](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)?  That's what ended up working for me (though it required a reboot for reasons I still can't really figure out)

---

### Post by varunendra on 2013-02-07
> **landersohn said:**
> The driver version in post #5 doesn't build for me
([https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/700176))
landersohn,

I'm not sure which version of Ubuntu you are using. If you are posting to get help, you should consider posting details. Your profile says 10.04, the bug-report page you linked to also talks about kernel version 2x, however [this post]("http://ubuntuforums.org/showthread.php?p=12496459") of yours suggests that you probably upgraded to 12.04.

Either way, it seems more appropriate to me that you start a new thread of your own and ask your question there providing as much details as possible.

Feel free to post a link to it here so we can follow.

As a side note, if you are still using 10.04, it would be a good idea and about time to upgrade to 12.04 or 12.10 - whichever suits you more.


**EDIT:**
@ManiacDan,
> (though it required a reboot for reasons I still can't really figure out)
Everytime?? Or just once after building the driver?
If it's just once, I believe **modprobe -rfv wl**, then **modprobe -v wl** should make it work without restart.

---

