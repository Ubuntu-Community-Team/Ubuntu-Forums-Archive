---
title: "X not working with newer kernels (Intel GPU)"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Dragonsong on 2010-09-26
Yeah, as the title says, I've been having issues with X for a while. Up to kernel 2.6.35-15 it worked flawlessly, and still does. With newer ones though, X doesn't load upon startup at all, and startx says it failed to load the screen and offers low graphics mode for me.
My GPU's the Intel HD Graphics.

Here's the dmesg log from kernel 2.6.35-17 (one of the not working ones):
[http://pastebin.com/9JNcNAN1](http://pastebin.com/9JNcNAN1)
And the Xorg.log:
[http://pastebin.com/2XHxX45P](http://pastebin.com/2XHxX45P)

If there's anything else need, let me know :)

---

### Post by kerry_s on 2010-09-26
well it looks like your running a bit of custom stuff.
grab a daily live cd & try it with out your modifications.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Dragonsong on 2010-09-26
I think all of my "custom stuff" comes from the xorg-edgers ppa. Removing it all with ppa-purge doesn't change the situation at all.
I guess there's no harm in testing the livecd though. Problem is, I lack blank CD's at the moment. Would say, running it with Wubi work?

---

### Post by kansasnoob on 2010-09-26
Please post the output of:

```
lspci | grep VGA
```

That will tell us the specific version of Intel GPU.

I'm battling a problem with 82945G/GZ Integrated Graphics, aka: i945:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

I thought of a few additional test case scenarios I need to perform today before actually filing a report.

---

### Post by Dragonsong on 2010-09-26
Here you go:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

### Post by plun on 2010-09-26
File a bug,please..... developers doesn't read forums !

Existing bugs, sorted "newest first".
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.searchtext=&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Howto file a new one

```
ubuntu-bug xserver-xorg-video-intel
```

---

### Post by kerry_s on 2010-09-26
> **kansasnoob said:**
> Please post the output of:

```
lspci | grep VGA
```

That will tell us the specific version of Intel GPU.

I'm battling a problem with 82945G/GZ Integrated Graphics, aka: i945:

[http://ubuntuforums.org/showthread.php?t=1579475](http://ubuntuforums.org/showthread.php?t=1579475)

I thought of a few additional test case scenarios I need to perform today before actually filing a report.


i bet it's the monitor.

---

### Post by kansasnoob on 2010-09-26
> **Dragonsong said:**
> Here you go:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Did you copy-n-paste that command?

Somehow that looks incomplete :confused:

Like if I run it:

```
lance@lance-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

You see it shows the actual version number :)

I'm much closer to being able to file my bug report as I'm now able to duplicate the bug on an installed Maverick, whereas I'd only seen it with the Live CD.

Now I'll be able to access the "buggy" install via chroot and do more troubleshooting. It's darn hard to troubleshoot a Live CD with no gui:)

---

### Post by kansasnoob on 2010-09-26
To determine the actual version of Intel GPU you could also possibly install the package "sysinfo" which will then show up in System Tools.

Or maybe post the full output of "lspci" :confused:

I've been troubleshooting a lot, as time allows, and the changelog for 'linux-libc-dev' is very interesting:

>  * Revert "SAUCE: i915 KMS -- blacklist i855"
  * Revert "SAUCE: i915 KMS -- blacklist i845g"
  * Revert "SAUCE: i915 KMS -- blacklist i830"
  * Revert "SAUCE: i915 KMS -- support disabling KMS for known broken
    devices"
  * execute module-inclusion within a subshell
    - LP: #621175

My i945 shouldn't be effected ........... I hope :P

BTW that changelog quote is from September 14th.

---

### Post by Dragonsong on 2010-09-27
> **kansasnoob said:**
> Did you copy-n-paste that command?

I did, and that's everything I get. As I already said though, I know my GPU's Intel HD Graphics (Which means their latest one, the one integrated on the CPU die)

---

### Post by ratcheer on 2010-09-27
I saw a new version of xorg for Intel in today's changes list. Maybe it will help.

> 5. [ubuntu/maverick] xserver-xorg-video-intel 2:2.12.0-1ubuntu5
      (Accepted) (Christopher James Halse Rogers)

Tim

---

### Post by kansasnoob on 2010-09-27
Also take a look here:

[http://ubuntuforums.org/showpost.php?p=9893106&postcount=16](http://ubuntuforums.org/showpost.php?p=9893106&postcount=16)

It worked for me and I left a rather lengthy comment at the bug report.

I'm also curious if you still have any of the order/manufacturer info from when you purchased that Intel GPU? We'd probably benefit by knowing more about the specific model of GPU :)

---

### Post by Catharsis on 2010-09-27
Your Xorg.0.log shows that you don't have KMS enabled, which will cause X not to load on the 2.12+ Intel driver. I don't see why it would be disabled, but you can try this to temporarily re-enable KMS and see if it fixes the problem for you:

1) Hold down Shift while booting to get to GRUB.
2) Highlight your kernel, and then press 'e'.
3) Add "i915.modeset=1" after "quiet splash" and then hit Ctrl+x to boot.

---

### Post by Catharsis on 2010-09-27
> **kansasnoob said:**
> Did you copy-n-paste that command

See [here](https://wiki.ubuntu.com/X/Tagging) for a table of lspci data. I'd guess the OP is using an Arrandale chipset, from the Core iX line of processors.

---

### Post by Dragonsong on 2010-09-28
Thanks for the suggestions, ratcheer, kansasnoob and Catharsis. Sadly, none of them seemed to change the situation whatsoever.

Anyway, I've filed a bug report, as I was asked to, which is over here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/648631](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/648631)

And it is indeed an Arrandale chipset. To be exact, the CPU's Celeron P4500.

Edit: To my untrained eye, the dmesg log in my OP shows that *something* is crashing at bootup (starting at line 765) which isn't happening on the kernels that are working just fine. I'd bet that's related.

---

### Post by dino99 on 2010-09-28
with the latest updates from x-swat or xedgers it might be ok now and dont need nomodeset anymore on the boot line

but to see if it makes difference, try either:

- nomodeset
- i945.modeset=0

this can be added into /etc/default/grub, then sudo update-grub

***** sometimes its a good idea to remove/purge then reinstall the package when there are troubles around, so in your case the package is xserver-xorg-video-intel, then reboot and check driver activation

---

