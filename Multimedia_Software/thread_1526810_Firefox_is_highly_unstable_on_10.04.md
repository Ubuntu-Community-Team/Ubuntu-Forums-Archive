---
title: "Firefox is highly unstable on 10.04"
date: 2010-07-08
forum: Multimedia Software
---

### Post by tim042849 on 2010-07-08
Note: I have a Gateway GT5422E with the nVidia chipset and the
nVidia Driver Version 195.36.24 installed (recommended version).
Like **all** versions of ubuntu and kubuntu that I have used 
in the past: **firefox is very unstable**. Firefox frequently
quits (just disappears) and worse yet, it is not unusual for X to
quit while in firefox and I will be dropped to the login screen.

These failures are likely to occur with flash videos and also from
amazon web pages. Furthermore, mplayer does not launch from links
to .wmv files. Which is really weird considering that I can launch
mplayer from Midnight Command when selecting .wmv files from my filesystem.

I wish to note also, that I have had none of these problems with
slackware 13 & 13.1 on the same machine.

I really like ubuntu and to recap, these problems described here have
persisted through several versions of ubuntu and kubuntu and I would
like to solve this once and for all.

Any and all suggestions are welcome.
thanks
tim

---

### Post by ajgreeny on 2010-07-08
This sounds like a configuration problem to me.

The most likely problem sounds like the graphics card causing the crashing of FF, though that seems a bit unusual, as nvidia cards are usually good and stable.  Have you looked for a newer driver of some sort, or even tried the open source driver, just to check if FF runs better with that?

As for links for wmv files not playing as you wish, the way they are dealt with will depend on the settings in your **FF- preferences- applications**, where you can alter the way things are done, and the various plugins you have added to FF for that purpose.  By default in Ubuntu the totem-mozilla plugin will play those links.  Personally I always remove totem-mozilla and add gecko-mediaplayer, which uses gnome-mplayer as its player.

---

### Post by tim042849 on 2010-07-08
> **ajgreeny said:**
> This sounds like a configuration problem to me.
;)A configuration problem present on every ubuntu or kubuntu install since 2006.
> 
The most likely problem sounds like the graphics card causing the crashing of FF, though that seems a bit unusual, as nvidia cards are usually good and stable.  Have you looked for a newer driver of some sort, or even tried the open source driver, just to check if FF runs better with that?

I presume you mean the driver that was installed originally? 
In previous installs I used the stock driver.
Can you advise on how to get back to that?
> 
As for links for wmv files not playing as you wish, the way they are dealt with will depend on the settings in your **FF- preferences- applications**, where you can alter the way things are done, and the various plugins you have added to FF for that purpose.  By default in Ubuntu the totem-mozilla plugin will play those links.  Personally I always remove totem-mozilla and add gecko-mediaplayer, which uses gnome-mplayer as its player.
Here's what happens when totem is selected:
1)Screen pops up. I pick 'totem'
2)I get an Error Alert:
> 
The playback of this movie requires a Microsoft Media Server (MMS) protocol source plugin which is not installed.

I will google the text above and check for the plugin.
I appreciate the reply. I hope we can get ubuntu squared away so it
runs like slack. Ubuntu sure is easier to work with (for me) and
in my book easy is good.
Hope to hear back on the driver issue.
thanks
tim

---

### Post by tim042849 on 2010-07-08
**P.S.** Just added **gecko-mediaplayer**
Clicked on a link, screen popped up, picked mplayer,
(I had disabled totem), screen went away. Lets find a
driver before tackling this again.
One step at a time ...

---

### Post by ajgreeny on 2010-07-09
> **tim042849 said:**
> ;)A configuration problem present on every ubuntu or kubuntu install since 2006.

I presume you mean the driver that was installed originally? 
In previous installs I used the stock driver.
Can you advise on how to get back to that?

Here's what happens when totem is selected:
1)Screen pops up. I pick 'totem'
2)I get an Error Alert:

I will google the text above and check for the plugin.
I appreciate the reply. I hope we can get ubuntu squared away so it
runs like slack. Ubuntu sure is easier to work with (for me) and
in my book easy is good.
Hope to hear back on the driver issue.
thanks
tim
Sorry, I don't have an nvidia card so am not totally sure about this, but I think if you rename your xorg.conf file and restart x the open source nv driver may be used instead of the proprietary one you have at the moment; not sure about that, however, and you may need to use the Hardware Drivers dialog to disable what you are using at the moment as well.

Have you changed the FF preferences setting for wmv files in Applications tab?  That should make gecko-mediaplayer run wmv files, if that's what you want.

---

### Post by tim042849 on 2010-07-09
From Tools->Administration->Hardware Drivers, one can pick any of 3 nvidia
drivers. Disabling all reverts to open source as I understand it. 
I was using the **recommended** driver. I disabled that (back to open source),
and saw that xorg.conf was deleted. I didn't like performance with the
open source, so now am using the second nvidia drive and I will see how that
goes. If instability persists, then I will try the third.

I installed the gecko plugin. Seems to play most wmv files thru the browser.
thanks
tim

---

### Post by lovinglinux on 2010-07-09
See [Firefox Optimization and troubleshooting](http://firefox-tutorials.blogspot.com)

---

### Post by tim042849 on 2010-07-09
> **lovinglinux said:**
> See [Firefox Optimization and troubleshooting](http://firefox-tutorials.blogspot.com)
There appear to be no references at that URI regarding the problems
that I have described. I.E. Firefox suddenly aborting. My personal
opinion is that this problem is rooted in ubuntu itself and has something
to do with hardware compatibility and likely video. Note above where I
indicated that I am trying a different driver: 
**Nvidia Accelerated Graphics driver (version 173)** and we will
see how that goes.

 thanks
  tim

---

