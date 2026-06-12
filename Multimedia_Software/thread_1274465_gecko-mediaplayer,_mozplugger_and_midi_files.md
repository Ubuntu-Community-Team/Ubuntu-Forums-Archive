---
title: "gecko-mediaplayer, mozplugger and midi files"
date: 2009-09-24
forum: Multimedia Software
---

### Post by bw44 on 2009-09-24
I have the gecko-mediaplayer plugin installed and about : plugins in Fiorefox says that it will handle midi files, but it doesn't.  When I click on an embedded midi file it launches Gnome Mplayer but then stops.

I installed timidity and the mozplugger plugin, and now mozplugger also claims to handle embedded midi files, so there is evidently a conflict, and gecko-mediaplayer continues to win.

Can anyone suggest how to re-configure gecko-mediaplayer to remove midi and allow (hopefully) mozplugger to successfully open the embedded midi files?

Thanks for any suggestions.

---

### Post by kdekorte on 2009-09-25
Open gnome-mplayer, select Edit->Preferences choose the plugin tab and uncheck midi support. This should revert back to mozplugger handling MIDI files.

---

### Post by bw44 on 2009-09-25
> **kdekorte said:**
> Open gnome-mplayer, select Edit->Preferences choose the plugin tab and uncheck midi support. This should revert back to mozplugger handling MIDI files.

Thanks very much for your help.  Since I posted my question I visited your support site and realized that I am using an older version of gecko-mediaplayer and gnome-mplayer.  When I tried what you suggested I got the attached screen.  I also noticed on your forum that someone had described this problem earlier in the year and you had fixed it.

My problem now is that I'm running Ubuntu 8.04 and I don't know how to get a new versions of gecko-mediaplayer/gnome-mplayer and install them. I saw that I can download lots more recent versions from your site, but if it doesn't come as something I can install with synaptic package manager, I'm lost. (I'm not a sophisticated user who knows how to compile and install programs.  I downloaded the most recent one, and from your INSTALL file tried to configure the setup.  But it complained some library (slib2?) was not available.  If the configuration had run, I doubt I could have gotten through the rest of the installation anyway.).

Anyway, I really appreciate your trying to help and I guess I'll just get used to downloading the midi files and playing them with timidity as a workaround.

I've used gecko-media player 0.6.0 since after I installed Ubuntu 8.04 and it's really worked well.  Never had any problems with it.  

Cheers,

bw44

---

