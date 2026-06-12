---
title: "Adobe Flash Fullscreen Freeze"
date: 2009-02-13
forum: Multimedia Software
---

### Post by krazyman on 2009-02-13
Hi All,

I'm getting a problem with Flash videos eg Youtube, BBC Iplayer etc. Here's what happens:

* Go to page, start watching video
* Hit fullscreen button
* Entire Flash frame freezes (video and animated buttons)
* Sound continues

I'm using

* Nvidia GeForce FX5500 256MB AGP8X card, with the Version 173 Proprietry Driver.
* Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6
* Adobe Flash version 10,0,15,3

I've tried:

* Switching to the older Nvidia proprietry driver
* Switching to the non-proprietry driver
* Removing and reinstalling the packages adobe-flashplugin, flashplugin-nonfree, flashplugin-nonfree-extrasound
* Renaming the ~/.mozilla/firefox directory to force a brand-new config
* Using Opera instead of Firefox
* Trying different websites

I've also tried using the swfdec and gnash flash players. They both work on fullscreen, but the former always uses about 60% cpu, and is choppy on fullscreen. The latter always uses about 50% cpu, and is good on fullscreen, but you have to right click and select view -> fullscreen (if you click the 'player' button for it, it ignores you).

So it defo looks like a problem with Adobe Flash. I'd rather use the Adobe version, since it's so much more efficient (16% cpu)...

It was last working probably a couple of weeks ago, last time I used it.

What on earth's happened?!

TIA,

Andy

---

### Post by ajgreeny on 2009-02-13
Try completely uninstalling, ie purging, and then reinstalling.  I have just had a problem with flash 10 on my 8.04.2 box, where I lost all sound in flash quite suddenly and a total reinstall did the trick.  It might work for you too.

---

### Post by krazyman on 2009-02-13
Ok, I did

apt-get purge flashplugin-nonfree-extrasound flashplugin-nonfree adobe-flashplugin

then reinstalled, but to no avail :(

---

### Post by Kar.ma on 2009-02-13
Could you please tell 

1) which version is reported in this page: 
[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) 

2) which file is listed under Shockwave Flash if you write in firefox address bar:
```
about:plugins
```

---

### Post by krazyman on 2009-02-13
webpage gives:
10,0,15,3

about plugins gives 
    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

Any ideas?

---

### Post by mr.datsun on 2009-02-14
A few people have reported this recently and usually attribute it to browser version, plug-in and/or their video card. My experience and research suggests that all these theories are wrong. 

Firstly, I have seen reports of this from people using different browsers, and different video cards. e.g nVidia cards or even on-board GPUs.

Secondly, I have experienced this on a new project which is Projector-based. The movie was compiled in Flex 2, written in AS3 and then made into a projector using the latest Windows Projector player v10.0.23 or something. 

The freeze occurs somewhere between a  second of entering video accelerated fullscreen mode and up to 8 days later. Seems to be unpredictable and unreproducible in my case, although other claim to get it each time they use iPlayer in a browser.

Thirdly, some people suggest that this is something related to video playback and their codecs. My experience contradicts this. My Flash 10 exe is playing sequences of bitmap slides, animated vector content and h264 full-screen movies on a stage running at 2880 pixels by 1600. As of now it has crashed in both slideshow mode and vector graphic mode. So it does not rely on video playback.

To confirm what others have written, this appears to be nothing to do with Flash freezing or AS3 errors. The movie's graphical display freezes until the ESC key is pressed. This exits fullscreen mode. And at that point the Flash movie is unfrozen and the content is revealed to be still animating as normal.

I have seen reports of this behaviour as far back as 2007 using the Flash 9 player. I think we will see more as fullscreen mode becomes more widespread.

I have seen official but unresolved bug reports on Adobe's site describing this same problem.

Any ideas or further information gratefully received.

---

### Post by krazyman on 2009-02-14
Ok I have found what's happening. It's not fixed, but I can work with it...

The fullscreen movie is playing BEHIND the firefox window. So if I minimise the window, there it is. It's not ideal tho, since if I alt-tab away from firefox, it's lost, I can't get it back at all. I have to navigate away from the page and back, to watch again.

I found this when trying to use captureMyDesktop to illustrate the problem. Since I normally use a maximised window for browsing, I never realised it was there.

Can anyone shed any light on why this may be happening?

Cheers.

---

### Post by WhiteHorse on 2010-03-16
Confirmed, this looks like a bug in flash. It started happening to me around version 10 in both chrome and firefox. Lots of people are reporting the same problem in IE and other browsers on windows and Mac. 

Some people have fixed it by disabling hardware acceleration in the flash setting menu(right-click on movie) but this doesn't work for me.

I'd like to thank Adobe for another let down. First we have to wait YEARS to get a plugin for our open source browsers. Then we have to deal with outdated plugins from them for years more. Then we get the lame-o version of the plugin with no mic or webcam. Then we get the full-screen freeze version forced upon us when the previous version actually used to work.

I've tried their latest beta as well. I'm convinced there's nothing wrong with my graphics card or OS because I can play full-screen flv, avi, etc in totem and vlc with no problems. I can run Nexuiz and other hardware accelerated games no prob.

Can we please come up with a work-around to using flash? I mean seriously! All I want is to look at videos online. I'd like to be able to save them to disk if I choose and I'd like the option to view fullscreen instead of a tiny box inside my browser. I've been testing HTML5 through Chrome and while it seems to provide the same thing flash does, it doesn't do fullscreen or allow saving to disk.

For those who are interested in trying HTML5 go to:
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by mrebanza on 2010-09-22
unfortunately i have found that Compiz Effects tend to cause these types of issues with flash . . . 


Solutions?

Temperately switch your "Window Manager" from compiz to Metacity with the "Compiz Fusion Icon" with can be downloaded from Ubuntu Apps Store or by running the following command from a terminal.  


```
sudo apt-get install fusion-icon
```

[IMG]http://thumbla.com/images/images/compizfusi.png[/IMG]
:popcorn:

---

### Post by Kuzma86 on 2010-10-19
Solution posted on this thread!!!

[http://guide.ubuntuforums.org/showthread.php?p=9996187#post9996187](http://guide.ubuntuforums.org/showthread.php?p=9996187#post9996187)

---

### Post by erectus on 2011-01-09
I had the same problem (flash video freezes in fullscreen) and I found the solution at [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)
 
 ```

 sudo mkdir /etc/adobe
 echo "OverrideGPUValidation=true" >~/mms.cfg
 sudo mv ~/mms.cfg /etc/adobe/
```this worked for me... hope this helps

---

### Post by opiumpoetry on 2011-03-13
here's what worked for me [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=10513659#post10513659[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10513659#post10513659") you may or may not have to uninstall Adobe Flash

---

### Post by ericjhemp on 2011-08-08
I have the same problem but the solution doesn't work for me :(
Even if I click metacity it freezes when I try fullscreen

---

### Post by pavankm on 2012-06-15
On fullscreen Frame rate drops considerably, but absolutely no frames are dropped in normal size view

---

