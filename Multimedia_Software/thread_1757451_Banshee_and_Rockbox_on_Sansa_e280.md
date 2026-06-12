---
title: "Banshee and Rockbox on Sansa e280"
date: 2011-05-13
forum: Multimedia Software
---

### Post by ds_shellback on 2011-05-13
Hi,

I'm trying to get Banshee to play nicely with Rockbox on a Sansa e280. I've put together the following .is_audio_player file which generally works ok. The Sansa e280 I've got has an additional 8GB microSD card in which means that when connected you get two instances; one called "Rockbox" and the other called "Rockbox Device" - these both show up in Banshee.

```
name="Rockbox"
audio_folders=MUSIC/
video_folders=VIDEO/
folder_depth=2
output_formats=audio/mpeg,video/mpeg,audio/ogg,audio/x-realaudio,audio/x-wav,audio/flac
input_formats=audio/mpeg
cover_art_file_type=jpg
cover_art_file_name=cover.jpg
cover_art_size=100
playlist_path=../PLAYLISTS/%File
playlist_format=application/x-mpegurl

```

I've got two problems:-

The same .is_audio_player file on the e280 and on the microSD card don't seem to behave the same; Playlists on the microSD card get put in /PLAYLISTS at the root level of the card; but despite my best efforts the e280 gets the PLAYLISTS as a sub-folder in the /MUSIC folder!

Is Banshee overriding the ../PLAYLISTS from .is_audio_player ???

This bug report gives the impression it should work:-
[https://bugzilla.gnome.org/show_bug.cgi?id=612342](https://bugzilla.gnome.org/show_bug.cgi?id=612342)

Also I have a lot of video podcasts in the folder /PODCASTS/.. which get a mention in the nice coloured bar banshee shows to indicate the file types on the device - is there some way to make these visible under the device entry in Banshee?

Thanks

---

