---
title: "[SOLVED] No sound in laptop"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by yssida on 2008-03-21
Hello everyone, I just did a fresh install of Ubuntu 7.10 and it had no sound. Specifically, the laptop was a Toshiba Portege M600. I did the PCI Id thing and got  8086:284b , I followed the instructions [here]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") and did not understand anything. I'm a bit dense in this field. Please help me.

---

### Post by keratos on 2008-03-21
> **yssida said:**
> Hello everyone, I just did a fresh install of Ubuntu 7.10 and it had no sound. Specifically, the laptop was a Toshiba Portege M600. I did the PCI Id thing and got  8086:284b , I followed the instructions [here]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") and did not understand anything. I'm a bit dense in this field. Please help me.

Just follow the instructions. They are very specific and quite simple to follow. You dont need to understand them if you dont want/cant. Just follow them. Open a terminal from the Accessories menu and away you go.

---

### Post by yssida on 2008-03-21
That is the problem. I'm a bit hesitant as to doing instructions which I can't understand. Anyway, I have a live CD so I'll go ahead. Which of these instructions do you recommend I follow? I think option A is pretty much ruled out.

Thanks~

---

### Post by superprash2003 on 2008-03-21
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by keratos on 2008-03-21
You dont need a live CD.

If you have an installation on your lappy, then just login and get an terminal window open, then follow..

For Heron..


OPTION C 


good luck my friend. good exercise for your linux badge this one!!

---

### Post by yssida on 2008-03-21
Okay am trying out option C now, but it's Gutsy. Hopefully it will work. Hopefully:popcorn:

---

### Post by yssida on 2008-03-21
This is what I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debconf-utils debhelper dpkg-dev gettext html2text intltool-debian patch
  po-debconf
Suggested packages:
  dh-make debian-keyring cvs gettext-doc diff-doc
Recommended packages:
  kernel-package fakeroot kernel-headers kernel-source kernel-source-2.4.27
  linux-source libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alsa-source debconf-utils debhelper dpkg-dev gettext html2text
  intltool-debian patch po-debconf
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 3491kB/5450kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main html2text 1.3.2a-3build1 [90.6kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main debhelper 5.0.51ubuntu3 [526kB]     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main debconf-utils 1.5.14ubuntu1 [40.8kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe alsa-source 1.0.14-1ubuntu2 [2834kB]
Fetched 3491kB in 2m26s (23.8kB/s)                                             
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

what should I do next?

---

### Post by keratos on 2008-03-21
sorry. my mistake. I was answering multiple threads and must have had heron in my head !!

oh well in that case

OPTION A ..

would have done but option C is actually a rebuild of the sound card driver source code for your specific system so that should be even better than A albeit a little more involved.

---

### Post by keratos on 2008-03-21
go into synaptic and select Settings->Repositories and unclick any line under the URI column with the word "cdrom" in it.

Then OK and click the reload button in synaptic then exit synaptic and try again.

---

### Post by keratos on 2008-03-21
Sorry - SYNAPTIC is the package manager. its in the menus somewhere from the menu on the panel but I dont use ubuntu so cannto remember exactly. if you cannot see "Synaptic" well its might be called "Package Manager".

When it asks for a password enter the admin password you used when installing Gutsy.

---

### Post by yssida on 2008-03-21
I tried option A first and got this

choking@archangel:/usr/src$ sudo module-assistant update
[sudo] password for choking:
sudo: module-assistant: command not found
choking@archangel:/usr/src$ cd /usr/src
choking@archangel:/usr/src$ sudo module-assistant update
sudo: module-assistant: command not found
choking@archangel:/usr/src$ sudo module-assistant prepare
sudo: module-assistant: command not found
choking@archangel:/usr/src$ sudo module-assistant auto-install alsa
sudo: module-assistant: command not found
choking@archangel:/usr/src$ sudo shutdown -r now

shall try C

---

### Post by yssida on 2008-03-21
I'm up to this part of the instruction

./configure --with-cards=hda-intel && make

and I got this

choking@archangel:~/alsa-patched/modules/alsa-driver$ ./configure --with-cards=hda-intel && make
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
choking@archangel:~/alsa-patched/modules/alsa-driver$

---

### Post by keratos on 2008-03-21
you have not got the package installed that offers the module-assistant executable, thats all.

you can search for it in synaptic.

A is "simpler"

B is more lengthy but will be compiled to your specific setup so should be more reliable.

Try both!

I'm off to work now so will not be able to respond until tonight.

---

### Post by yssida on 2008-03-21
Thank . Shall now try A again. :) You were a great help.

---

### Post by keratos on 2008-03-22
Back again....

So, what's the status ?

---

### Post by yssida on 2008-03-22
A doesn't work. Trying either C or B now.

---

### Post by keratos on 2008-03-22
please post the output of these two commands

```

grep Codec /proc/asound/card0/codec#*
uname -a

```

(two commands in a terminal)

---

### Post by yssida on 2008-03-22
For the first command, it is

choking@Archangel:~$ grep Codec /proc/asound/card0/codec#*
/proc/asound/card0/codec#0:Codec: Realtek ID 268
/proc/asound/card0/codec#1:Codec: Generic 11c1 Si3054

for the second command it is:

choking@Archangel:~$ uname -a
Linux Archangel 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by keratos on 2008-03-22
a dialup modem too eh??

OK. STOP!

Your kernel does not support your Realtek audio chip.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326)

You will never get it working with the current kernel.

You will have to upgrade to the latest and I mean latest, kernel. Possibly a testing/unstable version. 

I note that hardy has a .24 kernel package and this is the latest stable kernel ([www.kernel.org](www.kernel.org))
[http://packages.ubuntu.com/search?keywords=kernel&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=kernel&searchon=names&suite=hardy&section=all)
For this you will need to go into synaptic, click on one of the active source URL and where it says "gutsy" at the bottom, change to "hardy", then click reload on the toolbar and then search for 2.6.24

Install 2.6.24 kernel and if that doesnt work then you have no choice than to accept no sound :-(

---

### Post by yssida on 2008-03-22
where do I change the active source url in synaptic? Is it the one in Settings>Repositories>Third-Party SOftware?

---

### Post by keratos on 2008-03-22
i dont use ubuntu so cannot advise other than above from recollection.

no matter, you can edit the /etc/apt/sources.list file using gedit and add these:

```

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe main
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse universe main

```

the issue command
```

apt-get update

```

then do the search in synaptic for linux-image-2.6.24-12-386 and install it.

DELETE THE ABOVE LINES AFTER INSTALLING THE KERNEL PACKAGE

after installing the package please post output of /boot/grub/menu.lst so I can check if the kernel is bootable on powerup.

I AM GUESSING that this will work. I dont use ubuntu so I am a little concerned whether you can install hardy package without installing a heck of a lot more packages (the dependencies). I dont know?? Ubuntu is based on debian which is my distro (the "Granddaddy") so I have "some confidence" but .. we'll see.

I'm going out now so wont be able to reply until later. I think I've given you all you need to know for now assuming this works on ubuntu.

---

### Post by yssida on 2008-03-22
I still have the install cd, so if anything goes wrong I'll still have a lengthy install to do.Unless there is some way to boot the said kernel, I'll have to wait for your advice.

---

### Post by keratos on 2008-03-22
hi I'm back!

yes, just install that kernel image package and its dead simple to edit the bootup (we do it in /boot/grub/menu.list) as i said above.

have you installed that kernel image package yet?

---

### Post by yssida on 2008-03-22
shall try now :) thank you.

---

### Post by yssida on 2008-03-22
> I am having the exact same issue when I upgrade from kernel 2.6.24-11 to 2.6.24-12. The sound works perfectly in *-11 (even when I boot into it) but when I boot into *-12 no sound at all and I get the same error message.

We also seem to have the same sound card (minus revision):

(from lspci)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

ShouldI just instal kernel image *-11 instead of *-12?

---

### Post by yssida on 2008-03-22
Here is the result of the menu.lst file you were asing for:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=57acdc8a-4275-417f-96d9-0a9c86810619 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.24-12-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-12-386 root=UUID=57acdc8a-4275-417f-96d9-0a9c86810619 ro quiet splash
initrd          /boot/initrd.img-2.6.24-12-386
quiet

title           Ubuntu 7.10, kernel 2.6.24-12-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-12-386 root=UUID=57acdc8a-4275-417f-96d9-0a9c86810619 ro single
initrd          /boot/initrd.img-2.6.24-12-386

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=57acdc8a-4275-417f-96d9-0a9c86810619 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=57acdc8a-4275-417f-96d9-0a9c86810619 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by yssida on 2008-03-22
Hello! I have now booted into the new kernel, and I get this message:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

What is gstreamer? When I was in the login screen,I tried to press backspace and erased the wrong username I put in, I long pressed it hoping that some error sound might happen. It did. beep-beep-beep, the time it took me to fix my drivers in Windows XP took me about a month. In Ubuntu I'm making progress in three days :)

---

### Post by keratos on 2008-03-23
[http://en.wikipedia.org/wiki/GStreamer](http://en.wikipedia.org/wiki/GStreamer)
wiki always your friend!


Is your sound working now?

If not, open-->system --> Admin. --> Synaptic Package Manager-

Search for "alsa" n(o quotes!)

Click items in the list below
gnome-alsamixer
gstreamer0.10-alsa
gamix
libpt-plugins-alsa
linux-sound-base
asoundconf-gtk
gom
(infact click all the apps that start with alsa)
alsa-firmware-loaders
alsa-player******* (keep going down the list:)
then install them (apply)

the in a terminal, as root user:

sudo apt-get install libncurses5-dev
sudo apt-get install linux-backports-modules-generic

then download [http://users.piuha.net/martti/comp/d630/d630alsa.sh](http://users.piuha.net/martti/comp/d630/d630alsa.sh) (download to your /home/??? directory (whatever your login is)

the in a terminal, as root user, enter

cd /home/???? (whatever your login is)
chmod +x ./d630alsa.sh
sh ./d630alsa.sh
alsaconf

can you configure/hear your card now?

---

### Post by yssida on 2008-03-23
I did a fresh install of Ubuntu 7.10. I don't know why it keeps bringing up text-only logins and such. I don't know how to find my way around it so I reinstalled. Will update the kernel and download the necessary alsa files.

---

### Post by yssida on 2008-03-23
There is sound! But very low volume. Manageable. Thanks:)

---

### Post by keratos on 2008-03-23
Hi again

So what have you done after the reinstall. What EXACTLY did you do.

The sound should be okay but I need to know what the detail is, of the procedure you followed.

By the way, you dont need to reinstall linux. Linux is not like Windows and reinstalls are generally not required. For text logins (not sure what you mean by that) we could have fixed that. If you mean all you got was "Login:" prompt then that means the graphical server front-end called "X" wasnt starting. There is a log file in /var/log/Xorg0.log that would give a clue as to why X wasnt starting, but now you've reinstalled ... we'll never know :(

So, what have you done as regards sound , please specify in full

---

### Post by yssida on 2008-03-24
I reinstalled Ubuntu 7.10 with the exact username and password and computer name, then updated the kernel as you told me earlier then did this:

> **keratos said:**
> 

If not, open-->system --> Admin. --> Synaptic Package Manager-

Search for "alsa" n(o quotes!)

Click items in the list below
gnome-alsamixer
gstreamer0.10-alsa
gamix
libpt-plugins-alsa
linux-sound-base
asoundconf-gtk
gom
(infact click all the apps that start with alsa)
alsa-firmware-loaders
alsa-player******* (keep going down the list:)
then install them (apply)

the in a terminal, as root user:

sudo apt-get install libncurses5-dev
sudo apt-get install linux-backports-modules-generic



I did that in the order as you specified them, whilst running in the original kernel which came with the install. I think the crucial part seems to be the ones leading to the last, the one with the backports. Exactly that.

As for the text login, you were right, there was just a "login:" and I just type my username in and password. Since I had internet and a bit of knowledge with the terminal, I installed lynx. But was unable to use it. Had I known of that log, I would have looked at it first before doing anything drastic. But I wasn't bothered by it at all, installing Ubuntu only took me 15 minutes. Will update in case something happens  I didn't know how to find the log, so I just reinstalled it. This sound card seems to be common, and this fix might help other new users as well.

This problem solved :)!

---

### Post by keratos on 2008-03-24
Good!

Yes it is common.

ALWAYS worth jotting down your system spec before installing any O/S and verifying the compatbility. Can save a LOT of time

Mark this thread as SOLVED using the thread tools button at the top of the page please.

---

