---
title: "Firefox 3.0.7 - no sound in streaming videos"
date: 2009-03-22
forum: Multimedia Software
---

### Post by Martango on 2009-03-22
Hello everybody.

I've been away from Ubuntu for some years (forced Windows user through my work), but now I'm trying to use Ubuntu again on my home PC. I don't consider myself an experienced Linux user, and I have this problem with the sound in all streaming videos in Firefox (both on Youtube flash video and anything else streaming Microsoft formats). I have tried to fix it myself via Google and this forum, installing a lot of different plugin packs, but it doesn't seem to work for me... I know theres a lot of threads in here about the lack of sound in Youtube, I think I been through it all, but nothing did the trick for me. Actually I installed so many different plugins, that I decided to start all over again, so now I'm using a brand new installation of Ubuntu and I'm hoping that some of you could help me (step by step) with this problem - maybe the sound in Youtube for a start?

Here is a little info about my system:

I'm running Ubuntu 8.10, 64 bit version with all available updates installed.
In the beginning I could not get the sound on the system to work at all. I have a Creative Audigy 4 card (the onboard sound is disabled in the BIOS). To fix the sound I had to allow my user to use audio devices in System -> Administration -> Users and Groups and also the Autodetect function in System -> Preferences -> Sound did not work. So I changed the settings to my sound card and that fixed the system sound. So I can play CD's without problems.

Since I'm now working on a clean installation, Firefox prompts me to install a flash plugin the first time I browse a page with flash animations. I can choose between 3 different plugins: Adobe Flash Player, Swfdec SWF player and Gnash SWF Player, which one should I choose to begin with?

I really hope you have the time and patience to help me.

Thanks in advance!

Martin

---

### Post by flo-alb on 2009-03-23
Hi everyone,

i have the same problem with my 32bit version of ubuntu 8.10.
No Sound at streaming video. Sound with mp3 files works fine.

So i observe this treat and hope i get a solution for my problem too.

CU Florian

---

### Post by gandaran on 2009-03-23
> **flo-alb said:**
> Hi everyone,

i have the same problem with my 32bit version of ubuntu 8.10.
No Sound at streaming video. Sound with mp3 files works fine.

So i observe this treat and hope i get a solution for my problem too.

CU Florian
for 32-bits system
is the sound problem only with flash videos or other media type, for every media type install the ubuntu-restricted-extras package (codecs) if it's only flash sound problem check which adobe flash version is installed, if it's flash 9 upgrade to flash 10 which should fix the sound issue, if it still wont work with flash 10 then you have to fix[ pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by flo-alb on 2009-03-23
Hi,

have a look at the following tread:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+youtube]("http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+youtube")

It worked fine for me ....

CU

---

### Post by gandaran on 2009-03-23
> Since I'm now working on a clean installation, Firefox prompts me to install a flash plugin the first time I browse a page with flash animations. I can choose between 3 different plugins: Adobe Flash Player, Swfdec SWF player and Gnash SWF Player, which one should I choose to begin with?

don't choose any, for 64-bits it's best you try the adobe 64-bits beta flash and install it manually, download it [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or to /usr/lib/mozilla/plugins, easy and done, restart firefox.

---

### Post by Martango on 2009-03-23
> **gandaran said:**
> don't choose any, for 64-bits it's best you try the adobe 64-bits beta flash and install it manually, download it [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or to /usr/lib/mozilla/plugins, easy and done, restart firefox.

Thanks - I installed the 64-bit beta flash and it works fine in firefox. So far so good - you don't happen to know how to fix the sound in Youtube? :)

---

### Post by Martango on 2009-03-23
> **flo-alb said:**
> Hi,

have a look at the following tread:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+youtube]("http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+youtube")

It worked fine for me ....

CU

I followed the guide, part A 1-5 and C 1-4, but it only got worse and now I have no sound on my system at all. I can't even play CD's anymore... :(

---

### Post by gandaran on 2009-03-23
> **Martango said:**
> I followed the guide, part A 1-5 and C 1-4, but it only got worse and now I have no sound on my system at all. I can't even play CD's anymore... :(
that guide is for 32-bits systems and no I don't know of any guide or fix for 64-bits, if you cant fix it install the new beta ubuntu 9.04 (due for release in april) I have read all issues related to pulseaudio have been fixed in 9.04.

---

### Post by markbuntu on 2009-03-23
The only problem with pulseaudio is that Ubuntu did not give you the tools necessary to configure it properly. Apparently they do not like the gui so they just left it out.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by muscl3s on 2009-04-12
> **Martango said:**
> Hello everybody.

I've been away from Ubuntu for some years (forced Windows user through my work), but now I'm trying to use Ubuntu again on my home PC. I don't consider myself an experienced Linux user, and I have this problem with the sound in all streaming videos in Firefox (both on Youtube flash video and anything else streaming Microsoft formats). I have tried to fix it myself via Google and this forum, installing a lot of different plugin packs, but it doesn't seem to work for me... I know theres a lot of threads in here about the lack of sound in Youtube, I think I been through it all, but nothing did the trick for me. Actually I installed so many different plugins, that I decided to start all over again, so now I'm using a brand new installation of Ubuntu and I'm hoping that some of you could help me (step by step) with this problem - maybe the sound in Youtube for a start?

Here is a little info about my system:

I'm running Ubuntu 8.10, 64 bit version with all available updates installed.
In the beginning I could not get the sound on the system to work at all. I have a Creative Audigy 4 card (the onboard sound is disabled in the BIOS). To fix the sound I had to allow my user to use audio devices in System -> Administration -> Users and Groups and also the Autodetect function in System -> Preferences -> Sound did not work. So I changed the settings to my sound card and that fixed the system sound. So I can play CD's without problems.

Since I'm now working on a clean installation, Firefox prompts me to install a flash plugin the first time I browse a page with flash animations. I can choose between 3 different plugins: Adobe Flash Player, Swfdec SWF player and Gnash SWF Player, which one should I choose to begin with?

I really hope you have the time and patience to help me.

Thanks in advance!

Martin

I'm in the exact same boat as you.  I too haven't tried using linux for years because I've been forced to use Windows.  Today I installed the 32bit version of 9.04 and I have the same problem with sound.  Sound outputs perfectly fine when watching any kind of avi, wmv, mp3, etc. locally but when I try to stream anything online in Firefox I don't get any sound.  This includes video sites like youtube and audio streaming sites like slacker.com.  In theory, the package "ubuntu-restricted-extras" should be all you need at least for youtube to work correctly but it's not.  

Alas nothing works no matter what I try to install via the package manager.  I've already spent a good 4 hours troubleshooting.  If I don't find a solution in the next 24 hours then I'm going back to Microsoft.  I guess Windows isn't so bad after all.  No one should need to go through this much trouble to get such a trivial plugin to work properly in a damn browser.

---

### Post by soltanis on 2009-04-12
Yeah you guys need to download the Adobe flash player, it works with ALSA (and maybe pulseaudio but I wouldn't know...I got so fed up with PA I uninstalled it).

Occasionally for some reason playing flash videos in Firefox will inexplicably mute my sound. To fix that I have to go to alsamixer, reset the volume levels and unmute master.

---

### Post by muscl3s on 2009-04-13
> **soltanis said:**
> Yeah you guys need to download the Adobe flash player, it works with ALSA (and maybe pulseaudio but I wouldn't know...I got so fed up with PA I uninstalled it).

Occasionally for some reason playing flash videos in Firefox will inexplicably mute my sound. To fix that I have to go to alsamixer, reset the volume levels and unmute master.

I did install Adobe Flashplayer... like I just mentioned in my post.  It doesn't work.

---

### Post by muscl3s on 2009-04-13
Well I solved my problem finally this morning.  Apparently there was some kind of problem with packages conflicting with each other and "completely removing" them via the packet manager wasn't doing the job.  I used the administration application "computer janitor."  I noticed as soon as I opened the program that packages that were supposed to be completely uninstalled were not because a lot of them were pre-selected in the list by computer janitor.  I ran the removal tool, rebooted, and suddenly I could hear sound in youtube and slacker.com worked finally.  I wish I had a more precise reason why and how my issue was fixed but I'm just glad it works.

---

### Post by Martango on 2009-04-13
> **muscl3s said:**
> Well I solved my problem finally this morning.  Apparently there was some kind of problem with packages conflicting with each other and "completely removing" them via the packet manager wasn't doing the job.  I used the administration application "computer janitor."  I noticed as soon as I opened the program that packages that were supposed to be completely uninstalled were not because a lot of them were pre-selected in the list by computer janitor.  I ran the removal tool, rebooted, and suddenly I could hear sound in youtube and slacker.com worked finally.  I wish I had a more precise reason why and how my issue was fixed but I'm just glad it works.

I still have this problem - for 3 weeks now, and I'm also beginning to loose my patience and considering installing an old WinXP version that is lying on my table. But right now I'm back on the 32 bit Ubuntu 8.10, and I would like to try what you did, before I finally give up. Can you tell me which packages you "partly" removed before you made the computer janitor clean-up? Which flash player did you install? And where can I get this computer janitor program? I can't find it through the package manager.

---

### Post by Martango on 2009-04-17
Today I realized that I actually do have sound on the flash videos! :eek: Problem is that the sound from the flash video is transferred to my onboard sound chip instead of my PCI Audigy card - which is my preferred sound card. Strange thing is that when I choose autodetect in the sound settings (preferences -> sound) my Audigy card will not play, only my onboard sound is detected with autodetect. So I have to choose the Audigy card on the drop down list, either the playback ALSA or playback OSS. With that setting the sound was working on my system - except the streaming flash sound in firefox (like youtube etc.) but also system alerts and sound effects like the login tune does not play. Today I was changing my speakers, and by "accident" I connected the speakers to the motherboard output connector, and bling... sound was playing in youtube. Is there any way I can change sound settings in the adobe flash player so the sound is redirected to my PCI sound card? Or even better - can I set my PCI sound card as the default sound card, so the onboard sound chip will be ignored? I don't think that my PCI sound card is properly installed or detected by the system.

---

