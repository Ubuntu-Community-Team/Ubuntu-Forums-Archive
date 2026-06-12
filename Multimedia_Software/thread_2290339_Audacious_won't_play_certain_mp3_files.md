---
title: "Audacious won't play certain mp3 files"
date: 2015-08-11
forum: Multimedia Software
---

### Post by Evil Wayz on 2015-08-11
According to the error message it can't read the metadata.  THey work fine in my mp3 player, and I refuse to believe that many files are corrupt.  Anyone got a workaround to make Audacious play even with bad metadata?

---

### Post by FakeOutdoorsman on 2015-08-11
Can you provide a sample file?

---

### Post by Dennis N on 2015-08-11
Well, that's interesting that unreadable metadata would stop it playing. From what I have seen, Audacious doesn't need really need tags (metadata) to play. You could remove the tag and see if it plays the music without one. This can be done with an editor like Easytag. If so, you can write new compliant tags using Easytag. It also applies 'automatic corrections' to tags as they load - that's what the status box reports its doing, anyway. Maybe that alone will fix things.

---

### Post by mc4man on 2015-08-11
A sample would be best, at worst go - 
audacious -V /path/to/badmp3
& post complete terminal output

---

### Post by Evil Wayz on 2015-08-11
I tried to upload the most recent bad metadata song, and ubuntuforums won't let me upload it because it says the file is invalid.  Tried playing it and it said invalid stream.  Which means mostly likely they are corrupt.  Which means I get to sort through 1300 songs and get new copies.  Yay.

---

### Post by mc4man on 2015-08-11
> **Evil Wayz said:**
> I tried to upload the most recent bad metadata song, and ubuntuforums won't let me upload it because it says the file is invalid.  Tried playing it and it said invalid stream.  Which means mostly likely they are corrupt.  Which means I get to sort through 1300 songs and get new copies.  Yay.

you could try uploading one here if desired - if so then post link
[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by ajgreeny on 2015-08-11
Or you could archive a file and send it to us as a tar.gz or similar; that should work OK.

---

### Post by Evil Wayz on 2015-08-11
This output is huge, i apologize but there's no ```
 tag on ubuntu forums.  
[code]
INFO dbus-server.cc:739 [name_acquired]: Owned D-Bus name (org.atheme.audacious) on session bus.
INFO main.cc:353 [main]: No remote session; starting up.
INFO vfs.cc:93 [VFSFile]: <0x1ad5e30> open (mode r) file:///home/wolf/.config/audacious/config
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Transport/mms.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Transport/gio.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Transport/neon.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/cue.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/asx.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/m3u.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/audpl.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/pls.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/asx3.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/xspf.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/flacng.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/sid.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/modplug.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/xsf.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/ffaudio.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/vtx.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/console.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/cdaudio-ng.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/aac-raw.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/sndfile.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/amidi-plug.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/madplug.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/wavpack.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/psf2.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/vorbis.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/adplug.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/tonegen.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/metronom.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/qtaudio.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/oss4.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/pulse_audio.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/filewriter.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/alsa.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/sdlout.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/jack-ng.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/stereo.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/echo.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/resample.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/crystalizer.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/mixer.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/voice_removal.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/sox-resampler.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/silence-removal.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/bs2b.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/crossfade.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/speed-pitch.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/compressor.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Effect/ladspa.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/scrobbler.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/mpris2.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/playlist-manager.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/albumart.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/skins.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/gnomeshortcuts.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/lyricwiki-qt.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/search-tool.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/song-info-qt.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/aosd.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/alarm.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/notify.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/statusicon.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/hotkey.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/cd-menu-items.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/qtui.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/gtkui.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/albumart-qt.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/song_change.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/lirc.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/delete-files.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/General/lyricwiki.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Visualization/cairo-spectrum.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Visualization/blur_scope.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Visualization/gl-spectrum-qt.so
INFO plugin-registry.cc:525 [plugin_register]: Register plugin: /usr/lib/x86_64-linux-gnu/audacious/Visualization/gl-spectrum.so
INFO plugin-init.cc:99 [start_single]: Starting selected output plugin PulseAudio Output.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/Output/pulse_audio.so.
INFO playlist-files.cc:47 [playlist_load]: Loading playlist file:///home/wolf/.config/audacious/playlists/1000.audpl.
INFO playlist-files.cc:58 [playlist_load]: Trying playlist plugin Audacious Playlists (audpl).
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/Container/audpl.so.
INFO vfs.cc:93 [VFSFile]: <0x1aede30> open (mode r) file:///home/wolf/.config/audacious/playlists/1000.audpl
INFO probe.cc:34 [aud_file_find_decoder]: Probing file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/07%20%20The%20Fray%20-%20Look%20After%20You.mp3.
INFO probe.cc:59 [aud_file_find_decoder]: Matched MPG123 Plugin by extension.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/Input/madplug.so.
INFO probe.cc:34 [aud_file_find_decoder]: Probing file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/Allanah%20Miles-Black%20Velvet.mp3.
INFO probe.cc:59 [aud_file_find_decoder]: Matched MPG123 Plugin by extension.
INFO adder.cc:124 [add_file]: Adding file: file:///path/to/badmp3
INFO probe.cc:34 [aud_file_find_decoder]: Probing file:///path/to/badmp3.
INFO plugin-init.cc:143 [start_multi]: Starting Audio CD Menu Items.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/General/cd-menu-items.so.
INFO vfs.cc:93 [VFSFile]: <0x7fd5480013b0> open (mode r) file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/Allanah%20Miles-Black%20Velvet.mp3
INFO vfs.cc:93 [VFSFile]: <0x7fd544001300> open (mode r) file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/07%20%20The%20Fray%20-%20Look%20After%20You.mp3
INFO plugin-init.cc:143 [start_multi]: Starting MPRIS 2 Server.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/General/mpris2.so.
INFO plugin-init.cc:99 [start_single]: Starting selected interface plugin GTK Interface.
INFO plugin-load.cc:55 [plugin_load]: Loading plugin: /usr/lib/x86_64-linux-gnu/audacious/General/gtkui.so.
INFO interface.cc:69 [interface_load]: Loading GTK Interface.

(audacious:15424): IBUS-WARNING **: The owner of /home/wolf/.config/ibus/bus is not root!
ERROR mpg123.cc:238 [read_tuple]: mpg123 probe error for file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/Allanah%20Miles-Black%20Velvet.mp3: Message: I am done with this track.
INFO probe.cc:34 [aud_file_find_decoder]: Probing file:///path/to/badmp3.
ERROR vfs_local.cc:116 [vfs_local_fopen]: /path/to/badmp3: No such file or directory
INFO probe.cc:77 [aud_file_find_decoder]: Open failed: No such file or directory.
INFO probe.cc:34 [aud_file_find_decoder]: Probing file:///path/to/badmp3.
ERROR vfs_local.cc:116 [vfs_local_fopen]: /path/to/badmp3: No such file or directory
INFO probe.cc:77 [aud_file_find_decoder]: Open failed: No such file or directory.
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR util.cc:140 [audgui_simple_message]: Error opening file:///path/to/badmp3:
No such file or directory
ERROR mpg123.cc:238 [read_tuple]: mpg123 probe error for file:///media/wolf/2a1e3aba-3972-4747-8794-cb8a38caf061/home/wolf/Music/Music/07%20%20The%20Fray%20-%20Look%20After%20You.mp3: Message: I am done with this track.
```

---

### Post by mc4man on 2015-08-11
> audacious -V /path/to/badmp3
/path/to/badmp3 means *you*r  path to one of *your *bad mp3's. 
Ex. *here*, mp3 is in Music folder
> audacious -V /home/doug/Music/'cold cold ground.mp3'

Or just start audacious from terminal with
audacious -V
Then pick a troublesome mp3 in audacious gui, post terminal 
(there are always code tags available..

---

### Post by Evil Wayz on 2015-08-11
Oh.  Derp.  Give me a second, I'll find one.

---

### Post by Evil Wayz on 2015-08-11
[IMG]http://i59.tinypic.com/331dq9f.jpg[/IMG]

---

### Post by ajgreeny on 2015-08-11
Install mediainfo and run command ```
mediainfo /path/to/badmp3
```

---

### Post by Evil Wayz on 2015-08-11
mediainfo /home/wolf/Heart.mp3
General
Complete name                            : /home/wolf/Heart.mp3
File size                                : 4.67 MiB

---

### Post by Evil Wayz on 2015-08-11
Here's that sample file someone was askin about. [http://www.datafilehost.com/d/4f945d39]("http://www.datafilehost.com/d/4f945d39")

---

### Post by mc4man on 2015-08-11
> **Evil Wayz said:**
> Here's that sample file someone was askin about. [http://www.datafilehost.com/d/4f945d39]("http://www.datafilehost.com/d/4f945d39")
What ever it is doesn't seem to be anything a pc can do with, there's  just no 'info' at all. The whole file shows as in screen, ie. - nothing

---

### Post by shantiq on 2015-08-12
yes clearly something did not happen at the ripping process and the file although it claims 4.7Mb   has nothing in it which is why it does not play
how did you rip the disc to get this file; which process was used; which ripper?

---

### Post by Yellow Pasque on 2015-08-12
There's no DRM/encryption involved here, correct?

---

### Post by Evil Wayz on 2015-08-12
No DRM involved.  I believe the majority of these were ripped with sound juicer.  I KNOW I have listened to these mp3s before, i just hadn't in awhile.   I'm curious to know how this happened.  only thing I can think is I crashed linux mint a couple times and restored my files from a portable drive.  Maybe they didn't copy over?

---

