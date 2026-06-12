---
title: "Cannot play embedded flash videos in Karmic"
date: 2009-11-18
forum: Multimedia Software
---

### Post by mikebeecham on 2009-11-18
Hi guys,

I'm trying to view an embedded video on a website, but am having problems.  I know that Flash is installed and I know that flash works, but for some reason all I see is the video window (with nothing in it!), a couple of squares on the outside corners of the video window....and that's kind of it!

Is this a flash thing, a Karmic thing and, more importantly, can it be resolved?

Thanks

---

### Post by arnab_das on 2009-11-18
the restricted extras package has adobe flash in it.

[http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

the above link is a guide for the installation of restricted extras.

---

### Post by mikebeecham on 2009-11-18
HI arnab-das...

I already have the restricted-extras installed.  I've also uninstalled flashplugin, reinstalled flashplugin, uninstall vlc and reinstalled.

I'm at a bit of an impass at the moment.

---

### Post by arnab_das on 2009-11-18
try restarting your PC. sometimes happens to me as well. but restarting the PC/sometimes the browser resolves it.

---

### Post by mikebeecham on 2009-11-18
No go Arnab-Das....no change!

---

### Post by arnab_das on 2009-11-18
> **mikebeecham said:**
> No go Arnab-Das....no change!

go to this page:

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

see if u can see the flash video there. dont check for shockwave.

---

### Post by mikebeecham on 2009-11-18
Flash there is fine, which tells me again that flash (generally) is fine.  Watching flash-embedded videos are not?

It's good to help localise the issue by brain-storming it!

---

### Post by arnab_das on 2009-11-18
are u using flash block or any such firefox add ons? adblock plus? it shouldnt affect it, but try disabling them and recheck.

---

### Post by mikebeecham on 2009-11-18
Nope, the only one I'm using is styles

---

### Post by lovinglinux on 2009-11-18
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by arnab_das on 2009-11-18
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

wow! cool solution! +1000

@mike 

do keep us posted if it solves ur problem.

---

### Post by arnab_das on 2009-11-18
> **lovinglinux said:**
> See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

i'll bookmark that link for future use! :)

---

### Post by mikebeecham on 2009-11-18
Hi guys...

No, I'm sorry that didnt solve my problem.  Again, I know flash is working as I got a nice flash presentation on the Adobe website, but no difference to this embedded video!

The thing is, I've got Firefox, Opera and Chrome/Chromium on my machine here, and it does not work on any of them!

---

### Post by mad_prince on 2009-11-18
Hi, I've the same problem. I can't play embedded videos, for eg. from youtube, but when I go on youtube website all videos work fine.
But videos in JWPlayer work fine on all sites, so I think that the problem is only with YT and MegaVideo.

---

### Post by ArinSky on 2009-11-18
sudo apt-get remove flashplugin-* --purge
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
sudo apt-get install flashplugin-nonfree

if gnash or swfdec are default with karmic, then that should fix the problem which stems from them. I had this same problem with jaunty at first, but if you uninstall all flash and install just adobe it should fix it.

---

### Post by mad_prince on 2009-11-19
it doesn't work. But I found sth interesting. If any movie/control in flash doesn't work, I use Right click on it at first, and then normal left click, and it usually works :) I don't know why.

---

### Post by mikebeecham on 2009-11-20
Hi,

None of those options worked, and I've uninstalled and reinstalled a bunch of stuff...what I see is this.

On the webpage I can see the video window.  If I hover open the window then some play controls appear (play/pause, volume up/down, etc).  But nothing happens.

To the right of that window SHOULD be a list of 'episodes' that I can choose from...I should be able to see them, click on an episode and it start playing.  However, instead of the list all I see are two grey squares, one in the top-left corner of where the list should be, and one in the bottom-left corner.

It's almost like part of the flash (video window) is working as it should, but the other part (list) is not?

---

### Post by steve_k on 2009-11-21
FWIW, I'm experiencing the same problems, mainly with embedded Youtube videos and also with the BBC iPlayer. 

I've tried all the various solutions on this thread to no avail. So, I too, will be very interested to see what further suggestions will be made.

I'm currently running 9.10 with Firefox 3.5.5. It also makes no difference whether I'm running Firefox with/without any plugins, the problem remains the same.:confused:

---

### Post by The Resident Expert on 2009-11-21
I'm also having this problem.  At first I could only see videos on YouTube if I popped them out into a separate window; now I don't have to do that but I still can't see embedded video.  And I'd just got Jaunty the way I liked it, too.  Alas, why did I upgrade?

---

### Post by steve_k on 2009-11-22
I re-tried Mad_Prince's suggestion of right clicking before left clicking and it seems to work! Although I'm finding that I have to do a combination of right/left clicking before the embedded video working.

It's not ideal, but a suitable compromise. 

Nevertheless, thanks for the tip.

---

### Post by uboss on 2009-11-22
I'm having the same problem. I have to play with right/left click multiple times to just make a single click. Very annoying...indeed!

---

### Post by uboss on 2009-11-22
My problem solved. This is what I did: (Just to mention I have AMD 64 Karmic )
1. I downloaded the alpha version of flash player 10 for AMD 64 Linux) from this** [link]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")**
2. Extracted the libflashplayer.so file
3. In synaptic package manager removed **nspluginwrapper** which also removed flashplugin-nonfree, acroread and acroread fonts
3. Made new folder named **plugins** in **/home/user/.mozilla** and copied the **libflashplayer.so** file there.
4. Restarted Firefox and flash videos were working fine and I could easily click on the controls.
BUT..! I noticed that it was taking too much of CPU usage. So I deleted the plugins directory which I just made and re-installed nsplugin with synaptic and later re-installed acroread, acroread fonts, and flashplugin-nonfree. And now it is working just fine.

I think just un-installing nspluginwrapper and flashplugin-nonfree  and re-installing them did the trick.  The 64bit Alpha version of flashplayer was working fine but it was using too much resources so I decided to keep the flashplugin-nonfree which is working fine for now.

---

### Post by uboss on 2009-11-22
It worked for some time and after restarting started doing the same thing.  So I ended up using  the 64bit alpha version for flash player. Which is working fine except that it is taking too much resources.

---

### Post by andydread on 2009-11-22
I am having the same problem.  Running Karmic 64bit.  Embedded videos do not work.  On some sites the video controls do not work either and on some videos even at youtube the controls do not work.  Tried downloading the 64bit alpha from adobe and removing all other plugins and that worked but is very very unstable.  Firefox crashes (just disappears) going to many sites with flash.  So I had to remove the 64bit alpha and reinstall flashplugin-nonfree.  Gosh what a mess.  4G of ram drove me to install the 64bit Karmic in the first place.  Because none of their 32bit kernels support bigmem like Debian does.  So now I have 64bit Karmic and flash does not work.  Maybe Canonical can make a list of things that absolutely must work when they release a new version and test against that list? maybe? You know like at least a rudimentary form of quality control?  How can we release this version with such obvious breakage?  Wow. just WOW!

---

### Post by uboss on 2009-11-22
> I am having the same problem. Running Karmic 64bit. Embedded videos do not work. On some sites the video controls do not work either and on some videos even at youtube the controls do not work. Tried downloading the 64bit alpha from adobe and removing all other plugins and that worked but is very very unstable. Firefox crashes (just disappears) going to many sites with flash. So I had to remove the 64bit alpha and reinstall flashplugin-nonfree. Gosh what a mess. 4G of ram drove me to install the 64bit Karmic in the first place. Because none of their 32bit kernels support bigmem like Debian does. So now I have 64bit Karmic and flash does not work. Maybe Canonical can make a list of things that absolutely must work when they release a new version and test against that list? maybe? You know like at least a rudimentary form of quality control? How can we release this version with such obvious breakage? Wow. just WOW!

I'm pulling my hair since yesterday trying to fix it. I don't think it is Uuntu's fault. The culprit here is the **proprietary closed source flashplugin from adobe**. Which no one can do anything about except the adobe guys. 
But I do believe that more effort should be put into **gnash** (the opensource alternative to flash)  or something similar to get rid of this corrupt adobe flashplugin. I hope somebody can do something about it. 

Meanwhile I'm stuck with using this adobe flash plugin. The best thing to do is not to run more than one video at a time. I think I can live with that until someone finds a solution to this crap adobe plugin.

---

### Post by alecspoons on 2009-11-23
I am seeing the exact same thing as the original poster.
I'm using AMD 64 Karmic too.

---

### Post by Chadwick Crawford on 2009-12-05
I switched over to Chrome because this problem was so constant in Firefox, and that helped at first, but it's become buggy again. Sometimes reloading the page works, but most of the time I have to go to youtube.com to watch a video. Which is fine, but kind of annoying. Also using 9.10  on an AMD 64 laptop.

---

### Post by dentaku65 on 2009-12-06
See "my guide" for flash+firefox
[http://ubuntuforums.org/showthread.php?t=1346226](http://ubuntuforums.org/showthread.php?t=1346226)
Enjoy!

---

### Post by georgemcbaingage on 2009-12-06
Similar but different, I have flash installed, working fine, plays flash video on firefox but only if the video autoruns if the click here to play button  appears it does nothing. I know it must be the 64 bit that's the problem but really not sure where to start looking for a solution

---

### Post by karlkoch23 on 2009-12-19
Hi,

I am also on 64 Karmic with flashblock. My temporary solution is with the non-open adobe flash to simply use the space bar for starting and stopping the embeded video, clicking the volume controlls enables you to use up and down for volume, and left and right can be used for forward and reverse.
This is the best I could manage. Hope it helps.

---

### Post by TAFKARS on 2009-12-19
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

This one posted earlier on in the thread worked for me. I am also running the newly installed 64bit version of 9.10 (very buggy but getting there). Can now settle back and watch England torment SA via the (soon-to-be-knighted) king of tweak Graham Swann.

---

### Post by Kat of Zion on 2009-12-28
I have a relatively new computer (bought for xmas yesterday) and it runs Karmic 9.10. As of now, VLC and MPlayer do not play mp3s (but  Amarok does).  FLVs (and  embedded flash players such as what you find on YouTube) do not play anywhere (browser or otherwise)

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried the various flash players in synaptic and the libflashplayer.so file that others have reported success with. No luck on my install.  Is Karmic just too new to have caught up on having proper playback of flash elements?

---

### Post by misaelrod on 2010-01-04
Hey guys, i was having the same issue and ran across this perfect fix


[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

Enjoy

---

### Post by Kat of Zion on 2010-01-04
> **misaelrod said:**
> Hey guys, i was having the same issue and ran across this perfect fix


[http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/](http://technologycrowd.com/2009/11/01/installing-64-bit-flash-player-in-ubuntu-9-10-karmic-koala/)

Enjoy

Thanks for this.  Sadly in my case, I installed 32-bit Karmic on my machine rather than 64.  Im getting a feeling that it is just a matter of playing the waiting game. :eek:

---

### Post by enseyn on 2010-01-16
Same problem here, and none of these fixes have worked for me.

EDIT: nevermind, I didn't uninstall flash properly the first time. Given a second try misaelrod's suggestion worked perfectly! thank you so much.

---

### Post by Kat of Zion on 2010-01-18
> **enseyn said:**
> Same problem here, and none of these fixes have worked for me.

EDIT: nevermind, I didn't uninstall flash properly the first time. Given a second try misaelrod's suggestion worked perfectly! thank you so much.

Never did get an answer.  Anyone tried misaelrod's suggestion despite  runninga  32-bit Karmic install?   Im not planning on upgrading to a 64-bit distro anytime soon

---

### Post by Kets on 2010-07-07
It was a Compizproblem for me, i fixed it with this:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Thanks to 
[http://ubuntuforums.org/showthread.php?t=1422783](http://ubuntuforums.org/showthread.php?t=1422783)

---

