---
title: "at76 wireless with Ubuntu 9.10"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by claudio70b on 2009-10-02
Hi!

at76 (formerly at76c503a) is a driver for some Wireless LAN USB adapters like Netgear MA101 or one from Linksys.

until 8.10: some work was necessary, see [http://ubuntuforums.org/showthread.php?t=1029314](http://ubuntuforums.org/showthread.php?t=1029314)
since 9.04: worked out of the box thanks to adaption of ubuntu kernel team
since 9.10: ??? -> tell me, what are your experiences?

So far the at76 driver code was included in the kernel. And it was enabled and shipped with the ubuntu kernel binary. So there should be no need for manual compilation or use of ndiswrapper **idealy**.

I haven't found time for a closer look but ask you to report your experiences here.

---

### Post by pedor on 2009-10-02
I get a wlan0 but it refuse to connect 
**iwlist scan**

wlan0     Interface doesn't support scanning : Device or resource busy

[B]find /lib -iname at76_usb.ko
[/B]
lib/modules/2.6.31-10-generic/kernel/drivers/staging/at76_usb/at76_usb.ko
/lib/modules/2.6.31-11-generic/kernel/drivers/staging/at76_usb/at76_usb.ko

**find /lib -iname at76_usb.ko | xargs grep --text "Atmel at76x USB Wireless LAN Driver "**
/lib/modules/2.6.31-10-generic/kernel/drivers/staging/at76_usb/at76_usb.ko:<6>Atmel at76x USB Wireless LAN Driver 0.17 unloading
/lib/modules/2.6.31-10-generic/kernel/drivers/staging/at76_usb/at76_usb.ko:<6>Atmel at76x USB Wireless LAN Driver 0.17 loading
/lib/modules/2.6.31-11-generic/kernel/drivers/staging/at76_usb/at76_usb.ko:<6>Atmel at76x USB Wireless LAN Driver 0.17 unloading
/lib/modules/2.6.31-11-generic/kernel/drivers/staging/at76_usb/at76_usb.ko:<6>Atmel at76x USB Wireless LAN Driver 0.17 loading

---

### Post by claudio70b on 2009-10-03
2009-09-15 Greg Kroah-Hartman send a patch to delete the at76_usb driver (from drivers/staging), because meanwhile a new project was started/derived since linux 2.6.30 (at76c50x-usb, maintained by Kalle Valo)...

So it is possible that the Ubuntu kernel team hasn't noticed the change and distributes the wrong version of the driver or whatever

Post please ```
find /lib/modules -iname '*at76*'
``` and if it shows some at76c50x files, you can try removing the at76_usb.ko-s (or move the to your home i.e.) -- unplug the device first(!) --, and running ```
sudo depmod -aeq
``` and hope that (well -> try whether) the new in-kernel driver is used and works. :-D

Otherwise I guess I have to download the beta and invest by my very self :P

---

### Post by pedor on 2009-10-04
I get 
```
/lib/modules/2.6.31-11-generic/kernel/drivers/net/wireless/at76c50x-usb.ko
/lib/modules/2.6.31-11-generic/kernel/drivers/staging/at76_usb
/lib/modules/2.6.31-11-generic/kernel/drivers/staging/at76_usb/at76_usb.ko
```

I try to remove at76_usb.ko and run "sudo depmod -aeq" but  wlan0 is still unusable. Then i try to blacklist the at76c50x-usb module and now it uses the (old?) at76_usb and the card works again  :D :D

---

### Post by claudio70b on 2009-10-04
Ah, still both included. Yep, now you use the "more or less old" driver again. ;-)

So one can run **gksudo gedit /etc/modprobe.d/blacklist.conf** and add the line **blacklist at76c50x_usb** to the file, run **sudo depmod -aeq** to get it working again.

So I wonder why the new driver (at76c50x_usb) doesn't work (yet; for you?) and what they will change in the next releases.

---

### Post by pedor on 2009-10-04
It is only to add blacklist at76c50x_usb in /etc/modprobe.d/blacklist.conf

But now I get a gui-messages  "Your system encountered a serious kernel problem. Your system might become unstable now and might need to be restarted.\"

And now the system crash sometimes. :(
I don't know what I should do now ](*,)

---

### Post by onerbe on 2009-10-09
Hi

I had the same problem when I updated to 9.10, and the only way to get the wireless working was set the DNS servers and search domains to manual configuration.

This is not a fix, but will help you to get wireless working until the final release.

Hope it helps!

Kind Regards

---

### Post by bichopro on 2009-11-02
same problem here, any solution?

I install backport modules but crash the kernel.

---

### Post by Feareilo on 2009-11-03
claudio70b's post (#5 in this thread) solves everything.

---

### Post by der011 on 2009-11-03
Same problem here, unable to compile driver (0.17 from berlios, kernel 2.6.31), any patch?

---

### Post by Feareilo on 2009-11-03
claudio70b's post (#5 in this thread) solves everything.

---

### Post by Feareilo on 2009-11-04
Sorry everyone. I was runnin' my mouth like an idiot without trying  claudio70b's solution. It totally and completely works. Please excuse my douchebagism.

---

### Post by submain on 2009-11-15
Well, I think I took the hardcore way out of this, but it seems to be working for me.

The driver in the berliOS did not have support for some new structs in the new 2.6.31 kernel. I modified it in order for it to compile on the new kernel.

The patched source code can be found here:

[http://www.leo-sa.com/?p=70](http://www.leo-sa.com/?p=70)

---

### Post by bjk03 on 2009-11-28
> **claudio70b said:**
> Ah, still both included. Yep, now you use the "more or less old" driver again. ;-)

So one can run **gksudo gedit /etc/modprobe.d/blacklist.conf** and add the line **blacklist at76c50x_usb** to the file, run **sudo depmod -aeq** to get it working again.

So I wonder why the new driver (at76c50x_usb) doesn't work (yet; for you?) and what they will change in the next releases.

THANK YOU!!! I finally have wireless on 9.10!! Wish I would have found this thread sooner.

---

### Post by drazgo on 2009-11-30
your solution worked perfectly mate! thanks so much! :p

---

### Post by kbm on 2009-12-03
Adding the blacklist line has my wireless connection working, so thanks a bunch for that.  I'm not sure I'm out of the woods yet though...

Maybe I'm being daft here, but **depmod -aeq** complains that it needs the -E or -F option and q does not even seem to be a valid option.

Would not be worried about it too much, except that I get the kernel crash message now too.

Anyway, I used locate to find System.map and ran the command **depmod -aeq -F /boot/System.map-2.6.31-14-generic**, but I still get the kernel crash.  Have not used the system much since, but it still seems fine.

Tried to report the problem, and the reporting tool says that something is not a genuine Ubuntu module (although I installed from the cd and have not enabled any repos or even run an update yet).

So what simple, stupid mistake am I making here?  Also, assuming my running depmod did (or will do) something, will I need to re-run it every time I update the kernel (using Ubuntu repos)?

Almost forgot... the new, non-working driver detected that my router used WPA.  The old, working driver only gave me a list of routines that included WEP, LEAP, and two others, but not WPA.  I just went back to WEP with my router, but was wondering if this was normal/expected?

---

### Post by chris1379 on 2009-12-12
I may be out of place here but I am trying to get my WUSB11 v2.6, which uses this chip, in Ubuntu 8.04. The patch from claudio70b didn't work I think cause I'm using the wrong version of Ubuntu.
 
Chris

---

### Post by inovermyhead on 2010-02-12
This is outstanding.  I upgraded from 9.04 to 9.10 a couple of days ago and ran across the same problem described here.  The method in post #5 also worked for me.  Thanks.

A couple of cautions for the less experienced like myself.  First, I think there was a minor typo above, and the entry to blacklist.conf is actually **blacklist at76c50x-usb** not **blacklist at76c50x_us**b.
Second, I got the same error reported by kbm above when I tried to execute **depmod -aeq**.  I didn't try to work around it though, I just rebooted and my wireless came up working like a charm and has been working great since.

---

### Post by inovermyhead on 2010-02-27
Well, this wireless problem is now back for me unfortunately.  

My mythtv box has a version of ATI GPU(HD3200, R600 based) that I've been unable for going on 9 months now to get to perform adequately at full HD resolution with HDMI audio using an AMD 5050E processor.  I've tried multiple open source driver versions and a whole series of Catalyst driver versions, all with mixed but ultimately unsatisfactory results.  Most recently I've been using an open source radeonhd driver but performance is still not good enough.  From what I've been reading, a very recent version of open source ati radeon driver from the xorg-edgers ppa might finally do the trick.  Unfortunately, this would also require upgrading to a 2.6.33 kernel.

I waited with bated breath until it looked like 2.6.33 was stable enough to make the leap.  When 2.6.33 final came out a few days ago I got up the nerve.  After having this wireless problem with the Karmic upgrade, I was sort of anticipating similar problems, and I wasn't disappointed.  I used the pre-built binaries from the kernel mainline PPA and they installed just fine.  Upon reboot I had no wireless recognized at all, so far worse than the Karmic upgrade.  No real surprise there.  I'd read ahead and seen that it was recommended to also upgrade to the compat wireless package from here:

 /[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

so I already had these sources on hand for 2.6.33.  Indeed, before building and installing these there was no at76_usb OR at76c50x-usb driver present on my system for the new kernel.   After building and installing the compat wireless package, the at76c50x-usb driver was installed(I first removed the blacklist entry, btw).  After reboot, I got the exact same default behavior that I had with the Karmic upgrade, i.e. the network manager/nm-applet recognize the availabe access points, but are unable to connect to any of them.  My solution last time, based on the recommendations in this thread, was to blacklist the new at76c50x-usb driver, allowing the system to fall back to the older at76_usb driver from older kernel releases, since Karmic installed both drivers.  That worked like a charm.

Which brings me to my current problem.  The legacy at76_usb driver appears to have now been retired completely in favor of the newer at76c50x-usb driver, going back to kernel 2.6.32 in fact, so this workaround would not appear to be an option any more.  I'm not sure what my options are, but it would seem I either have to figure out how to build an at76_usb driver for 2.6.33(which I'm not sure it's even compatibe with) and continue to avoid(i.e. blacklist) the newer driver, or troubleshoot why at76c50x is giving me problems in the first place and find a way to work around it instead of without it.  The second option would seem safer so I'll start by going through the /var/log/daemon logs and see if I can get any clues.  Any tips would be welcome.  As my name indicates, I'm in waaay over my head already.

---

### Post by michall on 2010-04-06
For me new driver at76c50x-usb was not working under Lucid, because I had not installed atmel firmware. If you see an error in syslog after connecting usb adapter to computer, try

```
sudo apt-get install atmel-firmware
```Maybe this will solve your problem as well.

---

### Post by bichopro on 2010-04-29
the solution on post #5 work for me on karmic but today i install lucid lynx and can't see the device. i delete the blacklisted line and install the atmel-firmware (#20) now i can see the device but can't connect my wifi. any idea?
sorry my bad english

---

### Post by bichopro on 2010-04-29
bump

---

### Post by bichopro on 2010-04-30
bump

---

### Post by bichopro on 2010-05-01
bump

---

### Post by bjk03 on 2010-05-02
Ok so I upgraded from 9.10 to 10.04 and of course the wireless didn't work. So I commented out the black list line and installed the firmware as recommended in post #20. I can now see my wireless network but I cannot connect to it. What can I try now?

---

### Post by bichopro on 2010-05-02
> **bjk03 said:**
> Ok so I upgraded from 9.10 to 10.04 and of course the wireless didn't work. So I commented out the black list line and installed the firmware as recommended in post #20. I can now see my wireless network but I cannot connect to it. What can I try now?
same situation here! please help!

---

### Post by bjk03 on 2010-05-03
Apparently my usb adapter doesn't like the at76c50x-usb driver even after installing the firmware. The reason the blacklist doesn't work is that at76 was removed from the kernel. So I have a different adapter on order. [http://ubuntuforums.org/showthread.php?t=1471481]("http://ubuntuforums.org/showthread.php?t=1471481")

---

