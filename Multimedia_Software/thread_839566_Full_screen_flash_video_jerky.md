---
title: "Full screen flash video jerky"
date: 2008-06-24
forum: Multimedia Software
---

### Post by gammyhand on 2008-06-24
My 9800pro and athlon 64 3200+ never had any problems in XP with full screen flash movies and last time I installed ubuntu it was fine but for some reason in 8.04 it gets a bit jerky on full screen. Sound is usually synced and never breaks up though.

Any suggestions? I am using the proprietary ATI drivers.

---

### Post by kanin_te_sova on 2008-11-14
Hi!

Well, this isn't exactly something that fixes this problem. 

**It's a WORKAROUND** I figured out. It takes a few small steps but works if you want to view fullscreen without the jerkiness  (some flash movies seem not to have this problem though, hmm)! 

Anyways,

**I think you'll have to have *Compiz* running..** U know the *"Extra"* (3D hardware accelerated GFX) eye-candy stuff ticked under *Visual Effects*.

You want to use the _ZOOM effect_!

Now watch a flash movie. **Do NOT** do it FULL-SCREEN!

**Now do this:** 

Press and hold the *SUPER* button (that button is, for those of you who does not know it, the *"WinDoze"*-button on your keyboard) and scroll your mouse-wheel!

Now it's ZOOMING - Behaving in a way that will center/lock-on to your mouse-pointer! 

GREAT! [B]THAT was EASY!
[/B]
**BUT!**

Oh NO! That Flash *"hand"* sitting there [COLOR="Red"]like an ugly glove[/COLOR] *right in the middle* of your now - quite smoothly, (although "fake") running **"FLASH FULLSCREEN"**!

**What to do?** (If you don't get bothered by this then skip this part!)

[B]# 1. Go to the *Advanced Desktop Effects Settings* under /System/Preferences in the "start" menu.

# 2.Go to the *Enable Enhanced Zoom Desktop* settings under *Accessibilities*.

# 3. Click the *Mouse Behaviour* tab (third from the left) and then UNTICK the *"Sync Mouse"* option.[/B]

**That's it. **

**But: !!!**

**Now you will MANUALLY have to try and match the "minimized" flash/mozilla window you are watching as much to THE MIDDLE of your screen as possible!** Takes some SLIGHT "tweaking".

**But - [COLOR="red"]you now get rid of the annoying hand[/COLOR] :)**

This **WORKAROUND** may seem troublesome! **But you get the hang of it!**

If I REALLY want to watch a flash worth watching (that has the jerky quirk) it is definetly worth it... :popcorn:

If some has a PROPER fix for this JERKY full-screen problem please let me/us all know! (some at the Adobe team maybe? don't know)

In the mean time - let's be nice.

//emil

---

### Post by psyke83 on 2008-11-14
That's the most ridiculous - and excellent - workaround for jerky Flash. Simply awesome ;).

By the way, what happens if try "real" fullscreen after you disable unredirected windows for compiz (you can edit with gconf-editor if you can't find it in the CCSM application)? I can't try it here as I'm stuck on Windows, but it may help (or not).

---

### Post by kanin_te_sova on 2008-11-14
> **psyke83 said:**
> That's the most ridiculous - and excellent - workaround for jerky Flash. Simply awesome ;).


Ha ha thanks! :lolflag:

I will look into it - I'm getting quite tipsy here... Too much Wine... 

Well some "linux nerd " humour for ya... ;)

Psyke83 - If you find something else out that might help. PLZ reply.

Cheers 

//e...

---

### Post by kanin_te_sova on 2008-11-15
Hello again psyke83.

I tried disabling the *"Unredirect Fullscreen Windows"*.

And yeah - **actually it seems to fix ANOTHER weird bug**. A bug that seems to have no predictability!

**It's about being able to go fullscreen with Flash at all!**

Sometimes when I start a session Flash will not go fullscreen at all - it just "flashes" (pun NOT intended ;)) you a fullscreen, [COLOR="Red"]but won't stay that way! Aarrrgh![/COLOR] ](*,)

**Sometimes this happens - sometimes not!**

In the past I have actually successfully "FORCED" Flash into fullscreen by clicking the *"fullscreen icon"* **multiple times REALLY fast**, AK47-style, crossing my fingers - just hoping it would stick to fullscreen, he he. This used to work sometimes - I also had to disable the *"Enable Hardware Acceleration"* in the *Flash Settings* dialog sometimes!

**Anyhow, disabling the *"Unredirect Fullscreen Windows"* in Compiz actually fixes THIS particular annoyance. **

[B]But SOME videos are STILL JERKY - and some NOT! Regardless this setting being enabled or disabled. 
[/B]
It's like the lottery - u never really can be sure! #-o

For the record I have Ubuntu 8.04 (Studio edition) 2.6.24-21-rt kernel. Nvidia prop. drivers.

Well I don't know why this problem persISts? 

So, if I come across jerky Flash I will do my little WORKAROUND 'til this problem get sorted.

Anyhow thanks for the tip! Maybe this works for someone else!


All the best


//emil

---

### Post by kyleflan on 2009-03-25
> **kanin_te_sova said:**
> Hi!

Oh NO! That Flash *"hand"* sitting there [COLOR="Red"]like an ugly glove[/COLOR] *right in the middle* of your now - quite smoothly, (although "fake") running **"FLASH FULLSCREEN"**!


Another solution to this is to press super+l once you have the video zoomed and positioned correctly. This will "lock" the zoom position in place. Then you can move your mouse out of the way to the corner of your screen.

---

### Post by kyleflan on 2009-04-29
> **kyleflan said:**
> Another solution to this is to press super+l once you have the video zoomed and positioned correctly. This will "lock" the zoom position in place. Then you can move your mouse out of the way to the corner of your screen.

For those of you with CCSM 0.8.2, to achieve this you have to go to Enhanced Zoom Desktop -> Zoom Area Movement and set "Toggle zoom area lock" to some key combination, such as Super+L.

---

### Post by ashgray2 on 2009-04-29
Great post! Thanks for that. I'm having the same problem. Now I can do the same workaround. Real Help!

---

### Post by Benzjaminz on 2009-05-03
Classic fix. I'll definitely use it until I have time to do a proper fix on Jaunty.

---

### Post by Valir on 2009-05-03
This excellen solution by psyke83 worked for me: [http://ubuntuforums.org/showthread.php?t=1130582&highlight=flash+problem](http://ubuntuforums.org/showthread.php?t=1130582&highlight=flash+problem)

be sure to try the tile = true option

---

### Post by thefrioman on 2009-05-03
Ha ha this is the best solution yet i have searched every where and i even installed the modified kernel and drivers

such a simple workaround oh bye the way just hit the escape key and the pointer disappears

---

### Post by sadahalli on 2009-08-11
Great workaround Guys... Works beautifully.......

---

### Post by creepytennis on 2009-09-24
Hi,

The problem is that the Adobe Flash Player has a series of completely absurd 'tests' it performs to decide whether it will allow hardware acceleration on Linux. Most of the time it decides to disable hardware acceleration even on systems where it would otherwise work perfectly. The "Enable hardware Acceleration" option which appears when you right-click on the player is more or less ignored. You can read more about this here: [http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Luckily there is a quick and easy fix which will enable hardware acceleration on many systems. The solution below works with 32 bit Flash: 
 
1. sudo mkdir /etc/adobe 
 
2. sudo nano /etc/adobe/mms.cfg 
 
3. Paste "OverrideGPUValidation=true" (without quotation marks) 
 
4. Restart Firefox. 
 
The above sadly does not work with the 64 bit Flash, which at the moment appears to be entirely incapable of hardware acceleration.  
 
(From here: [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692))

---

### Post by ewan86 on 2010-01-03
> **creepytennis said:**
> Hi,

The problem is that the Adobe Flash Player has a series of completely absurd 'tests' it performs to decide whether it will allow hardware acceleration on Linux. Most of the time it decides to disable hardware acceleration even on systems where it would otherwise work perfectly. The "Enable hardware Acceleration" option which appears when you right-click on the player is more or less ignored. You can read more about this here: [http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

Luckily there is a quick and easy fix which will enable hardware acceleration on many systems. The solution below works with 32 bit Flash: 
 
1. sudo mkdir /etc/adobe 
 
2. sudo nano /etc/adobe/mms.cfg 
 
3. Paste "OverrideGPUValidation=true" (without quotation marks) 
 
4. Restart Firefox. 
 
The above sadly does not work with the 64 bit Flash, which at the moment appears to be entirely incapable of hardware acceleration.  
 
(From here: [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692))

Hi,

I did this even though I wasn't quite sure I had done it right, it seems slightly less jerky but now I get random lines of interference across the screen. How can I undo the above changes??

---

### Post by Xelyc on 2010-05-22
I Stumbled upon an easier fix for this issue and figured I would share.

Don't know quite how to do this with the command line though I am pretty sure it's possible. I  simply used the Compiz Configuration Settings Manager GUI (can be found in Ubuntu Software Center)

Run it then, click on General Options Icon

In General TAB,
Make sure Unredirect Fullscreen Windows feature is disabled.

In Display TAB
Set Texture filter option to "Best"
Enable Sync to VBlank 
(optional) Set your refresh rate to your monitors capabilities same with output and  disable the auto detection 

And That's it!
You should have crystal clear video resizing when you use the normal player Fullscreen button, 
No more messing around with compiz zoom and all that stuff that can get annoying after awhile. ;)

---

