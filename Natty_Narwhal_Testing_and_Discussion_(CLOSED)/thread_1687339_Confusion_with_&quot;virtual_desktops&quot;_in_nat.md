---
title: "Confusion with &quot;virtual desktops&quot; in natty KDE"
date: 2011-02-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by afoglia on 2011-02-13
I just upgraded to natty today and KDE's virtual desktop features are... well, a little nonsensical.

Under maverick, I had four desktops, that I could switch to with Ctrl-Alt-Left/Right.  They were laid out in the pager in one row.  When I set a window to be "On All Desktops" though the window decorations, it was on all four of those dekstops.

Now, under natty, I have those same four desktops, but Ctrl-Alt-Left/Right sends me to some parallel version of them, laid out in a grid.  My normal backround is only on the first desktop in each of these parallel versions.  The setting panel "Workspace Behavior" > "Virtual Desktops" lets me set the number of desktops in the row in the panel, but the shortcuts I set under the "Switching" tab control have I move between these parallel multiple desktops.

My guess is that this is related to the Desktop/Workspace paradigm that Gnome uses, but it seems incomplete and inconsistently implemented.

Is there some suggested way to make these work coherently?

---

### Post by s.fox on 2011-02-13
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by seeker5528 on 2011-02-14
Did you create any activities?

I have the default 'Desktop' activity and two additional activities that I created 'Unnamed' and 'WTF'.

For some reason on Desktop 3 I get a little box toward the top of the right side labeled 'WTF', but I don't see this on any other desktop and I don't see it in the 'Unnamed' activity.

I can't see that this box actually does anything, as a test I set different wallpaper for that desktop in the 'Desktop' and 'WTF' activities and clicking the box and when changing between the activities the wallpaper changes, but clicking/right clicking that box doesn't seem to change activities or provide any other function.

Hmmm. I just dragged the little box away from the edge of the screen and it went away, have no clue what was going on there.

Other than that everything seems to be as expected on my system. But....

Apparently somewhere along the way it seems that Jajuk hijacked the 'Ctrl'+'Alt'+'left/right arrow' keyboard shortcuts, and they stayed that way in spite of the fact that Jajuk was purged some time ago before the Natty development cycle started, so I had to set the keyboard shortcuts up again. I get the same thing whether I use the keyboard shortcuts or click on a desktop in the pager.

Later, Seeker

---

### Post by afoglia on 2011-02-17
(Sorry, I didn't have notifications on.)

> **seeker5528 said:**
> Did you create any activities?


I had no idea what "activities" were.  But, no I don't.

Under System Settings > Virtual Desktops > Desktops, I have:

Number of desktops: 4
Different widgets unchecked
Desktop names
Desktop 1: Workspace 1
Desktop 2-4: (blank)

And when I switch (something, I don't know what) with the pager in the panel, the new screen has no plasmoids (other than the panel, if that's a plasmoid).

This is a relatively new computer, so I hadn't even installed too much under maverick (and practically never ran lucid before upgrading).  I haven't transfered my music yet.  I did have to play around with the window manager and the decorations (running Plastik and not Oxygen), but that's all.

---

### Post by vmonkey on 2011-02-17
> **afoglia said:**
> (Sorry, I didn't have notifications on.)

I had no idea what "activities" were.  But, no I don't.



You can find activities if you rightclick on your desktop and then choose Activities (there are also shortcuts - Alt+D, Alt+A).

---

### Post by afoglia on 2011-02-17
> **vmonkey said:**
> You can find activities if you rightclick on your desktop and then choose Activities (there are also shortcuts - Alt+D, Alt+A).

Well then, I only have one, and it's "unnamed".

That did give me the idea of right-clicking on the other desktops/workspaces/somethings in the row shown on the panel, and I got nothing.

I think the first thing to do is figure out how it is even possible to have two differing multiple-desktop paradigms in KDE.

---

### Post by seeker5528 on 2011-02-17
> **afoglia said:**
> Number of desktops: 4
Different widgets unchecked
Desktop names
Desktop 1: Workspace 1
Desktop 2-4: (blank)

Sounds like something may have gotten munched while migrating the settings from the older version to the newer version.

For me when the 'Different Widgets' box is unchecked I get the same widgets and wallpaper on all my desktops, if it's checked the wallpaper and widgets can be different for each desktop.

I don't know when this setting was added because I don't often go in and change that stuff, but it used to be switching between the desktop layout and folder layout that determined if you could have different wallpaper (and I'm assuming widgets too) on each desktop, so you might also try a different layout to see if you get the same behavior with a different layout and then if the behavior continues after switching to a different layout and switching back again.

Later, Seeker

---

### Post by afoglia on 2011-02-17
> **seeker5528 said:**
> I don't know when this setting was added because I don't often go in and change that stuff, but it used to be switching between the desktop layout and folder layout that determined if you could have different wallpaper (and I'm assuming widgets too) on each desktop, so you might also try a different layout to see if you get the same behavior with a different layout and then if the behavior continues after switching to a different layout and switching back again.

I'm not sure what setting you mean.

Anyway, I did more testing, and it's very weird.  I just played with "Number of desktops" option in "System Settings > Virtual Desktops" and got some weird results.

No matter the number, ctrl-alt-(arrow) moves me among a 2x2 grid of desktops, all with my widgets/plasmoids, and my blue KDE background.

When the number of desktops is greater than 1, the number matches the number of desktops visible in the panel in the kicker.  But switching via clicking on the panel, to any but the first, brings me to a desktop with a purplish background.  I assume this is the default Ubuntu background.  The kicker's still there, but no plasmoids.  If on a window title bar, I go to the icon/menu button and go to "To Desktop", the number of desktops agrees with the number in the panel.  Only for the current desktop, does the panel show shaded rectangles for the windows.

When the number of desktops is 1.  The panel widget in the kicker shows me 4 desktops, all of which have my normal blue background and plasmoids.  These are the same desktops that the ctrl-alt-(arrow) switches among.  Everything is in agreement, except for the fact I have no idea where the setting "4" is, and it disagrees with the "1" I've set it as.

Forcing a window to be on all desktops works as expected in the last case.  In all other cases, the "all desktops" turn out to be the desktops in the panel (purple background).  Also in the latter case, the title bar button does not change icon.

When I have time, I may try to regenerate my conf files (or make a new user and see how his configuration differs).  What conf files should I be focusing on?  But the bigger question is what code path am I accessing that causes two different multidesktop paradigms?  I don't understand how that could exist.

---

### Post by seeker5528 on 2011-02-18
> **afoglia said:**
> I'm not sure what setting you mean.

The setting to show different widgets for each desktop.

> No matter the number, ctrl-alt-(arrow) moves me among a 2x2 grid of desktops, all with my widgets/plasmoids, and my blue KDE background.

I can't reproduce that behavior. If I change the pager to 1 row I see one row when I use the arrow keys, if I change it to 2 I see 2 when I use the arrow keys. The number of desktops always matches what the pager displays, doesn't matter whether I go to systemsettings to change the number of desktops or use the pager options to do it. If the option to show different widgets for each desktop is checked I see different stuff on each desktop if not I don't, but the widgets on the panel are always the same on all desktops.

> When I have time, I may try to regenerate my conf files (or make a new user and see how his configuration differs).  What conf files should I be focusing on?  But the bigger question is what code path am I accessing that causes two different multidesktop paradigms?  I don't understand how that could exist.

The plasma config files all look like they are all '.kde/share/config/plasma*' 

The only reason I can think of for the stuff to be different when you use the pager versus using the arrow keys is if you are using some non-KDE stuff. Something other than kwin for the window manager and/or a different panel+pager.

As I think about it more, the window manager other than kwin seems like the most likely suspect to me. If that's the case looking in 'systesettings --> system administration --> startup and shutdown --> autostart' seems like a good place to start looking.

As it turns out I was using metacity as the window manager on the system I'm looking at at the moment and it was metacity that was showing me a row (or rows depending on how I set that in the pager) when using the cursor keys to switch to another desktop.

Yep, you might think having the window buttons on the left might be a clue, but apparently you would be wrong. :P

 Setting the window manager back to kwin, it doesn't show anything when I use the cursor keys to change desktops other than indicating which desktop I'm currently on in the pager.

This makes me even more suspicious that you have something other than kwin set as the window manager, one that doesn't manage virtual desktops the same way kwin and I think the majority of the window managers do.

Later, Seeker

---

### Post by afoglia on 2011-02-20
> **seeker5528 said:**
> The only reason I can think of for the stuff to be different when you use the pager versus using the arrow keys is if you are using some non-KDE stuff. Something other than kwin for the window manager and/or a different panel+pager.

As I think about it more, the window manager other than kwin seems like the most likely suspect to me. If that's the case looking in 'systesettings --> system administration --> startup and shutdown --> autostart' seems like a good place to start looking.

[...]

This makes me even more suspicious that you have something other than kwin set as the window manager, one that doesn't manage virtual desktops the same way kwin and I think the majority of the window managers do.

I think you're right.  There is a compiz process running, and no kwin process running.  And compiz setting manager is configured for four desktops in a 2x2 formation.

I probably switched it because of some problem in maverick.  I just don't remember how, and I don't see any place to switch it.  The autostart settings you point out have no mention of window managers at all, nor does anywhere in "Startup and Shutdown".

Anyway, I'm switching back to maverick.  Natty is currently crap on my system (Envy 14).  Slow boot with a screen turned off, constant crashing when typing so as I had to boot into windows to write this response, a disappearance of virtual consoles, which makes debugging X problems impossible.  And now, for some reason I can't even get it to boot (despite not installing any new packages).

---

### Post by seeker5528 on 2011-02-21
Early KDE 4.x had an option somewhere in systemsettings to choose a window manager, but I think that's been gone for a few releases now.

If you had fusion-icon installed, I believe that has options for setting/unsetting compiz to be enabled at login.

Also if you have the session management set to save your session on logout and did the 'compiz --replace' thing in a terminal window, it would start with compiz (and anything else you had running when you last logged out of a KDE session). 

In that case you should be able to open a terminal window and type:

```
kwin --replace
```

Then log out and log in again or....

Go to 'systemsettings --> startup and shutdown --> session management --> on login', then choose the option to start with an empty session.

I've seen a few posts from people who have Envy machines, but since I don't have one, I don't follow that stuff very closely, but if you search the forum, you may find something that helps you out. 

Later, Seeker

---

### Post by afoglia on 2011-02-26
Well, I was too busy to downgrade last weekend, so I've been following the upgrades.  Something in the past week fixed the desktop issue.

I'd give you the current version number of the compiz package, but while doing something else, I switched to the discrete video card (ATI), and Ubuntu went to black, and won't reboot.  Ugh.

---

### Post by afoglia on 2011-02-28
> **afoglia said:**
> Well, I was too busy to downgrade last weekend, so I've been following the upgrades.  Something in the past week fixed the desktop issue.

My mistake.  The issue still exists.  I must have not tested it right, worried more about the booting trouble.

---

### Post by seeker5528 on 2011-03-02
If it is still using compiz, there is compiz-kde package that indicates it provides compatibility with KDE, don't know if it is really needed or not.

Could be a specific compiz plugin, might try disabling different desktop pluging in ccsm, assuming you have the compizconfig-settings-manager package installed. The compizconfig-backend-kconfig package may a difference too.

If you don't really care about compiz you could ditch it and just use the native KDE stuff.

Later, Seeker

---

### Post by afoglia on 2011-03-19
> **seeker5528 said:**
> If it is still using compiz, there is compiz-kde package that indicates it provides compatibility with KDE, don't know if it is really needed or not.

Could be a specific compiz plugin, might try disabling different desktop pluging in ccsm, assuming you have the compizconfig-settings-manager package installed. The compizconfig-backend-kconfig package may a difference too.

If you don't really care about compiz you could ditch it and just use the native KDE stuff.

I have all those packages installed.

I did find the where to change the window manager though.  It's in System Settings under Default Applications.

So the issue is definitely compiz/kde integration.  I'd think it was just the pager, except for the fact that the "pin window to all desktops" title bar button doesn't work properly either.

The only other interesting thing is there is are two plugins in ccsm, one of which is "KDE Compatibility".  It's currently deactivated, but when I activate, compiz appears to die.  (All the window decorations go away, clicking on windows don't bring them to the top, alt-tab does nothing, etc.)  Even after I restarted, the decorations were gone.  (I was able to regain control because the kicker panel was working again, and I could get into systemsettings to change back to kwin, then run ccsm and shut off the "KDE compatibility" plugin.)

Anyway, I should get back to teaching myself how to build and package a custom kernel to try to debug my kernel issues first.

---

