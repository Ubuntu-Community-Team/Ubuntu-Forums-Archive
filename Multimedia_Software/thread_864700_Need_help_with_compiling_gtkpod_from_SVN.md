---
title: "Need help with compiling gtkpod from SVN"
date: 2008-07-19
forum: Multimedia Software
---

### Post by nimbis on 2008-07-19
I started using Ubuntu Gutsy about 6 months or so ago, and the only thing that keeps it from being perfect is that I can't transfer .mp4 movies to my iPod with gtkpod. 
Whenever I tried to transfer mp4s with the version of gtkpod in the Gutsy repos, I got this message:

[INDENT][/INDENT]```
"Import of 'movie.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library. 
The following track could not be processed (filetype is known but analysis failed): 'movie.mp4'
```

A few months ago, this statement terrified me, but since then I've become comfortable with compiling and all that, and I thought I'd give it a go.
I grabbed a libmp4v2 tarball from [http://resare.com/libmp4v2/dist/]("http://resare.com/libmp4v2/dist/"). I successfully compiled it, and installed it with checkinstall.

I then got the latest SVN of gtkpod from this command:
```
 svn co https://gtkpod.svn.sourceforge.net/svnroot/gtkpod gtkpod 

```

First I compiled the libgpod trunk directory that I got from that command, and I installed it (without checkinstall, it didn't work that way for some reason)
Then I went into the gtkpod trunk directory, and attemped to build it with these commands:
```
./autogen.sh

```
This command revealed this line near the end:
```
 mp4v2 ................: yes -- will build with aac support

```
That's good, I thought, that means that I installed libmp4v2 correctly! :)
I then attempted to make it:
```
make
```
and got this output at the end of the process:
```
display_playlists.o: In function `pm_selection_changed_cb':
/home/freman/gtkpod/gtkpod/trunk/src/display_playlists.c:1535: undefined reference to `g_warn_if_reached'
collect2: ld returned 1 exit status
make[2]: *** [gtkpod] Error 1
make[2]: Leaving directory `/home/freman/gtkpod/gtkpod/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/freman/gtkpod/gtkpod/trunk'
make: *** [all] Error 2

```
I am so, so close. I can taste it. How do I get over this last hurdle?

---

### Post by pedja_portugalac on 2009-01-17
I have same problem. After gtkpod project people have separated libgpod and gtkpod. The package from within synaptic package manager isn't fully functional. The gtkpod from synaptic can't handle mp4 movies on my iPod (the one version before iPod touch). Before Interpid (or before libgpod and gtkpod separation) the package from synaptic worked fine on previous version of Ubuntu, but now it says exactly the same as in case above.

```
"Import of 'movie.mp4' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library. 
The following track could not be processed (filetype is known but analysis failed): 'movie.mp4'
```

So I decided to compile and install from source the latest gtkpod from svn. After downloading latest packages from subversion I can do that with simple ./autogen.sh > make > sudo make install for both libgpod and gtkpod and I can see the icon in the applications menu tab but it doesn't work, not even open the window. If I try to start gtkpod from terminal it say "some error". 

Did anyone have done it with success on Interpid?

---

### Post by andrew.46 on 2009-01-18
Hi pedja,

> **pedja_portugalac said:**
> Did anyone have done it with success on Interpid?

I managed to successfully compile gtkpod but I went about is slightly differently. If you are simply after an added option you might be best to recompile from the original Ubuntu source. I suspect that the 'build-dep' command may only work for Intrepid, if so my apologies for the gentleman who uses Hardy. To assemble to required dev files I ran:

```
$ sudo apt-get build-dep gtkpod 
```

and this assembled about 8 megs of required files including the dev files for libgpod:

```

  autotools-dev comerr-dev dpatch fakeroot flex libart-2.0-dev libavahi-glib-dev
  libcurl4-gnutls-dev libflac-dev libgconf2-dev libgcrypt11-dev libglade2-dev
  libgnomecanvas2-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgpod-dev
  libhal-dev libid3tag0 libid3tag0-dev libidl-dev libidn11-dev libkadm55 libkrb5-dev
  libldap2-dev liborbit2-dev libselinux1-dev libsepol1-dev libtasn1-3-dev libxml2-dev
  m4 orbit2 patchutils

```

This list will probably vary according to what is present already on your system I guess. It did not include libmp4v2 which is not a big surprise as the Ubuntu package must be built wthout it. So the following were also added manually:

```
$ sudo apt-get install  libmp4v2-0 libmp4v2-dev libmpeg4ip-0 libmpeg4ip-dev
```

To download the gtkpod source from Ubuntu I used the following, don't use sudo for this otherwise you will need to adjust the permissions:

```
$ apt-get source gtkpod 
```

and then the following:

```

$ cd gtkpod-0.99.12
$ ./configure

```

and saw the magic words:

```

Configuration for gtkpod 0.99.12 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 GTK2 version .........: 2.14.4
 GLib2/GThread version : 2.18.2
 gnome-vfs.............: yes -- will build with automount support
 hal...................: yes -- will build with HAL support
 libcurl ..............: yes -- will build with coverart download support
 mp4v2 ................: yes -- will build with aac support
 vorbisfile ...........: yes -- will build with ogg support
 FLAC .................: yes -- will build with FLAC support

```

(wooooo hooooo!) and proceded:

```

$ make
$ sudo checkinstall --fstrans=no

```

I attach a screenshot to show gtkpod + an mp4 (aac + h264) in action :-). Now if I only had access to an iPod ....

Andrew

---

### Post by pedja_portugalac on 2009-01-21
I'll try it right now. :wink:

Yes it works. Thank You Andrew very much for helping us ones again. :razz: You are the one who helped me most this days, respect for that. :wink:
PS. Right after install ubuntu complain about update for gtkpod. Don't update, guys, if you update you'll lost your ability to transfer movies to ipod cause the update bring back official gtkpod from aptitude!!!

---

### Post by holycoww74 on 2009-05-12
thank you SOO much for this how to.... worked perfectly on my new 4th Gen ipod nano.  now I won't have to boot windows and use that pile of crap iTunes.

---

### Post by andrew.46 on 2009-05-13
Hi holycoww,

> **holycoww74 said:**
> thank you SOO much for this how to.... worked perfectly on my new 4th Gen ipod nano.  now I won't have to boot windows and use that pile of crap iTunes.

Excellent news, I had almost forgotten this little piece of research I put together :-). One day I have to ge one of these ipods!!

All the very best,

Andrew

---

### Post by Athanasius on 2009-07-03
Thank you very much, the info helped me.  I don't know why the the default version in the repos. doesn't include video support, it really should.

---

### Post by vicadin on 2009-11-26
thank you very much. the installation process went smoothly but i have a little problem here. whenever i add an MP4 file to the music library, gtkpod won't show any cover art for it. i first thought videos didnt have any cover arts and that iPod extracted little thumbs for videos from the video itself, but now it seems it doesnt. i transfer the video to my iPod, and it plays it pretty well, but there's no thumbnail (or coverart). what could be the problem? mp4 files i have are encoded with H.264/AVC codec. does gtkpod automatically extract thumbnails for videos?

---

