---
title: "Compiz won't run at all now"
date: 2010-11-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-27
I ran some updates late last night some of which were for compiz. I rebooted after and the cairo dock was displayed correctly and it included a new icon design for one of the applets. 
During the course of the night I had occasion to reboot and now compiz won't run at all. It doesn't start on reboot and if I run compiz --replace the desktop flashes and windows top bar disappears. Desktop effects cannot be enabled either even though I have the up to date nvidia driver. The desktop became totally unresponsive one time and I needed to REISUB to reboot.
Compiz has not run since that first time.
Anybody else having similar problems?
Thanks.

---

### Post by plun on 2010-11-27
Yep....

Start ccsm

Go to preferences, change backend to gconf

```
compiz -- replace
```

Done....  the Unity plugin is probably still broken.

---

### Post by autocrosser on 2010-11-27
Yep--there was a "update" last evening to enable the "Unity plugin" so Unity would start by default...I just let it with my Unity-testing install & went to ccsm before I rebooted in my Gnome-Shell testing Natty install.....Sure enough, the plugin was checked--so it would have b0rked my GS install real good.....

If you can't get to ccsm--just post & we'll work you thru it..............

---

### Post by plun on 2010-11-27
> **autocrosser said:**
> Yep--there was a "update" last evening to enable the "Unity plugin" so Unity would start by default...I just let it with my Unity-testing install & went to ccsm before I rebooted in my Gnome-Shell testing Natty install.....Sure enough, the plugin was checked--so it would have b0rked my GS install real good.....

Well... it just broke for me....switching from ini to gconf backend solved the Compiz challenge for me...

Unity is discussed in another thread...;)

---

### Post by autocrosser on 2010-11-27
I'm all over it :D:D

Running a fresh alternate-install .iso--just loaded it last night & Unity is in by default (good for me--I was reloading my b0rked Unity install anyway)--that plugin was one of the first updates I got last night......

How's the build-branch going?  I'm in my Unity right now--very nice with 3.2--looks good....

Here's mine.......

---

### Post by Quackers on 2010-11-27
Thanks for the info plun but it only worked for about 5 seconds!
Cairo dock displayed as it should (with compiz running) and all was good except no wobbly windows. I enabled wobbly windows and all hell broke loose. The desktop flashed, all windows lost their borders and top bar. Compiz stopped running and cairo dock changed to the "non-compiz" shape.
So I rebooted.
No panel applets (with error messages about each) but cairo dock appeared in its compiz-running state. Then all panels and cairo dock disappeared completely.
REISUB reboot
Desktop comes back with compiz running but no top panel applets. I clicked on reload for all 5 of them but only the date applet appeared. No Wireless and no internet.
Rebooted again and it is now as above, except that I'm connected to the router via ethernet.
Any suggestions would be good.
Thanks :-)

---

### Post by plun on 2010-11-27
> **autocrosser said:**
> 
How's the build-branch going?  I'm in my Unity right now--very nice with 3.2--looks good....



Well, "nema problema"....;)

Just that I needs a menu for all apps.....equal stupid as GS for the monent...IMHO..;)

---

### Post by autocrosser on 2010-11-27
What you might try is create a new user & test if the same thing is happening there--My thought is that your /home is kind'a b0rked.....

I needed to do that with the reinstall I did last night--my prefs were all arf'd up & the easy fix was to just throw it all out & start over---helps that I have multiple installs--I just pull what I need over after the install is up & running.....

---

### Post by Quackers on 2010-11-27
I've created a new user and had to reboot to get to it and now I'm using a different looking desktop with no Applications/Places/Admin menu. Has it defaulted to Unity?
No wireless though, so doesn't look all that fixed at the moment.
Thanks for input :-)

---

### Post by autocrosser on 2010-11-27
If it looks kind'a like the picture I posted above--Yes you are now using Unity.....I customised my side bar & have Conky on the right side....

---

### Post by Quackers on 2010-11-27
Yes, it looks like that :-)
How do I get to everything?
The only thing I appear to be able to get to is Places.
Please excuse ny noobiness :-)

---

### Post by Quackers on 2010-11-27
Is clicking on the Ubuntu icon in the top left supposed to do anything? It's doing nothing here. Left click/right click - nothing! :-(

---

### Post by autocrosser on 2010-11-27
No function on the Ubuntu logo as of yet---I'm using a lower gnome-panel or avant-window-navigator to get the functionality right now--the menu in the upper left corner will be working "soon" (in other words---good question)

I install nautilus-open-terminal to get a term in the right-click desktop menu--then you can do a entry to get what you want---it may take a bit of mucking about to get what you want.....

---

### Post by Quackers on 2010-11-27
Ah right. Thanks for that.
No wireless is worrying though. I think maybe things are not fully fixed. No additional drivers are required for my wireless card so it should work straight away - if network manager is loading. I suspect it's not though.
I'll go back to the previous user for the moment, but I look forward to playing with unity :-)
Thanks again.

---

### Post by ronacc on 2010-11-27
wireless has been flaky for me on and off for a couple of weeks , I have found that if I rt click on the indicator and UNcheck enable wireless  and  then rt click and check enable again then rt click and check enable again ( you have rt click and check enable two times ) then wireless will start working , try that .

---

### Post by Quackers on 2010-11-27
Thanks ronacc but the applet never starts. It isn't in the top panel at all.
I've just used the "run application" applet (as alt + F2 doesn't work most of the time) to run nm-applet and it came back to the panel and connected wirelessly right away.
So it seems that when compiz runs nm-applet does not run and no wireless is available unless I start it with the run box.

---

### Post by lidex on 2010-11-27
Enabling some of the plugins in compiz definitely crashes me here. Compiz is apparently running but 'Appearances>Desktop Effects' shows 'None'. I want emerald back.

---

### Post by ronacc on 2010-11-27
I guess your NM problem is different than mine , BTW compiz runs ok for me and doesn't mess with my wireless ( once I get it to start ).

---

### Post by Quackers on 2010-11-27
I'm similar to lidex. I want emerald back :-)

---

### Post by cariboo on 2010-11-27
You don't have to run Unity, you can disable the plugin and just run the standard desktop, although affects still won't work. The system I'm using right now is what I call my baseline system, just he standard gnome 2.X desktop. I have 3 other systems running Unity, 64-bit, 32-bit and netbook and one system running gnome-shell from the ppa.

---

### Post by lidex on 2010-11-27
> **cariboo907 said:**
> You don't have to run Unity, you can disable the plugin and just run the standard desktop, although affects still won't work. The system I'm using right now is what I call my baseline system, just he standard gnome 2.X desktop. I have 3 other systems running Unity, 64-bit, 32-bit and netbook and one system running gnome-shell from the ppa.
I do have unity disabled and I do have effects but there are stability issues. A simple ctrl-alt-backspace gets me back up generally.

---

### Post by cariboo on 2010-11-28
If I try to enable affects, I get a lot of screen flashing, and then finally end up with no affects. I don't use them so I don't really care. This system I'm using now was upgraded from Maverick as soon as the Natty repositories were opened, so there probably is a lot of unneeded cruft. I'll probably redo the system after alpha 1 comes out.

---

### Post by Anduu on 2010-11-28
Changing to gconf backend got me back up and running as well.

Definitley some stability issues still.I randomly lose effects for no apparent reason and more often than not a compiz --replace will just hang forcing me to logout or ctrl+alt+backspace.

---

### Post by Quackers on 2010-11-28
> **cariboo907 said:**
> You don't have to run Unity, you can disable the plugin and just run the standard desktop, although affects still won't work. The system I'm using right now is what I call my baseline system, just he standard gnome 2.X desktop. I have 3 other systems running Unity, 64-bit, 32-bit and netbook and one system running gnome-shell from the ppa.

Don't have to run unity? I can't run unity in my normal admin account. It says unity isn't installed, but it is!

---

### Post by Quackers on 2010-11-28
Strangely enough, if I click on the unity plugin in ccsm unity runs fine :-)

---

### Post by lidex on 2010-11-28
> **Quackers said:**
> Strangely enough, if I click on the unity plugin in ccsm unity runs fine :-)

Same here. Can't do much with it though. Now at least I know to not
try to enable plugins with unity running.

---

### Post by Quackers on 2010-11-29
New compiz updates available.
No change in problems though :-)

---

### Post by lucazade on 2010-11-29
> **Quackers said:**
> New compiz updates available.
No change in problems though :-)

[https://launchpad.net/ubuntu/+source/compiz/](https://launchpad.net/ubuntu/+source/compiz/)

compiz (1:0.9.2.1+glibmainloop2-0ubuntu2) natty; urgency=low

  * debian/rules:
    - build with RelWithDebInfo cmake flag to get debug info and release
      optimisation
  * debian/patches/004_packagemode_is_release_debug_for_plugins.patch:
    - when compiz plugin built in "Package" mode, add optimization + debug
      symbols for stripping in dbgsym. Thanks RAOF for pointing at it
      (LP: #682574)
  * debian/patches/005_no_glib_plugin.patch:
    - remove glib plugin as conflicting with the glibmainloop branch
  * debian/source_compiz.py:
    - grab new gconf path in apport bug report
 -- Didier Roche <didrocks@ubuntu.com>   Mon, 29 Nov 2010 12:23:15 +0100

---

### Post by Quackers on 2010-11-29
I am pleased to announce that with all the latest updates and the new 2.6.37-7 kernel installed all previous ailments appear to have disappeared :-)

Panels and panel applets appear normally. Network icon appears normally and auto-connects. Compiz runs at startup. Desktop effects can be enabled. Alt + F2 works again. Unity plugin works faultlessly.

"compiz not responding" still appears when restarting.

Oh happy day :-) :-) :-)

---

### Post by autocrosser on 2010-11-29
YEP---Isn't it fun....I finished the "Weekend from Hell"..I had finished reinstalling my Unity-testing Saturday afternoon & had left the system run (I do BOINC--so that's not uncommon) & Sunday morning my wife comes in at 7am & tells me that "Your computer just shut off"----when she opened the drapes in the living room!!!!! Turns out that the power cord was pulled out of the power supply when the drapes opened......Needless to say, my Sunday was "interesting".......:icon_frown:](*,)

The sudden spike b0rked all 4 of my operating systems to one degree or another...Well--I was planning to reinstall my Lucid>Maverick>Natty updated install at Alpha 1 anyway........Just not one right after another........The one time that a UPS won't help you is when the cord comes out of the back of your system......You "might" guess that there are several zip ties in place now..........:D

---

### Post by Quackers on 2010-11-29
zip-ties? After that lot I might have been tempted to weld it :-)

---

### Post by autocrosser on 2010-11-29
The "next" step is a complete re-think of the cable management of my system---I've let it get away from me where everyone can't see it & that is where the problem came from.

---

