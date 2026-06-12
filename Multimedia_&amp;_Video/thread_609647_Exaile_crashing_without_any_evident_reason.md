---
title: "Exaile crashing without any evident reason"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by mAkKoOo210 on 2007-11-11
running exaile from the terminal, I don't get any error message but 
segmentation fault: core dumped
And then the program closes, even from the tray...
Any solution?

Ubuntu Gutsy Gibbon here, Exaile.py 0.2.10 (from information window)

---

### Post by Nano Geek on 2007-11-11
Did you install Exaile from Ubuntu or from the Exaile site?

---

### Post by mAkKoOo210 on 2007-11-11
From ubuntu repos...

---

### Post by Nano Geek on 2007-11-11
Hmm. Interesting.
What kind of computer specs do you have?
64 bit? AMD or Intel? Type of motherboard?

---

### Post by Nano Geek on 2007-11-11
If you want to try reinstalling it from source, you can use these instructions.

Type the following into the terminal. ```
sudo apt-get build-dep exaile
``````
wget http://www.exaile.org/files/exaile_0.2.11.1.tar.gz
```Extract the tar file in your home folder then.```
cd ./exaile_0.2.11.1/
``````
./configure && make && sudo make install
```
After that try it and see if it works.

Hope that helps.

---

### Post by mAkKoOo210 on 2007-11-12
Ubuntu i386, intel pentium 4...
For the motherboard, I don't know, any way to get it from the terminal?


I have followed your instruction, but I had a problem, typing> user@user-desktop:~/exaile_0.2.11.1$ ./configure && make && sudo make install
bash: ./configure: Nessun file o directory
???

---

### Post by Nano Geek on 2007-11-12
> **mAkKoOo210 said:**
> Ubuntu i386, AMD x600...
For the motherboard, I don't know, any way to get it from the terminal?


I have followed your instruction, but I had a problem, typing
???It's **./configure** not **/configure**. Also, you might want to remove your user name from the terminal output that you posted here. Just to stay secure. ;)

---

### Post by mAkKoOo210 on 2007-11-12
I've edited the previous reply because of some errors I made reporting...please check again, and thanks for your patience :)

---

### Post by Nano Geek on 2007-11-12
> **mAkKoOo210 said:**
> I've edited the previous reply because of some errors I made reporting...please check again, and thanks for your patience :)I think I figured it out. Try this insteed:```
make && sudo make install
```

---

### Post by mAkKoOo210 on 2007-11-12
Yes, this worked ^_^
But, exaile has some new features, right?
Will it update automatically? Or will I have to do something to keep it up to date?

(I'm waiting to see if this crashes or not...:P)

Edit: Why clicking on "Entire library", it says more/less: "Search Error: no such column: tracks.albums" ?

---

### Post by mAkKoOo210 on 2007-11-12
Damn, it happened again, Exaile crashed...:/

---

### Post by Nano Geek on 2007-11-12
> **mAkKoOo210 said:**
> Yes, this worked ^_^
But, exaile has some new features, right?
Will it update automatically? Or will I have to do something to keep it up to date?

(I'm waiting to see if this crashes or not...:P)

Edit: Why clicking on "Entire library", it says more/less: "Search Error: no such column: tracks.albums" ?Strange. That works fine for me. Does it say anything in the terminal when you do that?

---

### Post by mAkKoOo210 on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> Strange. That works fine for me. Does it say anything in the terminal when you do that?
> SELECT paths.name FROM artists, albums, tracks, paths WHERE paths.id=tracks.path AND artists.id=tracks.artist AND albums.id=tracks.albums ORDER BY LOWER(artists.name), THE_CUTTER(albums.name)
Traceback (most recent call last):
  File "/usr/local/lib/exaile/xl/panels/playlists.py", line 496, in open_playlist
    self.exaile.all_songs, None, None, sql)
  File "/usr/local/lib/exaile/xl/library.py", line 230, in search_tracks
    raise e
sqlite3.OperationalError: no such column: tracks.albums

But, as I said, apart from that, today it crashed, and even more I get this error (at loading, not when it crashes):
> Traceback (most recent call last):
  File "/usr/local/lib/exaile/xl/plugins/manager.py", line 62, in initialize_plugin
    plugin = __import__(re.sub('\.pyc?$', '', file))
  File "/home/makko210/.exaile/plugins/hotkeys.py", line 2, in <module>
    import plugins
ImportError: No module named plugins


---

### Post by Nano Geek on 2007-11-12
Try this:```
rm -r ~/.exaile
```You'll have to re-import you music, but hopefully it will work after that.

---

### Post by skrribble on 2007-11-12
i have a similar problem, but my exaile won't open at all.  when running exaile in the terminal, this is the error i get:

```
Traceback (most recent call last):
  File "/usr/local/lib/exaile/exaile.py", line 56, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

i have followed everything in this thread, but it didn't work.  any ideas??

---

### Post by Nano Geek on 2007-11-12
> **skrribble said:**
> i have a similar problem, but my exaile won't open at all.  when running exaile in the terminal, this is the error i get:

```
Traceback (most recent call last):
  File "/usr/local/lib/exaile/exaile.py", line 56, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```i have followed everything in this thread, but it didn't work.  any ideas??You could try this, but I'm just guessing at this point.```
sudo apt-get install python-cairo
```

---

### Post by mAkKoOo210 on 2007-11-13
> **asjdfwejqrfjcvm msz34rq33 said:**
> Try this:```
rm -r ~/.exaile
```You'll have to re-import you music, but hopefully it will work after that.
Nothing...it still doesn't work...
same error message when requesting the entire library

---

### Post by Nano Geek on 2007-11-13
> **mAkKoOo210 said:**
> Nothing...it still doesn't work...
same error message when requesting the entire libraryThis is really weird. The only other thing I could think of trying is to use the development version. It might have fixed your problem and, from what I've seen, it's fairly stable. Here are the instructions. ```
sudo apt-get install bzr-buildpackage
``````
bzr checkout http://bazaar.launchpad.net/~exaile-devel/exaile/main exaile
``````
cd ./exaile
``````
make && sudo make install
```I'm on a Windows machine right now, but I hope that will work.

---

### Post by Nano Geek on 2007-11-14
> **skrribble said:**
> i have a similar problem, but my exaile won't open at all.  when running exaile in the terminal, this is the error i get:

```
Traceback (most recent call last):
  File "/usr/local/lib/exaile/exaile.py", line 56, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```i have followed everything in this thread, but it didn't work.  any ideas??Both of you try this. It has been confirmed to work on Launchpad for a problem very similar to yours.
[https://bugs.launchpad.net/libcairo/+bug/129816/comments/11](https://bugs.launchpad.net/libcairo/+bug/129816/comments/11)

---

### Post by mAkKoOo210 on 2007-11-14
what should this do?
I deleted the exaile folder, and then sudo ldconfig...
I'll try exaile now

Edited: I'm a fool -.-
Now exaile doesn't start at all...Even reinstalling...

---

### Post by Nano Geek on 2007-11-16
> **mAkKoOo210 said:**
> what should this do?
I deleted the exaile folder, and then sudo ldconfig...
I'll try exaile now

Edited: I'm a fool -.-
Now exaile doesn't start at all...Even reinstalling...I'm sorry it took me so long to get back to this.

Does it give the same error message that it gave when we first started?

---

### Post by Dieter@be on 2007-11-17
Btw you don't need to compile from source.
The exaile dev(s) have/has setup a repo where you can install 0.2.11 packages from.
See [http://www.exaile.org/downloads](http://www.exaile.org/downloads)

(I'm also experiencing core dumps btw, independent of the version of exaile.  I think it has something to do with not being able to parse the tags from certain mp3 files)

edit: removed the corrupted mp3 but still exaile crashes.  I only have it crash when i let it rescan my collection though (approx 15k files)

---

### Post by Nano Geek on 2007-11-17
> **Dieter@be said:**
> Btw you don't need to compile from source.
The exaile dev(s) have/has setup a repo where you can install 0.2.11 packages from.
See [http://www.exaile.org/downloads](http://www.exaile.org/downloads)

(I'm also experiencing core dumps btw, independent of the version of exaile.  I think it has something to do with not being able to parse the tags from certain mp3 files)

edit: removed the corrupted mp3 but still exaile crashes.  I only have it crash when i let it rescan my collection though (approx 15k files)Hmm, strange. I'm not really sure what the problem is here. 

If you want, you can [file a bug report at Launchpad]("https://bugs.launchpad.net/exaile/") and possibly they would know of a fix that I don't know of.

---

### Post by mAkKoOo210 on 2007-11-17
Nevermind.
For a stupid error of mine, I had to format both Windows and Ubuntu, so now I have a brand new exaile running on my machine, and it works very well ^_^
Thank you a lot for your support :)

---

