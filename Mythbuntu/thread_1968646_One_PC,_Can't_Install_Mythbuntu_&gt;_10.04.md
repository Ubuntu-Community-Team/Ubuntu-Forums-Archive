---
title: "One PC, Can't Install Mythbuntu &gt; 10.04"
date: 2012-04-29
forum: Mythbuntu
---

### Post by uncle hammy on 2012-04-29
I have one PC that I have not been able to install Mythbuntu > 10.04...ever.  With *every* version of Mythbuntu (yes, I have tried them all -> 10.10, 11.04, 11.10, 12.04...32 and 64 bit) beyond 10.04, the installer won't even boot.  It hangs at Freeing initrd memory: 20somethingk freed.  If I try to do an upgrade instead of a fresh install, then the system simply won't boot afterwards.

I always boot from a USB drive with unetbootin, but have also tried hooking up an ide dvd drive to get it going.  I have swapped out ram, changed BIOS to failsafe and optimized defaults, upgraded the BIOS to it's most current...everything short of a new motherboard, which at this point would essentially mean a new PC.

At one time I was able to do an upgrade, which wouldn't boot, then use an old (8.04 IIRC) live cd to put acpi=off in my boot parameters to get it to run, but then the system wouldn't shut down (it would halt, but not actually power down).  Outlined in my thread here [http://ubuntuforums.org/showthread.php?t=1637397](http://ubuntuforums.org/showthread.php?t=1637397)

Now, this system is about 3-4 years old, but I certainly wouldn't characterize it as ancient, and *more* than capable of running 12.04 (AMD X2 4600, 4GB ram, etc).  

It's really starting to annoy the you know what out of me.  Anyone have any ideas how I can get this thing upgraded?

---

### Post by TrueBlueBlooded on 2012-04-29
I also have a PC that will not boot any version > 10.04.  I  eventually figured out that the graphics card was the culprit and that I  needed to use the NOMODESET kernel boot option.

Give this a read,  perhaps one of the kernel boot options will do the trick:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

-TBB

---

### Post by uncle hammy on 2012-04-29
Thanks for the link, nomodeset has no effect on this machine.  The only option of all the ones listed there that works is acpi=off, which as I indicated causes the machine to not be able to shutdown or reboot without physically pushing the power button.  I don't understand how this machine can have *zero* acpi issues with 10.04 and below, and suddenly with the advent of 10.10, Mythubtu is useless on it.

---

### Post by uncle hammy on 2012-04-29
OK, so I got the installer to boot using acpi=off and everything installed fine (I read something about "apm power_off=1" should fix the shutdown issue so I thought I'd give that a try).  I modified /etc/default/grub via live cd and put in acpi=off apm power_off=1.

Now, 12.04 won't boot again (booted fine with the installer with that parameter).

I get a bunch of nonsense (to me anyways)....

[0.288009] Stack:  
[0.288009] Call Trace:
[0.288009] <IRQ>
[0.288009] <EOI>
[0.288009] Code: 09 48 89 c3b8, etc, etc, etc

[0.288011] Stack:  
[0.288011] Call Trace:
[0.288011] <IRQ>
[0.288011] <EOI>
[0.288011] Code: 09 48 89 c3b8, etc, etc, etc

So I removed the "apm power_off=1" part and same results.

I thought the battle cry was "Linux just works"?

---

### Post by superm1 on 2012-04-29
So this is most certainly a kernel bug of sorts related to your hardware/BIOS setup.  Newer hardware that Canonical is working with the OEM's/vendors to certify is less likely to run into problems as the OEM's and vendors can fix BIOS issues ahead of time, but older stuff sometimes will just rot support wise. If you can get it to boot up/install, what you need to do is grab the latest kernel packages from here that match your architecture:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

If those still fail, then while booted up from them (with whatever arguments you need), file a bug against the kernel using this command:

```
#ubuntu-bug linux
```

You can add all sorts of description about last time it worked, what you've had to do etc.  *Hopefully* the kernel team will be able to help work it out and get this fixed in a future point release of 12.04.

---

### Post by uncle hammy on 2012-04-29
At this point, I am unable to get it to boot with *any* arguments....even the ones that allowed the installer to go.

[http://ubuntuforums.org/showthread.php?t=1968798](http://ubuntuforums.org/showthread.php?t=1968798) I have the same issue / mobo as this post.

The issue seems to have been reported...with not much interest....

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/712125](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/712125)

---

### Post by uncle hammy on 2012-04-29
OK, found this and disabled HPET in the BIOS per the last post, and I can now boot without any extra arguments....

[http://ubuntuforums.org/showthread.php?t=1843810&page=2](http://ubuntuforums.org/showthread.php?t=1843810&page=2)

---

