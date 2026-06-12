---
title: "ATI/AMD FGLRX graphics driver not installing"
date: 2011-06-18
forum: Multimedia Software
---

### Post by xavi787 on 2011-06-18
Hello

I tried to install the 3D-accelerated proprietary graphics driver for my graphics card but it doesn't work. 

I went to System > Administration > Hardware drivers.

It downloads but when trying to install I get an error that says: "SystemError: installArchives() failed"

lspci shows:
```

xavi@xavi-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
xavi@xavi-laptop:~$ 


```

thanks

---

### Post by handy on 2011-06-18
You have to uninstall the open-source drivers before you install the Catalyst stack.

After which you should be able to get where you want to be following the info' provided here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by xavi787 on 2011-06-18
> **handy said:**
> You have to uninstall the open-source drivers before you install the Catalyst stack.

After which you should be able to get where you want to be following the info' provided here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

What is the difference between the open-source drivers and the FGLRX driver? If there is no difference how can I go back to the open-source driver because I can't enable visual Effects in Appearance Preferences ](*,)

thanks

---

### Post by handy on 2011-06-18
The open-source drivers give great 2D & movie playback (still with some resolution limitations that won't bother most of us).

Where the Catalyst proprietary driver is still way ahead (though the gap is starting to close lately :)) is in 3D. Which means that you can't play games with intensive 3D with the open-source driver but you can with Catalyst.

If you have the desire to play such 3D games you should stick with Catalyst & hopefully a Ubuntu user will be able to give you the run-down on solving your problem.

If you want to go back to the open-source Gallium driver stack, first you have to be sure to purge the Catalyst stack & then reinstall the packages that you need. You will find a how-to linked at the bottom of the page. 

My search shows the Ubuntu wiki to be out of date, as the AMD/ATi open-source "Gallium" driver stack is being talked about as if it is in the future wherein  it is the driver stack that the current Ubuntu 11.04 is shipped with!

So (you may be appreciating that I no longer use Ubuntu, haven't for years, though Linux is more or less Linux underneath. :)) if you enable the xorg-edgers ppa repo you will get the latest open-source drivers as they become available. I have been using these (via a different source) on Arch Linux for pushing 21 months, & using the git kernels as well. The reliability has really pleasantly surprised me.

I have a how-to for xorg-edgers ppa & the kernel (you don't have to change the kernel to use the ppa) down in the **Ubuntu Stuff:** section of the first post of the thread linked below. If you aren't interested in upgrading your kernel then after purging Catalyst (*step 1. of the how-to*) just go to **5. Add the xorg-edgers PPA**, it is a simple process:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by Yellow Pasque on 2011-06-19
Or you could use this guide to install the latest fglrx drivers properly: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by xavi787 on 2011-06-20
> **handy said:**
> You have to uninstall the open-source drivers before you install the Catalyst stack.

After which you should be able to get where you want to be following the info' provided here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

How do I uninstall the open-source drivers? BTW I switched to Ubuntu 10.10.

---

### Post by xavi787 on 2011-06-20
Help anyone?

---

### Post by handy on 2011-06-20
Best to follow the guide in post_5.

---

### Post by Claus7 on 2011-06-20
Hello,

the commands you are asking are:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
to remove any remnants from fglrx.

And
```
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
```

to get rid of the open source drivers.

Regards!

---

### Post by xavi787 on 2011-06-21
I uninstalled the open-source drivers and tried to install FGLRX drivers without success. I got this when trying to install that driver:

```
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168d-1.fw for module r8169
```

Also when I type fglrxinfo I get this:

```
Segmentation fault
```

I think the drivers didn't install properly

---

### Post by Claus7 on 2011-06-24
Hello,

the segmentation fault indeed indicates that something is conflicting. I would advice you to remove everything that is named like: xserver-...

When you do that, restart, then install the packages you want, restart again, and see what you get.

Regards!

---

### Post by xavi787 on 2011-07-08
> **Claus7 said:**
> Hello,

the segmentation fault indeed indicates that something is conflicting. I would advice you to remove everything that is named like: xserver-...

When you do that, restart, then install the packages you want, restart again, and see what you get.

Regards!

On another partition I installed Ubuntu 10.10 and tried to install the FGLRX driver. 

First I tried to install using Additional Drivers without success.

Second I tried to install it manually and again I got the Segmentation fault error

Third I uninstalled the open-source and FGLRX drivers and  rebooted the computer. After that I tried to install the FGLRX again and yet again I got the Segmentation fault error.

I removed the ATI open-source drivers. When I go to Synaptic Package Manager and type xserver there are other xserver packets (mouse input, and other video cards). My question is: 
Should I unistall those as well? or those packets don't interfere with the FGLRX?

---

### Post by bobwyajnr on 2011-07-08
Hey dude,

It's me again! :popcorn:

OK to even have a hope of running FS-X you need the proprietary drivers up and working 100%!! It'll probably still end up being a slide-show though... ;)

Download Catalyst 11.6 straight from AMD/ATI. Make sure you're getting the **HD 3xxx** series and the right Linux OS architecture (x86 or x86/x64).

Follow the install guide posted by Temüjin ([Ubuntu Maverick install ATI Catalyst guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide"))! Follow the guide carefully to get the build dependencies and build the .deb file. Stop at this point!

I usually install the ATI driver .deb file in a root shell (boot into safe mode and select root shell w/networking). You probably also want to purge the OSS radeon driver stuff in a root shell (since you can be sure X won't be running!!) If you type:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh 2>&1 | tee /home/xavi/debug.txt
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx 2>&1 | tee -a /home/xavi/debug.txt
sudo dpkg -i fglrx*.deb 2>&1 | tee -a /home/xavi/debug.txt
chown xavi:xavi /home/xavi.debug.txt
```
All the ATI driver install console output goes into a debug file as well!

**nano** and **vim** are the usual emergency 'console only' text editors (nano being for human beings)! Get familiar with your commandline!! Get familar with the shortcuts to enter you TTY console sessions (CTRL+ALT+F1 -> CTRL+ALT+F6) - you can safely shutdown your system from these (when X hangs and you have a black screen, etc.)
```
sudo shutdown now
```

Don't go on blindly if you get a problem during the installation - just stop the guide. Follow the guide to get your OSS driver back if you can't boot into any kind of X-session. Put the guides into text files or print them off/use a second computer!

Please post the debug file here and any other errors! :D


Bob

PS
Catalyst 11.6 may be rubbish but yes it can play Crysis (on my laptops Radeon M4650M card)!!

Also if we really get stuck, on this thread, then get on the case to ATI... Their Linux drivers are still kak and they need to be told!! Where is my 4650M video UVD2 video decode acceleration, etc. :)

---

### Post by Claus7 on 2011-07-08
Hello,

> **xavi787 said:**
> On another partition I installed Ubuntu 10.10 and tried to install the FGLRX driver. 

First I tried to install using Additional Drivers without success.

Second I tried to install it manually and again I got the Segmentation fault error

Third I uninstalled the open-source and FGLRX drivers and  rebooted the computer. After that I tried to install the FGLRX again and yet again I got the Segmentation fault error.

I removed the ATI open-source drivers. When I go to Synaptic Package Manager and type xserver there are other xserver packets (mouse input, and other video cards). My question is: 
Should I unistall those as well? or those packets don't interfere with the FGLRX?

no, just remove the xserver-... that has to do with ati, radeon, nvidia.

I think that as *bobwyajnr* proposes chances are that you will avoid the segmentation fault if you install the drivers during safe mode.

Regards!

---

### Post by xavi787 on 2011-07-09
How do I boot into safe mode?:confused:

---

### Post by bobwyajnr on 2011-07-09
> **xavi787 said:**
> How do I boot into safe mode?:confused:

That's what that extra option (that you've never used!!) is for in the Grub menu. That's the menu that appears when you first turn on your PC. If it doesn't appear!! then maybe you want to jank up the timeout setting. You can do this in the **startupmanager** GUI (installed by default on Ubuntu Gnome I believe? Certainly in the repositories).

In this lovely Linux-Mint Grub bootloader (yes I can heartily recommend this distro :) ):
[IMG]http://farm2.static.flickr.com/1117/1191230849_68d271ee85_o.png[/IMG]
one would chose the second option down entitled **recovery mode**.

Generally Grub by default orders stuff:
> [SIZE="2"][LIST=1]
[*]boot newest kernel
[*]boot newest kernel (safe mode)
[*]boot older kernel
[*]boot older kernel (safe mode)
...
[*]memory test
[*]boot that horrible other OS by Bill something (that can't write to native Linux filesystems)
[/LIST][/SIZE]

OK seriously off-topic now: :popcorn:
Linux is an amazing OS. I recently had some 'issues' with my Grub bootloader. In the end I fixed it by **chroot**'ing my Linux install from a live session (read 'fool' the running Linux session that it had actually booted off the harddisk). A few simple lines of code and bang had my boot loader back (that one is on perma -bookmark now)!

Bob

---

### Post by xavi787 on 2011-07-09
Hello,

I booted into safemode and installed the driver. (I think so)
Then I booted normaly and typed fglrxinfo to see if the driver was working and once again "segmentation fault"

I attached the debug file

---

### Post by bobwyajnr on 2011-07-09
I did accidentally leave off (ah if you'd read the linked guide you would have seen my deliberate error:
```
sudo aticonfig --initial -f
```
just before you run:
```
flgrxinfo
```

But TBH I doubt that would cause a segmentation fault with the **fglrxinfo** (you might not get a sensible video mode when you reboot though). Give that a try (you've been to hell and back already - right? :p)

OK so you've only got the stock Maverick 32-bit kernel.

Did you enter the **root shell** after selecting **recovery mode** (just you and a console window - no fancy window managers at all)? Just clutching a straws here really. :D

I think your best bet is to raise a support incident with ATI directly (since your card is still officially supported). Make sure the HD3200M graphics card actually uses the HD3xxxM driver (I've read it's a die-shrunk HD 2400M so it would seem to be about right). It is a bit odd that you've replicated the same problem with installs of 2 different operating system versions...

Urumpph and I thought the ATI Linux installer had been improving slightly in recent months... Anyway keep the thread open... Maybe someone else can spot the subtle flaw in that log file... TBH it looked like a clean install to me.

Bob

---

### Post by bobwyajnr on 2011-07-09
Ah I forgot to check if you did the crucial reboot as well ([again from the linked guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Issues")):

> Reboot or fglrxinfo gives an error message. 

So did you (starting with the root shell/ **recovery mode**):
```
sudo aticonfig --initial -f
```
**[COLOR="DarkRed"]!!REBOOT NOW!![/COLOR]**

```
fglrxinfo
```

??

Bob

---

### Post by xavi787 on 2011-07-09
> **bobwyajnr said:**
> Ah I forgot to check if you did the crucial reboot as well ([again from the linked guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Issues")):



So did you (starting with the root shell/ **recovery mode**):
```
sudo aticonfig --initial -f
```
**[COLOR="DarkRed"]!!REBOOT NOW!![/COLOR]**

```
fglrxinfo
```

??

Bob

```
xavi@xavi-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 3.3.10524 Compatibility Profile Context

xavi@xavi-pc:~$ 


```

What does that mean? 
JK thanks a lot, now I just have to do all this again on my other OS.

Thanks :D:D:D

---

### Post by bobwyajnr on 2011-07-09
> **xavi787 said:**
> ```
xavi@xavi-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 3.3.10524 Compatibility Profile Context

xavi@xavi-pc:~$ 


```

What does that mean? 


The first bit is just giving some X-server info (sorry not too clued up on the nuisances there). I know you can have multiple X-server window manager clients (included networked ones). You can also overlay Window managers on-top of each other on a single display (something I was trying recently actually). Wikipedia would probably be a good place to look this up for more background!!

Anyway so it's not quite as simple as 2 physical monitor setup = Screen: 0 and Screen: 1!!

**OpenGL vendor string: ATI Technologies Inc.** means the proprietary ATI blob drivers have limped into some kind of functionality... You should be able to access the **Catalyst Control Centre** GUI in a normal Gnome/KDE session and be able run:
```
fglxgears
```
for a basic OpenGL pretty rendering test!

I would test some native Linux OpenGL games (e.g. World of Padman, Warsow, etc.) to confirm the drivers are fully functional!! This is a necessary pre-requiste for running any DirectX 9.0c Windows games via Wine.

Bob

---

### Post by xavi787 on 2011-07-09
I have two screens but only one is working.

---

### Post by bobwyajnr on 2011-07-09
> **xavi787 said:**
> I have two screens but only one is working.

Ahhh...

[Referring once again to the linked guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Issues") :) :

> Dual/Multi Monitors

If you have a dual monitor display (also known as "Big Desktop"), use:

```

sudo aticonfig --initial -f
sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"

```

I would probably run those commands in **recovery mode**.


After a reboot...

:P You should see dual-monitor goodness and be able to configure this with the **Catalyst Control Centre**.

:( If things go south in bad way then simply run:
```
sudo aticonfig --initial -f

```
again (from **recovery mode**). Hopefully anyway - otherwise you have an Ubuntu server edition now! :popcorn:

If the ATI driver doesn't behave itself I would start a new forum thread - since you've marked this one as [SOLVED] and help need - dual-monitor support - is different.

Bob

---

