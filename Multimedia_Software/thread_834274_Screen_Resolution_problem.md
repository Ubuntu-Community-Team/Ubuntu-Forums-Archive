---
title: "Screen Resolution problem"
date: 2008-06-19
forum: Multimedia Software
---

### Post by flyingsolo on 2008-06-19
I've been searching posts & trying to fix a display issue but unsuccessfully.
background:  ATI X1400 graphics card; proprietary driver
widescreen monitor on Dell laptop

When I display photos in Eye of Gnome, I get a vertically squished appearance.  If I try System-->Pref-->Screen Resolution, I get the following:

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

I can vary resolution if I use: gksudo displayconfig-gtk and currently it is set for the highest resolution available from the drop down list (1400x1050).  The display will allow 1920x1080 but that isn't allowed/available in drop down list of resolutions.

One more thing--if I try to run a slideshow or full screen image from Eye of Gnome, the display erratically displays blocks of the image and flashes on/off, eventually showing the photo but then doing the same again when it transitions to the next photo. (hard to advertise linux to friends when that happens!)

Sorry for being lengthy but wanted to be complete.  Any help would be greatly appreciated.

---

### Post by pietjanjaap on 2008-06-19
Restart in safe mode,
then use the last option, something with x,
Here ubuntu will search and indentify your videocard and monitor.
then reboot,
and install your videocard driver(i use envy).

---

### Post by flyingsolo on 2008-06-19
Thanks pietjanjaap--this has fixed the vertical squishing issue.  I still have a problem using the fullscreen or slideshow viewing of images in EOG.  As I said before, it seems to try hard to show the image but throws up blocks of the image in a very odd manner until it paints the image and then starts the same process again as it transitions to the next image either in the slideshow function or just using forward/back buttons to go to other pictures.  I've been using Ubuntu for three years on a desktop and this laptop with all the various previous versions but never saw this before.
Any ideas anyone?  Maybe reinstall eye of gnome?

---

### Post by Pjotr123 on 2008-06-19
Disable the visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

### Post by flyingsolo on 2008-06-19
Well, thank you Pjotr123, that did the trick!  But can you explain to me why the desktop effects was interfering with EOG?  I only had it on the 'Normal' setting so I had hoped it wouldn't be sucking to much system resources.

---

### Post by Pjotr123 on 2008-06-19
Well, it's a rather heavy feature, even at "normal". Too heavy for older video cards, usually. 

Oh well, it's only eye candy...  :-)

---

### Post by flyingsolo on 2008-06-19
'Older video card'!!  Geez!  This laptop is just a few years old!
But, joking aside, I think there must be something else not quite right because my son's friend was visiting recently and I know he has the same laptop but bought his just a few months before me.  And yet, he ran a slideshow just fine even though he has a lot of eye candy running (3D cube, wobbly windows, fire writing etc)  In fact, it was because I saw his run so well that I began to track down these issues.  Unfortunately he's now away at summer camp & not handy to ask about his setup.

---

### Post by Pjotr123 on 2008-06-19
Well, you might try to increase the RAM-portion of the video card, if it's one that uses shared RAM memory. You can do that in the BIOS of your laptop. 256 MB RAM is preferable. However, this decreases general RAM for the applications...

---

### Post by flyingsolo on 2008-06-23
Though my resolution problem is fixed, now I have serious slow down of the machine, mainly related to graphics, I think.

Example, if I type text, there is a visible delay between key entry and characters showing on screen. If I open Amarok, it takes a long time to write the playlist to the screen. If I open some photos, it takes time to switch to next photo in collection and you can see the image being painted in blocks. If I click on the date at upper right to see map and to do list, nothing happens and usually the panels (top & bottom) freeze!

I've posted this in the Beginners' question area but maybe it is really related to my graphics problems so thought I should ask here again.
Thanks.

---

### Post by Pjotr123 on 2008-06-24
How much RAM memory is there in your machine?

---

### Post by flyingsolo on 2008-06-24
2 G ram; should be plenty, I would think.

---

### Post by Pjotr123 on 2008-06-24
> **flyingsolo said:**
> 2 G ram; should be plenty, I would think.

Definitely. Hmmmm....

Do this:

Applications - Accessories - Terminal
type: top
press Enter

Which processes are eating your resources most heavily?

---

### Post by flyingsolo on 2008-06-24
Here is a typical top set of values being used.  Looks like no big demands to me.

> top - 09:45:07 up 22 min,  2 users,  load average: 0.08, 0.23, 0.26
Tasks: 152 total,   3 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.5%us,  1.4%sy,  0.0%ni, 92.4%id,  0.0%wa,  0.8%hi,  0.0%si,  0.0%st
Mem:   2074548k total,   964284k used,  1110264k free,    95164k buffers
Swap:  4072468k total,        0k used,  4072468k free,   424692k cached
Change delay from 3.0 to: 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6705 michael   20   0  239m 105m  25m R   13  5.2   2:53.89 firefox            
 6208 michael   20   0  131m  38m  25m S    7  1.9   1:25.42 amarokapp          
 6152 michael   20   0  222m  67m  18m R    4  3.4   1:33.00 Xgl                
 6049 michael   20   0  7620 4724 1912 S    1  0.2   0:01.04 gconfd-2           
 6665 michael   20   0 73936  18m  10m S    1  0.9   0:01.26 gnome-terminal     
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.28 init               


sorry, that doesn't cut/paste so well,  FF = 13%, amarok 7%, Xgl 4%

Just noticed, if I open Amarok and it starts trying to paint its screen, the Xgl in top jumps to 99 or 100%.

---

### Post by Pjotr123 on 2008-06-24
It appears that you're using two topics for this one problem:
[http://ubuntuforums.org/showthread.php?p=5251081#post5251081](http://ubuntuforums.org/showthread.php?p=5251081#post5251081)

Please don't do that; it's confusing and creates unnecessary work.

From that other post I see that you're not using the right restricted driver yet: you don't want the Mesa, but the fglrx. Even the open source "ati" is much better than the Mesa.

For the time being, I suggest you switch back to the "ati". No 3D acceleration, but your performance problem will be over. Perhaps somebody else can help you from there, with installing the right restricted driver.

Greeting, Pjotr.

-edit-

I'm sorry, I was too harsh: you said so yourself. Missed that line.  :-)

---

### Post by flyingsolo on 2008-06-24
Sorry for the confusion of two posts but originally I thought this was a new problem so posted on the beginner list but referenced this post in case the two were linked--that's my ignorance not knowing whether the 'fix' for the screen resolution issue was the cause of the new slow problem or if they were  independent issues.

---

