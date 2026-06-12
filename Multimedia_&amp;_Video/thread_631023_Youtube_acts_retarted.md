---
title: "Youtube acts retarted"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by bokorpop on 2007-12-04
My youtube is playing all choppy, with poor resolution and  I cannot adjust the volume. Look at my screenshot and see how the volume control looks all messed up. This happens for both firefox and epiphany. Also, I can't maximize the video window. Any suggestions?
[IMG]http://i152.photobucket.com/albums/s198/bokorpop/Screenshot1.png[/IMG]

---

### Post by vlasvlasvlas on 2007-12-22
HELLO!!!!!! i have the same problem in ubunutuuuuuuu!!!

doyou know whats the deal? resolve it already?

i didnt.......


anyone know why this may happen?

youtube WONT maximize window
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by OmarJ on 2008-01-05
Couple of possible problems here:

1. You have gnash installed as your firefox flash plugin. While it looks like it might be a good future bet, at the moment its quite buggy, and you should probably stick with the official Adobe plug-in, which can be found on the firefox plugin website.

Here's the link: [https://addons.mozilla.org/en-US/firefox/browse/type:7]("https://addons.mozilla.org/en-US/firefox/browse/type:7")

2. You may have to change some some congifurations on compiz, if you have that installed. Go to *System -> Preferences -> Advanced Desktop Effects Settings*  and uncheck 'Unredirect Fullscreen Windows' under *General* and also uncheck "Legacy fullscreen Support" under *Workspaces*.

Hope these work out for you. I do hear that a lot of people still get choppiness in their streamed videos even after they'v e done this, so maybe you should try disabling compiz altogether and see if that helps.

Anyway, best of luck, tell me how it goes.

---

### Post by jslmg on 2008-01-10
> **OmarJ said:**
> :
Go to *System -> Preferences -> Advanced Desktop Effects Settings*  and uncheck 'Unredirect Fullscreen Windows' under *General* and also uncheck "Legacy fullscreen Support" under *Workspaces*.


I'm not finding Legacy fullscreen support in ADS. No workspaces section that I can locate. Can you direct us a bit more?

---

### Post by jslmg on 2008-01-10
I'm not sure what helped, whether it was the Flash plugin installation or the unchecking of "Unredirect Fullscreen Windows," or both. But it has made a difference, correcting some of those interface issues shown in bokorpop's screenshot.

But it's not 100% yet:

 In Youtube videos, there's a big "0" that keeps flashing across the image, and several features are disabled, like expand-view mode, and the "Play Again" link. 

The buttons are still partially obscured, but not as messy as before.

Actually, the buttons at bottom don't respond at all, though there is a right-click menu that gives options such as pausing the video and such. I notice, though, that when I select "pause video" from that menu, the video stops playing, but the sound continues, and the video does not pick up where it paused when I press play. Seems like the browser continues receiving data even in pause. I'm pausing the player, but not the data.

I've attached a screenshot of a Youtube video after it's finished, in Epiphany. Notice the big "0" and the buttons cut off at the bottom.

---

### Post by thebusdriver360 on 2008-01-10
Hi, I think I have the same issue and I believe it is caused by gnash, how do I remove gnash?

---

### Post by thebusdriver360 on 2008-01-10
nevermind, i found it and fixed it

---

### Post by jslmg on 2008-01-10
> **thebusdriver360 said:**
> nevermind, i found it and fixed it

did you fix the video problems shown in my screenshot, or the earlier one? How does your Youtube look now?

---

### Post by Tech_Power888 on 2008-01-10
Hello there,

I had the same problem recently in Ubuntu 7.10. It was bugging me to the extent that I sat down and took a long hard look at the problem for some time. I can tell you pretty much exactly what is wrong. What Omar said is correct; Gnash is quite buggy. You will need to go into Synaptic and uninstall it. Also, while you are in Synaptic, make sure you uninstall adobe flash player as well (i think what you are looking for is "flashnonfree" or something similar). 

Once you have both of these uninstalled, do a full restart of your computer. Now go onto firefox, and head to the adobe.com website. You need to locate the absolute LATEST version of flash player (I think it's 9) and download the linux version. Install this on your machine, and do another restart. You should now be good to go. 

I had a play around with all sorts of stuff, before trying the most obvious thing, that was right under my nose all along. My youtube now runs perfectly. I was having exactly the same problems as you originally. The big white "0" and choppy video etc. My problem was completely resolved by following those simple steps.

Good Luck.

Ryan.

---

### Post by Casual Fan on 2008-01-10
Did you intend to type "retarted" (sic) in your title and post a screenshot of an Aspberger's syndrome video?

:confused: That's just plain wrong.

---

### Post by wolfen69 on 2008-01-10
this [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb) 
deb file is all you need to install flash in gutsy.

---

### Post by jslmg on 2008-01-11
> **wolfen69 said:**
> this [http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb) 
deb file is all you need to install flash in gutsy.

There seems to be some disagreement on, or different experiences with, how to best install a fully functioning flash for web-based video. See this thread:

[http://ubuntuforums.org/showthread.php?p=4108179#post4108179](http://ubuntuforums.org/showthread.php?p=4108179#post4108179)

As well as post #9 in this thread.

---

### Post by Tech_Power888 on 2008-01-11
Yeah, I just thought I'd post my recent experiences with this issue. I virtually tore my hear out trying to get this problem fixed, I went to every ubuntu help page etc, and simply could not work it out. So I did the first thing that I knew would be a step in the right direction; Stop, back up for a minute, remove everything and start from scratch. When I had done that, and I was about to try reinstalling the flash plugin automatically, it clicked that I would be better off going to the adobe website directly..If their version didn't work, then I knew I could start asking questions about why it wasn't. 

This move proved to be the right one though, and I had every video streaming website up and running in a matter of minutes.

---

### Post by d_fiant_1 on 2008-01-14
Had the same trouble, Installed firefox 3.0B2 and problem solved....unfortunately can't use sun java with it yet

---

