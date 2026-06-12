---
title: "3D acceleration in VBox?"
date: 2010-12-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by drfox on 2010-12-02
I've installed Natty in Virtual Box.
I have a GeForce 7150M video card, and Compiz runs fine on my Maverick OS. 
Although I've enabled 3D graphics in the VBox setup, when I go to Appearances and try to check "Normal," I get a message that I don't have 3D hardware. How do I get my Natty running in VBox to recognize and use my Nvidia card? Is it possible?
Larry

---

### Post by cariboo on 2010-12-03
You should be able to use the Classic Desktop in Vbox, but I wouldn't hold out much hope to run Unity in the current version.

---

### Post by twigusa on 2010-12-03
Somebody in another thread pointed to this bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/675307](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/675307)

which looks like there needs to be an update to Virtualbox itself for Unity to work.

Cheers,
Twig.

---

### Post by cariboo on 2010-12-03
The latest release versions usually don't work in Vbox, we'll have to wait for Oracle to come up with a solution.

---

### Post by endotherm on 2010-12-03
ubuntu/compiz don't/aren't able to use the vbox graphics driver. I think I had compiz working with a very old vbox and jaunty, but haven't had it with Karmic, Lucid, or Maverick using the vbox tools driver. no, you cannot access your hardware card directly. virtualized hardware has to remain...well... virtual.

---

### Post by jocko on 2010-12-03
> **endotherm said:**
> ubuntu/compiz don't/aren't able to use the vbox graphics driver. I think I had compiz working with a very old vbox and jaunty, but haven't had it with Karmic, Lucid, or Maverick using the vbox tools driver. no, you cannot access your hardware card directly. virtualized hardware has to remain...well... virtual.
Not true actually. 3d acceleration works quite well in virtualbox. Just install virtualbox-ose-guest-dkms, virtualbox-guest-utils and virtualbox-ose-guest-x11 to get it working in the natty guest (but the guest additions that comes with the non-ose version does not work with the natty kernel yet).
And compiz works very well too. It's just that compiz crashes when the unity plugin is activated...

---

### Post by schubi42 on 2010-12-04
> **jocko said:**
> Not true actually. 3d acceleration works quite well in virtualbox. Just install virtualbox-ose-guest-dkms, virtualbox-guest-utils and virtualbox-ose-guest-x11 to get it working in the natty guest (but the guest additions that comes with the non-ose version does not work with the natty kernel yet).
And compiz works very well too. It's just that compiz crashes when the unity plugin is activated...

Hi, so what if I'm running the non-OSE and have already installed the VBox additions? Uninstall them, install the packages from the ubuntu repositories or is the non-OSE not the way to go for testing unity and other 3d stuff on the natty narwhal?

---

### Post by cariboo on 2010-12-05
> It's just that compiz crashes when the unity plugin is activated...

Check the bit I quoted. You aren't going to be able to run Unity in Vbox, until Oracle fixes it. 

Unity needs a modified version of compiz specially create for it.

---

### Post by madjr on 2010-12-06
Oracle fixing stuff? for us? hmmm..

I wouldn't hold my breath...

The best thing the OP can do is get an usb thumb drive and install unity there.

---

### Post by bvidinli on 2010-12-07
virtualbox-ose-guest-dkms, virtualbox-guest-utils and virtualbox-ose-guest-x11

these can also be installed on non-ose virtualbox.

I tested on virtualbox 3.2.12, and guest additions 3.2.12,
installed natty, 
after login, no "3d" error displayed, however, nothing (no windows manager, unity or metacity) is loaded.

in this situation,
right click, add a launcher, 
you may add launcher for "gnome-terminal", metacity, gnome-desktop
clicking last two turns your desktop into normal ubuntu desktop after adding them as icon.

now, i am updateding natty, and will see if it will work.

---

### Post by cariboo on 2010-12-07
@bvidinli, you can run the Classic Desktop with no problems, but Unity won't run.

---

### Post by bvidinli on 2010-12-08
please anybody update this, for ways to run ubuntu natty/unity on virtualbox,
or
run natty in some other virtual machine, someother way. 

i will try to test natty if i can find a real computer other than I use.

---

### Post by cariboo on 2010-12-08
The problem is with VirtualBox, we'll have to wait for them to solve the problem.

---

### Post by xixx on 2010-12-11
Well, 3d acceleration works if guest additions from vbox 3.2.8 installed. If I'm installing guest additions later then 3.2.8, then 3d is not working. Seemless mode is working fine too. So, now I have vbox 3.2.12 with guest additions 3.2.8. (Host is ubuntu 10.10 x64 and guest is ubuntu 9.10 x32)

---

### Post by bvidinli on 2010-12-11
[http://download.virtualbox.org/virtualbox/3.2.8/VBoxGuestAdditions_3.2.8.iso](http://download.virtualbox.org/virtualbox/3.2.8/VBoxGuestAdditions_3.2.8.iso)

i downloaded, installed, 
but same error (no 3d support)
i checked that, the 3d support in machine display properties is enabled.
any idea ?

---

### Post by Merk42 on 2010-12-11
3D Support usually breaks during the alpha/beta of ANY Ubuntu release.  As Natty is still in development, it is not officially supported by Virtualbox, thus getting 3D support in it is not a priority for Oracle (nor was it for Sun, so don't get all into Oracle hate).

---

### Post by CanisSolaris on 2010-12-22
Oracle just released VirtualBox v4, which, in the changelog, includes:

*3D support: fixed Unity/Compiz crashes on natty*

[http://www.virtualbox.org/wiki/Changelog]("http://www.virtualbox.org/wiki/Changelog")

Am upgrading now, will let you know what happens...

---

### Post by CanisSolaris on 2010-12-22
> **CanisSolaris said:**
> Oracle just released VirtualBox v4, which, in the changelog, includes:

*3D support: fixed Unity/Compiz crashes on natty*

[http://www.virtualbox.org/wiki/Changelog]("http://www.virtualbox.org/wiki/Changelog")

Am upgrading now, will let you know what happens...

Okay, installed VirtualBox 4.0.0 for Windows as host, installed Natty as guest, installed Guest Additions from VirtualBox Devices menu, and now have Unity running...



Cheers!

---

### Post by cariboo on 2010-12-22
It must be Windows only, as I just installed it on Natty, vbox doesn't crash any more, but Unity still won't run.

---

### Post by Merk42 on 2010-12-22
> **cariboo907 said:**
> It must be Windows only, as I just installed it on Natty, vbox doesn't crash any more, but Unity still won't run.

Maverick Host, Natty Guest, worked for me.

---

### Post by cariboo on 2010-12-22
I had a huge problem updating the natty vm, it caused a kernel panic on the host, complete with flashing keyboard lights, I even had to reseat the sata cable on the hard drive, as it stopped showing up in the bios.

---

### Post by nperry on 2010-12-23
Hello Guys,

I've seen a lot of threads in the last couple of days asking about 3d support in VBox.

Today VirtualBox 4.0 was released, after checking the changelog[1] it shows that the bug about 3d support with unity in natty has been fixed.

So Yeah, get it here [2]

Go enjoy Unity in Virtualbox.

Thanks

Neil

[1] - [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)
[2] - [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by nperry on 2010-12-23
Please see [http://ubuntuforums.org/showthread.php?p=10271445](http://ubuntuforums.org/showthread.php?p=10271445)

Virtualbox 4.0 was released this morning, with the 3d support now fixed for unity/natty.

---

### Post by cariboo on 2010-12-23
No need for two vbox threads, merged.

---

### Post by drfox on 2010-12-23
I have VBox 4 installed, along with the extensions. 
If I look at the Session information, this is what I have configured:
System Base Memory: 1068 MB
Processor(s): 1
Boot Order: CD/DVD-ROM, Hard Disk
VT-x/AMD-V: Enabled
Nested Paging: Enabled
Display Video Memory: 128 MB
3D Acceleration: Enabled
2D Video Acceleration: Disabled
Remote Desktop Server: Disabled


And this is what happens at runtime:
Runtime Attributes
Screen Resolution 800x600x32&#65532;
VT-x/AMD-V  Disabled&#65532;
Nested Paging  Disabled&#65532;

Why is the VT-x/AMD-V being disabled?

---

### Post by loukingjr on 2010-12-24
I am running VB4.0 and Unity, at least for me only partially works. It doesn't look like it's quite drawn correctly and seems fairly slow. But I am not sure I have a good install either. I re-downloaded the original alpha .iso from Dec 2 I think then updated everything using update manager. Maybe I should of tried the daily build?

I am also having issues with applets needing reloaded at every boot. should I try the daily build or is this all normal since it's in alpha?

thanks.

---

### Post by cariboo on 2010-12-24
The applets needing reloading happens on my netbook when I reboot, coming out of hibernate they work the way they should.

---

### Post by loukingjr on 2010-12-24
> **cariboo907 said:**
> The applets needing reloading happens on my netbook when I reboot, coming out of hibernate they work the way they should.

ok thanks

---

### Post by cornflake000 on 2010-12-25
I have had no difference with the Vbox4 over the ose.  Same thing.  Doesn't recognize 3d or unity.  I only get 600x800 resolution and that's all folks!

---

### Post by cariboo on 2010-12-25
> **cornflake000 said:**
> I have had no difference with the Vbox4 over the ose.  Same thing.  Doesn't recognize 3d or unity.  I only get 600x800 resolution and that's all folks!

Is that with the guest additions installed? I got 1024X768 without doing any tweaking.

---

### Post by cornflake000 on 2010-12-25
The OSE version had guest additions installed and it still had crumby resolution.  Other OS's on that Vbox work just fine, DSL, Parsix, XP... but 4.0 doesn't seem to need them or at least I didn't see a new version.  The old guest additions are definitely not compatible with 4.0 in any case.  One thing I've been thinking is that I am using the same .vdi files I was using for the ose version which are getting a warning about an ext4 partition conflict.  I'm not sure that has anything to do with it but it sure wouldn't hurt to reinstall on a new virtual drive and see what happens.

---

### Post by dino99 on 2010-12-25
with Oracle v4:

- need to remove/purge the previous vbox
- there is no more OSE now
- you need to install the new guest additions
- download & install additional features

---

### Post by cornflake000 on 2010-12-25
Ahhh.. me stupid!  I have to reacquaint myself with vbox; it's been a long time since I've used it.  I should have known it should be purged, no shortcuts.  Last time I used it you had to download the guest adds separately.. that sort of dates it.  

Sorry to hold things up.  I'm reinstalling as I write.  New .vdi, the works.

>>> Update: Works like a dream... thanks.  Now I can critique Unity!!! ;)

---

### Post by MacUntu on 2010-12-25
Where do I get those Guest Additions for virtualbox-4.0?

---

### Post by cornflake000 on 2010-12-25
They come with the installation under /usr/share/virtualbox

---

### Post by MacUntu on 2010-12-25
Great, thanks. Another question: I have four cores (dual core + HT) and virtualbox-4.0 uses all of them, but combined never seems to consume more than 100% (1 total core) - is that normal?

Ah, with Guest Additions it's using more than 100%. :)

[[img]http://img.xrmb2.net/533594.jpg[/img]](http://img.xrmb2.net/images/533594.png)

---

### Post by Mr. Picklesworth on 2010-12-25
> **cornflake000 said:**
> I have had no difference with the Vbox4 over the ose.  Same thing.  Doesn't recognize 3d or unity.  I only get 600x800 resolution and that's all folks!

You need to install the guest additions using VirtualBox. That's with Install Guest Additions from the virtual machine's Devices menu. It'll mount a CD in the VM and then there is a script in there to do the installation. (Run the script from a terminal).

The guest additions package in Natty's repository won't work for this since it's still from the last version of VirtualBox ;)

---

### Post by loukingjr on 2010-12-26
> **cornflake000 said:**
> I have had no difference with the Vbox4 over the ose.  Same thing.  Doesn't recognize 3d or unity.  I only get 600x800 resolution and that's all folks!

hmm, I get 1440x900 in both gnome & unity, compiz works in gnome and as I stated earlier, Unity is a little iffy. You do need VB 4.0 guest additions installed. and it's a pain to get 4.0 additions installed on some guests that already   had additions.

---

### Post by loukingjr on 2010-12-26
I'm not sure what's wrong but, this is what I get running VB 4.0 and Unity...
[IMG]http://lh6.ggpht.com/_sA9c938TUEU/TRcTmM5Wh0I/AAAAAAAAFIQ/w5CFT7Vt5-0/s720/screenshot_01.jpg[/IMG]
the text is garbled as you can see when I mouse over the left panel. the top panel doesn't draw correctly and icons come and go. I opened a panel on the bottom so I could easily see what I was doing.

Edit:: btw, it did the exact same thing with the default theme n background, icons etc.

---

### Post by MacUntu on 2010-12-26
Open a terminal, run```
(compiz --replace &)
``` wait, close the terminal, and try again.

---

### Post by loukingjr on 2010-12-26
> **MacUntu said:**
> Open a terminal, run```
(compiz --replace &)
``` wait, close the terminal, and try again.

I assumed that the parentheses were not to be included. all that did it seems was to restart compiz then lock up the terminal and move it to the left top corner of the screen. There were a number of error messages in the terminal but I couldn't copy them seeing it was locked up.

---

### Post by loukingjr on 2010-12-26
Hmmm, I had done a fresh install of today's daily build and it seems worse than it was when I just updated 550+ packages after installing the dec 2 release.

[IMG]http://lh3.ggpht.com/_sA9c938TUEU/TRcp7S169ZI/AAAAAAAAFIY/DkmkvR-J-Vc/s720/screenshot_04.jpg[/IMG]
[IMG]http://lh5.ggpht.com/_sA9c938TUEU/TRcqtROIz-I/AAAAAAAAFIc/jQOvwEQ2qTE/s720/screenshot_03.jpg[/IMG]

---

### Post by shafin on 2010-12-26
> **loukingjr said:**
> I'm not sure what's wrong but, this is what I get running VB 4.0 and Unity...
[IMG]http://lh6.ggpht.com/_sA9c938TUEU/TRcTmM5Wh0I/AAAAAAAAFIQ/w5CFT7Vt5-0/s720/screenshot_01.jpg[/IMG]
the text is garbled as you can see when I mouse over the left panel. the top panel doesn't draw correctly and icons come and go. I opened a panel on the bottom so I could easily see what I was doing.

Edit:: btw, it did the exact same thing with the default theme n background, icons etc.
What's the amount of video memory in this virtual machine?

---

### Post by cornflake000 on 2010-12-26
> **Mr. Picklesworth said:**
> You need to install the guest additions using VirtualBox. That's with Install Guest Additions from the virtual machine's Devices menu. 

That doesn't always work for some reason.  I have to mount the guest additions iso in the actual folder /usr/share/virtualbox for them to install.  The link in the machine devices menu does nothing.  I've read of others with the same problem.

---

### Post by loukingjr on 2010-12-26
> **shafin said:**
> what's the amount of video memory in this virtual machine?

64mb

---

### Post by exploder on 2010-12-27
Thanks to this thread, I now have the Unity desktop working in Virtualbox 4.

Thanks!

---

### Post by KdotJ on 2010-12-27
So unity will work under virtualbox 4? Out of the box or is there tweaks to be made?

---

### Post by Merk42 on 2010-12-27
> **KdotJ said:**
> So unity will work under virtualbox 4? Out of the box or is there tweaks to be made?As of right now, out of the box. The only 'tweak' is that you need to install the Virtualbox additions, but you should be doing that on any installation of any OS anyway.

---

### Post by loukingjr on 2010-12-27
I'm curious what hosts people are using to run Unity in VirtualBox 4 because it sure wasn't working correctly on mine.

---

### Post by Quadunit404 on 2010-12-27
I'm about to try out Unity in VirtualBox right now. I'll see how far I can get with it.

I have this strong feeling I am not going to like Unity :|

---

### Post by cariboo on 2010-12-27
> **loukingjr said:**
> I'm curious what hosts people are using to run Unity in VirtualBox 4 because it sure wasn't working correctly on mine.

I'm running it on Natty, make sure you have 3D enabled under Display. I have the Display memory set at 32Mb, but I'm not sure if it's really needed.

**Edit**: I just set the display memory to 12Mb, Unity seems to run OK.

---

### Post by loukingjr on 2010-12-27
> **cariboo907 said:**
> I'm running it on Natty, make sure you have 3D enabled under Display. I have the Display memory set at 32Mb, but I'm not sure if it's really needed.

**Edit**: I just set the display memory to 12Mb, Unity seems to run OK.

wait I'm lost. I was wondering if anyone is running unity/natty/ubuntu 11.04 as a guest IN VirtualBox 4 and what host/hardware they are using it on. I have a feeling either it won't run in the Mac version of VB or my particular Mac, which is an iMac 5,1 with an ATI Radeon chipset.

---

### Post by cariboo on 2010-12-27
I'm running Natty in vbox with Natty on the host system too. :) For hardware, I'm running  a AMD x2 3800+ with 2Gb ram and an nVidia 9400GT video card..

---

### Post by Merk42 on 2010-12-27
Personally I'm running on a 10.10 host with a nVidia GeForce 7600 card

---

### Post by Quadunit404 on 2010-12-27
I tried Unity in VBox. It was slow (not VERY slow, but still slow) and crashed frequently (e.g. when I was trying to unpin Firefox from the Launcher it crashed, when trying to bring up the Applications window it crashed) but this is an alpha release I used so yeah, I guess I should expect crashes.

Before you ask, my card is a NVIDIA GT 330M.

---

### Post by loukingjr on 2010-12-27
Well hopefully someone running VirtualBox on a Mac will respond :D

---

### Post by loukingjr on 2010-12-28
well this was interesting. since I have Windows 7 running in bootcamp I thought I would try the Window's version of VB 4.0 and Natty. Turns out it runs better in Windows 7 than it does on my iMac. apparently the video drivers for bootcamp are newer than the ones in my firmware.

I guess I need a new iMac.

p.s. I installed yesterday's daily build and although it ran and looked MUCH better, the text in the top panel looked too large for it, condensed, and was cut off slightly on the bottom. maybe by the time 11.04 is released I will have the aforementioned iMac. :D

---

### Post by lsmobrian on 2010-12-30
On an iMac 9,1 GeForce 9400

Gave natty a shot after upgrading virtualbox, installed the the guest additions... and there's unity.  Seems a lot more stable than when I briefly tried maverick on my netbook

---

### Post by loukingjr on 2010-12-30
> **lsmobrian said:**
> On an iMac 9,1 GeForce 9400

Gave natty a shot after upgrading virtualbox, installed the the guest additions... and there's unity.  Seems a lot more stable than when I briefly tried maverick on my netbook
I'm on an iMac 5,1. I'm guessing that's my problem.

---

