---
title: "flash playback"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Bigneil on 2009-09-15
my playback was always choppy on full screen,  i read and tried the stuff in the sticky at the top.  but it didn't really help me much. I decided that it was probably due to my old banger of a graphics card and just accepted it. 

But, i have now upgraded the video card, i imagined that all would be magically fixed, and in many respects it has, i now have some great compiz stuff going on. but the flash is still lumpy on full screen?  

i went through the sticky again and re-did all the instructions making sure i chose the ones valid to my version of ubuntu. 

i also had a wee noodle about the forum and have had no luck so far. also the play back is fine in xp so i think it must be something to do with software or drivers?

can anybody shed some light on my situation??




8.04  Hardy

---

### Post by Bigneil on 2009-09-16
bump. any ideas from the experts??

---

### Post by martymc on 2009-09-16
I tried the sticky too with no success.

Word is, it's a problem with flash on non-windows computers and Adobe better get off their butts and fix it....

But for a lark, I downloaded the Opera browser last night. Whadda ya know! Smooth full screen video on my Athlon 2000+ with a pci video card.

I guess Mozilla better get off their butts and fix Firefox. :biggrin:

---

### Post by Bigneil on 2009-09-17
> **martymc said:**
> I tried the sticky too with no success.

Word is, it's a problem with flash on non-windows computers and Adobe better get off their butts and fix it....

But for a lark, I downloaded the Opera browser last night. Whadda ya know! Smooth full screen video on my Athlon 2000+ with a pci video card.

I guess Mozilla better get off their butts and fix Firefox. :biggrin:

That's very interesting, my machine is athlon xp too!   i'll give opera a go too :guitar:

---

### Post by caeroe on 2009-09-18
> **martymc said:**
> I tried the sticky too with no success.

Word is, it's a problem with flash on non-windows computers and Adobe better get off their butts and fix it....

But for a lark, I downloaded the Opera browser last night. Whadda ya know! Smooth full screen video on my Athlon 2000+ with a pci video card.

I guess Mozilla better get off their butts and fix Firefox. :biggrin:

Flash is flawless on my notebook running Jaunty x64.  Where as it's choppy on my more powerful desktop running the same OS.

My old notebook has just a ATI 64mb dedicated card, 1gb RAM.  My desktop runs an Nvidia 8800GT 512mb, 4gb RAM.  Both are AMD x64.

I dual boot on my desktop, so it's not a hardware or bandwidth issue.  My notebook runs flash as well as it can, given the age of the PC.

To clarify.  On my desktop I've tried the Flash 64bit plugin, Flash 32bit provided through Synaptic.  I've tried a whole host of drivers from 175 series to the 190.25 that I've just installed.  I've tried Opera 9.64/10.0 and Firefox 3.0.x/3.5.x.  Nothing worked, Flash is still choppy when I go fullscreen on my desktop.

---

### Post by creepytennis on 2009-09-21
Hey everyone.

I managed to solve this issue on my machine. I have Intel 915GM graphics.

This adobe blog is really the key:

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

The flash player does the unbelievably brain dead thing of checking the glxinfo vendor strings to make sure they do *not* contain the string "SGI". Flash hardware acceleration will only be enabled if the vendor strings do not contain the string "SGI". Incredible, huh? I guess this is the kind of idiocy we've got to contend with in closed-source binary blobs.

The advice given in one of the comments actually worked for me. Specifically, use a hex editor (such as 'ghex') to alter these two binaries:

/usr/lib/libGL.so.1.2
/usr/lib/xorg/modules/extensions/libglx.so

(or the actual binaries these files link to, if they are symbolc links. They were links on my system.)

They each contain one instance of "<null>SGI<null>" (plenty of the string "SGI" in other contexts, but ignore these). Change the single instance in each file to "<null>ATI<null>". Restart X, and you may just have hardware accellerated flash. It worked for me.

 :D

---

### Post by fonque on 2009-09-22
I am going to try this when I get home from work today

---

### Post by caeroe on 2009-09-23
I tried the above.  Flash is still choppy on my desktop, it's been like that ever since Jaunty.

Is there any fix for those running Nvidia cards with AMD processors?

---

### Post by Bigneil on 2009-09-26
Hi all, i have just built new machine and installed jaunty and followed the instructions in the sticky and flash is choppy on full screen.  i have come to the the conclusion that ubuntu is not very good at flash!  .... does anybody out there have full screen flash working?  how, and what hardware are you using??

my new machine is 64 bit but there was issues with running 64 in xp and ubuntu so i ended up dual booting in 32.. flash works fine in xp  Why??  

is it firefox? is it ubuntu?  or is it flash player??

---

### Post by L_V on 2009-10-16
> **creepytennis said:**
> /usr/lib/libGL.so.1.2
/usr/lib/xorg/modules/extensions/libglx.so

They each contain one instance of "<null>SGI<null>" 

Not this string at all for me.

The problem is not the Flash plugin, but this:

> Compiz and GPU-accelerated Flash on Linux do not mix. The Flash Player still works if you have Compiz as your window manager; you just won't be able to make use of GPU-accelerated features. This is a shame since Compiz is coming with the basic installation of various Linux distributions. Unfortunately, things get unstable when trying to do GPU acceleration in SWFs running under Compiz.

---

### Post by mtnone on 2009-10-16
I have the same problem.

I tired 
> /usr/lib/libGL.so.1.2
/usr/lib/xorg/modules/extensions/libglx.so

They each contain one instance of "<null>SGI<null>"and opera. no luck. 

Is there a way to deactivate compiz in full screen mode?

---

### Post by AsianSpanker on 2009-10-29
> **Bigneil said:**
> That's very interesting, my machine is athlon xp too!   i'll give opera a go too :guitar:

I have a Dell Demension 9100 media center, and I downloaded Opera to see if it could be true. Wishful thinking. Just as choppy on Opera as it is on Firefox. Has anyone tried errrrg explorer? Has anyone tried explorer on wine?

---

### Post by Bigneil on 2009-11-08
that is a very interesting idea!

---

