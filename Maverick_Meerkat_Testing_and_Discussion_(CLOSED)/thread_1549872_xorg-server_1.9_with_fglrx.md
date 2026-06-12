---
title: "xorg-server 1.9 with fglrx"
date: 2010-08-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-08-10
Good news everyone!

Alberto has released and pushed fglrx version 8.780 (which will likely become Catalyst 10.10) with xorg-server 1.9 support.

Everyone thank the man.

[https://launchpad.net/ubuntu/maverick/+source/fglrx-installer/2:8.780-0ubuntu1](https://launchpad.net/ubuntu/maverick/+source/fglrx-installer/2:8.780-0ubuntu1)

And Plun, for pointing out the page on Launchpad! :D


***

OK, here we go again... Just after everything was working great!

At this point fglrx isn't working. Do a purge and delete xorg.conf to get to the desktop.
$ sudo aptitude purge fglrx
$ sudo rm /etc/X11/xorg.conf

***

Quick update for Catalyst 10.9.

10.9 has just been released. Still no ABI v8 support, so same error as with 10.7 and 10.8. :(

Looks like we need 10.10 for 10.10. :D

For those interested, the Arch package page is a very good resource: [http://aur.archlinux.org/packages.php?ID=29111](http://aur.archlinux.org/packages.php?ID=29111)

***

Good news, everyone! We're at the cutting edge. At this point neither Arch or Gentoo have fglrx running on 1.9!

According to Phoronix > ATI's Catalyst driver that is usually months behind in supporting X.Org Server updates should actually work with the 1.9 release at this point however I got errors from fglrx_drv.so after I updated (hence this post may vanish if I find it's my fault).

Here starts my rebooting!

OK, so the error I'm getting is:
undefined symbol: savedScreenInfo

[s]This sounds like it could be multi-monitor related.[/s] More likely this is ABI related.

Experiments to fix: reinstalling packages created from ATi 10.7 installer, removing and installing packages from x-swat, recreating packages using ATi 10.7 installer. Nothing working yet.

Currently downloading a 10.7b OpenCL 1.1 Beta driver to see if it's much newer (released 5th August). Finished downloading, driver version is 8.753.1. Just about to reboot and try it out.

No dice. We're stuck until ATi release drivers compatible with ABI v8. [s]I do wonder, though, what Phoronix were on about when they said the drivers should work...[/s] Phoronix were talking out of their ****, it seems.

---

### Post by pulpo69 on 2010-08-10
i've this ppa or repo installed: 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
i choosed the propietary fglrx driver. all was fine till yesterday
with an kernel update (with the kernel xserver-xorg was removed in later updates it was installed again) nothing worked. boot gets till a violet
screen saying ubuntu and nothing more. choosing the failsafex
in grub i can only get a command line. anyone experienced the same? and how to solve it?

---

### Post by jfernyhough on 2010-08-10
Read the first paragraph of my post and perform the two commands.

The proprietary driver is broken at the moment and won't work again until ATi issue a working version. For now we will have to make do with no 3D acceleration.

---

### Post by rajeev1204 on 2010-08-12
If the driver worked with xserver 1.8 without a patch, what has changed now ?

What is an ABI ?

Also many nvidia users have reported working X with this 

Section "ServerFlags"
    Option         "IgnoreABI" "True"
EndSection

Can we try this ? Its a line the xorg.conf.


rajeev

---

### Post by jfernyhough on 2010-08-12
ABI stands for Application Binary Interface, like an API but at a lower level: [https://secure.wikimedia.org/wikipedia/en/wiki/Application_binary_interface](https://secure.wikimedia.org/wikipedia/en/wiki/Application_binary_interface)

The error with 10.7 is as follows:
```
[    16.818] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.826] dlopen: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so: undefined symbol: savedScreenInfo
[    16.826] (EE) Failed to load /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    16.826] (II) UnloadModule: "fglrx"
[    16.826] (EE) Failed to load module "fglrx" (loader failed, 7)
[    16.826] (EE) No drivers available.
```
Note that the error is an undefined symbol, meaning the driver is trying to set or access something that isn't defined in the ABI (like trying to use an undeclared variable or method).

IgnoreABI simply overrides a check that the ABI version is what is expected by the driver (working around an "ABI mismatch" error) and this is fine unless a symbol is used by the driver that is not defined by the ABI - here the nvidia driver is fine, fglrx is not.

Catalyst drivers are released roughly monthly; we just have to wait on a little while (10.6 was released on 16th June, 10.7 on 28th July). As the drivers are binary blobs there's not a lot else we can do (other than reverting back to xorg-server 1.8 until the new drivers are released!).

---

### Post by yaji on 2010-08-12
Can somebody explain it to me, why every time when new xserver is released, we have to wait for new drivers ? Why the xserver guys are breaking compatibility with proprietary drivers every six months ? Its just crazy to me.  :popcorn:

---

### Post by seanrich on 2010-08-20
So what can we do for now? Can we use Xorg server 1.8?

---

### Post by ELD on 2010-08-20
This early in testing an Alpha version do you really need fancy 3D graphics?

---

### Post by jfernyhough on 2010-08-20
Hmm... it could be that we might not need fglrx for long:

[http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_evergreen_3d&num=1)

> So what can we do for now? Can we use Xorg server 1.8? Yes. But given the date, wait for a little while. I have a feeling Catalyst 10.8 should do the job. :) If not then I'll be sad. :(

---

### Post by andrek on 2010-08-21
> **jfernyhough said:**
> Hmm... it could be that we might not need fglrx for long

Not before they (open source devs) make the power management as good as in fglrx. Crucial thing for laptop users.

---

### Post by yaji on 2010-08-21
Oh and some control panel would be nice too. I like to mess with 3D, video, color and screen settings.

---

### Post by jfernyhough on 2010-08-25
This may be good news. AMDs download pages aren't working; it won't display any results for graphics drivers (for me at least, and that's trying FF, Chromium, and *spit* IE). I'm hoping this is because new ones are being uploaded. :)

--edit
It's here!

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-8-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-8-x86.x86_64.run)

Downloading now. :D

No mention in release notes of any ABI changes or supporting Ubuntu 10.10...

--edit 2
Downloaded, done a --buildpkg, doesn't look promising as there is no x760 in the installer. Also seems that fglrx_drv.so was modified on 11th August which was very close to the time the xorg 1.9 updates came through. Here goes the reboot, anyway. :D

--edit 3
Bah. No change from 10.7. Same error of "undefined symbol: savedScreenInfo"

Disappointed. :(

Hopefully the 10.9 will be a mid-month release?

--edit 4
Thought I might as well send some feedback to the Linux Crew via the download page. :)

---

### Post by agaida on 2010-08-26
A little question? Where is a problem in using 1.8 and the new catalyst? And if all other will fail -  get the sources and patches from the Arch AUR and build and install the xorg-server with make and checkinstall.

---

### Post by jfernyhough on 2010-08-26
There is no problem with using 1.8 - it works fine, either with ATi's drivers or those from the x-swat PPA. We only have a problem with 1.9, so understandably a number of people have gone back to 1.8.

---

### Post by rajeev1204 on 2010-08-26
> **jfernyhough said:**
> There is no problem with using 1.8 - it works fine, either with ATi's drivers or those from the x-swat PPA. We only have a problem with 1.9, so understandably a number of people have gone back to 1.8.


Can you help me with downgrade to x server 1.8 ?


thanks.

---

### Post by ELD on 2010-08-26
Well i would expect new xserver support in 10.11, going by last ubuntu stable release it was 1 or two after i think they supported it.
 
10.8 seems to have OpenGL improvements so it is worth it - Spring RTS units no longer appear all grey.

---

### Post by legoman666 on 2010-09-08
Ive seen this asked several times but no one has bothered to answer. How on earth do you downgrade xserver from 1.9 to 1.8?

---

### Post by helliewm on 2010-09-08
Bump yes how do you downgrade to 1.8?

Helen

---

### Post by andrek on 2010-09-08
You might want to force install the earlier version from [https://launchpad.net/ubuntu/+source/xorg-server/2:1.8.1.902-0ubuntu2/](https://launchpad.net/ubuntu/+source/xorg-server/2:1.8.1.902-0ubuntu2/) (and all the other xorg packages) but I guess it'd be faster to install maverick alpha 3 which has xserver 1.8 by default (and then update the system watching not to update the xserver).

---

### Post by helliewm on 2010-09-08
I am thinking it may be easier to remove fglrx and just have 2d for now.

Helen

---

### Post by andrek on 2010-09-08
Well that's up to you. Removing fglrx isn't an option for me, as a laptop user (power management in the open-source driver still sucks), but if you want - go for it.

---

### Post by helliewm on 2010-09-08
I upgraded from Lucid now can't remove fglrx. It throws up all kinds of errors. Will back up in the morning and do fresh install of Maverick.

For anyone who wants to try to remove fglrx its sudo apt-get remove --purge fglrx.

You will then have the open source drivers and 2d no 3d acceleration for now.  

Also as previous pointed out there are power management issues with laptops with the open source drivers.

Helen

---

### Post by 23dornot23d on 2010-09-08
[COLOR=Red]DO THIS IS ONLY IF YOU DESPERATELY NEED YOUR 3D BACK - 
( I DID and it was the only easy way I could think of doing it )
[/COLOR]
  How I did it ..... to get all my 3D functionality back. 

( especially after seeing that you may need to re-install - is to )

Install a version of Maverick using an older Daily CD ...... anything between generic-6 to generic-14 ........ if you still have a CD that is

When going through the install ..... the bit where it asks which drive it goes on in advanced / custom mode

do everything as normal ..... but without ticking to format the drive that you have your original install of Maverick 2.6.35-20-generic in .

[B]Which I have just done and it works fine for me - 
Is to go back to a earlier -  Ubuntu Daily CD ..... 
[/B]then :-
**Install without ticking to Format the existing Maverick drive you are going to put it onto.**

[COLOR=Blue]Install the Graphics Drivers you need now
[/COLOR]
Afterwards ..... you can update and upgrade everything that you feel you may need - but not the xorg and video drivers .....

i.e. Things that I upgraded the latest kernel aptitude blender wings3d k3dsurf cairo-dock cairo-clock etc , depends what applications you want to use.

If you type these commands ........ into a terminal afterwards ..... 
aptitude update
aptitude safe-upgrade

And then by picking the things that are of use out of the list ...... you can avoid losing your graphics or your Grub ...... 
( I have always done this for Grub common and Grubpc up to just - now I will also include the xorg drivers - just until it gets sorted out )

**I now have my 3D back and all the compiz effects and Cairo Dock** - [ [Screen Shot 2.6.35-20-generic]("http://img530.imageshack.us/img530/3623/screenshot7v.png") ]

We only have a Month Left now and it will be all be sorted anyway .....

---

### Post by legoman666 on 2010-09-08
I don't need 3D so much as I need access to the ATI control panel so I can correct the overscan on my hdtv.

---

### Post by helliewm on 2010-09-09
Thanks for that I am not that worried I upgraded from Lucid and I think before it was an upgrade from Karmic and perhaps an upgrade from previous version too so I am due a new install:p I will just use 2d for now it will be sorted shortly. I did not know about the safe-upgrade thanks for that.

Helen

---

### Post by Devport on 2010-09-15
Is there any estimation when a 1.9 compatible fglrx will be released ?

Even though it is really great that open source drivers already reach 30 fps in my fps games on my poor old card - yet its too slow to play those games.

Well its enough to play SuperTuxKart but OMG I didn`t kill anybody since months !!!

---

### Post by andrek on 2010-09-15
Apparently fglrx **10.9** is going to be released today. Any news on xorg-server 1.9 compatibility?

---

### Post by jfernyhough on 2010-09-15
In the process of downloading now. It's not linked to on the site yet (I love that).

I'll report back shortly. Download still has 15 minutes or so, then I'll need to make a package, install, reboot, probably cry. :)

Oh, I can possibly check the release notes. Hang on.

--edit
No mention of Xorg 7.6 in the release notes, or Ubuntu 10.10. "RHEL 6 Early Look support" but I think that's still on server 1.7. Fedora 13 is 1.8 still so I can't see the enterprise version being newer. :D

Unfortunately it's starting to look like 10.10 will need 10.10. Hang on...

---

### Post by Rafaelcrocha on 2010-09-15
Let's cry together ):P:

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-20-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.GhryRK


lol

---

### Post by andrek on 2010-09-15
Ah, so we'll have to wait another 2-3 weeks I guess. Thanks for the heads up guys.

---

### Post by jfernyhough on 2010-09-15
OK, built and currently installing the generated packages.

Gah, module build failed for my .36-rc4 kernel. I'll have a look at the Arch patch and report back.

--edit
OOOH! OOH! Arch doesn't list xserver<1.9.0 as a requirement any more! Holy crap, this may work!

--edit 2
With patched files it installs and the kernel module builds. OK, here we go.

--edit 3
Bah! Same as before, undefined symbol: savedScreenInfo. Looks like it *is* going to be 10.10 for 10.10. I suppose the symmetry is nice. A little frustrating, though. :)

If anyone is interested, the driver is here: www2.ati.com/drivers/linux/ati-driver-installer-10-9-x86.x86_64.run . It should work with .35 with no issues, you will need to --extract and [patch](http://aur.archlinux.org/packages/catalyst/catalyst/fglrx-2.6.36.patch) to get it working with .36.

---

### Post by Nphyx on 2010-09-16
So I have a burning need to play Starcraft II in Wine under Maverick. After trying a variety of things I ended up compiling and installing xorg-server-1.8.2 from source in order to downgrade from Maverick's 1.9 server, then installed the latest 10.9 catalyst drivers. I'm running kernel 2.6.35-21 right now, and Xorg -version shows server version 1.8.2, but I'm still getting the "undefined symbol" error whenever I attempt to start X using fglrx drivers. Any thoughts? 1.8.2 is running fine under the open-source drivers, but maybe I need to downgrade other packages as well?

---

### Post by ranch hand on 2010-09-16
Or maybe leave the OS the way it is supposed to be and wait for the drivers and wine to catch up.  Should be soon.

Until then run your stable OS for your games.  Surely you have one knowing that 10.10 is not released yet.

---

### Post by ToxicBurn on 2010-09-17
> **yaji said:**
> Can somebody explain it to me, why every time when new xserver is released, we have to wait for new drivers ? Why the xserver guys are breaking compatibility with proprietary drivers every six months ? Its just crazy to me.  :popcorn:

I have asked this for years and i get angry people telling me its ATI's fault for not keeping up.

people love to point fingers

---

### Post by Nphyx on 2010-09-17
> **ranch hand said:**
> Or maybe leave the OS the way it is supposed to be and wait for the drivers and wine to catch up.  Should be soon.

Until then run your stable OS for your games.  Surely you have one knowing that 10.10 is not released yet.

There is no such thing as a "stable release" for my hardware yet, so no I don't have a stable OS :) Maverick is the first to really provide solid support for everything critical, except for issues with fglrx breaking. Lucid hosed me big time with unstable kernel and Xorg and Karmic required compiling a bunch of stuff by hand. And no, I don't run Microsoft junk on any of my machines.

Anyway I fixed the problem by cherry-picking every xorg package for 1.8.2 off launchpad, removing all the current ones, and installing via dpkg. It took several tries and several hours to resolve all the dependencies by hand but I got it figured out. Starcraft won't run fullscreen for some reason but it's playable now so I'm satisfied :)

---

### Post by cariboo on 2010-09-17
> **ToxicBurn said:**
> I have asked this for years and i get angry people telling me its ATI's fault for not keeping up.

people love to point fingers

Just like you're pointing your finger at the Xorg team?

---

### Post by yaji on 2010-09-17
Don't know how about him, but yeah, I am. The drivers works, then *bam* wild xserver appears, and the drivers aren't working anymore. 

Just think about where Microsoft would be now, if their software updates would break graphic drivers twice a year or even often.  :popcorn:

---

### Post by bjwest on 2010-09-17
This it one place where the finger should be pointed at the Xorg team.  They should give ati and nvidia a heads up if they're going to rename or delete a function/class that will break the drivers.  At least a month would be nice.  We're talking about a critical component to a working system here.  Nothing ticks me off more than upgrading and having my video not working any more.  With the kernel it's not so bad because you have both the old and new kernel to choose from when booting and can easily roll back, but with Xorg, you have no choice.  Once you upgrade (often, without knowing it will break the video), you're stuck with a broken system and no easy way to fix it.

---

### Post by cariboo on 2010-09-17
As I stated in another thread the manufacturers are well aware of changes coming in Xorg.

This seems to be more of a problem for ATI/AMD users. I have to wonder why it takes ATI/AMD so long to release a fix/work around, especially as they support far fewer graphics cards than Nvidia.

---

### Post by Nphyx on 2010-09-17
It may help to make fglrx dependent on the specific version of xorg it is known to run on, so that ATI users running fglrx will not get xorg upgrades until a new fglrx release updates dependencies.

---

### Post by laure_f_o on 2010-09-17
hello, I am getting crazy with this, since I upgrade to maverick my graphics does not work. i have the last version of Xorg 1.9, ati 10.9 and kernel .35-22, but:
> [I]Configurando fglrx (2:8.771-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.771 DKMS files...

------------------------------
Deleting module version: 8.771
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.771 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture x86_64
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
dpkg: error al procesar fglrx (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 10
dpkg: problemas de dependencias impiden la configuración de fglrx-amdcccle:
 fglrx-amdcccle depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.
dpkg: error al procesar fglrx-amdcccle (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de fglrx-dev:
 fglrx-dev depende de fglrx; sin embargo:
 El paquete `fglrx' no está configurado todavía.
dpkg: error al procesar fglrx-dev (--configure):
 problemas de dependencias - se deja sin configurar
Procesando disparadores para python-gmenu ...
No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                                                                                                             No se ha escrito ningún informe de Apport porque el mensaje de error indica que es un error proveniente de un fallo anterior.
                                                                                             Rebuilding /usr/share/applications/desktop.es_ES.utf8.cache...
Procesando disparadores para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Procesando disparadores para python-support ...
Se encontraron errores al procesar:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/I]any help, Thanksssssss.

Edit: In ATI web is said the driver is for ePCI but my HD4650 is AGP2...

---

### Post by Claus7 on 2010-09-17
Hello,

> **laure_f_o said:**
> hello, I am getting crazy with this, since I upgrade to maverick my graphics does not work. i have the last version of Xorg 1.9, ati 10.9 and kernel .35-22, but:
any help, Thanksssssss.

Edit: In ATI web is said the driver is for ePCI but my HD4650 is AGP2...

Today I tried to install fglrx to ubuntu 10.10 beta and a message appeared (similar to the above) informing me that maybe a prior installation of nvidia drivers existed. In order for the installation of fglrx to proceed I had to uninstall anything that had to do with nvidia.

Doing so, my system halted, meaning that my screen became totally black and my pc closed. I was informed also that fglrx was not installed since some dependencies were not met.

In order to get my screen back as it was, I had to type via recovery mode terminal:
```
sudo apt-get remove fglrx*
```

Things are ok for now without any problems. Just a remark: every time I dropped to a terminal and typed startx in order to bring my Desktop back the system was closing.

From this humble experience I would suggest not tampering at the moment with fglrx, at least not before the final version of maverick is out.

Regards!

---

### Post by jfernyhough on 2010-09-17
Three of the first four lines of the thread:
> At this point fglrx isn't working. Do a purge and delete xorg.conf to get to the desktop.
$ sudo aptitude purge fglrx
$ sudo rm /etc/X11/xorg.confI tried to make it easy...

---

### Post by workage on 2010-09-17
Same issue here, I even added the x-org experimental ppa and used their FGLRX package, I just get a console... so I ran aticonfig --initial. No change at reboot, so uninstalled fglrx and deleted xorg.conf, it didn't make a backup so I let it re-create. Back in business but wish I could use the latest video driver. Haven't attempted sudo sh ./atiinstaller yet however.

---

### Post by andrek on 2010-09-18
FGLRX doesn't work with xorg-server 1.9 so far. Just wait for a new driver release.

---

### Post by sanjeevchs on 2010-09-19
...sorry not working...

---

### Post by kal11 on 2010-09-20
> **sanjeevchs said:**
> ...sorry not working...

:-k

if you are working.

just try it

pd: sorry for my bad English.

---

### Post by ermin on 2010-09-20
I am also eagerly awaiting fglrx for xorg-server 1.9. The reason being that my laptop runs really hot when using open-source drivers. It even overheats (forced shutdown due to heat) quite often. Battery is not an issue for me. 

Recently however I have come over [http://wiki.archlinux.org/index.php/ATI#Powersaving]("this article here"). It describes how to turn on powersaving with the open-source drivers. I am still evaluating how good the settings proposed in the article work. Maybe they could help some of you.

---

### Post by forcecore on 2010-09-20
Is this rumor or true that somehow power profile can be changed with opensource driver in 2.6.35 manually by editing some config file??? i saw it somewhere.

---

### Post by ermin on 2010-09-20
> **forcecore said:**
> Is this rumor or true that somehow power profile can be changed with opensource driver in 2.6.35 manually by editing some config file??? i saw it somewhere.

I am pretty sure that is explained in the link in my earlier post.

---

### Post by forcecore on 2010-09-20
Then 10.10 should lower out of box profile to "mid" at least for preventing burns on Radeon cards. Most people who keep open driver will only use internet and watch movies, serious gamers install always closed official driver anyway...

---

### Post by xir_ on 2010-09-21
> **forcecore said:**
> Then 10.10 should lower out of box profile to "mid" at least for preventing burns on Radeon cards. Most people who keep open driver will only use internet and watch movies, serious gamers install always closed official driver anyway...

I agree with the content of your statement, but I would like to point out the open drivers are as official as the closed ones because they are made by AMD too.

---

### Post by John Dias on 2010-09-22
I find the fix at this tread:
[Follow me]("http://ubuntuforums.org/showthread.php?t=1576383")

Thanks for [Captain Giraffe's]("http://ubuntuforums.org/member.php?u=521914"), post #6.
Thanks for [chronaden]("http://ubuntuforums.org/member.php?u=1071673"), post #7.

This work for me:

1-Edit the file "/var/lib/dkms/fglrx/8.771/source/kcl_ioctl.c"
```
sudo vi /var/lib/dkms/fglrx/8.771/source/kcl_ioctl.c
```

2- Replace in 196 line:
```
return compat_alloc_user_space(size);
```
with this:
```
return KCL_IOCTL_AllocUserSpace32(size);
```

3- Rebuild the packages:
```
sudo dpkg-reconfigure fglrx
sudo dpkg-reconfigure fglrx-amdcccle
```

4- You may need this:
```
sudo aticonfig --initial
```
Done. Hope work for you!

---

### Post by smoosh on 2010-09-22
This thread is about xserver 1.9, but the thread with the solution you mentioned  only talks about lucid and maverick beta, neither one of which use xserver 1.9, so it's still not going to work for this application.

---

### Post by ranch hand on 2010-09-22
> **smoosh said:**
> This thread is about xserver 1.9, but the thread with the solution you mentioned  only talks about lucid and maverick beta, neither one of which use xserver 1.9, so it's still not going to work for this application.
Really?  I wonder how it got installed (about a month ago) on my Mangy Moose.

---

### Post by smoosh on 2010-09-22
Did you use duct tape??

---

### Post by smoosh on 2010-09-22
No really, does this actually work with xserver 1.9? I would love it too, but I tried, believe you me I tried...

---

### Post by ktp on 2010-09-23
> **ranch hand said:**
> Really?  I wonder how it got installed (about a month ago) on my Mangy Moose.

it must have snuck in when you weren't looking. =)

---

### Post by plun on 2010-09-23
Good news maybe......  ( I am on nVidia)

> fglrx-installer (2:8.780-0ubuntu1) maverick; urgency=low

  * New upstream release.
    - Fix build issues with kernel fix for CVE-2010-3081 (LP: #642518).
    - Add compatibility with 2.6.35 kernels (LP: #573748).
    - Add compatibility with xserver 1.9 (LP: #630599).
  * Make the driver Depend on the appropriate xserver-xorg-video-$ABI
    (LP: #616215).

[https://launchpad.net/ubuntu/maverick/+source/fglrx-installer/2:8.780-0ubuntu1](https://launchpad.net/ubuntu/maverick/+source/fglrx-installer/2:8.780-0ubuntu1)


---

### Post by smoosh on 2010-09-23
Worked for me! Thanks!

---

### Post by bardic on 2010-09-23
forgive my noobishness, but how would I go about installing the update plun posted?

---

### Post by plun on 2010-09-23
> **bardic said:**
> forgive my noobishness, but how would I go about installing the update plun posted?

Menu System > Administration > Additional drivers


If something goes wrong remove the driver from a terminal.

$ sudo aptitude purge fglrx
$ sudo rm /etc/X11/xorg.conf

---

### Post by cariboo on 2010-09-23
It should show up in the repositories when you do an update.

---

### Post by bardic on 2010-09-23
happy day! Thanks guys ^^

---

### Post by jfernyhough on 2010-09-23
Yup, it's there and I'm downloading the update right now. (16 minutes left? Bah...)

(Op edited)

---

### Post by plun on 2010-09-23
> **cariboo907 said:**
> It should show up in the repositories when you do an update.

No the driver must be installed and activated from Additional drivers....

This is the first driver which should work.

---

### Post by gfarmerfr on 2010-09-23
works for me too : HD4870 + xorg 1.9 + last kernel

---

### Post by jfernyhough on 2010-09-23
Ah, pants. Works fine with kernel .35, build fails with .36-rc5. Grr.

---

### Post by plun on 2010-09-23
Jockey aka "Additional drivers" must also be updated

> 
jockey (0.5.10-0ubuntu4) maverick; urgency=low

  * data/handlers/fglrx.py, nvidia.py:
    - **Re-enable fglrx now that it's compatible with xserver 1.9.**
    - Make sure that the initramfs is updated for both the newest kernel
      and for the current kernel, so as to be consistent with the default
      behaviour of the DKMS template that both driver packages use.

[https://lists.ubuntu.com/archives/maverick-changes/2010-September/008118.html](https://lists.ubuntu.com/archives/maverick-changes/2010-September/008118.html)

Available from update-manager....  (at least "Main")

---

### Post by superhick on 2010-09-23
for some reason I don't see any updates yet. Should I remove edgers PPA?

---

### Post by superhick on 2010-09-23
> **superhick said:**
> for some reason I don't see any updates yet. Should I remove edgers PPA?

I enabled "Main" repository server, and it showed up

---

### Post by jfernyhough on 2010-09-23
Hah! Take that! Patched it so it will build with .36! Thanks to the people at Arch (as always) for [this patch](http://aur.archlinux.org/packages/catalyst/catalyst/fglrx-2.6.36.patch) and Alexander Advoshin for his patch here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890/comments/3](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890/comments/3)

Once you've installed fglrx (and DKMS fails) copy the two files I've attached to /usr/src/fglrx-8.780/ then do a reinstall of fglrx. All this should do is trigger a DKMS build.

--edit
Bug reported for kernel 2.6.36: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/646237](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/646237)

---

### Post by superhick on 2010-09-23
Ok. It works, however, Xorg eats CPU (when I run glxgears for example, it jumps to 98% CPU usage). Framerate is 10x higher though. 
I did reconfigure X, but no bananas.
Any pointers to figure out why CPU usage is so high?

```
glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 3650
GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
```

---

### Post by djchandler on 2010-09-23
The new fglrx driver is now available through the regular repository channel. Jockey found and updated my driver (from xorg-radeon) today. This is the first day (that I know of) it has been available for the "point and click" user. Now for my "acid" test--watching streaming video. And everything is a lot cooler now too. The heat issue still seems to plague the xorg-radeon driver

Yay, and thanks to all who worked to make the fglrx proprietary driver compatible with xorg 1.9.

---

### Post by ermin on 2010-09-23
> **djchandler said:**
> And everything is a lot cooler now too. The heat issue still seems to plague the xorg-radeon driver.

By setting some power options for the open-source driver I have nearly the same temperature as with the new ati drivers. Diff about 5 degrees. 

The open-source drivers are definitely catching up.


PS: The power options for the open-source drivers can be found in one of my posts in this thread.

---

### Post by superhick on 2010-09-23
With compiz enabled, CPU usage is between 2 and 10%, which is ok I think

---

### Post by djchandler on 2010-09-23
> **ermin said:**
> By setting some power options for the open-source driver I have nearly the same temperature as with the new ati drivers. Diff about 5 degrees. 

The open-source drivers are definitely catching up.


PS: The power options for the open-source drivers can be found in one of my posts in this thread.

Now that I can run fglrx with Xorg Server 1.9, I have to agree that the heat issues seem to be about the same now regardless of whether using the OS radeon driver or proprietary fglrx. For low end GPUs, framerate is still a problem for the OS driver compared to fglrx.

---

### Post by yaji on 2010-09-23
Gaussian blur is working:


[[IMG]http://img522.imageshack.us/img522/4176/obszarroboczy1001.th.jpg[/IMG]](http://img522.imageshack.us/i/obszarroboczy1001.jpg/)

All glory to ATI.

---

### Post by jfernyhough on 2010-09-23
Hmm. You have crappy colour gradation on your desktop too. The output to my DVI monitor is fine, but it's really crappy on my laptop's internal panel.

---

### Post by thezood on 2010-09-23
> **jfernyhough said:**
> Hah! Take that! Patched it so it will build with .36! Thanks to the people at Arch (as always) for [this patch](http://aur.archlinux.org/packages/catalyst/catalyst/fglrx-2.6.36.patch) and Alexander Advoshin for his patch here: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890/comments/3](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890/comments/3)

Once you've installed fglrx (and DKMS fails) copy the two files I've attached to /usr/src/fglrx-8.780/ then do a reinstall of fglrx. All this should do is trigger a DKMS build.

--edit
Bug reported for kernel 2.6.36: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/646237](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/646237)

Hi, 

This doesn't work for me using 64bit maverick. Any idea what I'm doing wrong? Same error message while installing: 

```

Building only for 2.6.35-22-generic
Building for architecture x86_64
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)

```

make.log:

```

DKMS make.log for fglrx-8.723.1 for kernel 2.6.35-22-generic (x86_64)
tor 23 sep 2010 22.44.05 CEST
AMD kernel module generator version 2.1
cat: /lib/modules/2.6.35-22-generic/build/include/linux/utsrelease.h: No such file or directory
Error:
kernel includes at /lib/modules/2.6.35-22-generic/build/include do not match current kernel.
they are versioned as ""
instead of "2.6.35-22-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```

It's not really critical for me. I read the proprietary driver has better power management, otherwise the open source driver has been perfectly sufficient for me but if possible it would be cool to get it working.

---

### Post by Yurebis on 2010-09-23
Damn, maverick is ready to go with this fixed now.

---

### Post by ranch hand on 2010-09-23
Too bad it still does not support my card.  Nothing available.  Had to edit my menu to get the Additional Drivers back on my menu.

Always take it off as there has never been anything.  As of 9.04 there is, or was, a driver for my card on the ATI site.  Have not looked.  FOSS drivers work MUCH better on 9.04, 9.10 and 10.04.  Can't boot 10.04 at all with the ATI driver.  The others are kind of entertaining for about 10 minutes with the psychodelic effects.

Not going to bother checking it on this one.

---

### Post by jfernyhough on 2010-09-24
> **thezood said:**
> Hi, 

This doesn't work for me using 64bit maverick. Any idea what I'm doing wrong? Same error message while installing: 

make.log:

```

DKMS make.log for fglrx-8.723.1 for kernel 2.6.35-22-generic (x86_64)

```
You've still got the old version installed. Do a purge then try again.

---

### Post by meborc on 2010-09-24
it works

10.10 64-bit 

01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]

using NOT the edgers PPA, only the vanilla 10.10 repos... point and click and I have 3D :D

the problem now is that I was messing around with ATI catalyst control center and enabled xinerama... which is not very good... but now every time I click on ATI catalyst control center in the menu, I get logged out of gnome :S

any ideas how to reset the catalyst settings to "factory"? whih conf file should I delete?

EDIT: problem solved... removed xorg.conf... then removed drivers from jockey... then added them again :D now have working 3d on 2 monitors

---

### Post by hp400 on 2010-09-24
I'm afraid it does not work on my system. I'm on 32bit kubuntu maverick. 
I downloaded fglrx yesterday and it installed fine. After a reboot "Additional Drivers" reported it as being in use.
But kde desktop effects were disabled and compositing type was set to Xrenden. It was not possible to switch to OpenGL.
After deinstalling fglrx kde was working fine again - with desktop effects and openGl

---

### Post by Devport on 2010-09-24
> **hp400 said:**
> I'm afraid it does not work on my system. I'm on 32bit kubuntu maverick. 
I downloaded fglrx yesterday and it installed fine. After a reboot "Additional Drivers" reported it as being in use.
But kde desktop effects were disabled and compositing type was set to Xrenden. It was not possible to switch to OpenGL.
After deinstalling fglrx kde was working fine again - with desktop effects and openGl
I think this could be a problem of the combination of KDE 4.5 and fglrx :

[http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/](http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/)

---

### Post by plun on 2010-09-24
New update including kernel 2.6.36 fix

> fglrx-installer (2:8.780-0ubuntu2) maverick; urgency=low

  * debian/fglrx.postinst:
    - Call dpkg-trigger with "--by-package".
  * Add add-compatibility-with-2.6.36-kernels.patch:
    - Fix build issues with 2.6.36 kernels.
  * Add use-cflags_module-together-with-modflags.patch:
    - Fix build issues with kernels that don't have
      MODFLAGS and use CFLAGS_MODULE.

[https://lists.ubuntu.com/archives/maverick-changes/2010-September/008190.html](https://lists.ubuntu.com/archives/maverick-changes/2010-September/008190.html)



---

### Post by bjwest on 2010-09-24
Driver works well on Kubuntu 10.10beta, however I can't get flash video sites to go full screen.  Disabling hardware encoding makes no difference.

---

### Post by Asmodai on 2010-09-25
There still seem to be problems.
Since the build problems are fixed, I decided to try and install fglrx.
After a reboot the boot screen is low-res, so I guess fglrx is being loaded correctly.
However, desktop effects got disabled and the following outputs speak for themselves:

```
david@david-desktop:~$ glxinfo
name of display: :0.0
Segmentation fault (core dumped)
david@david-desktop:~$ glxgears
Segmentation fault (core dumped)
```

Any idea what's wrong now?

---

### Post by rapiertg on 2010-09-25
Since my lcd do not have EDID i had allways issues with out of sync after installing fglrx. Addind modes to xorg usually helped. This time the driver acts as it didnt see anything in xorg, and uses his own resolutions.

Tried disabling RandR12 in both xorg.conf and amdpcsdb, but its allways enabled during boot like it didnt see config files.

Any idea whats wrong?

---

### Post by ZardoZ84 on 2010-09-25
> **hp400 said:**
> I'm afraid it does not work on my system. I'm on 32bit kubuntu maverick. 
I downloaded fglrx yesterday and it installed fine. After a reboot "Additional Drivers" reported it as being in use.
But kde desktop effects were disabled and compositing type was set to Xrenden. It was not possible to switch to OpenGL.
After deinstalling fglrx kde was working fine again - with desktop effects and openGl

Me too, in 64 bits. I check wich dmesg and fglrx it's working. glxgears give a better framerate,and KDE wich composition works. But I can't get composition activated wich fglrxxxxx or opensource driver

I put glxinfo here, I think that fglrx it's only working wich opengl 1.4 and KDe now need Opengl 2.0, not ???

> 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions: ....

client glx vendor string: ATI
client glx version string: 1.4
client glx extensions: ....

GLX version: 1.4
GLX extensions: ....

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 3.3.10237 Compatibility Profile Context
OpenGL shading language version string: 3.30
OpenGL extensions: ....



---

### Post by yaji on 2010-09-25
Guys, have you tried running some games using Wine ? Im asking because all I get is bunch of artifacts: 

[[IMG]http://img836.imageshack.us/img836/3958/realtimehdribl001.th.png[/IMG]](http://img836.imageshack.us/i/realtimehdribl001.png/)

Oh, and I don't have Radeon 9500 but 4850. Something is clearly not right.

---

### Post by hp400 on 2010-09-25
Desktop effects are now working on my system. The steps to get there were the following:
1)sudo aticonfig --initial               # This one created /etc/X11/xorg.conf
2)purge ~/.kde/share/config/kwinrc
3)Restart X
4)System Settings -> Desktop Effects
       > Set compositing type to OpenGL
       > Enable Desktop effects


State is now:
All effects are in place (blur!, ..) fglx external driver is in use (jockey says so), catalyst control center is working,
fglrxinfo says this(was crashing before):
   display: :0.0  screen: 0
   OpenGL vendor string: ATI Technologies Inc.
   OpenGL renderer string: ATI Radeon 3100 Graphics
   OpenGL version string: 3.3.10237 Compatibility Profile Context

So it seems as if everything is in good working order, BUT: Graphics performance is poor! e g. When playing a video (small resolution) Xorg takes 80% of cpu, kwin takes 20%. It looks like as if there were very little jumps between the individual frames. Sometimes these jumps are big. When using the the desktop (moving windows, animated minimize) this also looks very rough.


@yaji: I tried some .exe apps in wine, these worked fine. wing commander did not start. wing commander in dosbox had  normal graphics but suffered from overall graphics performance.

---

### Post by hp400 on 2010-09-25
I've been investigating the bad video performance a bit. If glxgears is the only application window on the screen, I get a framerate of about 60. When I start another application, the framerate drops. The larger I make the other window, the less framerate I get. When I overlap the other window with the glxgears window, framerate drastically drops to 25!
And this without any activity in the other window! I was trying this with "System Settings" and konsole.

---

### Post by bjwest on 2010-09-25
> **hp400 said:**
> Desktop effects are now working on my system. The steps to get there were the following:
1)sudo aticonfig --initial               # This one created /etc/X11/xorg.conf
2)purge ~/.kde/share/config/kwinrc
3)Restart X
4)System Settings -> Desktop Effects
       > Set compositing type to OpenGL
       > Enable Desktop effects



Thanks for this hp400.  This also fixed my problem with not being able to go full screen on sites using flash video.

---

### Post by hp400 on 2010-09-26
Got smoother operation by disabling the Blur filter. Now Framerate is very high. Xorg and kwin still eating up cpu (80% + 20%), but is not noticable when doing normal work.  On the kde forums both blur and lanczos filter are made responsible for slowing down the system.
This is the blacklist howto:

[http://blog.martin-graesslin.com/blog/2010/07/blacklisting-drivers-for-some-kwin-effects/](http://blog.martin-graesslin.com/blog/2010/07/blacklisting-drivers-for-some-kwin-effects/)

---

### Post by mathew.chacko on 2010-09-27
Supper happy to see 3D working.

> 
:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon HD 5000 Series
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, 


There are jerks and glitches while moving the window with normal and extra in Appearance - Visual Effects settings. Hoping it will smoothen out with the final release.

Thank you the team very much.

---

### Post by hp400 on 2010-10-09
I got this one sortet out, too. I had the "Show FPS" effect enabled to display kwins performance. As a result Xorg and kwin used 98% of my cpu. After disabling "Show FPS"
cpu usage dropped below 5%. So everything is fine on my system from now, I guess. :smile:

---

