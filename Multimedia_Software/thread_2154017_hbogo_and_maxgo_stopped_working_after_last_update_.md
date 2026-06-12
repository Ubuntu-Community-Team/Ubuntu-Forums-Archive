---
title: "hbogo and maxgo stopped working after last update to ubuntu 12.04"
date: 2013-06-13
forum: Multimedia Software
---

### Post by solarmaze on 2013-06-13
This has happend on both of my systems.  Used to work great, now when I try to view a program, the screen just goes mostly blank, with arrows at each side as if I wanted to scroll through a program play list.  I know it has something to do with the last system update, but don't know how to fix it.  System says it is up to date. Probably something to do with flash??  I am a ubuntu / linux beginner.  Please help.... miss hbogo and maxgo.

thanks in advance

---

### Post by solarmaze on 2013-06-13
Looking further into this matter it seems that the last adobe flash update (11.2?) is what killed my video.

I cannot find an easy way (linux novice... needing foolproof step by step), to go back to the previous working version 11.1?

Help please...

---

### Post by pkinnaird on 2013-06-17
I'm also experiencing this problem as well as trouble with amazon prime instant videos.  I tried downgrading flash via synaptic and via an archive I found on the adobe site all the way to 11.2.202.275.

I'm able to login, but the player stops at 'optimizing your video quality' on hbo go. Amazon gets all the way up to buffering the video then just stops. 

In HBO Go, I opened chrome developer tools and see some elements in there about an unsupported browser version which aren't displaying in the browser. Not sure if this was there before or not, but I was definitely able to get HBO GO to work just a couple of weeks ago. Downgrading did not seem to help.

---

### Post by pkinnaird on 2013-06-17
One further note: this is definitely not a problem for all flash video. I'm able to play video on new york times and daily motion. Probably others as well though I haven't tested.  Probably something to do with the drm they're using on these sites?

---

### Post by beavansdoor on 2013-06-18
BUMP.  I've been struggling with this same problem for two days, would appreciate any solutions/workarounds anyone has discovered.

---

### Post by Giuseppe1 on 2013-06-18
I'm also having this problem and searching for a solution.

---

### Post by pkinnaird on 2013-06-19
For anyone that's still having this problem, I was able to resolve it by following the instructions here ([http://askubuntu.com/questions/145735/adobe-flash-player-not-working-with-amazon-prime?rq=1](http://askubuntu.com/questions/145735/adobe-flash-player-not-working-with-amazon-prime?rq=1)) for installing hal and removing the .adobe folder. At least it works in firefox.

I followed those instructions then tried amazon prime. It went through a new 'updating player' thing before loading video (yay!). I then tried HBO GO and that worked too. It wasn't HD, but that's probably due to the internet connection I'm on right now.

Let me know if this works for you!

---

### Post by fyremedic51 on 2013-06-21
Got rid of all adobe stuff. Downloaded Lightspark and Gnash SWF viewer. Works fine now.

---

### Post by jm011i on 2013-06-25
Hi folks,

I've tried all of these things, and still no dice: HBOGO loads up when I click a video, then black screen: nothing. All was working beautifully last week. Any other options?

---

### Post by suphawk on 2013-06-29
I have also tried all of this and more. Can no longer stream HBOGO or MAXGO on Ubuntu. I've tried in firefox and chrome, only getting a black screen when trying to start watching a show. Surely someone has a fix for this?

---

### Post by jedispork on 2013-06-30
Same problem here. I run xubuntu 12.04 as my htpc so this is quite disappointing.

---

### Post by alexpage on 2013-07-10
Same issue here, Ubuntu 12.04 with latest firefox and google-chrome-stable.  It stopped working maybe a month ago and I'm just getting around to trying to fix it.  Clearing the stuff in ~/.adobe didn't help.  With Adobe flash in Firefox I get a black screen, and with Pepper flash in Chrome it sits at "optimizing video quality".  I'm going to try Lightspark in a bit.

Edit: Seems to work with Lightspark.  CPU use is high, but it's smooth enough.

---

### Post by davisetdavis on 2013-08-02
I had this same problem with Linux Mint 13 and 15. What worked for me was to re-install Mint 13 and during the 500+ package initial update, I disabled all gstream updates. HBOGo and MAXGo etc.,are all working fine with Chromium and FireFox, not Google Chrome however.
I hope this helps.

---

### Post by jedispork on 2013-08-02
So does the email they posted over here mean that is not supported anymore? 

[http://forums.linuxmint.com/viewtopic.php?f=48&t=138868#p746769](http://forums.linuxmint.com/viewtopic.php?f=48&t=138868#p746769)

I ended up buying a appletv since directv finally enabled hbo go on it. Still doesn't make sense why they won't allow roku users.

---

### Post by uptown1772 on 2014-06-16
Tried some of the suggested solutions and it was not successful for both FF and Chrome. FYI I don't know if anyone else has noticed that when you check the properties of the screen it changes from v11 to v14?

---

