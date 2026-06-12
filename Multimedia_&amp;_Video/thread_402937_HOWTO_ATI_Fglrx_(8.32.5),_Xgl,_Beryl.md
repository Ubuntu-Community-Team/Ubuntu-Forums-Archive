---
title: "HOWTO: ATI Fglrx (8.32.5), Xgl, Beryl"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by bdogg64 on 2007-04-06
I have had problems with the fglrx drivers after 8.32.5, but now its working with my system and I wanted to share how. This is my first howto, so suggestions are welcome.

Here are the steps I took to get the driver working Ubuntu Feisty 7.04 and Xorg 7.2.

If you have previously installed a restricted driver, you need to disable it by adding fglrx to DISABLED_MODULES in /etc/default/linux-restricted-modules-common

[COLOR="Red"]*You need to enable the universe repository before updating[/COLOR]

sudo apt-get update
sudo apt-get install -y --force-yes module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r) wget

[COLOR="Red"]Download ati proprietary driver[/COLOR]
cd ~/
sudo wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.32.5-x86.x86_64.run

[COLOR="Red"]Build .deb packages[/COLOR]

sudo sh ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy

[COLOR="Red"]Install .deb packages:[/COLOR]

sudo dpkg -i xorg-driver-fglrx*.deb
sudo dpkg -i fglrx-kernel-source*.deb
sudo dpkg -i fglrx-control*.deb

[COLOR="Red"]Remove any old fglrx debs from /usr/src/:[/COLOR]

sudo rm /usr/src/fglrx-kernel*.deb

[COLOR="Red"]Needed for 8.32.5[/COLOR]

sudo mkdir -p /usr/src/modules/fglrx/linux
sudo touch /usr/src/modules/fglrx/linux/config.h

[COLOR="Red"]Download Patch for 2.6.20.* kernels[/COLOR]

cd ~/
sudo wget -O fglrx-2.6.20.patch http://ubuntuforums.org/attachment.php?attachmentid=34104&d=1180759878

[COLOR="Red"]Apply Patch for 2.6.20.* kernels[/COLOR]

cd /usr/src
sudo cp fglrx.tar.bz2 fglrx.tar.bz2-original
sudo tar -xvjf fglrx.tar.bz2
cd /usr/src/modules/fglrx
sudo patch < ~/fglrx-2.6.20.patch
cd /usr/src
sudo tar -cvjf fglrx.tar.bz2 modules/fglrx

[COLOR="Red"]Compile the kernel module:[/COLOR]

sudo module-assistant prepare

sudo module-assistant update

sudo module-assistant build fglrx

sudo module-assistant install fglrx

sudo depmod -a

[COLOR="Red"]Initial ati setup[/COLOR]

If you prefer to edit your /etc/X11/xorg.conf manually, just replace the "vesa", "ati", or "radeon" with "fglrx" instead of running the command below

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

[COLOR="Red"]You'll also want to disable AIGLX and Composite by adding this to your /etc/X11/xorg.conf[/COLOR]

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

```

And reboot your machine.

After rebooting, you can run 

```
fglrxinfo 
```

Which should show something like this

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

```

From here you should be able to follow the steps to install Xgl and Beryl

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

I hope this helps someone

B

---

### Post by zeny on 2007-04-06
Since no one else has said it, I will be first, Thank you man you rock! it helped me :)

---

### Post by moxiot on 2007-04-08
i'm sorry but i couldnt help to notice that u got ndiswrapper to work. i have the same laptop as you do. how the heck did you do it?!! i'm torn appart right now because i don't want to pay 20 bucks to the linuxant folks, not because of the money but because i want ndiswrapper to work. is there any guide that did the jod for you? i've tried it many, many times in many, many ways, and still no luck. 

also how does the beryl thing work for you, i have the ati drivers installed but i thought that our ati card wasn't compatible with beryl.

many thanks.

---

### Post by Mixy on 2007-04-09
Hi

I followed your guide, and got fglrx 8.32.5 install. Thanks for that ^^ Anyway, then i moved on to install xgl, and beryl. I clicked the link in your guide, and followed the other guide i found there :P

Anyway, i am having a problem with the other guide (i know your probably not responsible of that guide or anything, but as this is a forum, i figured i could ask :)). Anyway, i get to the point where i am supposed to add the gpg signature, and validate it.

> The packages in the repository are signed with a gpg signature so you can verify that they are valid. To add the gpg key to your keychain, use Synaptic / Adept or invoke the following command:

$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add - 
$ wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
.

I am not sure where to put this? It says I am supposed to "use Synaptic / Adept or invoke the following command:". I try in terminal, and then i get

[quote]mixy@Mixy:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
gpg: no valid OpenPGP data found.
[quote] That happends on all of the links.

Thanks for helping me out :)

---

### Post by bdogg64 on 2007-04-09
> **moxiot said:**
> i'm sorry but i couldnt help to notice that u got ndiswrapper to work. i have the same laptop as you do. how the heck did you do it?!! i'm torn appart right now because i don't want to pay 20 bucks to the linuxant folks, not because of the money but because i want ndiswrapper to work. is there any guide that did the jod for you? i've tried it many, many times in many, many ways, and still no luck. 

also how does the beryl thing work for you, i have the ati drivers installed but i thought that our ati card wasn't compatible with beryl.

many thanks.

Here is the link to the guide I followed to get ndiswrapper working. Worked like a charm

[http://ubuntuforums.org/showpost.php?p=2061722](http://ubuntuforums.org/showpost.php?p=2061722)

---

### Post by bdogg64 on 2007-04-09
> **Mixy said:**
> Hi

I followed your guide, and got fglrx 8.32.5 install. Thanks for that ^^ Anyway, then i moved on to install xgl, and beryl. I clicked the link in your guide, and followed the other guide i found there :P

Anyway, i am having a problem with the other guide (i know your probably not responsible of that guide or anything, but as this is a forum, i figured i could ask :)). Anyway, i get to the point where i am supposed to add the gpg signature, and validate it.

.

I am not sure where to put this? It says I am supposed to "use Synaptic / Adept or invoke the following command:". I try in terminal, and then i get

[quote]mixy@Mixy:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
gpg: no valid OpenPGP data found.
[quote] That happends on all of the links.

Thanks for helping me out :)

Just try the first one

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O - | sudo apt-key add -
```

---

### Post by Mixy on 2007-04-09
As i said, i got the same error for all of them :P That strangely includes the first one aswell XD

---

### Post by bdogg64 on 2007-04-09
> **Mixy said:**
> As i said, i got the same error for all of them :P That strangely includes the first one aswell XD

See if you can open this link in firefox and download the gpg to your home folder

[http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)

Then open a terminal, cd to your home directory or wherever you saved it and type
```

sudo apt-key add root*.gpg
```

This should add the authorization

Hopefully you will be able to proceed from there

---

### Post by moxiot on 2007-04-10
dude!!!! the link you gave me to for the ndiswrapper thing worked!!!! i know is off topic but i just had to YELL IT OUT. sorry, much better now. if you knew what i had been through....
anyways thanks a bunch, now i'll try your guide.

again, thanks.

---

### Post by Emx on 2007-04-10
Finnaly, something that works. Installing xorg-driver-fglrx from universe **doesn't work** because it's compiled for Xorg 7.1, and Xorg version that I have is 7.2.

---

### Post by bdogg64 on 2007-04-10
> **Emx said:**
> Finnaly, something that works. Installing xorg-driver-fglrx from universe **doesn't work** because it's compiled for Xorg 7.1, and Xorg version that I have is 7.2.

I got the driver 8.34.8 from universe to work even though its compiled for 7.1, but it wasn't very stable for me. The 8.32.5 was the best driver for me since its release.  I have since upgraded to 8.35.5 which solved my sleep, logout, and hibernate problems.  I'll still can't adjust the brightness on my laptop, which is my remaining hurdle, but that I can deal with.

---

### Post by barum87 on 2007-04-12
when I run this command:
sudo patch < -p0 ~/fglrx-2.6.20.patch

I get the following message:
bash: -p0: No such file or directory

hmm...I'm new to Ubuntu and I was basically following your guide, so what am I supposed to do here?

thanks in advance.

---

### Post by bdogg64 on 2007-04-12
> **barum87 said:**
> when I run this command:
sudo patch < -p0 ~/fglrx-2.6.20.patch

I get the following message:
bash: -p0: No such file or directory

hmm...I'm new to Ubuntu and I was basically following your guide, so what am I supposed to do here?

thanks in advance.

That command assumes you downloaded the patch to your home directory. If you downloaded it somewhere else, you will need to change the path.

e.g. 

sudo patch < path-to-your-fglrx-2.6.20.patch

---

### Post by barum87 on 2007-04-12
hmmm i do have the patch in my home directory.
it seems like -p0 is not recognized as a parameter?

---

### Post by bdogg64 on 2007-04-12
> **barum87 said:**
> hmmm i do have the patch in my home directory.
it seems like -p0 is not recognized as a parameter?

Possibly... I got the directions from ATI's website, but I'll edit the guide if it works without the -p0

---

### Post by thejaymanncan on 2007-04-20
I'm new to Ubuntu, and I'm following your guide. However, when I type in fglrxinfo after restarting, it comes up as this:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Oh yeah, when I was applying the patch, it stopped at this part:

```
Hunk #2 succeeded at 187 (offset -17 lines).
Hunk #3 FAILED at 4988.
1 out of 3 hunks FAILED -- saving rejects to file firegl_public.c.rej
```

When I log into XGL session, I get massive artifacts and glitches, so I'm guessing something went wrong when I was installing the drivers.

Hopefully you'll have some ideas of whats going on. This is all gibberish to me.

---

### Post by bdogg64 on 2007-04-21
> **thejaymanncan said:**
> I'm new to Ubuntu, and I'm following your guide. However, when I type in fglrxinfo after restarting, it comes up as this:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Oh yeah, when I was applying the patch, it stopped at this part:

```
Hunk #2 succeeded at 187 (offset -17 lines).
Hunk #3 FAILED at 4988.
1 out of 3 hunks FAILED -- saving rejects to file firegl_public.c.rej
```

When I log into XGL session, I get massive artifacts and glitches, so I'm guessing something went wrong when I was installing the drivers.

Hopefully you'll have some ideas of whats going on. This is all gibberish to me.

Can you post your Xorg.0.log and your dmesg output

---

### Post by thejaymanncan on 2007-04-21
> **bdogg64 said:**
> Can you post your Xorg.0.log and your dmesg output

Are these it?

EDIT: I managed to get Beryl to work, but I can only see one side of the cube. Every other side only displays the gnome panels, nothing else. Do you have any idea of what might be wrong?

---

### Post by rainman110 on 2007-04-23
> **thejaymanncan said:**
> I'm new to Ubuntu, and I'm following your guide. However, when I type in fglrxinfo after restarting, it comes up as this:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

Oh yeah, when I was applying the patch, it stopped at this part:

```
Hunk #2 succeeded at 187 (offset -17 lines).
Hunk #3 FAILED at 4988.
1 out of 3 hunks FAILED -- saving rejects to file firegl_public.c.rej
```

When I log into XGL session, I get massive artifacts and glitches, so I'm guessing something went wrong when I was installing the drivers.

Hopefully you'll have some ideas of whats going on. This is all gibberish to me.

Hello,

i had the same issue with no working 3d. It's okay that the patch didn't apply correctly, it still generates the kernel module. The Problem was loading the /usr/lib/xorg/modules/linux/libdrm.so (see your Xorg.0.log) . It is missing in the Xorg 7.2 release. I solved the problem by copying that file from my edgy system to feisty. For those who don't have it, you can find the file in the attachment.

Extract the file and copy it to the proper location:

```

tar -jxf libdrm.tar.bz2 
sudo cp libdrm.so /usr/lib/xorg/modules/linux/

```

Now restart X and "TADA" it works :) !

Cheers, Martin

---

### Post by banditti on 2007-04-23
I am getting the following, any thoughts?

> root@todd:/usr/src/modules/fglrx# patch < ~/fglrx-2.6.20.patch 
patching file firegl_public.c
Hunk #2 FAILED at 204.
Hunk #3 FAILED at 5069.
2 out of 3 hunks FAILED -- saving rejects to file firegl_public.c.rej


---

### Post by banditti on 2007-04-23
Sorry, forgot to mention, read and tried the above post, when I moved on in the process, got the following during the sudo module-assistant build fglrx step.

> Build of the package fglrx-kernel-source failed! How do you   &#9474;        
       &#9474; wish to proceed?

---

### Post by bdogg64 on 2007-04-23
The patch hunks 2 and 3 are going to fail, but thats ok. It will still complete the process if you build the fglrx module

---

### Post by banditti on 2007-04-23
I have the same problem and tried the solution of #19 and still it doesn't work.

---

### Post by bdogg64 on 2007-04-23
> **banditti said:**
> I have the same problem and tried the solution of #19 and still it doesn't work.

which part are you stuck on?

---

### Post by tiwoc on 2007-05-01
The fglrx kernel module does not get loaded when I follow your howto: it doesn't get listed when I run ```
lsmod
```

Even manual insertion does not work:
```
$ sudo modprobe -v fglrx
install /sbin/lrm-video fglrx 
insmod /lib/modules/2.6.20-15-generic/misc/fglrx.ko 
FATAL: Error running install command for fglrx
$
```

Any idea?

---

### Post by rainman110 on 2007-05-13
Install linux-restricted-modules-common! This will solve your problem.

---

### Post by tiwoc on 2007-05-13
It is already installed...

---

### Post by Spezi on 2007-05-19
> **bdogg64 said:**
> 

[COLOR="Red"]Download Patch for 2.6.20.* kernels[/COLOR]

cd ~/
sudo wget [http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch)



Download won't work :(
Can someone upload the file?

---

### Post by scradock on 2007-05-19
Right - the patch is no longer there. Does this mean the patch is no longer needed? Anyone know - was this fixed in Feisty release?

Without the patch, building fglrx fails for me. sudo module-assistant prepare made me remove the original fglrx-kernel-headers......, but then sudo module-assistant build fglrx failed while processing /usr/src/fglrx.tar.bz2.

Now I'm stuck. How do I recover? Any ideas? I can run with the 8.34.8 drivers, but the 8.36.5 don't seem so stable. I wanted to try 8.32.5 to see if that worked better.

HP Pavilion zv6000 with ATI Radeon Express 200M; Feisty (which I'm messing with), Edgy (my safe harbor); WXP (which I'm trying to get out of).

---

### Post by thriff on 2007-05-26
[http://www.thinkwiki.org/wiki/Problems_with_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx)

Might help...
There's no path listed for 8.36.5, so i guess it shouldn't be needed.

Personally i think I went wrong somewhere, or skipped something.

Having this in my Xorg.0.log:
```

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb78a7000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb78a7000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
I wonder why the version number is wrong... installed 8.36.5, 8.34.8 is the old one i had.

Since i don't get 3d aceleration i get this from fglrxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

Trying to find what I did wrong and fix it.

---

### Post by thriff on 2007-05-26
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6458 (8.36.5)

```

There! All fixed. I Think I had some old files messing with the modules. But after a cleanup ( sudo apt-get remove fglrx* ) and a reboot, following the guide worked nicely. With the newest kernel ( 2.6.20-16 ) and newest fglrx driver ( 8.36.5 ) ofcourse

---

### Post by Vincent_Lin on 2007-05-28
Hi,

After last nights updates (kernel, fglrx, etc..), my direct rendering is gone.  xgl session is totally bizzard looking.  gnome with metacity is fine, but no direct rendering.

Can some one tell me what I should do to enable direct rendering again?

Machine is IBM T42 with 9600 Mobility.  ubuntu 7.04 with lowlatency kernel, fglrx driver, xgl window manager, beryl, and ubuntustudio packages installed after fresh 7.04 installation. 

Thanks.

Vincent

---

### Post by Vincent_Lin on 2007-05-28
Hi,

Problem solved.

The updates conducted by Update Manger last night did not incorporate the update for linux-restricted-modules-2.6.20-16-lowlantency as part of the update.  I ran synaptic and selected to update this package and it solved the problem.

Can't tell who to blame, but it seems that Update Manager did not do it right.

Vincent

---

### Post by Vincent_Lin on 2007-05-31
Dear all,

I now have another problem after the fix mentioned in my last post to my 9600 Mobility with fglrx+xgl+beryl setup.

mplayer(gmplayer) and VLC could not play any video correctly - the image is expanded across the screen no matter what room level I select (normal, double, full screen, ), and there is a white band all over the border of the video window.  Video is still playing inside that white band/window border.  Sometimes, when I press "f" to make it full screen(in hope to bring the video playing in scale), xgl session dies and brings me back to gdm login.  Further xgl sessions after login sometimes dies(dead hang) and Ctrl-Alt-Fn, Ctrl-Alt-Backspace would not bring it to anything else.  Reset is the only way to bring it back live.

Interesting(puzzling) enough is Totem (Movie Player on gnome menu) is still  working fine except it complains not proper codec for DVD disk playing.

All things worked properly before this update, including totem, (g)mplayer and vlc.

Help!!  And thinks.

Vincent

---

### Post by ianrit on 2007-05-31
> **scradock said:**
> Right - the patch is no longer there. Does this mean the patch is no longer needed? Anyone know - was this fixed in Feisty release?

Without the patch, building fglrx fails for me. sudo module-assistant prepare made me remove the original fglrx-kernel-headers......, but then sudo module-assistant build fglrx failed while processing /usr/src/fglrx.tar.bz2.


I am having the same problems at this step as well. I am relatively new at this, so any help is most welcome. 

If you need me to post any logs or anything, just let me know.

-Thanks

---

### Post by bdogg64 on 2007-05-31
> **ianrit said:**
> I am having the same problems at this step as well. I am relatively new at this, so any help is most welcome. 

If you need me to post any logs or anything, just let me know.

-Thanks

You don't need the patch anymore starting with version 36.5, but it was unstable for me.  If anyone still needs the patch I can attach it.

---

### Post by rtech1 on 2007-06-01
> **bdogg64 said:**
> You don't need the patch anymore starting with version 36.5, but it was unstable for me.  If anyone still needs the patch I can attach it.

Yes!!!! I Need it... Please!!! Thanx

---

### Post by bdogg64 on 2007-06-02
Here is the patch - fglrx-2.6.20.patch

---

### Post by daimaru on 2007-06-02
dont quite get y you go through all the trouble why not just use the restriced drivers? i mean on edgy i used the original drivers from ati too but on feisty the restriced driver manger drives work just fine. 

so just click them 
go [here]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty")
follow the guide and u got beryl running...

---

### Post by bdogg64 on 2007-06-02
> **daimaru said:**
> dont quite get y you go through all the trouble why not just use the restriced drivers? i mean on edgy i used the original drivers from ati too but on feisty the restriced driver manger drives work just fine. 

so just click them 
go [here]("http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty")
follow the guide and u got beryl running...

The restricted drivers dont work successfully for everyone. I've tried the restricted drivers and they werent stable enough for me. I just installed the 8,37.6 driver that was released and iits working well so far.

---

### Post by applefreakpeeps on 2007-07-03
How about 2.6.21 ?? Willl the same method work?

---

