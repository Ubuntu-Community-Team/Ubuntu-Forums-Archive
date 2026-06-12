---
title: "Gnome sound events default only includes login and logout, why not other sounds?"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by geopgeop on 2007-08-05
I've been trying to figure out why only the login and logout entries have associated sounds (login.wav and logout.wav) in the System Sounds section of the Sounds tab in Sound Preferences (**System->Preferences->Sound**), and the other entries are blank, by default.  Why aren't the other sound events associated with their respective sounds (Select check box = toggled.wav; Choose menu item = activate.wav; etc.)?  I'm running Ubuntu Feisty, by the way.

All the other threads I see related to these sounds are to ask how to disable them; I'm asking to enable more sounds.

Some searching on Google led me that gnome-2.soundlist and gtk-events-2.soundlist are the files containing those settings.  If those files are not going to be changed in Feisty, Gutsy, or beyond, couldn't there at least be a table of events to their respective sounds?  I'll try listing them right here, but please help me correct any wrong associations.

(All files are in **/usr/share/sounds**)

**System Sounds**

(These are under gtk-events-2.soundlist)

[LIST]
[*]Select check box:	**toggled.wav**
[*]Choose menu item:	**activate.wav** (Beep)
[*]Click on command button:	**clicked.wav** (Clink [sic?])
[/LIST]


(These are under gnome-2.soundlist)

[LIST]
[*]Miscellaneous message:	**generic.wav**
[*]Question dialog:	**question.wav**
[*]Error message:	**error.wav** (Siren)
[*]Warning message:	**warning.wav**
[*]Informational message:	**info.wav** (Boing)
[*]Logout:	**logout.wav**, sometimes symlinked to **shutdown1.wav** (Logout)
[*]Login:	**login.wav**, sometimes symlinked to **startup3.wav** (Login)
[/LIST]


I also wonder why there isn't a table like this anywhere else; the closest I can think of is at [http://fedoraproject.org/wiki/Artwork/F8Themes/GnomeSounds]("http://fedoraproject.org/wiki/Artwork/F8Themes/GnomeSounds"), though those are custom sounds.

Some of the information I got for this was compiled from pages like [http://pastebin.ca/416065]("http://pastebin.ca/416065"), [http://www.vergenet.net/~conrad/sounds/gnome-audio/]("http://www.vergenet.net/~conrad/sounds/gnome-audio/") (actually, this is a table too, but again custom sounds...), and others, if I can think of any.

I'm not asking this to be in the default soundlist files for Ubuntu (many are annoyed just by the login and logout sounds themselves, no matter how good they sound), but I'd like this information readily available, or maybe as an optional package, call it gnome-audio-fulldefaultsettings or something like that to replace the soundfiles, but then that would conflict with libgnome, I think.

---

### Post by happy-and-lost on 2007-08-05
I like the idea of such packages. Maybe a mod could move this into the Gutsy Ideas Pool for further discussion?

---

