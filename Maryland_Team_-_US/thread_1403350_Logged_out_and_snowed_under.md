---
title: "Logged out and snowed under"
date: 2010-02-10
forum: Maryland Team - US
---

### Post by robomorris on 2010-02-10
am having problems starting Ubuntu 9.1. I installed it (also Win XP) and everything was fine. While downloading updates I lost power and that is where everything  went awry. I was  prompted to install 'sude dpkg --configure-a'  I have no idea what that is but now my Ubuntu won't boot up. I am now receiving the  following message, Gnu Grub Version 1.97 Beta 4, Minimal BASH-likeediting is supported...press tabfor possible command...   sh: grub      

I have no idea what to do. Your help would be invaluable as I have created lots of data. BTW my windows wont start either, not that I want it to!

Neophyte awaiting rescue.

The only program that I can use now is PUP linux on CD!

---

### Post by amsterdamharu on 2010-02-10
In the grub commandline try this:
[http://ubuntuforums.org/showthread.php?t=1390088#2](http://ubuntuforums.org/showthread.php?t=1390088#2)

You have to know where Ubuntu is installed (root filesystem).

You have grub2 so use the commands as they are not the commented ones.

---

### Post by robomorris on 2010-02-10
I tried the Http: command you sent but nothing happened. The prompt i get is:
sh:grub>

Should I try to type in the command that the hyperlink points to? Is sh:grub the command line to start at? Sorry for the ineptitude but I am not familiar with any programming and I only have access to the Internet through PUP which I have to reboot when I want to access Ubuntu.

---

### Post by amsterdamharu on 2010-02-10
Yes you should click on the link and ignore all the commands that start with # they are just comments.

Make sure you write down the correct command, in firefox press control and + to make the characters bigger.

Could you write down any response you get after typing the commands?

---

### Post by robomorris on 2010-02-10
Is it possible to determine what partition Ububtu and Windows reside as well as what kernel version one has?

---

### Post by robomorris on 2010-02-10
OK. I tried but no luck. When I start up Ubuntu I am left with the following:

sh:grub>

I tried: find/boot/grub/menu.list and got something like bad command. Should the prompt be different? How or what do i need to change the prompt?

As far as I can understand and I again apologize for my complete lack of understanding, I need to type the following:
-----------------------------------------------------------
find/boot/grub/menu.list

search /boot/grub/grub.conf

search  (hd0,2)/boot/vmlin (press tab)

linux                 /boot/vmlinuz--2-generic root=/dev/sda3 ro single (???)

initrd (press tab)

search (hd0,2)/boot/init (press tab)

initrd               /boot/initrd.img--2generic

boot
-------------------------------------------------------

If this is correct then I need to find out how to find correct prompt?
Why all the spacing between some of the commands, i.e.,  initrd           /boot.....

---

### Post by amsterdamharu on 2010-02-10
My post nr4

> Yes you should click on the link and** ignore all the commands that start with #** they are just comments.

Make sure you write down the correct command, in firefox press control and + to make the characters bigger.

Could you write down any response you get after typing the commands?

Could you try this:
```

search /boot/grub/grub.conf
#this could give you something like (hd0,2) use it for the next commands
root (hd0,2)
search (hd0,2)/boot/vmlin(press tab)
#this should give you a number of options of kernels to choose, choose one
#you need to know what partition your root system is on (what is / )
#you might guess /dev/sda2 means first disk, second partition
linux /boot/vmlinuz-2.6.24-26-generic root=/dev/sda3 ro single
&#65283;now choose initrd pressing tab will give you a list of what's in /boot
# use the same version number as kernel
search (hd0,2)/boot/init(press tab)
initrd        /boot/initrd.img-2.6.24-26-generic
boot

```

---

