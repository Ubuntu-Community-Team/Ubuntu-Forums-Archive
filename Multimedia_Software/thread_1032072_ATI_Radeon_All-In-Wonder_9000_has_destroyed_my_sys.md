---
title: "ATI Radeon All-In-Wonder 9000 has destroyed my system"
date: 2009-01-06
forum: Multimedia Software
---

### Post by richardcarter on 2009-01-06
Hello,

I have gone through so many linux distributions and something always goes wrong and I have to start all over.  In the past two days, I've gone through Ubuntu 8.10, Kubuntu, and now I'm trying linuxmint KDE 5.0.

My graphics were a bit sluggish and so I tried to install ATI graphics drivers for an ATI-All-In-Wonder 9000 graphics card using the official driver for my model of card from the ATI website. After rebooting I can't load kdm, but instead get a rundown of system processes, starting cupsd, starting sama, starting bluetooth, etc. But then it says "FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko) : No such device.


And then it gets to "running local boot scripts" and stops.

I am so so so sick of setting up my entire system, loading a linux distribution, configuring the desktop and themes to my preferences, getting rid of crap programs I don't want, installing the ones I do want, setting up all of my e-mail preferences and filters and then trying to fix the graphics card (because no graphics card ever seems to work properly by itself on Ubuntu/kubuntu/linuxmint/any other distro, and then having it crash and having to restart the process with the hope that it'll work next time.

I hate windows, I hate MAC, linux is dependable, but is a NIGHTMARE to set up.

Can someone help me?

I'm currently running linuxmint KDE Community Edition 5 on a Dell 4600 Desktop with the following specs:

[http://reviews.cnet.com/desktops/dell-dimension-4600-pentium/4507-3118_7-30529709.html?tag=mncol;rnav]("http://reviews.cnet.com/desktops/dell-dimension-4600-pentium/4507-3118_7-30529709.html?tag=mncol;rnav") except that I opted for an upgraded Radeon All-In-Wonder 9000 graphics card.

Help....Please...

---

### Post by eye208 on 2009-01-06
> **richardcarter said:**
> so I tried to install ATI graphics drivers for an ATI-All-In-Wonder 9000 graphics card using the official driver for my model of card from the ATI website.
Ubuntu already includes the official driver. You don't need to build it yourself.

---

### Post by richardcarter on 2009-01-06
> **eye208 said:**
> Ubuntu already includes the official driver. You don't need to build it yourself.

I would assume that the driver was at least somewhat functioning, since I did have video output and did have the ability to use compiz.  However, whenever I clicked on the ATI radeon control panel thing that comes with this version of linux, it would tell me that I didn't have the proper drivers installed.

Regardless, I can't even start my computer now.  Does linux not have some sort of rollback feature like windows does?

---

### Post by Skripka on 2009-01-06
> **richardcarter said:**
> I would assume that the driver was at least somewhat functioning, since I did have video output and did have the ability to use compiz.  However, whenever I clicked on the ATI radeon control panel thing that comes with this version of linux, it would tell me that I didn't have the proper drivers installed.

Regardless, I can't even start my computer now.  Does linux not have some sort of rollback feature like windows does?


"Can't boot"


Do you mean you cannot even see the BIOS post?  Or the machine isn't even spinning up?  Or GRUB appears but doesn't do anything?.....

---

### Post by richardcarter on 2009-01-06
> **Skripka said:**
> "Can't boot"


Do you mean you cannot even see the BIOS post?  Or the machine isn't even spinning up?  Or GRUB appears but doesn't do anything?.....


The computer goes through bios, then grub, then loads that graphical loading bar where it bounces back and fourth and then fills from left to right.  then instead of loading the visual operating system, it loads a text screen of starting the system processes with things like starting cupsd, starting samba, starting bluetooth, etc. But then it says "FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko) : No such device. 

And it just sits there in that state from there on.

---

### Post by Melcar on 2009-01-06
The drivers will not work with that card.  You need to figure out a way to uninstall them and go back to using the open source drivers.  What I would do is boot into "safe mode" and when dropped to command line mode rebuild X:

```
sudo dpkg-reconfigure xserver-xorg

```
Finish the setup and reboot.

---

### Post by Skripka on 2009-01-06
> **Melcar said:**
> The drivers will not work with that card.  You need to figure out a way to uninstall them and go back to using the open source drivers.  What I would do is boot into "safe mode" and when dropped to command line mode rebuild X:

```
sudo dpkg-reconfigure xserver-xorg

```Finish the setup and reboot.

Or booting and selecting "Recovery Mode" in GRUB--and then "xfix Fix X Server"-should also get one off the problematic driver.

---

### Post by richardcarter on 2009-01-06
> **Melcar said:**
> The drivers will not work with that card.  You need to figure out a way to uninstall them and go back to using the open source drivers.  What I would do is boot into "safe mode" and when dropped to command line mode rebuild X:

```
sudo dpkg-reconfigure xserver-xorg

```
Finish the setup and reboot.

The version of linux I'm using is linuxmint,  which is a modified form of Kubuntu.  When the computer starts, there seems to be no Grub after the bios.  Instead there is a menu that has several options:

Linuxmint Kernal
Linuxmint Kernal (recovery mode)
Linuxmint memtest

and then press f1 for help.

However, the computer won't switch to anything except for linuxmint kernal.  No matter what I press, the down arrow, tab, whatever, it doesn't let me select anything other than linuxmint kernal.  Even the "f1" button does nothing.

Is there some other way to boot into safemode?

---

### Post by Melcar on 2009-01-06
Use recovery mode.  It should just drop you to a command line when it finishes loading.

---

### Post by richardcarter on 2009-01-06
> **richardcarter said:**
> The version of linux I'm using is linuxmint,  which is a modified form of Kubuntu.  When the computer starts, there seems to be no Grub after the bios.  Instead there is a menu that has several options:

Linuxmint Kernal
Linuxmint Kernal (recovery mode)
Linuxmint memtest

and then press f1 for help.

However, the computer won't switch to anything except for linuxmint kernal.  No matter what I press, the down arrow, tab, whatever, it doesn't let me select anything other than linuxmint kernal.  Even the "f1" button does nothing.

Is there some other way to boot into safemode?

And I've tried pressing "esc" and that doesn't work either.

---

### Post by richardcarter on 2009-01-06
> **Melcar said:**
> Use recovery mode.  It should just drop you to a command line when it finishes loading.

It won't let me select the recovery mode option :(  There is no way to toggle to that option.

---

### Post by ubuntu-freak on 2009-01-06
> **richardcarter said:**
> It won't let me select the recovery mode option :(  There is no way to toggle to that option.

 
What happens when you press the down arrow key? I've never heard of this problem before.
 
Also, if you do manage to boot into recovery mode, use the "xfix" command, as the "dpkg-reconfigure" one doesn't affect graphics drivers and screen resolutions anymore.

---

### Post by richardcarter on 2009-01-06
I tried hitting random keys to toggle the selection.  I did something which brought me to a text screen which says:

Ubuntu Based: Linux Mint Elyssa - KDE CD richard-desktop tty1

richard-desktop login:

and when I put in my info, nothing happens. If I put the wrong info, it says "login incorrect" but if I put in the correct info, it just repeats with 

Ubuntu Based: Linux Mint Elyssa - KDE CD richard-desktop tty1

richard-desktop login:

What can I do?

---

### Post by richardcarter on 2009-01-06
> **ubuntu-freak said:**
> What happens when you press the down arrow key? I've never heard of this problem before.
 
Also, if you do manage to boot into recovery mode, use the "xfix" command, as the "dpkg-reconfigure" one doesn't affect graphics drivers and screen resolutions anymore.

The down arrow key does nothing :(

I use a wireless keyboard, which works in my Bios, but maybe the linux screen needs a wired keyboard?  I could try that.

---

### Post by richardcarter on 2009-01-06
> **richardcarter said:**
> The down arrow key does nothing :(

I use a wireless keyboard, which works in my Bios, but maybe the linux screen needs a wired keyboard?  I could try that.

Nope :(


I tried hitting a bunch of random buttons.  Some text about auto correcting errors in the root partition came up and it ran through something then rebooted.  But nothing changed.  Still gets stuck.

---

### Post by richardcarter on 2009-01-06
I used the install disk to boot into the on-disk operating system which allows you to install the os.  Now, using a file manager, I was able to pull up my xconf file, but of course I can't edit it because "root" is the owner.  And I tried cd ing in the terminal to the file, but it won't do it.


Ug.

---

### Post by ubuntu-freak on 2009-01-06
Found two bug reports concerning the arrow keys problem you described:
 
[https://answers.launchpad.net/ubuntu/+question/21336](https://answers.launchpad.net/ubuntu/+question/21336)
 
[https://answers.launchpad.net/ubuntu/+question/435](https://answers.launchpad.net/ubuntu/+question/435)
 
Have you got a PS2 keyboard handy? You may need it if you have to enter BIOS and enable any USB options.

---

### Post by richardcarter on 2009-01-06
> **ubuntu-freak said:**
> Found two bug reports concerning the arrow keys problem you described:
 
[https://answers.launchpad.net/ubuntu/+question/21336](https://answers.launchpad.net/ubuntu/+question/21336)
 
[https://answers.launchpad.net/ubuntu/+question/435](https://answers.launchpad.net/ubuntu/+question/435)
 
Have you got a PS2 keyboard handy? You may need it if you have to enter BIOS and enable any USB options.

Thanks for the reply!

I had to disable a setting in the bios called USB Emulation before because my computer wouldn't boot if my usb printer was plugged in.  I'll first try re-enabling that and see if that works.  If not I'll try the wired keyboard.  Thanks again.

---

### Post by richardcarter on 2009-01-06
> **richardcarter said:**
> Thanks for the reply!

I had to disable a setting in the bios called USB Emulation before because my computer wouldn't boot if my usb printer was plugged in.  I'll first try re-enabling that and see if that works.  If not I'll try the wired keyboard.  Thanks again.

Yay!!

Turning USB Emulation back on, I was able to make selections, including going into recovery mode.  The computer is now trying to fix the x server and I also ran the dpkg program. Hopefully that'll do it!

---

### Post by richardcarter on 2009-01-06
Well, I ran both dpkg and the other x thing and still, not fixed.  Now it boots up, says the same "Starting K Display Manager: kdm"  and starting samba and bluetooth and all that and still says: "FATAL: Error inserting speedstep_centrino: No such device.

And now it says Ubuntu Based: Linux Mint Elyssa - KDE CE richard-desktop tty1

richard-desktop login:

and won't log in.


Now what?

---

### Post by richardcarter on 2009-01-06
Oh, also every now and then,  as I stare at the text screen that does nothing, the screen flickers and I see green vertical bars with an "X" icon in the middle of the screen for a few seconds, then it returns to "running local boot scripts" and does nothing.

---

### Post by NoBugs! on 2009-01-06
It should be editable if you use the editor as root:
```
gksudo gedit
```
then open and edit the file.

---

### Post by richardcarter on 2009-01-06
> **NoBugs! said:**
> It should be editable if you use the editor as root:
```
gksudo gedit
```
then open and edit the file.

I'll try that.  I guess I can just copy and paste the fresh xorg file from the CD to the one on the hard drive?

---

### Post by richardcarter on 2009-01-06
> **NoBugs! said:**
> It should be editable if you use the editor as root:
```
gksudo gedit
```
then open and edit the file.

Nope.  Nothing happens when I type that.

On my laptop with Ubuntu 8.04 it brings up Gedit.

But on the computer with the problems, the desktop, nothing happens.

:(

---

### Post by richardcarter on 2009-01-06
> **richardcarter said:**
> Nope.  Nothing happens when I type that.

On my laptop with Ubuntu 8.04 it brings up Gedit.

But on the computer with the problems, the desktop, nothing happens.

:(

My linux mint system uses the kate editor.  I tried gksudo kate and it brought it up and allowed me to edit the xorg.conf file.  Replaced it with one from the CD, even though I think it was identical already because I'd run the dpkg and x thing already.

Rebooted and nothing happened.  I guess I have to reinstall the entire operating system for the 7th time.  And then reconfigure everything and still end up with a cruddy system with improperly working graphics.  If they could just make the initial set-up more user friendly (and yes I mean with GUI's and not terminals) than I could see linux/ubuntu becoming a mainstream OS.  I've been recommending it to friends for months and most had never heard of it, but I'm not going to do that anymore.  I can't recommend anything, Mac, Windows, or linux.

---

### Post by richardcarter on 2009-01-06
Does anyone have any more advice?  Or advice on how to configure my system better from the beginning?

If I were to buy a new system, what type of hardware should I purchase to make sure I can have the best linux experience possible.  I'm so tired of it being hit or miss.

---

### Post by richardcarter on 2009-01-06
As I was about to reinstall ubuntu, I realized that the hard drive size on the computer is wrong.  Somehow this was changed to about half as big as it really is.  Could this have something to do with my problem?  How do I change it back?

---

### Post by ubuntu-freak on 2009-01-06
If you're gonna buy a new system, I'd recomend one with either an Intel or NVIDIA based graphics device. My Lenovo N500 notebook with an Intel X4500 GPU is working great with Ubuntu.
 
Copying the installation CDs Xorg didn't help because it's all "autodetect" these days. I'm surprised the "xfix" command didn't help though.
 
Also, what did you mean when you said you wanted a quicker way of setting your system up? Mint comes setup multimedia-wise, so I guess you didn't mean in that sense. If you do decide to install vanilla Ubuntu again, set your system up with my [howto](http://ubuntuforums.org/showthread.php?t=766683). All you have to do is copy and paste the relevent commands into the terminal, plus there are some tips you may find useful. 
 
Talking about tips, from now on you should let your OS manage the graphics device driver. due to it's close relationship with the kernel.

---

### Post by richardcarter on 2009-01-07
> **ubuntu-freak said:**
> If you're gonna buy a new system, I'd recomend one with either an Intel or NVIDIA based graphics device. My Lenovo N500 notebook with an Intel X4500 GPU is working great with Ubuntu.
 
Copying the installation CDs Xorg didn't help because it's all "autodetect" these days. I'm surprised the "xfix" command didn't help though.
 
Also, what did you mean when you said you wanted a quicker way of setting your system up? Mint comes setup multimedia-wise, so I guess you didn't mean in that sense. If you do decide to install vanilla Ubuntu again, set your system up with my [howto](http://ubuntuforums.org/showthread.php?t=766683). All you have to do is copy and paste the relevent commands into the terminal, plus there are some tips you may find useful. 
 
Talking about tips, from now on you should let your OS manage the graphics device driver. due to it's close relationship with the kernel.

Thank you for all your input!

My notebook has an Intel GMA 900 graphics card, and it doesn't work very well with Ubuntu 8.04.  It took a lot of configuration to get it where it is, but I still have problems with the colour gradually fading from videos after about five minutes.  Other than that, I'm decently satisfied with the way it operates, aside from random complete lock-ups every now and then, which I think are related to the video card.

What exactly do I type to run the "xfix" command?  I believe I ran it, but I want to try one last time making sure I typed it correctly.

And now, why would my hard drive show the wrong drive size?  I went to reinstall the operating system, and it tells me my hard drive is half the size that it actually is.  This isn't good.

---

### Post by ubuntu-freak on 2009-01-07
You just boot into recovery mode, type "xfix" and execute.
 
I've no idea why your hard drive appears smaller - it should show every single partition on the drive.

---

