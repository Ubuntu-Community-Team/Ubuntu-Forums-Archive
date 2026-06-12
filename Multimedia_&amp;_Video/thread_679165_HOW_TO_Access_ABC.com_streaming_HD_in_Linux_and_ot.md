---
title: "HOW TO: Access ABC.com streaming HD in Linux and other content for Window or Mac"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by rosegarden78 on 2008-01-26
In one sentence: download Firefox for Windows and install it with WINE from the repositories.  Then follow the instructions at ABC.  I'm posting this simple how-to so I can link it to other threads.  Using a terminal type this command:

1) sudo apt-get install wine
---this installs _WINE_
---also installs the dependencies
2) download _Firefox 2.0 for Windows_
---use the mozilla website
---save it to your desktop
3) Click to Install Firefox.
4) Navigate to _/home/user/.wine_ to launch Firefox.  
5) Go to _ABC website_ and click movie.
6) Install _Flash plugin_ when asked.  
7) Install _ABC plugin_ when prompted.

Cheerio! :KS

P.S.  If you want to know why this happens: Because they sniff for the user's operating system and browser.  Using WINE with Firefox provides the site with all the identification it requires.  And since it's a Windows program it knows how to interface with their new HD plugin and vice versa.

Edit: Feb 20th 2008
I think abc.com servers are based in Los Angeles. Visit [www.speedtest.net](www.speedtest.net) to check connection speed. Then check System Monitor to see if you have network activity. You cannot multi-task or ever move the Wacom tablet without draining CPU. My CeleronM 1.4 can only play Lost in Normal screen size which is fine for me. Big and full screen cannot be handled by the Inspiron 1200 with 1280 MB of memory. Just sit back and watch and don't fiddle with the mouse cursor or use anything else that drains the CPU even try disabling the swap file using sudo swapoff /dev/sda5 at th terminal. Anything you can do to ease the load will help. Only disable swap file if you have more than 1 GB of memory.

---

### Post by rosegarden78 on 2008-01-27
I should mention _VirtualBox_ download you can run XP with network and sound on virtual PC, open source unlike VMware, very easy instructions even I could do it!

---

### Post by pulpinator on 2008-02-01
Success! Thank you very much. There's still some minor issues, like the Move Media Player not resizing correctly, but it's good enough for now.

---

### Post by LanceM on 2008-02-01
That does work for me as well but the video is a bit choppy. Any idea how to fix that?

---

### Post by HeinekenPissr on 2008-02-03
Lets try and move past these bulky, flawed workarounds.

Go to the following website to sign the petition asking ABC to support a plugin for Linux users

[http://www.ipetitions.com/petition/LinuxABC/](http://www.ipetitions.com/petition/LinuxABC/)

---

### Post by LanceM on 2008-02-04
> **HeinekenPissr said:**
> Lets try and move past these bulky, flawed workarounds.

Go to the following website to sign the petition asking ABC to support a plugin for Linux users

[http://www.ipetitions.com/petition/LinuxABC/](http://www.ipetitions.com/petition/LinuxABC/)

Didn't even know that was an option. Thanks :)

---

### Post by rosegarden78 on 2008-02-16
Thanks guys I'll look into signing the petition.  Choppy video?  Me too.  But I have on-board Intel 915GM graphics and SBC DSL so we upgraded to Pro speed for $5 more.  We're not sure we notice bandwidth any higher than the 168 kb/s with normal price.

ABC says you need 768 kb/s bandwidth to experience true HD but you need a screen resolution like 1440x880.  It might be a limitation of the service provider, your front side bus speed, graphics card, processor speed.  I'm not convinced purchasing a new laptop is worth it.  

My Inspiron 1200 with 512 MB and 1.4 CeleronM has just enough computing power to run Virtual XP and perform simple graphics and video compositing.  I think I'll wait another year before I consider upgrading.  The Dell 1420 looks promising we'll wait and see.

I'm not sure why the new ABC player doesn't have a Linux port.  Maybe it's brand new and they need more manpower.  In today's economy they might not have the budget.  I'm very glad I can still use it with Windows emulation and Firefox let's hope that doesn't change.



!! TIPS AND TRICKS - HOW TO SPEED UP CHOPPY VIDEO !!
EDIT: Feb 20, 2008 - I maxed my RAM out for $100 for 1Gb with 256 MB on-board for a total of 128O Gb. Then I disabled the swap file - sudo swapoff /dev/sda5. This seemed to ease the load on the CPU. This should reduce choppy video (max RAM) but you can't multi-task. The Move media player likes to use 1OO% system resources. Just sit back and enjoy the show.

---

### Post by Blessed_Coffee on 2008-02-22
Ya, I got this working too.

I wanted to watch the first three seasons of Lost a while back, but I couldn't find any... :-#
lol XD

---

### Post by AusIV4 on 2008-02-27
I tried this a few months back and the video was unwatchable. I tried it again today and it works great. I assume this can be chalked up to improvements in Wine.

---

### Post by satn3ver on 2008-03-22
I just tried this work around for SD viewing and its no dice. It loads the viewer and the episode but it is choppy and often freezes. I dunno if its my connection or something with WINE.

BTW, when i go to abc.go.com i get a script failure that i have to stop several times before the page loads.

---

### Post by sammydee on 2008-03-23
How about the user agent switcher for firefox in linux, will that solve the problem?

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

It can be used to spoof the operating system/browser version to anal websites that check for specific combos. Might help avoid having to use wine?

Sam

---

### Post by ionFreeman on 2008-03-24
Hey, thanks. I now get a pixelated, choppy version of Canterbury's Law. I want to see Karyn Plonsky's debut tomorrow, but I guess I already know what she looks like ;)

---

### Post by bcardarella on 2008-03-27
If you install the Firefox Agent Switcher Plugin:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

You won't get the "You must have Windows/Mac" screen. It seems that they're simply checking the UserAgent string. I chose IE/Vista

The new problem is that the video still doesn't load. It comes to a screen that says Flash8 is required to play the full-length episode. I have the latest Adobe Flash plugin... which I believe is Flash9. So there must be a failsafe in their flash file checking to see what platform the plugin is running on and fail if it isn't Windows/Mac.

It would be good to see if there is a way to spoof this. All we need to do is trick the Flash player into sending out the proper version/platform information.

---

### Post by ArtInvent on 2008-04-05
I tried this also a couple weeks ago and couldn't get ABC to play at all really. Yesterday I compiled the just released wine 0.9.59 and tried again. The ABC player in Firefox still has some weird behavior but I was actually able to watch some episodes in "large" screen size fairly well. With AT&T DSL in the LA area I'm also watching Hulu.com which is supposed to be in HD. I haven't really gotten HD to play in any case with smooth frame rates. It's like maybe 15 fps in full screen HD with either of these services.

I can also run XP in Virtualbox so I've tried watching these services that way as well. I would say this is worse as both audio and video tend to be choppy, can't really stand it. This is true for me even just playing local audio files in W Media Player. I watch the System Monitor window and VB maxes out the CPU quite often just playing audio. I have a pretty recent dual core with 2GB and 1GB assigned to XP so this doesn't seem right.

At least in Wine-Firefox the audio is fine. I generally prefer running things in Wine if possible rather than VB because it's faster and cleaner and completely bypasses Windows.

Of course, it does seem fairly trivial to play media in Flash on Firefox on Linux native, so I can't really understand why any of these services find it so hard to supply a Linux port.

---

### Post by puifais on 2008-05-04
Works great.  Thanks!

---

### Post by TracyO on 2008-05-09
I completed the instructions in the initial post of this thread, using WINE and Firefox for Windows.  I made it to the player and then discovered my sound wasn't working.  Any suggestions?  The ABC troubleshooting was so helpful in saying if you're speakers are turned up and it's still not working, fill out a feedback form.

Yes, my speakers are up.  I've got a new Inspiron 1525, and I was just listening to a radio show on here, so it's not a speaker problem.  When it gets onto the ABC shows website, it will often say that Mozilla has performed an illegal operation and should be restarted.  The only thing I can think of is that something went wrong in the spoofing with Flash or the ABC plug-in.

Thanks!

---

### Post by TracyO on 2008-05-10
I tried starting Firefox in Safe Mode, and it works now.  Happy day.

---

### Post by V0X on 2008-05-18
I'm having a bit of a weird problem. I can open the ABC full episode player without a problem, the commercials play fine, but after the commercials I get the ABC dialogue that says "Episodes are unavailable at this time. Please try again later." I did that, and it still didn't work. Then I tried it in a VM and on another computer and it worked flawlessly. Any ideas?

---

### Post by blazercist on 2008-05-19
mine works upto the poitn where it says loading... and then nothing.... i see the commercials just fine then it goes the the episode and stops at the loading screen.... sucks.

---

### Post by Crash87ss on 2008-06-04
Thanks! works great up to when the show starts playing, then my screen goes into lsd mode (lots of pretty, but not very useful colors). I've been working on getting video driver working properly, so I'm guessing that is my issue. But, has anyone else had this issue?

---

### Post by yankes1903 on 2008-06-05
I followed the instructions in the first post and everything installed fine. i got through the commercial, "click here to continue" then the video starts, the sound plays, then the colors of my screen invert and everything is black and neon pink and green and yellow.
help!
I have an inspiron 1420,resolution is 1440x900, 60 Hz refresh, Intel Graphics Media Accelerator X3100
(sadly this is further than I got trying to watch lost on vista with IE 7!!!)

---

### Post by jsestri2 on 2008-06-06
I am also seeing the same issue as the previous two posters. I saw the issue with both the open source and proprietary ATI drivers for my A215-S4807 Toshiba Satellite laptop. Could this be a new change to the wine package? I have not been able to find any other mention of this bug and you two are fairly recent posts...

EDIT: I created a bug for this on launchpad: [https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/237818")

---

### Post by yankes1903 on 2008-06-06
I'm pretty sure it's something with the Move Player abc.com uses because other networks work fine for me, except I just tested fox.com and the same thing happened and they also use the same Move Player.

---

### Post by jsestri2 on 2008-06-09
Since this is in the archive area it is probably not the proper place to discuss the issue -- I created a new thread in the support forums:

[http://ubuntuforums.org/showthread.php?t=823728](http://ubuntuforums.org/showthread.php?t=823728)

---

