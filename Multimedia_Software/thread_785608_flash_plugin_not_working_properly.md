---
title: "flash plugin not working properly?"
date: 2008-05-07
forum: Multimedia Software
---

### Post by nikosm on 2008-05-07
Dear community,

This regards the flash plugin in firefox 3 on hardy. The first time I visited a site that required a flash plugin, I got asked which one I'd like to install, I can't remember which one I chose, but now I am experiencing problems with certain cites. Sometimes the flash are displayed wrongly (e.g. [www.ted.com](www.ted.com)) , sometimes they don't get beyond some point (e.g. [www.timflach.com](www.timflach.com)) you see the first screen where it says loading and shows the percentage, after 100% is reached the percentage disappears but nothing happens). Firefox becomes non-responsive for a couple of seconds, then comes back, then becomes non-responsive again and so on... There is a lot of disk activity during that. In general, firefox is very slow when a flash is running.

I was wondering if it actually matters which plugin I chose to install. I wanted to try a different one to see if the error goes away, but I don't know how to change that now.

I tried installing flashplugin-nonfree with apt-get and saw that it's already installed.

Any ideas?

Thanks a lot,
Nikos

---

### Post by Xiong Chiamiov on 2008-05-07
Aside from Firefox 3 being a beta, the flash plugin is closed-source and developed by Adobe.  Until they stop producing crap, we can't do much about it.  Sometimes it works, and sometimes it doesn't.  You can try uninstalling it and using gnash.  Also try a different browser, whether a truly different browser (Kazehakase, Opera, Galeon, Epiphany) or just a rebranded Firefox (Swiftweasel, Swifterfox, IceCat/Iceweasel).

---

### Post by indiana_crook on 2008-05-07
> **nikosm said:**
> Dear community,

This regards the flash plugin in firefox 3 on hardy. The first time I visited a site that required a flash plugin, I got asked which one I'd like to install, I can't remember which one I chose, but now I am experiencing problems with certain cites. Sometimes the flash are displayed wrongly (e.g. [www.ted.com](www.ted.com)) , sometimes they don't get beyond some point (e.g. [www.timflach.com](www.timflach.com)) you see the first screen where it says loading and shows the percentage, after 100% is reached the percentage disappears but nothing happens). Firefox becomes non-responsive for a couple of seconds, then comes back, then becomes non-responsive again and so on... There is a lot of disk activity during that. In general, firefox is very slow when a flash is running.

I was wondering if it actually matters which plugin I chose to install. I wanted to try a different one to see if the error goes away, but I don't know how to change that now.

I tried installing flashplugin-nonfree with apt-get and saw that it's already installed.

Any ideas?

Thanks a lot,
Nikos

You might try uninstalling what flash plugins you have currently, and reinstall that flashplugin-nonfree that you said you already have.  What Graphics card do you have?

---

### Post by nikosm on 2008-05-07
Dear Xiong Chiamiov,

> **Xiong Chiamiov said:**
> You can try uninstalling it and using gnash.

I am not sure I understood what you suggested, but closing firefox running

```
sudo apt-get remove flashplugin-nonfree
```

and then 

```
sudo apt-get install gnash
```

and restarting firefox and visiting the problematic flash page didn't seem to have any effect.

I will try to install Swiftweasel this weekend.

Thank you very much for your suggestions.

Nikos

---

### Post by nikosm on 2008-05-07
> **indiana_crook said:**
> You might try uninstalling what flash plugins you have currently, and reinstall that flashplugin-nonfree that you said you already have.  What Graphics card do you have?

Hi indiana_crook,

I have already tried what you suggested, it didn't have any obvious effect. 

I should add that the flash doesn't always go to _exactly_ the same point before freezing, it's only more or less the same point every time.

My graphics card (from hardinfo):
```

-PCI Devices-
VGA compatible controller		: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller 
Display controller		: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller 

```

I have a lenovo X60 by the way, if that is relevant.

Thank you for your suggestions,
Nikos

---

### Post by bkly-dog on 2008-05-12
Firefox 2 was working fine for me on Gutsy. After upgrading to Hardy (with Firefox 3), the flash plugin is unreliable. I've installed flashplugin-nonfree. 

The flash plugin works great on some sites like youtube, but fails on many other sites including nytimes.com, ted.com, and dailyshow.com. 

What happens is that the "loading..." busy sign just keeps playing continuously and indefinitely.

Searching all the forums and the whole web, I've seen very little about this until I found this forum.

Does anyone know why the flash plugin worked fine for me on Gutsy, but is now failing?

---

### Post by nikosm on 2008-05-12
Just to let you know that installing swiftweasel didn't make any difference to the flash plugin behaviour.

Any ideas of what else to try?

Thanks,
Nikos

---

### Post by gandaran on 2008-05-12
> **nikosm said:**
> Just to let you know that installing swiftweasel didn't make any difference to the flash plugin behaviour.

Any ideas of what else to try?

Thanks,
Nikos

nikosm 
      there are three flash packages available for install, the only one recommended is the flashplugin-nonfree (adobe flash), the other two, gnash and swfdec don't work on many flash web pages, if you have gnash or swfdec, remove them and install only the flashplugin-nonfree package!

---

### Post by nikosm on 2008-05-12
Hi gandaran,

> **gandaran said:**
> nikosm 
the only one recommended is the flashplugin-nonfree (adobe flash), the other two, gnash and swfdec don't work on many flash web pages

I was using the nonfree flash plugin in the beginning of the post. It was with that plugin that the problem arised in the first place.



Changing it to gnash, as suggested above, didn't have any effect, maybe I did something wrong?

Kind regards,
Nikos

---

### Post by gandaran on 2008-05-12
nikosm 
      I visited the two sites you mentioned and they work fine with the adobe flash! do you also have the sun-java6-plugin installed? what about firefox settings, java enabled, flash pop-up blocked & etc?

---

### Post by nikosm on 2008-05-12
> **gandaran said:**
> nikosm 
I visited the two sites you mentioned and they work fine with the adobe flash! do you also have the sun-java6-plugin installed? what about firefox settings, java enabled, flash pop-up blocked & etc?

Java was enabled, sun-java6-plugin is installed, however gcj is used by firefox to display applets.


I don't know how, but the problem disappeared! I don't have an explanation, here is a list of things I remember doing since last time I checked:
 - in preferences, set Shockwave flash file / Shockwave flash Object to open with movie player.
 - reboot
 - start firefox, disable the gcj plugin

This is by no means a recipe to fix the problem, since as I said I don't know what fixed it. I have a faint suspicion that I was not using the nonfree plugin all the time, since there was a play symbol in every flash object that one had to press in order to start it. Now it was not like that, which might be an indication that only now is the adobe plugin being used.

Thanks to everybody for the useful suggestions and sorry for being unable to help others with this post - I just can't figure out what did the trick...

Nikos

---

### Post by nikosm on 2008-05-12
Hi bkly-dog,

> **bkly-dog said:**
> Firefox 2 was working fine for me on Gutsy. After upgrading to Hardy (with Firefox 3), the flash plugin is unreliable. I've installed flashplugin-nonfree. 

Do you have to push a "play" button for the flash animations to start? If so, you might be using a different plugin too, like I suspect I was doing... My experience is that a plugin installed is not necessarily used by firefox.

Good luck,
Nikos

---

### Post by bkly-dog on 2008-05-12
I don't necessarily have to push a "play" button. For instance, on ted.com, when I click a video link, the window comes up and sits there looking like it's ready to play a video, but nothing happens (the pause button in the control strip is available; when I click it, it turns into a play button, when I click that, nothing...). 

On nytimes.com and thedailyshow.com, the video window is drawn, but the "loading..." message just keeps playing continuously and indefinitely.

Videos on youtube work fine. 

I should mention:
Ubuntu Hardy 64
flashplugin-nonfree
Firefox 3 Beta 5

Isn't anyone else having this trouble? I've installed and reinstalled this software in different combinations and get the same exact results every time. 

This is a killer. How can one run a system that can play videos from most sites???

Any suggestions? Anyone seen this problem?

---

### Post by bkly-dog on 2008-05-12
And, by the way, I tried changing the action for both Sockwave Flash file entries in Firefox preferences--for application/x-shockwave-flash and application/futuresplash. I changed them both to "use movie player (default)", but that didn't fix the problem. In fact, Firefox seems to continue to use the Adobe flash player instead, for some reason. 
I confirm which video plugin is being used by right clicking on it. I get the menu for Adobe flash player 9.

---

