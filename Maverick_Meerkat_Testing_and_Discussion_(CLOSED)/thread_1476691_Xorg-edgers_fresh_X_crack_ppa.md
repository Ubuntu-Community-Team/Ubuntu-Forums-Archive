---
title: "Xorg-edgers fresh X crack ppa"
date: 2010-05-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-05-08
For the ultimate graphic freak.....

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Latest Xorg package

Latest nVidia driver

Latest Mesa

Update, Aug 1, -ignoreabi must be added to xorg.cong

> Section "ServerFlags"
Option "ignoreABI" "True"
EndSection


Please note ppa-purge if something goes wrong !

[https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)

;)

---

### Post by Linuxforall on 2010-05-08
Bear in mind that the latest also includes some real cutting edge stuff, the xswat ppa is hosting latest nvidia drivers for Lucid as well but no other radical stuff so for most, that makes a sensible choice there.

---

### Post by plun on 2010-05-08
> **Linuxforall said:**
> Bear in mind that the latest also includes some real cutting edge stuff, the xswat ppa is hosting latest nvidia drivers for Lucid as well but no other radical stuff so for most, that makes a sensible choice there.

Well, this is just development and everyone within this forum should be aware of this.....

Bleeding edge and breakage...:lolflag:

---

### Post by Linuxforall on 2010-05-08
> **plun said:**
> Well, this is just development and everyone within this forum should be aware of this.....

Bleeding edge and breakage...:lolflag:

True that.....that caveat remains with any dev branch. :)

---

### Post by autocrosser on 2010-05-08
I'm using it & "currently" it's all working very well---the nvidia drivers are very nice & I note that my system is (or "seems") faster/smoother, but that may be very subjective......

---

### Post by tad1073 on 2010-05-08
I tried it out and I was having higher than normal cpu usage so I reverted back

---

### Post by kansasnoob on 2010-05-08
So, does this effect only Nvidia?

I have Intel graphics on one machine and VIA on the other.

Edit: totally off-topic, but did you a get a PM from me today about this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

If so, sorry if I seemed "short tempered" about the PM's but when you're immersed in trying to help someone with boot or upgrade issues it's very distracting to have PM notifications pop up frequently.

That and I'm a grouchy old man.

---

### Post by ranch hand on 2010-05-08
I tried out the xorg edgers stuff on an install way back in 10.04 testing.  Worked pretty well.  Made it possible to run compiz (which I absolutely detest) and GS.  Then the generic caught up as far as that stuff being able to run.

I know that it also was dumping intel stuff on here too.

I would give it a whack.  They are ahead of the curve on this stuff.

---

### Post by jfernyhough on 2010-05-08
I was just about to try it out when I read:
> fglrx will not work at all, do not use this PPA if you need it.so probably just as well I didn't update!

(I'm seriously wondering whether getting an ATi-based laptop was a good idea... even things like mipmap-based blur in compiz don't work)

---

### Post by ranch hand on 2010-05-08
My card works better on the open driver, you might want to try it.  You can always switch back.

---

### Post by plun on 2010-05-09
> **autocrosser said:**
> I'm using it & "currently" it's all working very well---the nvidia drivers are very nice & I note that my system is (or "seems") faster/smoother, but that may be very subjective......

Yup... I observe the same after install.

Unigine Heaven 2.0  might be a good benchmark-tool 
[http://www.phoronix.com/scan.php?page=news_item&px=ODA5NA](http://www.phoronix.com/scan.php?page=news_item&px=ODA5NA)

Maybe only for "nerds"....:P

EDIT Download
[http://www.unigine.com/download/](http://www.unigine.com/download/)

EDIT again, my scores

> Unigine
Heaven Benchmark v2.0
FPS:	
9.4
Scores:	
236
Min FPS:	
6.5
Max FPS:	
15.9
Hardware
Binary:	
Linux 64bit GCC 4.3.2 Release Mar 21 2010
Operating system:	
Linux 2.6.34-1-preempt x86_64
CPU model:	
Intel(R) Core(TM) i3 CPU M 330 @ 2.13GHz
CPU flags:	
2127MHz MMX SSE SSE2 SSE3 SSSE3 SSE41 SSE42 HTT
GPU model:	
GeForce GT 330M PCI Express 195.36.24 1024Mb
Settings
Render:	
opengl
Mode:	
1920x1080 fullscreen
Shaders:	
high
Textures:	
high
Filter:	
trilinear
Anisotropy:	
16x
Occlusion:	
enabled
Refraction:	
enabled
Volumetric:	
enabled
Replication:	disabled
Tessellation:	disabled
Unigine Corp. © 2005-2010

--

---

### Post by zika on 2010-05-09
Any news when we can expect Maverick branch on xorg-edgers...? That is the only thing keeping me from editing my soeurces.list... :)

---

### Post by plun on 2010-05-09
> **zika said:**
> Any news when we can expect Maverick branch on xorg-edgers...? That is the only thing keeping me from editing my soeurces.list... :)

Well, I am using the Lucid branch and I cannot see any trouble with that.

Xorg-edgers is also an "official" Ubuntu ppa so they are probably aware of this.

---

### Post by vikrant82 on 2010-05-09
For some reason, they are pushing my framerate on glxgears from 3000 per 5s to 300 per 5s on Intel GM965.

---

### Post by crjackson on 2010-05-09
> **Linuxforall said:**
> Bear in mind that the latest also includes some real cutting edge stuff, the xswat ppa is hosting latest nvidia drivers for Lucid as well but no other radical stuff so for most, that makes a sensible choice there.

While I agree, I've gotta say where's the fun in that?:-)

I really saw no advantage in the edgers repos. for my machine.  So I did the ppa-purge thing (I love that tool!).

---

### Post by ToxicBurn on 2010-05-10
> **plun said:**
> For the ultimate graphic freak.....
 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
Latest Xorg package
 
Latest nVidia driver
 
Latest Mesa
 
 
Please note ppa-purge if something goes wrong !
 
[https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)
 
;)
 
 
What about ATI drivers ?
 
Im getting a ATI HD 5770 for my B-day in 10 days

---

### Post by ranch hand on 2010-05-10
I used it last round for a while and it made it so my poorly supported card would actually run compiz (I really hate the sucker but it did work) and GS.  The regular open driver caught up and I dropped the edgers stuff.

If you want the best drivers for ATI I would really recommend giving it a try.

---

### Post by ToxicBurn on 2010-05-10
> **ranch hand said:**
> I used it last round for a while and it made it so my poorly supported card would actually run compiz (I really hate the sucker but it did work) and GS. The regular open driver caught up and I dropped the edgers stuff.
 
If you want the best drivers for ATI I would really recommend giving it a try.
 
Thanks ranch hand i cant wait to get this new card and try it out .

---

### Post by hype on 2010-05-10
Glad to finally have Nvidia 195.36.24 installed on my system, latest Xorg, and all that by just adding this PPA. 
Thnaks for the hint ;)

---

### Post by Sarvatt on 2010-05-10
> **zika said:**
> Any news when we can expect Maverick branch on xorg-edgers...? That is the only thing keeping me from editing my soeurces.list... :)

Maverick PPA's just opened today and there is still a bug not letting me copy files over yet and I don't have the time to upload 60+ packages and build them in the correct order at the moment. Just use the lucid sources for now, they will work fine for some time to come.

---

### Post by zika on 2010-05-11
> **Sarvatt said:**
> Maverick PPA's just opened today and there is still a bug not letting me copy files over yet and I don't have the time to upload 60+ packages and build them in the correct order at the moment. Just use the lucid sources for now, they will work fine for some time to come.Cool! Thank You for all the work You've put in great PPA!

---

### Post by plun on 2010-05-13
xorg 1.8.1

[http://www.phoronix.com/scan.php?page=news_item&px=ODI0Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI0Mg)


```
Publishing details

    * Published 1 hour ago

Changelog

**xorg-server (2:1.8.1**+git20100513+server-1.8-branch.afd730f5-0ubuntu0sarvatt) maverick; urgency=low

  * Checkout from git 20100513 (server-1.8-branch branch) up to commit
    afd730f57fa1cd3e10ac47666bd6739016d60d55
  * Only added debian/ tree from origin/ubuntu
  * hook: Drop 02_Add-libgcrypt-and-libnettle-as-options-for-sha1.diff
    (upstream)
  * hook: Drop 05_only_call_gamma_set_if_nonnull.diff (upstream)
  * hook: Drop 06_dont_trap_access_to_timer_and_keyboard.diff (upstream)
  * hook: Drop 07-xfree86-fix-build-with-xv-disabled.diff (?)
  * hook: Drop 08-config-xorg-conf-d.diff (upstream)
  * hook: Drop 09-inputclass-sans-abi9.diff (upstream)
  * hook: Drop 10-config-libudev-backend.diff (upstream)
  * hook: Drop 11-xfree86-fix-video-fallback.diff (?)
  * hook: Drop 12-xfree86-dont-complain-about-missing-coredevices.diff
    (upstream)
  * hook: Drop 13-unbreak-input-abi.diff (upstream)
  * hook: Drop 14-tone-down-nidr-errors.diff (upstream)
  * hook: Drop 15-keep-udev-x11-driver.diff (upstream)
  * hook: Drop 100_rethrow_signals.patch (fails)
  * hook: Drop 109_fix-swcursor-crash.patch (?)
  * hook: Drop 110_findglyphbyhash-fix.patch (upstream)
  * hook: Drop 111_armel-drv-fallbacks.patch (unneeded)
  * hook: Drop 112_xaa-fbcomposite-fix-negative-size.patch (?)
  * hook: Drop 113_quell_nouveau_aiglx.patch (unneeded ?)
  * hook: Drop 115_xext_fix_cursor_ref_counting.patch (upstream)
  * hook: Drop 116_fix_typos_in_swap_functions.patch (upstream)
  * hook: Drop 118_xkb_fix_garbage_init.patch (upsteam)
  * hook: Drop 121_only_switch_vt_when_active.diff (?)
  * hook: Drop 122_xext_fix_card32_overflow_in_xauth.patch (pending)
  * hook: Drop 157_check_null_modes.patch (?)
  * hook: Drop 162_null_crtc_in_rotation.patch (?)
  * hook: Drop 164_trap-aspect-ratios.patch (?)
  * hook: Drop 165_man_xorg_conf_no_device_ident.patch (?)
  * hook: Drop 166_nullptr_xinerama_keyrepeat.patch (?)
  * hook: Drop 167_nullptr_xisbread.patch (?)
  * hook: Drop 169_mipointer_nullptr_checks.patch (?)
  * hook: Drop 172_cwgetbackingpicture_nullptr_check.patch (?)
  * hook: Drop 184_virtual_devices_autodetect.patch (unneeded)
  * hook: Drop 187_edid_quirk_hp_nc8430.patch (?)
  * hook: Drop 190_cache-xkbcomp_output_for_fast_start_up.patch (?)
  * hook: Drop 196_xvfb-fbscreeninit-handling.patch (?)
  * hook: Drop 197_xvfb-randr.patch (?)
  * hook: Drop 198_nohwaccess.patch (unneeded)
  * hook: Drop 199_xfvb-help-typo.patch (?)
  * hook: Drop 200_randr-null.patch (?)
  * hook: Drop 19-exa-handle-pixmap-create-destroy-in-lower-layers.diff
    (upstream)
  * hook: Drop 123_exa_sys_ptr_nullpointer_check.patch (upstream)
  * hook: Build with --disable-strict-compilation instead of --disable-
    werror
  * hook: Add build-dep on xfonts-utils
  * hook: increase serverminver to 1.8
  * hook: increase inputabiver to 9
  * hook: increase videoabiver to 7
 -- Robert Hooker <sarvatt@>   Thu, 13 May 2010 13:54:38 -0400
```

---

### Post by plun on 2010-05-23
Xorg-edgers now serves latest nVidia beta driver, ver 256.25

Info:
[http://www.phoronix.com/scan.php?page=news_item&px=ODI3Mw](http://www.phoronix.com/scan.php?page=news_item&px=ODI3Mw)

nVidia:
[http://www.nvnews.net/vbulletin/showthread.php?p=2255561](http://www.nvnews.net/vbulletin/showthread.php?p=2255561)

---

### Post by wolfe on 2010-05-24
Anyone know of a ppa where I can get 195.36.24 back?  This beta driver broke my boinc functionality and I really would like to roll back the driver, though I noticed this ppa has already replaced it with the 256.25

---

### Post by dino99 on 2010-05-24
> **wolfe said:**
> Anyone know of a ppa where I can get 195.36.24 back?  This beta driver broke my boinc functionality and I really would like to roll back the driver, though I noticed this ppa has already replaced it with the 256.25

x-swat

---

### Post by wolfe on 2010-05-24
x-swat has the 256.25

---

### Post by cariboo on 2010-05-24
> **wolfe said:**
> Anyone know of a ppa where I can get 195.36.24 back?  This beta driver broke my boinc functionality and I really would like to roll back the driver, though I noticed this ppa has already replaced it with the 256.25

195.36.24 are the default drivers from the repository, why use a ppa.

---

### Post by Starks on 2010-05-24
btw, ppa:sarvatt/xorg-testing has the xserver 1.9 candidates.

---

### Post by plun on 2010-05-24
> **Starks said:**
> btw, ppa:sarvatt/xorg-testing has the xserver 1.9 candidates.

:confused:   I can find his inactive ppa för xorg-testing but no ppa with 1.9 candidates.:confused:


Nevertheless a 1.9 version will probably break ABI version for the nVidia driver...maybe this works ?

```
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```

---

### Post by portis on 2010-05-24
> **Starks said:**
> btw, ppa:sarvatt/xorg-testing has the xserver 1.9 candidates.

I tried xserver 1.8 in xorg-edgers, but emacs doesnot like it. 
Emacs window doesn't repaint correctly, so that characters are overlapped.

Anyone has the same problem?

---

### Post by Starks on 2010-05-25
> **plun said:**
> :confused:   I can find his inactive ppa för xorg-testing but no ppa with 1.9 candidates.:confused:
You didn't even look at the page, did you?

It is far from inactive.

Also, how is this not a candidate for 1.9?
xorg-server                                               2:1.8.99.0+git20100520.ebd745ce-0ubuntu0sarvatt

---

### Post by plun on 2010-05-25
> **Starks said:**
> You didn't even look at the page, did you?

It is far from inactive.

Also, how is this not a candidate for 1.9?
xorg-server                                               2:1.8.99.0+git20100520.ebd745ce-0ubuntu0sarvatt

OK... sorry, just read the ppa description and didn't check any packages

Testing or not testing...?  :P

Phoronix wrote this about 1.9 and it seems to just be a bug-fix release.
[http://www.phoronix.com/scan.php?page=news_item&px=ODI3MA](http://www.phoronix.com/scan.php?page=news_item&px=ODI3MA)

---

### Post by zika on 2010-05-25
Beware, sarvatt/xorg-testing, just minutes made my machine without X. Luckily ppa-purge came to rescue... :)
ATI HD3650...

---

### Post by dino99 on 2010-05-25
hey, its the edge :P

---

### Post by autocrosser on 2010-05-25
Wow---looks like I'm missing all kinds of fun whilst on vacation.......:P

---

### Post by plun on 2010-05-25
> **zika said:**
> Beware, sarvatt/xorg-testing, just minutes made my machine without X. Luckily ppa-purge came to rescue... :)
ATI HD3650...

Thanks !    saving me from another test...:tongue:

---

### Post by Starks on 2010-05-25
You really should try it yourself before condemning.

xorg-testing works perfectly for me and i have an i945.

---

### Post by plun on 2010-05-25
> **Starks said:**
> You really should try it yourself before condemning.

xorg-testing works perfectly for me and i have an i945.

Ok.... but it breaks ABI for the nVidia driver, not sure if "Option "IgnoreABI" "True"" fixes this...:confused:

To test or not. ?...:)

---

### Post by Starks on 2010-05-25
Ignore ABI usually fixes the issues.

Are you using the new 256 driver?

---

### Post by plun on 2010-05-25
> **Starks said:**
> Ignore ABI usually fixes the issues.

Are you using the new 256 driver?

Yep.....

The 1.9 ppa is nevertheless terrible broken for my nVidia card :twisted:

a ppa-purge from recovery saved the situation, all ttys broken in normal mode....

Up and running again on xorg-edgers

---

### Post by Starks on 2010-05-25
Were you running xorg-testing and xorg-edgers at the same time. Choose one or the other.

If so, there will be ABI conflicts. Sometimes the cross-PPA ABIs will match or you will get lucky and be able to boot to X, but don't expect to be able to.

---

### Post by zika on 2010-05-26
> **Starks said:**
> Were you running xorg-testing and xorg-edgers at the same time. Choose one or the other.

If so, there will be ABI conflicts. Sometimes the cross-PPA ABIs will match or you will get lucky and be able to boot to X, but don't expect to be able to.Yes, that was the source of my mistake. I got it corrected, easily... Thank You. I'll stay with edgers I believe, for the time being...

---

### Post by jppr on 2010-05-27
> **plun said:**
> For the ultimate graphic freak.....

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Latest Xorg package

Latest nVidia driver

Latest Mesa


Please note ppa-purge if something goes wrong !

[https://launchpad.net/ppa-purge](https://launchpad.net/ppa-purge)

;)

I installed this in Linux Mint 9, i can´t understand how i update linux-meta packages... I mean linux-generic, linux-headers-generic and linux-image-generic... Why  those packages aren´t updated?

---

### Post by Starks on 2010-05-27
ppa-purge is already in the xorg-edgers repo in case people were wondering.

---

### Post by jppr on 2010-05-27
> **Starks said:**
> ppa-purge is already in the xorg-edgers repo in case people were wondering.

I don´t want purge anything... I just want do update linux-generic, linux-headers-generic and linux-image-generic... which still is 2.6.32.22.23 version. I just don´t understand how the f*ck those updated...

---

### Post by LKjell on 2010-05-27
> **jppr said:**
> I don´t wont purge anything... I just wont update linux-generic, linux-headers-generic and linux-image-generic... which is still 2.6.32.22.23 version. I just don´t understand how the f*ck those updated...

don't won't means you want. So you want to purge everything. But you do not want to update the kernel. And you do not know how they got updated.

Okey. If you pin with Synaptic then an apt-get update or using the update-manager will update the kernel. Sort of a bug. If you also use the check all in Synaptic it will also update. Therefore the only way to ensure that you do not update the kernel is to not update the kernel.

---

### Post by jppr on 2010-05-27
My kernel looks now in synaptic like this...

linux-generic 2.6.32.22.23
linux-headers 2.6.32-22
linux-headers-2-6-32-22-generic
linux-headers-2-6-34-4
linux-headers-2.6.34-4-generic
linux-headers-generic 2.6.32.22.23

linux-image-2.6.32.22-generic
linux-image-2.6.34-4-generic
linux-image-generic 2-6-32-22.23
linux-libc-dev 2.6.34-4.11

Yes i know how update system in synaptic and update-manager but it don´t change anything. Those 2.6.32 packages don´t updated. This is now Linux Mint 9. I dont have any kernel problems in Maverick

---

### Post by LKjell on 2010-05-27
Do you want to update or not is the question.

---

### Post by jppr on 2010-05-27
> **LKjell said:**
> Do you want to update or not is the question.

Yes, but i don´t now understand how i updated those 2.6.32 packages. it´s not help and change anything that i pin in synaptic update...

I installed this [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") in Linux Mint 9 and only problem is that kernel problem.

---

### Post by dino99 on 2010-05-27
> **jppr said:**
> Yes, but i don´t now understand how i updated those 2.6.32 packages. it´s not help and change anything that i pin in synaptic update...

I installed this [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") in Linux Mint 9 and only problem is that kernel problem.

when the ppa has been added, on which release is it pointing ?

---

### Post by jppr on 2010-05-27
> **dino99 said:**
> when the ppa has been added, on which release is it pointing ?
Lucid

---

### Post by seeker5528 on 2010-05-27
> **jppr said:**
> My kernel looks now in synaptic like this...

linux-generic 2.6.32.22.23
linux-headers 2.6.32-22
linux-headers-2-6-32-22-generic
linux-headers-2-6-34-4
linux-headers-2.6.34-4-generic
linux-headers-generic 2.6.32.22.23

linux-image-2.6.32.22-generic
linux-image-2.6.34-4-generic
linux-image-generic 2-6-32-22.23
linux-libc-dev 2.6.34-4.11

Yes i know how update system in synaptic and update-manager but it don´t change anything. Those 2.6.32 packages don´t updated. This is now Linux Mint 9. I dont have any kernel problems in Maverick

I can't think of any reason Mint would handle kernel meta-packages any differently than Debian and Ubuntu.

The meta-packages are only there to make sure you are updated to whatever happens to be the default version of the kernel at any given time.

The use of the meta-package mainly factors in in 3 ways. 

[list]1. If you are starting with a minimal install and adding what you want to it, the meta-package gives you a version of the kernel you know the developers are putting more of their time and effort into to smooth out issues, make sure modules work, modules are backported, etc... because it's the version they expect most people to be running. [/list]

[list]2. It makes sure you get updated to the newer kernel when doing a distribution upgrade.[/list]

[list]3. If you follow the development cycle, makes sure you are up to date with the default kernel during the development cycle since you should never be provided a kernel with an ABI change as an update to your existing kernel.[/list]

There is a possible 4th thing where there could be an update to the default kernel in a release version of the distribution that could require an abi change, but then there is extra work required to get the update out there and the user would take care of any modules they compiled and installed, so I expect they try to avoid that as much as possible.

If the kernel meta-packages won't update, then it's because there is a dependency issue, usually some package that has not made it into the archive yet.

But in your case I'm assuming.....

[list]You are not being shown that there is an update.[/list]
[list]That Mint 9 was released with the 2.6.32 version of kernel as the default.[/list]
[list]Through normal update channels, and I wouldn't expect it from unofficial sources providing updated kernels either, there will never be a meta-package that points to something other than a 2.6.32 kernel for Mint 9 because that is what selected as the default for the release.[/list]

Sound about right?

Later, Seeker

---

### Post by plun on 2010-06-05
Major upgrade tonight.....

- Mesa 0.7.9

- Xorg 1.8.2 RC1 (came earlier)

- nVidia 256.29 (came earlier)

- several Intel-driver upgrades this week


Phoronix article:
[http://www.phoronix.com/scan.php?page=news_item&px=ODMxMg](http://www.phoronix.com/scan.php?page=news_item&px=ODMxMg)

--

---

### Post by james_xxx on 2010-06-14
I may well be posting this in the wrong place, but after installing updated xorg-edgers packages this morning in Lucid, compositing is no longer working.

To play around, I was hoping to get rid of the configs & packages from xorg-edgers, using ppa-purge. However, when I run 'sudo ppa-purge xorg-edgers'. I get the following error:

```
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa

```

Can anyone offer any assistance on this?

---

### Post by zika on 2010-06-14
> **james_xxx said:**
> I may well be posting this in the wrong place, but after installing updated xorg-edgers packages this morning in Lucid, compositing is no longer working.

To play around, I was hoping to get rid of the configs & packages from xorg-edgers, using ppa-purge. However, when I run 'sudo ppa-purge xorg-edgers'. I get the following error:

```
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa

```

Can anyone offer any assistance on this?I do not remember syntax clearly, but, did You try with sudo ppa-purge xorg-edgers/ppa? I think that worked for me... I have numerous successful purges...

---

### Post by james_xxx on 2010-06-14
Neither of those seemed to work, either.

---

### Post by plun on 2010-06-14
> **james_xxx said:**
> Neither of those seemed to work, either.

Please show us your output from this terminal command
```

X -version
```

---

### Post by james_xxx on 2010-06-15
After messing with this issue for a while yesterday, I finally decided to do a fresh Lucid install, so I will not be able to report back on the X version I'd been using. 

Of all things, my display problems seem to have been largely alleviated by the fresh installation.

Edit:
I take it back. Things are no better. Already two X crashes today, with a lot of '[TTM] AGP Bind memory failed' in /var/log/syslog.

---

### Post by plun on 2010-06-19
New nVidia RC driver, ver 256.35 available from Xorg-edgers

Info:
[http://www.nvnews.net/vbulletin/showthread.php?p=2273450](http://www.nvnews.net/vbulletin/showthread.php?p=2273450)

No problems so far.....

---

### Post by autocrosser on 2010-06-19
I'm in---I finally had to delete my xorg.conf with this update.....looks like between the driver & new xorg my SLI setup works "out of the box".  Feels VERY strange to be running without a xorg.conf that I've tweaked.......I've been making conf files for over 10 years now & don't think I'll "really" miss it...

---

### Post by cowbud on 2010-06-19
Sweet upgrading to this fixed the problem of the nvidia drivers not detecting my second monitor's resolution properly!

---

### Post by cecilpierce on 2010-06-24
I'm using xorg-edgers ppa and nvidia 256.35, anybody know why the third mouse button (button 1&2 together) doesn't work ?
If I hold down the wheel button it works !

---

### Post by Linuxforall on 2010-06-24
If all you want is the latest nvidia, the x-swat ppa has far less radical stuff and always updates to latest nvida beta in day of release.

---

### Post by plun on 2010-07-05
Xorg upgraded to version 1.8.2, no problems with my nVidia Laptop.

About:
[http://www.phoronix.com/scan.php?page=news_item&px=ODM4NA](http://www.phoronix.com/scan.php?page=news_item&px=ODM4NA)

--

---

### Post by VastOne on 2010-07-05
Using Xorg-edgers ppa to keep nVidia current...

Just updated to kernel 2.6.35-rc4 via the deb process

Is there a way to force via update/upgrade to rehash the xorg process so that it will apply to the new kernel?

What I usually do is use ppa-purge to remove xorg-edgers ppa and then re enable it thus reinstalling it... This is obviously cumbersome and counter productive..

Thanks

---

### Post by plun on 2010-07-05
> **VastOne said:**
> 

Is there a way to force via update/upgrade to rehash the xorg process so that it will apply to the new kernel?



DKMS takes care of that and automagic installs the driver for the kernel.

If something fails, just run in Low-graphics mode and reinstall the nvidia driver.

```
sudo apt-get install --reinstall nvidia-current
```

Running with 2.6.35-RC4 without any issues.

---

### Post by VastOne on 2010-07-05
> **plun said:**
> DKMS takes care of that and automagic installs the driver for the kernel.

If something fails, just run in Low-graphics mode and reinstall the nvidia driver.

```
sudo apt-get install --reinstall nvidia-current
```

Running with 2.6.35-RC4 without any issues.

Thanks Plun

On this upgrade to rc4, DKMS did what it should have. 

On the last 2 daily 999 kernels I tested, it did not work.

I appreciate the feedback and help!  :popcorn:

---

### Post by VastOne on 2010-07-05
> **plun said:**
> Xorg upgraded to version 1.8.2, no problems with my nVidia Laptop.

About:
[http://www.phoronix.com/scan.php?page=news_item&px=ODM4NA](http://www.phoronix.com/scan.php?page=news_item&px=ODM4NA)

--

Hmmmm

I usually always get the latest from edgers via an update/upgrade but 5 packages are being held back (one of them xserver-xorg-core) and I am still at X 1.8.1.902

---

### Post by hikaricore on 2010-07-05
are you using dist-upgrade?

---

### Post by VastOne on 2010-07-05
> **hikaricore said:**
> are you using dist-upgrade?

No

---

### Post by paul_in_london on 2010-07-05
> **plun said:**
> DKMS takes care of that and automagic installs the driver for the kernel.

If something fails, just run in Low-graphics mode and reinstall the nvidia driver.

```
sudo apt-get install --reinstall nvidia-current
```

Running with 2.6.35-RC4 without any issues.

I'm running with 2.6.35-999 (05-Jul-2010).

I don't have any packages held back at the moment, but Nvidia is now broken for me. I've tried with and without an xorg.conf. I can't even boot into low graphics mode properly unless I temporarily "hide" xorg.conf.

When I updated to today's build of 2.6.35-999 I reinstalled nvidia-current (256.35) as usual to no avail.

The nvidia module libglx.so seems to load ok, but Xorg.0.log shows a stack trace/segmentation fault:

```
X.Org X Server 1.8.2
Release Date: 2010-07-01
[    21.834] X Protocol Version 11, Revision 0
[    21.834] Build Operating System: Linux 2.6.24-27-xen i686 Ubuntu
[    21.834] Current Operating System: Linux maverick 2.6.35-999-generic #201007051223 SMP Mon Jul 5 12:35:40 UTC 2010 i686
[    21.834] Kernel command line: BOOT_IMAGE=/vmlinuz root=UUID=3c84db8d-e82f-4f46-8d26-8fb4c7925a47 ro ipv6.disable=1
[    21.834] Build Date: 05 July 2010  08:11:53PM
[    21.834] xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2 (For technical support please see http://www.ubuntu.com/support) 
[    21.835] Current version of pixman: 0.19.1
[    21.835] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.835] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.835] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul  5 21:59:34 2010
[    21.865] (==) Using config file: "/etc/X11/xorg.conf"
[    21.865] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.898] (==) ServerLayout "Layout0"
[    21.899] (**) |-->Screen "Screen0" (0)
[    21.899] (**) |   |-->Monitor "Monitor0"
[    21.899] (**) |   |-->Device "Device0"
[    21.899] (**) |-->Input Device "Keyboard0"
[    21.899] (**) |-->Input Device "Mouse0"
[    21.899] (==) Automatically adding devices
[    21.899] (==) Automatically enabling devices
[    21.931] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.931] 	Entry deleted from font path.
[    21.992] (**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.993] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.993] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.993] (WW) Disabling Keyboard0
[    21.993] (WW) Disabling Mouse0
[    21.993] (II) Loader magic: 0x81f3c60
[    21.993] (II) Module ABI versions:
[    21.993] 	X.Org ANSI C Emulation: 0.4
[    21.993] 	X.Org Video Driver: 7.0
[    21.993] 	X.Org XInput driver : 9.0
[    21.993] 	X.Org Server Extension : 3.0
[    22.033] (--) PCI:*(0:1:0:0) 10de:0611:0000:0000 nVidia Corporation G92 [GeForce 8800 GT] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[    22.033] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.033] (II) LoadModule: "extmod"
[    22.208] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.251] (II) Module extmod: vendor="X.Org Foundation"
[    22.251] 	compiled for 1.8.2, module version = 1.0.0
[    22.251] 	Module class: X.Org Server Extension
[    22.251] 	ABI class: X.Org Server Extension, version 3.0
[    22.251] (II) Loading extension MIT-SCREEN-SAVER
[    22.251] (II) Loading extension XFree86-VidModeExtension
[    22.251] (II) Loading extension XFree86-DGA
[    22.251] (II) Loading extension DPMS
[    22.251] (II) Loading extension XVideo
[    22.251] (II) Loading extension XVideo-MotionCompensation
[    22.251] (II) Loading extension X-Resource
[    22.251] (II) LoadModule: "dbe"
[    22.252] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.260] (II) Module dbe: vendor="X.Org Foundation"
[    22.260] 	compiled for 1.8.2, module version = 1.0.0
[    22.260] 	Module class: X.Org Server Extension
[    22.260] 	ABI class: X.Org Server Extension, version 3.0
[    22.260] (II) Loading extension DOUBLE-BUFFER
[COLOR="Red"][    22.260] (II) LoadModule: "glx"
[    22.260] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    22.843] (II) Module glx: vendor="NVIDIA Corporation"
[    22.843] 	compiled for 4.0.2, module version = 1.0.0
[    22.843] 	Module class: X.Org Server Extension
[    22.843] (II) NVIDIA GLX Module  256.35  Wed Jun 16 19:21:24 PDT 2010
[    22.843] (II) Loading extension GLX[/COLOR]
[    22.843] (II) LoadModule: "record"
[    22.843] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.863] (II) Module record: vendor="X.Org Foundation"
[    22.863] 	compiled for 1.8.2, module version = 1.13.0
[    22.863] 	Module class: X.Org Server Extension
[    22.863] 	ABI class: X.Org Server Extension, version 3.0
[    22.863] (II) Loading extension RECORD
[    22.863] (II) LoadModule: "dri"
[    22.863] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.980] (II) Module dri: vendor="X.Org Foundation"
[    22.980] 	compiled for 1.8.2, module version = 1.0.0
[    22.980] 	ABI class: X.Org Server Extension, version 3.0
[    22.981] (II) Loading extension XFree86-DRI
[    22.981] (II) LoadModule: "dri2"
[    22.981] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.981] (II) Module dri2: vendor="X.Org Foundation"
[    22.981] 	compiled for 1.8.2, module version = 1.2.0
[    22.981] 	ABI class: X.Org Server Extension, version 3.0
[    22.981] (II) Loading extension DRI2
[    22.981] (II) LoadModule: "nvidia"
[    22.981] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    23.018] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.018] 	compiled for 4.0.2, module version = 1.0.0
[    23.018] 	Module class: X.Org Video Driver
[    23.035] (II) NVIDIA dlloader X Driver  256.35  Wed Jun 16 18:59:34 PDT 2010
[    23.039] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.039] (++) using VT number 7

[    23.040] (II) Primary Device is: PCI 01@00:00:0
[    23.040] (II) Loading sub module "fb"
[    23.040] (II) LoadModule: "fb"
[    23.071] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.133] (II) Module fb: vendor="X.Org Foundation"
[    23.133] 	compiled for 1.8.2, module version = 1.0.0
[    23.133] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.134] (II) Loading sub module "wfb"
[    23.134] (II) LoadModule: "wfb"
[    23.134] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.185] (II) Module wfb: vendor="X.Org Foundation"
[    23.185] 	compiled for 1.8.2, module version = 1.0.0
[    23.185] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.185] (II) Loading sub module "ramdac"
[    23.185] (II) LoadModule: "ramdac"
[    23.185] (II) Module "ramdac" already built-in
[    23.209] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    23.209] (==) NVIDIA(0): RGB weight 888
[    23.209] (==) NVIDIA(0): Default visual is TrueColor
[    23.209] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.209] (**) NVIDIA(0): Enabling RENDER acceleration
[    23.209] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    23.209] (II) NVIDIA(0):     enabled.
[    24.459] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
[    24.459] (--) NVIDIA(0): Memory: 524288 kBytes
[    24.459] (--) NVIDIA(0): VideoBIOS: 62.92.16.00.04
[    24.459] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.459] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.459] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
[    24.459] (--) NVIDIA(0):     LG Electronics L246WH (DFP-0)
[    24.459] (--) NVIDIA(0): LG Electronics L246WH (DFP-0): 330.0 MHz maximum pixel clock
[    24.459] (--) NVIDIA(0): LG Electronics L246WH (DFP-0): Internal Dual Link TMDS
[    24.549] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.549] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.549] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.549] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.549] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.549] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.549] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.549] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.549] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.549] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.549] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.550] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.550] (WW) NVIDIA(0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[    24.550] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    24.550] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    24.550] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.550] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.550] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.550] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.550] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.550] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.550] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    24.550] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.550] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.550] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    24.550] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.550] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    24.550] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.550] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.550] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    24.552] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.552] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.552] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.552] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.552] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.554] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.554] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.555] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.555] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.555] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.555] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.555] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.555] (WW) NVIDIA(0):     EDID's valid HorizSync range (30.000-83.000 kHz) would
[    24.555] (WW) NVIDIA(0):     exclude this mode's HorizSync (28.1 kHz); ignoring
[    24.555] (WW) NVIDIA(0):     HorizSync check for mode "1920x1080".
[    24.555] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.555] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[    24.555] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.555] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.555] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".
[    24.556] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.556] (WW) NVIDIA(0):     mode "720x576" is specified in the EDID; however, the
[    24.556] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.556] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.556] (WW) NVIDIA(0):     VertRefresh check for mode "720x576".
[    24.556] (WW) NVIDIA(0): The EDID for LG Electronics L246WH (DFP-0) contradicts itself:
[    24.556] (WW) NVIDIA(0):     mode "1280x720" is specified in the EDID; however, the
[    24.556] (WW) NVIDIA(0):     EDID's valid VertRefresh range (56.000-75.000 Hz) would
[    24.556] (WW) NVIDIA(0):     exclude this mode's VertRefresh (50.0 Hz); ignoring
[    24.556] (WW) NVIDIA(0):     VertRefresh check for mode "1280x720".
[    24.593] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    24.593] (==) NVIDIA(0): 
[    24.593] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    24.593] (==) NVIDIA(0):     will be used as the requested mode.
[    24.593] (==) NVIDIA(0): 
[    24.593] (II) NVIDIA(0): Validated modes:
[    24.593] (II) NVIDIA(0):     "nvidia-auto-select"
[    24.593] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    24.635] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    24.635] (--) NVIDIA(0):     option
[    24.635] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    24.635] (--) Depth 24 pixmap format is 32 bpp
[    24.635] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    24.637] (II) NVIDIA(0): Initialized GPU GART.
[    24.647] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    24.748] (II) Loading extension NV-GLX
[    24.860] (II) NVIDIA(0): Initialized OpenGL Acceleration
[    24.928] (==) NVIDIA(0): Disabling shared memory pixmaps
[    24.928] (II) NVIDIA(0): Initialized X Rendering Acceleration
[    24.928] (==) NVIDIA(0): Backing store disabled
[    24.928] (==) NVIDIA(0): Silken mouse enabled
[    24.958] (**) NVIDIA(0): DPMS enabled
[    24.958] (II) Loading extension NV-CONTROL
[    24.959] (II) Loading extension XINERAMA
[    24.959] (II) Loading sub module "dri2"
[    24.959] (II) LoadModule: "dri2"
[    24.959] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.959] (II) NVIDIA(0): [DRI2] Setup complete
[    24.959] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    24.959] (==) RandR enabled
[    24.959] (II) Initializing built-in extension Generic Event Extension
[    24.959] (II) Initializing built-in extension SHAPE
[    24.959] (II) Initializing built-in extension MIT-SHM
[    24.959] (II) Initializing built-in extension XInputExtension
[    24.959] (II) Initializing built-in extension XTEST
[    24.959] (II) Initializing built-in extension BIG-REQUESTS
[    24.959] (II) Initializing built-in extension SYNC
[    24.959] (II) Initializing built-in extension XKEYBOARD
[    24.959] (II) Initializing built-in extension XC-MISC
[    24.959] (II) Initializing built-in extension SECURITY
[    24.959] (II) Initializing built-in extension XINERAMA
[    24.959] (II) Initializing built-in extension XFIXES
[    24.959] (II) Initializing built-in extension RENDER
[    24.959] (II) Initializing built-in extension RANDR
[    24.959] (II) Initializing built-in extension COMPOSITE
[    24.959] (II) Initializing built-in extension DAMAGE
[    24.962] (II) Initializing extension GLX
[    24.994] [dix] Could not init font path element unix/:7100, removing from list!
[    25.477] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.560] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.560] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.560] (II) LoadModule: "evdev"
[    25.560] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.600] (II) Module evdev: vendor="X.Org Foundation"
[    25.600] 	compiled for 1.8.1.902, module version = 2.4.99
[    25.600] 	Module class: X.Org XInput Driver
[    25.600] 	ABI class: X.Org XInput driver, version 9.0
[    25.600] (**) Power Button: always reports core events
[    25.600] (**) Power Button: Device: "/dev/input/event1"
[    25.633] (--) Power Button: Found keys
[    25.633] (II) Power Button: Configuring as keyboard
[    25.633] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.633] (**) Option "xkb_rules" "evdev"
[    25.633] (**) Option "xkb_model" "pc105"
[    25.633] (**) Option "xkb_layout" "gb"
[    25.633] (**) Option "xkb_options" "lv3:ralt_switch"
[    25.635] (II) XKB: reuse xkmfile /var/lib/xkb/server-884C6C7246E5186E4DB7A4CD26B9F16BE06DFFDC.xkm
[    25.651] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.651] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.651] (**) Power Button: always reports core events
[    25.651] (**) Power Button: Device: "/dev/input/event0"
[    25.665] (--) Power Button: Found keys
[    25.665] (II) Power Button: Configuring as keyboard
[    25.665] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    25.665] (**) Option "xkb_rules" "evdev"
[    25.665] (**) Option "xkb_model" "pc105"
[    25.665] (**) Option "xkb_layout" "gb"
[    25.665] (**) Option "xkb_options" "lv3:ralt_switch"
[    25.674] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    25.674] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    25.674] (**) Logitech USB Receiver: always reports core events
[    25.674] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    25.685] (--) Logitech USB Receiver: Found keys
[    25.685] (II) Logitech USB Receiver: Configuring as keyboard
[    25.685] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    25.685] (**) Option "xkb_rules" "evdev"
[    25.685] (**) Option "xkb_model" "pc105"
[    25.685] (**) Option "xkb_layout" "gb"
[    25.685] (**) Option "xkb_options" "lv3:ralt_switch"
[    25.686] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    25.686] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    25.686] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    25.686] (**) Logitech USB Receiver: always reports core events
[    25.686] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    25.699] (--) Logitech USB Receiver: Found 12 mouse buttons
[    25.699] (--) Logitech USB Receiver: Found scroll wheel(s)
[    25.699] (--) Logitech USB Receiver: Found relative axes
[    25.699] (--) Logitech USB Receiver: Found x and y relative axes
[    25.699] (--) Logitech USB Receiver: Found absolute axes
[    25.699] (--) Logitech USB Receiver: Found keys
[    25.699] (II) Logitech USB Receiver: Configuring as mouse
[    25.699] (II) Logitech USB Receiver: Configuring as keyboard
[    25.699] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    25.699] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.699] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    25.699] (**) Option "xkb_rules" "evdev"
[    25.699] (**) Option "xkb_model" "pc105"
[    25.699] (**) Option "xkb_layout" "gb"
[    25.699] (**) Option "xkb_options" "lv3:ralt_switch"
[    25.699] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    25.699] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    25.699] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    25.699] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    25.699] (II) Logitech USB Receiver: initialized for relative axes.
[    25.699] (WW) Logitech USB Receiver: ignoring absolute axes.
[    25.699] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    25.699] (II) No input driver/identifier specified (ignoring)
[    25.765] 
[COLOR="Red"]Backtrace:
[    25.765] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x809e5fb]
[    25.765] 1: /usr/bin/X (0x8048000+0x59445) [0x80a1445]
[    25.765] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb786b410]
[    25.765] 3: /usr/lib/xorg/extra-modules/libglx.so (0xb7221000+0x1e739a) [0xb740839a]
[    25.765] 4: /usr/bin/X (0x8048000+0x4180c) [0x808980c]
[    25.765] 5: /usr/bin/X (0x8048000+0x46a97) [0x808ea97]
[    25.766] 6: /usr/bin/X (0x8048000+0x1ed05) [0x8066d05]
[    25.766] 7: /lib/libc.so.6 (__libc_start_main+0xe6) [0xb7588ce6]
[    25.766] 8: /usr/bin/X (0x8048000+0x1e8f1) [0x80668f1]
[    25.766] Segmentation fault at address 0x2
[    25.766] 
Fatal server error:
[    25.766] Caught signal 11 (Segmentation fault). Server aborting
[    25.766] 
[    25.766] [/COLOR]
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    25.766] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    25.766] 
[    25.829] (II) Power Button: Close
[    25.829] (II) UnloadModule: "evdev"
[    25.861] (II) Power Button: Close
[    25.861] (II) UnloadModule: "evdev"
[    25.909] (II) Logitech USB Receiver: Close
[    25.909] (II) UnloadModule: "evdev"
[    25.945] (II) Logitech USB Receiver: Close
[    25.945] (II) UnloadModule: "evdev"
```

Here are the updates I've had today (extracted from /var/log/aptitude):
```
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 11:50:14 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 95 packages, and remove 3 packages.
5,587kB of disk space will be used
===============================================================================
[REMOVE, NOT USED] librpm0
[REMOVE, NOT USED] librpmbuild0
[REMOVE, NOT USED] librpmio0
[INSTALL, DEPENDENCIES] libmono-messaging2.0-cil
[INSTALL, DEPENDENCIES] libmono-system-messaging2.0-cil
[INSTALL, DEPENDENCIES] libmono-wcf3.0-cil
[INSTALL, DEPENDENCIES] librpm1
[INSTALL, DEPENDENCIES] librpmbuild1
[INSTALL, DEPENDENCIES] librpmio1
[UPGRADE] chromium-browser 6.0.456.0~svn20100703r51609-0ubuntu1~ucd1 -> 6.0.457.0~svn20100705r51623-0ubuntu1~ucd1
[UPGRADE] chromium-browser-inspector 6.0.456.0~svn20100703r51609-0ubuntu1~ucd1 -> 6.0.457.0~svn20100705r51623-0ubuntu1~ucd1
[UPGRADE] chromium-browser-l10n 6.0.456.0~svn20100703r51609-0ubuntu1~ucd1 -> 6.0.457.0~svn20100705r51623-0ubuntu1~ucd1
[UPGRADE] gir1.0-clutter-1.0 1.2.12~git20100625.e32b0429-0ubuntu1~10.10~ricotz1 -> 1.2.12~git20100629.8769a627-0ubuntu1~10.10~ricotz1
[UPGRADE] hostname 3.03ubuntu1 -> 3.04ubuntu1
[UPGRADE] java-common 0.36 -> 0.38
[UPGRADE] libclutter-1.0-0 1.2.12~git20100625.e32b0429-0ubuntu1~10.10~ricotz1 -> 1.2.12~git20100629.8769a627-0ubuntu1~10.10~ricotz1
[UPGRADE] libice-dev 2:1.0.6+git20100604.1967c04c-0ubuntu0sarvatt -> 2:1.0.6+git20100705.5bb806a6-0ubuntu0sarvatt
[UPGRADE] libice6 2:1.0.6+git20100604.1967c04c-0ubuntu0sarvatt -> 2:1.0.6+git20100705.5bb806a6-0ubuntu0sarvatt
[UPGRADE] libmono-cairo1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-cairo2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-corlib1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-corlib2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-data-tds1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-data-tds2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-data1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-data2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-getoptions1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-getoptions2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-i18n-west1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-i18n-west2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-i18n1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-i18n2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-posix1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-posix2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-security1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-security2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-sharpzip0.84-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-sharpzip2.84-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-sqlite2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system-data1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system-data2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system-web1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system-web2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono-system2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono0 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono1.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libmono2.0-cil 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] libpciaccess0 0.11.0+git20100605.fa7cca61-0ubuntu0sarvatt -> 0.11.0+git20100705.3f59728d-0ubuntu0sarvatt
[UPGRADE] libsm-dev 2:1.1.1-1 -> 2:1.1.1+git20100705.e0be9c9d-0ubuntu0sarvatt
[UPGRADE] libsm6 2:1.1.1-1 -> 2:1.1.1+git20100705.e0be9c9d-0ubuntu0sarvatt
[UPGRADE] libxcomposite1 1:0.4.1+git20100604.7cc9ace4-0ubuntu0sarvatt -> 1:0.4.2+git20100705.01c4691e-0ubuntu0sarvatt
[UPGRADE] libxdamage1 1:1.1.3-1 -> 1:1.1.3+git20100705.8abc1c8e-0ubuntu0sarvatt
[UPGRADE] libxext-dev 2:1.1.2+git20100604.ce440c7d-0ubuntu0sarvatt -> 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt
[UPGRADE] libxext6 2:1.1.2+git20100604.ce440c7d-0ubuntu0sarvatt -> 2:1.1.2+git20100705.23643bd1-0ubuntu0sarvatt
[UPGRADE] libxfixes-dev 1:4.0.4+git20100604.bdebfcf8-0ubuntu0sarvatt -> 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt
[UPGRADE] libxfixes3 1:4.0.4+git20100604.bdebfcf8-0ubuntu0sarvatt -> 1:4.0.5+git20100705.01e803ae-0ubuntu0sarvatt
[UPGRADE] libxmu-dev 2:1.0.5+git20100604.af962b3b-0ubuntu0sarvatt -> 2:1.0.5+git20100705.e721c444-0ubuntu0sarvatt
[UPGRADE] libxmu-headers 2:1.0.5+git20100604.af962b3b-0ubuntu0sarvatt -> 2:1.0.5+git20100705.e721c444-0ubuntu0sarvatt
[UPGRADE] libxmu6 2:1.0.5+git20100604.af962b3b-0ubuntu0sarvatt -> 2:1.0.5+git20100705.e721c444-0ubuntu0sarvatt
[UPGRADE] libxmuu1 2:1.0.5+git20100604.af962b3b-0ubuntu0sarvatt -> 2:1.0.5+git20100705.e721c444-0ubuntu0sarvatt
[UPGRADE] libxrender-dev 1:0.9.5+git20100604.0dcf5c15-0ubuntu0sarvatt -> 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt
[UPGRADE] libxrender1 1:0.9.5+git20100604.0dcf5c15-0ubuntu0sarvatt -> 1:0.9.6+git20100705.d3d20437-0ubuntu0sarvatt
[UPGRADE] libxt-dev 1:1.0.8+git20100605.56621d3e-0ubuntu0sarvatt -> 1:1.0.8+git20100705.74cb722a-0ubuntu0sarvatt
[UPGRADE] libxt6 1:1.0.8+git20100605.56621d3e-0ubuntu0sarvatt -> 1:1.0.8+git20100705.74cb722a-0ubuntu0sarvatt
[UPGRADE] libxtst6 2:1.1.0+git20100604.c83fb2ae-0ubuntu0sarvatt -> 2:1.1.0+git20100705.1676c80d-0ubuntu0sarvatt
[UPGRADE] memtest86+ 4.00-2ubuntu3 -> 4.10-1ubuntu1
[UPGRADE] mono-2.0-gac 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] mono-gac 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] mono-runtime 2.4.4~svn151842-1ubuntu4 -> 2.6.3-3ubuntu1
[UPGRADE] rpm 4.7.2-1lbuild2 -> 4.8.1-5
[UPGRADE] rpm-common 4.7.2-1lbuild2 -> 4.8.1-5
[UPGRADE] rpm2cpio 4.7.2-1lbuild2 -> 4.8.1-5
[UPGRADE] terminator 0.93-1 -> 0.94~webupd8~lucid
[UPGRADE] whois 5.0.2ubuntu1 -> 5.0.5ubuntu1
[UPGRADE] xserver-xorg-video-ark 1:0.7.2+git20100604.b65010bb-0ubuntu0sarvatt -> 1:0.7.2+git20100705.7cf934ad-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-ati 1:6.13.99+git20100621.c3c5c8e2-0ubuntu0sarvatt -> 1:6.13.99+git20100705.37b34805-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-chips 1:1.2.2+git20100604.9f6bfce8-0ubuntu0sarvatt -> 1:1.2.2+git20100705.d8ce758f-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-i128 1:1.3.3+git20100604.3c58b1d2-0ubuntu0sarvatt -> 1:1.3.3+git20100705.ff026f65-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-i740 1:1.3.2+git20100604.8d8b9616-0ubuntu0sarvatt -> 1:1.3.2+git20100705.897fee2e-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-mach64 6.8.2+git20100604.ebfb29a0-0ubuntu0sarvatt -> 6.8.2+git20100705.6da9520f-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-neomagic 1:1.2.4+git20100604.fdfd0902-0ubuntu0sarvatt -> 1:1.2.5+git20100705.77faeb22-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-nv 1:2.1.17+git20100604.4fff9d3f-0ubuntu0sarvatt -> 1:2.1.17+git20100705.0f220eb6-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-r128 6.8.1+git20100604.c8657cd4-0ubuntu0sarvatt -> 6.8.1+git20100705.1936b9bb-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-radeon 1:6.13.99+git20100621.c3c5c8e2-0ubuntu0sarvatt -> 1:6.13.99+git20100705.37b34805-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-rendition 1:4.2.3+git20100604.432cefce-0ubuntu0sarvatt -> 1:4.2.4+git20100705.0bf606d1-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-s3 1:0.6.3+git20100604.36776d8a-0ubuntu0sarvatt -> 1:0.6.3+git20100705.798a0017-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-s3virge 1:1.10.4+git20100604.11fc32f5-0ubuntu0sarvatt -> 1:1.10.4+git20100705.f0ae83f0-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-savage 1:2.3.1+git20100604.b877be5d-0ubuntu0sarvatt -> 1:2.3.1+git20100705.1e9af8f8-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-siliconmotion 1:1.7.4+git20100604.2de1f7ae-0ubuntu0sarvatt -> 1:1.7.4+git20100705.8087bc23-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-sis 1:0.10.2+git20100604.13583aba-0ubuntu0sarvatt -> 1:0.10.3+git20100705.75a8a7c5-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-sisusb 1:0.9.3+git20100604.fdc38b41-0ubuntu0sarvatt -> 1:0.9.4+git20100705.43eab862-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-tdfx 1:1.4.3+git20100604.5e06e326-0ubuntu0sarvatt -> 1:1.4.3+git20100705.83661e56-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-trident 1:1.3.3+git20100604.cb7949bf-0ubuntu0sarvatt -> 1:1.3.4+git20100705.b5d17329-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-tseng 1:1.2.3+git20100604.bd71f657-0ubuntu0sarvatt -> 1:1.2.4+git20100705.f8084208-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-vesa 1:2.3.0+git20100604.d82f2e6e-0ubuntu0sarvatt -> 1:2.3.0+git20100705.fa1fcd48-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-vmware 1:11.0.1+git20100604.423d8a06-0ubuntu0sarvatt -> 1:11.0.1+git20100705.f307f77a-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-voodoo 1:1.2.3+git20100604.00216334-0ubuntu0sarvatt -> 1:1.2.4+git20100705.e58d3158-0ubuntu0sarvatt
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 11:54:23 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 4 packages, and remove 0 packages.
1,950kB of disk space will be freed
===============================================================================
[UPGRADE] xserver-common 2:1.8.1.902+git20100621+server-1.8-branch.2ae159ba-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt
[UPGRADE] xserver-xephyr 2:1.8.1.902+git20100621+server-1.8-branch.2ae159ba-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-core 2:1.8.1.902+git20100621+server-1.8-branch.2ae159ba-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt
[UPGRADE] xserver-xorg-video-intel 2:2.12.0+git20100702.afcd4182-0ubuntu0sarvatt -> 2:2.12.0+git20100705.a2aa4c23-0ubuntu0sarvatt
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 11:57:55 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
===============================================================================
[REINSTALL] nvidia-current
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 11:59:35 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 12:06:32 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 5 packages, and remove 0 packages.
20.5kB of disk space will be used
===============================================================================
[UPGRADE] apport 1.14.1-0ubuntu1 -> 1.14.1-0ubuntu2
[UPGRADE] apport-gtk 1.14.1-0ubuntu1 -> 1.14.1-0ubuntu2
[UPGRADE] apport-kde 1.14.1-0ubuntu1 -> 1.14.1-0ubuntu2
[UPGRADE] python-apport 1.14.1-0ubuntu1 -> 1.14.1-0ubuntu2
[UPGRADE] python-problem-report 1.14.1-0ubuntu1 -> 1.14.1-0ubuntu2
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 13:58:03 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 6 packages, and remove 0 packages.
8,192B of disk space will be used
===============================================================================
[UPGRADE] libgl1-mesa-dev 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
[UPGRADE] libgl1-mesa-dri 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
[UPGRADE] libgl1-mesa-glx 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
[UPGRADE] libglu1-mesa 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
[UPGRADE] libglu1-mesa-dev 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
[UPGRADE] mesa-common-dev 7.9.0+git20100702.6e83420e-0ubuntu0sarvatt -> 7.9.0+git20100705.a3b0aaf2-0ubuntu0sarvatt
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 13:58:46 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 14:02:14 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 15:15:09 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 15:15:23 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:03:33 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:03:53 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:14:16 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:23:13 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:31:28 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 3 packages, and remove 0 packages.
===============================================================================
[REINSTALL] xserver-common
[REINSTALL] xserver-xephyr
[REINSTALL] xserver-xorg-core
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:32:02 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
===============================================================================
[REINSTALL] xserver-xorg
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:32:28 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
===============================================================================
[REINSTALL] xorg
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 18:32:55 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 19:30:50 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
389kB of disk space will be freed
===============================================================================
[UPGRADE] grub-common 1.98+20100614-2ubuntu4 -> 1.98+20100705-1ubuntu1
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 19:35:00 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
===============================================================================
[REINSTALL] nvidia-current
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 19:36:57 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 19:43:39 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:04:53 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 12 packages, and remove 0 packages.
16.4kB of disk space will be freed
===============================================================================
[UPGRADE] eog 2.30.2-0ubuntu1 -> 2.30.2-1ubuntu1
[UPGRADE] gimp 2.6.8-2ubuntu1.1 -> 2.6.8-2ubuntu2
[UPGRADE] gimp-data 2.6.8-2ubuntu1.1 -> 2.6.8-2ubuntu2
[UPGRADE] gvfs 1.6.2-0ubuntu1 -> 1.6.2-0ubuntu2
[UPGRADE] gvfs-backends 1.6.2-0ubuntu1 -> 1.6.2-0ubuntu2
[UPGRADE] gvfs-bin 1.6.2-0ubuntu1 -> 1.6.2-0ubuntu2
[UPGRADE] gvfs-fuse 1.6.2-0ubuntu1 -> 1.6.2-0ubuntu2
[UPGRADE] libgimp2.0 2.6.8-2ubuntu1.1 -> 2.6.8-2ubuntu2
[UPGRADE] libgvfscommon0 1.6.2-0ubuntu1 -> 1.6.2-0ubuntu2
[UPGRADE] libxml2 2.7.7.dfsg-2ubuntu1 -> 2.7.7.dfsg-4
[UPGRADE] libxml2-utils 2.7.7.dfsg-2ubuntu1 -> 2.7.7.dfsg-4
[UPGRADE] python-libxml2 2.7.7.dfsg-2ubuntu1 -> 2.7.7.dfsg-4
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:06:15 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:06:22 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:21:44 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:36:19 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:37:00 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 1 packages.
71.5MB of disk space will be freed
===============================================================================
[REMOVE] nvidia-current
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:37:42 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 0 packages.
71.5MB of disk space will be used
===============================================================================
[INSTALL] nvidia-current
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:39:07 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Mon, Jul  5 2010 21:53:44 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 3 packages, and remove 0 packages.
===============================================================================
[UPGRADE] xserver-common 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2
[UPGRADE] xserver-xephyr 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2
[UPGRADE] xserver-xorg-core 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt -> 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2
===============================================================================

Log complete.
```

---

### Post by hikaricore on 2010-07-05
> **VastOne said:**
> No

If you're using maverick with edgers, you **should** be doing a dist-upgrade.
This way you won't have packages held back.  Usually this just means it wants to install extra packages.
As always be sure what you are doing when you update but as long as it isn't removing anything (or anything vital) just go for it.  :p

---

### Post by paul_in_london on 2010-07-05
Next things I tried were:

[LIST=1]
[*]Adding **Option "IgnoreABI" "True"** to xorg.conf
[*]Booting previous kernel
[*]Installing 2.6.35-rc4
[*]Purging the edgers ppa
[*]nvidia worked again
[*]Re-enabled edgers via /etc/apt/sources.list
[*]Rebooted to recovery mode
[*]sudo aptitude update
[*]sudo aptitude full-upgrade
[*]109 packages upgraded again I think it was
[*]Reboot
[/LIST]

nvidia still fscked :confused:

---

### Post by MikeDK on 2010-07-05
dont know if your all aware of this, but......im using xorg-edgers on my hp2510p and just got nvidia-common, nvidia-current and nvidia-settings installed via update-manager.....
Note this laptop hasnt got anything nvidia hardware installed.
why does update-manager install nvidia on a intel chipset based laptop????????????????????????????????????????????????????????????????????????????????????????????????????

Note. Im using Lucid x86_64 with default lucid kernel, has this got anything to do with the kernel?? or is it the update-manager? oor is it your ppa doing something wrong?????

---

### Post by ranch hand on 2010-07-05
All the drivers are installed by default so that the OS will work on any hardware.

The edgers ppa, if you read the page that comes up first, tells you that you should not just use the one for your box as they are packaged as a unit and may not work if you split them up.

When not using that ppa I remove the other drivers so that they do not need to be upgraded.  With the ppa I just leave it alone.

---

### Post by hikaricore on 2010-07-06
There are no benefits on this fourm to spamming punctuation for no good reason.
I felt it was worth mentioning that this kind of thing is generally frowned upon.  :p

---

### Post by Yellow Pasque on 2010-07-06
You can uninstall the other drivers by removing xserver-xorg-video-all and all the other packages for cards you don't have.
> The edgers ppa, if you read the page that comes up first, tells you that you should not just use the one for your box as they are packaged as a unit and may not work if you split them up.
The warning is referring to mixing different X components from other PPA or standard Ubuntu repos. It is safe to remove xserver-xorg-video-all metapackage and xserver-xorg-video packages for hardware you don't have. In fact, I would recommend people do that to save disk space and update install time. Also, bugs from some package can still screw up your system even if you don't have that video card (One time, I was hit by a bug in nvidia-common that caused errors in package management).

---

### Post by Linuxforall on 2010-07-06
> **MikeDK said:**
> dont know if your all aware of this, but......im using xorg-edgers on my hp2510p and just got nvidia-common, nvidia-current and nvidia-settings installed via update-manager.....
Note this laptop hasnt got anything nvidia hardware installed.
why does update-manager install nvidia on a intel chipset based laptop????????????????????????????????????????????????????????????????????????????????????????????????????

Note. Im using Lucid x86_64 with default lucid kernel, has this got anything to do with the kernel?? or is it the update-manager? oor is it your ppa doing something wrong?????


They are installed and kept in the repos in case you switch card and need an nvidia driver, they are not activated in any way.

---

### Post by Rob2687 on 2010-07-06
I am using a radeon card and with the nvidia packages that got installed my drivers got messed up. It was trying to use the nvidia drivers over the radeon ones.

---

### Post by MikeDK on 2010-07-06
> **Linuxforall said:**
> They are installed and kept in the repos in case you switch card and need an nvidia driver, they are not activated in any way.

you wanna bet???
i have not installed thes drivers my self, they came via update-manager, so its very clear that theres is something wrong here...

and still i dont have any kind of nvidia hardware installed on this laptop.

oh btw have been using ubuntu since 5.10

---

### Post by hikaricore on 2010-07-06
Want a cookie?

---

### Post by cariboo on 2010-07-06
> **MikeDK said:**
> you wanna bet???
i have not installed thes drivers my self, they came via update-manager, so its very clear that theres is something wrong here...

and still i dont have any kind of nvidia hardware installed on this laptop.

oh btw have been using ubuntu since 5.10

The various drivers that are installed, are dependencies of the ubuntu-desktop meta package, they get installed by default on a desktop installation.

---

### Post by MikeDK on 2010-07-07
yes but not nvidia-current, nvidia-common and nvidia-settings, these drivers is being installed by the user, i really wonder if its legal to put the proprietary nvidia-current driver in automatic installation, and i wonder why its being installed on a non-nvidia system, there is no nvidia-hardware what so ever on the system.

I could understand if it were the opensourced nouveau driver that was being installed pr default. but not the nvidia-current....

---

### Post by ranch hand on 2010-07-07
> **MikeDK said:**
> <snip>
Let's play nice here boys.  It is, after all, a testing OS.  A little humor is required when even thinking about it or you are going to go nuts.

Well, nuttier than you are now.  Can't be all that stable or you wouldn't be into running these development OS'.

We are all a little crazy so we need to get along with each other.  No one else wants to have much to do with us.

---

### Post by paul_in_london on 2010-07-07
Slight improvement after yesterday's updates - although nvidia is still broken, at least I now get a usable desktop when I'm dropped into "low graphics mode".

Didn't get round to checking the logs last night to see if the error messages were any different. Will see what tonight brings when I get back...

---

### Post by plun on 2010-07-07
> **paul_in_london said:**
> Slight improvement after yesterday's updates - although nvidia is still broken, at least I now get a usable desktop when I'm dropped into "low graphics mode".

Didn't get round to checking the logs last night to see if the error messages were any different. Will see what tonight brings when I get back...

Noticed that the ppa was broken last night and todays upgrade went well.

But... the nvidia driver is broken for me both nvidia-current and manually install the version directly from nvidia. (low-graphics mode OK)

```
sudo ppa-purge xorg-edgers
```

for a while.......

:^o


--

---

### Post by caryb on 2010-07-07
Are you sure about the command "ppa-purge xorg-edgers"? I get command not found from the terminal prompt as self with sudo & as root


Cary

---

### Post by Yellow Pasque on 2010-07-07
> **caryb said:**
> Are you sure about the command "ppa-purge xorg-edgers"? I get command not found from the terminal prompt as self with sudo & as root


Cary
You have to install the ppa-purge package first.. (and use 'sudo')

---

### Post by paul_in_london on 2010-07-07
Now I'm seeing this error in Xorg.0.log

```

...
[    22.793] (II) LoadModule: "nvidia"
[    22.793] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.827] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: WindowTable
[    22.827] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    22.827] (II) UnloadModule: "nvidia"
[    22.827] (EE) Failed to load module "nvidia" (loader failed, 7)
[    22.827] (EE) No drivers available.
[    22.827] 
Fatal server error:
[    22.827] no screens found
```

Apparently it's a known issue:

[http://www.nvnews.net/vbulletin/showthread.php?t=152439](http://www.nvnews.net/vbulletin/showthread.php?t=152439)
[http://comments.gmane.org/gmane.comp.freedesktop.xorg/43902](http://comments.gmane.org/gmane.comp.freedesktop.xorg/43902)

---

### Post by caryb on 2010-07-07
Ok, I got the ppa-purge file. When I run it it comes up with Could not find package list for PPA: xorg-edgers?

Before anyone asks yes I do have it installed & the package list is in the source list

Cary

Ok found the problem, I had commented out the xorg-edgers line in the source list. After uncommenting & doing a apt-get update it had cached the ppa in memory (I got this from RTFM or in this case the ppa-purge script) & now it is purging away :-)

Cary

---

### Post by zika on 2010-07-08
It seems that ia32-libs that came today from XorgEdgers broke my Flash (10.1 installed through nspluginwrapper) (reinstall did not help). I went back to 64-bit plugin (copied libflashplayer.so in ~/.mozilla/plugins)...
Of course, purged all 32-bit stuff, again...
Anyone else having this "problem"...?

---

### Post by okaiji on 2010-07-10
> **zika said:**
> It seems that ia32-libs that came today from XorgEdgers broke my Flash (10.1 installed through nspluginwrapper) (reinstall did not help). I went back to 64-bit plugin (copied libflashplayer.so in ~/.mozilla/plugins)...
Of course, purged all 32-bit stuff, again...
Anyone else having this "problem"...?

Yes, my flash broke, thereafter reinstall, didn't help here too.

So I had to ppa-purge this time round.

Furthermore... on a side note.
2.6.35 RC4 kernel created an error in DKMS doesn't build. :mad:

---

### Post by VastOne on 2010-07-10
> **okaiji said:**
> Yes, my flash broke, thereafter reinstall, didn't help here too.

So I had to ppa-purge this time round.

Furthermore... on a side note.
2.6.35 RC4 kernel created an error in DKMS doesn't build. :mad:

Strange.  Neither of these issues happened on my 3 systems.

---

### Post by okaiji on 2010-07-10
I try purging my other sources, could be due to other ppas

---

### Post by plun on 2010-08-01
Nerd-warning, Warranty-warning and you can blow up your PC.  (Nothing for newbies !)

Up and running Xorg 1.9 with nVidias newest driver, ver 256.44

Info (nothing about Xorg 1.9)
[http://www.nvnews.net/vbulletin/showthread.php?p=2295223](http://www.nvnews.net/vbulletin/showthread.php?p=2295223)

The PPA is also upgraded to this driver.

I didn't manage to start so I also installed the driver downloaded from nVidia.

After checking xorg-logs I noticed the -ignoreABI warning so I added it to xorg.conf

```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```


And it works......:D

---

### Post by autocrosser on 2010-08-01
Sounds like FUN!!!!!  I'm heading into town for a couple of hours---will play with it when I get back.....

---

### Post by plun on 2010-08-01
> **autocrosser said:**
> Sounds like FUN!!!!!  I'm heading into town for a couple of hours---will play with it when I get back.....

Yup... it is for a "nerd"....:D

The PPA-driver probably works directly with -ignoreABI added, I didn't check that.  (This also probably breaks all warranties, so be careful)

No CPU problems and I am going to check performance with Unigine Heaven.

Thermal level and Powermizer also seems to be fine. Laptop, GeForce GT 330M GPU

---

### Post by MacUntu on 2010-08-01
Well, there's always ppa-purge, so there's no excuse not to try it! :D

---

### Post by plun on 2010-08-01
> **MacUntu said:**
> Well, there's always ppa-purge, so there's no excuse not to try it! :D

OK.....:p

More findings....

- Running kernel 2.6.35-13, suspend OK

- TTY is broken.....

- Unigine Heaven, 3D Benchmark OK, The GPU temp went up rather high, 73 degrees Celsius, a little better score for my hardware setup.

```
Unigine
Heaven Benchmark v2.1
FPS:    
19.2
Scores:    
483
Min FPS:    
11.4
Max FPS:    
37.5
Hardware
Binary:    
Linux 64bit GCC 4.3.2 Release May 20 2010
Operating system:    
Linux 2.6.35-13-generic x86_64
CPU model:    
Intel(R) Core(TM) i3 CPU M 330 @ 2.13GHz
CPU flags:    
2127MHz MMX SSE SSE2 SSE3 SSSE3 SSE41 SSE42 HTT
GPU model:    
GeForce GT 330M PCI Express 256.44 1024Mb
Settings
Render:    
opengl
Mode:    
1024x768 windowed
```

---

### Post by MacUntu on 2010-08-01
Hm, no luck with 256.35:
```
[    45.252] (II) LoadModule: "nvidia"
[    45.253] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    45.253] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: WindowTable
[    45.253] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    45.253] (II) UnloadModule: "nvidia"
[    45.253] (EE) Failed to load module "nvidia" (loader failed, 7)
[    45.253] (EE) No drivers available.
```

Will try the one from Nvidia's site.

Edit: Yup, 256.44 works fine.

---

### Post by plun on 2010-08-01
> **MacUntu said:**
> H

Edit: Yup, 256.44 works fine.

Great....;)

---

### Post by rajeev1204 on 2010-08-02
> **jfernyhough said:**
> I was just about to try it out when I read:
so probably just as well I didn't update!

(I'm seriously wondering whether getting an ATi-based laptop was a good idea... even things like mipmap-based blur in compiz don't work)


Just download the 10.7 catalyst driver directly then, it installs on any xserver version .Not sure if xserver 1.9 has major changes that prevent installation.So be careful .

But the new X hasnt come in yet .

---

### Post by paul_in_london on 2010-08-03
> **MacUntu said:**
> 

Edit: Yup, 256.44 works fine.

That's the good news - I've stuck with Xorg-edgers the whole time waiting (im)patiently for a new nvidia driver.

The bad news for me is that the GUI is more sluggish than it was when nvidia was still broken - e.g. noticeable delay when minimizing/maximising windows.

I do have gnome-shell installed, but don't run it very often. I usually stick with compiz out of inertia :)

Obviously I had to wait for the new nvidia driver, but now that I have compiz back again it doesn't seem to load properly with the desktop. Reloading it (with compiz fusion icon) seems to do the trick though.

---

### Post by plun on 2010-08-04
> **paul_in_london said:**
> 

Obviously I had to wait for the new nvidia driver, but now that I have compiz back again it doesn't seem to load properly with the desktop. Reloading it (with compiz fusion icon) seems to do the trick though.

246.44 works just fine with my laptop but I must use the driver downloaded from nVidia. I cannot figure out whats wrong with the driver from ppa.

Compiz broke several times yesterday, the package compiz-fusion-plugins-extra is still broken, I also disabled animations, after this breakage I just enabled desktop effects again.

---

### Post by VastOne on 2010-08-04
> **plun said:**
> 246.44 works just fine with my laptop but I must use the driver downloaded from nVidia. I cannot figure out whats wrong with the driver from ppa.

Compiz broke several times yesterday, the package compiz-fusion-plugins-extra is still broken, I also disabled animations, after this breakage I just enabled desktop effects again.

Strange that on both my MM and LL setups none of this happened to me.

---

### Post by plun on 2010-08-06
New Xorg

```
xorg-server (**2:1.8.99.905**+git20100805.7e0575ba-0ubuntu0sarvatt) maverick; urgency=low

  * Checkout from git 20100805 (master branch) up to commit
    7e0575baf14ec4a89492fd2780f9ab5b9244afbd
  * Only added debian/ tree from origin/ubuntu
 -- Robert Hooker <@ubuntu.com>   Thu, 05 Aug 2010 19:23:35 -0400
```

Reinstalled my nvidia driver and it works ok......

---

### Post by plun on 2010-08-06
Broken......:^o

```
The following packages will be upgraded: 
  debhelper foomatic-db libgee2 libgl1-mesa-dev libgl1-mesa-dri 
  libgl1-mesa-glx libglib2.0-0 libglib2.0-bin libglib2.0-data 
  libglib2.0-dev libglu1-mesa libglu1-mesa-dev libsysfs2 libwmf0.2-7 
  libwmf0.2-7-gtk mesa-common-dev mutter-common openprinting-ppds 
  ubuntu-restricted-extras{b} xserver-xephyr{b} xserver-xorg-core{b} 
  xserver-xorg-video-intel xserver-xorg-video-nouveau 
23 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6MB of archives. After unpacking 7,000kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg-core: Depends: xserver-common (>= 2:1.8.99.905+git20100806.8d7b7a0d-0ubuntu0sarvatt) but 2:1.8.99.905+git20100805.7e0575ba-0ubuntu0sarvatt is installed.
  ubuntu-restricted-extras: Depends: ubuntu-restricted-addons which is a virtual package.
  xserver-xephyr: Depends: xserver-common (>= 2:1.8.99.905+git20100806.8d7b7a0d-0ubuntu0sarvatt) but 2:1.8.99.905+git20100805.7e0575ba-0ubuntu0sarvatt is installed.
The following actions will resolve these dependencies:

      Remove the following packages:              
1)      lubuntu-core                              
2)      lubuntu-desktop                           
3)      ubuntu-desktop                            
4)      ubuntu-restricted-extras                  
5)      xorg                                      
6)      xserver-xephyr                            
7)      xserver-xorg                              
8)      xserver-xorg-core                         
9)      xserver-xorg-input-all                    
10)     xserver-xorg-input-evdev                  
11)     xserver-xorg-input-mouse                  
12)     xserver-xorg-input-synaptics              
13)     xserver-xorg-input-vmmouse                
14)     xserver-xorg-input-wacom                  
15)     xserver-xorg-video-all                    
16)     xserver-xorg-video-apm                    
17)     xserver-xorg-video-ark                    
18)     xserver-xorg-video-ati                    
19)     xserver-xorg-video-chips                  
20)     xserver-xorg-video-cirrus                 
21)     xserver-xorg-video-fbdev                  
22)     xserver-xorg-video-i128                   
23)     xserver-xorg-video-intel                  
24)     xserver-xorg-video-mach64                 
25)     xserver-xorg-video-mga                    
26)     xserver-xorg-video-neomagic               
27)     xserver-xorg-video-nouveau                
28)     xserver-xorg-video-nv                     
29)     xserver-xorg-video-openchrome             
30)     xserver-xorg-video-r128                   
31)     xserver-xorg-video-radeon                 
32)     xserver-xorg-video-rendition              
33)     xserver-xorg-video-s3                     
34)     xserver-xorg-video-s3virge                
35)     xserver-xorg-video-savage                 
36)     xserver-xorg-video-siliconmotion          
37)     xserver-xorg-video-sis                    
38)     xserver-xorg-video-sisusb                 
39)     xserver-xorg-video-tdfx                   
40)     xserver-xorg-video-trident                
41)     xserver-xorg-video-tseng                  
42)     xserver-xorg-video-v4l                    
43)     xserver-xorg-video-vesa                   
44)     xserver-xorg-video-vmware                 
45)     xserver-xorg-video-voodoo                 

      Leave the following dependencies unresolved:
46)     gdm recommends xserver-xorg               
47)     xinit recommends xserver-xorg | xserver   
48)     gnome-shell recommends xserver-xephyr     


Accept this solution? [Y/n/q/?] 

```

---

### Post by plun on 2010-08-06
Followup, the troublemaker seems to be ubuntu-restricted-extras.

```
The following packages have unmet dependencies:
  ubuntu-restricted-extras: Depends: ubuntu-restricted-addons which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     ubuntu-restricted-extras  

Accept this solution? [Y/n/q/?] 

```


This update:
[https://lists.ubuntu.com/archives/maverick-changes/2010-August/004993.html](https://lists.ubuntu.com/archives/maverick-changes/2010-August/004993.html)

Bug filed:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/614575](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/614575)


--

---

### Post by Harry33 on 2010-08-29
OK, now xorg-edgers have built the new nvidia-current drivers 256.52.
These drivers fix the xserver 1.9 ABI issue,
the line ignoreABI is no longer needed.

---

### Post by plun on 2010-08-29
> **Harry33 said:**
> OK, now xorg-edgers have built the new nvidia-current drivers 256.52.
These drivers fix the xserver 1.9 ABI issue,
the line ignoreABI is no longer needed.

Yep..... 

But now I am on the 2.6.36 kernel with new challenges... :D

[http://www.nvnews.net/vbulletin/showthread.php?t=154105](http://www.nvnews.net/vbulletin/showthread.php?t=154105)

The solution from Zander works just fine....

---

### Post by ktp on 2010-08-29
> **plun said:**
> Yep..... 

But now I am on the 2.6.36 kernel with new challenges... :D

[http://www.nvnews.net/vbulletin/showthread.php?t=154105](http://www.nvnews.net/vbulletin/showthread.php?t=154105)

The solution from Zander works just fine....

You like challenges don't you...why else would most of us be here.

Thanks for the link...saves me and maybe others few hours =)

---

### Post by Harry33 on 2010-09-04
Well now, after the latest update, incompatibility issue is gone:
nvidia-current_256.53-0ubuntu1 in mavericks repo supports
- xserver 1.9
- kernel 2.6.36

---

### Post by plun on 2010-09-04
> **Harry33 said:**
> Well now, after the latest update, incompatibility issue is gone:
nvidia-current_256.53-0ubuntu1 in mavericks repo supports
- xserver 1.9
- kernel 2.6.36

Nope the "patch" which just is a line removal fails......

```
Building initial module for 2.6.36-020636rc3-generic
patch: **** malformed patch at line 5: static struct file_operations nv_fops = {
Error! Application of patch nvidia-2.6.36-ioctl.patch failed.
Check /var/lib/dkms/nvidia-current/256.53/build/ for more information.
dpkg: error processing nvidia-current (--configure):

```

---

### Post by Milos_SD on 2010-09-04
Does anyone have issues with compiz not re-drawning the screen when something moves? I got that issue when I updated xserver and xorg from xorg-edgers repo. I have 2.6.36-rc3 kernel and nvidia 256.53 driver.

---

### Post by plun on 2010-09-04
> **Milos_SD said:**
> Does anyone have issues with compiz not re-drawning the screen when something moves? I got that issue when I updated xserver and xorg from xorg-edgers repo. I have 2.6.36-rc3 kernel and nvidia 256.53 driver. 

I have no problem with this running a Geforce GT 330M 

One thing I noticed is that xorg-edgers is often updated with Mesa packages and the nvidia driver must then be reinstalled.

---

### Post by Milos_SD on 2010-09-04
> **plun said:**
> I have no problem with this running a Geforce GT 330M 

One thing I noticed is that xorg-edgers is often updated with Mesa packages and the nvidia driver must then be reinstalled.

I know that. Something else is a problem. I can play 3D games, like Heroes of Newerth, but compiz isn't working as it should.

---

### Post by plun on 2010-09-04
> **Milos_SD said:**
> I know that. Something else is a problem. I can play 3D games, like Heroes of Newerth, but compiz isn't working as it should.

Well, I have both Mavericks Compiz and Compiz++ (0.9), both are running just fine....  (except animations with compiz++)

---

### Post by Milos_SD on 2010-09-04
> **plun said:**
> Well, I have both Mavericks Compiz and Compiz++ (0.9), both are running just fine....  (except animations with compiz++)

The problem was wallpaper plugin. It doesn't work in 0.8.6 and 0.9 compiz versions. I'll stay on compiz 0.9, because I can use expo with screen edge activation. In Mavericks ccsm I can't set it, just get a bug report. :)

---

### Post by Harry33 on 2010-09-05
> **plun said:**
> Nope the "patch" which just is a line removal fails......

```
Building initial module for 2.6.36-020636rc3-generic
patch: **** malformed patch at line 5: static struct file_operations nv_fops = {
Error! Application of patch nvidia-2.6.36-ioctl.patch failed.
Check /var/lib/dkms/nvidia-current/256.53/build/ for more information.
dpkg: error processing nvidia-current (--configure):

```

Plun,

Could you report that to Launchpad as well.
See Robert Hooker's text:

[I]nvidia-graphics-drivers (256.53-0ubuntu1) maverick; urgency=low
  [ Alberto Milone ]
  * New upstream release:
    - Fixed a bug that prevented XvMC from initializing in most
      cases.
    - Added support for xorg-server video driver ABI version 8,
      which will be included in the xorg-server-1.9 series of
      releases (LP: #616023).
    - Fixed a bug that caused extremely slow rendering of OpenGL
      applications on X screens other than screen 0 when using a
      compositing manager.
    - Fixed a regression introduced after 256.35 that caused
      stability problems on GPUs such as GeForce GT 240.
    - Fixed a slow kernel virtual address space leak observed
      when starting and stopping OpenGL, CUDA, or VDPAU
      applications.
    - Fixed a bug that left the system susceptible to hangs
      when running two or more VDPAU applications simultaneously.
  [ Robert Hooker ]
  * debian/dkms/patches/nvidia-2.6.36-ioctl.patch:
    - Add patch from nvnews to add compatibility with kernel
      2.6.36.[/I]

---

### Post by plun on 2010-09-05
> **Milos_SD said:**
> The problem was wallpaper plugin. It doesn't work in 0.8.6 and 0.9 compiz versions. I'll stay on compiz 0.9, because I can use expo with screen edge activation. In Mavericks ccsm I can't set it, just get a bug report. :)

Ok... I am not using the wallpaper plugin, I want my icons on desktop...;)

---

### Post by plun on 2010-09-05
> **Harry33 said:**
> Plun,

Could you report that to Launchpad as well.
See Robert Hooker's text:
  [ Robert Hooker ]
  * debian/dkms/patches/nvidia-2.6.36-ioctl.patch:
    - Add patch from nvnews to add compatibility with kernel
      2.6.36.[/I]

Ok, done !

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/630690](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/630690)

Needs a confirmation !

---

### Post by hugmenot on 2010-09-05
Anyone else seeing clipped notify-osd notification bubbles with Intel graphics when xorg-edgers is installed?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=168567&stc=1&d=1283687913[/IMG]

I confirmed this on my system by adding xorg-edgers booted into current Live-CD. IF this is real, what should I do about it?

---

### Post by Milos_SD on 2010-09-05
It is some bug in libpixman-1.0 package. Here are packages that work:

[http://rapidshare.com/files/417201102/pixman.tar.gz](http://rapidshare.com/files/417201102/pixman.tar.gz)

---

### Post by hugmenot on 2010-09-05
> **Milos_SD said:**
> It is some bug in libpixman-1.0 package. Here are packages that work:

[http://rapidshare.com/files/417201102/pixman.tar.gz](http://rapidshare.com/files/417201102/pixman.tar.gz)

I’m on i386. Where did you get those from and do you have references as to what the bug is?

---

### Post by cariboo on 2010-09-05
Why would anyone want to install anything from an untrusted source like Rapidshare, if the package is legitimate, it should be in a repository or ppa.

---

### Post by Milos_SD on 2010-09-05
It is from xorg-edgers PPA. But that version is not there anymore. Xorg-edgers package maintainer give me the link to all pixman packages. [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/p/pixman/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/p/pixman/)

But the packages that are not broken (the ones that I uploaded to rapidshare, and posted the link here), are not in PPA anymore.

P.S. I'm sorry that I uploaded packages to rapidshare, but I don't have my own PPA or repository.

---

### Post by cariboo on 2010-09-05
If you have a launchpad account, and have signed the [Ubuntu Code of Conduct]("http://http://www.ubuntu.com/community/conduct"). you can create your own ppa.

---

### Post by Rob2687 on 2010-09-05
Rapidshare gives payouts for X number of downloads do they not? :-\"

---

### Post by cariboo on 2010-09-05
Who checks the files on any download service to see if there isn't anything malicious included with the file. 

We had an incident about a year ago where a member downloaded a .deb from gnome-look.org that had a malicious script built into it. Fortunately the member noticed something that wasn't quite right with it and asked for advice before installing it. 

That is why we recommend you only install packages from trusted sources, like the repositories and ppa's

---

### Post by Harry33 on 2010-09-06
> **plun said:**
> Ok, done !

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/630690](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/630690)

Needs a confirmation !

Plun,
This is fixed now.
Alberto Milone fixed it => nvidia-current_256.53-0ubuntu2.
Will be soon in maverick's restricted repo.

---

### Post by ratcheer on 2010-09-06
> **Harry33 said:**
> Plun,
This is fixed now.
Alberto Milone fixed it => nvidia-current_256.53-0ubuntu2.
Will be soon in maverick's restricted repo.

Yes, it reinstalled from the repos for me, this morning.

Tim

---

### Post by paul_in_london on 2010-09-06
> **ratcheer said:**
> Yes, it reinstalled from the repos for me, this morning.

Tim

Yes, confirmed fixed. Now have 2.6.36-999 working with nvidia-current_256.53-0ubuntu2.

---

### Post by Harry33 on 2010-09-22
Just to inform you that Brandon Snider has uploaded the new NVidia beta driver 260.19.06 to the X Updates PPA, both for lucid and maverick, 32-bit and 64-bit:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

This beta driver fixes the annoying desktop antialiasing sluggishness issue,
launchpad bug 629910:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/629910](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/629910)

We are still waiting for Alberto Milone to upload the driver into maverick repos.

---

