---
title: "ATI Catalyst 6.7 For Linux"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by nimrod_abing on 2006-07-30
ATI has just released a new driver package for Linux. The new version ATI Catalyst 6.7 can be found [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.27.10.html").

Although there is an installer available, I really prefer getting as much of my installed software as .deb packages from the official sources. I'm wondering if the fglrx and restricted kernel driver packages will get updated with these soon. Or do I have to wait until "Edgy" to be able to use the updated ATI drivers?

---

### Post by whatever on 2006-07-30
[list][*]there is already a thread for this driver version: [http://www.ubuntuforums.org/showthread.php?t=224928](http://www.ubuntuforums.org/showthread.php?t=224928)
[*]as long as a new version does not fix critical bugs it will probably never get into the dapper repositories
[*]if you want to use it anyway, you can do a manual install ([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)). but don't forget that you will have to rebuild the kernel module after updates then.[/list]

---

### Post by Dirhael on 2006-07-30
I installed this driver yesterday, and today I'm back to the previous release. Why is that you ask? Well, while the older driver certainly has its problems, the new one was worse on my system. To start off with, it didn't improve anything at all of what I needed it to improve (stability, video quality etc.). Secondly, it re-introduced the old bug of freezing X when trying to log out or reset X, or even when trying to shutdown the system. This particular bug was more then enough to make me drop this release. Here's hoping for better luch next time... :)

Oh, and I'm using a X1600XT (PCI-E) card in case anyone was wondering.

---

### Post by nimrod_abing on 2006-07-30
> **whatever said:**
> [list][*]there is already a thread for this driver version: [http://www.ubuntuforums.org/showthread.php?t=224928](http://www.ubuntuforums.org/showthread.php?t=224928)
[*]as long as a new version does not fix critical bugs it will probably never get into the dapper repositories
[*]if you want to use it anyway, you can do a manual install ([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.27.10_drivers_in_Ubuntu_Dapper_Manually)). but don't forget that you will have to rebuild the kernel module after updates then.[/list]

[LIST]
[*]OK, thanks. Will participate in that thread later...
[*]The current version 8.25.18 that comes with Dapper has a bug in libGL.so that prevents accelerated rendering from working on R9200 cards. I don't know if this new release fixes this bug yet. I wouldn't consider it critical since it can easily be fixed by replacing libGL.so with an older one that works.
[*]Ah, I've used that once before and am not afraid to use it again :)
[/LIST]

---

### Post by nimrod_abing on 2006-07-30
> **Dirhael said:**
> I installed this driver yesterday, and today I'm back to the previous release. Why is that you ask? Well, while the older driver certainly has its problems, the new one was worse on my system. To start off with, it didn't improve anything at all of what I needed it to improve (stability, video quality etc.). Secondly, it re-introduced the old bug of freezing X when trying to log out or reset X, or even when trying to shutdown the system. This particular bug was more then enough to make me drop this release. Here's hoping for better luch next time... :)

Oh, and I'm using a X1600XT (PCI-E) card in case anyone was wondering.

Typical of the "one step forward, two steps backward" when it comes to ATI drivers :)

Anyway, I'm willing to try installing this on my system if I read reports of GLX working on R9200. I'm using the libGL.so from an older driver release on my system.

It seems that this new driver introduces more problems rather than fixing the old ones. So I guess this means that this driver will never be in Dapper repositories...

---

