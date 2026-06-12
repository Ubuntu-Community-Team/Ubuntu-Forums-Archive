---
title: "cbs innertube site not working..how..HELP"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by firstc624 on 2007-01-13
OK how do i get mplayer to work correctly w/ firefox?  I am trying to watch tv online thru cbs website.  I have downloaded mplayer and installed the firefox extension media player connectivity, but i keep getting the error that the application doesn't understand it something like 

here is what it does when i try to play it thru mplayer gui "Couldn't resolve name ngfor AF_INET6:ad.doubleclick.net

That comes up every single time.

Please help me out i can't get it to play right.  It also doesnt give me the icon on the screen when it should be playing.  

PLEASE HELP

THANKS](*,)

---

### Post by firstc624 on 2007-01-14
bump

---

### Post by yigal.weinstein on 2007-01-20
I have no idea how to use the realplayer plugin of mplayer with Innertube nor how to use it with Firefox.  However if your goal is to watch Innertube a temporary solution is found in the Fedora forums, [http://forums.fedoraforum.org/showthread.php?p=700613#post700613]("http://forums.fedoraforum.org/showthread.php?p=700613#post700613").

The problem is for some bizzare reason Innertube doesn't work with Firefox but only with Mozilla-browser (```
$mozilla&
``` in terminal).
Here are detailed instructions for watching Innertube on Ubuntu:

1. Install the latest realplayer plugin:
i. Go to their website, [http://www.real.com/linux?pcode=rn&am]("http://www.real.com/linux?pcode=rn&am").
ii. Download Mozilla-compatible plug-in the middle download on the right-hand side of the website: RealPlayer10GOLD.bin.
iii. ```
$chmod 755 RealPlayer10GOLD.bin
$sh RealPlayer10GOLD.bin
``` 
install Realplayer wherever you want it - I just made it an invisble file on my home i.e. ~/.Realplayer
iv. No more work is required for installing realplayer plugin.

2. Install flash9: 
A nice installation procedure is [http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/]("http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/")

3. Install Mozilla-browser: 
```
$sudo aptitude install mozilla-browser
``` 


4. you are good to go: 
```
$mozilla [http://www.cbs.com/innertube/](http://www.cbs.com/innertube/) & 
```

Problems:
1. Track bar on bottom of video only seems to appear if play with the flash a bit.  If, for instance, you press the right button on the video and select pause and then right click again to select play it will appear.
2. Full screen doesn't work.
3. Obvious, this solution does not work with GPL software notably mplayer rather than realplayer.

I hope this helped.  Please if you find a solution to any of the above 3 problems I would appreciate their solution.

My computer has rather limited specs and still plays the stream well:
P4 1.8GHz, 512mb RAM, NVIDIA NV6 [Vanta/Vanta LT] (rev 15) graphics card - no Beryl :-(.

---

### Post by yigal.weinstein on 2007-02-24
This is great news as of Feb. 24 I tested and firefox can be used to watch innertube.

---

### Post by laser_in_your_eye on 2007-03-15
> **yigal.weinstein said:**
> This is great news as of Feb. 24 I tested and firefox can be used to watch innertube.

How did you get it to work after 2/24?  Mine still sits on a black screen with a message that my video will play after a brief message.  

I tried the mozilla browser too and although I can see video, it is very choppy.  The video plays fine on windows with the same internet connection.

---

### Post by yigal.weinstein on 2007-03-15
I guess I will have to ask the generic question of what codecs & plugins do you have installed?

flash & realplayer ?

---

### Post by sdowney717 on 2007-04-29
I found that for me it needed an updated nphelix g2 plugin

and here it is!

---

### Post by yigal.weinstein on 2007-04-30
This should really be uneccessary.  Totem seems to be able to handle playing the rm and of course realplayer can, I have been unable to get mplayer to play it though :(

---

### Post by mdeslaur on 2007-05-04
I had to disable AdBlockPlus in firefox to get innertube to work.

---

### Post by laser_in_your_eye on 2007-05-08
i tried disabling adblock plus and it made it so that i could view "player settings" where i confirmed that realplayer is installed.  also, when i right click on the viewing window without adblock i get the standard menu for right clicking anything in firefox.  when i do the same thing with adblock enabled it only get the flash player menu.  

still cannot get any video or sound...very sad

---

