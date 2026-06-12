---
title: "Alpha 3 Doesn't Boot - Alpha 2 Did"
date: 2010-08-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JayminP on 2010-08-09
Procedure i have to use...
1. Burn ISO to CD/MagicISO
2. Use Ubuntu Live USB Creator from ISO and Make Live USB
3. Use USB to do regular live boot up.

-Alpha 2 Worked just fine...
(USB i use is Bootable)
-Alpha 3 Doesn't work stops the boot @ (initramfs)

I tried cd boot but stops the boot up @ Copywriter/Welcome Message.(Might be because of non capable cd)...

Here is the big one....Its Toshiba A505...

---Kernel 2.6.35 Should Have Fixed The Problem--- 
If its because of Kernel Alpha 2 Shouldn't Boot Also.

Alpha 2 And Alpha 3 Does Have Different Kernels tho...

Alpha 2 includes the 2.6.35-6.7 [kernel]("http://kernel.org/") based on 2.6.35-rc3.
Alpha 3 includes the 2.6.35-14.19 [kernel]("http://kernel.org/") based on 2.6.35 final.

-------------------------------------------------------------------------------------
Tx

---

### Post by Catharsis on 2010-08-09
This is a known issue with usb-creator. You can follow its development at Bug [lpbug]608382[/lpbug]

For the workaround, edit /syslinux/syslinux.cfg on the usb drive and remove the word 'ui'. Save and exit, and now you can boot into it.

---

### Post by cariboo on 2010-08-09
Just to let you know the forum has a handy bbcode tag for launchpad bugs, use:

[noparse][lpbug]bug#[/lpbug][/noparse]

That way you don't have to copy and paste a link if you know the bug number eg:

bug# [lpbug]612437[/lpbug]

---

### Post by ranch hand on 2010-08-09
> **cariboo907 said:**
> Just to let you know the forum has a handy bbcode tag for launchpad bugs, use:

[noparse][lpbug]bug#[/lpbug][/noparse]

That way you don't have to copy and paste a link if you know the bug number eg:

bug# [lpbug]612437[/lpbug]
Thanks.  That is nice stuff to know.

---

### Post by GeoffreyTransom on 2010-08-09
I'm not even sure what alpha I have - I installed from the Updarte Manager (using the **sudo apt-get update -d** as mentioned on the Unbuntu download page) two weeks ago. I do know that it's one of the .35 kernels though.

Since the upgrade completed, the Ubuntu partition will not boot; it gets to the splash screen and just sits there (the HDD shows intermittent activity, but nothing ever results).

It would be sensational if this was known.

Machine specs: 

Compaq Presario CQ40 (NEVR BUY A COMPAQ OR HP)
2Gb RAM
everything worked perfectly under 10.04.

---

### Post by Catharsis on 2010-08-09
> **cariboo907 said:**
> Just to let you know the forum has a handy bbcode tag for launchpad bugs, use:

[noparse][lpbug]bug#[/lpbug][/noparse]

That way you don't have to copy and paste a link if you know the bug number eg:

bug# [lpbug]612437[/lpbug]

That's AWESOME! Haha, thanks cariboo907 :)

P.S. The [bbcode page](http://ubuntuforums.org/misc.php?do=bbcode) has the "Example Output" incorrect for the lpbug tag, fyi.

---

### Post by ranch hand on 2010-08-09
Hit e in the menu with 10.10 high lighted.  Then you can edit the menu entry.  Just remove "splash".

Hit Ctrl and x to boot with your edit.  Should boot.  May need more.

You should also be able to avoid plymouth by booting to recovery, using text login, typing startx at prompt.

---

### Post by cariboo on 2010-08-09
Can you hold down the shift key to get to the grub menu,and select recovery mode. Once at the menu select resume. You should be able to log in at the prompt, once you've logged in, at the prompt type:

```
sudo service gdm start
```

that should start X and take you to the desktop. Once you have actually booted to the desktop, you should be able to shutdown, and start up normally.

ranch hand has a variation, where he just had to start x from the prompt to get to the desktop. At the prompt type:

```
startx
```

both methods just work with the default drivers.

---

### Post by Catharsis on 2010-08-09
> **GeoffreyTransom said:**
> I'm not even sure what alpha I have - I installed from the Updarte Manager (using the **sudo apt-get update -d** as mentioned on the Unbuntu download page) two weeks ago. I do know that it's one of the .35 kernels though.

Since the upgrade completed, the Ubuntu partition will not boot; it gets to the splash screen and just sits there (the HDD shows intermittent activity, but nothing ever results).

It would be sensational if this was known.

Machine specs: 

Compaq Presario CQ40 (NEVR BUY A COMPAQ OR HP)
2Gb RAM
everything worked perfectly under 10.04.

Hi, do you mind starting a new thread for your issue? It's probably completely unrelated to the Original Poster's, and I don't want to have two conversations in the same thread (it gets messy).

---

### Post by jppr on 2010-08-10
I did yesterday fresh daily alternate usb-stick installations both Ubuntu and Kubuntu, i have also problem with live-cd but alternate works fine
_[http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)_

---

### Post by cariboo on 2010-08-10
> **Catharsis said:**
> That's AWESOME! Haha, thanks cariboo907 :)

P.S. The [bbcode page](http://ubuntuforums.org/misc.php?do=bbcode) has the "Example Output" incorrect for the lpbug tag, fyi.

the bbcode page example is correct

> bug# 612437

looks like this, I have to use noparse tags to show the code:

[noparse]bug# [lpbug]612437[/lpbug][/noparse]

---

### Post by Catharsis on 2010-08-10
> **cariboo907 said:**
> the bbcode page example is correct



looks like this, I have to use noparse tags to show the code:

[noparse]bug# [lpbug]612437[/lpbug][/noparse]

The Example Output shouldn't have the tags still around it. It should just be "2526" underlined.

---

### Post by JayminP on 2010-08-10
Removing 'ui' from the syslinux...it actually gives me new error about unknown command i think related to gfxboot which would be next commend i guess...

holding shift gives me boot:_ and when i try to type in commands it doesn't work...it doesn't take me to grub menu or commend line...

im downloading daily build i hope that fixes problems....

any other ideas? or way to download fixed live cd

Edited:-
in [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) whats the difference between daily and daily-live?

---

### Post by jppr on 2010-08-10
Daily-live is desktop / live-cd installation and daily is alternate installation. Yesterday I can´t did live-cd installation, there is something broken but like i said alternate installation works fine.

---

### Post by VMC on 2010-08-10
> **JayminP said:**
> Removing 'ui' from the syslinux...it actually gives me new error about unknown command i think related to gfxboot which would be next commend i guess...

holding shift gives me boot:_ and when i try to type in commands it doesn't work...it doesn't take me to grub menu or commend line...

im downloading daily build i hope that fixes problems....

any other ideas? or way to download fixed live cd

How did you create the usb? Using a previous Ubuntu?

This is what syslinux.cfg should look like now:

```
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
```

Have you tried burning a DVD R/W and go that route?

---

### Post by JayminP on 2010-08-10
i created usb using usb-creator from ubuntu alpha 3 iso...i burned iso to a cd but i couldn't boot it because of cd...so im using usb-creator from the CD and selecting USB from the list to make live usb.

using win 7

VMC, my config does look like that...

---

### Post by lnx4tw on 2010-08-10
> **JayminP said:**
> Removing 'ui' from the syslinux...it actually gives me new error about unknown command i think related to gfxboot which would be next commend i guess...

holding shift gives me boot:_ and when i try to type in commands it doesn't work...it doesn't take me to grub menu or commend line...

im downloading daily build i hope that fixes problems....

any other ideas? or way to download fixed live cd

Edited:-
in [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) whats the difference between daily and daily-live?

Have you had any luck booting? I have tried loading the netbook.iso with Linux Live USB and UNetBootin, neither work by default. With the Linux Live USB version on the thumbdrive I am able to edit the syslinux.cfg and take out the ui, but I am getting the same error, "gfxboot is an unknown command."

The error that I receive when booting with UNetBootin is

> FATAL: Error inserting ramzswap (/lib/modules/2.6.35-14-generic/kernel/drivers/s
swap.ko): Unknown symbol in module, or unknown parameter (see dmesg)
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

Any ideas?

Edit:
I am trying to use the latest maverik-netbook.iso from the daily builds.

---

### Post by JayminP on 2010-08-10
i'm still not able to get it to work...but if your computer only supports 2.6.35 kernel then use ubuntu 10.10 alpha 2 works just perfect...with no issue...
otherwise i did stick to stable....
if here for testing i don't know how others got it to work O_O

---

### Post by lnx4tw on 2010-08-11
I just installed Lucid then added the Maverick PPA so that I could get the packages. It was easier than messing with the USB.

---

### Post by thonuz on 2010-08-11
I am stuck with the the screen freezing up about 6 seconds into boot. I'm checking kernel logs and am aware of upgrade dangers. also. 
Safe mode boots and safe graphics. Well turns out its nvidia, even without restricted drivers--i did not install these. Entering "nv" works for now. I could not get text only boot. I thought that was alt+F2
editing my post again... after reboot it says in verbose can't find Nvidia and then I have to redit it configuration again. suspect its xorg or something seeing the breakage sticky.

---

### Post by GeoffreyTransom on 2010-09-06
> **Catharsis said:**
> Hi, do you mind starting a new thread for your issue? It's probably completely unrelated to the Original Poster's, and I don't want to have two conversations in the same thread (it gets messy).
Yep - will do. (Sorry for the tardy reply - I have been super busy of late).

It's a while since I last checked my Ubuntu partition - from memory the issue seemed to have something to do with the ATI driver; I booted to the low-res graphics GUI once, but then something odd happened and now it seems that the low-res graphics driver doesn't load.

Will start a new thread once I spend an horu or so getting back up to speed with the issue.

Cheerio


GT

---

