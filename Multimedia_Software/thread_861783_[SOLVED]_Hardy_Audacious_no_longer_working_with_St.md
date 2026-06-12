---
title: "[SOLVED] Hardy Audacious no longer working with Streaming"
date: 2008-07-16
forum: Multimedia Software
---

### Post by DantePasquale on 2008-07-16
Hi All,

I'm running Hardy and using Audacious to play .flac files mostly. I have a website running Jinzora2. Now when I try to play music from my website, Audacious doesn't work. Totem works fine (but doesn't sound as good IMHO, needs a graphic eq). 

My website is [http://www.cocoanet.us/~web8_dantepasquale/jinzora2]("http://www.cocoanet.us/~web8_dantepasquale/jinzora2") You'll need to register to try it out if you need to test this.

Audacious worked, but I found one song in .flac format, that for some reason Audacious thought it was sampled at 22hz instead of 44hz and sounded like playing a 45 at 33 rpm (showing my age here). So I started trying to figure out what was going on and ended up re-installing Audacious from the repositories. Still does not play any streams. I tried some different formats that Jinzora2 can support, but no difference and Totem can play them all. I downloaded the .flac file, and then Audacious could play it, but not from my website! Here's the only errors I see:

```
ERROR: neon: neon.c:961 (neon_aud_vfs_fread_impl): <0x8281680> Buffer underrun, trying rebuffering
```

But, if I right click on the song to View Track Details I get 2 popups. The first says:

```
Filename: http://www.cocoanet.us/~web8_dantepasquale/jinzora2/mediabroadcast.php?jz_user=USR47fa79b2ccf39&sid=S487eaec2e87ba&jz_path=T487d4ae0e3d17&action=play&type=track&jza=c0b08726247280dcf552d8f24f08ddc3&ext.flac
Input plugin: No input plugin recognized
```

The second popop says:

```
Filename: http://www.cocoanet.us/~web8_dantepasquale/jinzora2/mediabroadcast.php?jz_user=USR47fa79b2ccf39&sid=S487eaec2e87ba&jz_path=T487d4ae0e3d17&action=play&type=track&jza=c0b08726247280dcf552d8f24f08ddc3&ext.flac
Input plugin: FLACng Audio Plugin
```

Any ideas on how to figure out what is going on here? Why did this used to work? Why does Totem figure out what Codec to use but Audacious doesn't when streaming??? All Codecs are Enabled! HELP!!!:confused:

---

### Post by gandaran on 2008-07-17
reinstalling won't fix your problem as the audacious configuration files still remain in your hidden home folder, try deleting the files or even the whole .audacious folder (excerpt the audacious skins folder) and start audacious again. it'll revert to the default installation.

---

### Post by DantePasquale on 2008-07-17
The first idea I had was to remove the .audacious file, but there isn't one in my home dir and I can't find it. Every now-and-then, Audacious starts up like there's no .audacious dir at all, default skin, etc.

Where can I find the .audacious dir that is being used?

---

### Post by gandaran on 2008-07-17
audacious conf files are in hidden home .config/audacious 
skins, home .local/share/audacious (only for your own winamp, xmms or bmp skins)

---

### Post by DantePasquale on 2008-07-17
Cool, thanks for the information on where things are stored. Unfortunately, removing these to get back to the base config didn't help things. But I see in the ~/.config/audacious/log file the following:

```
** LOGGING STARTED AT Thu Jul 17 23:54:41 2008

Loaded plugin (/usr/lib/audacious/Output/null.so)
Loaded plugin (/usr/lib/audacious/Output/arts.so)
Loaded plugin (/usr/lib/audacious/Output/filewriter.so)
Loaded plugin (/usr/lib/audacious/Output/OSS.so)
Loaded plugin (/usr/lib/audacious/Output/pulse_audio.so)
Loaded plugin (/usr/lib/audacious/Output/ESD.so)
Loaded plugin (/usr/lib/audacious/Output/jackout.so)
Loaded plugin (/usr/lib/audacious/Output/ALSA.so)
Loaded plugin (/usr/lib/audacious/Input/sexypsf.so)
Loaded plugin (/usr/lib/audacious/Input/modplug.so)
Loaded plugin (/usr/lib/audacious/Input/demac.so)
Loaded plugin (/usr/lib/audacious/Input/cuesheet.so)
Loaded plugin (/usr/lib/audacious/Input/aac.so)
Loaded plugin (/usr/lib/audacious/Input/alac.so)
Loaded plugin (/usr/lib/audacious/Input/vtx.so)
Loaded plugin (/usr/lib/audacious/Input/metronom.so)
Loaded plugin (/usr/lib/audacious/Input/console.so)
Loaded plugin (/usr/lib/audacious/Input/flacng.so)
Loaded plugin (/usr/lib/audacious/Input/amidi-plug.so)
Loaded plugin (/usr/lib/audacious/Input/wma.so)
Loaded plugin (/usr/lib/audacious/Input/timidity.so)
Loaded plugin (/usr/lib/audacious/Input/tta.so)
Loaded plugin (/usr/lib/audacious/Input/tonegen.so)
Loaded plugin (/usr/lib/audacious/Input/musepack.so)
Loaded plugin (/usr/lib/audacious/Input/wavpack.so)
Loaded plugin (/usr/lib/audacious/Input/madplug.so)
Loaded plugin (/usr/lib/audacious/Input/cdaudio-ng.so)
Loaded plugin (/usr/lib/audacious/Input/vorbis.so)
Loaded plugin (/usr/lib/audacious/Input/sid.so)
Loaded plugin (/usr/lib/audacious/Input/sndfile.so)
Loaded plugin (/usr/lib/audacious/Input/adplug.so)
Loaded plugin (/usr/lib/audacious/Effect/echo.so)
Loaded plugin (/usr/lib/audacious/Effect/ladspa.so)
Loaded plugin (/usr/lib/audacious/Effect/sndstretch.so)
Loaded plugin (/usr/lib/audacious/Effect/voice_removal.so)
Loaded plugin (/usr/lib/audacious/Effect/stereo.so)
Loaded plugin (/usr/lib/audacious/Effect/audiocompress.so)
Loaded plugin (/usr/lib/audacious/General/song_change.so)
Loaded plugin (/usr/lib/audacious/General/aosd.so)
Loaded plugin (/usr/lib/audacious/General/scrobbler.so)
Loaded plugin (/usr/lib/audacious/General/evdev-plug.so)
Loaded plugin (/usr/lib/audacious/General/lirc.so)
Loaded plugin (/usr/lib/audacious/General/mtp_up.so)
Loaded plugin (/usr/lib/audacious/General/alarm.so)
Loaded plugin (/usr/lib/audacious/General/statusicon.so)
Loaded plugin (/usr/lib/audacious/General/gnomeshortcuts.so)
Loaded plugin (/usr/lib/audacious/General/hotkey.so)
Loaded plugin (/usr/lib/audacious/Visualization/spectrum.so)
Loaded plugin (/usr/lib/audacious/Visualization/paranormal.so)
Loaded plugin (/usr/lib/audacious/Visualization/rocklight.so)
Loaded plugin (/usr/lib/audacious/Visualization/blur_scope.so)
Loaded plugin (/usr/lib/audacious/Visualization/rootvis.so)
Loaded plugin (/usr/lib/audacious/Container/pls.so)
Loaded plugin (/usr/lib/audacious/Container/xspf.so)
Loaded plugin (/usr/lib/audacious/Container/m3u.so)
Loaded plugin (/usr/lib/audacious/Transport/lastfm.so)
Loaded plugin (/usr/lib/audacious/Transport/mms.so)
Loaded plugin (/usr/lib/audacious/Transport/neon.so)
Loaded plugin (/usr/lib/audacious/Transport/stdio.so)
device: default
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_item_visible: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_list_get_visible_count: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_list_get_visible_count: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_list_get_visible_count: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_list_get_visible_count: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_list_get_visible_count: assertion `UI_SKINNED_IS_PLAYLIST(playlistwin_list)' failed
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_update_list: assertion `playlistwin_list' failed
playlistwin_update_list: assertion `playlistwin_list' failed
dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
D-Bus support has been activated
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
skin_pixmap_free: assertion `p->pixbuf != NULL' failed
Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
Sending SaveYourselfDone(True) for initial SaveYourself
Received SaveComplete message in state save-yourself-done
Setting initial properties
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
tuple_get_value_type: assertion `tuple != NULL' failed
```

I seem to remember something about Audacious puking when .flac files have mp3 id information. Can the mp3 id info be causing this 'tuple' issue?

---

### Post by DantePasquale on 2008-07-25
If anyone reads this, according to the Audacious forums, and I quote, "jinzura[sic] is a piece of sh$t use something that complies with standards". Not much help, eh? So, since I don't feel like totally redoing my website with icecast or ampache then I'm stuck with a "piece of" well, you know...

I'm going to mark this thread solved and move on with my life ;)

---

### Post by foresto on 2008-08-22
I, too, have been cursing audacious on hardy.  Since upgrading from gutsy, audacious no longer plays most of my favorite shoutcast streams (e.g. somafm.com) and no longer handles .m3u playlist files that contain relative paths.

Upgrading to audacious 1.5.1 helped with these two problems quite a bit.  Unfortunately, doing so was a pretty involved task, so I don't expect most people will be able to follow in my footsteps.  This latest version is available in Intrepid, which won't be released for months.  Maybe someone can get it backported to Hardy, for all of us who just want our lightweight music player back?

---

### Post by Hopey on 2008-11-10
Well what I have learned via talking with Audacious developers, they think Ampache is piece of **** too. They are quite hard to work with in this case. If you want to stream, I suggest use some other player. Audacious could be the really nice, clean and good sounding player that Linux needs after Xmms, sadly it's developers are brats.

BTW audacious 1.5.1 stopped working with Ampache after upgrading to Ubuntu 8.10.

Oh, others have same problems too:

[http://ubuntuforums.org/showthread.php?t=965782&highlight=ampache+audacious](http://ubuntuforums.org/showthread.php?t=965782&highlight=ampache+audacious)

---

