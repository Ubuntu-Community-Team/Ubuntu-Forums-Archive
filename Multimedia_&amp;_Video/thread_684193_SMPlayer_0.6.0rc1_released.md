---
title: "SMPlayer 0.6.0rc1 released"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by rvm4000 on 2008-01-31
SMPlayer is a MPlayer frontend, developed using Qt (the current version requires at least Qt 4.2). More info [in the website](http://smplayer.sourceforge.net).

These are the most important changes since previous version (0.5.62):
> 
 * Added support for pls playlist files.
 * Better accuracy on subtitle selection. Fixes problems with mp4 embedded subtitles. Requires mplayer svn r25158 or above.
 * The cache setting is independent for each type of media.
 * New option Video->Add black borders, which replaces the letterbox options in Video->Aspect ratio.
 * Now the H.264 loop filter can be disabled for High Definition videos only (720p and above).
 * Possibility to update the video while dragging the time slider.
 * New icons for the default theme.
 * SSA/A.S.S subtitles can also be resized during playback. Requires at least mplayer r25843.
 * Now it's possible to zoom out the video image.
 * New Help->About dialog.
 * New option Help->FAQ which will show the FAQ.
 * Added the Finnish and the Korean translations.


There are some deb packages which should work on Feisty and Gutsy:

 * [smplayer_0.6.0rc1_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc1_i386.deb)
 * [smplayer-themes_0.1.15_all.deb](http://downloads.sourceforge.net/smplayer/smplayer-themes_0.1.15_all.deb)

As the version of mplayer included in Ubuntu (1.0rc1) is very old (it's so old that when that version was released I hadn't even started to develop smplayer) I have also created a deb package with a newer version (SVN r25873, dated 27 Jan. 2008):

 * [mplayer_1.0rc2svn25873_i386.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn25873_i386.deb) (compiled with gui support, includes mencoder too)

If you find any problem with any of these packages, please report ;)

---

### Post by ~LoKe on 2008-01-31
Nice work!  Unfortunately I won't be using it, as I'm partial to GTK2 front-ends for everything, but thanks!

---

### Post by bimbo on 2008-02-11
I love this. It may well start to replace kaffeine for me!

---

### Post by FlyingPenguin542 on 2008-02-18
Thanks for compiling this for us! SMPlayer is my favorite (and prettiest ;P) Mplayer GUI, as well as being the only one I've come across that deals with subtitles flawlessly. Though I don't really know why that is... oh well. Props for the shiny new MPlayer build too :D

---

### Post by rvm4000 on 2008-02-18
By the way, SMPlayer 0.6.0rc2 has already been released.

It includes some bufixes:
> 
* Fix for relative paths to the mplayer binary. The problem could cause that smplayer couldn't play anything if a directory or file named "mplayer" existed in the home directory.
* The option Play -> Repeat has been improved.
* The selection of chapters in mkv files didn't work well if using a recent mplayer from svn. This has been fixed now.


(There are also some bugfixes for Windows which I omit here)

* [smplayer_0.6.0rc2_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc2_i386.deb)

---

### Post by randcoop on 2008-02-23
I like SMplayer and would like to install the newest version.  I have the mplayer from the Gutsy repositories installed.  So I downloaded the mplayer package that is newer (linked in your message), but when I went to install it, gdebi said that there was a conflict with the installed mencoder.

Do I have to remove mplayer and smplayer using apt-get before installing the new deb packages that I've downloaded?  How do I eliminate the conflict the installer is finding?

---

### Post by rvm4000 on 2008-02-23
Maybe that *gdebi* (I've never used it) is not smart enough.

My mplayer package provides a newer version of mencoder, and it should cleanly replace the old version of mencoder. You can uninstall it manually, but at least *dpkg* would do it automatically:

```

ricardo@kubuntu:~/mplayer$ sudo dpkg -i mplayer_1.0rc2svn25873_i386.deb
dpkg: considering removing mplayer-doc in favour of mplayer ...
dpkg: yes, will remove mplayer-doc in favour of mplayer.
dpkg: considering removing mencoder in favour of mplayer ...
dpkg: yes, will remove mencoder in favour of mplayer.
(Reading database ... 98480 files and directories currently installed.)
Preparing to replace mplayer 2:1.0~rc1-0ubuntu9.2 (using mplayer_1.0rc2svn25873_i386.deb) ...
Unpacking replacement mplayer ...
Setting up mplayer (1.0rc2svn25873) ...

```

---

### Post by randcoop on 2008-02-23
Thanks...works now, though not as smooth an upgrade as I might have hoped.  Dpkg did do better than gdebi, but it still balked and said it couldn't upgrade at the end.  And that was only after I had to install libblog something and perl something.  And smplayer does require that the older one be removed...something about a conflict with smplayer-translations.

But as I said, it's working now.  

Thanks again.

---

### Post by disturbedite on 2008-02-23
smplayer is simply the best video player/frontend i've ever used.  its even better than kaffeine now, imo.

---

### Post by rvm4000 on 2008-02-23
> **randcoop said:**
> Thanks...works now, though not as smooth an upgrade as I might have hoped.  Dpkg did do better than gdebi, but it still balked and said it couldn't upgrade at the end. 

I've got that message too, but I think it refers to not upgrade the configuration file.

> **randcoop said:**
> And that was only after I had to install libblog something and perl something.

Yes, it seems mplayer depends on an old (and almost obsolete) package.

> **randcoop said:**
> And smplayer does require that the older one be removed...something about a conflict with smplayer-translations.

Again *dpkg* should cleanly install my smplayer package, replacing smplayer-translations.

---

### Post by randcoop on 2008-02-23
I did use dpkg to install smplayer...but it wouldn't do it until I ran dpkg -r on the old one.  When I tried just removing the smplayer-translator with dpkg, it wouldn't let me, saying that it would affect dependencies of the installed smplayer.  So I removed smplayer 0.5, then installed smplayer 0.6 and all was fine.  

But all of this was done with dpkg (I gave up on gdebi after you pointed out its deficiency on mplayer).

---

### Post by rvm4000 on 2008-02-24
Yes, sorry, I did't test it.

It seems it can be installed this way:
```

ricardo@kubuntu:~/svn$ sudo dpkg -i --auto-deconfigure smplayer_0.6.0rc2_i386.deb
dpkg: considering removing smplayer-translations in favour of smplayer ...
dpkg: yes, will remove smplayer-translations in favour of smplayer.
(Reading database ... 98001 files and directories currently installed.)
Preparing to replace smplayer 0.5.62-0ubuntu3~gutsy1 (using smplayer_0.6.0rc2_i386.deb) ...
De-configuring smplayer, to allow removal of smplayer-translations ...
Unpacking replacement smplayer ...
More than one copy of package smplayer has been unpacked
 in this run !  Only configuring it once.
Setting up smplayer (0.6.0rc2) ...

```

Anyway I think I fixed the problem in [revision 868](http://smplayer.wiki.sourceforge.net/space/showimage/smplayer_0.6.0rc2-SVN-r868_i386.deb):
```

ricardo@kubuntu:~/svn$ sudo dpkg -i smplayer_0.6.0rc2-SVN-r868_i386.deb
(Reading database ... 98001 files and directories currently installed.)
Preparing to replace smplayer 0.5.62-0ubuntu3~gutsy1 (using smplayer_0.6.0rc2-SVN-r868_i386.deb) ...
Unpacking replacement smplayer ...
Replacing files in old package smplayer-translations ...
Setting up smplayer (0.6.0rc2-SVN-r868) ...

```

---

### Post by randcoop on 2008-02-24
I have another question about smplayer, wondering if you might understand what's happening.  When I try the BBC news stream (with Realplayer preference, not Windows Media Player), I use the Launch Player option.  If I try to launch either mplayer or smplayer, it doesn't work.  If I use Kmplayer, it does.

Since KMplayer is using mplayer, I'm amazed that mplayer doesn't work.  And I'm wondering why SMplayer doesn't work.

Any thoughts?

---

### Post by disturbedite on 2008-02-24
kmplayer has a konqueror (& ff i think) plugin, smplayer does not.  maybe thats why.  (not being sarcastic).

---

### Post by randcoop on 2008-02-25
Not sure what you mean by that.  When I use Firefox 2.0.0.12, I use the MediaPlayer Connectivity extension and override plugins.  When I use Firefox 3.0.3 beta, that extension isn't available.  So I disable my plugins and launch the BBC video stream by using their Launch an External Player link.

In both cases, I'm not using the plugins at the BBC site, because they always fail.  I'm using mozilla-mplayerplug-in 3.40 and some others in most cases, but not at BBC.  I have no plugin installed for Kmplayer (again, unless I'm misunderstanding what you mean).

---

### Post by rvm4000 on 2008-02-25
> **randcoop said:**
> I have another question about smplayer, wondering if you might understand what's happening.  When I try the BBC news stream (with Realplayer preference, not Windows Media Player), I use the Launch Player option.  If I try to launch either mplayer or smplayer, it doesn't work.  If I use Kmplayer, it does.

You need to pass the -playlist option to smplayer:

smplayer -playlist "http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.ram?ad=1&ct=50"

Problem: the first video in the playlist doesn't have audio, and smplayer doesn't realize the 2nd does have, and so the audio options are disabled.

---

### Post by randcoop on 2008-02-25
Thanks for that answer.  I understand the problem now.

Given the limitation on the audio side for the SMplayer, it makes sense to use KMplayer for the BBC site.

---

### Post by rvm4000 on 2008-03-22
SMPlayer 0.6.0rc3 released.

> 
Most important changes since 0.6.0rc2:

 * Added new menu Video->Rotate, with options to rotate the image.
 * Added new option Play->Jump to, which will show a dialog where you can enter the position (time) to jump.
 * Added two new options in the Subtitles menu: "Enable closed caption" and "Forced subtitles only".
 * The software equalizer should work now with gl, gl2 and directx:noaccel.
 * Some multimedia keys should be recognized now in the shortcut editor.
 * Added help for all options in the preferences dialog.
 * New error dialog which will be shown if mplayer crashes, fails to start or finishes unexpectedly.
 * SMPlayer will try to use xv (or directx in windows) as default.
 * Added two new translations: Macedonian and Basque.


* [smplayer_0.6.0rc3_i386.deb](http://prdownload.berlios.de/smplayer/smplayer_0.6.0rc3_i386.deb)
* [smplayer-0.6.0rc3.tar.bz2](http://prdownload.berlios.de/smplayer/smplayer-0.6.0rc3.tar.bz2)

---

### Post by sloggerkhan on 2008-03-22
SMplayer is my favorite. It's one of only a handful of qt apps I use.

---

### Post by rvm4000 on 2008-03-25
Now it's available too a package for amd64:

[smplayer_0.6.0rc3_amd64.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc3_amd64.deb)

(Compiled on kubuntu 7.10)

---

### Post by mc4man on 2008-03-28
> SMPlayer 0.6.0rc3 released.
One thing I've noticed with rc3 is that when opening a dvd disk  the main movie starts  on chapter 2.  If I browse back to chapter 1 it treats it as a separate play list item, ie. it runs the time down, then when back in chapter 2 the time moves forward again. I see this both in gutsy and hardy - in both cases rc2 and mplayer work fine.
There are some other oddities in hardy but they don't affect use and are present in both rc2 and 3 

edit; my mistake on gutsy - while I wasn't using the repo ver. what I had was too old - works great with MPlayer SVN: 26295
will have to try similar on hardy
re edit; rc3 works fine on hardy as long as you use a newer version than what's  in hardy repo. (atm)  The linked ver. from smplayer site is also unsuitable due to packaging issue.

---

### Post by rvm4000 on 2008-03-28
One of the latest changes I made just before release 0.6.0rc3 was a fix for the chapter selection, it wasn't working well with the latest versions of mplayer.

I tried to keep things working with mplayer 1.0rc2 too, but maybe I broke something at the end. I'll take a look.

Anyway, what you describe sounds like if chapter #1 was in fact title #1. I didn't see that behavior is my tests.

> **mc4man said:**
> The linked ver. from smplayer site is also unsuitable due to packaging issue.

There's a new package: [mplayer_1.0rc2svn26030_i386.deb](http://downloads.sourceforge.net/smplayer/mplayer_1.0rc2svn26030_i386.deb)

---

### Post by mc4man on 2008-03-28
I'll try that new .deb for the heck of it though everything now works fine in both gutsy and hardy - the issue was solely the ver. of mplayer.(or at least using the latest svn resolved it)
The only strange thing now in hardy is when you do a file search for smplayer it only finds 2 files - a .desktop and an icon png - it was the icon I was looking for so that worked out

---

### Post by rvm4000 on 2008-03-29
I think this problem is fixed now in [smplayer svn r1033]( ftp://ftp.berlios.de/pub/smplayer/ubuntu/smplayer_0.6.0rc3-SVN-r1033_i386.deb). I tested with mplayer 1.0rc1, 1.0rc2 and svn r26265 and now DVDs start at chapter #1.

The fix was easy, just change this line in core.cpp (about line 569):
```

mset.current_chapter_id = 1;

```
with
```

mset.current_chapter_id = dvd_first_chapter();

```

---

### Post by mc4man on 2008-03-30
Small somewhat irrelevant update on hardy (considering it's still a beta)
svn r1033 builds and works fine in hardy - will allow people to use repo ver. of mplayer
The new updated mplayer above still suffers from package issue 
If you want to use a newer ver. of mplayer on hardy best option is to build oneself on hardy using make, make-install or checkinstall 
Using fakeroot debian/rules binary will produce libconfhelper-perl package error
Using  dpkg-buildpackage will fail in make (asm error)
Using  dpkg-buildpackage on 7.10  - package will fail in hardy due to libdirectfb version error
Ot. if anyone wants to use the latest avail. debs of sm/mplayer on hardy now without building there appears to nothing 'bad' about installing libconfhelper-perl ver. 0.12.5 on your own (depends on perl, liblogfile-rotate-perl - both available in hardy) - don't take my word on it though

---

### Post by SnakeHips on 2008-04-27
Just wanted to drop in and say thanks to RVM4000 for this great front-end to mplayer

I'm using Version: 0.6.0rc2 (SVN 834) on Xubuntu 8.04 and its sweet as a nut.

---

