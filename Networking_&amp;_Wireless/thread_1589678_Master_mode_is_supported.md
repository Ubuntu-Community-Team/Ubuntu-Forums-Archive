---
title: "Master mode is supported"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by cemzafer on 2010-10-06
Hi all,

I really wonder if master mode is supported for the following card. Can I use that card as an access point?
Thanks.

Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

---

### Post by BkkBonanza on 2010-10-06
No. I'm 99% sure that card does not support master mode. There are very few current cards under Linux that support master mode. The only one now that I know for sure is the Atheros ath9k series, eg. AR9281 (which I use as a access point in my Ubuntu based router).

There were a bunch of Prism ones years ago but they have become fairly obsolete now since people usually want "N" mode now.

---

### Post by bkratz on 2010-10-06
> **cemzafer said:**
> Hi all,

I really wonder if master mode is supported for the following card. Can I use that card as an access point?
Thanks.

Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

The person in this thread seems to have put in in the master mode. See post two.

[http://art.ubuntuforums.org/showthread.php?p=9908291](http://art.ubuntuforums.org/showthread.php?p=9908291)

He/she never solved their particular problem (no responses ) but perhaps if you PM them they could help you.


IT WAS YOU!!  nevermind

---

### Post by BkkBonanza on 2010-10-06
Part of the problem is that it's not enough to put the card in "master mode". To run an access point you also have to generate beacon signals and handle  management frames and authentication stuff. 

Usually the **hostapd** program is used for this and it has limited device support. In master mode alone the card just sits there like a dummy and doesn't know how to behave as an access point.

---

### Post by cemzafer on 2010-10-07
Thanks for all the replies, so I have to look at another solution with another card.

---

### Post by BkkBonanza on 2010-10-07
I did quite a bit of checking into this last year and couldn't find a USB dongle that would support it. Start with the [hostapd docs]("http://hostap.epitest.fi/hostapd/") to find drivers and work back to devices. 

I found the AR9281 on eBay for $15-20 but it is a miniPCIe device not USB. It worked well in my notebook for a mobile access point and then I moved it into my mini-itx box for use as a router/access point. It works.

I also tried RT8180 and ZyDas 1211 USB dongles which did not work.

The drivers under Windows tend to have better support because they are more fully developed by the manufacturers. In Linux the drivers are often third party OS hacks and they tend to stop short of master mode support, because not many people demand it.

Now with the mac80211 and net80211 driver support I think hostapd supports more devices than before, but it still seems to require some detective work as no one has written up any definitive lists.

See [this page]("http://wireless.kernel.org/en/users/Drivers") with AP column info. For USB [this one]("http://wireless.kernel.org/en/users/Drivers/carl9170") seems potential but I haven't tested it of course.

---

### Post by cemzafer on 2010-10-07
Hi Bonanza,

I found my old usb wireless dongle which is ZyXEL Communications Corp. ZyAIR G-220 802.11bg and also found out that this [http://sourceforge.net/projects/zd1211/develop](http://sourceforge.net/projects/zd1211/develop) link support the ap mode in this model.
But I cant compile the module which gives the following error.

linux/autoconf.h: No such file or directory

Any idea what could be the problem. Linux-headers are installed and autoconf and the other stuff are installed too.
Thanks.

---

### Post by chili555 on 2010-10-07
```
linux/autoconf.h: No such file or directory
```I saw this: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/529514](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/529514)

Especially see:> you can easily create that link:

sudo ln -s ../../include/generated/autoconf.h /usr/src/linux-headers-2.6.33-020633-generic/include/linux/autoconf.hAnd also:> you need to change to the directory where you want the link to be placed, then create the symlink.Of course, substitute your header version details. I believe your package will then compile.

---

### Post by cemzafer on 2010-10-07
Hi,

I create the symbolic link as you mentioned, but it gives a bunch of errors and stop compilation.

---

### Post by chili555 on 2010-10-07
I'd suggest removing the link. Second, I tried compiling this and no amount of fiddling could get it to work. I suspect development stopped once the *zd1211r*w module was included in the mainline kernel.

Are you sure that *zd1211rw* doesn't do Master mode?

---

### Post by cemzafer on 2010-10-07
when I do this sudo iwconfig wlan1 mode Master, it gives the following error.

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.

I think that this mode is not supported.
Thanks.

---

### Post by chili555 on 2010-10-07
I'm sorry; that's all I know to suggest.

---

### Post by cemzafer on 2010-10-08
Thanks for all the replies and infos, by the way zd1211rw driver does not support master mode because of the following output:

desktop:~$ iw list
Wiphy phy0
    Band 1:
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm)
            * 2472 MHz [13] (20.0 dBm)
            * 2484 MHz [14] (disabled)
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
    max # scan SSIDs: 4
    Supported interface modes:
         * IBSS
         * managed
         * monitor
         * mesh point
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * new_beacon
         * new_station
         * new_mpath
         * set_mesh_params
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * Unknown command (55)
         * Unknown command (57)
         * Unknown command (59)
         * set_wiphy_netns
         * Unknown command (65)
         * connect
         * disconnect

---

