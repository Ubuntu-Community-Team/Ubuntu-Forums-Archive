---
title: "Intrepid flash problems using flashplugin-nonfree"
date: 2008-11-19
forum: Multimedia Software
---

### Post by sdegrace on 2008-11-19
I have recently upgraded from Hardy to Intrepid on my Compaq Presario 2100 laptop. After the upgrade, I am having strange problems with some flash video using flashplugin-nonfree with fully-updated Firefox 3. Reinstalling flashplugin-nonfree has no affect on the problem.

[LIST]
[*]When the logged in user is in the administrator group, most flash application work. E.g., youtube works.
[*]However, some sites have problems such as lack of video or lack of sound and video. E.g., theonion.com.
[*]When the user is logged in and doesn't have administrative privileges, it seems like less sites work - e.g., the Scramble game on Facebook works for an administrative user but not a non-asministrative user (the non-admin user is told they need to install Flash, but installing it locally on their account does nothing).
[/LIST]

Does anyone have any suggestions about how to address this weird problem?

---

### Post by psyke83 on 2008-11-19
> **sdegrace said:**
> I have recently upgraded from Hardy to Intrepid on my Compaq Presario 2100 laptop. After the upgrade, I am having strange problems with some flash video using flashplugin-nonfree with fully-updated Firefox 3. Reinstalling flashplugin-nonfree has no affect on the problem.

[LIST]
[*]When the logged in user is in the administrator group, most flash application work. E.g., youtube works.
[*]However, some sites have problems such as lack of video or lack of sound and video. E.g., theonion.com.
[*]When the user is logged in and doesn't have administrative privileges, it seems like less sites work - e.g., the Scramble game on Facebook works for an administrative user but not a non-asministrative user (the non-admin user is told they need to install Flash, but installing it locally on their account does nothing).
[/LIST]

Does anyone have any suggestions about how to address this weird problem?

Make sure your non-administrative user is a member of the following groups: audio, pulse, pulse-access and pulse-rt.

It also won't hurt to ensure you have PulseAudio configured properly. See the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide

---

### Post by sdegrace on 2008-11-19
Well, I really didn't expect this to work, because there has not been the slightest sign of any problem with the audio (where flash is not working it is either acting like it is altogether absent, or else there is sound but no video).

However, I did all of the steps (common and intrepid) in the article you linked, and I added all my users to the groups specified. I was surprised to see that for my non-admin user, all Flash is now working, including the examples in my list of Scramble on Facebook and videos on The Onion. So thanks!!

There is absolutely no change in symptoms for my administrative user, though - most flash works, but some sites, theonion.com being the prime example, are still giving sound but no video. Any suggestions about that?

---

### Post by cha0s on 2008-11-23
Same here. No onion for me, which makes me very sad indeed =(. The audio seems to work, but there's no video. youtube.com works fine.

---

### Post by alcapone-g on 2008-11-24
I have the same problem. It is no video on yahoo.com. I did find out as mutch that is coused by adobe flash plugin. I did find some web site that gave me an exact solution what to do. I did what was showed on it and my video started working. Than I reloaded my ubuntu 8.10 and lost the web site. Now I can not get firefox to play video again. All what I remember it was something about loading restricted plugins from: deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free, but it is not all.

---

### Post by alcapone-g on 2008-11-24
From Synaptic Package Manager

Any flash has to be uninstalled example:
gnash
swfdec-mozilla

and than install :
flashplugin-nonfree 
flashplugin-nonfree-extrasound.
Embeded video in firefox starts working.

---

### Post by sdegrace on 2008-11-24
I checked and made sure I had no flash-related things other than flashplugin-nonfree installed, and I installed flashplugin-nonfree-extrasound. No dice, still sound with no video at The Onion. Anyway, theonion.com works for some (non-admin) users on this computer. It doesn't work on my own account, which is part of the admin group, if that matters.

---

### Post by cha0s on 2008-11-25
Huh, same here. My mom's account can use that stuff no problem, but my user in the Admin group, can't!

---

### Post by cha0s on 2008-12-09
Hey, just wanted to say I found that this is in fact a cache problem! If you empty your firefox cache, you can view ia video. For me anyways, it's like you can view one, then if you try to view another, you have to clear the cache again.

Haven't looked deep enough to know if it's the site/firefox yet, but that's a solution for now.

---

### Post by sdegrace on 2008-12-10
This solution does not work for me.

---

### Post by cha0s on 2008-12-25
Try navigating to the page with the video you'd like to watch, then hit ctrl-shift-del, then confirm you'd like to empty the cache, then hit F5 to refresh. It's not a one-time thing... it seems you have to clear the cache before watching ANY video on the onion... at least for me.

Try and post back if it helps...

---

### Post by sdegrace on 2009-01-07
No, I'm afraid it doesn't do anything, but thanks for your suggestion.

---

### Post by theether on 2009-03-10
Hi,

Had similar problems post upgrade. Turned out to be the wrong version of libnss3 is installed:

Flash not working with Firefox 3 on Ubuntu Intrepid using flashplugin-nonfree after upgrade from Hardy
[http://theether.net/kb/100107](http://theether.net/kb/100107)

Cheers.

---

### Post by audiosteve on 2009-06-21
I had the same issue with Intrepid.
Using Synaptic, I completely uninstalled all Pulse elements. Basically anything starting with pulse**** or libpulse**** was trashed. I then rebooted and everything worked great. Getting rid of Pulse and just using alsa seemed to be the solution for me.

---

