---
title: "install 8.42.3 on RS482 [ ATI Radeon Xpress 200] on a fresh install Ubuntu 7.10 Gutsy"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by basilebasilic on 2007-10-25
Hello,

On my desktop HP Compaq model dc5750 Small Form Factor AMD 64bits Athlon with a _**RS482 [ ATI Radeon Xpress 200]**_, I have successfully install the latest driver ati radeon 8.42.3!

And, I use Compiz_fuzion without problem for the moment. See the screenshot (first image attachement at the end of the post)

I have follow several sources :

[http://ubuntuforums.org/showthread.php?t=575843&highlight=ATI+Radeon+Xpress+1150](http://ubuntuforums.org/showthread.php?t=575843&highlight=ATI+Radeon+Xpress+1150)
[http://ubuntuforums.org/showthread.php?p=3616047](http://ubuntuforums.org/showthread.php?p=3616047)
[http://forum.ubuntu-fr.org/viewtopic.php?id=158516](http://forum.ubuntu-fr.org/viewtopic.php?id=158516)
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.42.3_Driver_Manually)

**1.Step**
[INDENT] install a new fresh Ubuntu 7.10 Gutsy
 config apt
 config synaptic
 install update system
 reboot[/INDENT]

**2.Step**
[INDENT] _**DON'T INSTALL the ATI proprietary drivers from menu (System-Admin)**_ [/INDENT]

**3.Step**
[INDENT]Grab the new driver 8.42.3 from here in your home directory : [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)
And for AMD64bits user like me : dowload this patch package in your home directory : [http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2](http://www.michaellarabel.com/downloads/fglrx-8.42-ubuntu+debian-2.tar.bz2)[/INDENT]

**4.Step**
[INDENT]Open a terminal
!/home/basile : basile it's the name of my user replace by yours.

```

sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-generic

cd /etc
sudo mkdir ati
cd ati
sudo mkdir custom-package
cd custom-package/

sudo cp /home/basile/fglrx-8.42-ubuntu+debian-2.tar.bz2 .
sudo tar xvfj fglrx-8.42-ubuntu+debian-2.tar.bz2

cd packages/Ubuntu/
sudo cp -R * /etc/ati/custom-package

cd /home/basile
chmod +x ati-driver-installer-8.42.3-x86.x86_64.run
sudo ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg custom-package/7.10

```

You should have this :

> 
basile@basile-ubu-desktop:~$ sudo ./ati-driver-installer-8.42.3-x86.x86_64.run --buildpkg custom-package/7.10
Created directory fglrx-install.OX8102
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.42.3....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: custom-package/7.10
Package /home/basile/xorg-driver-fglrx_8.42.3-1_amd64.deb has been successfully generated
Package /home/basile/xorg-driver-fglrx-dev_8.42.3-1_amd64.deb has been successfully generated
Package /home/basile/fglrx-kernel-source_8.42.3-1_amd64.deb has been successfully generated
Package /home/basile/fglrx-amdcccle_8.42.3-1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.OX8102

[/INDENT]

**5.Step**
[INDENT]
In the "linux-restricted-modules-common" file change DISABLED_MODULES="" to DISABLED_MODULES="fglrx" then save and close.
```
gksu gedit /etc/default/linux-restricted-modules-common
```
[/INDENT]

**6.Step**
[INDENT]```
sudo dpkg -i fglrx-kernel-source_8.42.3-1_amd64.deb 
sudo dpkg -i xorg-driver-fglrx_8.42.3-1_amd64.deb
sudo dpkg -i fglrx-amdcccle_8.42.3-1_amd64.deb

sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel
sudo depmod -a
sudo rm -f /usr/src/fglrx-kernel*.deb
```

_IMPORTANT: You have to recompile the kernel module after each kernel update!_ 
[/INDENT]

**7.Step**
[INDENT]This step for me, make nothing see result why :

```
sudo mkdir /lib/modules/$(uname -r)/volatile
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists

sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
ln: creating symbolic link `/lib/modules/2.6.22-14-generic/volatile/fglrx.ko' to `/lib/modules/2.6.22-14-generic/misc/fglrx.ko': File exists

```
[/INDENT]

**8.Step**
[INDENT]Reboot[/INDENT]

**9.Step**
[INDENT]```
sudo aticonfig --initial --force
sudo aticonfig --overlay-type=Xv
```[/INDENT]

**10.Step**
[INDENT]At this step, I don't yet OpenGL vendor ATI :

> basile@basile-ubu-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

basile@basile-ubu-desktop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
basile@basile-ubu-desktop:~$ [/INDENT]

**11.Step**
[INDENT]**_[COLOR="Red"]The step :[/COLOR]_**
```
sudo depmod -a
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
```[/INDENT]

**12.Step**
[INDENT]
Reboot
And for me it was completed.
After Reboot, you have in the tray area an icon that you announced you use proprietary driver and if you double click on it you should have the box see the second image attachment at the end of the post.
[/INDENT]

**13.Step**
[INDENT]So, at this step you have the new driver ati 8.42.3, how verify :

> basile@basile-ubu-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: **[COLOR="Red"]ATI Radeon Xpress Series[/COLOR]**
OpenGL version string: [COLOR="Red"]**2.0.6958 Release**[/COLOR]

basile@basile-ubu-desktop:~$ glxinfo | grep direct
**[COLOR="Red"]direct rendering: Yes[/COLOR]**
basile@basile-ubu-desktop:~$ [/INDENT]

**14.Step**
[INDENT]Install compiz_fusion manager
```
sudo apt-get install compizconfig-settings-manager
```[/INDENT]

**15.Step**
[INDENT]In :
```
sudo gedit /etc/X11/xorg.conf
```
change 
> Section "Extensions"
        Option          "Composite"     "0"
EndSection
to
> Section "Extensions"
        Option          "Composite"     "1"
EndSection

Under Section _"ServerLayout", add this_:

> Option "AIGLX" "True"[/INDENT]


**16.Step**
[INDENT]Permit fglrx to launch compiz effect 
```
sudo gedit /usr/bin/compiz
```

Search WHITELIST=".....nvidia...intel etc... " and add fglrx before nvidia!
like this :
> 
# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"[/INDENT]

**17.Step**
[INDENT]Reboot[/INDENT]

**18.Step**
[INDENT]Now, you can use compiz effect :
In the menu System - Preference - Apparence - Visual effect - Custom
View the first image attachement screenshot[/INDENT]

So, for me I use it from 2 hours now, it's ok, it's the same with glx perhaps better with the new driver ati 8.42.3.

---

### Post by Shin_Gouki2501 on 2007-10-25
i know its greats and such that u got it working
But for me its just seems as torture.
"Just" to install a GFX driver so many steps *_*
this can be the right way to do it ...

---

### Post by basilebasilic on 2007-10-25
For the moment, it's hard, I know...

But, when this driver will be available by synaptic or by proprietary drivers manager it should be easier :)) I hope with 2 clicks or 2 cmd it will be done :))

---

### Post by hrvooje on 2007-10-25
it works on my barton 2500+ with ati x1650 and gutsy! :) ( barton is 32-bit so i looked [----->>here also<<---]("http://forlong.blogage.de/"))

thanks man!

---

### Post by VCSkier on 2007-10-25
Are we to expect this to be available through Synaptic or Restricted Driver Manager soon?  Or will this have to be done via a 3rd party, like Envy?  If it will require the usage of Envy, has tseliot given any indication as to when Envy will support the new driver?

---

### Post by Raphaeld on 2007-10-25
Hi,

What do you mean by:

Config apt
config synaptic

Do you refer to the lines in step 4:

"sudo apt-get update
sudo apt-get install" ....?

Many Thanks
RaphaelD

---

### Post by Toadmund on 2007-10-25
I went through the steps, ATI driver fglrxinfo says I'm using ATI.

And 'direct rendering' YES!

But when I go to enable compiz by selecting 'extra' or 'custom' the GUI flickers and says this:
'Desktop effects could not be enabled'

Any clues?

---

### Post by Melcar on 2007-10-25
> **Toadmund said:**
> I went through the steps, ATI driver fglrxinfo says I'm using ATI.

And 'direct rendering' YES!

But when I go to enable compiz by selecting 'extra' or 'custom' the GUI flickers and says this:
'Desktop effects could not be enabled'

Any clues?


Make sure your video card is not blacklisted in the file /usr/bin/compiz

---

### Post by basilebasilic on 2007-10-26
Hi,

I juste mean after you have finished install  Gutsy,  you config your apt-get (sourcelist) and synaptic application. There isn't direct link with the topic, it's just to sure that you have check main, universe, multiverse, restricted repository.

> **Raphaeld said:**
> Hi,

What do you mean by:

Config apt
config synaptic

Do you refer to the lines in step 4:

"sudo apt-get update
sudo apt-get install" ....?

Many Thanks
RaphaelD

---

### Post by basilebasilic on 2007-10-26
Hi,

If you correctly follow steps from 14 I don't why doesn't work   :(. Try to repeat from step 14 perhaps.

But it's a good thing if your ATI driver fglrxinfov it's correctly install.

> **Toadmund said:**
> I went through the steps, ATI driver fglrxinfo says I'm using ATI.

And 'direct rendering' YES!

But when I go to enable compiz by selecting 'extra' or 'custom' the GUI flickers and says this:
'Desktop effects could not be enabled'

Any clues?

---

### Post by jpittack on 2007-10-26
> sudo cp -R * /etc/ati/custom-package

Is the * to be replaced by something?

> john@ubuntu:/etc/custom-package/packages/Ubuntu$ sudo cp -R * /etc/ati/custom-package
cp: target `/etc/ati/custom-package' is not a directory


I am not using a fresh install, just trying to get the process down.  I am still unfamiliar with using a terminal and want to go through everything once before I take the time to reinstall.

---

### Post by basilebasilic on 2007-10-26
No replace. Juste type the same command.

> **jpittack said:**
> Is the * to be replaced by something?

I am not using a fresh install, just trying to get the process down.  I am still unfamiliar with using a terminal and want to go through everything once before I take the time to reinstall.

john@ubuntu:/etc/custom-package/packages/Ubuntu$ sudo cp -R * /etc/ati/custom-package
cp: target `/etc/ati/custom-package' is not a directory 

You have forget to create the "ati" directory.

/etc/custom-package/  -> /etc/ati/custom-package/

---

### Post by Toadmund on 2007-10-26
> **Melcar said:**
> Make sure your video card is not blacklisted in the file /usr/bin/compiz

You mean in here:

sudo gedit /usr/bin/compiz
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```
Mine is the rs480, is it blacklisted?
Does '#" mean ignore?

---

### Post by RavanH on 2007-10-26
> **Toadmund said:**
> You mean in here:

sudo gedit /usr/bin/compiz
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```
Mine is the rs480, is it blacklisted?
Does '#" mean ignore?

My Radeon Xpress 200M turned out to be in that blacklist somewhere. No clue which one so what I did was simply change the line
```
BLACKLIST_PCIIDS="$T"
```
to
```
BLACKLIST_PCIIDS=""
```
thereby disabling the blacklist altogether. Don't think it will be a problem as long as I do not change my graphics card. And that is unlikely to happen, because I am on a laptop and the M stands for integrated with the motherboard or was it mobility ;) well... anyways, it works!

Excellent write-up/how-to! Maybe with some blacklist instructions added, it would be perfect :)

---

### Post by RavanH on 2007-10-26
Oh... and I also found that adding ```
	Option 		"TexturedVideo" "on"

``` to the ServerLayout in xorg.conf improved performance on my machine dramatically!

---

### Post by Melcar on 2007-10-26
> **Toadmund said:**
> You mean in here:

sudo gedit /usr/bin/compiz
```
# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T
```
Mine is the rs480, is it blacklisted?
Does '#" mean ignore?

Just put a # in front of the T.  

#T="   1002:5954 1002:5854 1002:5955" # ati rs480

I could not enable the desktop effects until I did that (even after adding fglrx to the driver whitelist).

---

### Post by masry4life on 2007-10-28
Great HOW-TO!
The only problem with me is that now the internet won't work.

I've reformatted everything and installed Ubuntu again, but after I use this to install the ati driver my internet stops working.

I think it might be from rebuilding the kernel.  I have no idea what I'm doing so please help.
If there's a simpler solution like a way to return to a previous network configuration before I rebuilt the kernel when it was working that would be great.

Thanks for the help

---

### Post by drama1981 on 2007-11-08
ill try this. hope fully it finally works

---

### Post by shriek on 2007-11-09
anyone know the best way for me to revert back to XGL solution? I just can't stand the black video in totem, black areas flickering randomly, and random systemwide freezes, anymore...

---

### Post by lordmule on 2007-11-09
Hey this is a nice guide. I only just decided to try getting ubuntu back on my mac last night (without reading this thread), I managed to get two stages of 3D drivers installed the one in the ubuntu repos: 8.37.x

So with this direct rendering available I was able to get a pithy 2500fps on glxgears

and following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") I managed to get up to the same version driver as you posted: 8.42.3 ( 2.0.6958 )

now that I have the latest driver my macbook pro managed 3500fps on glxgears, which is not at all great because the interface, cpu and gfx capabilities should see something in the order of 4000+. By comparison my geforce 4 ti4200 achieves 3000fps, and my geforce 6600gt does 4200fps, both in dual screen mode!

my macbook pro specs:

Intel Core Duo T2500 2.00GHz
1GB DDR2 RAM
ATI Mobility Radeon x1600 256MB 

uname -a: Linux 2.6.22-14-generic #1 SMP i686

I had this problem last year and held off till it was fixed...my laptop has been idle since :( I did notice a difference in the guide here youve managed to get composite and define a number of other features within xorg.conf

I was hoping people who have successfully set this up could report their glxgears performance.

thanks

---

### Post by zunzun on 2007-11-15
You made my day! It totally worked for me. Thank you very much!

I kind of cheated on your howto, though.
I first installed [envy]("http://albertomilone.com/nvidia_scripts1.html") (also needs some of your packages in step 4), then I started of at step 9. Worked like a charm.

After I rebooted, the package manager asked me to update linux-restricted-modules-2.6.20-16-generic and linux-restricted-modules-common. I don't know if this is a coincidence or related to my method of appoach :P

Haven't done the update yet, but I'm planning to.

Oh, BTW, I did it with Feisty.

---

### Post by zunzun on 2007-11-15
I updated. Bummer, the update destroys compiz again :-(

---

### Post by zunzun on 2007-11-15
The suggested update appears not to be caused by my alteration. On my other pc running kubuntu the updates were also available. So back to installing again :-)

---

### Post by bremen on 2007-11-23
I think the majority of this guide is unnecessary.  I just installed on a Xpress 200 using the restricted driver manager AND unblacklisting my card in /usr/bin/compiz.  Apparently the problem was always compiz and not the driver itself :)

---

### Post by drama1981 on 2007-11-23
> **bremen said:**
> I think the majority of this guide is unnecessary.  I just installed on a Xpress 200 using the restricted driver manager AND unblacklisting my card in /usr/bin/compiz.  Apparently the problem was always compiz and not the driver itself :)

strange that worked for you. i tried the same thing first. it kept kicking me out of my desktop and back to the login widow after less than 10 secs. as a side note you may have xgl installed also were as i dont. 

p.s. thankx to the poster of this guide it works like a champ now. although i cant use my rt kernel (havent tried a recompile yet)

---

### Post by bremen on 2007-11-24
It was a fresh install.  Not sure if xgl is installed by default or not, but I certainly didn't install it.  Only other things I did were a couple failed attempts using the restricted driver manager, and some edits to xorg.conf which were deleted each time it failed to load fglrx and defaulted to low graphics mode (replacing xorg.conf in the process)

---

### Post by drama1981 on 2007-11-24
> **bremen said:**
> It was a fresh install.  Not sure if xgl is installed by default or not, but I certainly didn't install it.  Only other things I did were a couple failed attempts using the restricted driver manager, and some edits to xorg.conf which were deleted each time it failed to load fglrx and defaulted to low graphics mode (replacing xorg.conf in the process)

did you change composite to "1" and add option aiglx "true" to xorg.conf?  i just ask that because i never tried adding them to xorg with the driver from the repos so that may be why that one didnt work for me. but im thinking maybe aiglx was supported before now ati just neglected to tell us that. it wouldnt be the first time something was supported and ati just didnt mention it.

---

### Post by bremen on 2007-11-24
No, the only thing I fiddled with in xorg.conf was the driver string.

---

### Post by oblivion82892 on 2007-11-27
Ok, I am a TOTAL n00b(I mean like first time EVER linux user). I was referred to use this by a friend of mine, and I am trying to find out how to make compiz fusion work. I am using a live CD. I just want to know how to get it on really quickly in the beginning so I can play around with it for the rest of the session.

I tried what he said in the first post, but then when I typed in the compizconfig into the search thingy, it didn't have compizconfig-settings-manager or whatever. It only have libcompiz.........

So from the second the desktop appears to the moment I get to play around with the cube, can you non-n00bs please give me an exact step-by-step explanation of exactly what I am supposed to do, what I'm supposed to click, what I'm supposed to type and where? I need lots of help!!!!!!!!!!
THANKS!!!!!!!!!!

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by drama1981 on 2007-11-27
> **oblivion82892 said:**
> Ok, I am a TOTAL n00b(I mean like first time EVER linux user). I was referred to use this by a friend of mine, and I am trying to find out how to make compiz fusion work. I am using a live CD. I just want to know how to get it on really quickly in the beginning so I can play around with it for the rest of the session.

I tried what he said in the first post, but then when I typed in the compizconfig into the search thingy, it didn't have compizconfig-settings-manager or whatever. It only have libcompiz.........

So from the second the desktop appears to the moment I get to play around with the cube, can you non-n00bs please give me an exact step-by-step explanation of exactly what I am supposed to do, what I'm supposed to click, what I'm supposed to type and where? I need lots of help!!!!!!!!!!
THANKS!!!!!!!!!!

:confused::confused::confused::confused::confused::confused::confused::confused:

to be honest with you i dont think its possible to do it from a live cd. the reason is because after you build the kernal module you have to reboot. however when your running a live cd and you reboot everything is reset hence you will lose any settings you have changed including installing driver/building the module. my suggestion would be to just install ubuntu. you can run ubuntu & windows or any other os from the same hard drive (dual boot) without losing anything providing you have enough space. you just need to resize your drive and setup a few new partitions. all of this is easily done during the install though.

---

### Post by briandu on 2007-11-27
Thanks for the guide, however when I get to Step 10 I receive all the right signals - meaning I get:

/etc/X11# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

followed by:

/etc/X11# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

It seems OK BUT  I had tp copy the file from the ...../misc  to the ...../volatile and NOT use the link ln-s method as after I reboot the link will be gone! Why I do not know. I only got to this point by copying the file.

On Step 11 it seems you repeat the same file linking - why? I fire off the aticonfig commands  and reboot yet I can not get further than Step 10. Any ideas? :confused:

---

### Post by drama1981 on 2007-11-27
> **briandu said:**
> Thanks for the guide, however when I get to Step 10 I receive all the right signals - meaning I get:

/etc/X11# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

followed by:

/etc/X11# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

It seems OK BUT  I had tp copy the file from the ...../misc  to the ...../volatile and NOT use the link ln-s method as after I reboot the link will be gone! Why I do not know. I only got to this point by copying the file.

On Step 11 it seems you repeat the same file linking - why? I fire off the aticonfig commands  and reboot yet I can not get further than Step 10. Any ideas? :confused:

i had the same problem but i found a fix for it elsewhere. i would set the link up again using the ln-s method since this is only way i have done it. now onto the fix.

You may need to add this to your rc.local so a symbolic link is created on boot. Some installs of Gutsy will remove the link on boot. If this link is not present you will not have 3D acceleration.

open terminal

gksu gedit /etc/rc.local

and before the "exit 0" line add the following :

insmod /lib/modules/$(uname -r)/misc/fglrx.ko

hope this helps. cheers :)

---

### Post by briandu on 2007-11-28
Hi drame1981,
this did not work so I rebooted and went into safe terminal and then deleted the file from .../volatile and then inserted the link ...ln -s......etc.
I also inserted the  statement into the rc.local and had to back that out due to the  conflict with what I did in the safe terminal. It must be said that the rc.local by itself did not work which is why i went "undercover" via safe terminal.

This is now stable HOWEVER...
glxinfo | grep direct    still give the wrong answer and fails so I am no further even after all this.

Any ideas anyone?
:confused:

---

### Post by briandu on 2007-11-28
Well, after all that the  whole thing failed and all my changed were kicked out!

The ....../volatile has reverted back to what it was! All my changes have been backed out even though I was root!

Looks like a fresh install job to me - my installation was an upgrade from v7 to v7.10

Curses!:(!

---

### Post by krelverehan on 2007-11-28
I tried your method here, but when I rebooted the second time it went into safe graphics mode and this is my readout for fglrxinfo
[INDENT][FONT="Courier New"]
krel@namcle:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)[/FONT][/INDENT]

Any ideas?

---

### Post by briandu on 2007-11-29
I would suggest that you use 

sudo dpkg-reconfigure -phigh xserver-xorg in a safe terminal window.

Looks like you have not picked up the driver at all. Use the above to pick up the driver again

---

### Post by tictactoe on 2007-12-21
vijay@vijay-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'
vijay@vijay-desktop:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

what could be the problem..........

found no problem during the installation

---

### Post by BLTicklemonster on 2008-01-04
> **lordmule said:**
> Hey this is a nice guide. I only just decided to try getting ubuntu back on my mac last night (without reading this thread), I managed to get two stages of 3D drivers installed the one in the ubuntu repos: 8.37.x

So with this direct rendering available I was able to get a pithy 2500fps on glxgears

and following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") I managed to get up to the same version driver as you posted: 8.42.3 ( 2.0.6958 )

now that I have the latest driver my macbook pro managed 3500fps on glxgears, which is not at all great because the interface, cpu and gfx capabilities should see something in the order of 4000+. By comparison my geforce 4 ti4200 achieves 3000fps, and my geforce 6600gt does 4200fps, both in dual screen mode!

my macbook pro specs:

Intel Core Duo T2500 2.00GHz
1GB DDR2 RAM
ATI Mobility Radeon x1600 256MB 

uname -a: Linux 2.6.22-14-generic #1 SMP i686

I had this problem last year and held off till it was fixed...my laptop has been idle since :( I did notice a difference in the guide here youve managed to get composite and define a number of other features within xorg.conf

I was hoping people who have successfully set this up could report their glxgears performance.

thanks

I tried using that guide, and got this when trying to install the .deb:

Errors were encountered while processing:
 fglrx-kernel-source


so I just sudo sh ati-driver~.run (whatever it's name was) and it looks installed. About to run aticonfig and see what blows up.


Edit:

Okay, it all works, except that I have a broken package in synaptic. I put:

DISABLED_MODULES="fglrx"

in

/etc/default/linux-restricted-modules-common

and all, I still show a broken package for 

fglrx-kernel-source

This is going to cause me problems, isn't it?

Do I fix it, or what?

---

### Post by sayak on 2008-03-10
you guys got a clue about any patch for installing the driver for a intel 32 bit processor ??

pls help

---

### Post by sayak on 2008-03-10
i mean  ATI Radeon Xpress 200 on an intel 32 bit 3.06GHz single core processor

---

### Post by Alhrath on 2008-07-02
Hi

Thank's a lot for this tutorial. Just need little help ^^

I can succefully complete setp 1-7 but then after reboot in step 8, after login, I just got a white screen with only the mouse activated.

I got an ATI RADEON XPRESS 200M, and use a i386 processor.

any idea of solution ?

---

