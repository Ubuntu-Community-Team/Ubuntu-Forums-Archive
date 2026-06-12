---
title: "grub 1.99~20101126-1ubuntu1 (natty) and default kernel..."
date: 2010-11-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2010-11-27
New Grub introduced sub-choice for "older" kernels...
Since I want one of those to be my default kernel, not the first one, which is mainline-daily, I am seeking help on how to do that. Usual GRUB_DEFAULT=2 doesn't work anymore...

---

### Post by plun on 2010-11-27
> **zika said:**
> New Grub introduced sub-choice for "older" kernels...
Since I want one of those to be my default kernel, not the first one, which is mainline-daily, I am seeking help on how to do that. Usual GRUB_DEFAULT=2 doesn't work anymore...

Hmmm..:confused:

How do I enable this sub-choice ?   I lost all my kernels except the RC2 from Ubuntu Mainline.

sudo update-grub sees all kernels but are lost in the menu.

```
plun@plun-laptop:~$ sudo update-grub
[sudo] password for plun: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.37-020637rc2-generic
Found initrd image: /boot/initrd.img-2.6.37-020637rc2-generic
Found linux image: /boot/vmlinuz-2.6.37-6-generic
Found initrd image: /boot/initrd.img-2.6.37-6-generic
Found linux image: /boot/vmlinuz-2.6.37-5-generic
Found initrd image: /boot/initrd.img-2.6.37-5-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I choose the maintainer version during install/config.

---

### Post by zika on 2010-11-27
> **plun said:**
> Hmmm..:confused:

How do I enable this sub-choice ?   I lost all my kernels except the RC2 from Ubuntu Mainline.

sudo update-grub sees all kernels but are lost in the menu.

```
plun@plun-laptop:~$ sudo update-grub
[sudo] password for plun: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.37-020637rc2-generic
Found initrd image: /boot/initrd.img-2.6.37-020637rc2-generic
Found linux image: /boot/vmlinuz-2.6.37-6-generic
Found initrd image: /boot/initrd.img-2.6.37-6-generic
Found linux image: /boot/vmlinuz-2.6.37-5-generic
Found initrd image: /boot/initrd.img-2.6.37-5-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I choose the maintainer version during install/config.
I have maintaner version also (see below).
I have, now, only the first kernel and a menu item: Previoos_Linux_versions...
It is not a big deal, but I've lost ability to do automatic boot with any of those other kernels...

```
~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2<<<<<<<<<<<<<<<<
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="..."
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by zika on 2010-11-27
[http://ubuntuforums.org/showpost.php?p=10169056&postcount=681](http://ubuntuforums.org/showpost.php?p=10169056&postcount=681) ...

Trouble lies, as far as I can see, in /etc/grub.d/10_linux...

---

### Post by efflandt on 2010-11-27
Maybe menu item numbering is different for the submenu.  Have you tried:

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

That should normally default to the grub menu item selected or used for previous boot.

---

### Post by zika on 2010-11-27
> **efflandt said:**
> Maybe menu item numbering is different for the submenu.  Have you tried:

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

That should normally default to the grub menu item selected or used for previous boot.
Yes. It doesn't work because saved saves number and that number is unobtainable because it is in submenu and submenu is just one of entries in main menu... I hope You get the picture... :)
Submenu makes every ordinary path unusable.
I've comment-ed out two lines in /boot/grub/grub.cfg (that creates submenu) and...
Next step is to tackle /etc/grub.d/10_linux but I need spare time to do that...
Nice idea but not well-thought before implemented... :)

Edit in /etc/grub/10_linux:
...
  if [ "$list" ] && ! $in_submenu; then
[COLOR="Red"]#[/COLOR]    echo "submenu \"Previous Linux versions\" {"
    in_submenu=:
  fi
done

[COLOR="Red"]#[/COLOR]if $in_submenu; then
[COLOR="red"]#[/COLOR]  echo "}"
[COLOR="red"]#[/COLOR]fi

All is back to "normal"...

---

### Post by plun on 2010-11-27
Ok.. sorry.. took another look at the Grub menu and my kernels was moved to the new menu entry "previous versions".... rather confusing ;)

Well, well...

---

### Post by zika on 2010-11-27
> **plun said:**
> Ok.. sorry.. took another look at the Grub menu and my kernels was moved to the new menu entry "previous versions".... rather confusing ;)

Well, well...Nice puzzle for Saturday. Learned new stuff and my machine is OK, so I'm fine...

---

### Post by plun on 2010-11-27
> **zika said:**
> Nice puzzle for Saturday. Learned new stuff and my machine is OK, so I'm fine...

Yup....:D

The filename is..../etc/grub.d/10_linux   ;)

Changed it as you did and everything is fine again....

A bug for this ?

EDIT changed this

```
#if [ "$list" ] && ! $in_submenu; then
   # echo "submenu \"Previous Linux versions\" {"
   # in_submenu=:
  #fi
```

---

### Post by dino99 on 2010-11-27
> **plun said:**
> Yup....:D

The filename is..../etc/grub.d/10_linux   ;)

Changed it as you did and everything is fine again....

A bug for this ?

EDIT changed this

```
#if [ "$list" ] && ! $in_submenu; then
   # echo "submenu \"Previous Linux versions\" {"
   # in_submenu=:
  #fi
```

yeah you should ( to get a better ubuntu :) )

---

### Post by zika on 2010-11-27
> **dino99 said:**
> yeah you should ( to get a better ubuntu :) )Not better, just the one that I'm used to...
I can see and must admit that this idea with submenu is very nice, but it needs some more work... I'm ready to wait...

---

### Post by plun on 2010-11-27
> **zika said:**
> Not better, just the one that I'm used to...
I can see and must admit that this idea with submenu is very nice, but it needs some more work... I'm ready to wait...

So am I.... maybe this just is a challenge for "nerds" which installs kernels from Ubuntu Mainline....;)

---

### Post by zika on 2010-11-27
> **plun said:**
> So am I.... maybe this just is a challenge for "nerds" which installs kernels from Ubuntu Mainline....;)If that is the point: I do install kernel from Ubuntu Mainline Daily, daily...

---

### Post by plun on 2010-11-27
> **zika said:**
> If that is the point: I do install kernel from Ubuntu Mainline Daily, daily...

So do I also but just the RC milestones..... I am a nerd...;)

The question is if this **new menu entry "previous versions" is good or bad**...  ???

(I still doesn't get it howto move a kernel to be a default one...??? )

---

### Post by jerrylamos on 2010-11-27
I get automatic boot and boot order of my choice by doing:
sudo gedit /etc/grub.d/06_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Lucid LTS on sda1' {
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro quiet
#linux /vmlinuz root=/dev/sda1 ro quiet radeon.modeset=0
initrd /initrd.img
}
menuentry 'Maverick>Narwhal on sda7' {
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro quiet
initrd /initrd.img
}
menuentry 'Lucid TV on sdb1' {
set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro quiet
initrd /initrd.img
}
save
exit
sudo update-grub

These entries appear before the regular Grub 2 entries when I boot.  Now if you want to boot a specific kernel, just put that kernel name and initrd name in the linux and initrd lines.

As written here the linux and initrd will boot the latest kernel which you don't want, so example to boot kernel 5 replace:

linux /vmlinuz root=/dev/sda1 ro quiet
initrd /initrd.img

with 

linux /boot/vmlinuz-2.6.37-5-generic-pae root=/dev/sda1 ro quiet
initrd /boot/initrd.img-2.6.37-5-generic-pae

as first menuentry which is automatic boot entry or wherever.

Jerry

---

### Post by VMC on 2010-11-28
Does anyone know where this newest grub gets the ***setparams*** info from?

When you see the grub menu, edit and the first line now shows , for examble, setparams Natty'.

Also, I get an error message when I try and boot any menu line:

error: no argument specified

edit: the newest grub2(1.99) requires root having an additonal argument, as:

 **set root='(/dev/sda,msdos1)'**

I had it set the old way as

 [B]set root='(hd0,1)'

[/B]That explained the argument error.

---

### Post by zika on 2010-11-30
New version, same problem with selecting non-first kernel...

---

### Post by dino99 on 2010-11-30
i'm using the default grub2 settings and have a clean and usable menu:
- only the latest kernel is shown
- the other(s) can be selected by clicking the 2nd line "previous kernel": this give you a new list where you pickup the kernel you like.

---

### Post by zika on 2010-11-30
> **dino99 said:**
> i'm using the default grub2 settings and have a clean and usable menu:
- only the latest kernel is shown
- the other(s) can be selected by clicking the 2nd line "previous kernel": this give you a new list where you pickup the kernel you like.As I said in my previous posts, I do too "have a clean and usable menu:
- only the latest kernel is shown
- the other(s) can be selected by clicking the 2nd line "previous kernel"", the only thing I am complaining is that, now, I can not set one of those from "previous kernel" submenu to be default and have my machine boot with it automatically...
If You have solution to that (apart from editing conf files for grub, which I wrote about, also and found how to do that) I would be gratefull. That worked like a charm for years...
[http://ubuntuforums.org/showpost.php?p=10169037&postcount=3](http://ubuntuforums.org/showpost.php?p=10169037&postcount=3)
[http://ubuntuforums.org/showpost.php?p=10169313&postcount=6](http://ubuntuforums.org/showpost.php?p=10169313&postcount=6)

---

### Post by drs305 on 2010-11-30
zika,

I can't boot into a natty VM at the moment, but can you use the equivalent of:

> GRUB_DEFAULT="Ubuntu, with Linux 2.6.37-6-generic (on /dev/sda12)"

---

### Post by zika on 2010-11-30
> **drs305 said:**
> zika,

I can't boot into a natty VM at the moment, but can you use the equivalent of:I will try that as soon I get back to my natty machine... Thank You!

No, it doesn't seem to be working. I'll play with that thought a bit more, once I get some time...

---

### Post by dino99 on 2010-11-30
@Zika

just tested with Startup-manager: it let me choose all the kernels, even those "previous", so its ok to me. (i've always accepted and installed the "maintainer" package, no tweak at all on my end.

---

### Post by drs305 on 2010-11-30
> **dino99 said:**
> @Zika
just tested with Startup-manager: it let me choose all the kernels, even those "previous", so its ok to me. (i've always accepted and installed the "maintainer" package, no tweak at all on my end.
@ dino99,

Could you open grub.cfg and tell us what the "set default=" looks like for an item on the submenu?

I've tried using the exact title and number method in /etc/default/grub and like *zika's* experience neither worked.

Thanks.

---

### Post by dino99 on 2010-11-30
@ DRS305

*****
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi

******

i remind we had a new os-prober some days ago; maybe you need to run it again and/or grub-mkconfig.

What i suspect is some conflicts with other grub2 installed by different release/distro on different partition/device. Actually the menu is correctly built only for the "active" grub2 (multiple kernels on other release(s) are not grouped.

---

### Post by drs305 on 2010-11-30
@ dino,

I am working with a Natty daily build from 2 days ago and updated this morning. It's in a VM so there are no 'outside' influences.

Thanks for posting the grub.cfg. It appears that you are using the default 0 setting. I think what *zika* wants, and what I want to learn, is how to select an entry 'hidden' behind the submenu. I'm trying to contact some of the devs on IRC but so far they haven't responded.

So far these haven't worked for an item in the submenu:
> GRUB_DEFAULT=some number  - for an entry in the submenu.
GRUB_DEFAULT="menuentry quote"
GRUB_DEFAULT=saved        - (in conjunction with GRUB_SAVEDEFAULT=true) 


---

### Post by dino99 on 2010-11-30
> **drs305 said:**
> @ dino,

I am working with a Natty daily build from 2 days ago and updated this morning. It's in a VM so there are no 'outside' influences.

Thanks for posting the grub.cfg. It appears that you are using the default 0 setting. I think what *zika* wants, and what I want to learn, is how to select an entry 'hidden' behind the submenu. I'm trying to contact some of the devs on IRC but so far they haven't responded.

So far these haven't worked for an item in the submenu:

dont have problem to select them with startup-manager: they are listed (dont have more idea to help, sorry)

---

### Post by cariboo on 2010-11-30
I noticed when I started up two systems this morning, I have a **Previous Linux Version** selection in the grub menu Selecting it brings up a menu with an older kernel, in my case 2.6.37-6.

---

### Post by drs305 on 2010-11-30
> **cariboo907 said:**
> I noticed when I started up two systems this morning, I have a **Previous Linux Version** selection in the grub menu Selecting it brings up a menu with an older kernel, in my case 2.6.37-6.

Yes. But that is the problem I think because multiple old kernels will be stored therein. So I don't think you can use "Previous Linux Version" as an entry and it doesn't seem to accept entries from the submenu as default selections.  

I do like hiding older kernels in a submenu though. Eventually as Natty gets closer to release date (or if earlier releases get the newer Grub) I'm sure I'll have to make a title tweak for users who want to put them back on the main screen (unless the devs make that an option). Actually, I can probably just comment the submenu section, so that will be easy...

---

### Post by cariboo on 2010-11-30
How often is someone going to use an older kernel as the default?

---

### Post by zika on 2010-11-30
If You have 2.6.37-999 installed it goes as first, at the top of the list. Ubuntu kernel goes into "older versions" ... Just for example... If they just left first 3 it would be great...
Of course, we are here in a vast minority, testing pre-alpha version of Ubuntu... So, Your question get a totally different meaning here...

I tried "saved" also and it does not work either.

I really do not like using StartUp Manager and stuff like that... I'm glad it, for once, proved to be OK...

---

### Post by zika on 2010-11-30
> **dino99 said:**
> @ DRS305
What i suspect is some conflicts with other grub2 installed by different release/distro on different partition/device. Actually the menu is correctly built only for the "active" grub2 (multiple kernels on other release(s) are not grouped.Just to make it clear, I'm not sure whom did You address this: I have only one grub installed and very simple arrangement...

---

### Post by zika on 2010-11-30
> **drs305 said:**
> I do like hiding older kernels in a submenu though. Me too. That is the only reason I started this discussion. If I were against hiding kernels, i would, just, easily, comment out "submenu" stuff in 10_linux and...

---

