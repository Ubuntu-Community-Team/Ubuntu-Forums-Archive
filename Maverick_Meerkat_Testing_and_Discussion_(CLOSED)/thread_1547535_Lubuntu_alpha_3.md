---
title: "Lubuntu alpha 3"
date: 2010-08-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-08-06
Hello fellow testers,

fairly hot off the press (I've just updated the wiki pages) [ Lubuntu Development](https://wiki.ubuntu.com/Lubuntu/Developers) has just been released, as with all Maverick, it's not a finished product yet. :p

All the details of downloading / known issues etc. are available from there. Please take the time to read the page on the [ alpha 3](https://wiki.ubuntu.com/Lubuntu/Developers/Maverick%20alpha%203) for where the team is up to.

Regards,

Phill.

---

### Post by uRock on 2010-08-06
I'll take it for a spin.

---

### Post by ranch hand on 2010-08-06
Oh boy, oh boy.  A new toy.

The bugger seems to be coming along very nicely.  I do not like chromium but that is such hard thing to change that even I can do it.

Just had a 403 error when trying to update/upgrade on current install anyway so I may as well just install the bugger and see how the new image works.

Have to back up some changes I made first.  I modified the blue to green on the GDM and wallpaper and some other little things.  Have to get on it.

Thanks for the notice.

---

### Post by andrewabc on 2010-08-06
> **ranch hand said:**
> Oh boy, oh boy.  A new toy.

The bugger seems to be coming along very nicely.  I do not like chromium but that is such hard thing to change that even I can do it.


I have chromium daily on ubuntu 9.10
It runs fast, even after it imported my firefox stuff. Now that chromium has proper adblock, I don't mind using it. I still use firefox for 99% of stuff, but chromium for certain things to test runs much faster.

Which version of chromium is going to be released with lubuntu 10.10?
There seems to be a lot of different versions of chrome/chromium 4.x, 5.x, and the dailies are 6.x. Not sure which is latest stable version.

EDIT:
I think 6.x is latest stable.

---

### Post by ranch hand on 2010-08-06
My problem has to do only with me.  I feel about google about the way I do about MS.  I just don't like to use their stuff so I do not.  I am sure that it works fine.  Have no idea about the version number.  Probably the one in the 10.10 repo.

---

### Post by teh603 on 2010-08-06
Supposedly, Chromium =/= Chrome. Chrome is by Google, Chromium is what Chrome is based on.

Or so I read here back during the Lucid test cycle somewhere around Beta 1.

---

### Post by ranch hand on 2010-08-07
Don't like the smell of it.  Like I said, it i just me.

---

### Post by kansasnoob on 2010-08-07
Thanks for the info, I'll have to give this a look :)

I was quite impressed with Lubuntu 10.04.

---

### Post by ronacc on 2010-08-07
I've got the .iso d/l'd I'll install later today in place of my sabayon install that committed suicide ( portage stikes again ):P

---

### Post by plun on 2010-08-07
> **ronacc said:**
> I've got the .iso d/l'd I'll install later today in place of my sabayon install that committed suicide ( portage stikes again ):P

Why install it from an iso.......??

Just to install the lubuntu-desktop meta package and use it as an extra desktop.

Works just great with Ubuntu and Gnome !.....):P

---

### Post by ranch hand on 2010-08-07
> **plun said:**
> Why install it from an iso.......??

Just to install the lubuntu-desktop meta package and use it as an extra desktop.

Works just great with Ubuntu and Gnome !.....):P
Just testing the ISO itself is important.  There are few folks that test the Ubuntu official ISOs in ISO testing.  Lubuntu needs all the help it can get in all areas of testing.

---

### Post by plun on 2010-08-07
> **ranch hand said:**
> Just testing the ISO itself is important.  There are few folks that test the Ubuntu official ISOs in ISO testing.  Lubuntu needs all the help it can get in all areas of testing.

Well... most users runs Ubuntu and its really easy to just install lubuntu-desktop and log out and change desktop-session.

It's a great extra desktop.....;)


(of course the iso must be tested)

---

### Post by ronacc on 2010-08-07
@ plun   I,ve already done what you suggest as far as adding it as a session to my main install but I figgured I'd test the install process also since the drive I'm going to use has a brain dead install on it now .and that drive is where my default grub is , so I'll give ubiquity a chance to screw up big time and loose all 6 installs

---

### Post by plun on 2010-08-07
> **ronacc said:**
> @ plun   I,ve already done what you suggest as far as adding it as a session to my main install but I figgured I'd test the install process also since the drive I'm going to use has a brain dead install on it now .and that drive is where my default grub is , so I'll give ubiquity a chance to screw up big time and loose all 6 installs

OK.... have fun...:D

---

### Post by 23dornot23d on 2010-08-07
> **ronacc said:**
> @ plun   I,ve already done what you suggest as far as adding it as a session to my main install but I figgured I'd test the install process also since the drive I'm going to use has a brain dead install on it now .and that drive is where my default grub is , so I'll give ubiquity a chance to screw up big time and loose all 6 installs

I created a USB pen drive with a version of Linux on it so that I always have a way of booting the other systems up ....... 
I used Burg ,,,,, and it works well for what I want, [following this thread]("http://ubuntuforums.org/showthread.php?t=1545550")
it may be of use to you ! 
(You could run the bootscript file to keep a record of all the bootinfo too)

---

### Post by ranch hand on 2010-08-07
> **ronacc said:**
> @ plun   I,ve already done what you suggest as far as adding it as a session to my main install but I figgured I'd test the install process also since the drive I'm going to use has a brain dead install on it now .and that drive is where my default grub is , so I'll give ubiquity a chance to screw up big time and loose all 6 installs
I installed it over my A1 that was up to date but getting in ugly temper.  Grub actually worked quite nicely.

On Ubuntu installs I always just modify grub and update it from the Live Session.  Couldn't get Pcmanfm to work right as root user so had to go with the default.

---

### Post by ronacc on 2010-08-07
actualy what I do is put each install on its own drive (not partition) and put its grub on that drive and just switch boot order in bios to select which is first so the risk of total disaster is small and I keep a supergrub disk handy too and heck its a test box anyway , I don't do this on my work box .

---

### Post by cariboo on 2010-08-07
I have a disk with 4 different installations, the only install I had a problem with was PCLinuxOS 2010, because it still uses grub-legacy, it wouldn't detect the Kubuntu and Maverick installation. The last version I installed was a Lucid based version of XBMC, grub2 detected the other installs, including XP, but the default labels leave something to be desired.

To get back on topic, once I've set up XBMC to my liking, I'll give Lubuntu a try. The current version of XMBC I'm using on my media center pc, was based on the mini.iso with lxde meta package installed.

---

### Post by jerrylamos on 2010-08-07
I've got a pile of partitions here.  Using whichever Ubuntu or Lubuntu was last installed, I do an /etc/grub.d/06_custom as suggested by Ranch Hand to make sense out of the mess.  Then do an update-grub.  Check /boot/grub/grub.cfg to verify it got the 06_custom files first followed by whatever update-grub was able to figure out from the partitions.

06_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above
menuentry "Meerkat A3 on sda12" {
set root=(hd0,12)
linux /vmlinuz root=/dev/sda12 ro quiet
initrd /initrd.img
}
menuentry "Lubuntu Meerkat A3 on sda10" {
set root=(hd0,10)
linux /vmlinuz root=/dev/sda10 ro quiet
initrd /initrd.img
}
menuentry "Meerkat A2 on sda16" {
set root=(hd0,16)
linux /vmlinuz root=/dev/sda16 ro quiet
initrd /initrd.img
}
menuentry "Meerkat A1 on sda13" {
set root=(hd0,13)
linux /vmlinuz root=/dev/sda13 ro i915.modeset=0 quiet
initrd /initrd.img
}
menuentry "Debian Live on /dev/sda8" {
set root='(hd0,8)'
linux /live/vmlinuz boot=live root=/dev/ram ramdisk_size=524388 rw quiet
initrd /live/initrd.img
}
menuentry "lubuntu Meerkat A2 Live on sda9" {
set root=(hd0,9)
linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=524388 rw quiet
initrd /casper/initrd.lz
}
menuentry "Lubuntu Lucid on sda7" {
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro quiet
initrd /initrd.img
}
menuentry "Lubuntu Lucid Live on /dev/sda17" {
set root='(hd0,17)'
linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=524388 rw quiet i915.modeset=0
initrd /casper/initrd.lz
}
menuentry "Karmic 1st on sda3" {
set root=(hd0,3)
linux /vmlinuz root=/dev/sda3 ro quiet
initrd /initrd.img
}
menuentry "Karmic on sda5" {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet
initrd /initrd.img
}
menuentry "Karmic on sda6" {
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro quiet
initrd /initrd.img
}
menuentry "slitaz-cooking live persistent on /dev/sda14" {
set root='(hd0,14)'
linux /boot/vmlinuz-2.6.30.6-slitaz root=/dev/sda14 home=/dev/sda14 rw quiet
initrd /boot/rootfs.gz
}
menuentry "slitaz on /dev/sda15" {
set root=(hd0,15)
linux /boot/vmlinuz-2.6.30.6-slitaz root=/dev/sda15 home=/dev/sda15 rw quiet
initrd /boot/rootfs.gz 

Have fun, Jerry

---

### Post by jerrylamos on 2010-08-07
Oh, this is intel video graphics i845G running Lubuntu Maverick A3.  Seems every time the people working on the intel driver, and get it running, someone makes a change in the linux kernel and everything goes blank screen.  For the last 2 years.  KMS is really iffy on this, and on Maverick A3 ati radeon mobility 7500 for that matter.  Yes there are launchpad bug entries.

Lubuntu Maverick A3 installed O.K. from the CD using the "try before you install" option.  It does get a lot of xorg crashes which apport reporting can't handle but the system keeps right on running.  I have the same crashes on Maverick A3.  The initial screen Lubuntu Maverick A3 "Install..." booted to blank screen no matter what.

Maverick A3 on the other hand won't boot the "Try before you install" CD but will do the "Install..." option.  Go figure.

Anyway they're both installed and running.

Jerry

---

### Post by ronacc on 2010-08-07
installed lubuntu A3 , the disk check showed errors on 2 files but I went ahead and installed it anyway ( I was feeling lucky ) . The install went ok and ubiquity found and added all of my other installs ok for a change and it didn't even argue about being told to install grub to the mbr of sdd .

---

### Post by ranch hand on 2010-08-07
Grub2 is a lot like a green broke horse.  Takes a while to get it to settle down.  I think they are getting it smoothed up nicely.  Be ready for parades in town before you know it.

---

### Post by phillw on 2010-08-08
> **ronacc said:**
> installed lubuntu A3 , the disk check showed errors on 2 files but I went ahead and installed it anyway ( I was feeling lucky ) It's a known bug, testing the iso and CD still needs doing manually. 
[Testing 10.10](https://wiki.ubuntu.com/Lubuntu/Developers#General Testing)
Thanks everyone for testing :D

Regards,

Phill.

---

### Post by ronacc on 2010-08-08
if the live cd boots and runs that the only real test .

---

### Post by ronacc on 2010-08-08
well that was interesting , unfortunately I'll have to remove it due to no 64bit ISO and I refuse to run I386 on a 64bit box .

---

### Post by phillw on 2010-08-08
> **ronacc said:**
> well that was interesting , unfortunately I'll have to remove it due to no 64bit ISO and I refuse to run I386 on a 64bit box .

Thanks for giving it a whirl, 64Bit is not a priority for lubuntu as it is primarily designed for lower specification computers. When it is released a 64Bit core will be available via the [minimal installation method](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall).

Regards,
Phill.

---

### Post by phillw on 2010-08-08
> **ranch hand said:**
> 

Just had a 403 error when trying to update/upgrade on current install anyway so I may as well just install the bugger and see how the new image works....

There was a problem with the a2 and updating, it has been rectified. If anyone still needs the work-round it is
> === Missing key for lubuntu ppa ===
When you update lubuntu it will error out saying that the key is missing. 
 1. Take a note of the key.  Use [ Key Servers](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Key%20Servers) to get the key.
 2. Remove the lubntu-ppa from sources using Software Sources (Preferences --> Sortware Sources).
 3. Add the lubuntu-ppa back on ```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
exit

```
Regards,
Phill.

---

### Post by ronacc on 2010-08-08
I'll give it a try on my netbook , my only concession to 32bit since AMD first brought out the athalon 64 .

---

### Post by ranch hand on 2010-08-08
The only time I had it was the day you posted the A3 notice.  My work around was to reinstall with A3.

Haven't had time to really fool with it yet but it looked pretty good.

Pcmanfm did not want to work right as root.  Had to come back here and use nautilus to edit grub to my liking.  Now, I really like nautilus but pcmanfm is next on the list and I would rather use it when working with Lubuntu.  That was a real bummer.  It was the same on the Live Session.

---

### Post by ranch hand on 2010-08-08
> **ronacc said:**
> I'll give it a try on my netbook , my only concession to 32bit since AMD first brought out the athalon 64 .
Geeze, I thought I was hardcore on 64 bit stuff.

---

### Post by xebian on 2010-08-08
I'm running a 64-bit right now as a VBox host.  Used the netboot to install and then added lxde-core, lxde-common, lxdm, lubuntu-artwork, lubuntu-default-settings. Then add your fav apps as you wish.

---

### Post by phillw on 2010-08-08
> **xebian said:**
> I'm running a 64-bit right now as a VBox host.  Used the netboot to install and then added lxde-core, lxde-common, lxdm, lubuntu-artwork, lubuntu-default-settings. Then add your fav apps as you wish.

Adding the lubuntu meta package would possibly be easier?

I'll go ask if the 10.10 meta package is available.

Regards,
Phill.

---

### Post by phillw on 2010-08-08
> **xebian said:**
> I'm running a 64-bit right now as a VBox host.  Used the netboot to install and then added lxde-core, lxde-common, lxdm, lubuntu-artwork, lubuntu-default-settings. Then add your fav apps as you wish.

Adding the lubuntu desktop package would possibly be easier?

If you install the 10.10 Maverick minimal (net boot) iso, you can add the lubuntu-desktop to it.
E.g.
[32 Bit minimal](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/)
[64 Bit minimal](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-amd64/current/images/netboot/)

The instructions at [Minimal Installtion](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall) should be fairly straight forward (it also contains work arounds for [Network Manager bug](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=530024)).

With 10.10 there is a 'stripped down' version of lubuntu avaialable
> A new meta-package (lubuntu-core) is available to install only core packages of Lubuntu. For those of you who prefer your lubuntu "low-fat" :-D

Regards,

Phill.
P.S. Gee, you are all keeping me on my toes and ensuring the wiki area is all up to date :-)

---

### Post by 23dornot23d on 2010-08-08
Should[  Cairo-dock]("http://i37.tinypic.com/x4j7l2.jpg")__ work in glx mode .... in lubuntu. [lxde background]("http://i38.tinypic.com/6ypg1e.jpg") is nice

It seems to work ok .... just the graphics are in a block ..... 

its as if there's no glx mode ..or  no opengl ....

also pressing F13 does not do a screenshot .... not sure if this is meant to work or not in Lubuntu

My Paint .... cannot get a line to show up yet .... tried all the colors and all the brushes ....
(might be my setup of this .... but could somebody else check it out please)

( I Must admit its ever so fast for loading the 3D applications ... Blender k3dsurf wings3d )

Not too keen on the large graphics icons being right up at the top on the desktop
a double click when closing a window often sets a program running .... 
due to accidentally  clicking the icon behind the window
that you are closing ..... starts a new program running .... 
* if the large desktop icons were just slightly lower down this could be avoided .....

---

### Post by jerrylamos on 2010-08-08
> **ronacc said:**
> if the live cd boots and runs that the only real test .

Well, Maverick A3 CD Live didn't boot.  The second boot option, Install, did.  i386 with intel i845G.

Now Lubuntu Maverick A3 (LXDE in place of Gnome, Chromium in place of Firefox) was the opposite.  CD Live ran and installed.  Second boot option Install went black.

Go figure.

Jerry

---

### Post by ronacc on 2010-08-08
> **jerrylamos said:**
> Well, Maverick A3 CD Live didn't boot.  The second boot option, Install, did.  i386 with intel i845G.

Now Lubuntu Maverick A3 (LXDE in place of Gnome, Chromium in place of Firefox) was the opposite.  CD Live ran and installed.  Second boot option Install went black.

Go figure.

Jerry

Yeah now that you mention it I have run into that situation on occasion and the reverse , where install wouldn't work from the menu but would from the live session . Like you said        "Go figure."

---

### Post by jerrylamos on 2010-08-09
> **plun said:**
> Why install it from an iso.......??

Just to install the lubuntu-desktop meta package and use it as an extra desktop.

I and many others on Maverick are looking for bugs.  Install from .iso is a fertile ground for bugs on Ubuntu so I test that.

Usually I've got a partition updated to supposed Maverick 3 and also a Maverick 3 .iso install.  Among other things the updated version occupies more disk space, and of course I had some problems with install (launchpad updated).

Jerry

---

### Post by phillw on 2010-08-10
> **23dornot23d said:**
> ....
also pressing F13 does not do a screenshot .... not sure if this is meant to work or not in Lubuntu....

What's an F13 key? :p It is Fn+PrtSc in lubuntu, that will place the screen-shot into your home directory as something named like```
2010-08-05-220521_1280x800_scrot.png
``` (Date, time and screen resolution). You *should* be able to make a key binding for f13=Fn+PrtSc but you'd need to ask on the mailing channel :D
> 
Not too keen on the large graphics icons being right up at the top on the desktop
a double click when closing a window often sets a program running .... 
due to accidentally  clicking the icon behind the window
that you are closing ..... starts a new program running .... 
* if the large desktop icons were just slightly lower down this could be avoided .....

I've copied that to the mailing list.

Regards,

Phill.
P.S. Thanks for the input.

---

### Post by 23dornot23d on 2010-08-10
Thanks Phillw ..... 

The [screenshots]("http://i37.tinypic.com/v4awrt.jpg") are working and going in my home directory ..... 

I did not realise they were there ......  
(as nothing seemed to happen when I pressed the key - but obviously it worked as they are there) 

Thank you .... :)

---

