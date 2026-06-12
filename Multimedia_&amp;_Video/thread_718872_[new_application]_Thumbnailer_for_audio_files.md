---
title: "[new application] Thumbnailer for audio files"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by stephantom on 2008-03-08
Step right up folks, gaze upon the miracle of all file thumbnailers because I am happy to present to you a shiny new script to do just that.

[center][img]http://img3.imagebanana.com/img/05lji7bf/Screenshot.png[/img][/center]

Yup, it generates thumbnails from your audio files (mp3 and flac to be precise).
The magic is done through extracting three seconds of audio data from the input file (starting from 00:10 because a lot of songs tend to have silence at the beginning).
So the files will have to have a minimum length of 13 seconds or they don't get a thumbnail.
The extraction is done using sox - a really wonderful tool for song editing - which also converts it to raw text data. This textual data is then trimmed and fed to gnuplot which produces the graph. The composite tool from the ImageMagick project then helps us to overlay an icon.

I'll attach a debian package to this post (it depends on sox, gnuplot and imagemagick). It's essentially just a bash script, so it should work on other architectures than i386, I guess.

You'll need to relogin (or killall -9 nautilus) for it to work.

Things you can customize:
[list][*]If you know your way around gnuplot you can probably change the color of the graph (currently it's red) or tweak it otherwise. Please let me know what you're doing and show examples! :-)
[*]You can replace the music note icon with any file you like (it's in /usr/share/audiothumb/overlay.png). Just try have it about the same size (or adjust the placement options in /usr/bin/audiothumb [line 12]).[/list]

Things I can't figure out right now:
[list][*]How to get rid of the frame/border that nautilus draws around every thumb. I imagine the thumbs would look nicer without them. Anyone know how to turn them off?
[*]How to enable this for ogg vorbis files. Their MIME type has a plus sign in them and gconf keys don't like plus signs.[/list]


Please post thoughts and feedback on this! :-)

---

### Post by abadr on 2008-05-28
Well, I didn't use this for Gnome as you planned but I looked at the script and copied the functionality to a web app I'm working on. 

Thanks for figuring that out.

---

