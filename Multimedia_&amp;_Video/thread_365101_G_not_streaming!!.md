---
title: "G not streaming!!"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by Alcopops on 2007-02-19
Hi all,

I am having some problems with gstreamer on edgy and could use some advice.

I want to use FLAC with gstreamer but cannot make it work. Neither rhythmbox, gnomebaker or serpentine will work with FLAC files and these apps all use gstreamer I believe.

However gxine and VLC (which I think are independent of gstreamer) both handle FLAC files perfectly.

This leads me to believe I have a problem with gstreamer and not with my FLAC files.

I have installed gstreamer 0.10 and most, if not all of the plugins (Via easyubuntu) I also installed FLAC from the repositories but to no avail.

A couple of other things:

I notice there is a plugin for gstreamer 0.8 called gstreamer0.8-flac (or similar) but could not find an equivalent one for gstreamer 0.10, should I be looking for this.

Do I need to configure gstreamer to use the plugins after downloading them, I didn't think I needed to because rhythm box will play mp3s ok presumably via gstreamer.

Lastly I tried to remove gstreamer 0.10 via synaptic and it seemed to want to take half the OS with it! It was telling me I would have to uninstall Open Office  and gnome desktop among others. Is this normal or does it indicate that I have a corrupt install of gstreamer.

I hope this is enough info for some kind soul to help me, burning flac files to audio cd is some thing that I do quite a lot; it would chafe me to have to boot into a proprietary OS like windows, to work with a free codec like FLAC!

If all else fails, does anyone know of an app that will create audio cds from flac files without requiring gstreamer. The ability to use cue files would be a big time saver also.

Thanks in advance 

Jaime

---

### Post by an.echte.trilingue on 2007-02-19
There are basically three media players for linux: mplayer, xine, and gstreamer.  Almost everything else you find simply acts as a user-friendly front end for these three players.

Gstreamer is the music player for Gnome; it is developed by the Gnome team and it is true that half the DE depends on it.  Gstreamer is what plays your startup music, media files embedded in Office Docs, etc.  It is pretty good at what it does for Gnome, but as a general purpose media player it is horrid.  DVDs are simply out of the question, for example.  FLAC support should be in gstreamer0.10-plugins-good; it you have installed that and it is not working I don't know what to say.

Despair not, however, because you can install other media players along side of gstreamer.  Mplayer is the best in my opinion (highest quality and lowest overhead on all the hardware I have tried it on), but it is not well integrated into Ubuntu and can be difficult to set up.  Xine is the one that is best integrated into Ubuntu.  Details on installing it and getting all formats working are [here]("https://help.ubuntu.com/community/RestrictedFormats").

Take care,
-mat

---

### Post by Alcopops on 2007-02-19
Hi Matt, thanks for the info, I have managed to get one of the alternative media players (gxine) installed and it plays flac files well, as does vlc infact.

I really need to create and burn audio cds from flac files though, so I need a burning program that doesn't rely on gstreamer.

I was looking at k3b but from surfing the web I am not sure if it 

a) will work independantly of gstreamer 
and 
b) supports audio cd creation from flac files.

Alternatively, perhaps I can manually convert flac files to wav files and use these to create an audio cd which should avoid any loss of quality. Is there a conversion program that can convert flac files to wav files. Does anyone know if soundkonverter will do this? This method is a bit cumbersome though, and would not let me work with cue files.

I guess the neatest solution would be to solve the problem with gstreamer but If I can't uninstall it and then reinstall it (without buggering the os) I am stuck since I wouldn't know where to start looking for the problem.

If anyone else has any ideas I would love to hear them :)

Cheers,

Jaime

---

### Post by Alcopops on 2007-02-19
update

grabbed k3b from repositories

did everything I wanted straight out of the box with zero configuration

Amazing...

...just Amazing

thanks all.

---

