---
title: "I do not want Rhythmbox in my sound indicator menu"
date: 2010-10-21
forum: Multimedia Software
---

### Post by k1id on 2010-10-21
Ever since the update to Maverick, Rhythmbox now shows up in the sound indicator menu and this has doesn't close if music is playing. I don't really use Rhythmbox to play music so I leave it on mute, but I do use it to manage my iPod and it not closing has caused me nothing but problems. I've looked and looked and cannot find a way to turn it off. Is there any solution to this? Thanks.

---

### Post by nLinked on 2010-10-22
Bump. Also want to remove it from Sound Indicator menu.

Most importantly, I want it to close when I click close button on Rhythmbox, instead of continuing to play in the background.

---

### Post by wojox on 2010-10-22
Open the file menu and select quit. That will shut it down completely.

As far as removing it from the menu, open main menu and uncheck it.

---

### Post by nLinked on 2010-10-22
> **wojox said:**
> Open the file menu and select quit. That will shut it down completely.

As far as removing it from the menu, open main menu and uncheck it.

Thanks, File Quit works as I need!

As for menu, I mean from the Sound icon menu.

---

### Post by mc4man on 2010-10-22
> As for menu, I mean from the Sound icon menu. 
If you wish to remove from the sound preferences applet you can but note that it doesn't change it's behaviour whatsoever. so don't really see the point.
.desktops listed in ~/.cache/indicators/sound/familiar-players-db.keyfile will be listed in sound preferences
( I added a few things to the list - while they can't be controlled they can be opened

Edit: - only good to add - rhythmbox will show up in list after running - didn't see any point to removing anyway

(you also can use the old notification icon for rhythmbox if so desired (plugins  - status icon - configure to owns main window

---

### Post by k1id on 2010-10-22
What we want is to now if we can completely dissociate Rhythmbox from the sound indicator. I want Rhythmbox to quit completely when when I push the close button because I won't remember. I think there's supposed to be an option for it like shown in the mock up here [https://wiki.ubuntu.com/SoundMenu#Rhythmbox](https://wiki.ubuntu.com/SoundMenu#Rhythmbox) but it's not in the preferences menu.

---

### Post by steve161 on 2010-10-22
> I want Rhythmbox to quit completely when when I push the close button because I won't remember.


Go to edit-plugins and uncheck status icon.

---

### Post by mc4man on 2010-10-22
> What we want is to now if we can completely dissociate Rhythmbox from the sound indicator.

While it doesn't appear rhythmbox is completly intergrated into the sound pref's menu at some point it will and that will be that.

Personally have no issue here, if I wish to close w/ the X button then simply stop playback first.

That being said you can still, at this point, have what you wish.
2 apparent ways
The current behavior is the result of the 22_hide_on_quit.patch - > Description: the close and ctrl<w> buttons are now mapped to hide the main
             window when a music is playing (we can bring it back using the
             soundmenu). If no music is playing or if Music -> Quit is
             triggered rhythmbox is closed.
Author: Didier Roche
Bug-Ubuntu: [https://bugs.launchpad.net/bugs/526552](https://bugs.launchpad.net/bugs/526552) 

So if you re-build the current source and exclude that patch you'll get exactly what you wish (as long as the status icon is disabled in plugins

The other way would be to revert to the rhythmbox version just prior to the patch being applied - rhythmbox 0.13.1-0ubuntu2
You can find the package set in launchpad.

In either case i'd first completely remove rhythmbox and any plugin's in synaptic, restart, and then do one of the above

(tested the re-build of current source, works as expected

---

### Post by k1id on 2010-10-22
Thanks, I'll try one of those. Or i might just deal with it and be careful about closing it, but it'll still really bug me.

---

### Post by nLinked on 2010-10-23
Still bugs me too. I can't get used to File > Quit easily and it's just a longer process. I also want it to stop playing when I press the Close button. For now, have removed it and installed Banshee until this gets an option in future.

---

### Post by aidan.whitehouse on 2010-11-27
Post #7 gave you the answer you wanted, but I guess you missed it...

This will make Rhythmbox act as it did in previous versions...

---

### Post by nLinked on 2010-11-28
> **aidan.whitehouse said:**
> Post #7 gave you the answer you wanted, but I guess you missed it...

This will make Rhythmbox act as it did in previous versions...

That removes the icon, but Rhythmbox still appears if you click on the speaker icon, it's integrated in there. That's where I want it removed from.

I'm just using Audacious now, very fast and light-weight. Might consider Rhythmbox in future if they let me remove the speaker drop down integration. I'd like to have that choice.

---

### Post by Jetro on 2011-01-21
*I'd* like Rhytmbox to launch without having to press the button *twice*. Just saying.

---

### Post by pshmell on 2011-03-02
B-b-b-bump. I would also like to remove the "Rhythmbox" button from the *Sound Menu* applet. I use Banshee, and it's just annoying to see Rhythmbox there if I don't use it.

The sound menu ought to look and see what the default multimedia library is for the current user, and only display that application name in the *Sound Menu*. 

I've looked through all the gconf settings. There is one schema for 'indicator-sound', but the only option is for muting. There ought to be a setting here for choosing which multimedia player (if any) to display.

Also, to the people saying "Why do you want it removed?"
Because it's my system, and I want it to look and feel how I want! That's why I run Linux! :)

---

### Post by huggs on 2011-09-28
To completely remove Rhythmbox from the dropdown Sound menu:
Look in ~/.local/share/applications/ for a Rhythmbox desktop file.
There should be two of them, with slightly different names.
Delete both. No more Rhytmbox in sound menu.
Even uninstalling Rhythmbox doesn't remove these desktop files, so it remains in the menu until they're manually deleted. 
Remember to reboot or restart gnome to see the change :-)

---

