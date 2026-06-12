---
title: "SMPlayer Gutsy Deb Packages"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by disturbedite on 2007-05-11
[COLOR=Red]DISCLAIMER:
I AM NOT AFFILIATED WITH THIS PROJECT IN ANY WAY.  i just enjoy the player (alongside kaffeine) and thought i'd make an *ubuntu package to share with anyone that might find it useful.[/COLOR]

i've created a deb package for smplayer with checkinstall/made on kubuntu gutsy i386/compiled with qt 4.2.3 cuz the packages available on the smplayer site are always outdated.

**Version 0.4.18** 
 * Updated the Swedish, German and Ukrainian translations. 
 * Qt 4: now the time and volume sliders should work better. Previously it wasn't easy to drag the slider's handle if it was bigger than usual. Now the actual size of the handle is taken into account so dragging should work as expected. 
 [http://www.content-type.com/-1254705825/smplayer_0.4.18-1_i386.deb.htm](http://www.content-type.com/-1254705825/smplayer_0.4.18-1_i386.deb.htm)
(click wait in line & download)

---

### Post by disturbedite on 2007-05-13
someone already beat me to it and compiled v 0.4.19 with qt 4.2.3 on feisty i386.

**Version 0.4.19** 
 * Updated the German and Russian translations. 
 * Changed the colorkey. The one in 0.4.18 didn't work on Windows with directx. 
 * Added a system tray icon if compiled with Qt 3 and KDE support.

 [http://smplayer.sourceforge.net/linux/download_en.php](http://smplayer.sourceforge.net/linux/download_en.php)

---

### Post by disturbedite on 2007-05-15
available from getdeb.  (compiled with qt4).

**Version 0.4.20** 
 * Updated the Japanese, Czech, Polish, Italian and Chinese translations. 
 * Floating control: don't assume that in fullscreen mode the screen starts at 0x0 (it might be on a 2nd monitor). This may fix the problem on which the floating control may show on the wrong monitor. 
 * Playlist: the playlist is now only marked as "modified" only when changed by the user (and not when smplayer adds items to it, for instance, the files loaded from command line). 
 * By user request: New option in preferences (config file only): initial_panscan_factor. It specifies the default zoom value all new videos will have (by default 1.0). 
 
[http://www.getdeb.net/app.php?name=SMPlayer](http://www.getdeb.net/app.php?name=SMPlayer)

---

### Post by disturbedite on 2007-05-16
made by me with same attributes as above.

**Version 0.4.21** 
 * Updated the Turkish translation. 
 * Parse the StreamTitle line from Shoutcast streams, and display it in the info window and title bar. 
 
[http://www.ifpost.com/ifpost/download/3897090525233391](http://www.ifpost.com/ifpost/download/3897090525233391)

---

### Post by disturbedite on 2007-05-17
made by me.
[B]
Version 0.4.22[/B] 
 * Updated the German translation. 
 * (Playlist) After removing the selected items, it tries to keep the cursor on the same row it was before (previosly the cursor was always moved to the 1st row). 
 * Made the rest of actions translatable. 
 * Added an option in the preferences dialog (subtitles tab) to select the default position of the subtitles. 100 means the bottom of the video window while 0 mean the top. 
 * The colorkey is configurable now. Preferences->Advanced.

[http://www.ifpost.com/ifpost/download/2326500590464443](http://www.ifpost.com/ifpost/download/2326500590464443)

---

### Post by disturbedite on 2007-05-18
by me again.

**Version 0.4.23** 
 * Updated the Turkish, German, Ukrainian, Swedish and Polish translations. 
 * Moved all translations to a subdir: src/translations. 
 And if TRANSLATION_PATH is not defined on compilation, smplayer will look for translations in application_path/translations/ (this is intended for Windows). 
 * Changed the default colorkey to 0x020202 (this really was the old colorkey). 
 * Made the colorkey field in preferences editable, so there's two ways to set the colorkey: typing it yourself or selecting a color in the color dialog. Warning: currently no check is performed on the typed value. If the value is invalid it would return 0 (black). 
 The value must be in hexadecimal, this way: #RRGGBB, where RR, GG and BB are the red, green and blue components of the color.

[http://www.ifpost.com/ifpost/download/7719297494699982](http://www.ifpost.com/ifpost/download/7719297494699982)

---

### Post by disturbedite on 2007-05-19
me again.

**Version 0.4.24** 
 * Updated the Italian and Polish translations. 
 * Added support for SSA/*** styles (-***-force-style option in mplayer). As these styles are a lot, I just simply added a line edit so you can enter the styles you want. This option may be very useful with srt/sub files when using the SSA/*** library, as subtitles may look much nicer. 
   By default, it will use "Bold=1,Outline=2,Shadow=2" which provides a  nice black shadow. 
   Info about these styles can be found at: [http://www.perlfu.co.uk/projects/asa/***-specs.doc](http://www.perlfu.co.uk/projects/asa/***-specs.doc) (look at chapter 5)

[http://www.ifpost.com/ifpost/download/5563871257780929](http://www.ifpost.com/ifpost/download/5563871257780929)

---

### Post by disturbedite on 2007-05-21
**Version 0.4.25** 
 * Not providing a default for SSA/*** style override, as this setting may affect real SSA/*** subtitles. Added a "whatsthis" help for this field. 
 * Now DESTDIR is used in the Makefile to select the installation directory,   and changed the smplayer.spec to use it. 
 * Updated the Ukrainian and German translations.

**Note: Version 0.5.0 to be released soon.** 
The main objective for version 0.5.0 was the shortcut editor. This was achived in version 0.4.15. Since then, changes have been and will be minimal until 0.5.0 is released.

[http://www.ifpost.com/ifpost/download/6323036394612873](http://www.ifpost.com/ifpost/download/6323036394612873)

---

### Post by disturbedite on 2007-05-23
**Version 0.4.26** 
(This release only contains translation updates) 
 * Updated the Ukrainian, German, Polish, Dutch, Chinese and Turkish  translations.

[http://www.ifpost.com/ifpost/download/7744927497461591](http://www.ifpost.com/ifpost/download/7744927497461591)

---

### Post by disturbedite on 2007-05-23
**Version 0.4.27**
* Applied patch to fix bug #1703280. (Segfault on exit when using Qt3).
* Now the tooltip in the system tray icon should display the same as the window title.

[http://www.ifpost.com/ifpost/download/5200632470041690](http://www.ifpost.com/ifpost/download/5200632470041690)

---

### Post by disturbedite on 2007-05-24
**Version 0.4.28** 
 * Written the documents Install.txt and Release_notes.txt, and updated Readme.txt. 
 * Updated the Polish translation. 
 * Added the Serbian translation.

[http://www.ifpost.com/ifpost/download/0960380043445877](http://www.ifpost.com/ifpost/download/0960380043445877)

---

### Post by disturbedite on 2007-05-25
**Version 0.4.29**
* Fixed bug #1725272 (the LCD in the floating control didn't show the hours).
* Added the debian subdirectory (created in a kubuntu 7.04). This way it's possible to create a deb package.
* Updated the German and Ukrainian translations.

[http://www.ifpost.com/ifpost/download/2057059008436588](http://www.ifpost.com/ifpost/download/2057059008436588)

---

### Post by disturbedite on 2007-05-27
**Note**:  i have used a new (to me) & much better method of creating deb packages and hence smplayer is now compiled with qt3 instead of qt4.  (cuz the documentation does not describe how to compile with qt4 and i assume the way of doing this is different).  (if anyone knows how to compile it with qt4 using this method please feel free to pm me). this package is created with fakeroot 1.7.1 & so future versions of smplayer will be compiled this way as well, obviously.
[B]
Version 0.4.30[/B] 
 * Updated the Japanese and Serbian translations. 
 * Added the Traditional Chinese translation. 
 * debian/control: now depends on mplayer | mplayer-nogui 
 * Install.txt: explained how to create a deb package.

[http://www.ifpost.com/ifpost/download/2904937599824498](http://www.ifpost.com/ifpost/download/2904937599824498)

---

### Post by disturbedite on 2007-05-29
compiled with qt4.[B]

Version 0.5.0[/B] 
 * Updated the Italian, German and Ukrainian translations.

[http://www.ifpost.com/ifpost/download/7399825361293408](http://www.ifpost.com/ifpost/download/7399825361293408)

smplayer themes
**Version 0.1.1**
[http://www.ifpost.com/ifpost/download/9417174282371196](http://www.ifpost.com/ifpost/download/9417174282371196)

---

### Post by _profox on 2007-05-31
Great. A package for Gutsy :)

And for all other distro versions, you can use the packages I created.
They are available on [http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
and they are updated every new release.

They are available with or without KDE support.
And for Feisty you can choose between Qt3 or Qt4.
If you don't know what to pick, check the bottom of the website.

Packages I have made available on the website:

**Ubuntu Feisty Fawn (i386)**
smplayer (Qt3; without KDE support)
smplayer (Qt3; with KDE support)
smplayer (Qt4; without KDE support)
smplayer (Qt4; with KDE support)
extra themes/icons package

**Ubuntu Edgy Eft (i386)**
smplayer (Qt3; without KDE support)
smplayer (Qt3; with KDE support)
extra themes/icons package

**Ubuntu Dapper Drake (i386)**
smplayer (Qt3; without KDE support)
smplayer (Qt3; with KDE support)
extra themes/icons package

---

### Post by disturbedite on 2007-05-31
cool.  i had grabbed some of your packages from your page before.  i tried the kde3 version package but it didn't have the kde dialog...

---

### Post by disturbedite on 2007-06-01
now compiled with qt 4.3.0.

**Version 0.5.1** 
 * Updated the Traditional Chinese and Bulgarian translations. 
 * Now the title bar shows "file name - SMPlayer", instead of   "SMPlayer - file name". 
 * MPlayer can be compiled to display its texts in another language, but SMPlayer requires the texts to be in English. Unfortunately it's not possible to change the MPlayer language without recompiling. This is a problem. 
  As a work-around I've made some of the internal regular expressions  configurable (by editing the config file). 
 rx_endoffile should specify the text that MPlayer outputs when a file has arrived to the end (by default "^Exiting... \\(End of file\\)"). If SMPlayer fails to catch this text, the playlist won't work properly. 
 rx_novideo should specify the text that MPlayer outputs when a file has no video, by default "^Video: no video". If SMPlayer fails to catch this text, the video window won't be hidden when playing sound files. 
 There are other English texts which SMPlayer looks for, but they are far less important (most of them are just simply displayed on the status bar). 
 * (By user request) Created an action to change the window from normal size to double size and vice versa (this new action doesn't appear in any of the menus, it's handled by a key shortcut, by default CTRL+D). 
 The best way would be to add key shortcuts to all Video->Size suboptions, but it's not possible for the moment (I actually can add shortcuts but they won't be configurable). 
 * It seems that it's not a good idea to have the debian subdirectory in the sources, as it can conflict with the one made by package maintainers. 
 As a quick solution, for now I've just renamed it to debian-rvm. If you want to create a deb package with dpkg-buildpackage, just rename it back to debian.

[http://www.ifpost.com/ifpost/download/3851532265583942](http://www.ifpost.com/ifpost/download/3851532265583942)

---

### Post by disturbedite on 2007-06-02
**Version 0.5.2** 
 * Updated the German and Ukrainian translations. 
 * (Qt 4) Option Open->Close, now it exits from fullscreen mode before closing   the window. 
 * Now most options in the subtitle menu are disabled if there's none subtitle  selected. 
 * If the option Play->Repeat is enabled, files will start to play from   the beginning. 
 * (By user request) Now it's possible to choose the path of the ini file. This is done by the -ini-path command line option. Example: 
   **smplayer -ini-path /tmp**   will try to read the configuration from /tmp/smplayer.ini. 
   The path is optional, if none is passed then it will use the application   path, so **smplayer -ini-path** will read the configuration from smplayer.ini   in the application path. 
 This feature requires Qt 4. The option -ini-path (and the optional argument) will be ignored if compiled with Qt 3. This option won't work either with KDE support (and in this case you'll get an error if you try to use the -ini-path option). 
 * Assigned the keys F5 and F6 for show_main_toolbar and show_language_toolbar, and updated shortcuts/default.keys with the new keys.

[http://www.ifpost.com/ifpost/download/8586201723317017](http://www.ifpost.com/ifpost/download/8586201723317017)

---

### Post by mimihu88 on 2007-06-02
> **disturbedite said:**
> **Version 0.5.2** 
 * Updated the German and Ukrainian translations. 
 * (Qt 4) Option Open->Close, now it exits from fullscreen mode before closing   the window. 
 * Now most options in the subtitle menu are disabled if there's none subtitle  selected. 
 * If the option Play->Repeat is enabled, files will start to play from   the beginning. 
 * (By user request) Now it's possible to choose the path of the ini file. This is done by the -ini-path command line option. Example: 
   **smplayer -ini-path /tmp**   will try to read the configuration from /tmp/smplayer.ini. 
   The path is optional, if none is passed then it will use the application   path, so **smplayer -ini-path** will read the configuration from smplayer.ini   in the application path. 
 This feature requires Qt 4. The option -ini-path (and the optional argument) will be ignored if compiled with Qt 3. This option won't work either with KDE support (and in this case you'll get an error if you try to use the -ini-path option). 
 * Assigned the keys F5 and F6 for show_main_toolbar and show_language_toolbar, and updated shortcuts/default.keys with the new keys.

[http://www.ifpost.com/ifpost/download/8586201723317017](http://www.ifpost.com/ifpost/download/8586201723317017)

can't be installed 
dependency problem with libc6
but libc6 already been installed in my computer
strange!

---

### Post by _profox on 2007-06-03
> **disturbedite said:**
> cool.  i had grabbed some of your packages from your page before.  i tried the kde3 version package but it didn't have the kde dialog...
That's weird. Did you try the Feisty version? Because I use the Feisty/Qt3/KDE version myself and it works like a charm on my machine.

Oh, and I see I have to update my packages to 0.5.2 :) (I'm still on 0.5.0)
But that'll be work for tomorrow..

---

### Post by disturbedite on 2007-06-03
> **mimihu88 said:**
> can't be installed 
dependency problem with libc6
but libc6 already been installed in my computer
strange!

could you be a little more specific please?  could you try installing it by doing this:
dpkg -i smplayer_0.5.2_i386.deb
and then post the output?

it might be that you need to update to a newer version of libc6.

> **_profox said:**
> That's weird. Did you try the Feisty version? Because I use the Feisty/Qt3/KDE version myself and it works like a charm on my machine.

yes the feisty version is the one i tried.  i am on gutsy tho, i don't know if thats why.  so my setup is Gutsy/Qt4 but i can't get the kde open dialog cuz i have to install a bunch more packages and it doesn't seem worth it.  (with my packages that is).

---

### Post by disturbedite on 2007-06-04
**Version 0.5.3** 
 * Updated the Polish and Russian translations. 
 * New fullscreen control widget, smaller than the previous one. If using Qt 4 it's better not to use the CleanLooks style, its buttons are huge and look awful in this widget. 
 * Fixed bug #1729705 (I hope). This has required a lot of changes, so other  bugs may appear.

[http://www.ifpost.com/ifpost/download/4124010229996769](http://www.ifpost.com/ifpost/download/4124010229996769)

---

### Post by disturbedite on 2007-06-05
whoops, i missed this version...

**Version 0.5.4** 
 * The size of the floating control can be changed by editing the config file. 
 Option floating_control_width under the [default_gui] section. The value is a percentage (100 = all screen width, 50 = half of the screen width). By default, 100. 
 * The size and position of the main window will be remembered. 
 * (Qt 4) The balloon that reminds you that the program is already running   in the system tray will be shown only 5 times.

---

### Post by disturbedite on 2007-06-05
**Version 0.5.5** 
 * Added in the audio menu an option to load an external audio file (and another one to unload it). This allows to watch movies on which the audio track is in an external file (mp3, wav...). 
 Note: if you play the movie again later, you'll see two audio tracks in the menus (the original one, and the external one), but changing tracks doesn't work. Strange things may happen if you do it. 
 * Added the option "dont_use_eq_options" in the config file, ([preferences] section). If set to true, smplayer won't pass the options -brightness, -contrast, -hue, and -saturation to mplayer. It seems that some graphic cards don't support them or have some kind of problem with them. 
 * Updated the German translation 
 * Added an empty icon for gamma (to prevent this slider to be higher than the  rest).

[http://www.ifpost.com/ifpost/download/6210325413809036](http://www.ifpost.com/ifpost/download/6210325413809036)

---

### Post by Tiftof on 2007-06-06
I'm having problems with libc6 too... Where could I get an update package for libc6?

Here's the output via dpkg:

```
(Reading database ... 184123 files and directories currently installed.)
Preparing to replace smplayer 0.5.5 (using smplayer_0.5.5_i386.deb) ...
Unpacking replacement smplayer ...
dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 smplayer depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 smplayer depends on libqt4-core (>= 4.3.0); however:
  Package libqt4-core is not installed.
 smplayer depends on libqt4-gui (>= 4.3.0); however:
  Package libqt4-gui is not installed.
 smplayer depends on libqt4-qt3support (>= 4.3.0); however:
  Package libqt4-qt3support is not installed.
 smplayer depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
dpkg: error processing smplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 smplayer

```

---

### Post by disturbedite on 2007-06-06
@Tiftof
ppl, [I]please read the previous (especially my first ones on this thread) first!
[/I]
it says right there what the problem is, you're using versions of dependencies that are too old & you don't even have some qt4 packages installed.
these packages are created on gutsy (i386) (as i said in my first post) with qt4 and are not guaranteed to work on other versions of *ubuntu.
i'd recommend going to the previous page and read the post the other guy made with a link to his page where he maintains packages for other versions of *ubuntu.  grab one of them.

---

### Post by disturbedite on 2007-06-06
**Version 0.5.6** 
 * Updated the German and Ukrainian translations. 
 * Changed the buttons in the floating control from QPushButtons to   QToolButtons. 
 * Added an option in Preferences to enable or disable the cache. (Cache could be disabled by setting it to 0, but this is clearer). 
   The cache is **disabled** by default, as it seems this option causes some trouble with some video formats. As a side effect now videos start to play faster.

[http://www.ifpost.com/ifpost/download/0955381602040486](http://www.ifpost.com/ifpost/download/0955381602040486)

---

### Post by Shinoda on 2007-06-07
> **disturbedite said:**
> compiled with qt4.Through [FONT=Courier New]dpkg-buildpackage -rfakeroot[/FONT]? Can you please tell me how? TIA.

---

### Post by disturbedite on 2007-06-07
well, you could read the documentation yourself, but in case you are lazy, i'll post how to do it here, i don't mind, really.

[COLOR=Blue] here is instructions on compiling it yourself with qt4 support:

Be sure you have installed the Qt 4 development package. Its name maybe
qt4-devel, libqt4-dev or similar. Some distros have a separate 
qt3support package, install it too.

Uncompress the source code, open a console (konsole or similar) and enter
in the smplayer-0.5.x directory.

Type: "make prep".
This is an important step. Don't forget it. That command makes some changes 
in the sources so they can be compiled with Qt 4.

Now type "make". With a little bit of lucky, that's all.

But it may fail. Don't worry.

If it fails it is probably because the Qt 3 qmake has been used instead of
the Qt 4 one. It seems that some distros (ubuntu for example) have renamed that
tool to qmake-qt4. Others may have installed in another directory.
Look at the contents of the qt4-devel package (or whatever its name is) and
find out where it is.

Now type something like this (just examples):
make QMAKE=qmake-qt4
or
make QMAKE=/usr/share/qt4/bin/qmake

Once it is compiled you can install it with "make install". That will install 
smplayer in /usr/local.[/COLOR]        

[COLOR=Red] to make a deb package with qt4 support, here is how:  (its much easier)

1.  extract the source.
2.  rename the debian-rvm folder to debian
3.  open the rules file in the debian folder
4.  find this part:
# Add here commands to compile the package.
    # Qt 3
    $(MAKE) PREFIX=/usr
    # Qt 4
    #$(MAKE) prep
    #$(MAKE) PREFIX=/usr QMAKE=qmake-qt4
4.  edit it like this:
# Add here commands to compile the package.
    # Qt 3
    #$(MAKE) PREFIX=/usr
    # Qt 4
    $(MAKE) prep
    $(MAKE) PREFIX=/usr QMAKE=qmake-qt4
(comment out the qt3 line and uncomment the two qt4 lines).
5.  open console/terminal in the smplayer-0.5.x directory or cd to it and type:
dpkg-buildpackage -rfakeroot.
the deb package will be placed in the parent folder of where you extracted the source folder (one folder up).
6.  install it from there.  (you can delete the other files if you want, they're not necessary).[/COLOR]

---

### Post by disturbedite on 2007-06-07
**Version 0.5.7** 
 * Added *.ac3 to the list of audio filters in the open dialogs. 
 * On startup, if the previous height of the window is less than 200, then  the window is resized to the default size. 
 * Updated the Polish and German translations. 
 * Updated the instructions to make a deb package in Install.txt.

[http://www.ifpost.com/ifpost/download/8249917287566972](http://www.ifpost.com/ifpost/download/8249917287566972)

---

### Post by Shinoda on 2007-06-07
> **disturbedite said:**
> well, you could read the documentation yourself, but in case you are lazy, i'll post how to do it here, i don't mind, really.I did read the [FONT=Courier New]Install.txt[/FONT] file and knew how to compile SMPlayer with Qt 4. What I didn't know was how to pass dpkg-buildpackage the flag to do so. I admit it was a tad lazy of me to not try harder and find out for myself, but at least this way maybe those even more clueless than me will benefit from your instructions. So anyway, tyvm indeed.

---

### Post by disturbedite on 2007-06-07
i was just being a little sarcastic....sorry  ;)

but yeah, i had the same question too, i emailed the author and he told me.

---

### Post by Shinoda on 2007-06-07
> **disturbedite said:**
> i was just being a little sarcastic....sorry  ;)Heh, it's cool. I myself frequently dwell in sarcasm. :]

So when I came across SMPlayer for the first time I thought I'd do more or less what you're doing here (we all like bleeding-edge debs), but since you're still very active about it, less work/worries/responsibility for me. :>

Thanks and keep it up.

---

### Post by mimihu88 on 2007-06-08
~/smplayer-0.5.7$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is smplayer
dpkg-buildpackage: source version is 0.5.7
dpkg-buildpackage: source changed by Ricardo Villalba <rvm@escomposlinux.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.7
dpkg-checkbuilddeps: Unmet build dependencies: libqt3-mt-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

when I tried to build a deb package there were errors above

---

### Post by mimihu88 on 2007-06-08
I can install the deb package downloaded here but only  0.5.0 not 0.5.5 or 0.5.7 because the dependencies problem
it is very strange that why 0.5.0 no problem

---

### Post by mimihu88 on 2007-06-08
sudo dpkg -i smplayer_0.5.5_i386.deb
dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 smplayer depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 smplayer depends on libqt4-core (>= 4.3.0); however:
  Package libqt4-core is not installed.
 smplayer depends on libqt4-gui (>= 4.3.0); however:
  Package libqt4-gui is not installed.
 smplayer depends on libqt4-qt3support (>= 4.3.0); however:
  Package libqt4-qt3support is not installed.
 smplayer depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.

---

### Post by mimihu88 on 2007-06-08
> **mimihu88 said:**
> ~/smplayer-0.5.7$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is smplayer
dpkg-buildpackage: source version is 0.5.7
dpkg-buildpackage: source changed by Ricardo Villalba <rvm@escomposlinux.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.7
dpkg-checkbuilddeps: Unmet build dependencies: libqt3-mt-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

when I tried to build a deb package there were errors above

ok,I solved the problem by installing "libqt3-mt-dev"
and installed on my computer no problem
thanks

---

### Post by disturbedite on 2007-06-08
yes, figuring out the problem requires reading.

---

### Post by disturbedite on 2007-06-08
**Version 0.5.8** 
 * Updated the Italian, Simplified-Chinese and Swedish translations. 
 * Added two new options in the Video->Deinterlace menu: kerndeint and yadif (mode 1). The latter option should give a much more fluid motion than the normal yadif option, but you need a really fast computer, as this option uses a lot of CPU. 
 Some videos require to change the field dominance to work properly, so an option for this will be added in the future. Meanwhile you can pass the option -field-dominance to mplayer if you need it.

[http://www.ifpost.com/ifpost/download/1044401763164851](http://www.ifpost.com/ifpost/download/1044401763164851)

---

### Post by rvm4000 on 2007-06-08
> **Shinoda said:**
> I did read the [FONT=Courier New]Install.txt[/FONT] file and knew how to compile SMPlayer with Qt 4. What I didn't know was how to pass dpkg-buildpackage the flag to do so. I admit it was a tad lazy of me to not try harder and find out for myself, but at least this way maybe those even more clueless than me will benefit from your instructions. So anyway, tyvm indeed.

The way to create a deb package compiled with Qt 4 is not explained yet in that document, because I think the current method is not the right way. 

I think the best would be to use a environment variable, and according to its value compile with Qt 3 or Qt 4. This way you won't need to modify the rules file. Just set a environment variable in your ~/.profile (or whatever) and forget about it.

When this is done, I'll update the instructions in Install.txt.

---

### Post by disturbedite on 2007-06-08
welcome to the forum rvm!

---

### Post by Shinoda on 2007-06-09
> **disturbedite said:**
> welcome to the forum rvm!He's been around for a few weeks already, posting in another thread (just click his nick and then "Find all posts by rvm4000"), so how come his post count is "1"? oO

---

### Post by disturbedite on 2007-06-09
**Note:  it appears that rvm forgot to bump the version number in the about dialog, unless i did something wrong.  can you confirm rvm?**[B]

Version 0.5.9[/B] 
 * Updated the Swedish, German, Ukrainian and Polish translations. 
 * The application was probably getting the wrong screen resolution if  a virtual desktop was enabled. I hope this is fixed now.

[http://www.ifpost.com/ifpost/download/4462876469470671](http://www.ifpost.com/ifpost/download/4462876469470671)

---

### Post by rvm4000 on 2007-06-09
Yes, I forgot to change the version number. It says 0.5.8 but it's indeed 0.5.9.

---

### Post by Shinoda on 2007-06-10
```
Preparing to replace smplayer 0.5.7 (using .../smplayer_0.5.9_i386.deb) ...
Unpacking replacement smplayer ...
dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 smplayer depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 smplayer depends on libqt4-core (>= 4.3.0); however:
  Version of libqt4-core on system is 4.2.3-0ubuntu3.
 smplayer depends on libqt4-gui (>= 4.3.0); however:
  Version of libqt4-gui on system is 4.2.3-0ubuntu3.
 smplayer depends on libqt4-qt3support (>= 4.3.0); however:
  Version of libqt4-qt3support on system is 4.2.3-0ubuntu3.
 smplayer depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
dpkg: error processing smplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 smplayer
```Apparently your deb depends on Gutsy's versions, and since I'm using Feisty it won't install, so I made one myself.

---

### Post by disturbedite on 2007-06-10
> **Shinoda said:**
> Apparently your deb depends on Gutsy's versions, and since I'm using Feisty it won't install, so I made one myself.

PEOPLE, PLEASE READ the thread.  i've stated that already!  more than once i believe.
and you wasted your time, since _protofox on page 3 of this thread lists his website where he maintains packages for feisty & older...

---

### Post by disturbedite on 2007-06-10
**Version 0.5.10** 
 * Moved the denoise submenu inside the video filter menu. 
 * (By user request) Added the option "AC3/DTS pass-through S/PDIF" in Preferences->General. If will simply add "-afm hwac3" to the command line. 
 * Renamed "Yadif (mode 0)" to "Yadif (normal)", and "Yadif (mode 1)" to  "Yadif (double framerate)".

[http://www.ifpost.com/ifpost/download/3808233786882289](http://www.ifpost.com/ifpost/download/3808233786882289)

---

### Post by Shinoda on 2007-06-11
> **disturbedite said:**
> PEOPLE, PLEASE READ the thread.  i've stated that already!  more than once i believe.Yeah, I've read it completely... a good while ago as you might imagine, so didn't quite remember that bit. Anyway, my bad.> **disturbedite said:**
> and you wasted your time, since _protofox on page 3 of this thread lists his website where he maintains packages for feisty & older...No, I didn't. He's still in 0.5.8. :p

---

### Post by disturbedite on 2007-06-11
[B]Version 0.5.11
[/B]* Updated the Ukrainian and German translations.
* Shortcuts for previous and next items in playlist didn't work in main window. Fixed.
* Added an option in Preferences->Subtitles to use the new -subfont option in MPlayer. In the future SMPlayer will try to autodetect when this option is needed.
* Added in Preferences a new section: MPlayer language, where the user can change some of the texts that SMPlayer looks for. Intended in case that MPlayer displays its messages in another language. (Unfortunately MPlayer can't change language at runtime).

[http://www.content-type.com/-1950241789/smplayer_0.5.11_i386.deb.htm](http://www.content-type.com/-1950241789/smplayer_0.5.11_i386.deb.htm)
(used content-type since ifpost is apparently down).

---

### Post by Shinoda on 2007-06-12
> **disturbedite said:**
> (used content-type since ifpost is apparently down).Why not just attach it?  It's simpler, more reliable, and you can keep track of the number of hits just out of curiosity.> **Shinoda said:**
> So when I came across SMPlayer for the first time I thought I'd do more or less what you're doing here (we all like bleeding-edge debs), but since you're still very active about it, less work/worries/responsibility for me. :>Please disregard that. :p I hadn't really noticed at the time yours are for Gutsy. I hope you don't mind my posting Feisty debs in your thread though. Just trying to help, etc., especially since _profox doesn't seem to have the same amount of availability as we — me and you — do to keep up with the development versions.

---

### Post by rvm4000 on 2007-06-12
> **disturbedite said:**
> **Version 0.5.11**
don't know whats new since rvm hasn't posted a changelog yet.  (i will update this when he does).

I couldn't do it yesterday because I had problems with my internet connection.
Anyway the changelog is always also inside the *.tar.gz ;)

---

### Post by disturbedite on 2007-06-12
@Shinoda
i don't use the forum attachment so that i can post in other forums too from one central location.  and besides i'm being considerate, i don't wanna clutter the ubuntuforums servers anyway.

as for your packages, i kinda do mind having feisty & gutsy packages, since mine are only for gutsy.  the reason is partly that on rvm's website he lists my packages as that specifically, so it'd be confusing to also have feisty packages.

i will change the title of my thread to SMPlayer deb packages for Gutsy...
so could you create another thread of your own with a similar title but obviously for feisty for your packages?

---

### Post by disturbedite on 2007-06-12
> **rvm4000 said:**
> I couldn't do it yesterday because I had problems with my internet connection.
Anyway the changelog is always also inside the *.tar.gz ;)

i forgot about that!  thanks for the reminder.  :)

---

### Post by Shinoda on 2007-06-12
> **disturbedite said:**
> i don't wanna clutter the ubuntuforums servers anyway.Yes, you're right. That did occur to me actually.> **disturbedite said:**
> i kinda do mind having feisty & gutsy packages, since mine are only for gutsy. the reason is partly that on rvm's website he lists my packages as that specifically, so it'd be confusing to also have feisty packages.I'm sorry, are you talking about [SMPlayer's website]("http://smplayer.sf.net/")? I can't seem to find your packages listed there. But I do agree it would be a bit confusing to have both Feisty and Gutsy packages regularly thrown at the same thread.> **disturbedite said:**
> i will change the title of my thread to SMPlayer deb packages for Gutsy...It was mainly because of the lack of such specificity that I felt I'd post Feisty packages here.> **disturbedite said:**
> so could you create another thread of your own with a similar title but obviously for feisty for your packages?[Done]("http://ubuntuforums.org/showthread.php?t=472149").

---

### Post by disturbedite on 2007-06-13
thanks.

my packages are listed [here]("http://smplayer.sourceforge.net/linux/download_en.php") btw...

---

### Post by disturbedite on 2007-06-13
**Version 0.5.12** 
 * Updated the Swedish, German and Ukrainian translations (although changes  I've just made could have broken them...) 
 * Reorganized the preferences dialog a little bit by using several tab  widgets. This prevents that sections growing too much. 
 * Better explained the "MPlayer language" section (I hope) and added regular expressions for Spanish, Italian, German and French in the comboboxes, taken from the MPlayer translation files (completely untested!).

[http://www.ifpost.com/ifpost/download/5293814325099969](http://www.ifpost.com/ifpost/download/5293814325099969)

---

### Post by Shinoda on 2007-06-13
> **disturbedite said:**
> thanks.Np, mate.> **disturbedite said:**
> my packages are listed [here]("http://smplayer.sourceforge.net/linux/download_en.php") btw...I honestly fail to understand how I didn't see them there before. Maybe I should get some sleep. :p

---

### Post by disturbedite on 2007-06-13
> **Shinoda said:**
> I honestly fail to understand how I didn't see them there before. Maybe I should get some sleep. :p

JH are my initials, maybe thats why...

---

### Post by disturbedite on 2007-06-13
**Version 0.5.13** 
 * Updated the Ukrainian, German and Polish translations. 
 * (By user request) Now the mouse wheel can be configured to zoom the video (Preferences->Keyboard and mouse->Mouse). 
 Note: compatibility couldn't be kept, if you have previously changed the behavior of the mouse wheel you'll need to change it again. 
 * Now the options in the menu Video->Size will always be executed even if the option is already selected. Useful if you resized the window. Also added shortcuts for Size->100% and Size->200% (Ctrl+1 and Ctrl+2) and I'm very sorry but these shortcuts can't be changed. 
 * (By user request) Added the option Audio->Filters->Volume normalization. 
 Note: this option only affects the current file, if you want the filter to be used for all files add "volnorm" to the audio filters field in Preferences->Advanced. 
 * (By user request) Clicking the system tray icon with the mouse middle   button pauses/unpauses the file. 
 * Tooltips for QActions are explicitly created now to try to work around   a bug in Qt 4.3.

[http://www.ifpost.com/ifpost/download/1074508081198836](http://www.ifpost.com/ifpost/download/1074508081198836)

---

### Post by colo505 on 2007-06-14
For AMD64

---

### Post by colo505 on 2007-06-14
current dev version, amd64 deb

---

### Post by disturbedite on 2007-06-14
@colo505
since you didn't make an introduction, i'll ask you this now...
your packages are created on gutsy right?  and are they compiled with qt3 or qt4?

assuming they are for gutsy, then i don't mind you posting them here... ;)

---

### Post by disturbedite on 2007-06-14
**Version 0.5.14** 
 * Updated the Swedish, Ukrainian and Polish translations. 
 * I think for volume normalization it's best to have a global option, so I added a volume normalization option in Preferences->General. If checked the volnorm filter will be used for all files. 
 * Added an option in Preferences->General to set the maximum amplification level for softvol. By default 110. Valid range 10-10000.

[http://www.ifpost.com/ifpost/download/4064865189194204](http://www.ifpost.com/ifpost/download/4064865189194204)

---

### Post by disturbedite on 2007-06-18
**Version 0.5.15 **
 * Updated the Russian, Italian, Swedish, German, Ukrainian, Polish and Simplified-Chinese translations. 
 * (By user request) Added an option in Preferences->General to enable the postprocessing filter for all videos.

[http://www.ifpost.com/ifpost/download/5489914444258394](http://www.ifpost.com/ifpost/download/5489914444258394)

---

### Post by disturbedite on 2007-06-19
**Version 0.5.16 **
 * Updated the Ukrainian and Polish translations. 
 * Added two new translations: Romanian and Portuguese from Portugal.

[http://www.ifpost.com/ifpost/download/2153493194259459](http://www.ifpost.com/ifpost/download/2153493194259459)

---

### Post by disturbedite on 2007-06-20
damn!  i just finished making the 0.5.17 package and 0.5.18 is out!  go figure.  ;)

**Version 0.5.17 **
 * Updated the Brazilian Portuguese, Slovak, Ukrainian, German and Portuguese from Portugal translations. 
 * Now QCoreApplication::arguments () will be used to read the arguments from command line if Qt > 4.1. On NT-based Windows this should allow the program to get the right characters if the filename contains characters from other alphabets.

[http://www.ifpost.com/ifpost/download/5548015027170900](http://www.ifpost.com/ifpost/download/5548015027170900)

---

### Post by disturbedite on 2007-06-20
**Version 0.5.18 **
 * Updated the Russian translation. 
 * Added support for audio CDs (only tested with one disc) so please test yourself and report problems. Test also if VCD and DVD still work properly. 
 Note: I don't know if this option will work on Windows, I never could play an audio CD with the Windows version of MPlayer.

[http://www.ifpost.com/ifpost/download/6032043774199131](http://www.ifpost.com/ifpost/download/6032043774199131)

---

### Post by disturbedite on 2007-06-21
**Version 0.5.19** 
 * Updated the German and Polish translations. 
 * (Windows) The priority of the SMPlayer process is changed accordingly to the priority of MPlayer (SMPlayer will try to run with higher priority). 
 Note: not much tested. 
 * As a lot of people have complained, I changed "Brazilian Portuguese" and "Portuguese from Portugal" to "Portuguese - Brazil" and "Portuguese - Portugal".

[http://www.ifpost.com/ifpost/download/7347530190165445](http://www.ifpost.com/ifpost/download/7347530190165445)

---

### Post by _profox on 2007-06-22
Disturbedite: maybe we could work together to provide packages :) I compile packages for smplayer for dapper, edgy and feisty. I have the following packages available:

feisty - qt3 - kde support
feisty - qt3
feisty - qt4
edgy - qt3 - kde support
edgy - qt3
dapper - qt3 - kde support
dapper - qt3

I update the development packages once or twice a week. But I also provide the latest stable version (0.5.0)
Maybe I can give you access to always upload your latest Gutsy package to my website? (if you want)

---

### Post by disturbedite on 2007-06-23
sounds good to me.  pm me the info & how to go about it.

---

### Post by disturbedite on 2007-06-23
**Version 0.5.20**
* Updated the German, Ukrainian, Portuguese and Romanian translations.
* Now it will exit from compact mode before playing an audio file. Otherwise the GUI would not have any menus or buttons at all.
* Temporary fix: in playlist, the latest_dir won't be changed when adding multiple files, to avoid that wrong paths with dvd:, vcd:... could be used.

[http://www.ifpost.com/ifpost/download/8737579650431541](http://www.ifpost.com/ifpost/download/8737579650431541)

---

### Post by disturbedite on 2007-06-25
**Version 0.5.21**
* Updated the Brazilian Portuguese translation.
* Moved the video and audio sections in Preferences->General to a new tab, and moved also the font section in Subtitles to another tab, to try to make the preferences dialog smaller.

Note: This is the last release which can be compiled with Qt 3. I'm going to start to port it to Qt 4 now. New features, bug fixes and translation updates will have to wait.

[http://www.ifpost.com/ifpost/download/1632699759793534](http://www.ifpost.com/ifpost/download/1632699759793534)

---

### Post by disturbedite on 2007-06-26
**SMPlayer Themes 0.1.2**
(don't know what new since there isn't anything in the changelog nor posted).

[http://www.ifpost.com/ifpost/download/1493912524087922](http://www.ifpost.com/ifpost/download/1493912524087922)

---

### Post by disturbedite on 2007-06-26
NOTE:
there is a new experimental qt4 build since its being port to qt4.  the rules file still has the qt3 info?  well, i tried compiling it the normal way, it wouldn't compile with the qt4 method AND the qt3 method but it refused to compile either way, so my builds may be on hold for now...

---

### Post by Shinoda on 2007-06-26
> **disturbedite said:**
> (don't know what new since there isn't anything in the changelog nor posted).Check the [FONT=Courier New]Changelog[/FONT] file in the tar.gz.

---

### Post by disturbedite on 2007-06-26
> **Shinoda said:**
> Check the [FONT=Courier New]Changelog[/FONT] file in the tar.gz.
that is the first thing i did.

---

### Post by rvm4000 on 2007-06-26
smplayer-themes-0.1.2

From the Changelog:

Version 0.1.2
 * Renamed the debian directory to debian-rvm, so it doesn't conflict with
   the one made by package maintainers.
   So if want to create a deb package with dpkg-buidpackage, rename it back
   to debian (or create a symlink).
 * Added a dependency on smplayer in the control file.

> **disturbedite said:**
> NOTE:
there is a new experimental qt4 build since its being port to qt4.  the rules file still has the qt3 info?  well, i tried compiling it the normal way, it wouldn't compile with the qt4 method AND the qt3 method but it refused to compile either way, so my builds may be on hold for now...

In rules change:

build-stamp: configure-stamp
        dh_testdir

        # Add here commands to compile the package.
        # Qt 3
        $(MAKE) PREFIX=/usr
        # Qt 4
        #$(MAKE) prep
        #$(MAKE) PREFIX=/usr QMAKE=qmake-qt4

with:
build-stamp: configure-stamp
        dh_testdir

        # Add here commands to compile the package.
        # Qt 4
        $(MAKE) PREFIX=/usr QMAKE=qmake-qt4

(not tested though)

You'll also need to change the version number in the debian/changelog.

**Edit:** I've just updated the rules file in version qt4-0626.

---

### Post by disturbedite on 2007-06-27
thanks very much for that info & the update rvm4000.

p.s.  sorry for the missed smplayer-qt4-0625 build...
p.s.#2:  a tip for others, the version field in the changelog doesn't like non-number characters!  ;)

**Version qt4-0625-1**
 * Updated the German and Polish translations.
 
 (Let's start with the easiest...)
 * Removed the prep section in Makefile, and the conv2qt4.sh and conv2qt4.bat in src/ as they won't be needed anymore.
 * Ported filedialog.h and filedialog.cpp. Removed all KDE 3 code.
 These files contains all open/save dialogs. Now using the Qt 4 dialogs, which are a little bit nicer (in linux).
 * Ported aboutdialog.h and aboutdialog.cpp. This is the "About SMPlayer" dialog.
 Note: the link at the bottom still doesn't work.
 * Ported core.h and core.cpp. Only the Qt headers have been changed. It seems no other change is required.
 * Ported infofile.h and infofile.cpp. Only the Qt headers were changed. This class creates the info text you can see in Options->View info and properties (Information tab).
 * Ported desktopinfo.h and desktopinfo.cpp. Only the Qt headers were needed to change.

**Version qt4-0626-1**
 * Updated the Polish translation.
 * Ported trackdata.h, trackdata.cpp, tracks.h, tracks.cpp, encoding.h, encoding.cpp, mediadata.h, mediadata.cpp, mediasettings.h, mediasettings.cpp, preferences.h, preferences.cpp, recents.h, recents.cpp, translator.h and translator.cpp (only renamed headers needed).
 * Ported subtracks.h and subtracks.cpp. It was necessary to change a Q3ValueList with QList. Don't know if this could have unexpected results.
 This class stores the subtitle tracks and it's responsible for checking if any of the subtitles matches the user's favourite language.

[http://www.ifpost.com/ifpost/download/4637635142139472](http://www.ifpost.com/ifpost/download/4637635142139472)

---

### Post by Shinoda on 2007-06-27
Thanks for the info, rvm4000.> **disturbedite said:**
> that is the first thing i did.I don't doubt it. Just suggested you'd check the file because it had the changes listed when I did (maybe rvm4000 updated it in the meanwhile).> **disturbedite said:**
> p.s.#2:  a tip for others, the version field in the changelog doesn't like non-number characters!  ;)Works fine with alphanumeric chars and hyphens for me (i.e. in Fiesty).

---

### Post by disturbedite on 2007-06-27
> **Shinoda said:**
> I don't doubt it. Just suggested you'd check the file because it had the changes listed when I did (maybe rvm4000 updated it in the meanwhile).
i think he did, cuz it was empty when i checked it.
[quote=Shinoda]Works fine with alphanumeric chars and hyphens for me (i.e. in Fiesty).[/quote]
duh hyphens & numbers work.  i meant letters...

---

### Post by disturbedite on 2007-06-28
**Version qt4-0627 **
 * Updated the French translation, using the one sent by Kud Gray. 
 * Ported inputdvddirectory.h, inputdvddirectory.cpp and inputdvddirectorybase.ui (first ui ported, not easy to port these files...). This dialog appears when the user select Open->DVD from folder. 
 * Ported logwindow.h, logwindow.cpp and logwindowbase.ui. This is the widget used to display the mplayer/smplayer logs. 
 * Ported (partially) filepropertiesdialog.h, filepropertiesdialog.cpp, and filepropertiesdialogbase.ui. Still using Q3ListBox. This dialog appears with Options->View info and properties.

[http://www.ifpost.com/ifpost/download/9836469565994897](http://www.ifpost.com/ifpost/download/9836469565994897)

---

### Post by disturbedite on 2007-06-28
**Version 0.5.29-qt4-0628 **
 * Updated the Ukrainian and Russian translations. 
 * Ported (partially) inforeader.h and inforeader.cpp. Now using QLists instead of Q3ValueLists. Still using Q3Process though. 
 * Ported eqslider.h, eqslider.cpp, eqsliderbase.ui, verticaltext.h, verticaltext.cpp, videoequalizer.h and videoequalizer.cpp. All of this is the video equalizer. 
 * Ported seekwidget.h, seekwidget.cpp and seekwidgetbase.ui. This provides the widget that allows the changing of the seeking times in Preferences->Interface. 
 * Ported preferencesdialogbase.ui and made some small changes in preferencesdialog.h/preferencesdialog.cpp to make it compile. Still using a lot of Qt 3 widgets. This is the preferences dialog and it's huge. I'll change them later because I thought about splitting it into modules. 
 * Ported mplayerwindow.cpp and mplayerwindow.h. This is the widget used for the video.

[http://www.ifpost.com/ifpost/download/2456810320757804](http://www.ifpost.com/ifpost/download/2456810320757804)

---

### Post by disturbedite on 2007-06-29
NOTE:
it appears that rvm forgot to bump the version number/build date in the about dialog.  don't fret, it is indeed build/version 062***9***[I].
[/I][B]
Version 0.5.29-qt4-0629-1 [/B]
 * Updated the pt_PT translation. 
 * filepropertiesdialog.cpp: replaced the Q3ListBox with QListWidget. So this file is completely ported. 
 * mplayerprocess: changed the Qt headers but still using Q3Process. 
 * Ported global.h and global.cpp. 
 * The link in the "about" dialog at last works (if Qt >= 4.2). 
 * Fix: use setAutoFillBackground() only if Qt >= 4.1. 
 * Now the option "Don't repaint the video background" is checked by default in linux.

[http://www.ifpost.com/ifpost/download/2972012717992538](http://www.ifpost.com/ifpost/download/2972012717992538)

---

### Post by disturbedite on 2007-06-30
NOTE:
thanks for the deb creation script rvm!  makes life easier.
[B]
Version 0.5.29-qt4-0629-2[/B]
* Updated the German translation.
* Created the file create_deb.sh for Ubuntu users. If you run it, it will create a deb package.
* Started to write the new preferences dialog. When finished it will look like the old one, but internally each section will be a separate widget, so it will be easier to maintain. This new dialog is hidden, if you want to see it press Ctrl+6.

[http://www.ifpost.com/ifpost/download/3709190470514274](http://www.ifpost.com/ifpost/download/3709190470514274)

---

### Post by disturbedite on 2007-07-01
Note:
i missed a few builds, as you can see in the changelog...

**Version 0.5.29-qt4-0701-1**
* Updated the Ukrainian, German, Russian and Polish translations.
* The interface section is available in the preferences dialog. I added this section first because I needed to test the language and iconset change.
[B]
Version 0.5.29-qt4-0630-2[/B]
* The first two sections (General and Drives) in the new preferences dialog should now be fully functional, although testing is needed. I very easily could have forgotten to copy some code from the old dialog and some options might not work as expected. So testing would be very appreciated.
* Switched to the new Qt 4 automatic connections in FilePropertiesDialog.
[B]
Version 0.5.29-qt4-0630-1[/B]
* Made InfoReader a little bit smarter. Now it calls mplayer on its own, and PreferencesDialog and FilePropertiesDialog ask it for the info (available drivers, codecs,etc.), so this is not done anymore by BaseGui.
* Now the new preferences dialog is used if compiled with #define NEW_PREFERENCES_DIALOG 1 (in config.h). Otherwise the old dialog will be used to keep things working.

[http://www.ifpost.com/ifpost/download/7792360574105915](http://www.ifpost.com/ifpost/download/7792360574105915)

---

### Post by disturbedite on 2007-07-02
**Version 0.5.29-qt4-0701-2**
* Updated the German translation.
* The performance section is now available in the preferences dialog.
* Added the keyboard & mouse section too.
* Added the subtitle section. And now using the new QFontComboBox to select the system font. BTW, I've just realized that the QFontComboBox was added in Qt 4.2. So that means that now SMPlayer requires at least Qt 4.2.

[http://www.ifpost.com/ifpost/download/6647905091501210](http://www.ifpost.com/ifpost/download/6647905091501210)

---

### Post by gebeleizis on 2007-07-02
I am trying to download your files (wich use to work fine) and Firefox displays this:
> 
Warning: mysql_query() [function.mysql-query]: Access denied for user 'www-data'@'localhost' (using password: NO) in /var/www/upload/ifpost.php on line 71

Warning: mysql_query() [function.mysql-query]: A link to the server could not be established in /var/www/upload/ifpost.php on line 71

Warning: Cannot modify header information - headers already sent by (output started at /var/www/upload/ifpost.php:71) in /var/www/upload/ifpost.php on line 72

Warning: Cannot modify header information - headers already sent by (output started at /var/www/upload/ifpost.php:71) in /var/www/upload/ifpost.php on line 73
! debian-binary 1183396013 0 0 100644 4 ` 2.0 control.tar.gz 1183396013 0 0 100644 2359 ` &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;n&#65533;&#65533;k&#65533;+:r&#65533;$&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;&#65533;,&#65533;&#65533;C&#65533;}&#65533;&&#65533;&#65533;&#65533;Y&#65533;&#65533;R&#65533;&#65533;&#65533;&#985;Y&#65533;&#65533;&#65533;&#65533;/&#65533;v&#65533;3} &#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>8&#65533;3f&#65533;&#65533;x&#65533;s&#65533;.&#65533;&#65533;R*.&#65533;&#444;s&#65533;=`&#65533;&#65533;&#65533;06&#65533;;&#65533;tm;&#65533;&#65533;}o&#65533;&#65533;&#65533;&#65533;u&#65533;&#874;~&#65533;&#65533;K'&#65533;&#65533;&#65533;q&#65533; ...and lots of this stuff and then just crashes. 
Whats up with this?

---

### Post by disturbedite on 2007-07-02
you're the first to report a problem.
which architechure are you on (x86 or 64bit?) and which version are you using?

i test ff trunk (3.0) & have no problem...

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9a7pre) Gecko/20070702 Minefield/3.0a7pre - Build ID: 2007070209

---

### Post by Shinoda on 2007-07-03
> **disturbedite said:**
> you're the first to report a problem.Actually someone else at my thread complained about downloads being corrupted a few days ago. I then tried them myself with Swiftfox 2.0.0.4 x86 and the same as gebeleizis described (except for the crashing) happens to me for any file from IFPost &#8212; which is nevertheless odd since they used to work fine &#8212;, so I just switched to Content-Type at least for the time being.

---

### Post by disturbedite on 2007-07-03
eh.  as i said, i use ff trunk and have no problem.  but just in case, i will upload to content-type as well.

---

### Post by disturbedite on 2007-07-03
NOTE:
don't know whats new with this build (0703) since rvm didn't post a changelog.  but i did miss a few builds as you can see...
[B]
Version 0.5.29-qt4-0702-2 [/B]
 * Updated the Polish translation. 
 * Added the "whatsthis" help again to the preferences dialog. So now the preferences dialog recovers whole functionality. 
 * And something new: the "help" button works. It will display all "whatsthis" messages in a single page. There's not help for everything yet. 
 * Moved the old preferences stuff to old-preferences directory. Now the old preferences dialog is not compiled any more. 
 So the new preferecences dialog is mostly finished. 
 
** Version 0.5.29-qt4-0702-1 **
 * Updated the German and Polish translations. 
 * The advanced section is also available in the preferences dialog. 
 So now all sections are available again. Although it looks like before, the preferences dialog has completely been rewritten, so there could be bugs. So please test it, and report if you find any problem. 

[http://www.content-type.com/1986542724/smplayer_0.5.29-qt4-0703_i386.deb.htm](http://www.content-type.com/1986542724/smplayer_0.5.29-qt4-0703_i386.deb.htm)
(changed to content-type for those of you that are experiencing problems downloading the package(s) w/ firefox.  :roll: [even tho you could use another browser to download the package(s)].;)

---

### Post by disturbedite on 2007-07-05
**Version 0.5.29-qt4-0704**
* Added a bat file (compile_windows.bat) to make compilation on windows easier.
* Updated the German and Japanese translations.
* Renamed some ui files.
* Using a QDialogButtonGroup in the about dialog now.
* Try to load the qt translation file. This way texts directly generated by the Qt library (ok and cancel buttons, the file dialog, etc.) will also be translated (if a translation is available for your language). Currently it will try to load the *.qm file from the Qt translation path (querying QLibraryInfo). It should work on linux but I don't know if it will work on windows.
Note: currently the language for these translations can't be changed at run-time. 

[http://www.content-type.com/-193276659/smplayer_0.5.29-qt4-0704_i386.deb.htm](http://www.content-type.com/-193276659/smplayer_0.5.29-qt4-0704_i386.deb.htm)

---

### Post by disturbedite on 2007-07-06
**Version 0.5.29-qt4-0705**
* Now the qt translation file is loaded too when the user changes the language in the preferences dialog (unfortunately it seems that the strings in buttons are not updated at runtime, so you'll need to restart the program to have a full translation).
This is what it will be done:
First it will try to load the qt translation from the Qt translation folder, if that fails then it will try to load it from the smplayer translation folder. This would allow smplayer to use non official Qt translations for other languages, without having to install them in the Qt directories.
In Windows it will just look for the translations in the smplayer translation folder, as most windows users won't have Qt installed.
* Made some changes in the actions editor to avoid corruption of the key shortcuts. The corruption happened because the shortcuts were translated (for example, the shortcut "Ctrl+Right" was translated to "Ctrl+Derecha" in Spanish) but when a language change occurs at runtime, the new language don't understand the shortcuts. This has been fixed not allowing the shortcuts to be translated.
* Using a QDialogButtonGroup in the file properties dialog. The QDialogButtonBox shows the Ok, Cancel... buttons in different ways according to the current style. The best way to see the difference is to use the Cleanlooks style: smplayer -style cleanlooks
* Updated the Ukrainian, German, Polish and Russian translations.

[http://www.content-type.com/-1327629130/smplayer_0.5.29-qt4-0705_i386.deb.htm](http://www.content-type.com/-1327629130/smplayer_0.5.29-qt4-0705_i386.deb.htm)

---

### Post by disturbedite on 2007-07-07
**Version 0.5.29-qt4-0706-2**
* New feature: on startup smplayer will try to create two directories: $HOME/.smplayer and $HOME/.smplayer/screenshots
Now the configuration file will be stored in $HOME/.smplayer/ If you want to keep your configuration just copy $HOME/.config/RVM/smplayer.ini to $HOME/.smplayer/
And obviously the directory $HOME/.smplayer/screenshots will be used to store the screenshots (this also fulfills an old request).
This change also affects Windows! Not compiled yet on Windows but according to the Qt docs the directories will be C:/Documents and Settings/Username/.smplayer and C:/Documents and Settings/Username/.smplayer/screenshots
[B]
Version 0.5.29-qt4-0706-1[/B]
* Started to use the new (and more complicated) method in Qt 4 for retranslating the texts. While doing this I have found a bug: the vertical texts in the video equalizer doesn't appear when the language is Japanese, Chinese or Georgian (it worked with Qt 3 but it seems that it never worked with Qt 4). Until I find a fix, as a work around I added a tooltip so the user could know what each control is for.
* The problem with texts in buttons in QDialogButtonGroups, which are not retranslated, seems to be fixed in Qt 4.3. I'm still using Qt 4.2.3 so I added a work around for Qt 4.2.
* Added "buddies" (or key accelerators) in the Advanced section in preferences. I'm afraid this breaks the translations but it's something that has to be done. I'll add them in the other sections too.

[http://www.content-type.com/1052450490/smplayer_0.5.29-qt4-0706-2_i386.deb.htm](http://www.content-type.com/1052450490/smplayer_0.5.29-qt4-0706-2_i386.deb.htm)

---

### Post by disturbedite on 2007-07-09
**Version 0.5.29-qt4-0708** 
 * Updated the zh_CN, German and Turkish translations. 
 * Bug fix: now the info about the demuxer, audio and video codec are updated  after a restart of the mplayer process. 
 * Ported the shortcuts' editor, by using a QTableWidget instead of a Q3Table. 
 This has been a very hard task (and in fact it's not completely finished yet), as there are a lot of differences between Q3Table and QTableWidget. Moreover QTableWidget is more prone to crashes as it requires the use of pointers all around. 
 * Updated the shorcuts/default.keys as the previous one lacked the action "quit".

[http://www.content-type.com/585835751/smplayer_0.5.29-qt4-0708_i386.deb.htm](http://www.content-type.com/585835751/smplayer_0.5.29-qt4-0708_i386.deb.htm)

---

### Post by disturbedite on 2007-07-10
**smplayer-themes Version 0.1.3**
* Added the Tango theme by Yurkovsky Andrey
* Removed the Oxygen theme as I don't know the license of the icons.  (in other words, don't install if you use the oxygen theme).

[http://www.content-type.com/-679932234/smplayer-themes_0.1.3_all.deb.htm](http://www.content-type.com/-679932234/smplayer-themes_0.1.3_all.deb.htm)

**Version 0.5.29-qt4-0709** 
 * The priority option in preferences was broken. Fixed. 
 * More changes in the action editor. 

[http://www.content-type.com/591976946/smplayer_0.5.29-qt4-0709_i386.deb.htm](http://www.content-type.com/591976946/smplayer_0.5.29-qt4-0709_i386.deb.htm)

---

### Post by disturbedite on 2007-07-12
**Version 0.5.29-qt4-0710 **
 * Updated the Russian translation. 
 * Now changing a key shortcut in the actions' editor is much easier. Now you double click or press enter on a shortcut (you can do it in any column) and a dialog will appear to ask you for the new shortcut. In this dialog you press the key or combination of keys that you want to assign to the shortcut. If you want to delete, just click on the Clear button. 
 Note: this has been done by using some code from Edyuk ([http://www.edyuk.org](http://www.edyuk.org)) 
 Note 2: it's possible that some keys are not caught properly. In that case report it. 

[http://www.content-type.com/2021003920/smplayer_0.5.29-qt4-0710_i386.deb.htm](http://www.content-type.com/2021003920/smplayer_0.5.29-qt4-0710_i386.deb.htm)

---

### Post by disturbedite on 2007-07-14
**Version 0.5.29-qt4-0714-1**
* Updated the German translation.
* Tried to fix the AltGr issue but I have also realized that the Tab key can't be entered so I think it's best to go back to the old method. Retrieved the old intro text for preferences.
* make clean deletes the file src/Makefile, as this file is generated by qmake.[B]

Version 0.5.29-qt4-0713[/B] 
 * Updated the German, Polish and Ukrainian translations. 
 * In the action editor the AltGr key is not detected properly. So it's not possible to enter keys such as "#" or "@" as shortcuts. Until I fix it, I'm going back to the old method to enter keys.

[http://www.content-type.com/2060662452/smplayer_0.5.29-qt4-0714-1_i386.deb.htm](http://www.content-type.com/2060662452/smplayer_0.5.29-qt4-0714-1_i386.deb.htm)

---

### Post by disturbedite on 2007-07-18
**Version 0.5.29-qt4-0716 **
 * Updated the Ukrainian, Japanese and Russian translations. 
 * Started to write myprocess class. But this is done separately in a testing program. 
 * Fix: now reading the info about video, audio drivers, codecs and demuxers is done in a language independent way (it looks for tags like "ID_VIDEO_OUTPUTS" instead of English text).

[http://www.content-type.com/-550999966/smplayer_0.5.29-qt4-0716_i386.deb.htm](http://www.content-type.com/-550999966/smplayer_0.5.29-qt4-0716_i386.deb.htm)

---

### Post by disturbedite on 2007-07-19
**Version 0.5.29-qt4-0718**
 * Updated the Polish and German translations. 
 * Now inforeader and mplayerprocess uses the new myprocess. This is an important change. MyProcess is a class which inherits from QProcess (the Qt4 one, of course, although it provides some compatibility functions, like addArgument(), otherwise I would have to make a lot of changes in core.cpp). It provides a special working mode for Windows: the output of mplayer is sent to a temporary file and read from it. I hope this will improve performance under Windows.

  [http://www.content-type.com/-1171451529/smplayer_0.5.29-qt4-0718_i386.deb.htm](http://www.content-type.com/-1171451529/smplayer_0.5.29-qt4-0718_i386.deb.htm)

---

### Post by disturbedite on 2007-07-20
**Version 0.5.29-qt4-0720**
 * Fix with the myprocess stuff. A connection was not made. This could make it so that the screensavers weren't turned on. 
 * Some changes in mplayerwindow. Now it knows when a video starts or stops so it could manage clearingt the video background or not. This was previously done in core. It also has a fix, now the video background stops repainting just *before* the mplayer process starts, instead of doing it when it already has started. This could fix that the video window could still get black sometimes. 
 * Shortcut editor: the new dialog for editing key shortcuts comes back. The problems are not fixed, you can't enter keys like "Tab" yet except for those cases I've added a button "Capture". When toggled it will try to capture the shortcut (as before), otherwise you can freely edit the shortcut as a regular text.

[http://www.content-type.com/-879302900/smplayer_0.5.29-qt4-0720_i386.deb.htm](http://www.content-type.com/-879302900/smplayer_0.5.29-qt4-0720_i386.deb.htm)

---

### Post by disturbedite on 2007-07-23
**Version 0.5.29-qt4-0722**
* Updated the Romanian, Russian and Ukrainian translations.
* Bug fix: exit from fullscreen when playing an audio file.
* Bug fix: the end of file is signaling once the process has finished.
* The info window prints the absolute file path instead of the directory only.
* Bug fix: the size of the main window might be much bigger than it should be when playing a file passed through command line. I think this is fixed now.
The problem was that the file begins to play before the main window is shown. Anyway this part of the code is a mess and has to be fixed.

[http://www.content-type.com/-916917176/smplayer_0.5.29-qt4-0722_i386.deb.htm](http://www.content-type.com/-916917176/smplayer_0.5.29-qt4-0722_i386.deb.htm)

---

### Post by disturbedite on 2007-07-24
**Version 0.5.29-qt4-0723**
 * Updated the German, Polish and Ukrainian translations. 
 * Started to port the network stuff (for the single instance). Implemented a blocking client. This makes things a lot easier. Previously this was done in a main window, which waited hidden until knowing if it can show (no other running instance) or quit. Now the connection to another instance is done in main.cpp with 2 or 3 lines or code, and before creating the main window. This is *much faster*. Now the file passed to the running instance starts to play almost instantaneously. 
 The code (myclient.h, myclient.cpp) is quite simple and does few checks, and I don't even know if it is a correctly implemented. I'll try to improve it (this is the first time I've use QTcpSocket, and the 2nd time I've done something relative to networking). 
 There's a problem, though. For simplicity the main window always shows. This is a problem if you use to leave smplayer running in the system tray for the whole session, as when you enter in the next session the main window of smplayer will be visible. I'll try to fix it in the future.

[http://www.content-type.com/1457466413/smplayer_0.5.29-qt4-0723_i386.deb.htm](http://www.content-type.com/1457466413/smplayer_0.5.29-qt4-0723_i386.deb.htm)

---

### Post by disturbedite on 2007-07-24
**Version 0.5.29-qt4-0724**
 * Some fixes in myclient. Now uses UTF-8 to encode the texts, the timeout is set to 200 ms. 
 Anyway I'm not sure this is properly done. For instance if it tries to read a line from the server just before sending the data, only the first line is sent, the rest is lost. 
 * Fix: if you don't pass any file to the 2nd instance, it won't show. 
 * Fix: tray icon: it will remember again if the main window was hidden on startup.

[http://www.content-type.com/594607528/smplayer_0.5.29-qt4-0724_i386.deb.htm](http://www.content-type.com/594607528/smplayer_0.5.29-qt4-0724_i386.deb.htm)

---

### Post by disturbedite on 2007-07-25
NOTE:
i reverted to uploading to ifpost temporarily cuz content-type won't upload for some reason with konqueror or ff.

**Version 0.5.29-qt4-0724-2**
* More fixes in myclient.cpp.
* Fix: when a video finished and a 2nd one starts to play from the playlist, the setting for not repainting the window background was ignored.

[http://www.ifpost.com/ifpost/download/9409517366251903](http://www.ifpost.com/ifpost/download/9409517366251903)

---

### Post by disturbedite on 2007-07-26
**Version 0.5.29-qt4-0725**
 * Properly fixed a problem with a signal. 
 * Got rid of the QTextStream in myclient.cpp. 
 * By user request: added a new option in Preferences->Interface: Change volume on every file. If checked SMPlayer will remember the volume of every file, and will be restored when played again. For new files the default volume will be used. That was the normal behavior until now. The new thing is if you uncheck it. In this case SMPlayer will never change the volume when a file is loaded. Problem: on startup SMPlayer won't know the current volume value, the volume slider will be wrong. 

[http://www.content-type.com/1062184916/smplayer_0.5.29-qt4-0725_i386.deb.htm](http://www.content-type.com/1062184916/smplayer_0.5.29-qt4-0725_i386.deb.htm)

---

### Post by disturbedite on 2007-07-27
**Version 0.5.29-qt4-0727**
 * Updated the Japanese, Russian, German, Ukrainian and French translations. 
 * Set the new option dont_change_volume to false as default, as it seems that mplayer in windows starts to play all videos with a very high volume. 
 * If the name of the executable (without extension) is "smplayer_portable" then the option -ini-path will be activated (that means that smplayer will look for the config file in the app path). 
 * The volume icon in Preferences->Interface is hidden so the dialog is not so wide. 
 * Some changes in the widgets of Preferences->Interface. Enabled the changing of style again. 
 * I started to document some of the classes for doxygen.

[http://www.content-type.com/96088280/smplayer_0.5.29-qt4-0727_i386.deb.htm](http://www.content-type.com/96088280/smplayer_0.5.29-qt4-0727_i386.deb.htm)

---

### Post by disturbedite on 2007-07-30
**Version 0.5.29-qt4-0730**
 * Updated the French translation. 
 * Some small, but important fixes for Windows. 
 * New option for command line that I think could be very useful: -action 
 This option passes the specified action to an already running instance. For instance, you're watching a video in smplayer, then you type: 
 smplayer -action pause and the video will be paused. 
 smplayer -action fullscreen will toggle the video to fullscreen. 
 This will allow the user to control smplayer with a remote control. You can see a list of all available actions in "Preferences->Keyboard and mouse". Under the "Name" column in the shortcut editor there is all the actions' names. 
 When using -action all other parameters (except ini-path) are ignored. So it you want to open a movie and enter in fullscreen, this is NOT valid: 
 smplayer movie.avi -action fullscreen 
 But you can do it in two steps: 
 smplayer movie.avi 
 smplayer -action fullscreen 
 The exit code will be 0 if the -action option is successful and -1 if there's an error.

[http://www.content-type.com/199117614/smplayer_0.5.29-qt4-0730_i386.deb.htm](http://www.content-type.com/199117614/smplayer_0.5.29-qt4-0730_i386.deb.htm)

---

### Post by disturbedite on 2007-08-02
**Version 0.5.29-qt4-0801**
* Updated the German translation.
* (Windows) Added some code to prevent the monitor from turning off while media is playing. (Not tested yet).
* Disabled some code in helper.cpp as it's not needed anymore.
* Renamed preferencesdialog2 to preferencesdialog.

[http://www.content-type.com/-1293437936/smplayer_0.5.29-qt4-0801_i386.deb.htm](http://www.content-type.com/-1293437936/smplayer_0.5.29-qt4-0801_i386.deb.htm)

---

### Post by disturbedite on 2007-08-03
**Version 0.5.29-qt4-0803**
* Updated the German translation.
* Try to keep pause after taking a screenshot.
* Moved options for volume from Preferences->Interface to General->Video & audio (which required a redesign of the Interface section).
* Hid the option "Use -subfont" as it seems that new SVN releases of mplayer don't require it. Also that option is not documented in the manpage.

[http://www.content-type.com/-473277141/smplayer_0.5.29-qt4-0803_i386.deb.htm](http://www.content-type.com/-473277141/smplayer_0.5.29-qt4-0803_i386.deb.htm)

---

### Post by disturbedite on 2007-08-05
**Version 0.5.29-qt4-0804**
* Updated the German and Ukrainian translations.
* The message "Screenshot taken..." is not displayed in the OSD if the video is paused. This is to prevent the video advancing one frame.
* Some changes in the about dialog.
* Changes in some ui files.
* Added shortcuts in the Interface and Mouse sections in Preferences.

[http://www.content-type.com/-1324761633/smplayer_0.5.29-qt4-0804_i386.deb.htm](http://www.content-type.com/-1324761633/smplayer_0.5.29-qt4-0804_i386.deb.htm)

---

### Post by disturbedite on 2007-08-07
**Version 0.5.29-qt4-0807 **
 * Updated the Chinese (zh_CN), Ukrainian, German, Polish and French translations. 
 * Removed obsolete translations in the *.ts files. 
 * Compiled again without the option to change style. It still causes crashes.

[http://www.content-type.com/1204042380/smplayer_0.5.29-qt4-0807_i386.deb.htm](http://www.content-type.com/1204042380/smplayer_0.5.29-qt4-0807_i386.deb.htm)

---

### Post by disturbedite on 2007-08-08
**Version 0.5.29-qt4-0808**
* Added the updated qt_fr.qm sent by Kud Gray.
* Now "make clean" will only delete the smplayer_*.qm files in the translation folder, to keep the qt_*.qm ones.
* (Linux) Try to load first the qt_*.qm from the smplayer translation path, and if that fails then try to load from the Qt translation path (previosly it was the opposite).
* Ported timeslider.h, timeslider.cpp and some small changes in other files.
* Now the moc_*.cpp files are included in the *.cpp files. This reduces the compilation time. In my computer, previosly it took about 2 minutes, now it takes 1:30. This also revealed serious mistakes in some headers.
* Added shortcuts in the General, Drives and Performance sections in preferences. (Translators are gonna "love" this change...)

[http://www.content-type.com/2091667628/smplayer_0.5.29-qt4-0808_i386.deb.htm](http://www.content-type.com/2091667628/smplayer_0.5.29-qt4-0808_i386.deb.htm)

---

### Post by disturbedite on 2007-08-09
**Version 0.5.29-qt4-0809**
* Updated the German, Polish, Russian and Ukrainian translations.
* I started to port the playlist. Ported things: the toolbar, the actions, and the popup menu. (See the "broken things" above).
Other minor changes: Q3ValueList -> QList, Q3TextStream -> QTextStream (I hope not, but there's the possibility that something has broken).
Now the playlist is not a QMainWindow, but a QWidget (previously I had to use a QMainWindow because in Qt 3 is not possible to add a toolbar to a normal widget, now at last I can do what I initially wanted).
You'll see that now the playlist looks slightly different.
Still to port: the list view (which will be the hardest part) and drag&drop.
* Fixed a bug in the playlist. The "length" field of the items was incorrectly read when loaded from the config file.

[http://www.content-type.com/688307146/smplayer_0.5.29-qt4-0809_i386.deb.htm](http://www.content-type.com/688307146/smplayer_0.5.29-qt4-0809_i386.deb.htm)

---

### Post by disturbedite on 2007-08-10
**Version 0.5.29-qt4-0810 **
 * (Playlist) Using now a QTableWidget. This is the area where the items of the list are shown. Please test if everything is ok (moving items, selecting items, deleting selected items...). 
 Still have to port the drag&drop code. 
 * (Windows) When changing the audio track, mplayer doesn't keep the volume (it's louder). Added a workaround, smplayer will restore the volume just after the change of the audio track.

[http://www.content-type.com/-287382263/smplayer_0.5.29-qt4-0810_i386.deb.htm](http://www.content-type.com/-287382263/smplayer_0.5.29-qt4-0810_i386.deb.htm)

---

### Post by disturbedite on 2007-08-11
**Version 0.5.29-qt4-0811**
 * (Playlist) Ported the drag&drop. Easier than expected, less code than with Qt 3 and no extra code needed to support Firefox. 
 * Some small changes in playlist: no alternating row colors (doesn't look good in Windows), bigger icons in the table. 
 * Finished porting of the playlist. 
 * Internal changes in core.

[http://www.content-type.com/990678836/smplayer_0.5.29-qt4-0811_i386.deb.htm](http://www.content-type.com/990678836/smplayer_0.5.29-qt4-0811_i386.deb.htm)

---

### Post by disturbedite on 2007-08-12
**Version 0.5.29-qt4-0813**
* Updated the Romanian translation.
* Added a new option for the config file: restore_pos_after_fullscreen (in section [Preferences]). If its value is "true" then the main window will save the current position on screen and restore it again when exiting from fullscreen mode. The default value is "true" for Windows and "false" for Linux. Change it if the main window moves up or down after exiting from fullscreen mode.
* (By user request) Added a new option in Preferences->Interface: "Remember position and size" (of the main window). Checked by default.
* (By user request) Added two new options in Preferences->General->Video & audio: "Direct rendering" and "Double buffering".

[http://www.content-type.com/522684037/smplayer_0.5.29-qt4-0813_i386.deb.htm](http://www.content-type.com/522684037/smplayer_0.5.29-qt4-0813_i386.deb.htm)

---

### Post by disturbedite on 2007-08-14
**Version 0.5.29-qt4-0814**
 * Updated the French, German and Polish translations. 
 * Changed the behavior of "Use postprocessing" and "Volume normalization" in Preferences->General. Previously if you checked "Use postprocessing" for instance, then all videos would use postprocessing, no matter the setting in Video->Filter->Postprocessing. Now this specifies the default setting for new videos. If checked, all new videos opened will have the option Video->Filter->Postprocessing enabled but you can disable it if you want. Previously this wasn't possible. I think this behavior is more consistent. 
 * Ported images.h/images.cpp and moved to the new resource system. Right now the only thing still to be ported is the main window.

[http://www.content-type.com/-77016616/smplayer_0.5.29-qt4-0814_i386.deb.htm](http://www.content-type.com/-77016616/smplayer_0.5.29-qt4-0814_i386.deb.htm)

---

### Post by disturbedite on 2007-08-15
**Version 0.5.29-qt4-0815**
* Updated the Traditional Chinese, German, Ukrainian, Russian and Simplified Chinese translations.
* The icons in File properties->Info didn't appear. Fixed.
* Renamed the icons starting with letter "x". For example, "xnext.png" is now "next.png". Anyway if an icon with the new name is not found it will still look for an icon with the old name to keep compatibility with the icon's themes.

[http://www.content-type.com/1649393973/smplayer_0.5.29-qt4-0815_i386.deb.htm](http://www.content-type.com/1649393973/smplayer_0.5.29-qt4-0815_i386.deb.htm)

---

### Post by disturbedite on 2007-08-16
NOTE:
this build doesn't work for me (as of yet) but i just thought i'd post it in case it does work for others.  obviously, if you install it and it doesn't work, then downgrade to yesterday's build.

**Version 0.5.30-qt4-0816**
* Started to port the main window. There's a lot of things to do. Today I've just made it compile and made a few other changes to make it show the toolbars properly. WARNING: there might be something broken.
* The action's editor shows now QActions, instead of Q3Actions, as the main window now uses QActions.

[http://www.content-type.com/738006149/smplayer_0.5.30-qt4-0816_i386.deb.htm](http://www.content-type.com/738006149/smplayer_0.5.30-qt4-0816_i386.deb.htm)

---

### Post by disturbedite on 2007-08-16
NOTE:
the bug that broke smplayer has been fixed.  its the second bullet on this build changelog.

**Version 0.5.30-qt4-0817**
 * Updated the French translation. 
 * Actions' editor: only save or load actions with a name.
 * Ported the floating control. 
 * baseguiplus and defaultgui almost ported. 
 * A few changes in basegui. Still a lot of work to do with the menus.

[http://www.content-type.com/1244865399/smplayer_0.5.30-qt4-0817_i386.deb.htm](http://www.content-type.com/1244865399/smplayer_0.5.30-qt4-0817_i386.deb.htm)

---

### Post by disturbedite on 2007-08-18
NOTE:
sorry for the delay but content-type was down earlier so i had to wait to upload this build's package.

**Version 0.5.30-qt4-0818**
 * Updated the Ukrainian translation. 
 * Continuing with the boring task of porting the menus. 
 * Created myactiongroup, to ease the creation of menus where only one of the options should be checked. 
 * Now the menu Options->OSD uses this new system. And the good thing is that options can have shortcuts.

[http://www.content-type.com/-830873003/smplayer_0.5.30-qt4-0818_i386.deb.htm](http://www.content-type.com/-830873003/smplayer_0.5.30-qt4-0818_i386.deb.htm)

---

### Post by disturbedite on 2007-08-20
**Version 0.5.30-qt4-0819**
* Updated the Japanese translation.
* Undone something with submenus. I realized there's an easy way.
* Ported Video->Denoise.
* Ported Video->Size. Now you can add shortcuts for these options. But unfortunately an old problem previously fixed comes back: if you select an already selected option it will do nothing. That means that if you resize the window manually and then select Video->Size->100% it won't resize to the original size. I'll try to fix it in the future.
* Ported Video->Deinterlace.
* Ported Audio->Channels.
* Ported Audio->Stereo mode.
* Ported Video->Aspect ratio.
* Added the denoise filters into the Video->Filters menu.

[http://www.content-type.com/-378815405/smplayer_0.5.30-qt4-0819_i386.deb.htm](http://www.content-type.com/-378815405/smplayer_0.5.30-qt4-0819_i386.deb.htm)

---

### Post by disturbedite on 2007-08-21
**Version 0.5.30-qt4-0820**
* Updated the Romanian, German, Polish and Ukrainian translations.
* Now the maximum value for volume is 100 instead of 99.
* Ported Open->Recent files. And some fixes: now if the list is empty the submenu won't appear. You can also set the max. number of items in the list to 0 in Preferences->Interface.
* Ported the rest of menus: audio and subtitle track selection, title, chapter and angle submenus. I left this for the end for a reason: it was to be the hardest part and very error-prone. So test it, it wouldn't be strange if there are crashes or weird things. BTW, the angle submenu is completely untested (I don't have any multi-angle DVDs). 

[http://www.content-type.com/1644851182/smplayer_0.5.30-qt4-0820_i386.deb.htm](http://www.content-type.com/1644851182/smplayer_0.5.30-qt4-0820_i386.deb.htm)

---

### Post by disturbedite on 2007-08-22
**Version 0.5.40**
 * Ported the drag&drop in main window. 
 * The file properties dialog was still using a Q3GroupBox. Fixed. Now smplayer won't be linked anymore to the qt3support library.
 * Ported the code to embed the playlist in the main window. It's not compiled by default because there are still some things to fix but you can try it, it works better than before (there's even an animation when you move the playlist to the top area). To do it change the value of DOCK_PLAYLIST to 1 in config.h before compiling. (Note:  this new experimental feature was not enabled during compilation).
 * Reduced the number of warnings when compiling with QT3_SUPPORT_WARNINGS. This change is very error-prone.

[http://www.content-type.com/45534694/smplayer_0.5.40_i386.deb.htm](http://www.content-type.com/45534694/smplayer_0.5.40_i386.deb.htm)

---

### Post by disturbedite on 2007-08-23
**Version 0.5.41**
* Updated the Ukrainian and Russian translations.
* Fixed the problem with the Video->Size menu. All options will work now no matter the previous selection.
* Some changes in Install.txt, just to mark some obsolete sections and make clear that it can only be compiled with Qt >= 4.2.

[http://www.content-type.com/-834502109/smplayer_0.5.41_i386.deb.htm](http://www.content-type.com/-834502109/smplayer_0.5.41_i386.deb.htm)

---

### Post by disturbedite on 2007-08-24
**Version 0.5.42**
* Serious bug: a lot of actions were missing in the actions' editor. Fixed.
* More improvements with the playlist embedded in the main window: now it should be properly hidden/shown when toggling compact and fullscreen mode, and when clicking on the systray icon. Also the playlist button in toolbar (and menu) should be updated when the playlist is closed by clicking on its close button. But you'll see that now the main window is not resized when the playlist is shown or hidden. I left this problem for the end (it's not trivial). Anyway you can press CTRL-1 to force a resize.
This code is not compiled by default yet. If you want to see it, change the value of DOCK_PLAYLIST to 1 in config.h before compiling.  (Note: i still did not enable this feature yet since its still experimental).

[http://www.content-type.com/-880853439/smplayer_0.5.42_i386.deb.htm](http://www.content-type.com/-880853439/smplayer_0.5.42_i386.deb.htm)

---

### Post by disturbedite on 2007-08-26
**Version 0.5.43**
 * Updated the Italian translation. 
 * Small fix for Windows in the fullscreen code. 
 * Removed the "&" characters in the description of the actions in the actions' editor. 
 * Now using less deprecated functions.

[http://www.content-type.com/2002054107/smplayer_0.5.43_i386.deb.htm](http://www.content-type.com/2002054107/smplayer_0.5.43_i386.deb.htm)

---

### Post by disturbedite on 2007-08-27
**Version 0.5.44**
 * Updated the Polish, German and French translations. 
 * When trying to stop a video, the mplayer process will be killed if it doesn't finish within 3 seconds. 
 * New dialog to enter a URL (the playlist check doesn't work yet). 
 * Don't load actions from playlist to the actions' editor as it seems they are already there from the main window (in Qt 4.3 they appear twice).

[http://www.content-type.com/1989655525/smplayer_0.5.44_i386.deb.htm](http://www.content-type.com/1989655525/smplayer_0.5.44_i386.deb.htm)

---

### Post by disturbedite on 2007-08-28
**Version 0.5.45**
 * Updated the Ukrainian and German translations. 
 * The playlist check in the open URL dialog works. If checked the option -playlist will be added to the mplayer command line. (Internally some text will be appended to the URL, so smplayer can recognize it. This may seem ugly (and it is) but allows to add the URL to a playlist or to the recent files menu, and it will still work). 
 * Added an icon to the open URL dialog (url_big.png). 
 * Added two options for the config file: enable_audiocd_on_windows and enable_vcd_on_windows. It seems that mplayer on Windows doesn't have support for VCDs and Audio CDs (at least not the build supplied with smplayer). Setting these options to "true" will enable the entries in the open menu.

[http://www.content-type.com/-475114717/smplayer_0.5.45_i386.deb.htm](http://www.content-type.com/-475114717/smplayer_0.5.45_i386.deb.htm)

---

### Post by disturbedite on 2007-08-29
**Version 0.5.46**
* Added the option -playlist for command line. This option should be prepended in front of a filename (URL or whatever). This option will make mplayer treat the file as a playlist. This option has nothing to do with smplayer's playlist! In fact smplayer won't have any control over the playlist at all. For smplayer it will be treated like a single file.
* Added the option -help for command line. It will show a help message.
BTW, the translators will have a challenge, as keeping the formatting is not easy. (Take a look at the Spanish translation).
* Added the option -close-at-end command line. The main window will be closed when the file/playlist finishes.

[http://www.content-type.com/-2055733794/smplayer_0.5.46_i386.deb.htm](http://www.content-type.com/-2055733794/smplayer_0.5.46_i386.deb.htm)

---

### Post by disturbedite on 2007-08-30
**Version 0.5.47**
* Updated the Russian, German, French and Romanian translations.
* Now the help messages (for -help) are formatted automatically by a function, this makes it easy to translate these messages. I apologize for yesterday's madness. As compensation today I have adapted the translations I received myself.
There's nothing else new in this version, but I released it so other translators don't go crazy.

[http://www.content-type.com/1237229138/smplayer_0.5.47_i386.deb.htm](http://www.content-type.com/1237229138/smplayer_0.5.47_i386.deb.htm)

---

### Post by disturbedite on 2007-08-31
**Version 0.5.48**
* Updated the Russian and Japanese translations.
* Now smplayer will also look for icon themes in $HOME/.smplayer/themes. In the case a theme is both in the user directory and the system directory (usually /usr/share/smplayer/themes) it will look first in the user directory. If the icon is not there then it will look in the system directory.
* Under linux the buttons for color selection (Preferences->Subtitles) now look better.

[http://www.content-type.com/204278790/smplayer_0.5.48_i386.deb.htm](http://www.content-type.com/204278790/smplayer_0.5.48_i386.deb.htm)

---

### Post by disturbedite on 2007-09-01
NOTE:
i missed a bunch of the themes releases, so here is the latest version...

**Version 0.1.7**
* New theme: Oxygen-Refit.
* Updated Play/styles.qss for Qt 4.
[B]
Version 0.1.6[/B]
* Updated the Tango theme.

**Version 0.1.5**
* Added the Gartoon theme created by Kud Gray, based on the Gartoon Icons for Gnome.
* Added the create_deb.sh script.
[B]
Version 0.1.4[/B]
* Updated the Tango theme.

[http://www.content-type.com/-1306354894/smplayer-themes_0.1.7_all.deb.htm](http://www.content-type.com/-1306354894/smplayer-themes_0.1.7_all.deb.htm)

---

### Post by disturbedite on 2007-09-02
**Version 0.5.49**
* Updated the Polish and Ukrainian translations.
* Fixed warnings about using deprecated setBackgroundColor.
* Renamed command line option -action to -send-action. This option will try to send the specified action to another running instance of smplayer, after that it will quit.
* Added a new option for command line: -actions. As opposite to -send-action, this option will run the actions in the same instance. There could be several actions, separated by spaces (and enclosed in quotes). Examples:
smplayer video.avi -actions fullscreen (the file video.avi will be loaded, and just after that fullscreen mode will be toggled).
smplayer video.avi -actions "extrastereo_filter on_top" (will load the video, and then the extrastereo filter and the stay on top options will be toggled.
"Toggled" means: if the option was previosly enabled now it will disabled and vice versa. If you want to be sure that an option will be on or off you can pass "true" or "false" as a parameter:
smplayer video.avi -actions "on_top true" (the option Video->Stay on top will be checked, no matter the previous state).
smplayer -actions "show_language_toolbar false" (will hide the language toolbar)
Some actions are not checkable, like open_vcd, double_speed... In that case you shouldn't use "true" or "false". But if you do it will be ignored.
If you make a mistake and enter an action that doesn't exists, you'll get a warning (in the logs or in console) and it'll be ignored. 

[http://www.content-type.com/1353720559/smplayer_0.5.49_i386.deb.htm](http://www.content-type.com/1353720559/smplayer_0.5.49_i386.deb.htm)

---

### Post by disturbedite on 2007-09-03
THEME UPDATE:

**Version 0.1.8**
* Added the Noia theme, created by Vitaliy Motsyo.

[http://www.content-type.com/-754036699/smplayer-themes_0.1.8_all.deb.htm](http://www.content-type.com/-754036699/smplayer-themes_0.1.8_all.deb.htm)

---

### Post by disturbedite on 2007-09-04
THEME UPDATE:
**Version 0.1.9**
* Added the Nuvola theme, created by Nardog.

[http://www.content-type.com/-526389333/smplayer-themes_0.1.9_all.deb.htm](http://www.content-type.com/-526389333/smplayer-themes_0.1.9_all.deb.htm)

**Version 0.5.50**
* Updated the German, Ukrainian and Japanese translations.
* I hope I fixed a problem with the playlist actions not showing (or appearing duplicated) in the actions editor. Now it works ok with Qt 4.2.3 but I won't be sure the problem is really fixed until I test it with Qt 4.3.
* Added the option Subtitles->Use SSA/*** library to make easy to enable or disable the use of the *** lib without having to open the preferences dialog.
* Added new option in Preferences->General "Close when finished." If checked, the main window will be closed when the current file/playlist finishes.
Now the command line option -close-at-end will enable that option.
* Added shortcuts in the Preferences->Subtitles dialog.

[http://www.content-type.com/-594928818/smplayer_0.5.50_i386.deb.htm](http://www.content-type.com/-594928818/smplayer_0.5.50_i386.deb.htm)

---

### Post by disturbedite on 2007-09-05
THEME UPDATE:
**Version 0.1.10**
* Added the Breathless theme, by Kud Gray.

[http://www.content-type.com/1209270355/smplayer-themes_0.1.10_all.deb.htm](http://www.content-type.com/1209270355/smplayer-themes_0.1.10_all.deb.htm)

**Version 0.5.51**
* Updated the Chinese (zh_CN), French, Romanian, German, Ukrainian and Polish translations.
* Made a mistake, the new option "close when finish" was enabled by default. Now that option will be disabled by default.
* (Windows) When using Qt 4.3, inforeader fails, it can't read the output of mplayer. That means there won't be info about the codecs, demuxers, output drivers... I don't know why this happens, but disabling redirection of the mplayer output to a temporary file makes it to work again. I also realized that QProcess in Qt 4.3 works much better, so it's not necessary to send the mplayer output to a temporary file. So now if compiled with Qt 4.3 it won't use temporary files, fixing the problem with inforeader. The problem persists if compiled with Qt 4.2.3 but using the Qt 4.3 dll's, the problem will still be present. Unless...
* Now inforeader uses QProcess (not myprocess), so now it shouldn't be affected by the problem metioned before.
* It doesn't try to create the app home directory ($HOME/.smplayer) if -ini-path is used.

[http://www.content-type.com/1112263200/smplayer_0.5.51_i386.deb.htm](http://www.content-type.com/1112263200/smplayer_0.5.51_i386.deb.htm)

---

### Post by d351GuJu on 2007-09-05
For some reason I cant view the page, is anyone else having same problem?

d351GuJu

---

### Post by disturbedite on 2007-09-06
i was too.  i think content-type went down for a while today.  its back up now.

---

### Post by disturbedite on 2007-09-07
THEME UPDATE:
[B]
Version 0.1.11[/B]
* New version of the Breathless theme with smaller icons (32x32 instead of 128x128). 

[http://www.content-type.com/1330671191/smplayer-themes_0.1.11_all.deb.htm](http://www.content-type.com/1330671191/smplayer-themes_0.1.11_all.deb.htm)
[B]
Version 0.5.52[/B]
* Updated the Russian translation.
* Fix in the open URL dialog: the text should be selected now.
* Fix for Qt 4.3.1 under Windows: after playing an audio file the video window didn't show when playing a video.
* Experimental: add file to be opened in the playlist (deleting the whole playlist first). This prevents that when a file finishes, an item from an old playlist starts to play.
* Added a context menu for when clicking on a toolbar.

[http://www.content-type.com/643041153/smplayer_0.5.52_i386.deb.htm](http://www.content-type.com/643041153/smplayer_0.5.52_i386.deb.htm)

---

### Post by disturbedite on 2007-09-09
sorry i missed two builds/releases, but i went on a trip.

**Version 0.5.55**
* Updated the Japanese, Polish, Ukrainian, German, Romanian and Dutch translations.
* The trailing "/" in dvd device paths will be removed again, but not if used with drive letters (E:/ for instance). It seems that sometimes it's necessary to enter the drive that way in order to play a DVD.
* Fixed all deprecated warnings. Now smplayer can be compiled without QT3_SUPPORT defined. Still using deprecated signals (for instance for QActions) but I've got no warnings about them so it'll be difficult to fix unless I compile Qt with no Qt3 support at all (I guess).

**Version 0.5.54**
* Updated the German, Ukrainian and Romanian translations.
* Disabled again the playlist in main window as it has serious problems with Qt 4.3.1 (at least in Windows).
* The trailing "/" in dvd device paths won't be removed. It seems that sometimes it's necessary. Windows users be careful when playing a dvd from a folder on the hard disk the path shouldn't end in "/", that would make mplayer fail.
* (By user request) Added "Video->Flip image" which flips the image upside-down. This option will affect the current video only, it's not a global option.
* Now you can move the toolbars wherever you want.
* Added the option "Create index if needed" in Preferences->Performance. The option will pass -idx to mplayer. From mplayer manpage: "Rebuilds index of files if no index was found, allowing seeking. Useful with broken/incomplete downloads, or badly created files."

**Version 0.5.53**
* Some fixes in the code to add the file to play in the playlist.
* Some more improvements on the playlist embedded in the main window: now the main window resizes when the playlist is docked/undocked. It also remembers its state on startup.
For first time this code will be compiled as default so other people could test it. There's two known issues: the main window doesn't resize properly when playing an audio file (no video window) and the playlist is undocked (maybe another Qt 4.2.3 bug?). And to avoid some problems when exiting from fullscreen, the playlist is made floatable when entering fullscreen mode.
How to use it? By default the playlist will appear docked in the bottom area. You can move it to the top area if you want, or make it floatable by dragging it outside the window. You can dock it again by dragging the playlist to the bottom or top areas of the main window (there's also a button in the title bar for this).
* Added a help message about the option "It's a playlist" in Open->URL.

[http://www.content-type.com/-1770782881/smplayer_0.5.55_i386.deb.htm](http://www.content-type.com/-1770782881/smplayer_0.5.55_i386.deb.htm)

---

### Post by disturbedite on 2007-09-10
**Version 0.5.56**
* Updated the French translation.
* Fixed regular expression in core.cpp to identify the DVD drive letter.
* Rewrite the code to automatically resize the main window.
* More fixes in the code to embed the playlist in the main window. Now exiting fullscreen works ok, the playlist is restored where it was before. There are still some minor issues.
On my computer (linux, Qt 4.2.3) it works quite well, so I enabled the code by default again. But... will it work on Windows w/ Qt 4.3.1?

[http://www.content-type.com/-1493312279/smplayer_0.5.56_i386.deb.htm](http://www.content-type.com/-1493312279/smplayer_0.5.56_i386.deb.htm)

---

### Post by TheMono on 2007-09-11
Hi - I just got tipped off to this thread after I posted in the equivalent thread for feisty.

[http://ubuntuforums.org/showthread.php?t=472149&highlight=smplayer&page=15](http://ubuntuforums.org/showthread.php?t=472149&highlight=smplayer&page=15)

I've started using the Launchpad packaging archive for building smplayer packages for feisty, and on request I've added gutsy support. You can use them by adding 

deb [http://ppa.launchpad.net/themono/ubuntu](http://ppa.launchpad.net/themono/ubuntu) gutsy main restricted universe

to your /etc/apt/sources.list
Available packages for feisty are smplayer-classic, smplayer, and smplayer-themes. Gutsy does not have smplayer-classic available. Packages are abailable for both i386 and AMD64.

Hope I'm not stealing anyones thunder here!

---

### Post by disturbedite on 2007-09-11
its quite all right.  since there is a repo with up-to-date builds, i will discontinue my builds.  so everyone that wants them, just do as TheMono said.

but i will post one final build, since its newer than the one in that repo atm.

**Version 0.5.57**
 * Fixes in the window resize code. Now resizes should be much smoother. Only if you do something that altesr the size of the window, like moving a toolbar or docking the playlist, could produce some flickering if you later change the video size using any of the options in the menu Video->Size. It also fixes the problem of the window getting very small in Windows (although I couldn't test it). 
 Of course this is in linux using Qt 4.2.3. Will it work on Windows with Qt 4.3.1? 
 * Added the action "Toggle double size" in Video->Size.

[http://www.content-type.com/682593436/smplayer_0.5.57_i386.deb.htm](http://www.content-type.com/682593436/smplayer_0.5.57_i386.deb.htm)

---

### Post by TheMono on 2007-09-11
The builds will be done in the morning, New Zealand time lol. 0.5.57 uploaded now, should be present in the repo in ~20 minutes.

---

### Post by disturbedite on 2007-09-12
thanks mono.

certainly a better solution (the repo i mean) since i (& rvm the author) can't maintain a repo.

---

