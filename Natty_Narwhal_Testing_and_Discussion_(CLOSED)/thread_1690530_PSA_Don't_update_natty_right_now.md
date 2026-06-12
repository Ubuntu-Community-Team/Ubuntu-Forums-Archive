---
title: "PSA: Don't update natty right now"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by castrojo on 2011-02-18
eglibc is broken on AMD64

The platform team and IS are working to remove the binary from the archive, please help spread the word.

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/721469](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/721469)

---

### Post by Quackers on 2011-02-18
Too late! No evolution now :-)
But thanks anyway.

---

### Post by jennybrew on 2011-02-18
> **castrojo said:**
> eglibc is broken.

The platform team and IS are working to remove the binary from the archive, please help spread the word.

Woo ... bad timing.
I updated about 10 minutes before your post.
What, if any, are the consequences and what actions may I have to take?
Thanks 

Edit: ah right its Evolution! No problem ..... the Achilles heel program anyhow

---

### Post by fabricator4 on 2011-02-18
Thanks, I was just about to do an update...

---

### Post by castrojo on 2011-02-18
Packages to downgrade are here:

[http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/)

You're looking for anything ending in *ubuntu16_amd64.deb

If someone could make a list of all the URLs and test that a downgrade works it would help people out (I'll add it to the original post)

---

### Post by MacUntu on 2011-02-18
Thanks! I already was upgraded to the bad one. :)

---

### Post by cariboo on 2011-02-18
There's a broken dependecny for libnih1

---

### Post by JRV on 2011-02-18
I updated and had no problems for about two hours.

After reading this thread I tried Evolution and it doesn't load.

This is the first time I have tried Evolution on my test machine, it is not used for E-mail.

---

### Post by petst on 2011-02-18
Too late, skype can't start.:D

---

### Post by mc4man on 2011-02-18
> eglibc is broken on AMD64
it also affects 32 bit installs

---

### Post by pressureman on 2011-02-18
And with libc6 2.12 it's indicator-applet whack-a-mole again...

```

[   53.377739] indicator-apple[1945] general protection ip:7fa3bf8c4e52 sp:7fff2bfd5d68 error:0 in libc-2.12.2.so[7fa3bf843000+177000]
[   54.752802] indicator-apple[1951] general protection ip:7f13ef113e52 sp:7fff976413f8 error:0 in libc-2.12.2.so[7f13ef092000+177000]
[   55.771723] indicator-apple[1967] general protection ip:7fd181215e52 sp:7fff13750778 error:0 in libc-2.12.2.so[7fd181194000+177000]
[   56.939878] indicator-apple[2024]: segfault at 30 ip 00007f8bad2ade52 sp 00007fff8cf631a8 error 4 in libc-2.12.2.so[7f8bad22c000+177000]
[   57.926220] indicator-apple[2031]: segfault at 0 ip 00007f3e17653e52 sp 00007fff3bc9a328 error 4 in libc-2.12.2.so[7f3e175d2000+177000]
[   58.895329] indicator-apple[2037] general protection ip:7fcc27442e52 sp:7fff98162c78 error:0 in libc-2.12.2.so[7fcc273c1000+177000]
[   59.631731] indicator-apple[2043] general protection ip:7f230ad66e52 sp:7fffdd61fe88 error:0 in libc-2.12.2.so[7f230ace5000+177000]
[   60.291497] indicator-apple[2049]: segfault at d0 ip 00007f00b2b9ce52 sp 00007ffff23ff4e8 error 4 in libc-2.12.2.so[7f00b2b1b000+177000]
[   60.919940] indicator-apple[2055] general protection ip:7f65217e7e52 sp:7fffdb470f38 error:0 in libc-2.12.2.so[7f6521766000+177000]

```

... eventually it loads...

---

### Post by Quackers on 2011-02-18
nm-applet is working for me, but no icon appears in the top panel.

---

### Post by Framli on 2011-02-18
Thanks Jorge.

---

### Post by castrojo on 2011-02-18
Fixed with this upload:

[https://lists.ubuntu.com/archives/natty-changes/2011-February/007794.html](https://lists.ubuntu.com/archives/natty-changes/2011-February/007794.html)

---

### Post by mick8985 on 2011-02-18
still getting 
```
evolution-network-manager-WARNING **: network_manager_check_initial_state: Timeout was reached
Inconsistency detected by ld.so: dl-deps.c: 622: _dl_map_object_deps: Assertion `nlist > 1' failed!
```

on i386

---

### Post by zika on 2011-02-19
[Is it safe?](http://www.youtube.com/watch?v=dG5Qk-jB0D4)

---

### Post by loftwyr on 2011-02-19
Updated, didn't have a problem until I had to reboot due to power failure.  Now I can't boot as most of the boot processes are SEGV.  How do I fix this?\

Can I chroot and update somehow?

---

### Post by TerminX on 2011-02-19
> **loftwyr said:**
> Updated, didn't have a problem until I had to reboot due to power failure.  Now I can't boot as most of the boot processes are SEGV.  How do I fix this?\

Can I chroot and update somehow?
You'll need to mount the affected installation's partitions in a recovery environment as if you were just going to chroot to it, but instead you'll have to dpkg -x the older, working libc6 packages into the root of the install.

After you do that, you should be able to chroot to it and explicitly install the older packages with dpkg -i, at which point you'll just need to wait until an updated and working libc6 package is available.

---

### Post by rebootme on 2011-02-19
Thanks for the warning!  I was just about to update...

---

### Post by loftwyr on 2011-02-19
> **TerminX said:**
> You'll need to mount the affected installation's partitions in a recovery environment as if you were just going to chroot to it, but instead you'll have to dpkg -x the older, working libc6 packages into the root of the install.

After you do that, you should be able to chroot to it and explicitly install the older packages with dpkg -i, at which point you'll just need to wait until an updated and working libc6 package is available.

Since the newer versions had fixed the problem (and are now accepted) I dpkg -x libc6 and the chrooted to update the rest.

Thanks for the help!

---

### Post by GeoPirate on 2011-02-20
Is it safe to update yet?

---

### Post by Sophont on 2011-02-20
Does anybody actually use Evolution? ;-)

I thought everybody is using Thunderbird or GMail instead.

---

### Post by Harry33 on 2011-02-20
> **GeoPirate said:**
> Is it safe to update yet?

This bug is market as being fixed.
I use this latest eglibc with no problems at all.
Here:
[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/721469](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/721469)

---

### Post by jennybrew on 2011-02-20
Evolution is working just fine here again although it woudnt be my choice for such an important office application as e-mail.

---

### Post by tjeremiah on 2011-02-20
> **Sophont said:**
> Does anybody actually use Evolution? ;-)

I thought everybody is using Thunderbird or GMail instead.

No. I wish there was a way to make Thunderbird the default.

---

### Post by Harry33 on 2011-02-20
> **tjeremiah said:**
> No. I wish there was a way to make Thunderbird the default.

I am afraid we have to wait for that moment quite some time.
Evolution and especially its data-server is quite deeply buried into gnome2.

You can unistall all actual evolution packages by removing the meta package ubuntu-desktop first. That one depends on evolution.
But you cannot uninstall evolution-data-server system completely or after that you do not have panels nor applets any longer. It is the address book that keeps hanging on (packages evolution-data-server-common, libcamel*, libebook*, libecal*, libedataserv* and libedataservui*).

---

### Post by cariboo on 2011-02-20
Seeing as the problem has been solved via updates, I've unstuck this thread.

---

### Post by loftwyr on 2011-02-20
Not fully fixed, the latest libc doesn't take to prelink.  Although extracting the libc deb to the root fixes it, as soon as the prelink runs through cron, the whole system goes SEGV again.  I've annoted the bug with it but maybe that should be a new bug?

---

### Post by Harry33 on 2011-02-20
> **loftwyr said:**
> Not fully fixed, the latest libc doesn't take to prelink.  Although extracting the libc deb to the root fixes it, as soon as the prelink runs through cron, the whole system goes SEGV again.  I've annoted the bug with it but maybe that should be a new bug?

Better to place a new bug report on that issue.

But if this one is solved, this thread should be flagged as solved.

---

### Post by Aide9aic on 2011-02-21
Confirming the issue with libc6 and prelink. Did a reboot after upgrading today (Sunday 20 Feb) and my system would constantly crash with "error 7 in ld-2.13.so". Googling took me to a [page in the Arch forums]("https://bbs.archlinux.org/viewtopic.php?id=112484") where folks described a similar problem along with a fix:

> The problem is that I can't even roll back to a previous version because as soon as I chroot, I get a segfault (from trying to execute bash).
...
I took glibc-2.13 (the current version) and untarred it. Then I just copied everything under lib and lib64 into the /lib and /lib64 directories on my root partition/LVM and I was able to chroot in! So I unprelinked everything and am currently booting into my system!

I followed the same steps and got my system back. Yay.

---

