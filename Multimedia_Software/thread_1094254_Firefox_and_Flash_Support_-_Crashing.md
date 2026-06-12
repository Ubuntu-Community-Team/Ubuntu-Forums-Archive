---
title: "Firefox and Flash Support - Crashing"
date: 2009-03-12
forum: Multimedia Software
---

### Post by umechanism on 2009-03-12
For the past month, I have been reading, seaching threads, testing, etc...in an attempt to prevent Firefox from crashing every single time I visit YouTube or other flash sites.  I know there are some issues with libflash-nonfree versus the version from adobe.  I'm past all that now.

I just want to know which .so files I need to delete and what version of flash I should be running.  I'm using:

Firfox 3.06
Ubuntu 8.10
32 Bit OS
libflash-nonfree
Pulse Audio

Things I have tried based on information in this forum:
[LIST]
[*]Uninstalling libflash-nonfree and replacing it with Adobe's version
[*]Deleting Adobe's version and replacing it with libflash-nonfree
[*]Uninstalling Firefox, deleting the .mozilla folder, and installing everything new again.
[*]Deleting all Firfox / flash related files that end in ".so".
[*]Installing FF under Wine - still crashed.
[*]Using Opera instead of FF - more stable but still crashed.
[*]Disabling desktop effects
[*]Launching FF from the terminal using "Sudo firefox".
[/LIST]

I'm sure I've left something out but I think I've tried just about all of it to no avail.  Firefox and Opera still crash.  

I need help.  

Thanks.

---

### Post by gandaran on 2009-03-12
the flashplugin-nonfree and adode-flashplugin are exactly the same, all these packages download and install the same flash from adobe.com! it's a waste of time installing deferent packages, you always land up with the same libflashplayer.so (plugin) file installed.
I don't know whats causing your problem, maybe video drivers, memory?
flash works very well for most linux users, sorry can't help you.

---

### Post by umechanism on 2009-03-12
> **gandaran said:**
> flash works very well for most linux users, sorry can't help you.

If you Google around for "Firefox Crashes" of "Firefox Crashes on Youtube", etc...you'll find a lot of people who disagree with you.

I have an old computer as well which is running Ubuntu and has never had a crash.  My new computer crashes faster than the stock market.

Thanks for your help.

---

### Post by blastus on 2009-03-12
Flash has always been unstable on Linux. If I browse flash websites, in particular YouTube, for any length of time, Firefox will either crash, or the flash video won't render but I can hear the audio. Epiphany is even worst, even when the browser has completely crashed I can still hear flash audio and there is no way I know of to kill it. Sometimes I've even had to reboot to get ANY sound back on my system. 

Lately flash has been extremely unstable for me to the point where I almost have to re-open the browser for every single YouTube clip I watch. I'm using 64bit Intrepid primarily, but flash has been unstable on my machines for years. It didn't matter what version of Ubuntu or whether it was 32bit or 64bit, flash on Linux is just plain crap.

I don't think there is anything we can do except hope for a stable feature-complete open source flash player one day. The proprietary Adobe flash player will NEVER be stable on Linux IMO.

---

### Post by PrinceArithon on 2009-03-12
Actually Flash was much more stable in older versions of Ubuntu.  I can think back to 6.06 and 6.10.  This was back in 2006.  I remember that flash worked great for the most part.  Some people had problems if they were using 64 bit or using a certain video card.  But I remember if you were running nVidia and had 32 bit you were ok...for the most part.

Like the only problem was if you had a media player open and went to a flash video the flash wouldn't play, it would just sit there.  But as soon as you closed the media player and refreshed the page it would play fine.

But ever since 8.04 I've had serious problems with this.  It started with 8.04 where if I started by using my media player (Amarok or any other) and I wanted to go to Flash, most of the time I couldn't and it wouldn't work.  So I'd have to restart (not log out).  Then I could go to youtube and all would work.  Then if I wanted to go back to listening to my mp3's or a CD I'd have to restart again.  I tried some of the fixes but none worked.

So then in came 8.10 and it worked better.  I could now go between flash videos and my media player.  But what would happen is if I switch between the 2 either the flash videos will stop playing.  Or while they media player is playing something it would all of a sudden start sounding like I have a CD with a scratch on it and it's now skipping on the one spot over and over.  And the skipping sound won't go away until I totally reset the system...

My fix was to use Opera.  So far it has worked about 90% of the time.  So far no crashes with Opera, and about most of the time I won't get the CD skipping thing...

So in the end I know it has something to do with Flash, and possibly my audio driver...but seriously it's kinda ridiculous.  It used to work fine and now it's just a pain...

---

### Post by gandaran on 2009-03-13
> **blastus said:**
> Flash has always been unstable on Linux. If I browse flash websites, in particular YouTube, for any length of time, Firefox will either crash, or the flash video won't render but I can hear the audio. Epiphany is even worst, even when the browser has completely crashed I can still hear flash audio and there is no way I know of to kill it. Sometimes I've even had to reboot to get ANY sound back on my system. 

Lately flash has been extremely unstable for me to the point where I almost have to re-open the browser for every single YouTube clip I watch. I'm using 64bit Intrepid primarily, but flash has been unstable on my machines for years. It didn't matter what version of Ubuntu or whether it was 32bit or 64bit, flash on Linux is just plain crap.

I don't think there is anything we can do except hope for a stable feature-complete open source flash player one day. The proprietary Adobe flash player will NEVER be stable on Linux IMO.
flash maybe crap for you, I have been using ubuntu since 7.04 and adobe flash, never had any issue with flash, in fact it works just as well in linux as in windows and this is also true for most linux users, you only hear the ones that complain about adobe flash!
are you using the 32-bits flash from synaptic or have you tried the 64-bits beta adobe flash?

---

### Post by PrinceArithon on 2009-03-13
OK so I got lucky and done some searching on my problem...and I came across this link.  [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I basically followed the instructions on this thread and it worked for me....I'm very shocked by this, not to mention the sound on my system got better from this too.  So I say give it a try and see if this doesn't fix at least part of the problem...

---

### Post by umechanism on 2009-03-13
> **PrinceArithon said:**
> OK so I got lucky and done some searching on my problem...and I came across this link.  [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I basically followed the instructions on this thread and it worked for me....I'm very shocked by this, not to mention the sound on my system got better from this too.  So I say give it a try and see if this doesn't fix at least part of the problem...

So did you solve your Firefox crashing issues by following Markbuntu's post or did you just get your sound working?  I had already used his post to get my sound, via Pulse Audio, working but not video.

---

### Post by PrinceArithon on 2009-03-14
I tested the hell out of my system for the past day.  It doesn't crash as much.  It did still crash at times, but at least I can now go to a site and if it crashes I can go back and it wont crash a 2nd time...strange for sure..

---

### Post by gandaran on 2009-03-14
did any of you ever looked at this tread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by umechanism on 2009-03-23
> **gandaran said:**
> did any of you ever looked at this tread [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Great link!  This fixed my pulse audio woes right up.  Unfortunately, FF still crashes very often.

Here's an obervation - I have Ubuntu 8.10 running on my new laptop but it was installed via Wubi.  I've never had a crash on the laptop.  Flash works great!  Ubuntu on my desktop was installed the conventional way.  Is this a potential clue????  Are any of you who have crashing problems running Wubi?

---

