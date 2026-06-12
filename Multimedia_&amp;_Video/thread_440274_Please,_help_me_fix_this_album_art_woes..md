---
title: "Please, help me fix this: album art woes."
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by RCC2k7 on 2007-05-11
So I recently decided to break free from the MP3 slavery and re-encoded my CD collection in Ogg format. Now, here's a problem.

When I had my collection in MP3 files, I have them tagged complete with album art I scanned myself. The newly created OGG collection doesn't have album art - I don't know if it is possible to embed album art in an OGG file so players will use it, as is the case with MP3s.

As a result of this, programs like Amarok and Cowbell attempt to download album art from Amazon that many times is not even the correct image. And even with this, most players won't use the downloaded art. Amarok will use art it downloads, but won't embed it into the OGG file. Rhythmbox likes to play stupid pranks like this one. [link to screenshot](http://users.onelinkpr.net/robertoc04/images/AlbumArtWoes.jpg).

Is there a way to embed album art in OGG files, using **my own** scanned images?

---

### Post by barney_1 on 2007-05-11
I use easytag to edit id3 tags.  I know the program works for ogg as well.  It has the ability to embed pictures with the id3 tags to if it's possible to do that with ogg files I'd be this program will work for you.  It's in the repo:
```
sudo apt-get install easytag
```

---

### Post by flaviusc on 2007-05-11
In order to use artwork (not embedded in the file) with Rhythmbox you have to copy the artwork image to the folder where the audio files are located and rename the picture to cover.png (or cover.jpg, etc).

---

### Post by RCC2k7 on 2007-05-11
> **barney_1 said:**
> I use easytag to edit id3 tags.  I know the program works for ogg as well.  It has the ability to embed pictures with the id3 tags to if it's possible to do that with ogg files I'd be this program will work for you.  It's in the repo:
```
sudo apt-get install easytag
```

Nice program. It doesn't support album art for Ogg files, only for MP3's but as far as other tagging options I like what I saw. Thanks.

---

### Post by RCC2k7 on 2007-05-11
> **flaviusc said:**
> In order to use artwork (not embedded in the file) with Rhythmbox you have to copy the artwork image to the folder where the audio files are located and rename the picture to cover.png (or cover.jpg, etc).

It looks like this is the only solution for album art in Ogg files so far. Thanks.

---

### Post by RCC2k7 on 2007-05-11
I had to go with **flaviusc's** suggestion. But Luther Vandross insisted in being member of a Puerto Rican rock band. :D :guitar:  I had to find out where Rhythmbox stores the album covers (~/.gnome2/rhythmbox/covers/) and remove Mr. Vandross from there.

---

### Post by starpause on 2008-04-17
a command line tool to get the job done is  [eyeD3]("http://eyed3.nicfit.net/")

here's an example usage (which assumes you are in the directory containing all the mp3s for an album and cover.jpg):

```
eyeD3 --add-image=cover.jpg:FRONT_COVER *.mp3;
```

search the net and read the man pages for more ideas :)

however, my favorite tag editor right now is [kid3]("http://kid3.sourceforge.net/") ... quite amazing how easy it is to use, simply highlight a track and drag an image into the kid3 window.

---

