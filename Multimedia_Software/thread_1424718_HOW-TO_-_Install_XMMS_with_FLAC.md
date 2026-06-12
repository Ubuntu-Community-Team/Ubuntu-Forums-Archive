---
title: "HOW-TO - Install XMMS with FLAC"
date: 2010-03-08
forum: Multimedia Software
---

### Post by The Soul Man on 2010-03-08
This guide will show how to install XMMS from source with the Flac plugin. It was originally based on howto's from blogs. I have tested this on Karmic Koala and it should work fine.

We will start off with XMMS. We'll take the plugin later..



First you need to update your packages list
[COLOR=Black]> sudo apt-get update[/COLOR]Now install build-essentials
> sudo apt-get install build-essentialAlright, now we need to install the XMMS&#8217;s dependencies
> sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev libgl1-mesa-dev libglib1.2-dev libgtk2.0-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev libsm-dev libvorbis-dev libxxf86vm-dev libxml2-dev libssl-devNow we need a working directory
> mkdir ~/buildLet's enter the directory

> cd ~/buildDownload the XMMS sources
> wget [http://]("http:///")xmms.org/files/1.2.x/xmms-1.2.11.tar.gzExtract the file and enter the extracted directory
> tar xvf xmms-1.2.11.tar.gz> cd xmms-1.2.11/Run configure with --prefix=/usr
> ./configure --prefix=/usrNow make it
> makeand install it
> sudo make installNow we gotta make a shortcut for XMMS.
Right click on your Gnome Menu, and click on Edit Menu. Go to "Sound and Video" and press "New item"

Fill in as seen below
> Type: Application
Name: XMMS
Command: xmms %F
Comment: Multimedia Audio PlayerNow simply remove the work directory.
> cd ~and
> rm -dfr ~/buildYou have now installed XMMS. Let's install the flac plugin.

We need to get the build dependencies
> sudo apt-get build-dep flacMake working directory
> mkdir ~/buildEnter it
> cd ~/buildGet flac sources
> apt-get source flacEnter flac directory
> cd flac-1.2.1Run configure
> ./configureMake
> makeCopy the library you made
> sudo cp src/plugin_xmms/.libs/libxmms-flac.so /usr/lib/xmms/InputLeave directory
> cdRemove directory
> rm -rf ~/buildYou're done!

Feel free to ask questions if problems arises.

---

### Post by BiiG on 2010-03-20
heyy man .. "./configure --prefix=/usr" after i type in this command it says 
" *** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first *** "
whats the problem ? did i mess up ? lol..

---

### Post by The Soul Man on 2010-03-23
> **BiiG said:**
> heyy man .. "./configure --prefix=/usr" after i type in this command it says 
" *** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first *** "
whats the problem ? did i mess up ? lol..
I think it will work now. I just edited the dependency part to use libglib2.0-dev instead of libglib1.2-dev.
try the how-to once more.

---

### Post by zeus.jay on 2010-06-08
Hey Soul Man were you able to get flac install working under lucid?

Thanks
J

```
charset.c:144: error: 'struct <anonymous>' has no member named 'user_char_set'
charset.c: In function 'convert_from_user_to_utf8':
charset.c:149: error: 'struct <anonymous>' has no member named 'user_char_set'
charset.c: At top level:
charset.c:152: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
charset.c:162: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
charset.c:174: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
charset.c:189: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [charset.lo] Error 1
make[3]: Leaving directory `/tmp/Build/flac-1.2.1/src/plugin_xmms'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/Build/flac-1.2.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/Build/flac-1.2.1'
make: *** [all] Error 2

```

---

### Post by asbesto on 2010-06-17
> **The Soul Man said:**
> I think it will work now. I just edited the dependency part to use libglib2.0-dev instead of libglib1.2-dev

HOW and WHERE? I can't find any modification you made in this post, and the compile doesn't work, I have the same error again.

```

checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

:confused:

---

### Post by bunuelo on 2010-12-02
The flac-1.2.1/plugin_xmms project requires libgtk1.2-dev and not the 2.0 variety.  this includes the deprecated glib-config script.

Also, I downloaded and compiled the source for xmms-1.2.11 before downloading and compiling flac-1.2.1, which had errors compiling the examples, but at least it finished compiling the flac-1.2.1/src/plugin_xmms/.libs/libxmms-flac.so file, which I copied to my ~/.xmms/Plugins directory.

Then, starting xmms worked.  The flac plugin looked beautiful sitting in the Input plugins list.  Also, the configure button worked, and I was able to set plugin parameters, but then when trying to actually play a flac file, xmms segfaulted and blamed itself.

I ran xmms through gdb and found the segfault was occuring on line 196 of flac-1.2.1/src/plugin_xmms/http.c, which is a pthread_join command.  I remarked this command, recompiled and recopied into my Plugin directory and now everything works perfectly.  yay for open source!

I love xmms.  It's the only player that can efficiently open 10,000+ streaming files in a playlist without trying to find meta-data for each one.  Let's keep fixing it up, the poor orphan.  An upgrade to glib-2.0 is due.

Bo

---

