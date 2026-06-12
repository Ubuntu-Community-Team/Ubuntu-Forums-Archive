---
title: "fglrx with kernel 2.6.37"
date: 2010-11-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-11-07
** Updated for fglrx-installer 8.801 **

Alberto Milone has just uploaded fglrx to the natty build queue.
[https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.801-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.801-0ubuntu1)

** Updated for Catalyst 10.12 **

No official support for kernels >= 2.6.36, but according to Arch the patches are the same. Steps below will work until x-swat is updated, attached files are updated for 10.12

** Manual patching instructions updated for Catalyst 10.12, fglrx 8.801 **

Another [s]kernel[/s] driver, another fglrx breakage. Nice!

However, this time round all the hard work has been done as there's already a patch out here: [http://www.cosmicencounter.net/mirror/patch/sema_init.patch](http://www.cosmicencounter.net/mirror/patch/sema_init.patch)

Credit for the patches as always to Arch and Gentoo. This process is mine, though!

**In summary:**
1) Download and extract [10.12]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-12-x86.x86_64.run") from [AMD]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx").
2) Apply [2.6.36]("http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/fglrx-2.6.36.patch") patch
3) Apply [sema_init]("http://www.cosmicencounter.net/mirror/patch/sema_init.patch") patch
4) Apply [makefile]("http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/makefile_compat.patch") patch
5) Build packages
6) Install

**Details:**
1) Once downloaded:
$ chmod +x ati-driver-installer-10-12-x86.x86_64.run
$ ./ati-driver-installer-10-12-x86.x86_64.run --extract [name of directory e.g. ~/temp/ati]

This will extract the files so we can patch and build manually.

2) You need to apply the patch from [here]("http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/fglrx-2.6.36.patch"). Find the relevant sections in [extracted files dir]/common/lib/modules/fglrx/build_mod/firegl_public.c and add in those from the patch. Or, use the attached pre-patched version of firegl-public.c, just replace the old version.

3) Apply the patch from [here]("http://www.cosmicencounter.net/mirror/patch/sema_init.patch") to firegl_public.c (again, the attached version is already done).

4) The makefile in common/lib/modules/fglrx/build_mod/2.6.x needs to be patched with [this]("http://aur.archlinux.org/packages/catalyst-generator/catalyst-generator/makefile_compat.patch"). A pre-patched version is attached.

5) In the folder you extracted the files (let's call it ~/temp/ati/) run:
$ ./ati-installer.sh 8.801 --buildpkg Ubuntu/natty

This will place packages in ~/temp/

6) In ~/temp/ (or wherever you put the files):
$ sudo dpkg -i *.deb

If you haven't already got an xorg.conf you will need to run:
$ sudo aticonfig --initial
and reboot. 

All should be well again!

(Bug report for 10.10 is here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/672127](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/672127))

---

### Post by alphacrucis2 on 2010-11-07
Great stuff. Thanks.

---

### Post by reynaldo666 on 2010-11-15
Hi,
I need help, please.
I followed your instructions: 

reynaldo@cerbero:~/Documentos/Builds$ ./ati-driver-installer-10-10-x86.x86_64.run --extract fglrx-10-10
Creating directory fglrx-10-10
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.783................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

reynaldo@cerbero:~/Documentos/Builds$ cd fglrx-10-10/


But I'm getting that error:

reynaldo@cerbero:~/Documentos/Builds/fglrx-10-10$ patch -p0 < ../fglrx-2.6.36.patch 
patching file work/common/lib/modules/fglrx/build_mod/firegl_public.c
Hunk #1 FAILED at 320.
Hunk #2 FAILED at 407.
2 out of 2 hunks FAILED -- saving rejects to file work/common/lib/modules/fglrx/build_mod/firegl_public.c.rej

What's wrong?

---

### Post by jfernyhough on 2010-11-15
The clue is here:> patching file work/common/lib/modules/fglrx/build_mod/firegl_public.cThe file is in common/lib/modules/fglrx/build_mod/, so you will have to edit the patch a little; remember these are for Arch, not for Ubuntu. Alternatively, just use the attached files.

---

### Post by jfernyhough on 2010-11-17
A fixed package was released today! Hopefully it will work. ;)

---

### Post by jfernyhough on 2010-11-17
Catalyst 10.11 was released today. No Ubuntu package yet but the patches needed are exactly the same as for 10.10 so it's fairly easy to get them installed. Updated first post.

---

### Post by jfernyhough on 2010-11-17
Package released via x-swat PPA. Use this.

There also seems to be an issue with 2.6.37-5; on my laptop this won't allow X to start no matter the driver in use (aticonfig'ed xorg.conf or no xorg.conf). 37-4 works fine, however.

---

### Post by reynaldo666 on 2010-11-18
Hi jfernyhough,
I was trying to build it on kernel 2.6.37 backported to lucid following your procedure, but I don't know if it would work.
Do you have any idea?
Thanks!

---

### Post by dinoman1989 on 2010-11-30
fixed it for me for lucid on kernel 2.6.32-26 as well :)  you're a hero.

---

### Post by alur on 2010-12-13
Thank you very much :)
By the way, this still works (and is very much required) with 10.12.

---

### Post by rajeev1204 on 2010-12-13
.................

---

### Post by HX_unbanned on 2010-12-15
So, does this Fglrx patching must be done with Kernel 2.6.36-1, Ubuntu 10.10 32bit and currently installed fglrx v8.780 ( Catalyst 10.10 ), too ?

I have not been able to update my Catalyst drivers since upgrading to Maverick. When I tried to install Catalyst 10.11, Ubuntu just crashed because of failed DKMS config. With Catalyst 10.12, I cannot upgrade because of installation errors.

Please, provide necessary steps to finally be able to run my Ubuntu PC with Kernel 2.6.36 and Catalyst 10.12 ... these updates are vital because I use dual-monitor heavy-production environment ...

---

### Post by jfernyhough on 2010-12-15
> **HX_unbanned said:**
> So, does this Fglrx patching must be done with Kernel 2.6.36-1, Ubuntu 10.10 32bit and currently installed fglrx v8.780 ( Catalyst 10.10 ), too ?No. If you had read the first line of the first post you would know to use the X-Swat PPA: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

> Please, provide necessary steps to finally be able to run my Ubuntu PC with Kernel 2.6.36 and Catalyst 10.12 ... these updates are vital because I use dual-monitor heavy-production environment ...The instructions are the same. Just replace all instances of 10.11 with 10.12. Or just use the X-Swat PPA, it's far easier.

If you had searched the forums you should also have found my old thread about 2.6.36, but as this is the development section (i.e. for Natty, what will become Ubuntu 11.04) I'm not interested in old kernels.

--edit
OK, fine, I'll update my first post and try building 10.12.

---

### Post by HX_unbanned on 2010-12-16
Anyway -

Now the sentence - "Merry X-mas !!!" has actually meaning with Catalyst 10.12 release :)

... no appropriate associations with abriavature "NY" though ... :(

Hopefully we will be able to use them on our Maverick /w 2.6.36 kernel ..

---

### Post by Tweedle on 2010-12-16
I truely have my fingers crossed for natty to FINALY make my ATI Xpress 200M usable. I'm not sure if I need this patch, but if the control panel continues to tell me that I don't have an ATI piece of hardware, and I can't figure it out in the end, I'm gonna cry. I've been trying everything I can find on the issue, but not a single thing has worked correctly. I've got an ATI IXP400 chipset with an Xpress 200 (could be 200M. I've even seen it called a 200G, but it's older Compaq desktop) it uses an MSI 7184 mobo (the msi website doesnt even list this thing) and nothing seems to work correctly on it. Maybe I just need to set it on fire and steal a new box, cause I'm broke as dirt and I want something useful. If you guys have any tips, please let me know. I'm going to install the Alt-i386 of natty now, and I'll post back how it goes. thanks.

---

### Post by cariboo on 2010-12-16
I have a Dell branded MSI motherboard that has the same graphics chipset, I could never get it took work properly either in Windows or Ubuntu. I found an inexpensive Nvidia 8400GS for it and haven't had a problem since.

---

### Post by Yellow Pasque on 2010-12-16
> **Tweedle said:**
> I truely have my fingers crossed for natty to FINALY make my ATI Xpress 200M usable. I'm not sure if I need this patch, but if the control panel continues to tell me that I don't have an ATI piece of hardware..
This patch is for the proprietary ATI (Catalyst) driver, which hasn't supported your card in almost 2 years.

> and I can't figure it out in the end, I'm gonna cry.
Tissue?

---

### Post by HX_unbanned on 2010-12-17
> **Temüjin said:**
> This patch is for the proprietary ATI (Catalyst) driver, which hasn't supported your card in almost 2 years.

Tissue?

I don't think it will help. There is job for mommy and daddy ... ;)

--

[@jfernyhough]("http://ubuntuforums.org/member.php?u=143103"), do you got any update of time when compiled driver may arrive in x-swat ppa ?

---

### Post by rajeev1204 on 2010-12-17
The ATI Xpress 200 works flawless with the open source driver. I had one some time ago. There is no need to install any additional drivers and on top of that you get a pretty high res boot which is not possible in the fglrx driver.

---

### Post by jfernyhough on 2010-12-17
> **HX_unbanned said:**
> do you got any update of time when compiled driver may arrive in x-swat ppa ?It generally takes a week or so for it to be patched and built. Robert Hooker ([https://launchpad.net/~sarvatt](https://launchpad.net/~sarvatt)) is the one to watch on this.

--edit
OK, files updated for 10.12. Looks to be installing fine, will try a reboot in a little while.

--edit2
It's all good. Gaussian blur looks a bit better too, not as much window shadow left in the wrong places. :D

--edit 3
Allowing Mipmaps in Static Window Switcher still makes the desktop freeze, however. Bah.

---

### Post by HX_unbanned on 2010-12-18
> **jfernyhough said:**
> It generally takes a week or so for it to be patched and built. Robert Hooker ([https://launchpad.net/~sarvatt]("https://launchpad.net/%7Esarvatt")) is the one to watch on this.

--edit
OK, files updated for 10.12. Looks to be installing fine, will try a reboot in a little while.

--edit2
It's all good. Gaussian blur looks a bit better too, not as much window shadow left in the wrong places. :D

--edit 3
Allowing Mipmaps in Static Window Switcher still makes the desktop freeze, however. Bah.

Hmm, I see ... week for building is when LP is not overloaded with package queue, huh? :D

@edit2 - Oh, Well, I am on edge with Compiz 0.9.2.1, so I cannot test Extras ... but, well, shadows and still some frustrating issues with Reflections is what I truly expect to be fixed :)

What's about (Adobe) Flash issue in browsers ( FF 3.6 ) when running Quake Live type content? Have you tried it? :popcorn:

---

### Post by ITCompozer on 2010-12-28
It doesn't work for me with kernel 37 rc 2

---

### Post by jfernyhough on 2010-12-28
Why are you still using rc2? rc7 has been out for the last week; both mainline build and the Ubuntu kernel are based on this.

I suspect, however, you are doing it wrong.

If you could provide a little more information rather than "it doesn't work" that would be helpful (e.g. your graphics card, the version of Catalyst you are using, or whether you are using x-swat, error messages or a description of what is failing, e.g. the build process or the X failure message, etc. etc. etc.)

--edit

rc8 has just been released. Waiting for a build.

---

### Post by rajeev1204 on 2010-12-29
Iam using the driver from hardware drivers and it works just fine .This patch has long been applied to the official driver from the repos though its still an old catalyst version.I think 10.11.Thanks to patch submitted by the OP .

Using the PPA will provide 10.12 catalyst. 

Btw, unity does not work with the proprietary driver for many, is it working for you guys?

---

### Post by Yellow Pasque on 2010-12-29
^No Unity/ATI for me so Unity is not living up to its name.

---

### Post by screaminj3sus on 2011-01-01
> **Temüjin said:**
> ^No Unity/ATI for me so Unity is not living up to its name.

ATI drivers never work properly during ubunu dev cycles, unity or no unity...They usually only work a bit after the final is released, but the last few releases ati has provided pre-release drivers for Canonical to include in the repositories.

---

### Post by LinuxMaster9 on 2011-01-02
I am running ubuntu 10.10 x64 and have a Radeon HD 5850. I installed the Jockey Driver offered and it works fine until I step away for a while and it goes to black then freezes. it also freezes my computer if I run a couple of things or a youtube video. Basically it randomly freezes my PC. I havent tried the instructions listed up top yet as I was following the ATI wiki installation instructions for Maverick and managed to screw my Xorg up and had to reinstall. Any suggestions? I love playing Penumbra and Amnesia. I'm unsure what my kernel is as I just ran the update and it updated the kernel so what ever the latest release under stable.

---

### Post by anders_c_ on 2011-01-02
> **LinuxMaster9 said:**
> I am running ubuntu 10.10 x64 and have a Radeon HD 5850. I installed the Jockey Driver offered and it works fine until I step away for a while and it goes to black then freezes. it also freezes my computer if I run a couple of things or a youtube video. Basically it randomly freezes my PC. I havent tried the instructions listed up top yet as I was following the ATI wiki installation instructions for Maverick and managed to screw my Xorg up and had to reinstall. Any suggestions? I love playing Penumbra and Amnesia. I'm unsure what my kernel is as I just ran the update and it updated the kernel so what ever the latest release under stable.
If you are running 10.10 then you don't have the .37 kernel even if you have updated, to check what kernel you are running type "uname -r" in a terminal. This thread is for people running the testing version of the upcoming 11.04 release.
Unless i misunderstood you and you did an upgrade from maverick to natty?

---

### Post by LinuxMaster9 on 2011-01-02
> **anders_c_ said:**
> If you are running 10.10 then you don't have the .37 kernel even if you have updated, to check what kernel you are running type "uname -r" in a terminal. This thread is for people running the testing version of the upcoming 11.04 release.
Unless i misunderstood you and you did an upgrade from maverick to natty?

I'm sorry, I was just looking for a solution to my issue and saw the thread after doing a search. I did not realize it was for Natty. Where should I go then for the solution? I created my own thread but no one has responded with answers. Put it this way, I have just installed 10.10 x64 and ran the updates. That is as far as I have gotten. Any suggestions?

---

### Post by cariboo on 2011-01-02
Have you tried the latest drivers from ATI/AMD?

---

### Post by LinuxMaster9 on 2011-01-02
That's just it, I don't know... what driver does Jockey currently use? I tried the download instructions from AMD for 10.12 but it jacked up Xorg as aticonfig did not exist after install.

---

### Post by LinuxMaster9 on 2011-01-02
uname -r

2.6.35-24-generic

---

### Post by cariboo on 2011-01-02
I personally refuse to use ATI/AMD graphics cards, I've used up all my knowledge about them. :)

---

### Post by jfernyhough on 2011-01-03
Alberto Milone has just uploaded fglrx to the natty build queue.
[https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.801-0ubuntu1](https://launchpad.net/ubuntu/natty/+source/fglrx-installer/2:8.801-0ubuntu1)

---

### Post by jfernyhough on 2011-01-03
> **LinuxMaster9 said:**
> Any suggestions?Add the x-swat PPA to your system, and update the drivers. They have the latest AMD drivers backported to Maverick (10.10).

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Run:

$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

then update your software sources (e.g. use synaptic). The update should be picked up; if not, do a search for fglrx in synaptic and mark it for installation. Everything else should "just work".

---

### Post by LinuxMaster9 on 2011-01-03
Ok thanks. So Should I avoid using Jockey? Cause I have yet to figure out why my computer will just freeze especially when it goes into like sleep or screensaver mode. I think it has to do with the Jockey drivers but I don't know. Im almost tempted to get an Nvidia card but I can't afford one for what i do.

---

### Post by andrek on 2011-01-03
Don't use Jockey. Apply the X-Swat PPA, then install fglrx and do "sudo aticonfig --initial" and then just reboot. Everything should go fine.

---

### Post by LinuxMaster9 on 2011-01-03
Ok. Thank you for all your help everyone! ^_^ I was running my self nuts wondering why I couldn't get my PC to stop freezing randomly. I'm going to be test Natty when it reaches Beta Stage. Question, can i use Gnome 3 or do I have to use Unity? I want Gnome 3.

---

### Post by cariboo on 2011-01-03
I'm using gnome 3 from the[ gnome 3 build ppa]("https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds"), it's pretty stable until you add gnome shell from the [ricotz testing ppa]("https://launchpad.net/~ricotz/+archive/testing"), then it seems to crash if you look at it sideways. :)

---

### Post by LinuxMaster9 on 2011-01-03
um....I get "aticonfig command not found"  What now?

---

### Post by andrek on 2011-01-04
Are you sure you have added the x-swat ppa, updated the sources (sudo apt-get update) and then installed fglrx and fglrx-amdcccle?
By the way. The proper version of fglrx just got into 'default' Ubuntu restricted repository. Just make sure to successfully install the fglrx and fglrx-amdcccle packages.

---

### Post by Harry33 on 2011-01-04
> **cariboo907 said:**
> I'm using gnome 3 from the[ gnome 3 build ppa]("https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds"), it's pretty stable until you add gnome shell from the [ricotz testing ppa]("https://launchpad.net/~ricotz/+archive/testing"), then it seems to crash if you look at it sideways. :)

Why not the newer Gnome3 Team:
[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

---

### Post by jfernyhough on 2011-01-04
Please please keep this thread about fglrx. :)

*goes to add gnome3 ppa*

---

### Post by HX_unbanned on 2011-03-12
Any chance to see AMD Catalyst 11.3 built in X Updates PPA ??? \\:D/

---

### Post by Yellow Pasque on 2011-03-12
It's in beta status ATM, which is not open to general public. Distributing it would violate AMD's terms.

---

### Post by HX_unbanned on 2011-03-12
> **Temüjin said:**
> It's in beta status ATM, which is not open to general public. Distributing it would violate AMD's terms.

Yes, it is, but I meant it as question if stable will be available for maverick ( with 2.6.37 / 2.6.38 kernel ) users within ppa. Sorry for confusion.

It is very imporrtant because fglrx may be cause various bugs with DisPlex 0.7.1 and Adobe Flash 10.2 in FF 3.6.15 ( and maybe FF 4 ) in my current Maverick 32bit installation ...

---

### Post by Claus7 on 2011-04-10
Hello,

> **HX_unbanned said:**
> Any chance to see AMD Catalyst 11.3 built in X Updates PPA ??? \\:D/

I would like to see 11.3 as well in my maverick box and I think this is the safest way of upgrading without messing things a lot. Since 11.3 is just only a couple of days out I think that we have to wait a little.

> **HX_unbanned said:**
> Yes, it is, but I meant it as question if stable will be available for maverick ( with 2.6.37 / 2.6.38 kernel ) users within ppa. Sorry for confusion.

It is very imporrtant because fglrx may be cause various bugs with DisPlex 0.7.1 and Adobe Flash 10.2 in FF 3.6.15 ( and maybe FF 4 ) in my current Maverick 32bit installation ...

This link about firefox and flash might help you, which urges you to install Flash-Aid. 
[http://ubuntuforums.org/showpost.php?p=10001177&postcount=12](http://ubuntuforums.org/showpost.php?p=10001177&postcount=12)
At least it worked for me.

Regards!

---

### Post by alphacrucis2 on 2011-04-10
> **Claus7 said:**
> Hello,



I would like to see 11.3 as well in my maverick box and I think this is the safest way of upgrading without messing things a lot. Since 11.3 is just only a couple of days out I think that we have to wait a little.

Just download Cat 11.3 from AMD. It's perfectly safe to install it in 10.10 via the buildpkg method as per the binary driver howto. I install their (AMD's) catalyst update every month.

---

