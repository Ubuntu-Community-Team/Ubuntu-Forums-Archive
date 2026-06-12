---
title: "Grub2 v1.99 background_image problem"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MAFoElffen on 2011-04-08
Ubuntu Natty 11.04beta1, Grub2 v1,99

With a Grub2 boot menu background image... after the image is set, we used to set color_normal-text_color,background_color with the text color as any rgb color and the background color to "black" which in grub, is supposed to be transparent...

This does not seem to be working in this version yet, as black is coming up as black, with the image behind it-- not as transparent.  Anyone else having this trouble?

---

### Post by tetobear on 2011-04-08
I have the same problem i set the background black but it doesnt make it transparent for the pic...

---

### Post by tetobear on 2011-04-08
Here a good thread...
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by VanR on 2011-04-09
I had that problem. I had to change out background jpgs until I found one that worked. Don't know why, but some of the images wouldn't show. Just a big black box over it.

---

### Post by VinDSL on 2011-04-09
LoL!  Love the avatar!  :D

I'm going to use a modded version, on another site...

---

### Post by MAFoElffen on 2011-04-09
> **VanR said:**
> I had that problem. I had to change out background jpgs until I found one that worked. Don't know why, but some of the images wouldn't show. Just a big black box over it.
You "are" correct... even thogh I have the stock grub images package installed, allot of the images in it will not display.  Once I found one that did work, then I noticed another problem-- 

When I did get an image to display, then the settings for menu_color_normal and  menu_color_highlight are inoperative, defaulting only to light-gray text/tranparent and highlight at black text/light-gray highlighting for the menu select item... no matter what you change them to.  at least for the image I found to work.

---

### Post by MAFoElffen on 2011-04-09
> **VinDSL said:**
> LoL!  Love the avatar!  :D

I'm going to use a modded version, on another site...
LMAO!!! I think ur mod is closer to the truth!

---

### Post by VanR on 2011-04-09
Here is the thread.
[http://ubuntuforums.org/showthread.php?t=1718521&highlight=grub+background](http://ubuntuforums.org/showthread.php?t=1718521&highlight=grub+background)

---

### Post by MAFoElffen on 2011-04-09
> **VanR said:**
> Here is the thread.
[http://ubuntuforums.org/showthread.php?t=1718521&highlight=grub+background](http://ubuntuforums.org/showthread.php?t=1718521&highlight=grub+background)
LMAO. I'm sorry, but that is good info for older versions of Grub2 and previous versions of Ubuntu...  Please do not take this wrong or personal, I am here to test, help and play nice.  I know my way around Grub and Grub2 enough to be dangerous..  :)

You would do better to look at the online Ubuntu Grub2 Doc's for updated instructions as per Grub2 releases and such. "tetobear's" link (above) was actually a good reference for some of the features not in the online doc's.

Saying that, "**THESE**" problems we are finding now - are new and different.  These problems are things that worked before in earlier releases of Grub2 and are not working now in this release.  Right? (*Should work, but is not.*)

We are doing our job here by pointing this out while this is still in "beta."  Hopefully, by us identifying these problems, we can either come up with some good work-arounds... or others can fix it before the time of the distribution release, right? If not, then a later update?  At least, if not fixed, we can say "yes, we know this is broke..."

But this is still early and besides >> This is actually an upstream from GNU Grub 1.99~rc1, release March 31, 2011... (Their doc's say March, but their wiki says 1-13-2011)  So we are beta testing with another release candidate...  I guess I should do my homework and look through the GNU Grub Doc's on this release candidate for changes they made and search through their bug logs for similar problems to see if it is GNU or down at the Ubuntu level.  

OR we could just report these to Ubuntu's lauchpad and let them find the problems... I, personally would like to play with this until I know for sure that it is really broken without some "other" way around it.  When I get to that point, I'll reference the launchpad bug number here, for others to "join" (meaning they have that problem too).

---

### Post by MAFoElffen on 2011-04-09
Okay... I went through the new GNU Grub manual for 1.99~rc1 and through the dev wiki.

Their bug tracking system is a little obscure.  There are some new features that Vladimi Serbinenko there refers to as "fancy menu".   The manual says that the menu theming is controlled by a separate text file.  I can see that Vladimir Serbinenko was working on "changes" to that on April 1st, so I am assuming there is "something."

This seems "upstream" and my course of action will be to report it to Ubuntu Launchpad... that way Ubuntu can re-enforce that there is a problem.  I'll comeback and edit this post to reference the bug number.

---

### Post by MAFoElffen on 2011-04-09
**Darn it!**  (LOL)  AS I write, grub changes are hitting the update/upgrade repositories for natty.  My server is updating packages now.

After I reinstall my theming changes back into the files, I'll see if it's fixed or still exists in that package update. 

EDIT-- Done, but no changes on these problems.

---

### Post by VanR on 2011-04-09
> **MAFoElffen said:**
> LMAO. I'm sorry, but that is good info for older versions of Grub2 and previous versions of Ubuntu...  Please do not take this wrong or personal, I am here to test, help and play nice.  I know my way around Grub and Grub2 enough to be dangerous..  :)

You would do better to look at the online Ubuntu Grub2 Doc's for updated instructions as per Grub2 releases and such. "tetobear's" link (above) was actually a good reference for some of the features not in the online doc's.

Saying that, "**THESE**" problems we are finding now - are new and different.  These problems are things that worked before in earlier releases of Grub2 and are not working now in this release.  Right? (*Should work, but is not.*)

We are doing our job here by pointing this out while this is still in "beta."  Hopefully, by us identifying these problems, we can either come up with some good work-arounds... or others can fix it before the time of the distribution release, right? If not, then a later update?  At least, if not fixed, we can say "yes, we know this is broke..."

But this is still early and besides >> This is actually an upstream from GNU Grub 1.99~rc1, release March 31, 2011... (Their doc's say March, but their wiki says 1-13-2011)  So we are beta testing with another release candidate...  I guess I should do my homework and look through the GNU Grub Doc's on this release candidate for changes they made and search through their bug logs for similar problems to see if it is GNU or down at the Ubuntu level.  

OR we could just report these to Ubuntu's lauchpad and let them find the problems... I, personally would like to play with this until I know for sure that it is really broken without some "other" way around it.  When I get to that point, I'll reference the launchpad bug number here, for others to "join" (meaning they have that problem too).


  Not sure what you mean since that thread I referred you to is only a few days old. Of course I am new here

---

### Post by MAFoElffen on 2011-04-09
Reported

**Please**, if you have this problem, join into the bug report here at the Ubuntu Launchpad:

Bug #756267 at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/756267](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/756267)

---

### Post by MAFoElffen on 2011-04-09
> **VanR said:**
> Not sure what you mean since that thread I referred you to is only a few days old...
No problems with you or that. I'm sorry that I didn't make myself understood, I guess. Thank you for your help.  Yes, it is only a week old, but if you look at his thread, his disclaimer says "he is **also** having theming problems in Natty" and with Grub2 1.99~rc1... just as we are.

Standard Grub2 background package that I used was via-
```
sudo apt-get install grub2-splashimages
```which installs previously Grub2 compatible images into:
```
/usr/share/images/grub
```But that is just a technique (one of many ways to do the same thing...)

---

