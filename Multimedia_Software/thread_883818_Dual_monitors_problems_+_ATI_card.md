---
title: "Dual monitors problems + ATI card"
date: 2008-08-08
forum: Multimedia Software
---

### Post by chenjin824 on 2008-08-08
Hi all,

I find some thread regarding this but I can't append my specific problem at the end of the thread, so I have to open a new thread.
Sorry about that.

I was trying to set up my dual monitor according to Ziox's method at [http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)
basically, it is this 5 steps:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo aticonfig --initial --overlay-type=Xv
sudo aticonfig --desktop-setup=horizontal --sync-vsync=on --add-pairmode=Width0xHeight0+Width1xHeight1
sudo aticonfig --query-monitor
sudo aticonfig --enable-monitor=STRING,STRING <==replaced with the result from the query.
sudo aticonfig --force-monitor=STRING,STRING <==replaced with the result from the query.

Something I should tell is: it's Ubuntu 8.04 + ATI HD2400 vedio card + Gnome. I think ubuntu has installed Fglrx cuz when i type in $fglrxinfo, it reports some information like "ATI Inc."

When i finished those 5 steps and restart X, its resolution becomes 2560*768, which is samller than 1280x1024+1280x1024. And I can't use the system config tool in the Gnome to change it-it is already the maximum option i can use. These two monitor are 19'' and have the same original resolution 1280x1024.

Then I was trying to start over the whole procedure and didn't work out. Then i searched on other bbs and found out somebody did this:
aticonfig --initial=dual-head --screen-layout=right
aticonfig --dtop=horizontal,reverse --overlay-on=1
aticonfig --resolution=0,2650x1024,1280x1024,1280x1024

I tried his method too, but it still didn't work. I did all this
in the X environment and with the two monitors plugged in.
What do you think I should do to fix this?

BTW, a trivial question is, even if I backuped the original xorg.conf file, what should i do to reuse this file when i found I didn't do everything correctly? I mean, when I just copy the backup file to xorg.conf and restart X, it does change anything at all. I can't go back to the nature resolution any more!!! How to do with this?

Sorry about this long question, i've been stuck on it for days and really need to proceed my real work, so please take a look and give me some hints to conquer it. Thanks for your time.

Jin

---

### Post by markbuntu on 2008-08-08
You need to get:

amdcccle 

which is the ati Catalyst Control Center. You should use that to set your monitor resolutions and big desktop. If you have it already, it may be in Applications/Other, or you can type

amdcccle

in a terminal to see if it pops up.

If your display setup is really messed up you can do"

aticonfig --initial -f

This will force a reset of the driver to the default configuration. Then you should use amdcccle to set up the big desktop. After you do that, you can use the aticonfig commands to adjust the resolution of individual displays.

aticonfig --help

will give you a list of command options you can use.

---

### Post by chenjin824 on 2008-08-08
Many thanks to you, markbuntu.

I tried to follow your method, but it seems not that easy to do.

At the very start, we need to install the following packages:
# XFree86-Mesa-libGL
# libstdc++
# libgcc
# XFree86-libs
# fontconfig
# freetype
# zlib
# gcc 

But how can i install them? I tried to enable the multiverse and restricted source in my source.list file, but still it reports can't find the package, like XFree86-Mesa-libGL.

So how could i get over this?

---

