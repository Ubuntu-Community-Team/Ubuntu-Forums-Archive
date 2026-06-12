---
title: "Rhythmbox panel icon - one click to open?"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Middlerun on 2010-06-15
I used to be able to open the Rhythmbox window by just clicking the Rhythmbox icon in the notification area. Now in Lucid it brings up a menu (isn't that what right click is for??) and I have to select "Show Rhythmbox", and sometimes I accidentally click on "Quit" and I have to start Rhythmbox again. It's a real PITA. Is there any way to make it the way it was before? I've looked at the Rhythmbox options and can't find anything about it. (Why do GNOME applications always have barely any options?)

EDIT: Fixed in Maverick! :D

---

### Post by kev92486 on 2010-06-23
I'm looking for a fix to this as well.  It's only one extra click to perform, but then I have to move my mouse down to "Show Rhythmbox" as well which really throws off a routine that I've been used to doing the same way for a few years now.

---

### Post by jaminthorns on 2010-06-26
This is because, in Ubuntu, Rhythmbox uses the application indicator instead of the notification area. This gives all icons a menu and provides no right-click functions in an effort to streamline tray icons and introduce universal standards. It's not a bug, just a new way of doing things, and it's not going to be reverted so you'll just have to deal with it unless you can find a way to force the use of the notification area yourself (which might actually be possible, i'm not sure).

---

### Post by cybrsaylr on 2010-06-26
Why not just add the Rhythmbox icon to the upper panel alongside the FF and Help icons. I did this. Then you just click on the Rhythmbox icon once for it to open. 

All I did was click Applications > Sound & Video > then dragged the Rhythmbox icon into the upper panel next to FF and Help icons.

---

### Post by almostalive2003 on 2010-06-30
Would it be possible uninstall the version that came with Lucid and get a deb file for the version that came on Karmic and use that instead? Or would it still do the same thing?

I love Rhythmbox. I've tried using others but they are all to fancy and usually use more ram and cpu then Rhythmbox. It's just this one thing is really annoying. Because of it I did try other players. Which that one part did work the way I liked it. I just didn't like the players.

Or could somebody suggest something besides banshee and exaile. Similar to Rhythmbox.

---

### Post by CarpKing on 2010-06-30
If anyone else picks up this new standard, changing music players won't resolve this annoyance.  That's the thing about standards.  I hope they put a little more thought into making this not only consistent, but consistently good.

---

### Post by HeWhoE on 2010-07-19
As a temporary fix, I've replaced the status icon plugin by taking a copy of the plugin from my Fedora 13 system and using it to replace the one in my Ubuntu system. 

The temporary fix (until I figure out where to find the source package for this plugin):

[LIST=1]
[*] Extract the attached tar.gz file
```
tar xvf rhythmbox-status-icon-plugin.tar.gz
```

[*] Replace the Ubuntu 10.04 version of the status icon plugin with the one extracted from the archive.
```
cp -R status-icon /usr/lib/rhythmbox/plugins/
```
[/LIST]



NOTE: The included files are for x86 systems.

---

### Post by Marctwo on 2010-07-19
As soon as I tried Rhythmbox a couple of weeks ago I knew I wouldn't be using it on a daily basis specifically because of this.  The whole point of tray icons is to be quick and intuitive.

> **jaminthorns said:**
> This is because, in Ubuntu, Rhythmbox uses the application indicator instead of the notification area. This gives all icons a menu and provides no right-click functions in an effort to streamline tray icons and introduce universal standards. It's not a bug, just a new way of doing things, and it's not going to be reverted so you'll just have to deal with it unless you can find a way to force the use of the notification area yourself (which might actually be possible, i'm not sure).

I'm new to Linux so I don't quite know how things are done around here yet...  But I can't see the point of capping an intuitive interface that all OS users are familiar with.  Who exactly is this better for?

I've only been using Ubuntu for a few weeks but I'm sick to death of getting the panel menu instead of the useful menu that I want when I right click on one of these 'tray' icons.

---

### Post by liedan on 2010-07-21
A simple solution would be if double click opened rhythmbox. This is how notification area works in windows and I think it' s quite intuitive.

---

### Post by bpeel on 2010-07-22
Whatever the technical excuses for this it's still a really bad idea in my opinion. Having right click open a context menu is deeply ingrained into most user's intuition so removing that seems totally absurd. Especially as the right mouse button now does nothing.

What happened to being able to hide the rhyhmbox window by clicking on the icon? I can't find any obvious way to do that any more. The status icon is now effectively useless.

---

### Post by Moustaffa on 2010-08-07
I also found this unhandy, but lately I've been using Docky and this solves the problem for me (single clicking Rhythmbox icon the dock shows and hides the window).

It's a pretty good dock actually compared to the old ones (AWN, Cairo, SIM), those sucked imo.

---

### Post by Bartdmm on 2010-08-23
> **HeWhoE said:**
> As a temporary fix, I've replaced the status icon plugin by taking a copy of the plugin from my Fedora 13 system and using it to replace the one in my Ubuntu system. 

Thank you so very much. The new status icon system in 10.04 has annoyed me greatly since its release, and you have now finally rid me of this particular(ly bad) annoyance.

I can finally use Rhythmbox again the way it was meant to be used.

---

### Post by oyejorge on 2010-08-25
It worked so much better in Jaunty.

The left click should show/hide rhythmbox and the right click should show options. It feels like I'm working on a mac without the right click.

I am unfortunately getting an error with HeWhoE's temporary fix
> ** (rhythmbox:26048 ): CRITICAL **: app_indicator_set_menu: assertion `GTK_IS_MENU (menu)' failed

---

### Post by bryonak on 2010-08-27
I've run across this problem after updating an Ubuntu surf station a few days ago. It's quite an annoyance, and since HeWhoE's solution (good find, by the way!) doesn't work for me (I assume the shared object is 32bit), I made a 64bit package.
The attached deb replaces the three differing files in /usr/lib64/rhythmbox/plugins/status-icon/ with equivalents from my Fedora install.
The forum seems not to allow debs, just extract it via "right click, extract here" first.

Note that installing this package will *overwrite* the status plugin, so if you remove it again Rhythmbox will not have a working status-icon plugin. This can be then fixed by reinstalling rhythmbox-plugins.
Of course, no warranty and you're responsible for your own computer ;)

---

### Post by liedan on 2010-08-27
> **bryonak said:**
> I've run across this problem after updating an Ubuntu surf station a few days ago. It's quite an annoyance, and since HeWhoE's solution (good find, by the way!) doesn't work for me (I assume the shared object is 32bit), I made a 64bit package.
The attached deb replaces the three differing files in /usr/lib64/rhythmbox/plugins/status-icon/ with equivalents from my Fedora install.
The forum seems not to allow debs, just extract it via "right click, extract here" first.

Note that installing this package will *overwrite* the status plugin, so if you remove it again Rhythmbox will not have a working status-icon plugin. This can be then fixed by reinstalling rhythmbox-plugins.
Of course, no warranty and you're responsible for your own computer ;)

Many thanks!!! A can confirm it works like a charmm.:popcorn:
(Ubuntu Lucid 64bit)

---

### Post by lunatico on 2010-08-30
> **HeWhoE said:**
> As a temporary fix, I've replaced the status icon plugin by taking a copy of the plugin from my Fedora 13 system and using it to replace the one in my Ubuntu system. 


I tried this but not getting applet status icon at all. If I start from command line I get error:

```
** (rhythmbox:781): CRITICAL **: app_indicator_set_menu: assertion `GTK_IS_MENU (menu)' failed

```

Any ideas? Question about the fix, does it give the scroll-over-icon functionality back? Before they changed this I used to be able to scroll over the icon to change volume or change song (configurable from plugins section in the application).

Thanks!

---

### Post by Cavsfan on 2010-09-09
I searched for a solution to this problem and could not find one, but I did find out how to fix it. See if [[COLOR=blue]_this post may solve your problem._[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9825402&postcount=10")

---

### Post by lunatico on 2010-09-09
> **Cavsfan said:**
> I searched for a solution to this problem and could not find one, but I did find out how to fix it. See if [[COLOR=blue]_this post may solve your problem._[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9825402&postcount=10")

Thanks! But not quite... there is the option I need there. mouse-wheel-mode set to 1. But the icon won't take it... even if I remove indicator-application to force it to life in the notification area as opposed to the indicators area still no joy.
It's just sad how they broke this. :(

---

### Post by Cavsfan on 2010-09-09
> **lunatico said:**
> Thanks! But not quite... there is the option I need there. mouse-wheel-mode set to 1. But the icon won't take it... even if I remove indicator-application to force it to life in the notification area as opposed to the indicators area still no joy.
It's just sad how they broke this. :(

Maybe it's the Karmic vs. Lucid thing. It works perfectly for me now. I don't like things to be difficult. 
I want to click on something and I expect it to open and when I click close I expect it to close. And that is how mine works now.

---

### Post by patryk77 on 2010-09-23
Another alternative solution I thought of...

I went to System / Preferences / Keyboard Shortcuts

I set: Sound / Launch Media Player to Ctrl+Alt+M

I can now open it with that shortcut... I can live with that :guitar:

---

### Post by aryasudhanshu on 2010-10-18
> **HeWhoE said:**
> As a temporary fix, I've replaced the status icon plugin by taking a copy of the plugin from my Fedora 13 system and using it to replace the one in my Ubuntu system. 

The temporary fix (until I figure out where to find the source package for this plugin):

[LIST=1]
[*] Extract the attached tar.gz file
```
tar xvf rhythmbox-status-icon-plugin.tar.gz
```

[*] Replace the Ubuntu 10.04 version of the status icon plugin with the one extracted from the archive.
```
cp -R status-icon /usr/lib/rhythmbox/plugins/
```
[/LIST]



NOTE: The included files are for x86 systems.


Awesome man! Rhythmbox was getting frustrating to use. I am still not clear as to what the rationale behind making such a change was but this is certainly not a change for good. Total lack of usability.

---

### Post by Cavsfan on 2010-10-19
Since installing Maverick Desktop 64 bit, this is no longer an issue. When I open Rhythmbox, it just opens and doesn't go to the panel
like it did in Lucid.
It tried to pull in every one of my songs though and I had to do tell it not to update. But, all is smooth in Maverick.

---

