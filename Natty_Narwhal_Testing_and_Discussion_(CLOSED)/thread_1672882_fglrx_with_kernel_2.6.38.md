---
title: "fglrx with kernel 2.6.38"
date: 2011-01-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2011-01-21
** Updated for fglrx 8.840 **

Alberto Milone has pushed a new fglrx-installer. See here for more details: [http://ubuntuforums.org/showthread.php?t=1717755](http://ubuntuforums.org/showthread.php?t=1717755)

It looks like it's pretty much compatible with xserver 1.10 and kernel 2.6.38 (bit daft if it isn't ;)). Nice.

Next up, fglrx with kernel 2.6.39. ;)


** Manual build instructions for historical and reference purposes **

**In summary:**
1) Download and extract [11.3]("http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run") from [AMD]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").
2) Apply the patch attached [here](http://osdir.com/ml/debian-bugs-dist/2011-02/msg00257.html)
3) Build packages
4) Install

**Details:**
1) Once downloaded:
$ sh ./ati-driver-installer-11-3-x86.x86_64.run --extract [name of directory e.g. ~/temp/ati]

This will extract the files so we can patch and build manually.

2) Download and apply the patch from [here](http://osdir.com/ml/attachments/txtq2PBdGtr8X.txt) to [dir]/common/lib/modules/fglrx/build_mod/firegl_public.c (or use the attached file at your own risk).

3) In the folder you extracted the files (let's call it ~/temp/ati/) run:
$ ./ati-installer.sh 8.831.2 --buildpkg Ubuntu/natty

This will place packages in the parent directory (e.g. ~/temp/)

4) In ~/temp/ (or wherever you put the files):
$ sudo dpkg -i *.deb

If you haven't already got an xorg.conf you will need to run:
$ sudo aticonfig --initial
and reboot.

---

### Post by rajeev1204 on 2011-01-22
> **jfernyhough said:**
> With the release of 2.6.38-rc1 fglrx is broken again. Surprise!

Nothing yet from Arch.

However, according to [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ati_r500_pflipper&num=1") (pinch of salt time) the OSS drivers are getting to the point where fglrx will be unnecessary, which would be great.


That article is misleading on many many counts.

---

### Post by Harry33 on 2011-01-22
Well first of all that Phoronix article was about ATI radeon r500 card test. So no HD cards was tested.
Then, it depends on how you read it.
For example (OpenArena v.0.8.5):
"open-source driver performance was still well behind that of the proprietary Catalyst driver from before the R500 support was dropped"
and
"ATI driver is now 40% faster than where it is at with an Ubuntu 10.10 stock installation. This though is just one third of the frame-rate as the Catalyst 9.3 driver".

---

### Post by t1497f35 on 2011-01-22
(offtopic)
I agree that Phoronix is often so optimistic that sometimes it's (unintentionally) misleading. The open source ATI drivers have still lots and lots to do to be speedwise on par with ATI if ever at all
(/offtopic)

---

### Post by rajeev1204 on 2011-01-22
I think its quite clear that the point of the open source driver is not to match the speed of the proprietary driver for every single case.

Its main focus is to provide out of the box OSS drivers which are stable and covers most needed functionality for a 'normal' user.The OSS drivers will never have the entire feature set of the proprietary drivers, though it might catch up as far as speed is concerned.

Ontopic.

Hey jferny, do keep us posted on any new patches which make this work for the new kernel.


cheers. :)

---

### Post by jfernyhough on 2011-01-22
OK, so apparently patches for 2.6.37 work with 2.6.38. I'm just about to reboot and try with -rc2.

:D

Bah... breaks VirtualBox's vboxdrv... :( Needs some manual patching according to here: [http://www.virtualbox.org/ticket/8143](http://www.virtualbox.org/ticket/8143). New thread with details: [http://ubuntuforums.org/showthread.php?p=10386607](http://ubuntuforums.org/showthread.php?p=10386607)

---

### Post by jfernyhough on 2011-01-22
It worked... first time... there must be something wrong... :D

fglrx (and vboxdrv) working fine with 2.6.38. Only thing I have lost is laptop panel brightness control, but this is down to the kernel as the same thing happens on both my 311c and 1749.

---

### Post by Skazzi on 2011-01-23
There are some problems with drivers have been installed that way.
> glxinfo | grep OpenGL
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5670
OpenGL version string: 4.1.10362 Compatibility Profile Context
OpenGL shading language version string: 4.10
OpenGL extensions:But wine told> err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctlyAnd if I want to preload libGL (such I made with nvidia-current), I'd take > ERROR: ld.so: object '/usr/lib/fglrx/libGL.so' from LD_PRELOAD cannot be preloaded: ignored

---

### Post by jfernyhough on 2011-01-27
11.1 is out, and Arch have only one patch listed here: [http://aur.archlinux.org/packages.php?ID=29111](http://aur.archlinux.org/packages.php?ID=29111)

I wonder if this actually will work straight off with 2.6.38? Downloading... :D

--edit
Hmm... built with no patches... interesting. About to reboot.

--edit 2
Crikey... it "Just Worked" &trade; ... I'm pleasantly surprised!

---

### Post by BrokeMahPC on 2011-01-27
Thank you for the pointers Jferny!

What GFX card did you do that with? Also could you do me and others a huge favour and write a few lines about where you got the 2.6.38 rc2 from and how you installed it? I'm a bit rusty.
Also did you do kernel 1st driver 2nd?

regards,

BrokeMahPC

---

### Post by andrek on 2011-01-27
Hey, I can confirm that fglrx 11.1 works great with 2.6.38rc2 kernel. I got it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc2-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc2-natty/)

---

### Post by rajeev1204 on 2011-01-27
Are you telling me that fglrx works fine even with the new X  server 1.10?

Sorry,i think that version has not landed in natty yet.Are we still on X Server 1.9?

---

### Post by andrek on 2011-01-28
We're still at 1.9 but I think I'd be better to be careful when upgrading to 1.10. I guess, let's say on 99% - it won't work.

---

### Post by Harry33 on 2011-01-28
> **rajeev1204 said:**
> Are you telling me that fglrx works fine even with the new X  server 1.10?

Sorry,i think that version has not landed in natty yet.Are we still on X Server 1.9?

Definitely recent latest fglrx will not support xserver 1.10.
But open source ati does support it.

---

### Post by jaansson on 2011-01-28
What about unity? Does that work with new fglrx? Havn't been able to log in to unity before, it has just been the background showing, and indicators seem to be working as network connection is showing up. Or will the classic desktop have to do it for now?

---

### Post by rajeev1204 on 2011-01-28
> **jaansson said:**
> What about unity? Does that work with new fglrx? Havn't been able to log in to unity before, it has just been the background showing, and indicators seem to be working as network connection is showing up. Or will the classic desktop have to do it for now?

Unity wont work with fglrx its a known bug and is set to be fixed by alpha 2 by the unity guys.

[https://bugs.launchpad.net/unity/+bug/685682](https://bugs.launchpad.net/unity/+bug/685682)

---

### Post by jaansson on 2011-01-28
> **rajeev1204 said:**
> Unity wont work with fglrx its a known bug and is set to be fixed by alpha 2 by the unity guys.

[https://bugs.launchpad.net/unity/+bug/685682](https://bugs.launchpad.net/unity/+bug/685682)

Oh, thanks. Thought I read somewhere before that it was a driver bug, but thanks for that link. Now I've got something more to look forward to :)

---

### Post by ELD on 2011-01-28
So it works with a newer kernel, but does it work with the newer xorg version? If not doesn't it make it pointless or do a new kernel and new xorg go hand in hand?

---

### Post by andrek on 2011-01-28
It's not pointless. 2.6.38 has introduced some synaptics multitouch patches which are amazing for me, as a touchpad user. I can always hold on upgrading the xorg stuff.

---

### Post by ELD on 2011-01-28
Well you just answered my question anyway.

I thought they might go hand in hand - if they don't then that's cool if the drivers work.

That's what i meant i thought they both got updated at the same time so it would break the driver - which isn't the case :)

---

### Post by BrokeMahPC on 2011-01-31
Looks like what GFX card people use is a secret? You are only giving half the information - we need to know what hardware you got it to work on too!

---

### Post by andrek on 2011-01-31
ATi Mobility 4570 @ Dell Studio 1555 if that helps you.

---

### Post by PelPix on 2011-02-01
It's broken in 2.6.38 rc3 again.  Probably an entirely new problem.  Dear dear.

---

### Post by jfernyhough on 2011-02-01
If you updated recently this could well be down to xserver 1.10.

> On Mon, Jan 31, 2011 at 08:37:16PM -0800, Bryce Harrington wrote:
> Alrighty, the new X server has been uploaded and all drivers queued to
> rebuild.
>
> New issues we know about:
>
> * -nvidia and -fglrx are broken. We'll need updated ones from the
> respective vendors. Use -nouveau or -ati respectively in the mean
> time.

--edit
Oh, no, it's not. Grr...

```
implicit declaration of function ‘acquire_console_sem’
```Sounds like a sema-init issue the same as .37 originally.

---

### Post by artemka373 on 2011-02-02
> **jfernyhough said:**
> If you updated recently this could well be down to xserver 1.10.



--edit
Oh, no, it's not. Grr...

```
implicit declaration of function &#8216;acquire_console_sem&#8217;
```Sounds like a sema-init issue the same as .37 originally.
Checkout this patch: [http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/3b716dfe326fef23](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/3b716dfe326fef23) (scroll down there for the .diff)
If you have no BKL (Big Kernel Lock), you have also need to comment 1914, 1920 lines in common/lib/modules/fglrx/build_mod/firegl_public.c

---

### Post by jfernyhough on 2011-02-04
Arch has a new patch* listed: [http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/2.6.38_console.patch](http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/2.6.38_console.patch)

This removes support for any .38 kernels older than -rc3, though. *It is the same patch as the previous post.

I'm at work so I can't test it until later.

--edit
OK, I've built using the new patch, reinstalled -rc3, and everything looked to work correctly. Just about to reboot.

--edit 2
Well that killed it. Don't use the patch as-is. I really should listen to people. :)

Question is now that I've removed fglrx, do I add edgers and try the newer ati drivers? I suppose I have to, really...

---

### Post by jfernyhough on 2011-02-04
Well waddayaknow... Compiz works fine with the OSS drivers, and the virtual console is the correct screen resolution. It may be that most people won't need fglrx soon...

Blur doesn't work though. :(

---

### Post by PGHammer on 2011-02-05
> **jfernyhough said:**
> Well waddayaknow... Compiz works fine with the OSS drivers, and the virtual console is the correct screen resolution. It may be that most people won't need fglrx soon...

Blur doesn't work though. :(

Unless you have HD6xxx hardware and/or need support in Compiz/Kwin for Blur, you can use the FOSS driver (R600c for HDXxxx) as it stands today.  That is not just the default in Natty, but the default in Maverick as well.  I'm using that driver for my HD5450 PCIe in Natty alpha 2 (and used it with openSuSE 11.4 M6 as well; both are x64).  Still, reliance on that binary blob is a VERY hard habit to break (mostly because we've had to).

---

### Post by jfernyhough on 2011-02-06
The most frustrating thing I've found with the OSS driver is that it won't power off my laptop panel correctly (e.g. with 'xset dpms force off' or similar). My external display goes blank as normal, but the internal one gets a groovy additive colour effect.

---

### Post by andrek on 2011-02-06
The OSS driver also doesn't have proper power management. There's a significant difference between the -ati driver and fglrx in terms of GPU temperature (and therefore fan speed AND battery time).

---

### Post by zyghom on 2011-02-07
> **andrek said:**
> The OSS driver also doesn't have proper power management. There's a significant difference between the -ati driver and fglrx in terms of GPU temperature (and therefore fan speed AND battery time).

very very true

---

### Post by ibladesi on 2011-02-10
applied patch to 2.6.38-rc4 - xserver would kinda start.. and then crash.. was using v1.9, not v1.10 
 
It was, however, nice to see the deb files generated and the packages install (along with the kernel modules compiling sucessfully).. Could it be my 3200HD in this terrible HP Touchsmart Tx2? Who knows? I'm not about to buy another ATI product to find out! (Although, I cannot say that 100% - I love my Phenom II)
 
Been following this thread for a while.. Been such a big help. Thanks to all those who carry AMD's ati linux division on their shoulders. I cannot believe they continue to put out such crap drivers and refuse to go open source. They make the end users do everything the hard way. Has there been a working out of the box release of fglrx for my system yet? NO. thats sad too.. I'm not exaggerating.
 
oh and btw.. regarding heat and power management.. This laptop.. when compiling a kernel.. gets to 90 deg C.. at that point, who cares if the gpu is hot.. this was with the fglrx drivers too

---

### Post by Hanmac on 2011-02-17
i hope the proprietary driver is coming soon, the free driver turn the cpu-usage of xserver >75%. my graphic card is:
 ati raedion 3300 (onboard). with the fglrx driver doesn't this happen. and i can play some games with the free driver like desmume

---

### Post by jfernyhough on 2011-02-17
Catalyst 11.2 is out, and though it builds it segfaults when X tries to start.

I'm hoping 11.3 will have early-look support ready for the release of Ubuntu 11.04.

---

### Post by diepes on 2011-02-20
What is the reason AMD/ATI does not want to fully support opensource drivers for there cards ?

Surely it would be a lot less work for them, and much better for there clients.

---

### Post by Harry33 on 2011-02-20
> **diepes said:**
> What is the reason AMD/ATI does not want to fully support opensource drivers for there cards ?

Surely it would be a lot less work for them, and much better for there clients.

What exactly do you mean?
AMD has released the specs for their cards in order to help Linux communities to build open source drivers.
Right now driver version 6.14 does have a wide support for the newest cards.
Do you mean AMD ought build open source drivers themselves?

The heading of this thread, fglrx on the other hand is not open source, though it is free.

---

### Post by rajeev1204 on 2011-02-20
> **diepes said:**
> What is the reason AMD/ATI does not want to fully support opensource drivers for there cards ?

Surely it would be a lot less work for them, and much better for there clients.


AMD do support the development of the open source drivers.Iam not sure what you mean by 'fully'.Core open source development comes directly from AMD and the rest from the xorg community developers.

They recently released documentation for the 6000 series as well is what i read.

Nvidia hardware also has a oss driver with experimental 3d at this stage .

I prefer the fglrx driver myself though.

You can follow these links [http://developer.amd.com/zones/opensource/pages/default.aspx](http://developer.amd.com/zones/opensource/pages/default.aspx)

and [http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by pkscwc on 2011-02-27
I got my system with Ubuntu10.10 and HD Radeon 3450 working with  kernel 2.6.38 (patched it up also) and catalyst 11.2 (fglrx 8.821 patched up with attached firegl_public.c) using the process as detailed above. The file firegl_public.c.bz2  given above required change at line 934. The changed file is attached.

I am going to use the same set of files i.e. latest [kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.38-rc6.tar.bz2") , its [patch ]("http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.38-rc6-git6.bz2")and the fglrx 8.821 / catalyst 11.2 files ( firegl_public.c file replaced with above file) on new phenom II x6 machine with hd5970 card.

Results will be posted here. 

Thanks. 

Pankaj.

---

### Post by ivanmmj on 2011-03-02
Did you have any luck with RC6? (RC7 is out. Didn't notice it until now.)

> **pkscwc said:**
> I got my system with Ubuntu10.10 and HD Radeon 3450 working with  kernel 2.6.38 (patched it up also) and catalyst 11.2 (fglrx 8.821 patched up with attached firegl_public.c) using the process as detailed above. The file firegl_public.c.bz2  given above required change at line 934. The changed file is attached.

I am going to use the same set of files i.e. latest [kernel]("http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.38-rc6.tar.bz2") , its [patch ]("http://www.kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.38-rc6-git6.bz2")and the fglrx 8.821 / catalyst 11.2 files ( firegl_public.c file replaced with above file) on new phenom II x6 machine with hd5970 card.

Results will be posted here. 

Thanks. 

Pankaj.

---

### Post by ivanmmj on 2011-03-02
I'm having an issue with the patched files here. The debs are created but they error out while installing.

> Error! Bad return status for module build on kernel: 2.6.38-rc3-ivan (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.821/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/fglrx.0.crash'
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.821-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-rc3-ivan
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev


Off I go to read the patch itself.



EDIT:
Fixed by patching the makefile as well. There's an updated version of the patch that I used. I'm going to try it with RC7 now.

---

### Post by hai2lp on 2011-03-16
I'm try using patch but its show many ```
Hunk #4 FAILED at
```
and still error

---

### Post by andrek on 2011-03-17
I'd suggest to wait a week/two/moar for AMD to make the new Catalyst. (either 11.3 or 11.4)

---

### Post by Dr.Paneas on 2011-03-20
Yeah, same error here. How can I go back to my old kernel ?

---

### Post by jfernyhough on 2011-03-20
This isn't a kernel issue at the moment, it's an issue with the version of XOrg.

---

### Post by Harry33 on 2011-03-20
> **jfernyhough said:**
> This isn't a kernel issue at the moment, it's an issue with the version of XOrg.

Actually this is not a kernel nor xserver 1.10 issue.
Fglrx (ATI proprietary drivers) do not support the latest xserver yet.
There are no working patches to that.
One can only wait for the new upgraded drivers
or
even better, install open source drivers:
xserver-xorg-video-ati.

---

### Post by jfernyhough on 2011-03-20
> **Harry33 said:**
> Fglrx (ATI proprietary drivers) do not support the latest xserver yet.That's what I meant. :rolleyes:

---

### Post by Harry33 on 2011-03-20
> **jfernyhough said:**
> That's what I meant. :rolleyes:

OK fine then. Sorry I misunderstood.:)

---

### Post by Hanmac on 2011-03-21
> even better, install open source drivers:
xserver-xorg-video-ati. 	

this does not work for me because the open source does not full support my onboard graphic card (Xorg > 70% cpu)

---

### Post by jfernyhough on 2011-03-21
> **Harry33 said:**
> OK fine then. Sorry I misunderstood.:)Don't worry - your answer was better. ;)

---

### Post by ubunaut on 2011-03-22
> **Harry33 said:**
> Actually this is not a kernel nor xserver 1.10 issue.
Fglrx (ATI proprietary drivers) do not support the latest xserver yet.
There are no working patches to that.
One can only wait for the new upgraded drivers
or
even better, install open source drivers:
xserver-xorg-video-ati.

Unfortunately the open source drivers don't work with as many 3D games as are supported by FGLRX.

---

### Post by Harry33 on 2011-03-22
> **ubunaut said:**
> Unfortunately the open source drivers don't work with as many 3D games as are supported by FGLRX.

Well that gaming issue is not a bug, it is merely the state of the open sources drivers.
Still, these dirvers are developing all the time.

---

### Post by ubunaut on 2011-03-22
> **Harry33 said:**
> Well that gaming issue is not a bug, it is merely the state of the open sources drivers.
Still, these dirvers are developing all the time.

It is difficult to replace FGLRX until the open source drivers are as widely compatible. It is great to see though that some games do work already.

---

### Post by pkscwc on 2011-03-25
Sorry, 
for late reply.
I did try with rc6 only.
Today , again , I am going to try on a new machine with same set of software.

---

### Post by pkscwc on 2011-03-25
My steps modified from above:

    
Unhappy fglrx with kernel 2.6.38-rc6



** Manual build instructions for Catalyst 11.2, fglrx 8.821, kernel 2.6.38-rc6 **

In summary:
1) Download and extract 11.2 from AMD.
2) Apply this patch
3) Build packages
4) Install

Details:
1) Once downloaded:
$ sh ./ati-driver-installer-11-2-x86.x86_64.run --extract [name of directory e.g. ~/temp/ati]

This will extract the files so we can patch and build manually.

2) Download and apply the patch from here to [dir]/common/lib/modules/fglrx/build_mod/firegl_public.c

3) In the folder you extracted the files (let's call it ~/temp/ati/) run:
$ ./ati-installer.sh 8.821 --buildpkg Ubuntu/maverick

This will place packages in the parent directory (e.g. ~/temp/)

4) In ~/temp/ (or wherever you put the files):
$ sudo dpkg -i *.deb

---

### Post by Arkantos on 2011-03-27
> **pkscwc said:**
> 
2) Download and apply the patch from here to [dir]/common/lib/modules/fglrx/build_mod/firegl_public.c


How to apply this patch?

> **pkscwc said:**
> 
4) In ~/temp/ (or wherever you put the files):
$ sudo dpkg -i *.deb

I tried this but I get these error messages:

> 
(Reading database ... 184597 files and directories currently installed.)
Preparing to replace fglrx 2:8.821-0ubuntu1 (using fglrx_8.821-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:8.821-0ubuntu1 (using fglrx-amdcccle_8.821-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.821-0ubuntu1 (using fglrx-dev_8.821-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-dev ...
Preparing to replace fglrx-modaliases 2:8.821-0ubuntu1 (using fglrx-modaliases_8.821-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
dpkg: dependency problems prevent configuration of fglrx:
 fglrx depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.821-0ubuntu1) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev

---

### Post by hexion on 2011-03-27
> **Arkantos said:**
> How to apply this patch?

It's not really a patch but a patched file. Just copy it to the location described overwriting the old file.

---

### Post by rajeev1204 on 2011-03-28
fglrx wont work with natty at the moment due to lack of xserver 1.10 support .



/offtopic

Funny how they call it 1.ten.It should have been 2.0 as far as simple math principles are concerned.Wonder where the devs learn such numbering.Its utterly erroneous.

---

### Post by lucazade on 2011-03-28
> **rajeev1204 said:**
> 
/offtopic

Funny how they call it 1.ten.It should have been 2.0 as far as simple math principles are concerned.Wonder where the devs learn such numbering.Its utterly erroneous.
True, I'm still wondering why.
I thought my math knowledge was poor! Maybe because it is a point instead of a comma?

---

### Post by cariboo on 2011-03-28
> **rajeev1204 said:**
> fglrx wont work with natty at the moment due to lack of xserver 1.10 support .



/offtopic

Funny how they call it 1.ten.It should have been 2.0 as far as simple math principles are concerned.Wonder where the devs learn such numbering.Its utterly erroneous.

To me it seems a logical progression, as far as I can see it shouldn't change to 2.0 until we've seen 1.99.

---

### Post by Harry33 on 2011-03-28
> **lucazade said:**
> True, I'm still wondering why.
I thought my math knowledge was poor! Maybe because it is a point instead of a comma?

I see your point.
That is how it is in math (according to our numeral system, base ten).
 - 1.10 is less than 1.2 (although 1.2 is not as accurate figure, it only has one decimal).
 - 1.9 is much higher than 1.20 or even 1.200.
:guitar:

---

### Post by lucazade on 2011-03-28
> **Harry33 said:**
> I see your point.
That is how it is in math (according to our numeral system, base ten).
 - 1.10 is less than 1.2 (although 1.2 is not as accurate figure, it only has one decimal).
 - 1.9 is much higher than 1.20 or even 1.200.
:guitar:

Strange thing is in my country we use the comma to separate decimals and not the point. Point is used only for thousands.

Every 0 after the last decimal, i hope to remember well, in math doesn't count..
so 1,1 or 1,10 or 1,100 is the same .. mmh .. :D

edit:
latest xserver was 1.9, now we have 1.10.. should be 2.0
correct?

---

### Post by lucazade on 2011-03-28
Incrementing sequences

"There are two schools of thought regarding how numeric version numbers are incremented: Most free software packages treat numbers as a continuous stream, therefore a free software or open source product may have version numbers 1.7.0, 1.8.0, 1.8.1, 1.9.0, 1.10.0, 1.11.0, 1.11.1, 1.11.2, etc. An example of such a software package is MediaWiki. However, many programs treat version numbers in another way, generally as decimal numbers, and may have version numbers such as 1.7, 1.8, 1.81, 1.82, 1.9, etc. In software packages using this way of numbering 1.81 is the next minor version after 1.8. Maintenance releases (i.e. bug fixes only) would generally be denoted as 1.81a, 1.81b, etc."

[http://en.wikipedia.org/wiki/Software_versioning](http://en.wikipedia.org/wiki/Software_versioning)

solved my "existential issue" :)

---

### Post by Harry33 on 2011-03-28
> **lucazade said:**
> 
Every 0 after the last decimal, i hope to remember well, in math doesn't count..
so 1,1 or 1,10 or 1,100 is the same .. mmh .. :D
...


In english . (dot) is the decimal separator and , (comma) is the thousand separator.

Yes they do count. The more decimal numbers the more accurate number it is.
You see 1.1 (one decimal shown) can very be 1.10009910 or 1.10010101 (8 decimals shown).

---

### Post by knavarathna92 on 2011-03-28
[http://twitter.com/CatalystCreator](http://twitter.com/CatalystCreator)

new catalyst driver releases tomorrow :D

---

### Post by rbrick49 on 2011-03-28
thank you lets hope it works

---

### Post by cariboo on 2011-03-28
Even though the driver should be released tomorrow, it's going to take a day or two for it to make it into the repositories

---

### Post by rbrick49 on 2011-03-28
> **cariboo907 said:**
> Even though the driver should be released tomorrow, it's going to take a day or two for it to make it into the repositories
thanks cariboo I can wait a couple of days I hope 3d and unity work with it

---

### Post by cariboo on 2011-03-29
You never know, Alberto may already have the new drivers, when the nVidia drivers were released it was within hours of the official release.

---

### Post by rbrick49 on 2011-03-29
cariboo lets not put to much pressure on Alberto,I jumped the gun by buying the new ati 6950 card  so i cant really complain about natty thats how it is new projects take time it seems to be coming together ok from my end. I havent had to much buggy drama

---

### Post by jfernyhough on 2011-03-29
11.3 is here (possibly useful), as is an 11.4 preview for Windows 7 (not useful). I'll keep trawling and see if there's an 11.4 for us. Currently downloading 11.3.

--edit
natty is a supported dist in packages, building packages now

--edit 2
Packages build, installing

--edit 3
dkms build fails, looks like we need to apply 2.6.38 patches

--edit 4
Applied console patch, dkms builds correctly. Now to reboot to test xserver 1.10 compatibility!

--edit 5
No dice. Currently segfaults with Ubuntu kernel 2.6.38-7, doesn't even get that far on 2.6.38.2 mainline. Waiting to see what Arch come up with. ;)

---

### Post by devguy on 2011-03-29
> **jfernyhough said:**
> 11.3 is here (possibly useful), as is an 11.4 preview for Windows 7 (not useful). I'll keep trawling and see if there's an 11.4 for us. Currently downloading 11.3.

--edit
natty is a supported dist in packages, building packages now

--edit 2
Packages build, installing

--edit 3
dkms build fails, looks like we need to apply 2.6.38 patches

--edit 4
Applied console patch, dkms builds correctly. Now to reboot to test xserver 1.10 compatibility!

Good info, but I'm not all that hopeful after reading that Catalyst 11.3 has "early look support" for OpenSuse 11.4, which only has kernel 2.6.37 and Xorg 1.9 (ie no better than Catalyst 11.2).

Please prove me wrong!  :)

---

### Post by Vrroom on 2011-03-29
> **jfernyhough said:**
> 11.3 is here (possibly useful), as is an 11.4 preview for Windows 7 (not useful). I'll keep trawling and see if there's an 11.4 for us. Currently downloading 11.3.

--edit
natty is a supported dist in packages, building packages now

--edit 2
Packages build, installing

--edit 3
dkms build fails, looks like we need to apply 2.6.38 patches

--edit 4
Applied console patch, dkms builds correctly. Now to reboot to test xserver 1.10 compatibility!

wow you are quick :D

---

### Post by jfernyhough on 2011-03-29
Ack... no go at the moment... :( Just get an X segfault on 2.6.38-7

You're right, though, it doesn't look promising until 11.4:
[quote=CatalystCreator]
Catalyst 11.4 preview is for Windows only. Have to wait until April for Cat 11.4 for Linux (but hoping to get Ubuntu 11.04 support in) [/quote]

---

### Post by devguy on 2011-03-29
> **jfernyhough said:**
> Ack... no go at the moment... :( Just get an X segfault on 2.6.38-7

We're probably going to have to wait for AMD to again release a special Ubuntu build into the Natty repositories (like with the past versions of Ubuntu).

Will probably arrive shortly after the Beta, or maybe Beta 2.

---

### Post by Vrroom on 2011-03-29
[https://twitter.com/#!/CatalystCreator/status/52800003906863105](https://twitter.com/#!/CatalystCreator/status/52800003906863105)

Catalyst 11.4 preview is for Windows only. Have to wait until April for Cat 11.4 for Linux (but hoping to get Ubuntu 11.04 support in)

---

### Post by chronniff on 2011-03-29
[http://www.phoronix.com/scan.php?page=news_item&px=OTI2OQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI2OQ)

this article about latest catalyst says there should be an ubuntu beta out thursday for natty

---

### Post by Harry33 on 2011-03-30
> **chronniff said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=OTI2OQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI2OQ)

this article about latest catalyst says there should be an ubuntu beta out thursday for natty

Well Natty beta is not an issue here, the fglrx is.
That Phoronix article has also info on fglrx:

> Don't expect to see it in Catalyst 11.4 either, but Catalyst 11.5 in May is where AMD should finally have the final xorg-server 1.10 ABI supported, due to the last minute ABI break before the 1.10 release in late February. 
...
This means AMD will likely provide Canonical with a Catalyst 11.5 pre-release sometime in the next two weeks while the official release of that will be out in May.

So, Catalyst 11.4 will not support xserver 1.10.

---

### Post by rbrick49 on 2011-03-30
> **Harry33 said:**
> Well Natty beta is not an issue here, the fglrx is.
That Phoronix article has also info on fglrx:



So, Catalyst 11.4 will not support xserver 1.10.
well just great thanks amd nvidia here I come I am reigned to the fact nvidia try to keep up with open source, amd dont really seem to care unity 2d will have to do for the mean time or good old reliable windows sad to say

---

### Post by Vrroom on 2011-03-30
A new fglrx-installer update has been pushed in natty few minutes back. Don't know if it will work with xorg 1.10.

---

### Post by rbrick49 on 2011-03-30
> **Vrroom said:**
> A new flgrx-installer update has been pushed in natty few minutes back. Don't know if it will work with xorg 1.10.

well I an going to give it a shot thanks for the heads up vrroom

---

### Post by rbrick49 on 2011-03-30
no failed to build on my system
asus motherboard
amd proccesor dual core 5000+
8 gig of ram
ati radeon 6950 graphics card
sorry Alberto

---

### Post by zarquon42 on 2011-03-30
Hi everyone, I stumbled across here, after yesterdays disappointment wiht the 11.3 driver - it seems that the new fglrx installer supports x-server 1.10 as the changelog states: build-dep on xserver-xorg-dev to >= 2:1.10.0. I can't test it, as I'm currently at work.  greetz  zarquon

---

### Post by rbrick49 on 2011-03-30
well folks I spat my dummy pulled out the ati amd 6950 graphics card went back to my onboard ati raeon 3100 card and unity 3d is working just fine on my computer now

---

### Post by hai2lp on 2011-03-30
> **rbrick49 said:**
> well folks I spat my dummy pulled out the ati amd 6950 graphics card went back to my onboard ati raeon 3100 card and unity 3d is working just fine on my computer now

It's the new Catalyst 11.3 supported with latest kernel 2.6.38 / Ubuntu Natty ?

---

### Post by Vrroom on 2011-03-30
> **rbrick49 said:**
> well folks I spat my dummy pulled out the ati amd 6950 graphics card went back to my onboard ati raeon 3100 card and unity 3d is working just fine on my computer now

with new fglrx or open source drivers?

---

### Post by rbrick49 on 2011-03-30
> **Vrroom said:**
> with new fglrx or open source drivers?

0x0dc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0dd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0de  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0df  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0e5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ea  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0eb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ec  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ed  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ee  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ef  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow

```

```

---

### Post by rbrick49 on 2011-03-30
> **Vrroom said:**
> with new fglrx or open source drivers?

ron@ron:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS780
OpenGL version string: 2.1 Mesa 7.10.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_shader_objects, GL_ARB_shader_stencil_export, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, GL_EXT_draw_buffers2, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_array, GL_OES_EGL_image, GL_OES_read_format, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_depth_clamp, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

with open source I dont no wether to try the new fglrx with this 3100 card or not maybe I should give it a sho to see what happens I only have to purge it if it doesnt build

---

### Post by rbrick49 on 2011-03-30
it wont build on 3100 card either

---

### Post by Vrroom on 2011-03-30
> **rbrick49 said:**
> it wont build on 3100 card either

:(

---

### Post by Harry33 on 2011-03-30
The new fglrx (ATI proprietary driver) is in Natty repos now.
That is actually not a Catalyst 11.4 release (there is no such release yet, latest stable is 11.3), but a prerelease (fglrx 8.84).

See here:
[https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.840-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.840-0ubuntu1)
It is claimed to support both xserver 1.10 and kernel 2.6.38.

It has been said to be a special prerelease edition for Canonical and Ubuntu-users.
See more info here:
[http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ](http://www.phoronix.com/scan.php?page=news_item&px=OTI3MQ)

---

### Post by jfernyhough on 2011-03-30
AMD pre-release drivers: another reason I love Ubuntu. :D

---

### Post by rbrick49 on 2011-03-30
Now Harry33 will this new update work with my 3100 card and my 6950 card I hope so as I am downloading the new fglrx update now 2 second ago I came back into natty forum and you have just posted a new kernel is out I have been trying this new fglrx most of the afternoon if this works I am coming to Finland to kiss you if it doesnt guess 
regards Ron

---

### Post by Harry33 on 2011-03-30
> **rbrick49 said:**
> Now Harry33 will this new update work with my 3100 card and my 6950 card I hope so as I am downloading the new fglrx update now 2 second ago I came back into natty forum and you have just posted a new kernel is out I have been trying this new fglrx most of the afternoon if this works I am coming to Finland to kiss you if it doesnt guess 
regards Ron

Kernel 2.6.39
This is just a rc1 yet, meaning the development has begun. 2.6.39 will not get pulled into Natty.

Fglrx 8.84
Alberto Milone (aka Tseliot) informs it is built-depend on xserver-xorg-dev (1.10.0).
Well I haven't tested. I am quite happy with the open source xserver-xorg-video-ati in one of my setups (Radeon HD 2600 Pro).

---

### Post by rbrick49 on 2011-03-30
> **Harry33 said:**
> Kernel 2.6.39
This is just a rc1 yet, meaning the development has begun. 2.6.39 will not get pulled into Natty.

Fglrx 8.84
Alberto Milone (aka Tseliot) informs it is built-depend on xserver-xorg-dev (1.10.0).
Well I haven't tested. I am quite happy with the open source xserver-xorg-video-ati in one of my setups (Radeon HD 2600 Pro).
well H the 3100 works but no unity I will give the 6950 a try and post back in a short while
regards Ron
ps no kisses yet H and I am not gay
the 6950 works graphics are beautiful but no unity so will see what new kernel does
regards Ron

---

### Post by cariboo on 2011-03-30
I just posted [this]("http://ubuntuforums.org/showthread.php?t=1717755").

---

### Post by jfernyhough on 2011-03-30
Updated op. Thanks cariboo!

(slightly jealous you got an email :P)

---

### Post by zarquon42 on 2011-03-31
Unity didn't come up by itself after installing fglrx (on a hd4670) - adding unity to startup programs did the job.  
Greetz  Stefan

---

### Post by jfernyhough on 2011-03-31
Unity should load either when you log in to the Ubuntu Desktop session, or enable the Unity plugin in ccsm.

---

### Post by meanpt on 2011-03-31
My ATI Mobility Radeon doesn't work at all. So far I couldn't pass the blackscren but I do hear the sound of the desktop landing and the see wireless white led, which means it's on. This is the reason I've been keeping naty inside virtualbox.

---

### Post by jfernyhough on 2011-03-31
I just tried booting with 2.6.38-7 rather than mainline 2.6.38.2 and I end up at a blank, black screen. Hmm. The mainline build works fine...

---

### Post by andrek on 2011-03-31
It works just fine and dandy on 2.6.38-7-generic here. (and the new fglrx and xserver of course) Unity is pretty laggy but works nevertheless. One bugger is that I have to do "compiz --replace" every time I boot into the classic mode.

---

### Post by ibladesi on 2011-04-01
Just got it working with 2.6.39-rc1!! I haven't seen a gui on this laptop in quite a while!!! I'm pumped!

wget [http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch](http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch)
wget [http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch](http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch)
wget [http://osdir.com/ml/attachments/txtq2PBdGtr8X.txt](http://osdir.com/ml/attachments/txtq2PBdGtr8X.txt)
mv ./txtq2PBdGtr8X.txt ./2.6.38-support.patch
if [ -f `echo $PWD`/ati-driver-installer-11-3-x86.x86_64.run ]
  then
echo "No need to download driver"
else
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)
fi
chmod +x ./ati-driver-installer-11-3-x86.x86_64.run
./ati-driver-installer-11-3-x86.x86_64.run --extract driver
mv *.patch ./driver/
cd ./driver/
patch -p1 -i *.patch
sudo ./ati-installer.sh 8.831 --install

yeah i think thats it.. feel free to sub in aria2c --split=40 in place of wget..

---

### Post by jfernyhough on 2011-04-01
Though those patches will get 11.3 to work with 2.6.39 it won't work with xorg-server 1.10. Good to know there are patches in the wings for when Catalyst 11.4 is released, though!

---

### Post by rajeev1204 on 2011-04-01
Additional drivers (jockey) offers fglrx now.A few unity updates coming soon which will hopefully make the unity desktop working for fglrx users.


edit:unity wont work, all i have is a blank screen with a badly rendered wallpaper in the background.

---

### Post by ikt on 2011-04-01
> **rajeev1204 said:**
> edit:unity wont work, all i have is a blank screen with a badly rendered wallpaper in the background.

confirmed, hoping this is fixed.

---

### Post by Vrroom on 2011-04-01
Same here. Have to use classic desktop and now I am missing unity.

---

### Post by cubeist on 2011-04-01
> **Vrroom said:**
> Same here. Have to use classic desktop and now I am missing unity.

Using the daily builds from the Unity PPA will work with fglrx.
[https://launchpad.net/~unity](https://launchpad.net/~unity)

---

### Post by Vrroom on 2011-04-01
Yes, but I will wait for next compiz release in repos. So for those who are not getting unity working with fglrx, here is what is happening:

For unity to work with new fglrx, we need both latest compiz and unity versions. Latest unity 3.8.2 has been released, but latest compiz with patch for fglrx has not been released in repos. So once you get an update to compiz, unity will work.

However, you can get compiz from daily builds that have patch for fglrx from here---> [https://launchpad.net/~unity/+archive/daily](https://launchpad.net/~unity/+archive/daily)

So, its up to you. You can wait for next compiz release in repos and use classic desktop for time being or install latest compiz from daily build PPA and get unity working.

---

### Post by waspbr on 2011-04-01
^^^

the daily unity works well-ish with the fglrx drivers, unity doesn't seem to load at startup for me, but this is easily fixed with 

```
compiz --replace
```

I even made a launcher for that code in case of compiz breaking, which is does once in a while. 

On the plus side, the screen tearing issue seems to have been resolved. I would normally see some tearing when I would move the wobbly windows around but nothing this time, 

Things are getting better but there is still some ground to cover.

---

### Post by ibladesi on 2011-04-01
yeah I have 2.6.39 with older 1.9.2.901 xserver.. The 8.840 stuff wasn't working for me. If you have xserver 1.10, i  think the 8.840 patched will work. 

I find it a little strange that we hear nothing of 11-3 and then on the 11th hour.. err 29th day AMD rushes it out? The files do read 3-24 tho.. 

I cannot imagine the madness if there were ati-proprietary-nightlies..

---

### Post by Vrroom on 2011-04-01
> **waspbr said:**
> ^^^

the daily unity works well-ish with the fglrx drivers, unity doesn't seem to load at startup for me, but this is easily fixed with 

```
compiz --replace
```

I even made a launcher for that code in case of compiz breaking, which is does once in a while. 

On the plus side, the screen tearing issue seems to have been resolved. I would normally see some tearing when I would move the wobbly windows around but nothing this time, 

Things are getting better but there is still some ground to cover.

Yeh I saw that and it is configurable. If you turn off vsync, there will be visual tearing similar to fglrx drivers in the past but you will get more FPS in games. If you turn on vsync fully there will be no visual tearing but you will get relatively less FPS in games as is vertical refresh sync is a bit resource hungry.

Now the best part is that you can customize these settings on per application basis. Really cool.

---

### Post by Cam! on 2011-04-01
Hey! I just installed the beta for 11.04, and I'm using the default drivers for my ATI Radeon HD 6850. How do I install the pre-release drivers?

---

### Post by zarquon42 on 2011-04-02
Everything seemed to work fine - until I tried to watch a movie - there is a slight stuttering in the video output - hardly noticable but makes you dizzy after a while - returning to the open source drivers solved the problem (reinstalling fglrx not). 
I'm using a ATI HD 4670 mobile.

EDIT: unchecking Sync to Vblank in compizconfigsettings-manager -> openGL resolved the issue of bad 2D performance (I didn't find it first, as it moved from "general options-> display settings" to "OpenGL" settings). Instead the Tear-Free option in ATI-CCC can be used.

---

### Post by Hanmac on 2011-04-06
same problem there: graphic things like videos, games or other programs draw over all other windows and even over kontextmenus
the only thing that work is to minimize all other windows

---

### Post by rajeev1204 on 2011-04-07
Hi

Got some updates in compiz yesterday and unity runs now with fglrx.But it crashes too early if you do anything.They seem to have pushed the unity daily into main now.

Crashes with a few alt tabs or any other key for that matter.Very sluggish when its working.And the desktop freezes in a minute or so.

Iam back to classic desktop atm.

---

### Post by ibladesi on 2011-04-27
latest 11.4 (still) needs patches to successfully create module.. at least on my build of kernel 2.6.39-rc5
 
wget [http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch](http://www.mindwerks.net/wp-content/uploads/2011/03/2.6.39_bkl.patch)
wget [http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch](http://www.mindwerks.net/wp-content/uploads/2011/03/no_bkl.patch)
wget [http://osdir.com/ml/attachments/txtq2PBdGtr8X.txt](http://osdir.com/ml/attachments/txtq2PBdGtr8X.txt)
mv ./txtq2PBdGtr8X.txt ./2.6.38-support.patch
if [ -f `echo $PWD`/ati-driver-installer-11-4-x86.x86_64.run ]
then
echo "No need to download driver"
else
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-4-x86.x86_64.run)
fi
chmod +x ./ati-driver-installer-11-4-x86.x86_64.run
./ati-driver-installer-11-4-x86.x86_64.run --extract driver
mv *.patch ./driver/
cd ./driver/
patch -p1 -i 2.6.38-support.patch
patch -p1 -i 2.6.39_bkl.patch
patch -p1 -i no_bkl.patch
sudo ./ati-installer.sh 8.841 --install
 
in case forum code messes up what I wrote.. 
[http://home.comcast.net/~ibladesi/fixfglrx.sh](http://home.comcast.net/~ibladesi/fixfglrx.sh)
 
edit: yeah.. download the script above.. forum code kinda messed up the links..

---

