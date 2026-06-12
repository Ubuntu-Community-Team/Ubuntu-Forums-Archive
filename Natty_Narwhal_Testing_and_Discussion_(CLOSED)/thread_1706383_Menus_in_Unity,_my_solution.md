---
title: "Menus in Unity, my solution"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-03-13
The thing I miss most in Unity is the easy ability to create menus.

I have a lot of applications I use occasionally, but the launcher would have too many icons if they were all there. The Ubuntu button will probably have a solution to this problem when Unity is finished.  Until then I have devised this method of using text based menus to give me easy access to programs without cluttering up the launcher with too many icons.

To have better access to familar icons I installed the human theme with the command:
```

sudo apt-get install human-theme

```

Next I created a text based utility menu in a script file called "UtilityMenu.sh"

This is the file:
```

#!/bin/bash

clear 
echo " "
echo " "
echo "                               Utilities Menu"
echo " "
echo " "
echo " "
echo "                             1 - Calculator"
echo "                             2 - Conky"
echo "                             3 - pyRenamer"
echo "                             4 - Search for Files"
echo "                             5 - Take Screenshot"
echo "                             6 - Gparted"
echo "                             7 - Ubuntu Tweak"
echo "                             8 - Nautilus as Root"
echo "                             9 - Root Terminal"
echo " "
echo " "
echo " "
echo -n "                              Enter Selection: "
read choice

case $choice in
  1) clear 
     gcalctool;;
  2) clear
     conky;;
  3) clear
     /usr/bin/pyrenamer;;
  4) clear 
     gnome-search-tool;;
  5) clear
     gnome-screenshot --interactive;;
  6) clear
     gksudo gparted;;
  7) clear
     ubuntu-tweak;;
  8) clear
     gksudo nautilus;;
  9) clear
     gksudo gnome-terminal;;
esac

exit 0

```

Then I created a .desktop file to launch the script.

A .desktop file can behave kind of wierd. You can't click on it to open it with gedit.
You need to open it from the command line with the command:
```

gedit 'Utility Menu.desktop'

```

This is the "Utility Menu.desktop" file:
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Utility Menu
Exec=/home/USERNAME/UtilityMenu.sh
Icon=/usr/share/icons/Humanity/apps/48/administration.svg
Terminal=true
Type=Application
StartupNotify=true

Name[en_US]=Utility Menu

```

Now make both files executable and drag the icon for the .desktop file to the launcher.

I hope someone else finds this usefull.

These are the two threads I started in the process of figuring this out.

[http://ubuntuforums.org/showthread.php?t=1700605](http://ubuntuforums.org/showthread.php?t=1700605)
[http://ubuntuforums.org/showthread.php?t=1701240](http://ubuntuforums.org/showthread.php?t=1701240)

---

### Post by KrazyPenguin on 2011-03-13
Menus are cool!!!

---

### Post by kerry_s on 2011-03-13
how come you didn't use zenity ?

---

### Post by mc4man on 2011-03-13
good to see you're putting some use to this stuff..
just to add a bit to something - 

As you saw once a .desktop is created you can't simply rename the 'actual' name of the desktop _file_ (mv and the extended rename command can

You can however change the 'display' name at any point by simply editing in the .desktop - Name=, ie. the 'actual' and 'display'  don't have to be the same
(not really a factor or of interest here, occasionally can be useful.

---

### Post by kerry_s on 2011-03-13
> **mc4man said:**
> good to see you're putting some use to this stuff..
just to add a bit to something - 

As you saw once a .desktop is created you can't simply rename the 'actual' name of the desktop _file_ (mv and the extended rename command can

You can however change the 'display' name at any point by simply editing in the .desktop - Name=, ie. the 'actual' and 'display'  don't have to be the same
(not really a factor or of interest here, occasionally can be useful.


you can just use the main menu to create it, no need for all that work.

---

### Post by rburkartjo on 2011-03-13
jrv that is cool you could also do what i did. install cairo dock and put in the applications menu. it give you the menu as was in 10.10

---

### Post by rburkartjo on 2011-03-13
i also get it to launch as startup

---

### Post by kerry_s on 2011-03-13
just a quick example with zenity:

```

#!/bin/sh

choose=`zenity --text="Utilty's" --list --column="Select" "Root File Manager" "Root Terminal"`

if [ "$choose" = "Root File Manager" ]; then
	gksudo nautilus / &
fi

if [ "$choose" = "Root Terminal" ]; then
	gksudo gnome-terminal &
fi

exit 0

```

---

### Post by mc4man on 2011-03-13
> **kerry_s said:**
> you can just use the main menu to create it, no need for all that work.
Not sure what all that work refers to, how the Op choose to create a .desktop was up to him
There are sometimes when  it's just as easy to create a .desktop than use an alacarte created one, even though the end result _could _be the same

---

### Post by kerry_s on 2011-03-13
> **mc4man said:**
> Not sure what all that work refers to, how the Op choose to create a .desktop was up to him
There are sometimes when  it's just as easy to create a .desktop than use an alacarte created one, even though the end result _could _be the same

i mean it's less typing & you don't need to get the wording right, less chance of typo's.

i have nothing against how he did it, just saying you can just as easily do it from the main menu.

---

### Post by beew on 2011-03-13
> **rburkartjo said:**
> jrv that is cool you could also do what i did. install cairo dock and put in the applications menu. it give you the menu as was in 10.10


Isn't that kind of odd to have two docks on the same screen? I would prefer the Cairo dock (which I use now with 10.10, much better looking and more functional than the Unity dock, same goes for awn and dockey) but that is not possible to use with Unity since I can't remove the Unity dock.

---

### Post by VeeDubb on 2011-03-14
This is a step in the right direction.  Well, I'm not sure it's the right direction, except that any direction away from the unity menu is a good one.  I love everything about unity except for the lack of a usable application menu.  What they've put together is fine for netbooks, tablets, anything like that.  On the other hand, it just plain sucks for desktop usage.  

Sure, if you've only got a dozen apps you ever use, this is a dream come true.  

If you're like most people and have more application that you want to access, it's pretty lame.

If you have a lot of applications you use regularly, and a handful of applications with non-obvious names that are critically important but not frequently used, the unity menus are a nightmare.

I'll have to play with this for now, and see if anybody comes up with a more polished solution down the road.

---

### Post by beew on 2011-03-14
I am not sure what OP tries to do. Does it just add a bunch of desktop launchers instead of a menu with this approach?

I find the dash super user unfriendly and super impractical. Aside from the icons layout how do you open a program when you already have one running full screen? (it is in full screen because another "feature", the global menu requires it) You have to open the dash which take over the whole screen. They could have easily put a menu button on the Unity dock but I doubt that they would do that, since that undermines the "super smooth experience" and consistency (consistently awkward to use) of Unity.

---

### Post by beew on 2011-03-14
Is it possible to at least make the dash smaller so it doesn't take up the whole screen? Can the icon size in the dash be changed?

---

### Post by seeker5528 on 2011-03-14
> **VeeDubb said:**
> Sure, if you've only got a dozen apps you ever use, this is a dream come true.  

If you're like most people and have more application that you want to access, it's pretty lame.

If you have a lot of applications you use regularly, and a handful of applications with non-obvious names that are critically important but not frequently used, the unity menus are a nightmare.

:???: :???: :???:

Hmmm, [Unity](http://home.comcast.net/~seeker5528/Screenshot-Unity-vs-Menu1.png) Vs [traditional menu](http://home.comcast.net/~seeker5528/Screenshot-Unity-vs-Menu2.png).

Not really seeing how one is more of a nightmare than the other and Unity has those nice 'search' and 'Find available apps' options.

I guess the real question relative to what the OP said in the first post is.....

If you go to 'gnome-control-center --> main menu' and make changes, are those changes reflected in the Dash?

EDIT: And no Dash didn't show up full sceen, I had to click the little symbol in the lower right corner to make it go full screen, but maybe that depends on your screen resolution, didn't try resizing other than that. 

Later, Seeker

---

### Post by cariboo on 2011-03-14
Using gnome-control-center->Main Menu isn't going to do a lot of good, as Unity uses zeitgiest to display the most used applications/files in the Applications and Places menus.

Personally I would think it would be more of a usability nightmare if the old style menus were mixed in with the Unity menus.

---

### Post by beew on 2011-03-14
> **cariboo907 said:**
> Using gnome-control-center->Main Menu isn't going to do a lot of good, as Unity uses zeitgiest to display the most used applications/files in the Applications and Places menus.

Personally I would think it would be more of a usability nightmare if the old style menus were mixed in with the Unity menus.

I don't see how. If a menu option is added to the Unity bar (like in Cairo or awn) it will solve the problem. If you want the dash you don't have to add it. To each his own.

But to me the dash is just too intrusive. Right now I can open a new app by using a small menu in the Cairo dock (or the gome panel) without leaving the screen and the task I am doing, but with the Dash I have to let it take over the screen and then pick a category and then  click "show all apps" and then scroll through a long list of big icons before I can get it started. No amount of sophistry can convince me that this represents better usability.

I also can't see how the search option is more convenient than the menu. Besides, if you have to always use the search option this would defeat the purpose of the icon view anyway.

Instead of trying so hard to convince people that the Unity devs and Mark know better than the users what would produce the best user experience and shove their design down our throats why not just implement a few options so that everyone is happy? Or how about an option to change the icon size in the dash and a list view option for those who want to use it?

I know it is an alpha and I don't expect all or even many user requested features would be implemented immediately, or perhaps not even til 12.04. I am fine with that, but what I have a problem with is the dig in the heel response of some people involved along the line of "No, this is the best design and your feature request would not be considered because it is at odd with what we think would give you the best user experience." (or even worse, you can use the classic desktop or bugger off to another distro)

---

### Post by kerry_s on 2011-03-14
you can jump right to app section you want from the right click now.
so in a since a smaller menu is available, sure it still opens dash, but maybe that will change?

---

### Post by lucazade on 2011-03-14
> **beew said:**
> ..so that everyone is happy..

everyone?
Ubuntu has million of users.. did you get in touch with all of them?

Or you have only read some some hundred of bad comments about Unity?
which is only the 0.0001% of users maybe.

(nothing personal with you, but I don't understand why say "everyone" instead of "my personal opinion")

---

### Post by beew on 2011-03-14
> **lucazade said:**
> everyone?
Ubuntu has million of users.. did you get in touch with all of them?

Or you have only read some some hundred of bad comments about Unity?
which is only the 0.0001% of users maybe.

(nothing personal with you, but I don't understand why say "everyone" instead of "my personal opinion")

Adding options (options as in you don't have to use it ) allows everyone to have choice, it doesn't take away anything, so while I can't say everyone would be happy (some people are only happy with the old styled gnome panel so they would never be happy, some people are only happy with Windows or Mac so they would not be happy either, but that is a trivial and useless point) but definitely more people would be since options add, rather than subtract. It is just simple logic and you don't need to interview everyone to know that.

To ask you your own question, how do you know that everyone, or most people are happy with Unity as it is now? Just because my sample is limited it doesn't follow that your assertion is valid. In fact I am not aware that Canonical has done systematic market survey to gauge user attitude, who are the often cited "average users" or "new users"?  When did they express an opinion? Having the feed back of 0.00001% of users is better than not having any at all.

---

### Post by KrazyPenguin on 2011-03-14
> **beew said:**
> I am not sure what OP tries to do. Does it just add a bunch of desktop launchers instead of a menu with this approach?

I find the dash super user unfriendly and super impractical. Aside from the icons layout how do you open a program when you already have one running full screen? (it is in full screen because another "feature", the global menu requires it) You have to open the dash which take over the whole screen. They could have easily put a menu button on the Unity dock but I doubt that they would do that, since that undermines the "super smooth experience" and consistency (consistently awkward to use) of Unity.

Actually now that I am using Unity ON MY PRODUCTION MACHINE :shock:
it has become second nature to me.  I didn't think that it was possible at first!!!

Some choices on how to handle the fullscreen situation:
(BTW apps are NOT required to run in fullscreen --- they current app will be united in the top panel even if it isn't fullscreen)
- you can double click top panel to unmaximize it
- You can press <superkey> and press <superkey><#> to open up an app with corresponding number located on the launcher
- you can do a <superkey><a> and click on the app on the launcher
- you can press <superkey> and click from favs if it is on there (it may take a few uses for it to show up)
- You can create a custom hotkey
- you can press <superkey> and type in one or two letters and you should see the app on the dash
- you can go to the indicator and click on "System Settings" on the bottom to open a Control Panel
- You can open the terminal and start the app that way
- You can keep apps open in the Desktops that you use most, Press <superkey> <w> to see all 4 desktops by default -- just press ctrl-alt-arrows to navigate

Also, a lot of features will be left out of this version until 11.10, stability over features sounds good to me.

The only thing I miss is the indicators, the rest is a piece of cake.

Good luck!!!

---

### Post by seeker5528 on 2011-03-14
> **cariboo907 said:**
> Using gnome-control-center->Main Menu isn't going to do a lot of good, as Unity uses zeitgiest to display the most used applications/files in the Applications and Places menus.

Personally I would think it would be more of a usability nightmare if the old style menus were mixed in with the Unity menus.

Looks like more or less the same categories as the gnome-main-menu to me..... [Screenshot](http://home.comcast.net/~seeker5528/Screenshot-Categories.png).

I don´t see why using Zeitgeist should mean XDG menus can´t be used to populate the entries so your custom stuff gets recognized and alacarte used to create those custom entries, and on a seperate related note why your custom menu entries can´t be done (being XDG menus and all) in a way that gets recognized equally on all desktops so you don´t have to create custom entries in each environment.

Or on another seperate note why the stuff for the dash isn´t looking (can´t look?) at ´~/.local/share/applications/mimeapps.list´ to see that ´x-scheme-handler/mailto=claws-mail.desktop;´, hmmm, claws-mail should be the application opened when clicking on ´check email´.

Later, Seeker

---

### Post by VeeDubb on 2011-03-15
> **seeker5528 said:**
> Hmmm, [Unity](http://home.comcast.net/~seeker5528/Screenshot-Unity-vs-Menu1.png) Vs [traditional menu](http://home.comcast.net/~seeker5528/Screenshot-Unity-vs-Menu2.png).

Not really seeing how one is more of a nightmare than the other and Unity has those nice 'search' and 'Find available apps' options.

The difference is obvious.  

One sorts them into more than 2 or 3 categories, where the categories are logically named while also allowing you to create additional categories and move items around within the menu.

The other is completely locked down and requires the user to search through an enormous list of all installed applications or remember enough of the application name to make the search function usable.

I don't care if we get the old menus or not.  What I do care about is the ability to rearrange the menus, create new pages of applications, and arrange my applications in a way that is functional and efficient for me.  Even my cell phone can do that.  My cell phone can do that.  The idea that a full fledged desktop opperating system can't do that without major recoding is simply absurd.

If unity provided that one function, I would be thrilled.  Beyond normal/expected issues with running any alpha software, this is my only complaint with unity, but it's a serious enough issue that I probably will never use Unity (or gnome shell) as my main desktop until one of them adds this functionality.

---

### Post by Gorlist on 2011-03-15
Been using 11.04 for about a week now on my work pc - so far I really like Unity but I have been finding the top taskbar pretty annoying. I think having it change from the window name to "toolbar options" is a bit of gimmick, and seems useless if you don't have the window full size. The other downside is you tend to accidentally go over the main menu button causing unity to pop out. I understand the reason, saving on screen space but not if it makings the user experience more tiring.

I think its progress, looking forward to the updates.

---

### Post by KegHead on 2011-03-15
Hi!

Still working w/Unity.

Jury is still out.

KegHead

---

### Post by beew on 2011-03-15
> **Gorlist said:**
> Been using 11.04 for about a week now on my work pc - so far I really like Unity but I have been finding the top taskbar pretty annoying. I think having it change from the window name to "toolbar options" is a bit of gimmick, and seems useless if you don't have the window full size. The other downside is you tend to accidentally go over the main menu button causing unity to pop out. I understand the reason, saving on screen space but not if it makings the user experience more tiring.

I think its progress, looking forward to the updates.

After making the icon size smaller, making the top panel transparent and enabling the cube it doesn't look as bad as i felt at first (have yet to install emerald, but will do soon)

I still have a few issues. 1) The global menu. I hate it  2) the top panel is a waste of space, with gnome2 you can put applets there but in Unity it is useless and I think this is because of the stupid global menu, once you get rid of it the top panel would be quite useless except for the indicator applets 3) the biggest show stopper is the absence of a usable application menu. The dash is awkward and inflexible 4) I would like to have an option to move the Unity bar and arrange the icons on it (or remove it and use a better dock).

These are the main issues.

Also, a bit secondary it would be nice if the top panel and the Unity bar move along with the desktop during rotation instead of being static. I would also like to have a real desktop switcher on the Unity bar. In general I would like the Unity bar to be as flexible and feature rich as AWN or the Cairo Dock, at this point it is too basic.

But all in all, it is a better design than Gnome Shell and a lot better than the default look of gnome2 (which is good only because it allows almost any customization you want)

---

### Post by JRV on 2011-03-15
> **kerry_s said:**
> how come you didn't use zenity ?

Because I didn't know about it until you pointed out to me in this thread.

Thank you for suggesting it.  I read the man page, very useful.

---

### Post by ranch hand on 2011-03-15
> **VeeDubb said:**
> The difference is obvious.  

One sorts them into more than 2 or 3 categories, where the categories are logically named while also allowing you to create additional categories and move items around within the menu.

The other is completely locked down and requires the user to search through an enormous list of all installed applications or remember enough of the application name to make the search function usable.

I don't care if we get the old menus or not.  What I do care about is the ability to rearrange the menus, create new pages of applications, and arrange my applications in a way that is functional and efficient for me.  Even my cell phone can do that.  My cell phone can do that.  The idea that a full fledged desktop opperating system can't do that without major recoding is simply absurd.

If unity provided that one function, I would be thrilled.  Beyond normal/expected issues with running any alpha software, this is my only complaint with unity, but it's a serious enough issue that I probably will never use Unity (or gnome shell) as my main desktop until one of them adds this functionality.
I have no idea why that is missing in them both but it is.  Rather silly.

If all you do with your box is giggles and gossip ("social sites" and porn) the current setup is probably fine.

I do more with my box and prefer something that works as opposed to what I am supposed to like by some jumped up "expert" doing research to prove a point.

The tobacco industry did a lot of smoking is good for you research.  Didn't make them right.  Only idiots smoke.  Yes I smoke so I should know.

It appears that the assumption is that only idiots use computers too.

With a little literacy you can actually read a menu faster than wading through hundreds of icons.

---

### Post by seeker5528 on 2011-03-16
> **VeeDubb said:**
> The difference is obvious.

Different doesn´t necessarily make it a nightmare.  

> One sorts them into more than 2 or 3 categories, where the categories are logically named while also allowing you to create additional categories and move items around within the menu.

They both have mostly, if not exactly, the same [categories](http://home.comcast.net/~seeker5528/Screenshot-Categories.png) and my [first screenshot](http://home.comcast.net/~seeker5528/Screenshot-Unity-vs-Menu1.png) was showing a single category, a category I chose because it is a category that has more items than will fit onscreen in the Gnome menu and the Unity dash, it looks like they all did actually fit onscreen in the dash after clicking to view the dash full screen, but in both cases you can scroll to see the stuff that doesn´t fit onscreen so not that big of a deal.

> I don't care if we get the old menus or not. What I do care about is the ability to rearrange the menus, create new pages of applications, and arrange my applications in a way that is functional and efficient for me.

I see that as a valid complaint, I have mixed feelings about the dash not picking up on custom categories/launchers, but that is orthogonal to whether it is a nightmare to use or not.

Personally I don´t mess with the application menu that much so I´m content to run the application in question, then pin it do the dock.

For me the bigger question is what happens if you download something from a third party site, that has an installation process that includes adding an item into the menu using standard mechanisms that should theoretically make it show up in any desktop that uses XDG menus, *and* you are doing this in a user specific way in your home directory, will that application show on the launcher?

It looks like the dash *is* using XDG menus (/etc/xdg/menus/unity-place-applications.menu), but for whatever reason (oversight, compatibility, being clobbered by the over rides, just not there yet?), it´s not recognizing the customizations. 

Later, Seeker

---

### Post by mc4man on 2011-03-16
> feelings about the dash not picking up on custom categories/launchers
See no issue with 'custom launchers' (.desktops) showing up in dash. They just have to be in any of the 3 commonly avail. applications directories

---

### Post by seeker5528 on 2011-03-16
> **mc4man said:**
> See no issue with 'custom launchers' (.desktops) showing up in dash. They just have to be in any of the 3 commonly avail. applications directories

I´ll have to play around with that some more. Maybe also compare the results of using the command line utility.

[http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html](http://portland.freedesktop.org/xdg-utils-1.0/xdg-desktop-menu.html)

I don´t see any reason the alacarte created .directory file should be ignored it seems pretty standard, unless these just are not checked for at all by unity-place-applications. 

I could see it possibly being an issue that the alacarte made .desktop files don´t include a category line.

In the mean time I created a bug report..... 

[https://bugs.launchpad.net/ubuntu/+source/unity-place-applications/+bug/736517](https://bugs.launchpad.net/ubuntu/+source/unity-place-applications/+bug/736517)

EDIT: Have to investigate more to see if I can figure out what this ¨When menu entries are explicitly assigned to a new submenu it is not necassery to list any categories.¨ is about.

Later, Seeker

---

### Post by mc4man on 2011-03-16
> I could see it possibly being an issue that the alacarte made .desktop files don´t include a category line
I think that's the main reason why they're not seen in dash.
Haven't  really used alacarte-made.desktops here in the past, actually never used the menu that much (find the r. click can do quite alot.

 I tend to create the several  non userapp.desktops I need from scratch rather than use alacarte.

Anyway,  - using alacarte a desktop would not show in dash until a proper category line was edited in, then it shows
(even if the alacarte-made.desktop was added to the launcher, nothing in dash till a category line

---

### Post by JRV on 2011-03-17
What is dash?

---

### Post by mc4man on 2011-03-17
main menu created .desktops (alacarte-made) should now be shown in dash with new unity-place-applications - 0.2.40-0ubuntu1 upgrade.

Dash is referring generally to the big ubuntu button in unity panel and or the applications and files places screens

Edit: as an aside - an interesting change inc. was - 
Alt+F2 - type in about:config and it will run ccsm on the unityshell plugin. Kind of an obscure way to get to unityshell settings

---

### Post by kerry_s on 2011-03-17
hey did you guys/gals notice the new alt+f2 or the smart search bar for applications?
pretty interesting.

---

### Post by mc4man on 2011-03-17
The Alt+F2 is going to be very useful - wonder if there is a way to remove a historical entry if desired.

There is a new compiz and unity upgrades now - well worth reading the changelog  for changes, bug fixes ect.

---

### Post by JRV on 2011-03-17
I have installed all available updates as of 22:00 GMT 3/17/11.

When I press the Ubuntu button in the upper left corner I get a darkened area with eight icons, the top four are grayed out.  The bottom four show "Browse the Web", "View Photos", "Check Mail" and "Listen to Music".  They all work except "Listen to Music", it opens Firefox.

At the top there is a box marked "Search". I can type something in this box, but when I hit Enter nothing happens.

Alt-f2 doesn't seem to do anything.

Is there something wrong with my installation?

When I try to create a menu in alacarte it creates the alacarte-made.desktop files in /home/USER/.local/share/applications, but where is the menu?

I tried to add a category entry to a .desktop file with gedit by adding a line that said "Category=Whatever" and it didn't seem to make a difference.

---

### Post by mc4man on 2011-03-17
> When I press the Ubuntu button in the upper left corner I get a darkened area with eight icons, the top four are grayed out. 
Do you have the unity-place-applications and unity-place-files packages installed?
(currently 0.2.40-0ubuntu1 and 0.5.44-0ubuntu1 respectively 

The latest unity (3.6.6 ) seems to have some breakage in the applications and files .places, though generally they should work as far as searches and clicking on icons

---

### Post by JRV on 2011-03-17
> **mc4man said:**
> Do you have the unity-place-applications and unity-place-files packages installed?


Yes, the latest versions.

---

### Post by mc4man on 2011-03-17
> Yes, the latest versions.
Possibly i misunderstood you - usually when someone says 'greyed out' they mean it isn't usable
The default opening of the 'dash' (bfb), is the shortcuts - the 1st 3 to applications, the 4th to files & folders. They should work.( the icons are 'grey'

The search from dash works fine here, but not always, sometimes I can't type in, if so then a close and re-open fixes.

The dropdown category selection in applications and files &folders seems broken here w/ 3.6.6

Alt+F2 should open a 'Run a command' -   (previously was 'Search commands')
Typing something in should the expand the window (lens), to 'Results' and 'History', if any.

The latest applications.places doesn't require a category line in a custom .desktop to show, though sometimes a restart, (logout/in) is required before it's found

If you can't get the above then your install has some issues - I do a fresh install once or twice weekly.

---

### Post by JRV on 2011-03-17
The grayed out icons were colored and all opened /usr/share/applications until an upgrade awhile back.  Now they are gray and do nothing.

Nothing else works as you describe.

I think it's time for a re-install.

---

### Post by mc4man on 2011-03-17
> **JRV said:**
> The grayed out icons were colored and all opened /usr/share/applications until an upgrade awhile back.  Now they are gray and do nothing.

Nothing else works as you describe.

I think it's time for a re-install.
from changelog 

- Launcher - Replace Dash lens Launcher icons with updated versions
      (LP: #676613)

I think natty has and continues to be best served fresh.

---

### Post by douham on 2011-03-17
My latest update has bought Unity (3.66) breakage too. If I launch the dash ¨play music" will launch firefox. Also launching  the applications dash, then all aplications-click on a category eg; system, education etc launches the whatever icon is underneath.
This system was installed at alpha2.

I might download the latest nightly.

---

### Post by kerry_s on 2011-03-17
> **JRV said:**
> The grayed out icons were colored and all opened /usr/share/applications until an upgrade awhile back.  Now they are gray and do nothing.

Nothing else works as you describe.

I think it's time for a re-install.

i agree, fresh install. i think old settings are getting in the way. i had 32bit installed, which had app crashes often. i did a fresh install & used the opportunity to switch to 64bit.
i haven't had 1 single crash of any thing. it's perfect.

---

### Post by mc4man on 2011-03-17
> **douham said:**
> My latest update has bought Unity (3.66) breakage too.  Also launching  the applications dash, then all aplications-click on a category eg; system, education etc launches the whatever icon is underneath.
This system was installed at alpha2.

I might download the latest nightly.

I believe that is broken with the latest unity - it dropdowns here but nothing can be selected (no entries highlighted, ect.
It's launching what's underneath because in essence it;s not 'there'

filed bug though may end up a dupe
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/737203)

---

### Post by JRV on 2011-03-18
Kerry,

Well I re-installed from the 3/18/11 daily build 64 bit alternate disk and the dash works like you said.  Now back to it, I have a lot of customizing and fine tuning to do.

> **mc4man said:**
> 
I think natty has and continues to be best served fresh.

You got that right.

---

### Post by JRV on 2011-03-22
> **mc4man said:**
> See no issue with 'custom launchers' (.desktops) showing up in dash. They just have to be in any of the 3 commonly avail. applications directories

I know about /usr/share/applications and /home/USER/.local/share/applications.
What is the third?


kerry_s - I rewrote my menu using zenity, I like it.  Thanks for the tip.

---

### Post by mc4man on 2011-03-22
> What is the third?
/usr/local/share/applications
Typically for sources one builds themselves

---

### Post by JRV on 2011-03-22
> **mc4man said:**
> /usr/local/share/applications
Typically for sources one builds themselves

Thank you for the quick reply.

---

### Post by rabideau on 2011-03-28
> **beew said:**
> I am not sure what OP tries to do. Does it just add a bunch of desktop launchers instead of a menu with this approach?

I find the dash super user unfriendly and super impractical. Aside from the icons layout how do you open a program when you already have one running full screen? (it is in full screen because another "feature", the global menu requires it) You have to open the dash which take over the whole screen. They could have easily put a menu button on the Unity dock but I doubt that they would do that, since that undermines the "super smooth experience" and consistency (consistently awkward to use) of Unity.
I have resorted to using Synapse to quickly open programs.... not Gnome-Do (I think that is no longer supported...).

I agree that the Unity menu is bleak although it is better than it once was... which is not to be not to be confused with good.

---

### Post by rburkartjo on 2011-03-28
rab i dont know if do is still supported by it is still working great on my end. though could change with the beta release this week

---

