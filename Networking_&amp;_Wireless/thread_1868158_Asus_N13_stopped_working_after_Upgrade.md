---
title: "Asus N13 stopped working after Upgrade"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by Stupendous man on 2011-10-23
Hello,

I recently updated to version 11.10 via the update manager. Prior to that I was using the previous release with my Asus N13 wireless USB adapter. The adapter didn't work at all until I followed the steps listed in this thread:

[http://ubuntuforums.org/showthread.php?t=1766327](http://ubuntuforums.org/showthread.php?t=1766327)

So now, I still see the adapter present as I did before, but it doesn't connect. The icon shows no network adapters available, and when I check the preferences, I still see my password and stuff displayed under the wireless section, and the "connect automatically" checkbox is checked, but it just doesn't...

Does anyone have any idea why?

---

### Post by jawilljr on 2011-10-23
That's because the Ralink staging drivers have been removed by [this commit](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fefecc6989b4b24276797270c0e229c07be02ad3)

Do this:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and remove these:

```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```

Reboot and try and connect.

Jerry

---

### Post by Stupendous man on 2011-10-23
Well that did the trick nicely. Thanks for the rapid help. You rock.
:popcorn:

---

### Post by jawilljr on 2011-10-23
No problem...glad to help.

Jerry

---

### Post by robotdna on 2011-10-25
Same thing happened to my E-350 based mini-itx system.
1. Installed Ubuntu 11.04 
2. Asus USB N13 did not work
3. used workaround to resolve conflict (from this forum) by adding rt2800usb to blacklist.conf

4. Upgraded distribution to 11.10
5. Asus usb N13 stopped working
6. Tried workaround from Jerry (this thread) but usb N13 still not working

---

### Post by robotdna on 2011-10-26
> **robotdna said:**
> Same thing happened to my E-350 based mini-itx system.
1. Installed Ubuntu 11.04 
2. Asus USB N13 did not work
3. used workaround to resolve conflict (from this forum) by adding rt2800usb to blacklist.conf

4. Upgraded distribution to 11.10
5. Asus usb N13 stopped working
6. Tried workaround from Jerry (this thread) but usb N13 still not working


I still have the problem and starting to think of getting different USB wifi adapter, **any recommendations for better supported usb adapter?**
Also another option I have is to reinstall ubuntu 11.04 and use workaround #3 (not for too long though as I would hate to not upgrade OS with various security fixes)

Please let me know if anyone has figured out solution for this.

---

### Post by robotdna on 2011-10-27
I reinstalled older ubuntu (11.04) and used workaround from [chili555]("http://ubuntuforums.org/member.php?u=35909") mentioned in another thread here.

Just had to add 
blacklist rt2800usb
in /etc/modprobe.d/blacklist.conf
and reboot.

Can anyone recommend an usb adapter that will keep working out of box in future Ubuntu releases?
I do not want to keep building driver everytime after upgrading distribution, that defeats the reason I moved to Ubuntu from other distributions.

---

