---
title: "Import playlists from iPod/iTunes"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by grsing on 2007-01-15
Is there any way to import playlists from either an iPod or saved from iTunes into a music program in Ubuntu? When my iPod is plugged in, I can just play the playlists off of it through RhythmBox, but I'd like to be able to do it with the music I have on my computer (it's the same music, pretty much). I spent a long time making many of those playlists, and it'd be nice if I didn't have to remake them by hand just for Rhythmbox/Exaile/whatever (I'm fairly agnostic regarding what music player I use in Ubuntu, so if there's one that does this in a way that others can't, that's fine). Thanks.

---

### Post by NeoLithium on 2007-01-15
```

sudo aptitude install gtkpod

```

Works great for iPods :)

---

### Post by jonlatane on 2007-01-27
A fantastic alternative is to use Banshee.  There is even an iTunes import plugin that will automatically import your playlists for you.  

However, the version of Banshee in the Edgy repositories doesn't have the support for this plugin, so you'll need to build a more recent version from source.  Here's a step-by-step:


Pre:  Make sure you don't have Banshee or anything else unnecessary installed:
```

sudo apt-get remove banshee banshee-official-plugins banshee-daap
sudo apt-get autoremove

```

Also make SURE you have the universe and multiverse repositories.

1.  Install the GStreamer plugins:
```

sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly \
    gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly-multiverse \
    gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg

```

2.  Get everything you need to build it:
```

sudo apt-get build-dep banshee
sudo apt-get install libmono-sqlite2.0-cil libmono-cairo2.0-cil libglib2.0-dev \
    libtool subversion autoconf automake1.9 gnome-common libavahi1.0-cil

```

3.  Get the version 0.11.3 tarball, available at [http://banshee-project.org/Releases](http://banshee-project.org/Releases)

MAKE SURE YOU GET 0.11.3, THE NEWER VERSIONS HAVE CAUSED PROBLEMS FOR ME, AND IT HAS ALL THE SUPPORT YOU NEED ANYWAY.

4.  Extract the archive.  In a terminal, go to the directory you extracted and do:
```

./configure --prefix=/usr --disable-docs
make
sudo make install

```

5. Get the iTunes import plugin here: [http://code.google.com/p/banshee-itunes-import-plugin/downloads/list](http://code.google.com/p/banshee-itunes-import-plugin/downloads/list) and put the file iTunesImporter.dll in /usr/lib/banshee/Banshee.Plugins

6.  Make sure your folder with all your music also contains your iTunes Music Library.xml file.  If for some reason you keep your music in a directory that doesn't contain this file, I think iTunes's Export Library function should work, though I haven't tried it.  This is just an explanation and a note, the average user can skip this step.

7.  Fire up Banshee.  In Edit->Plugins... make sure that both "Smart Playlists" and of course "iTunes Importer" are enabled.  Import the folder containing all your music.  When it's done, the iTunes Import plugin will find your iTunes XML file and ask you if you want to import your play counts, ratings, playlists, smart playlists, etc.  Click "yes" and wait for it to finish and you're done!

OPTIONAL: SWITCH BACK TO UBUNTU VERSION OF BANSHEE

I always prefer to only be running software from the Ubuntu repositories.  So:
```

sudo rm -R /usr/lib/banshee
sudo apt-get install banshee banshee-official-plugins banshee-daap

```

Since your Library isn't in the directory /usr/lib/banshee, it will be retained with the downgrade.  I did have the problem that all the columns except the "Now Playing" one were taken off when I started it, but if that happens just go to View->Columns... to pick which you want.

Banshee is very, very nice and has pretty much complete iPod support.

---

### Post by jonlatane on 2007-03-19
So after doing a fresh Edgy install and getting sick of updating Banshee all the time, I've made a .deb of Banshee 0.11.3 that can use the iTunes import plugin.  It was built with checkinstall, and I added the iTunes import plugin so once you enable it everything should work right off the bat.  Just import the directory with your iTunes music files and your iTunes music library.  Again, for some reason when you first install, all the columns will be disabled but go to View->Columns to fix this.  You should be able to use this package as a drop-in replacement for the version in the repositories.

[http://www.unc.edu/~jlatane/dev/banshee_0.11.3-1_iTunes-import_i386.deb](http://www.unc.edu/~jlatane/dev/banshee_0.11.3-1_iTunes-import_i386.deb)

I would have attached it, but the file is bigger than the limit for the forums.  My university has plenty of bandwidth :)

---

