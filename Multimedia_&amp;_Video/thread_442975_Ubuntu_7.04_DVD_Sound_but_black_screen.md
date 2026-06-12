---
title: "Ubuntu 7.04 DVD Sound but black screen?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by esoterica on 2007-05-14
I have already followed all the steps in this How-To for getting DVD's to work, everything there seemed to go perfectly...

Enabling Multimedia in Feisty (HOW-TO)
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

I've rechecked files referenced in that post and everything seems to match up exactly.

When I insert a commercial and legal movie into my DVD burner drive Totem Movie Player 2.18.1 auto runs and I can hear the sound of the movie just fine, however the screen for the video image part is black. When I go to the menu while the sound for the DVD is playing I click on "Play Disc" and it gives me this error message:

> 
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.


I've tried some other media players on here like Mplayer and this gxine 0.5.11, gxine which won't even play the audio, for example gxine tells me:

> 
No demuxer found - stream format not recognised.


I'm not sure which player to use, I don't have a preference, just one that actually works. So what is missing from all the instructions I could find on playing DVD's that's actually needed to get them to play?

I went back and followed all of these instructions instead of the above How To post, the instructions seem to contain the same info but a little more, the problem still remains the same though.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

and 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I also don't even see an icon listed to run this Totem Program from my applications list, since it seems to be the closest I have to anything that at least almost works I'd like to add it to the applications list somehow once I get it actually playing the video and audio of my DVD's. The only way I can even see to fire it up now to retest is by removing and reinserting the DVD, I'll worry about adding it to the list though later, for now I'd just like to watch some movies I rented.

It's been a while since I've used Linux, there's always been something stupid like this that's happened to keep it from winning my heart over, I'd really like it to all work this time around because I want to keep it. It's annoying to have to deal with all this hunting down and trying to install all this different stuff with archaic names and multiple versions, but it's even more annoying when after it seems like you've done all that it still doesn't work. 

Any ideas what step I may have missed here that the audio of DVD's work but no video?

I ran everything from the command line and nothing reported any errors when doing it.

---

### Post by esoterica on 2007-05-14
Have people been having better luck playing DVD's by ditching Unbuntu and trying Linux Mint instead?

I'd really like for the first time in my entire life to finally have a Linux system where everything actually worked on it so I could use it on a regular basis and spend more time learning Linux and less time just trying to get it to work. So far Ubuntu seems to be the closest I've yet to see for an out of the box working experience, but these little bugs like this are still discouraging.

---

### Post by esoterica on 2007-05-14
Here's an update just incase anyone else is trying to find a solution to this same problem. I think I found the answer here...

[https://answers.launchpad.net/ubuntu/+source/totem/+question/6099](https://answers.launchpad.net/ubuntu/+source/totem/+question/6099)

I had clicked on System >> Preferences >> Desktop Effects

and enabled that despite the warning messages, I guess this installs Beryl, though it doesn't specificly tell you this in the warnings or anywhere else I could find.

Anyhow, I opened that again and clicked the "Enable Desktop Effects" button once again thinking maybe this would turn the experimental desktop effects options off, it didn't, I still have the translucent user bars, but, the Video and sound does play when I run DVD's now, the quality is pathetic, but it does play so I'll give it that and be happy about it for now.

Is there some way I can undo this desktop effect I've enabled?

It looks like for now it's just going to lead to more problems than it's worth when someone else here suggested I enable it the other night.

---

### Post by esoterica on 2007-05-14
P.S.S.S.S.S.S.S

Someone should add this info to the Sticky on How To enable DVD's, or start a new sticky listing problems you may experience when enabling this Desk Top Effects option.

The error messages would have never led me to think this had anything to do with the problem and I see others who posted similar problems with no working suggested fixes.

Also, that external link specifies this is a problem with ATI cards, just for the record I'm not using an ATI graphics card, it's an Intel 950, but the same problem and fix applied.

---

### Post by hamishw on 2007-05-14
Aha!!!
I have been getting the same problem with divx / avi / vcd play back. I will try the desktop effects solution and let you know what happens. 
Thanks for being persistent!
Hamish

---

### Post by esoterica on 2007-05-14
So far so good, I haven't been able to figure out yet how to uninstall or undo the Desktop Effects, but so far everything seems to be working, including the desktop effects. Haven't tried to burn a DVD yet, so I can't confirm if that works or not, but it will play them, there's no menu options in Totem, it just goes directly into playing the DVD, but I think I read about a different DVD player app somewhere that was a little more modern and supported some of these more common features.

---

### Post by boterbram on 2008-04-16
The solution for me:

[http://www.uluga.ubuntuforums.org/showthread.php?t=729034](http://www.uluga.ubuntuforums.org/showthread.php?t=729034)

---

