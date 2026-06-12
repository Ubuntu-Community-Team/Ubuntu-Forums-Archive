---
title: "How to get S3/VIA UniChrome video to work in Ubuntu Dapper!"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by pcatiprodotnet on 2006-09-25
I have "S3 UniChrome" graphics video built into my cheap motherboard, and Ubuntu Dapper didn't detect it, so it defaulted to type "vesa" with no 3D acceleration; I tried changing /etc/X11/xorg.conf from "vesa" to "via", as some others have done, but it didn't work.
The following OpenChrome.org driver worked great for me! It has an easy .deb package (already compiled binary for kernel 2.6.15-26-386, run with "dpkg -i x.deb", or you may compile your own); be sure to read the easy readme...
[http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

To compile your own (if you upgraded your kernel)...
When asked to type "./autogen.sh" you really need to type: ./autogen.sh --prefix=/usr/
If you use the gui/window to copy files to a system folder it will need Write access; so, be sure to open the "To" window from your root terminal prompt by typing "sudo nautilus".
sudo apt-get install subversion build-essential automake1.9 libtool pkg-config xserver-xorg-dev libxvmc-dev x11proto-gl-dev libglu1-mesa-dev x11proto-core-dev libxvmc-dev xserver-xorg-dev x11proto-gl-dev libgl1-mesa-dev cvs
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)
also read...
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[http://gamesplace.info/opensource/openchrome/dapper-binaries/README](http://gamesplace.info/opensource/openchrome/dapper-binaries/README)
sudo gedit /etc/X11/xorg.conf and replace "vesa" with "via".
I just upgraded my kernel to 2.6.15-27-686 and the compile instructions worked flawlessly; however, it wasn't noticably faster than the pre-compiled 386 version, according to command: glxgears -printfps

After you get it working (test with "glxinfo" indicating direct rendering, "glxgears -printfps", and a 3D game from the repository like TuxCart), I recommend locking this xorg package and the matching kernel in synaptic until you're ready for future upgrades. If it breaks your video then change "via" back to "vesa".  Ubuntu developers, please add this to future releases.
Enjoy, -pc

---

### Post by ozp on 2006-09-27
I have a similar video card. Xorg says it is a VESA one

Its a k8m890 

[http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/](http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/)

at the viaarena.com its possible to download source code of the video driver.

I dont have a clue about how to install this

but It would be good to have a working driver because the VESA one its really to bad

---

### Post by pcatiprodotnet on 2006-10-02
I updated my original post with more info & tips on compiling.  However, I'm not sure if this will help with the viaarena driver.

---

### Post by kernco on 2006-10-02
> **ozp said:**
> I have a similar video card. Xorg says it is a VESA one

Its a k8m890 

[http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/](http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/)

at the viaarena.com its possible to download source code of the video driver.

I dont have a clue about how to install this

but It would be good to have a working driver because the VESA one its really to bad

I have the same, and haven't been able to get the via driver to work, I'm stuck using vesa.  I updgraded to the pre-release edgy packages, and now X is very, very slow.  I would really like to get via working.  I did the steps above, but still no luck.  X fails to start with the error "no devices found" or something along those lines.

---

### Post by ozp on 2006-10-03
I live in Brazil and here this kind of chipset is very popular because its cheap.

I have 2 computers running VIA chipsets in my office.
and another old computer running xubuntu 

I´m a linux advocate and some of the few psychologists that is able to run linux on your own (I had some support to install one ubuntu and the xubuntu)

But I am unable to read and make deep changes in the system. This is not possible.

Ubuntu team or Brazilian Ubuntu team should look closer to this issue

---

### Post by pulver on 2006-10-25
ozp, tried the openchrome driver yet? ;)

---

### Post by ozp on 2006-10-26
I dont know how to install the driver.

The computer is used for work (so it cannot stop for any reason)

So if the installs require just "sudo apt-get install" thats ok
but if it is required to do more stuff, I get afraid to make X stop at all

Is there a easy way to install the openchrome driver?

---

### Post by pulver on 2006-10-27
I'm not running Ubuntu atm, switched to arch, so I'm not the right person to answer that question. On arch it's in the extra repo so a pacman -S openchrome and change from vesa to via in xorg.conf is all needed to get out of vesa hell. Maybe someone else can help you install it on Ubuntu.

---

### Post by deanlinkous on 2006-11-19
All I remember doing is downloading drm.ko and via.ko from here
[http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

put the drm.ko and via.ko files in the /lib/modules/2.6.15-26-386/kernel/drivers/char/drm/ folder.

Now download xserver-xorg-driver-via_+194-1_i386.deb from
[http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)
and save it somewhere.

Install the deb using **dpkg -i xserver-xorg-driver-via_+194-1_i386.deb**

Now use the command **sudo depmod -ae**

Now edit you xorg.conf and change **vesa** to **via**

reboot or restart xserver....

3D acceleration on and rocking TuxRacer watch out!

---

### Post by wickwire on 2006-11-19
I have an amilo L7310W, after a clean install (dapper 6.06) I replaced the "vesa" driver with the "via" driver on xorg.conf and in order not to get a black screen when loading X, I added:

Option "VBEModes" "true" in the Section "Device" of the xorg.conf file

- I get direct rendering: yes ever since. Didn't need to install any other packages to get it to work.

Forgot to mention, also tried out tuxracer (different name recently though, in the repos) and it worked just fine. Hope this helps.

---

### Post by sabitha on 2006-11-19
can i use this for via K8M800 ??? :-?

---

### Post by sabitha on 2006-11-19
> **pcatiprodotnet said:**
> I have "S3 UniChrome" graphics video built into my cheap motherboard, and Ubuntu Dapper didn't detect it, so it defaulted to type "vesa" with no 3D acceleration; I tried changing /etc/X11/xorg.conf from "vesa" to "via", as some others have done, but it didn't work.
The following OpenChrome.org driver worked great for me! It has an easy .deb package (already compiled binary for kernel 2.6.15-26-386, run with "dpkg -i x.deb", or you may compile your own); be sure to read the easy readme...
[http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)

To compile your own (if you upgraded your kernel)...
When asked to type "./autogen.sh" you really need to type: ./autogen.sh --prefix=/usr/
If you use the gui/window to copy files to a system folder it will need Write access; so, be sure to open the "To" window from your root terminal prompt by typing "sudo nautilus".
sudo apt-get install subversion build-essential automake1.9 libtool pkg-config xserver-xorg-dev libxvmc-dev x11proto-gl-dev libglu1-mesa-dev x11proto-core-dev libxvmc-dev xserver-xorg-dev x11proto-gl-dev libgl1-mesa-dev cvs
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code)
also read...
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)
[http://gamesplace.info/opensource/openchrome/dapper-binaries/README](http://gamesplace.info/opensource/openchrome/dapper-binaries/README)
sudo gedit /etc/X11/xorg.conf and replace "vesa" with "via".
I just upgraded my kernel to 2.6.15-27-686 and the compile instructions worked flawlessly; however, it wasn't noticably faster than the pre-compiled 386 version, according to command: glxgears -printfps

After you get it working (test with "glxinfo" indicating direct rendering, "glxgears -printfps", and a 3D game from the repository like TuxCart), I recommend locking this xorg package and the matching kernel in synaptic until you're ready for future upgrades. If it breaks your video then change "via" back to "vesa".  Ubuntu developers, please add this to future releases.
Enjoy, -pc

work nice on K8M800 forget about my first question.
~$ glxinfo | grep direct 
__driCreateNewScreen_20050727 - succeeded
direct rendering: Yes

and now my FPS score (before 27x.xxx FPS)
~$ glxgears
__driCreateNewScreen_20050727 - succeeded
2375 frames in 5.0 seconds = 474.862 FPS
2229 frames in 5.0 seconds = 445.733 FPS
2398 frames in 5.0 seconds = 479.544 FPS
2397 frames in 5.0 seconds = 479.346 FPS

great HOWTO

---

### Post by deanlinkous on 2006-11-19
> **wickwire said:**
> I have an amilo L7310W, after a clean install (dapper 6.06) I replaced the "vesa" driver with the "via" driver on xorg.conf and in order not to get a black screen when loading X, I added:

Option "VBEModes" "true" in the Section "Device" of the xorg.conf file

- I get direct rendering: yes ever since. Didn't need to install any other packages to get it to work.

Forgot to mention, also tried out tuxracer (different name recently though, in the repos) and it worked just fine. Hope this helps.

Thanks for that!!! Interesting that we cant have this out of the box!

---

### Post by girgi on 2006-11-20
I have gateway mx 3231  notebook with S3 Graphics UniChrome Pro IGP this video card,

there was terribel graphic accelerator, I installed this one, change "vesa" to "via" and now it is qoute good!:) but now there is one problem, I cann't watch video:( there is only sound, there is no video:(  why?   plsss help mee...

before I installed this driver, I was watching video...

---

### Post by girgi on 2006-11-23
hello....plssss HELPPP meeee................ I want to watch video........

---

### Post by du_chef on 2006-11-27
> **wickwire said:**
> I have an amilo L7310W, after a clean install (dapper 6.06) I replaced the "vesa" driver with the "via" driver on xorg.conf and in order not to get a black screen when loading X, I added:

Option "VBEModes" "true" in the Section "Device" of the xorg.conf file

- I get direct rendering: yes ever since. Didn't need to install any other packages to get it to work.

Forgot to mention, also tried out tuxracer (different name recently though, in the repos) and it worked just fine. Hope this helps.

I tried this in ubuntu edgy 6.10 didn't work at all.. It seems that I must bye my self a new graphic card...

---

### Post by sud_crow on 2006-12-02
> **du_chef said:**
> I tried this in ubuntu edgy 6.10 didn't work at all.. It seems that I must bye my self a new graphic card...

I made a howto, but it is in Spanish.
You can have a look here:
[http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/](http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/)

If there is enough interested people, I may translate it.

This howto was made for the via k8m890 chipset and Ubuntu Edgy 6.10, but it should work for any video card supported by the VIA ARENA Linux driver and every Ubuntu where the dependencies are met.

Regards.

---

### Post by jeeves on 2006-12-03
There's certainly interest - I think the failure to get unichrome grahics working on Ubuntu has been a major problem for a lot of users with inexpensive PCs.

I fed your instructions through the Google Spanish > English translator, which helped quite a bit. But if you decide to do an actual english version, it should make a lot of people happy.

---

### Post by rudykovanda on 2006-12-05
> **ozp said:**
> I have a similar video card. Xorg says it is a VESA one

Its a k8m890 

[http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/](http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/)

at the viaarena.com its possible to download source code of the video driver.

I dont have a clue about how to install this

but It would be good to have a working driver because the VESA one its really to bad

I have MB Asus K8V-VM witch K8M890CE (3230) graphics and in Kubuntu 6.10 I have this same problems, in "vesa" is very slow. I use Google :) and read this :

[http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188](http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188)

and make:


sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

sudo apt-get install build-essential libxinerama-dev x11proto-xinerama-dev libxvmc-dev sysutils tofrodos

sudo apt-get build-dep xserver-xorg-video-via

sudo apt-get build-dep xorg


(if question about install/remove say Y)

dovnload souce from 

[http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz](http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz)


and as root (or sudo)

# tar zxvf CN_CX700-CN800XORG40071-kernel-src_[fecha].tgz

# cd CN_CX700-CN800XORG40071-kernel-src_[fecha]/src

# ./makedriver

type your release and select procesor architecture


its make DIR CN_CX700-CN800XORG400xxx (xxx - release)


# ldconfig

# ./vinstall_2D

- this install via_drv.so and modify xorg.conf

and startx - in x86 via driver loaded, screen is very faster that "vesa", but screen is very unstable, has bug, broken pixels etc...

in 64bit driver not load, I not remember error, I test x86.... 

Any idea ?

---

### Post by rudykovanda on 2006-12-05
I added 

Option "no_accel" "yes" 

and driver works fine ! No 3D, but fast 2D....

---

### Post by sud_crow on 2006-12-05
Well, although rudykovanda made a good abstract of what is sayd in the tutorial, I was already in the translation process, so I ended it anyway.

I leave the link here, but im opening another post, as this is made with Edgy in mind and this thread was about Dapper.
[How-to: VIA K8M890 Chrome 9 IGP and Linux’s Xorg - Ubuntu Edgy 6.10]("http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")

Hope its good enough. If there are any grammatical or orthographic errors, please tell me about them.

---

### Post by ellip on 2006-12-11
First off, I would like to thank you for the English tutorial, it was very helpful.

But now I am having a problem after the install finished.  I ran vinstall_2D and everything went fine so I rebooted.  X starts up but it is a completely blank screen.  X does not crash and it plays the normals sounds when Gnome starts.  So I killed X and read the output.  It gave this error:

(EE) VIA(0): Couldn't open "/dev/video2"


I am not sure where to go from here.  Any ideas?
Thanks.

---

### Post by furni on 2007-04-25
i try to install this driver on my laptop with vn890 chipset.

and i have problem :
> 
c# ./makedriver 
Which version driver you want to release ? 
71
mkdir: nie mo&#380;na utworzy&#263; katalogu `/CN_CX700-CN800XORG40071/': File exists
mkdir: nie mo&#380;na utworzy&#263; katalogu `/CN_CX700-CN800XORG40071//': File exists
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P),C7/C7M, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
1
cd: 5: can't cd to ../../../../../../config/imake
okay, continuing in programs/Xserver/hw/xfree86/drivers/via
+ rm -f Makefile.bak
+ mv -f Makefile Makefile.bak
../../../../../../config/imake/imake -I../../../../../../config/cf  -Wundef -DTOPDIR=../../../../../.. -DCURDIR=programs/Xserver/hw/xfree86/drivers/via
/bin/sh: ../../../../../../config/imake/imake: not found
make: *** [Makefile] B&#322;&#261;d 127
Vim: Warning: Input is not from a terminal
Makefile:4: *** polecenia zaczynaj&#261; si&#281; przed pierwszym obiektem. Stop.
cp: nie mo&#380;na wykona&#263; stat na `via_drv.o': No such file or directory
 -------- Complete to make & copy driver --------

i check imake
> 
# whereis imake
imake: /usr/bin/imake /usr/X11R6/bin/imake /usr/bin/X11/imake /usr/share/man/man1/imake.1.gz

so mayby someone know where is the problem?

---

### Post by ozp on 2007-04-25
I have a 7.04 box here, that use the VIA chipset

I think the new ubuntu can set up the VIA now

Maybe its easyer to upgrade ubuntu instead of hacking around 

I&#314;l try to upgrade my 6.06 version to 7.04 so I can use the right driver

---

### Post by furni on 2007-04-26
Unfortunately, not  becouse i working on ubuntu 7.04 and i still have this problem. I try to use xserver-xorg-video-via package form reposytory and it didnt work. :(

---

### Post by deepclutch on 2007-05-01
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

^^ for Via gfx the only way is =D> 
thx openchrome guys!

---

### Post by furni on 2007-05-02
> **deepclutch said:**
> [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)


i doesnt work. :( 

Xorg.0.log:
```

...
(II) VIA: driver for VIA chipsets: CLE266, KM400/KN400, K8M800,
	PM800/PM880/CN400, VM800/CN700/P4M800Pro
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by Cyber+ on 2007-05-03
Thats not working on 7.04 :(

---

### Post by ubunxpm on 2007-05-04
Hello everybody,

I used to have the crawling X server problem when the via driver was in use. I used the "vesa" driver for a while but it's inefficient and can not be a substitute to "via" since 3D doesn't work well with it.

I found out that the problem is kernel related. It's not ubuntu's fault. For some reason this new kernel that ubuntu and many other distributions using causes a device (don't know which one) to use the same IRQ with the video card. 

I don't want to give some nice metaphors to better explain why your X server is too slow (even though I can) instead I am going to give you just a link:

[https://help.ubuntu.com/community/DebuggingIRQProblems?highlight=%28irq%29](https://help.ubuntu.com/community/DebuggingIRQProblems?highlight=%28irq%29)

this wiki page explains ways to solve IRQ Conflicts. The replacement boot parameter that I used is "pci=routeirq"

reconfigure the xserver to use the via driver and reboot. At the grub menu use one of the available boot parameters explained in the link and make sure your systems boots properly and brings you to the desktop (no crawling). Then make the changes permanent by editing menu file.

path for the menu file: /boot/grub/menu.lst
command to edit the menu file: sudo gedit menu.lst

Hope the info helps...

---

