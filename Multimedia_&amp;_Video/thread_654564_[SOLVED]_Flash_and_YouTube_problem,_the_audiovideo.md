---
title: "[SOLVED] Flash and YouTube problem, the audio/video trainwreck."
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by Taum on 2007-12-31
This is my third day of searching these forums for an answer and without finding people who have experienced the same problem as me, I've decided to start this thread.  Hopefully someone will recognize these symptoms and direct me to a thread that solves the problem or, better yet, have someone who knows Ubuntu well enough to find a new way to fix this issue.  In any case, I hope this isn't some repeated post.

**The Symptoms:**  When playing a video on YouTube or other Flash based videos, everything progresses as normal, but eventually there will come a pause in video and audio, then the video starts again some seconds from where the pause started, but the audio jumbles forward to catch up to the video, as if it was falling down the stairs.  I can go back to the offending spot and replay it later without issue.

**The Fixes:**  I've already tried a few of the remedies that I've found on here for various, more cryptic problems, but nothing has worked as of yet.  I've uninstalled and reinstalled the non-free flash.  I've upgraded the core of Firefox to the Hardy Heron level.  I've even tried jumping up and down and yelling at my computer.  Nothing has changed.

So, I don't know if it's Flash or my Audio drivers or the Video Card, but something is not right with my Ubuntu and I would appreciate any help I can get on this.  Thank you!

---

### Post by foolsh on 2007-12-31
did you try installing the linux version of flash from the adobe site?

---

### Post by Taum on 2007-12-31
Not recently, but I did try a few weeks ago.

---

### Post by Taum on 2008-01-01
Ok, I just tried that again and that didn't fix my issue.

Any other ideas?

---

### Post by markyb86 on 2008-01-01
same deal here ive tried all the browsers and i just cant get satisfied :-(

and yes i have compiz enabled. dont ask, not the cause of the problem

---

### Post by Taum on 2008-01-01
I am not using Compiz.

---

### Post by markyb86 on 2008-01-01
im just saying everyone always asks that first, and its not the cause of the problem in any way

"tomboy notes keeps freezing" 
"oh you you have compiz installed?"

-or- 

"grub wont find my partition"
"oh did you install compiz?"

---

### Post by Taum on 2008-01-02
Well, at least I'm not the only one with this problem.  I'm going to consult other sources and if I find a solution there, I'll post it here, but I would still love for the wonderful folks here to help out with this problem.

---

### Post by wolfen69 on 2008-01-02
you could give linux mint a try. (based on gutsy) flash and all codecs work out of the box.

sorry i couldnt be of more help.

---

### Post by markyb86 on 2008-01-03
'linux mint' will it crash all of the browsers constantly? because ubuntu's flash works just crashes

---

### Post by Taum on 2008-01-03
I'd like to think that the other people that use Ubuntu are able to watch browser based videos, so it's not like it's an ***Ubuntu*** problem but more of a specific issue that I have to deal with.

---

### Post by wolfen69 on 2008-01-03
> **markyb86 said:**
> 'linux mint' will it crash all of the browsers constantly? because ubuntu's flash works just crashes

i havnt had ***any*** problems with firefox or opera.

---

### Post by wolfen69 on 2008-01-03
btw, here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then click and install.

---

### Post by Taum on 2008-01-03
I know this will sound silly, but how does one go about removing the flash plug-in?

---

### Post by markyb86 on 2008-01-03
> **wolfen69 said:**
> btw, here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then click and install.

is there a workaround if my flash plugin is part of ubuntu-restricted-extras  ??

---

### Post by Taum on 2008-01-04
I just tried [this fix that I found]("http://sendderek.wordpress.com/2007/10/20/how-to-fix-the-no-sound-issue-in-firefox-flash/") and now there's no bunching up that I can detect, but now the audio is trailing the video, meaning that it doesn't sync up.  The audio's about a second behind the video.  Not what I call a fix, but it's an elimination process, yes?

---

### Post by UbunNooB on 2008-01-04
I just stumbled across this post and decided to chime in...I too am having an issue with viewing videos on youtube. The sound streams but the video shows only a few frames (if that) then my browser turns gray and I can't close out the window and need to exit out of Ubuntu and log back on.  

I am wondering if it's something with the plugins because I had to reinstall Gusty and my previous install worked fine but I just got the chance to download the drivers tonight and all hell has broken loose on the browser.

I do not know how to uninstall the plugins but I have posted that question in another post.

---

### Post by Taum on 2008-01-06
So, I've uninstalled that fix, but I'm left with the same problem.

Any ideas?

---

### Post by skorstensbloss on 2008-01-08
I have the exact same problem :(
Where the audio and video stops and resumes, creating weird noises in the process.
It gets really nasty if I have several Youtube video tabs open(only one playing),  the skips get really frequent and firefox freezes up in short intervalls
I cant find a fix either.

---

### Post by eye208 on 2008-01-08
> **Taum said:**
> but eventually there will come a pause in video and audio, then the video starts again some seconds from where the pause started, but the audio jumbles forward to catch up to the video, as if it was falling down the stairs.  I can go back to the offending spot and replay it later without issue.
These are symptoms of network congestion. I doubt you'll be able to fix the problem through software.

---

### Post by skorstensbloss on 2008-01-08
Finally! I found a fix in a thread, while searching for network congestion hahaha 
Its not perfect though, the problem still persists but its not as bad and it made video quality on youtube better for some reason.
heres the link:
[http://ubuntuforums.org/showthread.php?t=648356](http://ubuntuforums.org/showthread.php?t=648356)

---

### Post by skorstensbloss on 2008-01-08
No I take that back. Its still the same, the symptoms I have tend to build up with time so I got a bit over-excited in the beginning.

---

### Post by Taum on 2008-01-08
> **eye208 said:**
> These are symptoms of network congestion. I doubt you'll be able to fix the problem through software.

It's got nothing to do with the network, this is pre-cached info, it's not like the play tab is getting to the end of the cached video and hanging up.  I can pause the video, let it load completely, and it'll still give me issues.

I didn't have this issue with Edgy or Feisty, so I think it's a Gutsy problem, not a network problem.

---

### Post by trevoore on 2008-01-10
Mh, I've got the same problem.

Also the longer you view the video the more frames are jumped and the oftener the video stops.
Actually it seems like the whole computer stalls not just the video.

Anybody else with suggestions?
t

---

### Post by trevoore on 2008-01-11
bounce.

---

### Post by jslmg on 2008-01-17
> **markyb86 said:**
> im just saying everyone always asks that first, and its not the cause of the problem in any way

"tomboy notes keeps freezing" 
"oh you you have compiz installed?"

-or- 

"grub wont find my partition"
"oh did you install compiz?"

LOL... 

Yeah, first response to anything around here seems to be, "Is compiz running?"

But seriously, I have no audio at all in web-based Flash. Perfect video, but no audio. Others here have various problems--some get audio, but no video; some have slow, jumping video, but fine audio; still some get partial audio, but video's OK. I'd leap for joy if I could even get partial audio! I'd go get myself another beer in celebration! But, no audio here.

Perfect video, no audio in web-based flash. Great audio in all other respects on my system.

Any ideas?

---

### Post by markyb86 on 2008-01-17
my sons computer even got to the point of playing just fine and then the audio dies after 30 or so seconds and the video keeps going ....

His computer is a 1.6ghz Pentium 4 256mb ram 32mb Nvidia Geforce 2 running gutsy...
And no compiz is NOT enabled

---

### Post by jslmg on 2008-01-17
OK, my particular issue--a very common one, it seems--has been solved.

If you have good video in Flash, but no audio, download the plugin here:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bug site.

---

### Post by niceguy123 on 2008-01-18
> **jslmg said:**
> OK, my particular issue--a very common one, it seems--has been solved.

If you have good video in Flash, but no audio, download the plugin here:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bug site.

Thanks,

I think that it worked. After I installed the plug in I read on the video I was trying to watch that the guy who made it wrote that he needs a new mic.

---

### Post by markyb86 on 2008-01-18
> **niceguy123 said:**
> Thanks,

I think that it worked. After I installed the plug in I read on the video I was trying to watch that the guy who made it wrote that he needs a new mic.
I hate when that happens! "I cant hear anything" and there wasnt anything to hear?

almost as bad as "I havent recieved my paycheck yet" you dont have a paycheck...

---

### Post by twig43 on 2008-01-25
ok this is my first post being a member of this fo and I found that if you use google video to search for your youtube videos the videos don't skip or pause and get all jumbly, I think it has something to do with the frame

---

### Post by eye208 on 2008-01-25
> **Taum said:**
> It's got nothing to do with the network, this is pre-cached info, it's not like the play tab is getting to the end of the cached video and hanging up.  I can pause the video, let it load completely, and it'll still give me issues.

I didn't have this issue with Edgy or Feisty, so I think it's a Gutsy problem, not a network problem.
I think it's a Flash plugin problem. What version are you using? (Enter "about:plugins" in the URL bar to find out.)

I'm running Flash 9.0 r115, the latest. Video playback is flawless here. Yes, I'm running Gutsy too.

---

### Post by Taum on 2008-02-06
> **eye208 said:**
> I think it's a Flash plugin problem. What version are you using? (Enter "about:plugins" in the URL bar to find out.)

I'm running Flash 9.0 r115, the latest. Video playback is flawless here. Yes, I'm running Gutsy too.

I'm using: Shockwave Flash 9.0 r115.  I've resolved that it's probably the crap onboard video card I'm using.  I"m not sure about that, but I'm not getting results elsewhere, so I'm just going to assume it's hardware, which I have not the money to fix at this time.

---

### Post by gandaran on 2008-02-07
> **Taum said:**
> This is my third day of searching these forums for an answer and without finding people who have experienced the same problem as me, I've decided to start this thread.  Hopefully someone will recognize these symptoms and direct me to a thread that solves the problem or, better yet, have someone who knows Ubuntu well enough to find a new way to fix this issue.  In any case, I hope this isn't some repeated post.

**The Symptoms:**  When playing a video on YouTube or other Flash based videos, everything progresses as normal, but eventually there will come a pause in video and audio, then the video starts again some seconds from where the pause started, but the audio jumbles forward to catch up to the video, as if it was falling down the stairs.  I can go back to the offending spot and replay it later without issue.

**The Fixes:**  I've already tried a few of the remedies that I've found on here for various, more cryptic problems, but nothing has worked as of yet.  I've uninstalled and reinstalled the non-free flash.  I've upgraded the core of Firefox to the Hardy Heron level.  I've even tried jumping up and down and yelling at my computer.  Nothing has changed.

So, I don't know if it's Flash or my Audio drivers or the Video Card, but something is not right with my Ubuntu and I would appreciate any help I can get on this.  Thank you!

this looks like a slow internet connection!

anyway here's a easy way to install flash 

the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

---

### Post by sajochin on 2008-02-07
> **Taum said:**
> **The Symptoms:**  When playing a video on YouTube or other Flash based videos, everything progresses as normal, but eventually there will come a pause in video and audio, then the video starts again some seconds from where the pause started, but the audio jumbles forward to catch up to the video, as if it was falling down the stairs.  I can go back to the offending spot and replay it later without issue.

The problem probably is your system load. You could use "top" in a terminal to check your cpu load. The cause for high cpu load might be youtube videos in other tabs. They cause quite some load, even if the videos are paused or have finished playing).

---

### Post by Taum on 2008-02-07
> **gandaran said:**
> this looks like a slow internet connection!

anyway here's a easy way to install flash 

the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

Well, I've turned off the ubufox and disabled the non-free Flash from the Synaptic Package Manager, restarted the computer, but Flash is still installed.  How do I go about uninstalling it?  I looked around on these forums, but I didn't see anything definite.

Oh, and it's not a slow internet connection.  I know this because the same problems aren't being repeated with the other computers on the router (Mac and Win).  The bandwidth is 15Mb, so it's not dial-up or anything.

---

### Post by Taum on 2008-02-07
> **sajochin said:**
> The problem probably is your system load. You could use "top" in a terminal to check your cpu load. The cause for high cpu load might be youtube videos in other tabs. They cause quite some load, even if the videos are paused or have finished playing).

Using "top", I DO see a spike in CPU usage when these problems occur, usually going from 50%-70% CPU usage to 99%.  When flash is not playing, my CPU usage is about 5%-10%, so it may be possible that I need a video card with more onboard RAM in order to use less from the CPU.

---

### Post by gandaran on 2008-02-07
> **Taum said:**
> Using "top", I DO see a spike in CPU usage when these problems occur, usually going from 50%-70% CPU usage to 99%.  When flash is not playing, my CPU usage is about 5%-10%, so it may be possible that I need a video card with more onboard RAM in order to use less from the CPU.

how about your media player (totem, vlc or mplayer ) if it's a problem with your video card then you  must have some problem here too, check cpu usage.

look I really recommend installing flash my way, it will be installed right to the mozilla folder, try it 

to unistall other flash plugins, go to synaptic, look for flashplugin-nonfree and gnash, if the little box is green choose complete removal then click on the apply button.

---

### Post by Taum on 2008-02-07
> **gandaran said:**
> how about your media player (totem, vlc or mplayer ) if it's a problem with your video card then you  must have some problem here too, check cpu usage.

look I really recommend installing flash my way, it will be installed right to the mozilla folder, try it 

to unistall other flash plugins, go to synaptic, look for flashplugin-nonfree and gnash, if the little box is green choose complete removal then click on the apply button.

Neither flashplugin-nonfree nor gnash have green boxes next to them.  I'm still at a loss for how to uninstall flash.

The standalone movie player does not seem to be an issue, though.  It probably isn't the video card then...

---

### Post by gandaran on 2008-02-08
> **Taum said:**
> Neither flashplugin-nonfree nor gnash have green boxes next to them.  I'm still at a loss for how to uninstall flash.

The standalone movie player does not seem to be an issue, though.  It probably isn't the video card then...

what, how, where, did you install flash then? was it a .deb package or a tarball? did you install to /usr/lib/mozilla or home .mozilla folder?
try locate a flashplayer.xpt and libflashplayer.so file


the flashplugin-nonfree is back, the package is repaired now, but to install you must get rid of that flash you got!

---

### Post by Taum on 2008-02-08
> **gandaran said:**
> what, how, where, did you install flash then? was it a .deb package or a tarball? did you install to /usr/lib/mozilla or home .mozilla folder?
try locate a flashplayer.xpt and libflashplayer.so file


the flashplugin-nonfree is back, the package is repaired now, but to install you must get rid of that flash you got!

I got it from the Adobe site.

---

### Post by Taum on 2008-02-08
Oh, and I'm still having the same problem after this newest release of Firefox...

---

### Post by Taum on 2008-02-08
After [installing Seamonkey]("http://ubuntuforums.org/showthread.php?t=186011") I've yet to have any glitches in video.  Perhaps I should uninstall Firefox and reinstall it...

---

### Post by gandaran on 2008-02-08
why not try the opera browser too? , download the opera 2.50b ubuntu .deb package from opera website (be-careful download the 2.50b version as the 2.25 won't work with the newer flash).
it's my favourite browser!

---

### Post by Taum on 2008-02-08
So, I uninstalled all of the Firefox components, re-installed *just* Firefox, and lo and behold, Flash was waiting there for me.  It's still messed up, this time a little worse in that the glitches happen more frequently.

I'll try the Opera, too.

---

### Post by gandaran on 2008-02-08
you can also reinstall ubuntu, could solve your problems!

---

### Post by kelvin spratt on 2008-02-08
Flash is not a problem on Gutsy there was a problem but its resolved now the problem was no flash being installed due to a mdsum error and was resolved by Completely removing flash and downloading from Adobe the simple instructions are under the download. But first you need to rid the system of the old install and gnash as that gives the symptoms you are getting, Read up how to purge your system, And any so called fixes then re install flash if your system and video card is OK you will have no problems.
It also can be you network giving problems but sounds more like gnash corruption than anything else to me.hope this is helpful.

---

### Post by Taum on 2008-02-08
Opera is not to my liking.

I've uninstalled Firefox and reinstalled it.  Now I've done this:

```
cd ~/.mozilla/plugins
ls -al
rm *flash*
```

Then after installing the Flash 9 from Adobe, I went: 

```
cd usr/lib/firefox/components
sudo rm xpti.dat
```

Per the Adobe instructions.  So, I completely removed the Flash and reinstalled the new stuff and I STILL have the same problems.  *sigh*

---

### Post by Taum on 2008-02-22
Well, I tried a live disc of Gentoo, but I couldn't figure out how to turn on the networking for it, so I gave up.  Still scratchin' my head.

---

### Post by Taum on 2008-02-25
Ok, so I've formatted my hard drive, reinstalled Ubuntu from a fresh 7.10 cd, turned off Ubufox, installed Flash 9.0 from Adobe, made sure there there was no xpti.dat like Adobe asks, and I *still* have trouble playing flash videos in Firefox.  And, it's just Firefox, no other browser has this issue.  I love my Firefox, but it's really frustrating me at this point.

Anyone have any clues?

---

### Post by jkj5000 on 2008-02-25
Okay, I've done everything in my power to get flash working properly.  I'm beginning to think the problem is with my hardware.  I'm running ubuntu 7.10 on an older Pentium 3 machine with 400 something MB of ram.  Audio plays fine, but the images are always choppy, like I'm watching a webcam movie.  Am I missing something or do you guys think the problem is my older hardware?

Thanks :D

---

### Post by brivy on 2008-02-25
I don't know if this will at all be helpful but I'm "hearing" the increasing frustration in your posts and believe me when I tell you I've been there.  I had to quit Ubuntu because it wouldn't play anything off the web.  I switched to Fedora 8 and eventually to SuSE 10.3.  In both of those distributions everything played correctly, just like it is supposed to.  Several weeks ago I somehow roached my Windows partition and didn't have my copy of SuSE to fix it.  I found a copy of Xubuntu 7.10, fixed the partition and then let it install over SuSE.  When I opened Firefox and went to You Tube to see if something had possibly changed.  On the website it asked if I wanted to install the plugin, I clicked yes. It then offered me the choice of Flash or Gnash.  I chose Flash, it installed and lo and behold the video played without a problem.  The only thing I did differently was install it from the You Tube website instead of going through Synaptic.

The only thing I can think of is that Adobe has changed its Flash plugin so that it now works with Ubuntu/Xubuntu and with Synaptic there is an older plugin in the repositories. Good luck and hang in there. 

Of course, there is another question as to why Flash works so well with other distributions and not with Ubuntu, but of course that is something than Canonical needs to figure out.

---

### Post by Taum on 2008-02-25
> **brivy said:**
> I don't know if this will at all be helpful but I'm "hearing" the increasing frustration in your posts and believe me when I tell you I've been there.  I had to quit Ubuntu because it wouldn't play anything off the web.  I switched to Fedora 8 and eventually to SuSE 10.3.  In both of those distributions everything played correctly, just like it is supposed to.  Several weeks ago I somehow roached my Windows partition and didn't have my copy of SuSE to fix it.  I found a copy of Xubuntu 7.10, fixed the partition and then let it install over SuSE.  When I opened Firefox and went to You Tube to see if something had possibly changed.  On the website it asked if I wanted to install the plugin, I clicked yes. It then offered me the choice of Flash or Gnash.  I chose Flash, it installed and lo and behold the video played without a problem.  The only thing I did differently was install it from the You Tube website instead of going through Synaptic.

The only thing I can think of is that Adobe has changed its Flash plugin so that it now works with Ubuntu/Xubuntu and with Synaptic there is an older plugin in the repositories. Good luck and hang in there. 

Of course, there is another question as to why Flash works so well with other distributions and not with Ubuntu, but of course that is something than Canonical needs to figure out.

Well, it seems to be a Ubuntu + Firefox issue, the video plays well in other browsers, like Opera and SeaMonkey.  Too bad they're not as cool as Firefox otherwise.

---

### Post by Taum on 2008-02-25
I've found the answer!

It's a little thing called [Firefox 3.0]("http://en.wikipedia.org/wiki/Mozilla_Firefox#Version_3.0")!  It's completely solved my problems!

Now to see what breaks on this alpha version...

---

