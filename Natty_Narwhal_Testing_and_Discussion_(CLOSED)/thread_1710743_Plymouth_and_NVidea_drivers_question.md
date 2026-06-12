---
title: "Plymouth and NVidea drivers question"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by exploder on 2011-03-20
I installed todays daily build of Natty x64, everything works exceptionally well except for Plymouth. I installed the NVidea current drivers for my GT 220 graphics and installed bootupmanager to try and fix the Plymouth splash. Plymouth displays fine on shutdown now but is just a black screen on start up.

Is there a solution for this or is this still in the works? 

I must say though that this is absolutely the best image quality I have ever seen out of this graphics card in Linux!

---

### Post by Harry33 on 2011-03-20
> **exploder said:**
> I installed todays daily build of Natty x64, everything works exceptionally well except for Plymouth. I installed the NVidea current drivers for my GT 220 graphics and installed bootupmanager to try and fix the Plymouth splash. Plymouth displays fine on shutdown now but is just a black screen on start up.

Is there a solution for this or is this still in the works? 

I must say though that this is absolutely the best image quality I have ever seen out of this graphics card in Linux!

The proprietary drivers do not support kernel KMS (mode setting).
This is why Plymouth is usually only loaded for a very limited time.
Some setups won't show it at all.

I even have an ATI (with open source drivers) setup, where I rarely see Plymouth.
So I think this is just the way Plymouth is.

---

### Post by jennybrew on 2011-03-20
> **Harry33 said:**
> The proprietary drivers do not support kernel KMS (mode setting).
This is why Plymouth is usually only loaded for a very limited time.
Some setups won't show it at all.
I even have an ATI (with open source drivers) setup, where I rarely see Plymouth.
So I think this is just the way Plymouth is.

I too have an ATI set up which doesnt display the splash properly.
Others I know via LUG have NVidia equipment and guess what ..Plymouth splash doesnt display properly.
Trawl through Launchpad, either for this pre release or for previous releases and you will find numerous unresolved bug reports.
I have sat through one experience where friend asked to see what I was doing and, on seeing the boot mess, laughed and walked away.
So yes, thats the way Plymouth is unfortunately.

---

### Post by exploder on 2011-03-20
Normally I can get bootupmanager to fix plymouth. Plymouth does not even work on start up with the open source drivers, so maybe there is hope for it being fixed.

---

### Post by Harry33 on 2011-03-20
Right JennyBrew and exploder,

I have one ATI setup (Radeon HD2600 pro). Usually I do not see Plymouth during boot up, or at least P is visible less than 1 sec.
But, if I upgrade any package which causes ureadahead to rebuild, I see P for about 2-3 secs, but only one time ( one boot up).

On my Intel setup ( 9 series card), I always see Plymouth right after grub almost up till gdm.

On my NVidia setup (GTX285) with nvidia-current_270.30, I always see Plymouth just like with Intel.

On all these setups, Plymouth is fully visible during shut down.

---

### Post by jennybrew on 2011-03-20
> **Harry33 said:**
> , Plymouth is fully visible during shut down.

On all of my systems this is the same its fully visible on shut down.

My gripes with Plymouth are .

!:  it doesnt function correctly on approximately 50% of recent hardware.

2:  There doesnt seem to be any intention to fix the numerous reported problems / bugs.

3:  whereas it does more than just show a splash screen ...it is a ridiculous method of showing a splash    screen.

Please please Ubuntu take a look at this blight on a super system !!!

---

### Post by lucazade on 2011-03-20
> **jennybrew said:**
> On all of my systems this is the same its fully visible on shut down.

My gripes with Plymouth are .

!:  it doesnt function correctly on approximately 50% of recent hardware.

2:  There doesnt seem to be any intention to fix the numerous reported problems / bugs.

3:  whereas it does more than just show a splash screen ...it is a ridiculous method of showing a splash    screen.

Please please Ubuntu take a look at this blight on a super system !!!

Not really correct, somethings has been done for natty.
[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-grub2-boot-framebuffer](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-grub2-boot-framebuffer)

obviously proprietary drivers doesn't help, but plymouth works better in natty than in maverick with nvidia because grub detect resolution via vbe and apply it to startup sequence..

anyway i made a all-black plymouth some release ago and i don't care anymore about it :P

---

### Post by Harry33 on 2011-03-20
> **jennybrew said:**
> 
...
3:  whereas it does more than just show a splash screen ...it is a ridiculous method of showing a splash    screen.
Please please Ubuntu take a look at this blight on a super system !!!

I did like more the xsplash in Karmic, the way X was loaded early in boot process.
There, I used the same background on xsplash, gdm and desktop.

Then became RedHat's Plymouth ...

---

### Post by deconstrained on 2011-03-20
This worked really well for me:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by lucazade on 2011-03-20
> **deconstrained said:**
> This worked really well for me:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Yes, it worked well with lucid and maverick.. 
but it is no more needed because natty grub2 detects correct resolution (where a kms driver is not available) and applies it to boot routine.

---

### Post by Iehova on 2011-03-20
My Plymouth (with nVidia card) was working fine (albeit at a low resolution) until the recent xorg updates which borked it, and also considerably lengthened the boot time. Now shutdown is not graphical at all whilst startup mostly shows just a purple screen and for the final second or so there is something like a textual version of the boot splash with some random text on and around it.

---

### Post by mc4man on 2011-03-20
> **Harry33 said:**
> I did like more the xsplash in Karmic, the way X was loaded early in boot process.
There, I used the same background on xsplash, gdm and desktop.

Then became RedHat's Plymouth ...
Always liked that splash, was hoping lucid/plymouth would build upon that (animate it or something

( because I like subdued and use ambiance  still use karmic's bg....jpg as the current desktop background in natty on a ws desktop monitor

---

### Post by exploder on 2011-03-20
I have seen plymouth a couple of times tonight after applying updates but it only works after the update, after that it goes right back to the black screen. 

Seeing plymouth like that makes me think it is probably fixable.

---

### Post by Harry33 on 2011-03-21
> **exploder said:**
> I have seen plymouth a couple of times tonight after applying updates but it only works after the update, after that it goes right back to the black screen. 

Seeing plymouth like that makes me think it is probably fixable.

Unfortunately that does not guarantee a fix.
You see Plymouth only after certain updates (because ureadahead is rebuilt) because the boot process is slow then. After ureadahead is built, the boot process is fast again => you do not get to see Plymouth anymore.

The real issue is, that Plymouth should be loaded earlier in boot process.
But that is not supported because of the way KMS is working.

The bottom line is, however, why waste so much time to develop Plymouth.
It may not be the best direction. Perhaps X (with configurable background) should be loaded earlier in boot and the splash completely removed.:guitar:

---

### Post by lucazade on 2011-03-21
> **Harry33 said:**
> Unfortunately that does not guarantee a fix.
You see Plymouth only after certain updates (because ureadahead is rebuilt) because the boot process is slow then. After ureadahead is built, the boot process is fast again => you do not get to see Plymouth anymore.

The real issue is, that Plymouth should be loaded earlier in boot process.
But that is not supported because of the way KMS is working.

The bottom line is, however, why waste so much time to develop Plymouth.
It may not be the best direction. Perhaps X (with configurable background) should be loaded earlier in boot and the splash completely removed.:guitar:

Usplash -> Xsplash -> Plymouth -> no splash at all, replace "splash" in grub to "quiet-services" option to suppress all services messages!
This way we would get a flickerfree startup until desktop is loaded :)

---

### Post by Harry33 on 2011-03-21
> **lucazade said:**
> Usplash -> Xsplash -> Plymouth -> no splash at all, replace "splash" in grub to "quiet-services" option to suppress all services messages!
This way we would get a flickerfree startup until desktop is loaded :)

True, but the black screen lasts for too long. If X would be loaded earlier, it would look better.
Also, the Ubuntu "dependency-hell" could be eased a bit here.
Why does mountall depend on Plymouth (actually libplymouth2)?

---

### Post by lucazade on 2011-03-21
> **Harry33 said:**
> True, but the black screen lasts for too long. If X would be loaded earlier, it would look better.
Also, the Ubuntu "dependency-hell" could be eased a bit here.
Why does mountall depend on Plymouth (actually libplymouth2)?

I think for fsck hd checks.. unfortuantely!

---

### Post by Yofel on 2011-03-21
> **Harry33 said:**
> True, but the black screen lasts for too long. If X would be loaded earlier, it would look better.
Also, the Ubuntu "dependency-hell" could be eased a bit here.
Why does mountall depend on Plymouth (actually libplymouth2)?

Because mountall needs plymouth to manage the file system check messages and keyboard input in a sane way since it's not guaranteed that it's the only process that needs it now that we use upstart (since the services are starting in parallel). So removing plymouth isn't an option, best you can do is disable the splash, it should still function as a message queue even without the graphical gimmick.

---

### Post by Harry33 on 2011-03-21
> **Yofel said:**
> Because mountall needs plymouth to manage the file system check messages and keyboard input in a sane way since it's not guaranteed that it's the only process that needs it now that we use upstart (since the services are starting in parallel). So removing plymouth isn't an option, best you can do is disable the splash, it should still function as a message queue even without the graphical gimmick.

That is not a very good explanation.
Plymouth is only an application providing one type of a graphical boot animation.
Any system will boot without it well.

I think the dependency is there because Plymouth has been set to run before the root filesystem is mounted. That does not necessarily need to be so.

Now, if X would be loaded as early as possible (still not before root mounting) and then a xsplash above that, the system would boot just fine.

---

### Post by lucazade on 2011-03-21
> **Harry33 said:**
> That is not a very good explanation.
Plymouth is only an application providing one type of a graphical boot animation.
Any system will boot without it well.

I think the dependency is there because Plymouth has been set to run before the root filesystem is mounted. That does not necessarily need to be so.

Now, if X would be loaded as early as possible (still not before root mounting) and then a xsplash above that, the system would boot just fine.

I think plymouth and mountall are linked because of fsck.
Fsck can only shows automatic check results in plymouth and use its input handling for [c]ancel test.
Maybe fsck has been patched to remove interactive output in VTs and requires necessarily plymouth to work.. infact also server edition ships plymouth.
Correct me if wrong!

---

### Post by Harry33 on 2011-03-21
> **lucazade said:**
> I think plymouth and mountall are linked because of fsck.
Fsck can only shows automatic check results in plymouth and use its input handling for [c]ancel test.
Maybe fsck has been patched to remove interactive output in VTs and requires necessarily plymouth to work.. infact also server edition ships plymouth.
Correct me if wrong!

Well couldn't that be changed then.
I mean if and only if Plymouth would be mabe optional.

---

### Post by lucazade on 2011-03-21
> **Harry33 said:**
> Well couldn't that be changed then.
I mean if and only if Plymouth would be mabe optional.

mountall (2.10) lucid; urgency=low

  * Add hard dependency on Plymouth; without it running, mountall will
    ignore any filesystem which doesn't show up within a few seconds or that
    fails to fsck or mount.  If you don't want graphical splash, you simply
    need not install themes.

I hope plymouth could be optional but I believe it won't happen

---

### Post by jennybrew on 2011-03-21
> **lucazade said:**
> mountall (2.10) lucid; urgency=low

  * Add hard dependency on Plymouth; without it running, mountall will
    ignore any filesystem which doesn't show up within a few seconds or that
    fails to fsck or mount.  If you don't want graphical splash, you simply
    need not install themes.

I hope plymouth could be optional but I believe it won't happen

I think trawling through Launchpad, looking through hundreds of posts on the Ubuntu Forums, listening to people at the LUG ... that Plymouth has been "done" to death.
It isnt going to be fixed for everybody so best forget about it now.
For those of us with a commitment to good design standards its probably a major down associated with Ubuntu.
Its obvious there is a policy decision to ignore the Plymouth issue 
Now to something positive ........................... :)

---

### Post by Harry33 on 2011-03-21
> **jennybrew said:**
> I think trawling through Launchpad, looking through hundreds of posts on the Ubuntu Forums, listening to people at the LUG ... that Plymouth has been "done" to death.
It isnt going to be fixed for everybody so best forget about it now.
For those of us with a commitment to good design standards its probably a major down associated with Ubuntu.
Its obvious there is a policy decision to ignore the Plymouth issue 
Now to something positive ........................... :)

This describes quite well what I have begun to think about the Plymouth mess.
I say mess, because I have seen Plymouth more or less unfunctional, at least crippled, depending on the graphics card used and the drivers using it.
I have seen the development of Plymouth through Jaunty - Lucid - Maverick and now in Natty.
I have seen it first in Fedora (from Red Hat Enterprise Linux).
Admitting, it does not work, at least it does not fulfill what it was supposed to be.
Remember this:

Plymouth:
> Basically, the idea is that in the 30 seconds it takes for your machine to boot, you shouldn't be flickering through different display modes or staring at a horribly scaled frame-buffer splash. By setting the display mode appropriately, the transition between Plymouth and X is seamless, and with a matching Plymouth and GDM theme, you can do all sorts of visually appealing things.
 From: [http://ubuntuforums.org/showthread.php?t=965338](http://ubuntuforums.org/showthread.php?t=965338)

---

### Post by BigSilly on 2011-03-21
Yes I agree with your sentiments here Jennybrew and Harry33. Free software people point to Nvidia not playing well with Linux and releasing source code to enable the proper Plymouth functionalityin KMS, but we have Intel powered laptops here at home and neither of those work perfectly with Plymouth, with garbled text often interrupting an oh-so-brief-flash-past of a Plymouth splash.

Though I didn't care much for Karmic as a release, it had by far the nicest splash screen at boot. And yes, before anyone chimes in, it is very important imho. I'm tired of reading people say how there are more important things to fix in Ubuntu. There may well be, and I daresay I don't understand all the facts, but the list of things like this that don't function as they should piles ever higher, and it just doesn't look good imho. If it can't work for everyone, why do we have it?

---

### Post by deconstrained on 2011-03-22
Just use the uvesafb module for a better boot-time splash. It doesn't interfere with the proprietary module that gives you hardware acceleration for things like Compiz...

---

### Post by dino99 on 2011-03-22
Remember why plymouth was created and the nigtmare we got into karmic cycle:
 lot of users was begging for a better ubuntu look compared to OSX/MS. So plymouth hide the bootup dust under the carpet.

Later the forum was invaded by people (kids) whining about a faster bootup, so we got ureadahead.

All this means: more code to load, more dependencies, more headhache. Silly design really.

and the fan boys still crying: why my fatty distro is not a dragster ?

my solution: remove the metapackages, uninstall what is not needed, use gconf accordingly.

---

### Post by deconstrained on 2011-03-22
> **dino99 said:**
> Remember why plymouth was created and the nigtmare we got into karmic cycle:
 lot of users was begging for a better ubuntu look compared to OSX/MS. So plymouth hide the bootup dust under the carpet.
Oh god don't remind me. I had (and still have) luks devices that I unlock at boot. In Karmic there were times the splash got in the way of the only means to enter my passphrase that worked at the time - the text screen (which would come up after Plymouth crashed, before coming back again). And I couldn't even boot.

Somehow it has improved a lot since then, and I'm glad. Works almost flawlessly - 1280x720 is the best I can get but it's still really sleek.

---

