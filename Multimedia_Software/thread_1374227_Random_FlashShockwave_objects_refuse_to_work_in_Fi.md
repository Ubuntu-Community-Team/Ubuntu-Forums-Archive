---
title: "Random Flash/Shockwave objects refuse to work in Firefox"
date: 2010-01-06
forum: Multimedia Software
---

### Post by Objekt on 2010-01-06
I run Ubuntu 9.10 64-bit, using Firefox 3.5.6 (courtesy of Ubuntuzilla) as my Web browser.  I've had a problem with some Flash and/or Shockwave objects simply refusing to work inside Firefox, despite having 64-bit Flash player and all necessary plugins/addons/extras etc. installed.

There is no pattern to the problems, other than all of them being Flash or Shockwave objects that won't play.  The majority of Youtube videos do play, including HD ones.  However, this morning I encountered a pair of Youtube clips that Simply Would Not Play.  I could load the page they were on, but all I ever saw was a black box, with no audio, where the video should have been.

I also noticed that on some of the videos that do play, the Flash player's built-in volume control does nothing.  I can slide it up or down or mute it entirely, but the sound from the Flash video is unaffected.

I'll post URLs of the problem videos later, so others can try them.

Meanwhile I was able to watch other Youtube videos without issue, on another tab, aside from the broken Flash player volume control.

I've also had a problem with the streamaudio.com player for a radio station, which I believe uses Shockwave.  I like to listen to Atlanta, GA's WSB 750 AM radio in the mornings before work, but so far I have to do it on a virtual Windows XP machine running Firefox 3.5.6, under Virtualbox.  If I try to open the player in Firefox 3.5.6 running in the host OS (Ubuntu 9.10), I get only a blank popup window.  URL is [http://wsbradio.com/]("http://wsbradio.com/"); click the "Listen Live" box at upper left to try it.

Both machines, the host Ubuntu 9.10 install and the guest Windows XP machine, use exactly the same ad-blocking HOSTS file.  I use the NoScript addon in the host OS install of Firefox, but I allow any and all scripts when visiting the radio station's website.  

Since the streaming radio works on the virtual XP machine, I'm pretty sure my network configuration, HOSTS file etc. have nothing to do with this.

Has anyone else had this problem?  The Flash content really should be agnostic with respect to the host OS and browser, shouldn't it?

I guess it could be some random problem with the 64-bit vs. the 32-bit version of the Flash plugin, so I may try instaling 32-bit Ubuntu on a virtual machine to find out whether there's a difference.

---

### Post by JohnnyDiamond on 2010-01-06
I have the exact same but opposite problem. 

In Youtube and Vimeo, I can play every video I come across. 
However, when using my USB mouse, I can not control any of the playback functions. 
Rarely, I can pause and adjust volume with the trackpad mouse built in to my laptop. 

The space-bar-to-pause function usually ALWAYS works tho. 

Same on a 64-bit system.  I am going to try the new sticky uninstall everything and reinstall only flash tonight.

---

### Post by nanotube on 2010-01-06
> **Objekt said:**
> I run Ubuntu 9.10 64-bit, using Firefox 3.5.6 (courtesy of Ubuntuzilla) as my Web browser.  I've had a problem with some Flash and/or Shockwave objects simply refusing to work inside Firefox, despite having 64-bit Flash player and all necessary plugins/addons/extras etc. installed.


ubuntuzilla installs the 32bit build of firefox from mozilla, so you must be using a 32bit flash plugin with it. so... suggest you look in about:plugins to see which version you're running, and if it's not the latest, grab the latest 32bit flash plugin.

there's an ubuntuzilla faq on flash plugin here:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)

no telling if it will help or not... but doesn't hurt to make sure you're running the latest.

---

### Post by Objekt on 2010-01-06
That could be it.  about: plugins>Shockwave Flash says I have:

```
    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999
```

Adobe's version test webpage ([http://kb2.adobe.com/cps/155/tn_15507.html](http://kb2.adobe.com/cps/155/tn_15507.html)) also says I have "WIN 9.0.999.0" and (amusingly!) that my OS is Windows XP.  Curious.

I know the latest version of Flash is 10, with a 10.1 beta available.  So that could explain why some videos and streaming audio popups don't work for me: they work only with the newer version of Flash.

---

### Post by nanotube on 2010-01-06
so, try uninstalling the old flash plugin and grabbing the newest libflashplugin.so from adome and sticking it into ~/.mozilla/plugins/ directory.

---

### Post by Objekt on 2010-01-06
> **nanotube said:**
> so, try uninstalling the old flash plugin and grabbing the newest libflashplugin.so from adome and sticking it into ~/.mozilla/plugins/ directory.

Just did that, now have version 10.0 r42.  Fixed the issues.  Woohoo.

---

### Post by nanotube on 2010-01-07
> **Objekt said:**
> Just did that, now have version 10.0 r42.  Fixed the issues.  Woohoo.

cool! :)

---

### Post by Objekt on 2010-01-07
It would be great to have a sticky in the 64-bit forum to alert Ubuntuzilla users to this possible problem.  Knowing about it in advance would have saved me some trouble.

---

### Post by nanotube on 2010-01-07
> **Objekt said:**
> It would be great to have a sticky in the 64-bit forum to alert Ubuntuzilla users to this possible problem.  Knowing about it in advance would have saved me some trouble.

well, it /is/ stated on the ubuntuzilla website...

but if you'd like, feel free to make a post on the 64-bit forum and ask whoever's the mod there to sticky it... :)

---

