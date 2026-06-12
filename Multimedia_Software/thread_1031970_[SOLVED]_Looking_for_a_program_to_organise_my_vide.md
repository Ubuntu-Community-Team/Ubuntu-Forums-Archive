---
title: "[SOLVED] Looking for a program to organise my video clips..."
date: 2009-01-05
forum: Multimedia Software
---

### Post by OzSchuby on 2009-01-05
Gudday.

So I've got quite a collection of short clips off YouTube etc that I'd like to organise.

I like Picasa for pictures, how you can assign and search for tags, so I downloaded that, but it doesn't support video files...

I've tried a search on Linux App Finder and Google but haven't managed to find what I'm looking for.

Main features I'd like are the ability to put tags on video files, easy viewing of the files and possibly a notes section.  (I know that might be pushing it a bit...)

Anyway, I hope someone out there has got some ideas.

Cheers!

p.s.  This is my first thread in any forum - hope I get some help...

---

### Post by lovinglinux on 2009-01-05
Welcome to the Ubuntu community. Here you will get a lot of help, that's for sure :)

When someone gives you good info, don't forget to hit the "thanks" button on the bottom right corner of the post, to show your appreciation. If your question is solved, don't forget to tag the thread as solved using the "Thread Tools" menu. This help others looking for the same solution and allow people who give help in the forums to avoid reading a solved thread.

I think what you need is [GCstar]("http://www.gcstar.org"). You can add tags with it, descriptions and a lot more info. I has an option to add a link to the video file, for opening it from GCstar, so you can easily browse and play your collection.

GCstar is primarily designed for movie collection, but it also has options for toggling the display of information you don't need, thus making it very flexible.

I don't recall how Picasa tagging system works, but usually this kind of software (at least the good ones) embed the tags as EXIF/IPTC data in the image file itself, so you can retrieve them with any software with EXIF/IPTC support. GCstar does not embed tags in the videos, but inside a database. So you if you loose your database, the tags are gone. Nevertheless, it has several exporting options for compatibility with other softwares.

I'm not aware of any software for Linux with the capability of embedding tags directly into videos. In my Windows times, I knew an application that was able to embed tags in avi files, but since video formats in general do not support tags it is kind of useless, unless you convert your collection to avi.

There is mkvtoolnix that can embed tags into mkv containers, but I'm not aware of applications that can read them to organize or search your collection.

---

### Post by OzSchuby on 2009-01-06
Cool.

Thanks for your quick post!  I've installed GCstar and had a try, but it seems a bit buggy.

(I originally tried the 'movie collection' model and found that didn't really do what I wanted - I couldn't search/sort based on my tags/info.  So then I tried to set up my own user model for the clips, and when I tried to add an entry it went blank, and reloading the file came up with an error...  Might have to jump on the GCstar forum to see if I can get some help with it.)

It does look like the user model collection should do most of what I want it to though (if I can get it working...)

Thanks again for your help - I reckon I'll mark this as solved.

---

### Post by lovinglinux on 2009-01-07
I have experienced some issues with it too, when filtering by "Series". I'm not using it right now, because what I need is an application to record and track TV series.

So I'm developing my own application. It is actually a Firefox extension.

You might want to take a look on it at [http://fmc.isgreat.org/](http://fmc.isgreat.org/)

Probably not what you need, but the next version will include a playlist manager that search for video files on a folder you specify and list them so you can play, create playlists and save playlists. Now I'm considering creating a tagging system. I don't think will be hard to do that.

---

### Post by lovinglinux on 2009-01-11
I did it. As mentioned in the previous post, the next version of my extension will handle tags and a lot more stuff.

It will automatically list all media files from folders that you specify in the preferences, where you store videos, tv recordings, music and downloads. Then you can play those files or add them individually to a playlist and save it. You can also automatically create playlists based on keywords contained in the media file names or based on tags that you assign to each media file. You can assign any number of tags to each media you need.

You can also append playlists to saved playlists, delete or edit them manually through the extension interface.

I'm very excited with this new version. Despite the fact that it has a lot of features for tracking and recording TV shows and movies, I think you will like the playlist manager.

I will release it soon, but there a few issues to solve first.

---

