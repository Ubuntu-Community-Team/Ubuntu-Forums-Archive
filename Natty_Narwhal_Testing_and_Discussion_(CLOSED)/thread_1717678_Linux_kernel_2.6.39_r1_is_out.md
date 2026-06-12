---
title: "Linux kernel 2.6.39 r1 is out"
date: 2011-03-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-03-30
Here is the announcement:

[https://lkml.org/lkml/2011/3/29/351](https://lkml.org/lkml/2011/3/29/351)

---

### Post by lucazade on 2011-03-30
> **Harry33 said:**
> Here is the announcement:

[https://lkml.org/lkml/2011/3/29/351](https://lkml.org/lkml/2011/3/29/351)

there are also debs in kernel ppa (not patched)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/)

---

### Post by dino99 on 2011-03-30
Something that catch my attention:

- It _feels_ like it was all drivers, filesystems and irq cleanups.
-  we had a fair amount of VFS cleanup

Looks very interesting to me, i like cleaning stuff :)

---

### Post by jfernyhough on 2011-03-30
Hmm... do I try it or do what I normally do and wait until rc3?

(Try it of course! :D)

--edit
Bah... nvidia fails to build in dmks.

---

### Post by gnomeuser on 2011-03-30
The DRM updates look promising and naturally the continued VFS locking changes should prove interesting.

I am pretty pleased with this cycle and look forward to .40 opening the show for more fun.

---

### Post by KegHead on 2011-03-30
Hi!

I'm waiting a few days!

.38 seems ok right now.

KegHead

---

### Post by cariboo on 2011-03-30
Natty will stay with 2.6.38, we'll probably see the .39 version in Oneiric Ocelot.

---

### Post by alazou on 2011-03-31
I've been eager to try nouveau with page flipping :DD. In 2.6.38 I already don't see any difference between the blob and nouveau other than a 8-10 degree C temperature increase <3

---

### Post by petersonja on 2011-03-31
How can I try it on Natty?

---

### Post by lucazade on 2011-03-31
> **petersonja said:**
> How can I try it on Natty?

For i386 32bit use the following commands (for 64bit take deb packges from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/"))

```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/linux-headers-2.6.39-020639rc1-generic_2.6.39-020639rc1.201103300912_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/linux-headers-2.6.39-020639rc1_2.6.39-020639rc1.201103300912_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/linux-image-2.6.39-020639rc1-generic_2.6.39-020639rc1.201103300912_i386.deb
sudo dpkg -i *.deb

```

---

### Post by alazou on 2011-03-31
That was nice :) ! it feels snappier than the blob, and the temperature levels are much closer to it.

The only problem is that it doesn't detect my wireless card so I can't use it :'(.
Running kde 4.6 with compositing and blur enabled.
My wireless card is a intel 4965 AGN

---

### Post by lucazade on 2011-03-31
Unfortunately kernels from mainline ppa lack some patches, usually applied by the ubuntu kernel team, like apparmor and ureadahead.

---

### Post by alazou on 2011-03-31
Yeah that's been an issue for me since I switched to the .38 kernel

---

### Post by lucazade on 2011-03-31
> **alazou said:**
> Yeah that's been an issue for me since I switched to the .38 kernel

tried it now, brake wireless also for me (ath5k) :)

---

### Post by petersonja on 2011-03-31
Is it don't work well with nvidia-current (270.30)? Because it isn't boot...

---

### Post by alazou on 2011-03-31
> **lucazade said:**
> tried it now, brake wireless also for me (ath5k) :)
That's a real pity. I'm really trying to find a way to make it work, but I can't find any meaningful error message

> **petersonja said:**
> Is it don't work well with nvidia-current (270.30)? Because it isn't boot...
Maybe, like someone said earlier, the dkms won't load nvidia kernel module

---

### Post by Locke_99GS on 2011-03-31
It's not the fault of dkms that it won't build, rather an incompatibility between the current nvidia drivers (270.29 & 270.30) and 2.6.39. The driver won't manually build against 2.6.39, either.

Hopefully in short order there will be kernel patches to let the nvidia driver work with it, or nvidia will release a new driver that is compatible.

---

### Post by plun on 2011-03-31
All you need is a file or a symlink from the 2.6.38 kernel, **smp_lock.h**

Put it in /usr/src/linux-headers-2.6.39-020639rc1-generic/include/linux

Both a nvidia install and a dkms install works.


(home brewed solution so no guarantees.....:D  , I just checked the nvidia-installer log  )



--

---

### Post by ngsupb on 2011-03-31
well wifi doesn't work here too :( can't use.

But nouveau drivers faster around in 3 times :D Not as good as nvidia's but it is much better than currently.

---

### Post by alazou on 2011-03-31
> **ngsupb said:**
> well wifi doesn't work here too :( can't use.

But nouveau drivers faster around in 3 times :D Not as good as nvidia's but it is much better than currently.

How did you evaluate the speed boost ?
I have to say, the figure tool of matlab freezes a lot for like 10s with nouveau... oh well better then having to wait 2 seconds after typing before a character appear when using kate and nvidia blob.

---

### Post by Locke_99GS on 2011-03-31
> **plun said:**
> All you need is a file or a symlink from the 2.6.38 kernel, **smp_lock.h**

Put it in /usr/src/linux-headers-2.6.39-020639rc1-generic/include/linux

Both a nvidia install and a dkms install works.


(home brewed solution so no guarantees.....:D  , I just checked the nvidia-installer log  )



--

Awesome. I'll give that a shot later.

---

### Post by ngsupb on 2011-04-01
> **alazou said:**
> How did you evaluate the speed boost ?
I have to say, the figure tool of matlab freezes a lot for like 10s with nouveau... oh well better then having to wait 2 seconds after typing before a character appear when using kate and nvidia blob.
Don't take my words too close. Just glxgears info and dragging windows around.

As I remember phoronix did more accurate tests on games. You can check there.

---

### Post by Locke_99GS on 2011-04-01
@plun
Linking to copying smp_lock.h didn't work for me. 

2.6.39 finally did away with the BKL. smp_lock.h is the header for BKL support. I did get nvidia 270.29 (haven't tried 270.30) to compile and boot without issue though by commenting out the include directive to smp_lock.h in the nvidia sources.

The real reason I was excited about the 39 kernel was proper support for the realtek 8192cu driver, which my daughter's computer used for network access. It is sad, though, that the 39 kernel from Ubuntu's mainline kernel ppa didn't enable this to be built at all. 

After recompiling a fresh kernel (and less generic, since I configured this one myself) I'm glad to say that with 8192cu support enabled and the nvidia sources fixed to not rely on the BKL, my daughter will (when she gets home from school) be able to enjoy running the 39 kernel. I haven't had any network drops with the kernel's 8192 driver, where I had with the upstream driver. I wonder what was changed.

---

### Post by dino99 on 2011-04-01
remind that its a 1st draft, so be patient, usualy rc3 is usable but before nothing is sure

---

### Post by KegHead on 2011-04-01
Hi!

Using on my desktop w/10.10.

No problems.

KegHead

---

### Post by darryn.smith on 2011-04-02
Decided to try 2.6.39.  And found it actually fixed a few issues I was having on my HP Envy 14.  On previous natty 2.6.38-7 the wireless switch (F10) caused instant hard lockup.  Rebooting resulted in lockup as well.  The only way to resolve it was to boot into windows activate the wireless (f10) and reboot into Ubuntu.  

Also high traffic on the Broadcom  BCM43224 caused the wireless to drop the connection and refuse to rejoin the network. 

With 2.6.39 the wireless works as it should. At least it seems to. 


2.6.39-020639rc1-generic x86_64 

So far so good.

---

### Post by ronacc on 2011-04-02
I'm up and running with it on amd64 with the nvidia 270.30 driver , plun's fix worked as advertised . I hope this cures a couple of showstoppers for me that have persisted since the start of 2.6.38 , I bugged them as regressions and no action yet . Looks good so far but I wont be sure till it cooks for awhile and a couple of reboots .:P

---

### Post by rusty725 on 2011-04-03
installed it today seems a bit faster than 2.6.38-2, 270.30 installed as suggested above. seems more responsive.

---

### Post by VinDSL on 2011-04-03
> **darryn.smith said:**
> Decided to try 2.6.39. [...]

So far so good.
Dittos!

Banshee works.  Chat works.  Chromium works.

What else does a guy need?!?!?  :D

---

### Post by plun on 2011-04-03
> **ronacc said:**
> I'm up and running with it on amd64 with the nvidia 270.30 driver , plun's fix worked as advertised . I hope this cures a couple of showstoppers for me that have persisted since the start of 2.6.38 , I bugged them as regressions and no action yet . Looks good so far but I wont be sure till it cooks for awhile and a couple of reboots .:P

Yep... installed this kernel again today after my complete reinstall yesterday.

Output from a dkms/nvidia-current reinstall

[http://paste.ubuntu.com/588868/](http://paste.ubuntu.com/588868/)


--

---

### Post by KegHead on 2011-04-03
Hi!

Still working.

Waiting for r2.

KegHead

---

### Post by KegHead on 2011-04-08
Hi!

Installing r2 today on natty.

KegHead

---

### Post by KegHead on 2011-04-08
Hi!

Installed rc2 today.

Was not asked to restart.

Anyone?

KegHead

---

### Post by VinDSL on 2011-04-08
Where did you find the r2 image file?  I've been watching for it.

v2.6.39-rc2-natty only contains the header file...

I see 2.6.39-999 is present in the dailys:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-08-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-08-natty/)

Is that what you used?!?!?

---

### Post by KegHead on 2011-04-08
kernel.ubuntu.com/~kernel-ppa/mainline

---

### Post by VinDSL on 2011-04-08
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc2-natty/)

...only contains the headers -- no images.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-08-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-08-natty/)

...contains the headers and images.

Which one did you use?

---

### Post by VinDSL on 2011-04-08
I just installed 2.6.39-999 (which is 2.6.39-rc2, natty abinum:999) and it built OK.

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel2
vindsl@Zuul:~/Downloads/Kernel2$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
(Reading database ... 226922 files and directories currently installed.)
Preparing to replace linux-headers-2.6.39-999 2.6.39-999.201104080911 (using linux-headers-2.6.39-999_2.6.39-999.201104080911_all.deb) ...
Unpacking replacement linux-headers-2.6.39-999 ...
Preparing to replace linux-headers-2.6.39-999-generic 2.6.39-999.201104080911 (using linux-headers-2.6.39-999-generic_2.6.39-999.201104080911_i386.deb) ...
Unpacking replacement linux-headers-2.6.39-999-generic ...
Preparing to replace linux-image-2.6.39-999-generic 2.6.39-999.201104080911 (using linux-image-2.6.39-999-generic_2.6.39-999.201104080911_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.39-999-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-headers-2.6.39-999 (2.6.39-999.201104080911) ...
Setting up linux-headers-2.6.39-999-generic (2.6.39-999.201104080911) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-image-2.6.39-999-generic (2.6.39-999.201104080911) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-999-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104080911 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104080911 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.30)...                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-020639rc1-generic
Found initrd image: /boot/initrd.img-2.6.39-020639rc1-generic
Found linux image: /boot/vmlinuz-2.6.39-999-generic
Found initrd image: /boot/initrd.img-2.6.39-999-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernel2$ 

```

Let's see if it boots now.

Wish me luck.  LoL!  :D

---

### Post by VinDSL on 2011-04-08
w00t!  #5 is alive...  ;)


[INDENT]**Natty beta 1 / Linux 2.6.39-999-generic kernel / nVidia 270.30 / Conky / conkyForecast / Lua**    (Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-8-apr-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-apr-2011(2).png")[/INDENT]

---

### Post by KegHead on 2011-04-08
Headers only.

I'll look at your site.

KegHead

---

### Post by KegHead on 2011-04-08
Hi!

It worked!

Thanks!

KegHead

---

### Post by Locke_99GS on 2011-04-08
Glancing over the config for rc2 from the PPA, they still haven't enabled the new wireless drivers. (one in particular I look forward to) Matter of fact, it looks like all natty kernels share the same config, all maverick kernels share a config, etc...

If this is the case, 39+ kernels will only get 38 features. Lame. I'll continue building my own from kernel.org.

---

### Post by Locke_99GS on 2011-04-08
edit: double post

---

### Post by KegHead on 2011-04-09
Hi VinDSL!

Let's keep this thread going to stay on the cutting edge!

KegHead

---

### Post by lucazade on 2011-04-09
I don't see updates.. why bumping?

there are only headers for 2.6.39rc2

---

### Post by KegHead on 2011-04-09
Hi!

Have you checked out post #36?

My link was about two days old.

KegHead

---

### Post by lucazade on 2011-04-09
> **KegHead said:**
> Hi!

Have you checked out post #36?

My link was about two days old.

KegHead

Didn't notice the other directory, thanks

---

### Post by VinDSL on 2011-04-09
> **KegHead said:**
> Hi VinDSL!

Let's keep this thread going to stay on the cutting edge!

KegHead


Heh!  Will do!  :D


> **lucazade said:**
> I don't see updates.. why bumping?

there are only headers for 2.6.39rc2

They have dailys, at the top of the mainline page.

I just updated 2.6.39-999-generic a few minutes ago...

```

commit:0c3efe54d0165cecf0698b468e253577b555dde6 series:natty abinum:999
full_version<2.6.39-rc2>
version<2.6.39>
long<v2.6.39-rc2-106-g0c3efe5>
abinum<999>

```

Come on in.  The water's fine!  ;)

---

### Post by VinDSL on 2011-04-13
All hail!  Linux 2.6.39 rc3...  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-13-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-apr-2011.png")[/INDENT]


Unity has been coming along nicely!

Might as well use the latest kernel too.  ;)

BTW, if you're running nVidia 270.30, you still need to implement the **smp_lock.h** hack on page 2...

---

### Post by KegHead on 2011-04-13
Hi!

Thanks!

Downloading now!

KegHead

---

### Post by Harry33 on 2011-04-13
> **VinDSL said:**
> All hail!  Linux 2.6.39 rc3...  :D
Unity has been coming along nicely!
Might as well use the latest kernel too.  ;)

BTW, if you're running nVidia 270.30, you still need to implement the **smp_lock.h** hack on page 2...

Have you tried the latest nvidia-current_270.41.03 from xorg-edgers?

---

### Post by dino99 on 2011-04-13
rc3 i386 feedback:

nvidia-current fail with genuine natty package but works with x-swat ppa (270.41)
dont get errors logged
smaller ram footprint
but higher cpu activity
looks like a RT kernel: high reactivity

very pleased :)

---

### Post by KegHead on 2011-04-13
Hi!

Downloaded and running perfectly.

KegHead

---

### Post by Harry33 on 2011-04-13
> **dino99 said:**
> rc3 i386 feedback:
nvidia-current fail with genuine natty package but works with x-swat ppa (270.41)
dont get errors logged
smaller ram footprint
but higher cpu activity
looks like a RT kernel: high reactivity
very pleased :)

Does it work out of the box, even w/o symlinking smp_lock.h?

---

### Post by VinDSL on 2011-04-13
> **Harry33 said:**
> Have you tried the latest nvidia-current_270.41.03 from xorg-edgers?
No.

I dropped xorg-edgers off my sources list, a while back.  I cannot remember why...  :D

Maybe it's time to revisit them.

---

### Post by Harry33 on 2011-04-13
> **VinDSL said:**
> No.
I dropped xorg-edgers off my sources list, a while back.  I cannot remember why...  :D
Maybe it's time to revisit them.

The same nvidia-current_270.41.03 is in X Updates too. In fact Xorg-edgers has a copy of that one.
Here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

I did only download the driver and install it with dpkg.

---

### Post by VinDSL on 2011-04-14
Back to the "999" Daily kernel...

```

vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.39-999-generic #201104130905 SMP Wed Apr 13 10:28:53 UTC 2011 i686 i686 i386 GNU/Linux 

```

Heh!  Are you still in?!?!?  :D

---

### Post by KegHead on 2011-04-14
Hi!

Using 04-13.

No problems.

Looking for 4-14.

KegHead

---

### Post by dino99 on 2011-04-14
just wait for next rc, there is no change made by ubuntu right now, so no need to test the dailies

---

### Post by KegHead on 2011-04-14
Hi!

Thanks for the update.

I'll hold off.

Please keep us updated with a good link!

KegHead

---

### Post by dino99 on 2011-04-14
> **KegHead said:**
> Hi!

Thanks for the update.

I'll hold off.

Please keep us updated with a good link! ::) do you know phoronix ? or kernel.org ?

KegHead

::)

---

### Post by KegHead on 2011-04-14
No,

I just download daily Natty.

KegHead

---

### Post by VinDSL on 2011-04-15
Interesting!  The updates are flowing hot n' heavy!

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel
vindsl@Zuul:~/Downloads/Kernel$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
(Reading database ... 268571 files and directories currently installed.)
Preparing to replace linux-headers-2.6.39-999 2.6.39-999.201104130905 (using linux-headers-2.6.39-999_2.6.39-999.201104141057_all.deb) ...
Unpacking replacement linux-headers-2.6.39-999 ...
Preparing to replace linux-headers-2.6.39-999-generic 2.6.39-999.201104130905 (using linux-headers-2.6.39-999-generic_2.6.39-999.201104141057_i386.deb) ...
Unpacking replacement linux-headers-2.6.39-999-generic ...
Preparing to replace linux-image-2.6.39-999-generic 2.6.39-999.201104130905 (using linux-image-2.6.39-999-generic_2.6.39-999.201104141057_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.39-999-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-headers-2.6.39-999 (2.6.39-999.201104141057) ...
Setting up linux-headers-2.6.39-999-generic (2.6.39-999.201104141057) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.41.03)...                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Setting up linux-image-2.6.39-999-generic (2.6.39-999.201104141057) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-999-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104130905 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.39-999.201104130905 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
 * dkms: running auto installation service for kernel 2.6.39-999-generic                                                                                                     
 *       nvidia-current (270.41.03)...                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-999-generic /boot/vmlinuz-2.6.39-999-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-020639rc3-generic
Found initrd image: /boot/initrd.img-2.6.39-020639rc3-generic
Found linux image: /boot/vmlinuz-2.6.39-999-generic
Found initrd image: /boot/initrd.img-2.6.39-999-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernel$ 

```


I assume, everyone knows how to read the changes.

[LIST]
[*]Myriad of updates, in the official repos, including...
[*]nvidia-current (270.41.03)
[*]The daily built ok!
[/LIST]

Time to clear out some (2-3 day-old) kernels, and reboot...  :D

BRB

---

### Post by KegHead on 2011-04-15
Hi!

Thanks VinDSL!

BTW-Are you having any problems w/VLC, UMPlayer?

KegHead

---

### Post by VinDSL on 2011-04-15
> **KegHead said:**
> Are you having any problems w/VLC, UMPlayer?
I use neither, sooo... no problem with either.  :D

I do use Banshee, and was having some problems, last night, but this is not unusual.

Banshee is under heavy development, and I was warned that it wouldn't be stable until the final release of Natty.

Anyway, sometimes things just happen for no reason.  Such is life, when you're riding on the razor's edge.

I haven't had any problems with Banshee today, and did nothing to fix it -- except for powering-down my PC, before going to bed.

Talking about sleep... 2.6.39 has been a snooze, so far.  ;)

---

### Post by KegHead on 2011-04-15
Hi!

Thanks for the reply!

I know I'm missing something, but what is it?

Anyone?

Thanks!

KegHead

---

### Post by MAFoElffen on 2011-04-16
Did I see a directory in the ppa there for an rc2?

I asked this earlier somewhere and was left unanswered.  I assume that these ppa's are for the Desktop kernel builds(?)  What about the server kernels?  How would I go about that for building a server kernel on the 2.6.39rc1? Anyone know?

---

### Post by dino99 on 2011-04-16
ah ah the googling mystery 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by alazou on 2011-04-16
Seems like my wireless card is considered legacy now, and they made another kernel build option : CONFIG_IWL4965=m for it. So the config from the ppa wouldn't detect my card cause of the config from the 2.6.38 that it uses. So I'm building the kernel right now. Quite slow on my poor XPSm1530 :'(

Couldn't wait any longer lol I __had__ to use this kernel cause of the nouveau goodies. Never had luck with Nvidia blob X KDE, and I get really decent hardware acceleration with nouveau now <3

---

### Post by KegHead on 2011-04-16
Hi!

I'm using daily...current.

Works for me.

Downloading 04-16 today I HOPE.

KegHead

---

### Post by matt_symes on 2011-04-16
What graphics cards are you guys using ?

---

### Post by MAFoElffen on 2011-04-16
> **MAFoElffen said:**
> I asked this earlier somewhere and was left unanswered.  I assume that these ppa's are for the Desktop kernel builds(?)  What about the server kernels?  How would I go about that for building a server kernel on the 2.6.39rc1? Anyone know?
No answer to that-- I think this is still in the spirit of the context of this thread.  For my own education on this, let me change my questions to something a little more generic...

Using "source" you would use either a config file from the last working kernel or an alternate config modified with your new configuration settings.  During a normal "update/upgrade" process that included kernel changes, it sees deb packages it in that ppa of the flavor of your kernel (for me -server or -pae, along with others for the desktops/architecture here).  But here you are talking about using alternate dev kernels in alt.ppa's...

In this ppa, there are debian packages of kernels.  Further up the tree is config files for flavours or types.

At the point in the tree where the kernel packages are, I don't know how these packages are setup to get the config file for the type of "build."  Does it look to see what "type" of config flavour it needs? Such as what is being used currently and what compares in the config  files in \~kernel-ppa/configs/natty?

As a deb package, I might be wrong, but I'm assuming it at least checks architecture, but flavour/type?  If not, I'm assuming that it is the default config is set to the -generic natty desktop kernel config file of the architecture being used.  

If it does check what "flavour/type of" then all these questions are moot and it just makes the right choice and installs the correct config file for the right type of kernel (desktop, server, powerpc, virtual...).  

If not, (or if someone needed a kernel for a different architecture or type than what is being used currently) then how does someone change it to point to the correct type/flavour? (Architecture would be just picking the correct arch-deb-package.)  Change the deb package by inserting/replacing the correct config file?  Replace the config file after the install? Start from scratch from source with an alternate .config file and apply all the patches?  

LOL--  Am completely wrong or am I just over-thinking this and making this much harder than it really is?  Just curious and wanting to understand what I'm "doing"... before I do something that I might have to back out of later.  (Not that I haven't already done that many times before!)

Cause you know the next adventure might be to test natty's package ubuntu-xen-server (Xen 4.0.x) with the new kernels...

---

### Post by Locke_99GS on 2011-04-16
The kernel is configured, then built according to that configure. You cannot change the configuration of the kernel after it has been compiled - the deb packaged kernels are pre-built apparently to the 2.6.38 natty generic config - this is why you don't get any of the new .39 features from the mainline ppa, they were configured using the .38 featureset. The packages you get are only architecture specific. The kernel metapackage you choose will determine whether you will receive generic/server/pae kernels, and only when that metapackage changes its dependency. With the mainline ppa not offering server configured builds, it won't pull in a server version of the latest mainline build.



The simplest method to deal with this, in my personal option, would be to just compile your own kernel. This gives you the ability to lean out the kernel (no need to build modules for things you will never have) and tune  and optimize some of the options to your specific needs. You also have the option here to apply whatever patches you choose to your kernel.

You can start with the config from your current kernel and built with that, or make further tweaks to it before building.

My kernels are relatively lean and only take about 20 minutes or so to compile. Bigger kernels take longer to build, and obviously older processors will take longer to build them also.

---

### Post by VinDSL on 2011-04-16
> **matt_symes said:**
> What graphics cards are you guys using ?
Mine is in my sig...  ;)


> XFX 7600GT 560M AGP (PV-T73A-UDF3)

Essentially:  nVidia GeForce 7600GT AGP


Courtesy: [Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150210")

---

### Post by VinDSL on 2011-04-16
> **MAFoElffen said:**
> LOL--  Am completely wrong or am I just over-thinking this and making this much harder than it really is?
Who knows?  Only you!

Most ppl, in the dev forums, tend to be a little neurotic (def - emotionally unstable or unusually anxious).  So, you're in good company.  LoL!  :D

I normally run Ubu on Liquorix kernels.

Linkage:  [http://liquorix.net/debian/pool/main/l/linux-liquorix-2.6/](http://liquorix.net/debian/pool/main/l/linux-liquorix-2.6/)

If they had a 2.6.39 kernel available, that's what I would be using.

In the meantime, I'll run the dailys, and hope Liquorix catches up soon...  :)

---

### Post by alazou on 2011-04-16
> **Locke_99GS said:**
> The kernel is configured, then built according to that configure. You cannot change the configuration of the kernel after it has been compiled - the deb packaged kernels are pre-built apparently to the 2.6.38 natty generic config - this is why you don't get any of the new .39 features from the mainline ppa, they were configured using the .38 featureset. The packages you get are only architecture specific. The kernel metapackage you choose will determine whether you will receive generic/server/pae kernels, and only when that metapackage changes its dependency. With the mainline ppa not offering server configured builds, it won't pull in a server version of the latest mainline build.



The simplest method to deal with this, in my personal option, would be to just compile your own kernel. This gives you the ability to lean out the kernel (no need to build modules for things you will never have) and tune  and optimize some of the options to your specific needs. You also have the option here to apply whatever patches you choose to your kernel.

You can start with the config from your current kernel and built with that, or make further tweaks to it before building.

My kernels are relatively lean and only take about 20 minutes or so to compile. Bigger kernels take longer to build, and obviously older processors will take longer to build them also.

May I ask what are the specs of your computer ? Also, by making your kernel lean do you see an improvement in speed ? I think it should not be that much of a boost because the kernel is modular, but it doesn't hurt to ask.

Also, what new features are you refering to ? I though this kernel was mainly an update of what was already there

---

### Post by VinDSL on 2011-04-17
LoL!  I got bored and installed the latest Liquorix kernel...  :D

```

vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
[sudo] password for vindsl: 
NVRM version: **[COLOR="Red"]NVIDIA UNIX x86 Kernel Module  270.41.03[/COLOR]**  Sat Apr  9 00:04:57 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) 
vindsl@Zuul:~$ uname -a
Linux Zuul **[COLOR="Red"]2.6.38-3.dmz.1-liquorix-686[/COLOR]** #1 ZEN SMP PREEMPT Sat Apr 16 08:01:29 UTC 2011 i686 i686 i386 GNU/Linux
vindsl@Zuul:~$ unity --version
**[COLOR="Red"]unity 3.8.8[/COLOR]**
vindsl@Zuul:~$ 

```


Everything is running fine - Ubu 11.04 beta 2 - Unity - Empathy - Gwibber - Banshee - Firefox - blah, blah, blah.  ;)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-17-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-17-apr-2011.png")[/INDENT]


Aren't kernels fun?!?!?!?

OK, back on topic...  :)

---

### Post by Locke_99GS on 2011-04-17
> **alazou said:**
> May I ask what are the specs of your computer ? Also, by making your kernel lean do you see an improvement in speed ? I think it should not be that much of a boost because the kernel is modular, but it doesn't hurt to ask.

Its a Phenom2 x4 CPU. Here's everything interesting:
[http://dl.dropbox.com/u/1108539/hardinfo_report-17apr11.html](http://dl.dropbox.com/u/1108539/hardinfo_report-17apr11.html)

There is little to no performance boost from leaning out the kernel, but it does compile faster and boost faster. There are many, many things useless to most people that get compiled right into the kernel. This is just a waste. The biggest gain can be had for adding specific support for your components rather than generic support, the ability to optimise and tweak, and patches.

> Also, what new features are you refering to ? I though this kernel was mainly an update of what was already there

See: [http://lwn.net/Kernel/](http://lwn.net/Kernel/) for articles about kernel features. Particularly, I'm excited about the inclusion of the rtl8192cu wifi driver, and USB graphics and DisplayLink support.

---

### Post by VinDSL on 2011-04-20
Linux kernel 2.6.39 rc4 is out...

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel
vindsl@Zuul:~/Downloads/Kernel$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
Selecting previously deselected package linux-headers-2.6.39-020639rc4.
(Reading database ... 265679 files and directories currently installed.)
Unpacking linux-headers-2.6.39-020639rc4 (from linux-headers-2.6.39-020639rc4_2.6.39-020639rc4.201104191410_all.deb) ...
Selecting previously deselected package linux-headers-2.6.39-020639rc4-generic.
Unpacking linux-headers-2.6.39-020639rc4-generic (from linux-headers-2.6.39-020639rc4-generic_2.6.39-020639rc4.201104191410_i386.deb) ...
Selecting previously deselected package linux-image-2.6.39-020639rc4-generic.
Unpacking linux-image-2.6.39-020639rc4-generic (from linux-image-2.6.39-020639rc4-generic_2.6.39-020639rc4.201104191410_i386.deb) ...
Done.
Setting up linux-headers-2.6.39-020639rc4 (2.6.39-020639rc4.201104191410) ...
Setting up linux-headers-2.6.39-020639rc4-generic (2.6.39-020639rc4.201104191410) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
 * dkms: running auto installation service for kernel 2.6.39-020639rc4-generic                                                                                                
 *       nvidia-current (270.41.03)...                                                                                                                                 [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
Setting up linux-image-2.6.39-020639rc4-generic (2.6.39-020639rc4.201104191410) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-020639rc4-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
 * dkms: running auto installation service for kernel 2.6.39-020639rc4-generic                                                                                                
 *       nvidia-current (270.41.03)...                                                                                                                                 [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-020639rc4-generic /boot/vmlinuz-2.6.39-020639rc4-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-020639rc4-generic
Found initrd image: /boot/initrd.img-2.6.39-020639rc4-generic
Found linux image: /boot/vmlinuz-2.6.39-020639rc3-generic
Found initrd image: /boot/initrd.img-2.6.39-020639rc3-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.38-3.dmz.1-liquorix-686
Found initrd image: /boot/initrd.img-2.6.38-3.dmz.1-liquorix-686
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.03  Sat Apr  9 00:04:57 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
vindsl@Zuul:~$ uname -a
Linux Zuul 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 15:45:56 UTC 2011 i686 i686 i386 GNU/Linux
vindsl@Zuul:~$ unity --version
unity 3.8.8
vindsl@Zuul:~$ 

```

Everything built / runs just fine!  ;)

---

### Post by dino99 on 2011-04-20
> **VinDSL said:**
> Linux kernel 2.6.39 rc4 is out...

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

Everything built / runs just fine!  ;)

yeah run fine with i386+8500gt

---

### Post by VinDSL on 2011-04-20
Heh!

I had some real issues with the dailys, the past couple of nights.

Luckily, my Liquorix was still present.  That was the only kernel that would boot this machine.  The 2.6.38 Ubu kernel wouldn't even boot.

Anyway, all's well, that ends well.  2.6.39 rc4 is a keeper (and I'm looking forward to rc5).

I'm going to stay away from the 999 dailys for a while!  LoL!

---

### Post by zika on 2011-04-20
Nice, first breath of OO: [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-20-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-20-oneiric/)

When I come back from a holiday, it will be OO tool-chain time...

---

### Post by VinDSL on 2011-04-21
> **zika said:**
> Nice, first breath of OO: [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-20-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-04-20-oneiric/)
Sweet!

I'm looking forward to OO.

Natty is becoming a snooze.  ZZZZzzzzzz...

---

### Post by jardo on 2011-04-21
> **VinDSL said:**
> LoL!  I got bored and installed the latest Liquorix kernel...  :D

```

vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
[sudo] password for vindsl: 
NVRM version: **[COLOR="Red"]NVIDIA UNIX x86 Kernel Module  270.41.03[/COLOR]**  Sat Apr  9 00:04:57 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) 
vindsl@Zuul:~$ uname -a
Linux Zuul **[COLOR="Red"]2.6.38-3.dmz.1-liquorix-686[/COLOR]** #1 ZEN SMP PREEMPT Sat Apr 16 08:01:29 UTC 2011 i686 i686 i386 GNU/Linux
vindsl@Zuul:~$ unity --version
**[COLOR="Red"]unity 3.8.8[/COLOR]**
vindsl@Zuul:~$ 

```


Everything is running fine - Ubu 11.04 beta 2 - Unity - Empathy - Gwibber - Banshee - Firefox - blah, blah, blah.  ;)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-17-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-17-apr-2011.png")[/INDENT]


Aren't kernels fun?!?!?!?

OK, back on topic...  :)

sorry for the noob question...but what's the name of that application u have on the right side of the desktop?:confused::confused: i want that too :( and i want the same background too :D

---

### Post by dino99 on 2011-04-21
tread off, but its conky

[http://ubuntuforums.org/search.php?searchid=80548142](http://ubuntuforums.org/search.php?searchid=80548142)

---

### Post by jardo on 2011-04-21
> **dino99 said:**
> tread off, but its conky

[http://ubuntuforums.org/search.php?searchid=80548142](http://ubuntuforums.org/search.php?searchid=80548142)
sorry for the offtopic...thanks!

---

### Post by drewesq on 2011-04-21
> **VinDSL said:**
> All hail! Linux 2.6.39 rc3... :D
 
[INDENT](Click to expand)
 
[[IMG]http://vindsl.com/images/vindsl-desktop-13-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-13-apr-2011.png")
[/INDENT] 
Unity has been coming along nicely!
 
Might as well use the latest kernel too. ;)
 
BTW, if you're running nVidia 270.30, you still need to implement the **smp_lock.h** hack on page 2...
 
What is that gadget you use on the right there??

Cheers!

---

### Post by Locke_99GS on 2011-04-21
@drewesq I only see the Unity interface and Conky on that screenshot.

---

### Post by dino99 on 2011-04-21
> **drewesq said:**
> What is that gadget you use on the right there??

Cheers!

for the lazy: #84

---

### Post by drewesq on 2011-04-21
Conky, that'll be it then!
 
Sorry for butting in on the thread.

---

### Post by VinDSL on 2011-04-21
> **jardo said:**
> sorry for the noob question...but what's the name of that application u have on the right side of the desktop?:confused::confused: i want that too :( and i want the same background too :D

> **drewesq said:**
> What is that gadget you use on the right there??

Cheers!
It's a mixture of Conky, conkyForecast, and Lua.

Here's my most recent data dump:  [http://ubuntuforums.org/showpost.php?p=10624494&postcount=16875](http://ubuntuforums.org/showpost.php?p=10624494&postcount=16875)

If you have any questions, please use that Mega thread...  ;)

---

### Post by KegHead on 2011-04-21
Hi VinDSL!

I've been gone for a few days.

What's the status of kernel updates/

KegHead

---

### Post by VinDSL on 2011-04-22
> **KegHead said:**
> Hi VinDSL!

I've been gone for a few days.

What's the status of kernel updates/

KegHead
Natty is on the final countdown.  It'll be released next Thursday.

There are two versions of 2.6.39 rc4 now -- Natty and OO.

I quit using the dailys, after a couple of recent failures, and have settled on 2.6.39 rc4 Natty.

If / when they come out with an rc5 for Natty, I'll try that, otherwise...

I'm in a holding pattern, until Natty is released.  ;)

---

### Post by KegHead on 2011-04-22
Hi!

Thanks for the update.

Good idea as I've had video problems with the kernels.

KegHead

---

### Post by solitaire on 2011-04-22
Anyone noticed excessive power usage with the2.6.39 kernel?

Seen at least one report today over at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1") saying that 11.04 & 2.6.39 (and the .38 ) kernel is using between 10%-18% more than previous kernels.

---

### Post by VinDSL on 2011-04-22
> **solitaire said:**
> Anyone noticed excessive power usage with the2.6.39 kernel?

Seen at least one report today over at [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=linux_mobile_uffda&num=1") saying that 11.04 & 2.6.39 (and the .38 ) kernel is using between 10%-18% more than previous kernels.
Not sure what "power usage" refers to...

If you're talking about AC wall current, this machine consumes 190-200 watts, and there hasn't been an increase.

If you're talking about ram & cpu, no, I haven't noticed an increase there either.


Here's a screenie from a couple of hours ago:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-22-apr-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-22-apr-2011.png")[/INDENT]


This screenie was made for a Banshee thread, but (if you look around) you can plainly see that ram & cpu usage is low.

The only excessive ram & cpu usage I've experienced with Natty was:


Linkage:  [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/725434)

```

summary:

- libcairo causes a significant 'across the board' memory use increase
- with -nvidia loaded
+ Nvidia drivers lead to extra memory usage for each process using libGL

```

```

This bug was fixed in the package cairo - 1.10.2-2ubuntu2

---------------
cairo (1.10.2-2ubuntu2) natty; urgency=low

  * Don't turn the gl backend on for natty since it creates issues for nvidia
    users and is only used for wayland (lp: #725434)
  * debian/control,
    debian/libcairo2.symbols,
    debian/rules:
    - updated for the non-gl build
  * debian/control: Breaks on wayland
 -- Sebastien Bacher <seb128@ubuntu.com> Fri, 08 Apr 2011 18:27:43 +0200

```

This bug has not come back, and I've been keeping a close eye on mem usage, ever since.

Anyway, personally, I haven't "noticed excessive power usage with the2.6.39 kernel".  ;)

---

### Post by KegHead on 2011-04-23
Hmm, 

I guess I'll wait a few more releases.

KegHead

---

### Post by VinDSL on 2011-04-24
This is an interesting development...  :D

There is a growing concern (amongst some) that 2.6.38 & 2.6.39 are consuming too much electricity.  Alrighty then...

Soooo, I decided to install the 2.6.37.6-Natty (28-Mar-2011) mainline kernel, to see how it works.

Linkage:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37.6-natty/)

It built and runs fine...

```

vindsl@Zuul:~$ cd Downloads
vindsl@Zuul:~/Downloads$ cd Kernel
vindsl@Zuul:~/Downloads/Kernel$ sudo dpkg -i *.deb
[sudo] password for vindsl: 
Selecting previously deselected package linux-headers-2.6.37-02063706.
(Reading database ... 255620 files and directories currently installed.)
Unpacking linux-headers-2.6.37-02063706 (from linux-headers-2.6.37-02063706_2.6.37-02063706.201103281005_all.deb) ...
Selecting previously deselected package linux-headers-2.6.37-02063706-generic.
Unpacking linux-headers-2.6.37-02063706-generic (from linux-headers-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb) ...
Selecting previously deselected package linux-image-2.6.37-02063706-generic.
Unpacking linux-image-2.6.37-02063706-generic (from linux-image-2.6.37-02063706-generic_2.6.37-02063706.201103281005_i386.deb) ...
Done.
Setting up linux-headers-2.6.37-02063706 (2.6.37-02063706.201103281005) ...
Setting up linux-headers-2.6.37-02063706-generic (2.6.37-02063706.201103281005) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
 * dkms: running auto installation service for kernel 2.6.37-02063706-generic                                                                                                 
 *       nvidia-current (270.41.06)...                                                                                                                                 [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
Setting up linux-image-2.6.37-02063706-generic (2.6.37-02063706.201103281005) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-02063706-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
 * dkms: running auto installation service for kernel 2.6.37-02063706-generic                                                                                                 
 *       nvidia-current (270.41.06)...                                                                                                                                 [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-02063706-generic /boot/vmlinuz-2.6.37-02063706-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.39-020639rc4-generic
Found initrd image: /boot/initrd.img-2.6.39-020639rc4-generic
Found linux image: /boot/vmlinuz-2.6.38-3.dmz.1-liquorix-686
Found initrd image: /boot/initrd.img-2.6.38-3.dmz.1-liquorix-686
Found linux image: /boot/vmlinuz-2.6.37-02063706-generic
Found initrd image: /boot/initrd.img-2.6.37-02063706-generic
Found linux image: /boot/vmlinuz-2.6.37-5.dmz.1-liquorix-686
Found initrd image: /boot/initrd.img-2.6.37-5.dmz.1-liquorix-686
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~$ sudo cat /proc/driver/nvidia/version
NVRM version:**[COLOR="Red"] NVIDIA UNIX x86 Kernel Module  270.41.06[/COLOR]**  Mon Apr 18 14:54:25 PDT 2011
GCC version:  gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
vindsl@Zuul:~$ uname -a
Linux Zuul **[COLOR="red"]2.6.37-02063706-generic[/COLOR]** #201103281005 SMP Mon Mar 28 11:33:42 UTC 2011 i686 i686 i386 GNU/Linux
vindsl@Zuul:~$ unity --version
**[COLOR="red"]unity 3.8.10[/COLOR]**
vindsl@Zuul:~$ 

```


I'm on a desktop machine, and 2.6.39 rc4 is working great, even if it does chew up a few extra watts.

I'll continue running 2.6.39 rc4, but keep 2.6.37.6 sitting on the drive, just in case things heat up...  ;)


**EDIT**


Er...  I hate to say this, but...

2.6.37.6 has worked a treat.  This thing is flying!

It seems that we've come full circle.  LoL!


I'm going to continue running 2.6.37 for a few days...  :)

---

### Post by matt_symes on 2011-04-24
> 2.6.37.6 has worked a treat. This thing is flying!

Not on my PC :(

---

### Post by KegHead on 2011-04-24
Hi!

I'm still gun shy!

Waiting a few days.

KegHead

---

