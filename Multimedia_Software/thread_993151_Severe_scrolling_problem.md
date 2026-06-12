---
title: "Severe scrolling problem"
date: 2008-11-25
forum: Multimedia Software
---

### Post by Ouguiya on 2008-11-25
Hello everyone!

Today I am writing because of a very nasty problem which I haven't been able to get a hold of, and I hope that any of you may be able to help me.

Problem Description: The Problem looks like this: In almost any program, whenever I scroll up or down, there appears to be some kind of display problem. The lower part (when scrolling down) get's squished together, and ramains as such. When scrolling slower, the text is squished more tightly, while when scrolling faster, it almost appears as if the same text is written twice on the page, although it isn't. Makring the relevant text with the mouse for example then shows the correct text, but still the squished one only partially dissapears.This means that when I scroll down for a while, the entire text becomes almost not readable. I have to click on another program, then on the one expierencing the problem again to resolve this matter.

Solutions already tried: 
-Standard troubleshooting stuff, such as rebooting, searching around the internet, scrolling in diffrent modes, etc.
-Tweaked around the restricted driver settings to see if it had to do something with it. But no matter what I change about my nvidia, the problem remains firmly.

Observations: This problem seems to arrise particularly often when more than 2 applications are open, so my guess is, that this may be a RAM problem, but seriously: If 3 programs already hammer out the ram so much that I can't scroll anymore, then something is really pulling a lot of memory...

Hardware specifications: I have loaded my hardware specifications into a html format, for anyone wishing to look deeper into the problem.

I am thankful for any help anyone can provide me.

Thanks in adavance,

Ouguiya

---

### Post by Ouguiya on 2008-11-26
bump - Please... I beg of you. Does noone have a solution to this problem?

---

### Post by psyke83 on 2008-11-26
This problem is caused by compiz and the NVIDIA driver. There are some corruption issues in the current driver, but you may be able to overcome this problem.

You should follow the instructions in [this]("http://www.nvnews.net/vbulletin/showthread.php?t=118088")* post and also disable DynamicTwinView (if you only have a single screen set up). For an explanation of the latter, see [here]("http://ubuntuforums.org/showpost.php?p=6197465&postcount=23").

*Note: the current beta driver incorporates these tweaks by default, but it's not necessary to upgrade, as the stable driver works fine (when configured correctly).

---

### Post by Ouguiya on 2008-11-27
Dear psyke83,

Thank you for your reply. I have set the settings as you recommended, and also followed the instructions from the post you kindly provided.

I will test the display for the day, see if the problem arises again, and will then edit this post to tell if it worked or not.

Thanks again for your help!

Yours,

Ouguiya

---

### Post by Ouguiya on 2008-11-27
Update: Ok, sadly, these settings didn't work, the problem still persists. Disabling dynamic twinview may have been a good alternative, but then I wasn't even able to switch screens any more (from neither the nvidia control center, nor the "Screen resolution" window).

As I like to have my small laptop display on my huge screen at home, this is a feature I do not really want to miss.

A new solution: 
Since psyke83 told me that this is a problem between compiz and nvidia, I started digging a little bit. Given the post he provided, it suggested that compizconfig automatically set the refresh rate to 50, when it should be 60 (on most displays).

Now, although probably all more advanced users already figured this one out, I thought I should add it here if someone like me who doesn't know much yet about ubuntu or linux comes by with the same problem:

In the Compizconfig window (Accessible under System - Preferences - Compizconfig Settings manager) there is, on the top, a preference button labeled: "General options". When clicking on this, there is a tab on the top which states: "Display settings".

There, I was able to find a slider for the refresh rate, and, as told by the other post which psyke83 provided, it was indeed set to 50. The good news is that this setting can be changed, which I did.

Up till now, the problem has not appeared again. I have to play around with the vsinc settings in nvidia-config and compizconfig, but I hope that this solves the problem for good.

Thanks again for all your help psyke83!

Yours,

Ouguiya


Edit: I found that if you enable vsync, this fix does not work. If however vsync is disabled in the compizconfig (I haven't found this necessary in nvidia as of yet), this solved the problem for me (at least as far as I can tell now)

---

### Post by psyke83 on 2008-11-27
There are two important gconf keys in compiz:

/apps/compiz/general/screen0/options/detect_refresh_rate
/apps/compiz/general/screen0/options/refresh_rate

If "detect_refresh_rate" is enabled, the "refresh_rate" value is completely ignored (which I suspect is happening for you). You shouldn't edit these keys - instead, disable the DynamicTwinView option so that compiz can correctly detect the refresh rate.

See: [http://ubuntuforums.org/showpost.php?p=6197465&postcount=23](http://ubuntuforums.org/showpost.php?p=6197465&postcount=23)

P.S. You should re-enable vsync in compiz, otherwise these settings don't do anything. Your videos will tear if vsync is disabled.

---

### Post by Ouguiya on 2008-11-27
Hello again.

Sorry to warm this post up, but, as psyke83 already noted, my idea did not work.

I tried playing around with the settings - nothing helped, neither in compiz, nor in nvidia.

I then tried psyke83's approach, but, as I think I stated above, disabeling dynamic twinview stops me from switching my screen, which is very annoying. I want to at least be able to change the screen. (I do not really need twinview, but switching from one screen to another is necessary in my case).

Next, I also tried the fix which was kindly provided by psyke83. I found out that when following all instructions to the letter, this bug does indeed go away, but a new one appears: After running the command "nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1", my computer starts having an incredible time-lag. All applications take minutes to launch or perform an action. This get's especially ugly when the Avant window navigator wishes to push a row on the horizontal. Nothing works during those moments.

I wouldn't really want to give up on AWN, which leaves me stuck between a rock and a heartbeat.

I plan on informing the guys over at nvnews as well, I hope they may have an answer to this problem.

Yours,

Ouguiya

---

### Post by Ouguiya on 2008-11-28
Bump - any more comments?

---

### Post by tmegbert on 2008-12-04
I was having the exact symptoms you describe.
I changed the refresh rate in compiz from 50 to 60 and now I can scroll my firefox.  I haven't seen any side effects yet.

thanks for the info.

---

