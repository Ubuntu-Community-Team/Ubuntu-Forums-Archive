---
title: "Rhythmbox .11, Cover Art, and Screenlets"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by booljayj on 2007-10-10
The new rhythmbox, standard on Gutsy, has some trouble with the cover art plugin, namely in three areas.

1) Rhythmbox sometimes just stops showing the cover art in the bottom left, where it should be, and other times simply fails to do so completely.

2) The NowPlaying screenlet has trouble getting the cover art from rhythmbox. I have tried with the cover art plugin, the awn-cover plugin, and both together. Sometimes it will display the album art for the previous album, whereupon a little jolting will remind it of the current song. Other times, it just will refuse to show the cover art and will forever remind me that I have "No Cover".

3) Rhythmbox does not properly read covers that are stored along with the song files in their respective folders. I have most of my music highly organized and labelled, with high-quality (512 x ~512) cover art to complement that. Sometimes Rhythmbox will actually use those files, and sometimes it will just decide to use Amazon. The problem is that there is no consistency to this, and it will switch off for the exact same album numerous times.

I would think that the plugin should scan the album folders first to find manual cover art, and then search amazon to find the appropriate one if none is available. This might be an idea for a separate plugin, but is there anything that will simply post in dbus the location of the album art, allowing any program to easily access and display that information? I don't know if that's how it currently works, but my custom artwork has NEVER shown up in the NowPlaying screenlet. It only ever shows the amazon artwork. Granted, I don't exactly know how dbus works, but if it works like I think it does (a little like a log, a little like a highway, which posts entries whenever something happens and can send those to various programs) then this surely should not be a problem.

One more peeve: why wouldn't the NowPlaying screenlet resize the output of it's cover art when the size of the screenlet itself is scaled? Here's what I mean: at 100%, the screenlet shows a small ~128x128 cover art preview. At 200%, it still shows the same darn 128x128 preview, but enlarged! Please, somebody clue me in on how to get it to scale the resolution of the image along with the screenlet, and not just the size. There's nothing in the python files that resizes the images, or at least I could not find it, so how would this be possible?

Answers to any of these questions would be greatly appreciated.

---

### Post by booljayj on 2007-10-10
If you can't see the different in this little thumbnail, zoom in on the full-size pic.
[http://picasaweb.google.com/Booljayj/ForumPictures/photo#5119787371229294514](http://picasaweb.google.com/Booljayj/ForumPictures/photo#5119787371229294514)

P.S.- Just so nobody asks, those are screenlets - specifically the desktop wallpaper, now playing, and Facebook ones - on Ubuntu Gutsy, Compiz-Fusion enabled.

---

### Post by rsambuca on 2007-10-10
For some reason, Rhythmbox will first look for album covers in its hidden default folder.  I had the exact same problem as you until I found out about this.  To fix it, go to your home folder, and view the hidden files, then go to .gnome2, then rhythmbox > covers.  Delete all of the folder covers and then when you restart Rhythmbox it will look in your music folders and use them if they are there.

---

### Post by booljayj on 2007-10-10
Ah, much appreciated Mr. Bearded-Spock. That fixes the problem of cover art showing up within rhythmbox, but actually opens up a new problem with the screenlet.

Now the screenlet is showing the correct album art, but only after the song has been playing for about a minute. Pausing and resuming a song will repeat this one-minute buffer. I assume this is some sort of transfer error. Also, it's still pretty darn blurry. Any ideas, anyone?

---

### Post by mlkv on 2007-11-21
> **rsambuca said:**
> For some reason, Rhythmbox will first look for album covers in its hidden default folder.  I had the exact same problem as you until I found out about this.  To fix it, go to your home folder, and view the hidden files, then go to .gnome2, then rhythmbox > covers.  Delete all of the folder covers and then when you restart Rhythmbox it will look in your music folders and use them if they are there.

I've tried to do it but it won't work.. Rhythmbox ignores my cover.jpg file, then probes Amazon, only to find no images (it looks like it will always fail when looking for compilation album covers?).

Any idea about how I should go about trying to fix this issue?

EDIT: since everyalbum named "ArtistName - AlbumName" has its own cover.jpg that gets correctly fetched by Rhythmbox, could it be a problem with compilations, which are named "VA - AlbumName"? They seem to be the only ones that Rhythmbox refuses to play along with their cover.jpg file.

---

