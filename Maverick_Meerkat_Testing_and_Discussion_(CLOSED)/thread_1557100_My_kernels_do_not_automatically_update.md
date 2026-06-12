---
title: "My kernels do not automatically update"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-08-20
A few weeks ago, I had a severe problem with 2.6.35-11 (system would not boot), so I reverted to rev 10. I used aptitude to remove rev 11. The next day, rev 12 was released, but aptitude did not offer to upgrade to it, so I manually installed it with aptitude. It booted just fine, as has every other revision since then (I am now on rev 16).

But also ever since then, it will not upgrade my kernels automatically (i.e., by doing update, then safe-upgrade). For revisions 12 through 16, I have had to manually install the newer kernels and headers. I assume I broke something in the safe-upgrade process when I removed the defective (for me) rev 11.

Can anyone explain to me how to fix this? Thanks.

Tim

---

### Post by MacUntu on 2010-08-20
Do you have the packages linux, linux-image, and linux-image-generic installed?

---

### Post by ratcheer on 2010-08-20
> **MacUntu said:**
> Do you have the packages linux, linux-image, and linux-image-generic installed?

linux-generic and linux-image-generic are installed. linux and linux-image are not installed.

So, if I manually install those last two packages, should everything then be ok?

Thanks,
Tim

---

### Post by ranch hand on 2010-08-20
It would hurt nothing and I believe that it would straighten the problem out.

---

### Post by ratcheer on 2010-08-20
> **ranch hand said:**
> It would hurt nothing and I believe that it would straighten the problem out.

Thanks. I installed the two missing packages (see above) and rebooted. On the first attempt to start Maverick, it gave me a bunch of error messages (white text on black screen) and stopped. A second attempt came up, but I got an "!" in a jagged icon at the top right panel. When I clicked it, it told me it had detected "serious kernel errors".

I rebooted again and everything now appears to be ok. I am hoping that when it upgrades to 2.6.35.17 all of this will be straightened out. I saw in the Maverick change logs that that kernel was released, but aptitude has not yet detected it, for me.

Running "aptitude search 2.6.35-17" shows that the upgrades are now available, so adding those packages did not fix my problem.

Tim

---

### Post by ratcheer on 2010-08-20
```

tim@tim-desktop:~$ aptitude show linux-headers-generic linux-image-generic linux-generic linux linux-headers
Package: linux-headers-generic           
State: not installed
Version: 2.6.35.16.17
Priority: optional
Section: devel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-headers-2.6.35-16-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers available.

Package: linux-image-generic
State: installed
Automatically installed: no
Version: 2.6.35.16.17
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image-2.6.35-16-generic, linux-firmware
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image available.

Package: linux-generic
State: installed
Automatically installed: no
Version: 2.6.35.16.17
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image-generic (= 2.6.35.16.17)
Description: Complete Generic Linux kernel
 This package will always depend on the latest complete generic Linux kernel available.

Package: linux
State: installed
Automatically installed: no
Version: 2.6.35.16.17
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image (= 2.6.35.16.17)
Provided by: type-handling
Description: Generic complete Linux kernel.
 This package will always depend on the latest generic complete Linux kernel available.

No current or candidate version found for linux-headers
Package: linux-headers
State: not a real package
Provided by: linux-headers-2.6.35-14, linux-headers-2.6.35-14-generic, linux-headers-2.6.35-14-generic-pae,
             linux-headers-2.6.35-14-virtual, linux-headers-2.6.35-15, linux-headers-2.6.35-15-generic,
             linux-headers-2.6.35-15-generic-pae, linux-headers-2.6.35-15-virtual, linux-headers-2.6.35-16,
             linux-headers-2.6.35-16-generic, linux-headers-2.6.35-16-generic-pae, linux-headers-2.6.35-16-virtual,
             linux-headers-2.6.35-17, linux-headers-2.6.35-17-generic, linux-headers-2.6.35-17-generic-pae,
             linux-headers-2.6.35-17-virtual


```

Tim

---

### Post by ratcheer on 2010-08-20
I just installed linux-headers-generic. Somehow, I missed it when I attempted to install all the packages recommended by MacUntu.
```

Package: linux-headers-generic           
State: installed
Automatically installed: no
Version: 2.6.35.16.17
Priority: optional
Section: devel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-headers-2.6.35-16-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers available.

```

Tim

---

### Post by ratcheer on 2010-08-20
aptitude update and safe-upgrade still do not detect the new kernel release 2.6.35-17.

Tim

---

### Post by ranch hand on 2010-08-20
I do not know what repo you are using but I am not finding anything to do with ...17 except linux-doc.

---

### Post by cariboo on 2010-08-20
I'm just doing updates, I'm getting the 2.6.35-16 generic kernel. I see under **New in repository** in synaptic that there is 2.6.35-17 waiting for depends to catch up.

---

### Post by MacUntu on 2010-08-20
The -16 kernel had a bad bug, so the -17 is on its way, but it's not yet in the repos (at least not all bits and pieces).

---

### Post by dino99 on 2010-08-20
> **MacUntu said:**
> The -16 kernel had a bad bug, so the -17 is on its way, but it's not yet in the repos (at least not all bits and pieces).

get installed here (headers & image only at time))

---

### Post by ratcheer on 2010-08-20
> **MacUntu said:**
> The -16 kernel had a bad bug, so the -17 is on its way, but it's not yet in the repos (at least not all bits and pieces).

Ok, thanks. I'll wait a while longer and try again.

Tim

---

### Post by seeker5528 on 2010-08-20
> **ratcheer said:**
> But also ever since then, it will not upgrade my kernels automatically (i.e., by doing update, then safe-upgrade). For revisions 12 through 16, I have had to manually install the newer kernels and headers. I assume I broke something in the safe-upgrade process when I removed the defective (for me) rev 11.

The way the dependencies go linux-image is a metapackage depending on linux-image-generic and linux-image-generic is a metapackage that depends on the actual kernel package linux-image-*series*-*abi*-generic. The series and ABI numbers are part of the package name, so whenever one or both of them change it's a new package as opposed to incrementing the package version number and keeping the same name, which would usually be the case if the ABI didn't change.

If you do the safe upgrade with apt (apt-get upgrade) or do a safe upgrade in Synaptic by having 'settings --> preferences --> general --> system upgrade' set to 'default upgrade' you won't get any upgrades that cause new packages to be pulled in.

It seems from previous discussions that 'aptitude safe-upgrade' may install things that won't get installed when using the safe options in apt or synaptic and installing a new kernel when the kernel metapackages point to one could be one of those things, but it may not be one of those things, so using 'safe-upgrade' could be what is causing it not to pull in the newer kernels.

When I updated today the metapackages depend on the ABI 16 kernel packages even though there were ABI 17 packages available, which is a different kind of thing since the Ubuntu devs have to update the linux-image-generic metapackage to depend on the newer kernel every time the ABI changes, which is not automatic.

Later, Seeker

---

### Post by ratcheer on 2010-08-20
> **ratcheer said:**
> Ok, thanks. I'll wait a while longer and try again.

Tim

Awesome, everything is working correctly again! I just did an update and safe-upgrade and all the meta-packages and real packages were updated to 2.6.35.17.18.

Thanks very much. 

Tim

---

### Post by ratcheer on 2010-08-20
But, I got the ! icon again, and once again, it reports that "Your system has encountered a serious kernel problem." Other than the warning, everything seems to be working just fine.

WTF?

Tim

---

### Post by MacUntu on 2010-08-20
I'm not using apport, maybe it's re-reportin already happened oopses? Look in /var/crash and delete every -16 kernel related crash files.

---

### Post by ratcheer on 2010-08-20
> **MacUntu said:**
> I'm not using apport, maybe it's re-reportin already happened oopses? Look in /var/crash and delete every -16 kernel related crash files.

Done. Every kernoops file there was related to linux-image-2.6.35-16-generic.

Thanks again. You seem to know this stuff inside and out.

Tim

---

### Post by MacUntu on 2010-08-20
> **ratcheer said:**
> You seem to know this stuff inside and out.

I'm glad I don't (as seeker5528 proved :D). :lolflag:

---

### Post by ratcheer on 2010-08-24
I think I have gotten myself back into the same situation, again. :( I have successfully upgraded to 2.6.35-18 kernel and headers, but the metapackages linux-generic, linux-image-generic, and linux-hearers-generic are still at 2.6.35-17. Why won't the metapackages keep up? What am I doing wrong?

I have even tried "aptitude safe-upgrade linux-generic linux-image-generic linux-headers-generic", but that command finds nothing to upgrade. Are they releasing the actual packages before the metapackages are available?

Tim

---

### Post by xebian on 2010-08-24
> **ratcheer said:**
> I think I have gotten myself back into the same situation, again. :( I have successfully upgraded to 2.6.35-18 kernel and headers, but the metapackages linux-generic, linux-image-generic, and linux-hearers-generic are still at 2.6.35-17. Why won't the metapackages keep up? What am I doing wrong?

I have even tried "aptitude safe-upgrade linux-generic linux-image-generic linux-headers-generic", but that command finds nothing to upgrade. Are they releasing the actual packages before the metapackages are available?

Tim

Guess what happens if you update the meta-package and the actual package is not there?

---

### Post by ratcheer on 2010-08-24
> **xebian said:**
> Guess what happens if you update the meta-package and the actual package is not there?

I give up. What?

Tim

---

### Post by ranch hand on 2010-08-24
You really should start using apt to get your update/upgrades.  There is no sign, as of this morning of another kernel.

I am going to run update/upgrade for this evening in a while.  There may be something there and listed in the update.  If it is not all there for the upgrade it will not be installed, even by a "dist-upgrade".  There is really no call to due these self inflicted problem.

Please believe me.  I am REALLY good at doing self inflicted problems.  Could probably get some kind of reward for it.  This is one even I have avoided (so far).

---

### Post by ranch hand on 2010-08-24
It actually appears to be ready now, some others are not.
```

root@sam-desktop:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.35-18 linux-headers-2.6.35-18-generic linux-image-2.6.35-18-generic
The following packages have been kept back:
  computer-janitor computer-janitor-gtk gnome-control-center libgnome-window-settings1 mono-runtime
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 0 to remove and 5 not upgraded.
Need to get 45.1MB of archives.
After this operation, 229MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by ratcheer on 2010-08-24
Thanks, ranch hand. I am having enough trouble understanding aptitude. Right now, I really don't feel like learning another way to do it. Maybe later.

What are advantages of apt-get over aptitude? And vice versa?

Tim

---

### Post by ranch hand on 2010-08-24
Well, while I subscribed to the bug objecting to the removal of aptitude from default installation, it has never blown my skirt up.  So I am not the right person to ask about its advantages over apt.

All I can say is that apt does not install things that are not ready.  That is not to say that it has never installed something on a testing OS that would break the OS.  Just that all the parts of the package(s) were there.

We are in testing after all and things will break.  I just like a system that keeps this to a minimum.  Apt works best for me.

---

### Post by Longinus00 on 2010-08-25
> **ratcheer said:**
> Thanks, ranch hand. I am having enough trouble understanding aptitude. Right now, I really don't feel like learning another way to do it. Maybe later.

What are advantages of apt-get over aptitude? And vice versa?

Tim

There is no reason to use apt over aptitude if you're just running it via command line actions, aptitude is a frontend to apt so in that aspect they are the same thing.

ratcheer, next time just leave the kernel and change the default in grub.

---

### Post by VinDSL on 2010-08-25
> **ratcheer said:**
> Thanks, ranch hand. I am having enough trouble understanding aptitude. Right now, I really don't feel like learning another way to do it. Maybe later.[...]I'm an Aptitude fanboui, but...

Truthfully (and it pains me to say this) I've had NOTHING but trouble with Aptitude on 10.10!

Update Manager, apt-get and (gulp) Synaptic seem to be the way to go, for now.

My biggest biatch with Aptitude (in 10.10) is, it keeps trying to reinstall old kernels over the freshly installed ones.  

I'm at a total loss to explain this.  I've removed the old packages every which way to Sunday, but Aptitude refuses to play ball!

So, my recommendation -- until things get sorted out -- is to use Update Manager, apt-get, and you-know-what...  ;)

---

### Post by ratcheer on 2010-08-25
> **VinDSL said:**
> I'm an Aptitude fanboui, but...

Truthfully (and it pains me to say this) I've had NOTHING but trouble with Aptitude on 10.10!

Update Manager, apt-get and (gulp) Synaptic seem to be the way to go, for now.

My biggest biatch with Aptitude (in 10.10) is, it keeps trying to reinstall old kernels over the freshly installed ones.  

I'm at a total loss to explain this.  I've removed the old packages every which way to Sunday, but Aptitude refuses to play ball!

So, my recommendation -- until things get sorted out -- is to use Update Manager, apt-get, and you-know-what...  ;)

I am not having that problem. Use purge to get rid of the old kernels and I don't think they would come back.

I really think my problem is that I am subscribed to the Maverick changes mail list, so I find out when a new kernel is released and go searching for it. When aptitude finds it, I install it. And, I think I am doing it before the associated metapackages have been released. I just need to learn to cool my jets for a day or so.

Last night, after ranch hand said he had gotten the new kernel and metapackages with apt-get, I tried again with aptitude and they installed without a hitch. From now on, I intend to wait longer and install after the metapackages are available.

Tim

---

### Post by ratcheer on 2010-08-25
2.6.35-19 is being released today, but I am promising myself not to update until the metapackages are available.

NEW QUESTION: I do not have linux-backports-modules installed. Is it generally advisable to always do so? What exactly are these? Is there a metapackage for them, too?

Thanks,
Tim

---

### Post by jerrylamos on 2010-08-25
> **ranch hand said:**
> It actually appears to be ready now, some others are not.
```

.....
  linux-headers-2.6.35-18 linux-headers-2.6.35-18-generic linux-image-2.6.35-18-generic
.....

```

?  Ranch Hand, I've been doing updates every day, sudo apt-get update and sudo apt-get dist-upgrade.

Synaptic says 2.6.35-15 is installed, but I don't know where.  Last one in /boot is 2.6.35-14.  Update-grub only finds -14, not -15.

So where did you get 2.6.35-18?  In Repositories "Updates", do you have pre-released updates checked?  What about unsupported updates?  Do you have ppa.launchpad.net checked in "Other Software"?

Thanks, Jerry

---

### Post by cariboo on 2010-08-25
2.6.35-18.24 came in  yesterday doing regular updates, do you have linux-image-generic installed?

---

### Post by jerrylamos on 2010-08-25
> **cariboo907 said:**
> 2.6.35-18.24 came in  yesterday doing regular updates, do you have linux-image-generic installed?

Cariboo907, Synaptic says linux-image-generic 2.6.35.14.15 is installed. Most recent linux image in /boot is vmlinuz-2.6.35-14-generic dated 08-02 in spite of doing many sudo apt-get update and sudo apt-get dist-upgrades since.

Do I have to have ppa selected?  proposed updates selected?  unsupported updates selected?

Should I re-install linux-image-generic?

Thanks, Jerry

---

### Post by ranch hand on 2010-08-25
Why not go to synaptic and try installing the newest kernel in there?

---

### Post by cariboo on 2010-08-25
+1 that's the best idea. I don't think any of us are using kernels from a ppa, just the normal upgrades. I just upgraded to 2.6.35-19 a couple of minutes ago.

---

### Post by jerrylamos on 2010-08-25
> **ranch hand said:**
> Why not go to synaptic and try installing the newest kernel in there?

Just did a reload.  Synaptic says linux-image-2.6.35-14.19 is installed already.  If I do uname -a I get:

Linux linux 2.6.35-14-generic #19-Ubuntu SMP Mon Aug 2 01:43:35 UTC 2010 i686 GNU/Linux

Notice date is Aug 2 2010 pretty old.  What's in /boot is 
vmlinuz-2.6.35-14-generic

?  There are reports in the threads of linux updates since Aug 2 ?

Thanks, Jerry

---

### Post by ranch hand on 2010-08-25
> **jerrylamos said:**
> Just did a reload.  Synaptic says linux-image-2.6.35-14.19 is installed already.  If I do uname -a I get:

Linux linux 2.6.35-14-generic #19-Ubuntu SMP Mon Aug 2 01:43:35 UTC 2010 i686 GNU/Linux

Notice date is Aug 2 2010 pretty old.  What's in /boot is 
vmlinuz-2.6.35-14-generic

?  There are reports in the threads of linux updates since Aug 2 ?

Thanks, Jerry
Sounds to me like you need to run;
```

sudo update-grub

```
and then;
```

sudo grub-mkconfig

```
That last will give you the contents of the /boot/grub/grub.cfg file.

See if under the section "10_linux" what kernels are listed.

The newest one should be at the top.

This;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet
        initrd /initrd.img
}
EOF

```
added to your /etc/grub.d/40_custom file, edited to match your partition, should boot you to the newest kernel on that partition.

You would need to run update-grub of coarse.

---

### Post by arpanaut on 2010-08-25
If you have more than one install going, you may need to boot into your primary boot OS, say Lucid and run update-grub from there.  I have multiple drives and I control my primary boot drive from Lucid, my test drives I install grub to the mbr of my secondary drive.  Thus when, say maverick updated the kernel, in order for the new kernel to boot I must update-grub from the controlling grub on primary=Lucid.

Make sense?  Maybe that is not the case for you, but for some reason your updated kernels are not being seen by grub.  Just a possible solution.

---

### Post by VinDSL on 2010-08-25
> **arpanaut said:**
> If you have more than one install going, you may need to boot into your primary boot OS, say Lucid and run update-grub from there.[...]Yep!  That's what I do...

[LIST]
[*]Update 10.10
[*]Restart into 10.04
[*]Update Grub in 10.04
[*]Restart into 10.10
[/LIST]

I go a little further than *ranch hand*.

When I'm in 10.04, I totally remove Grub, and rebuild it from scratch -- but that's just me.

I get rather neurotic, when it comes to Grub, especially when 2 different distros are playing with it...  ;)

---

### Post by ranch hand on 2010-08-25
> **VinDSL said:**
> Yep!  That's what I do...

[LIST]
[*]Update 10.10
[*]Restart into 10.04
[*]Update Grub in 10.04
[*]Restart into 10.10
[/LIST]

I go a little further than *ranch hand*.

When I'm in 10.04, I totally remove Grub, and rebuild it from scratch -- but that's just me.

I get rather neurotic, when it comes to Grub, especially when 2 different distros are playing with it...  ;)
If you are removing grub from Lounge Lizard, why not grab a deb package from one of your Mangy Moose installs /var/cache/apt/archives and install that on 10.04.  Better grub version that 10.04 has.

---

### Post by VinDSL on 2010-08-26
> **ranch hand said:**
> If you are removing grub from Lounge Lizard, why not grab a deb package from one of your Mangy Moose installs /var/cache/apt/archives and install that on 10.04.  Better grub version that 10.04 has.Hey, now there's an idea!

I was just looking at grub-pc and grub-common debs, in the archives.

The time stamps inside the 10.04 grub-common deb are 1-AUG-2010.

The time stamps inside the 10.10 grub-common deb are 25-SEP-2010.  LoL!

Dittos for grub-pc...

Um... Have you done this, or would I be the guinea pig?!?!?  :)

---

### Post by VinDSL on 2010-08-26
Wanna hear a funny one?

The other day, I uninstalled Grub2 (on 10.04) and installed vintage Grub.

When I rebooted, I checked the Grub entries.

I didn't know you could chainload Grub2 from vintage Grub!?!?!

Anyway, that was too wierd for me, so I went back to Grub2 on both distros, before everything got jacked up.

---

### Post by jerrylamos on 2010-08-26
Ranch Hand & Cariboo, thanks.  Mirror problem.  I've been using the mirror at North Eastern University for the last couple years since it's the fastest one from here.  No problem through the last several Alpha's & Beta's & various proposed fixes until this month.  They must be on summer vacation.

Switched to the U.S. Archive and linux 19 came in fine.

Yay!  Jerry

---

### Post by ranch hand on 2010-08-26
> **VinDSL said:**
> Hey, now there's an idea!

I was just looking at grub-pc and grub-common debs, in the archives.

The time stamps inside the 10.04 grub-common deb are 1-AUG-2010.

The time stamps inside the 10.10 grub-common deb are 25-SEP-2010.  LoL!

Dittos for grub-pc...

Um... Have you done this, or would I be the guinea pig?!?!?  :)
The newest grub works fine on 9.10, let alone 10.04.  I have not tried it on a 9.04 install but it would probably work there, the one that 9.10 has as default does.

---

### Post by VinDSL on 2010-08-26
> **ranch hand said:**
> The newest grub works fine on 9.10, let alone 10.04.[...]Good deal!  I'll try it.

I haven't used 10.04 for anything (except messing with Grub) since installing 10.10.

Same thing happened when I installed 10.04.  9.10 just sat there, for months, taking up space.

The thing is... I don't want to invoke Murphy's Law!  ;)

---

### Post by ktp on 2010-08-26
> **VinDSL said:**
> The thing is... I don't want to invoke Murphy's Law!  ;)

you really don't want to mess with that law. :lolflag:

---

