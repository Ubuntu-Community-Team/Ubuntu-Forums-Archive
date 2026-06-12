---
title: "Master volume not doing anything, youtube videos have no sound"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by blacklantern on 2006-08-16
To anyone who can help:

I've recently done a fresh install of Dapper Drake. It was kind of troublesome, because the CD was bugged, and I had to dig up and old breezy cd and upgrade from it. After all was said and done, I once again found myself very pleased with my new shiny operating system - until I discovered a problem, the only one that seems to exist.

My master volume doesn't seem to be doing anything; in order to change volume in an application, I have to use the volume control of the application itself. This is fine for things like totem, but impossible for things like gaim and cnn videos with the mplayer plugin, as I have no volume option within those applications.

Furthermore, flash videos such as those found on youtube.com and newgrounds.com aren't working at all. Does anyone have a suggestion on what my options might be at this point?

---

### Post by louis_nichols on 2006-08-16
Well... what I can suggest is that you search for the output within every application and make sure it's alsa, instead of oss. That is, on the application side. But you also have an option to choose between alsa and oss within the sound settings (at least, I do), somewhere in sound prefs, so that should be alsa too.

As for the flash thing, there are several solutions on the forum, but the one I use is to just start firefox with the command **aoss firefox**. You ust have installed the package alsa-oss for this.

---

### Post by blacklantern on 2006-08-16
How might I go about checking the output of those applications? Also, I see nothing mentioning alsa in the sound preferences. Finally, though I do have alsa-oss installed, starting firefox with the command aoss firefox does not enable me to get sound in flash videos.

---

### Post by louis_nichols on 2006-08-16
Well, about the flash videos, I suggest you search the forums for another solution. Not having sound in flash is a common problem and several solutions have been posted throughout. At least one of them should work.

As for the rest, setting the output of an application is very much application-dependant and can be tricky at times. For example, totem doesn't have such an option in prefs, but can be set in a different way, depending again on whether you have totem-gstreamer or totem-xine. For Totem-Gstreamer, the option is actually hidden within the menu System>Preferences. But you have to enable it using Alacarte menu editor, where you will see it in the list, but you have to check the option. For totem-xine, you set this in a config file, placed in the folder ~/.totem  . I don-t remember the exact name and I'm not at my box right now, but it's something like xine-config or xine.config.

XMMS has the option to set the output in th eright-click menu>preferences. For mozilla-mplayer, I think you should set it in the mplayer app first. Or maybe you also have to edit a config file somewhere. My point is that I think you should treat each app's situation separately.

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

