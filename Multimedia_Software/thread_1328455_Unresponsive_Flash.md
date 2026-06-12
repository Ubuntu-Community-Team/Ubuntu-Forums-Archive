---
title: "Unresponsive Flash"
date: 2009-11-16
forum: Multimedia Software
---

### Post by DanTheMan0207 on 2009-11-16
I am running 9.10, and am having problems with an unresponsive flash player. Especially running Pandora, it doesn't respond at all to any clicks, and often playing flash video is the same. Play, pause, mute, about 50% of the time clicking has no effect. I am running an [NVIDIA 7300GT]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130025") with dual screens.
Thanks for any help.

---

### Post by ElSlunko on 2009-11-16
It seems to be a bug with compiz. Are your unning 64bit ubuntu?

A dirty work around is to right click anywhere on your browser and hold down your right click and you should be able to left click again.

---

### Post by DanTheMan0207 on 2009-11-16
I tried what you suggested, but it didn't seem to help. And yes, I am running 64 bit. If it is Compiz, what could I do to fix it?

---

### Post by DanTheMan0207 on 2009-11-16
Nevermind, solved it. Running at a lower intensity of visual effects seemed to have completely solved the problem. Thanks for the help!

---

### Post by zeth01 on 2009-11-30
um please explain how you solved

---

### Post by zeth01 on 2009-11-30
yup got it.  so heres what you do:

right click desktop background
go to change desktop background
go to visual effects tab
select None
Refresh Pandora page
Pandora will now work

---

### Post by solemnavalanche on 2009-12-06
> **zeth01 said:**
> yup got it.  so heres what you do:

right click desktop background
go to change desktop background
go to visual effects tab
select None
Refresh Pandora page
Pandora will now work

Sorry to be a wet blanket, but I don't think this actually counts as a solution. This simply means that Compiz and Pandora are incompatible. That seems like a problem... right? I'd like to be able to use Pandora with desktop effects enabled.

Edit: Ok, here's a better solution that worked for me. 

WORKAROUND 3: Open a terminal and enter:
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

This enabled Desktop Effects and Pandora to coexist, at least for me.

For more info, see this bug: [https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

---

### Post by isaacx3 on 2010-04-04
I think i figured out a much better way to fix it! 

Well i kept reading that it was a incompatibility between the website and compiz, Its not, Its a incompatibility with flash and compiz, cut out the website! SOOOOO heres the fix:

Press the applications button and click ubuntu sofware center, When you install flash you mostly type flash in the search and download the flash pluging (if you have it installed, Remove it now!) Now you have to install the following packeges: 
Gnash SWF viewer
swfdec flash player

After its all installed go to youtube, It should be fixed,
If you see a black or grey box you have to install the normal flash player along with everything else! OK THANKS

:KS:popcorn::mad::guitar::lolflag:):P:p;)

---

### Post by UserSince2003 on 2010-04-12
Try this.  It worked for me:
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)

---

