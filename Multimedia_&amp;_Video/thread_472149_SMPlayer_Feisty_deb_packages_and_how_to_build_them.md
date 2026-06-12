---
title: "SMPlayer Feisty deb packages and how to build them"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by Shinoda on 2007-06-12
**NB: Thanks to TheMono you may now have SMPlayer [[B]automatically updated**]("http://ubuntuforums.org/showpost.php?p=3340532&postcount=139"), and because of this I will no longer build packages for it.[/B] The rest of this post shall remain unaltered for historic purposes and also due to laziness.

I am not in any way affiliated with the project or its developer, rvm4000, but since [SMPlayer]("http://smplayer.sf.net/") is such an awesome piece of software, I thought I'd build deb packages for Feisty from its source's development releases and share them with anyone who might want it. There's also a similar [thread]("http://ubuntuforums.org/showthread.php?p=2830374") for Gutsy debs and a [website]("http://wesley.debianbox.be/packages/") maintained by _profox with various packages, including 64-bit ones, but not always up to date (hence this thread, though I offer 32-bit builds only).

My packages (after this post) are built with dpkg-buildpackage using latest fakeroot and Qt available in the Ubuntu repos in the following manner:

**How to build SMPlayer deb packages**[LIST=1]
[*]If you have all of the packages below installed you may skip this step, otherwise run in a terminal
```
sudo aptitude install build-essential debhelper fakeroot libqt4-dev qt3-dev-tools
```
[*][Download]("http://smplayer.sourceforge.net/en/linux/download.php") development source package.
[*]Assuming for instance you downloaded the 0.5.40 tarball to your desktop (replace according to your case), one line at a time run
```
cd ~/Desktop
tar xf smplayer-0.5.40.tar.bz2
cd smplayer-0.5.40
./create_deb.sh
cd ..
sudo dpkg -i smplayer_0.5.40_i386.deb
```
[*]Clean the mess, i.e., delete everything (keep the deb if you want).[/LIST]

---

### Post by Shinoda on 2007-06-12
[**Version 0.5.11**]("http://www.ifpost.com/ifpost/download/0487401672342283") 
 * Updated the Ukrainian and German translations.
 * Shortcuts for previous and next items in playlist didn't work in main window. Fixed.
 * Added an option in Preferences->Subtitles to use the new -subfont option in MPlayer. In the future SMPlayer will try to autodetect when this option is needed.
 * Added in Preferences a new section: MPlayer language, where the user can change some of the texts that SMPlayer looks for. Intended in case that MPlayer displays its messages in another language. (Unfortunately MPlayer can't change language at runtime).

---

### Post by Shinoda on 2007-06-13
[**Version 0.5.12**]("http://www.ifpost.com/ifpost/download/6657752581603122")
 * Updated the Swedish, German and Ukrainian translations (although changes  I've just made could have broken them...)
 * Reorganized a little bit the preferences dialog, by using several tab  widgets. This prevents that sections grow too much.
 * Better explained the "MPlayer language" section (I hope) and added regular expressions for Spanish, Italian, German and French in the comboboxes, taken from the MPlayer translation files (completely untested!).

---

### Post by Shinoda on 2007-06-13
[**Version 0.5.13**]("http://www.ifpost.com/ifpost/download/8210827271779399")
 * Updated the Ukrainian, German and Polish translations.
 * (By user request) Now the mouse wheel can be configured to zoom the video (Preferences->Keyboard and mouse->Mouse).
 Note: compatibility couldn't be kept, if you have previously changed the behavior of the mouse wheel you'll need to change it again.
 * Now the options in the menu Video->Size will always be executed even if the option is already selected. Useful if you resized the window. Also added shortcuts for Size->100% and Size->200% (Ctrl+1 and Ctrl+2) and I'm very sorry but these shortcuts can't be changed.
 * (By user request) Added the option Audio->Filters->Volume normalization. 
 Note: this option only affects the current file, if you want the filter to be used for all files add "volnorm" to the audio filters field in Preferences->Advanced.
 * (By user request) Clicking in the system tray icon with the mouse middle   button pauses/unpauses the file.
 * Now tooltips for QActions are explicitly created, to try to work around   a bug in Qt 4.3.

---

### Post by Shinoda on 2007-06-14
[**Version 0.5.14**]("http://www.ifpost.com/ifpost/download/4575795879551309")
 * Updated the Swedish, Ukrainian and Polish translations.
 * I think for volume normalization it's best to have a global option, so I added a volume normalization option in Preferences->General. If checked the volnorm filter will be used for all files.
 * Added an option in Preferences->General to set the maximum amplification level for softvol. By default 110. Valid range 10-10000.

---

### Post by TyPhoon101 on 2007-06-18
what is the difference between your package and that from smplayer.sourceforge.net ?

---

### Post by Shinoda on 2007-06-18
> **TyPhoon101 said:**
> what is the difference between your package and that from smplayer.sourceforge.net ?As I explain in the first post, mine are usually more up to date, i.e., I build them as soon as I notice there's a new development release, which normally happens within the day. Basically, if you like bleeding-edge versions, I'm saving you time and work.

---

### Post by Shinoda on 2007-06-18
[**Version 0.5.15**]("http://www.ifpost.com/ifpost/download/2738275425031766")
 * Updated the Russian, Italian, Swedish, German, Ukrainian, Polish and Simplified-Chinese translations.
 * (By user request) Added an option in Preferences->General to enable the postprocessing filter for all videos.

---

### Post by TyPhoon101 on 2007-06-18
so you are building packages from the official development releases, but aren't those unstable ?and you are making tailor-made changes as per user request ? in that case can you make any amd64 packages ? there is no amd64 packages for ubuntu 7.04 for smplayer.:(

---

### Post by Shinoda on 2007-06-18
> **TyPhoon101 said:**
> so you are building packages from the official development releases, but aren't those unstable ?Changes in every new version are so small I don't believe stability will be a problem. Afair I'm yet to come across difficulties in that regard.> **TyPhoon101 said:**
> and you are making tailor-made changes as per user request ?Not really, I'm just sharing my own debs (i.e. for my system).> **TyPhoon101 said:**
> in that case can you make any amd64 packages ?Actually I do have an Athlon 64 processor, but not the 64-bit version of Ubuntu, and I don't think there's a way to build amd64 packages under these conditions (except maybe with a VM). But it's easy to build your own packages, and you could even use this thread to share them if you'd like, properly labelled as being for amd64 of course. Just follow the instructions I added to the first post.

---

### Post by Shinoda on 2007-06-18
[**Version 0.5.16**]("http://www.ifpost.com/ifpost/download/6347306418767241")
 * Updated the Ukrainian and Polish translations.
 * Added two new translations: Romanian and Portuguese from Portugal.

---

### Post by Shinoda on 2007-06-20
[**Version 0.5.17**]("http://www.ifpost.com/ifpost/download/6633443576334365")
 * Updated the Brazilian Portuguese, Slovak, Ukrainian, German and Portuguese from Portugal translations.
 * Now QCoreApplication::arguments () will be used to read the arguments from command line if Qt > 4.1. On NT-based Windows this should allow the program to get the right characters if the filename contains characters from other alphabets.

---

### Post by Shinoda on 2007-06-20
[**Version 0.5.18**]("http://www.ifpost.com/ifpost/download/4017429669267887")
 * Updated the Russian translation.
 * Added support for audio CDs (only tested with one disc) so please test yourself and report problems. Test also if VCD and DVD still work properly.
   Note: I don't know if this option will work on Windows, I never could play an audio CD with the Windows version of MPlayer.

---

### Post by TyPhoon101 on 2007-06-21
i could not play  a vcd in smplayer .i selected open vcd and it showed the the cd/dvd drive is not configured yet. and took me to the cd/dvd drive configuration tab. i chose /dev/cdrom from the drop-down menu clicked ok but nothing happened. but in mplayer i chose open vcd and it started playing :confused:

---

### Post by Shinoda on 2007-06-21
> **TyPhoon101 said:**
> i chose /dev/cdrom from the drop-down menu clicked ok but nothing happened. but in mplayer i chose open vcd and it started playingIs [FONT=Courier New]/dev/cdrom[/FONT] what you have in MPlayer under Preferences > Misc > CD-ROM device? If so, strange. If not, copy whatever's there to SMPlayer's respective option (Options > Preferences > Drives > Select your CD device).

---

### Post by Shinoda on 2007-06-21
[**Version 0.5.19**]("http://www.ifpost.com/ifpost/download/7066193875465417")
 * Updated the German and Polish translations.
 * (Windows) The priority of the SMPlayer process is changed accordingly to the priority of MPlayer (SMPlayer will try to run with higher priority).
   Note: not much tested.
 * As a lot of people have complained, I changed "Brazilian Portuguese" and "Portuguese from Portugal" to "Portuguese - Brazil" and "Portuguese - Portugal".

---

### Post by TyPhoon101 on 2007-06-21
> **Shinoda said:**
> Is [FONT=Courier New]/dev/cdrom[/FONT] what you have in MPlayer under Preferences > Misc > CD-ROM device? If so, strange. If not, copy whatever's there to SMPlayer's respective option (Options > Preferences > Drives > Select your CD device).
i have the same in mplayer i.e dev/cdrom .also one problem when i play a rmvb file in mplayer the seek bar does not work it just starts from the beginning no matter what position i choose. can you fix this or this is a problem with mplayer?

---

### Post by Shinoda on 2007-06-21
> **TyPhoon101 said:**
> when i play a rmvb file in mplayer the seek bar does not work it just starts from the beginning no matter what position i choose.In my experience, some files or file types just can't be sought, i.e., it's not the player's fault. Not 100% sure though.> **TyPhoon101 said:**
> can you fix this or this is a problem with mplayer?If you had read the first post you would know rvm4000 is the one who you should be asking.

---

### Post by Shinoda on 2007-06-23
[**Version 0.5.20**]("http://www.ifpost.com/ifpost/download/5323305653148393")
 * Updated the German, Ukrainian, Portuguese and Romanian translations.
 * Now it will exit from compact mode before playing an audio file. Otherwise the GUI would not have any menus or buttons at all.
 * Temporary fix: in playlist, the latest_dir won't be changed when adding multiple files, to avoid that wrong paths with dvd:, vcd:... could be used.

---

### Post by Shinoda on 2007-06-24
[**Themes Version 0.1.2**]("http://www.ifpost.com/ifpost/download/4579951326115686")
* Renamed the debian directory to debian-rvm, so it doesn't conflict with the one made by package maintainers.
So if you want to create a deb package with dpkg-buidpackage, rename it back to debian (or create a symlink).
* Added a dependency on smplayer in the control file.

---

### Post by Shinoda on 2007-06-26
[**Version 0.5.21**]("http://www.ifpost.com/ifpost/download/8931430031845442")
 * Updated the Brazilian Portuguese translation.
 * Moved the video and audio sections in Preferences->General to a new tab, and moved also the font section in Subtitles to another tab, to try to make the preferences dialog smaller.
 
**Note:** This is the last release which can be compiled with Qt 3. [rvm4000 is] going to start to port it to Qt 4 **now**. New features, bug fixes and translation updates will have to wait.

---

### Post by Shinoda on 2007-06-27
**Note:** currently SMPlayer is being ported to Qt 4. These versions could be really **unstable**. You're warned.

[**Version qt4-0626-1**]("http://www.ifpost.com/ifpost/download/0703928637569478")[LIST]
[*]Updated the Polish translation.
[*]Ported trackdata.h, trackdata.cpp, tracks.h, tracks.cpp, encoding.h, encoding.cpp, mediadata.h, mediadata.cpp, mediasettings.h, mediasettings.cpp, preferences.h, preferences.cpp, recents.h, recents.cpp, translator.h and translator.cpp (only renamed headers needed).
[*]Ported subtracks.h and subtracks.cpp. It was necessary to change a Q3ValueList with QList. Don't know if this could have unexpected results. This class stores the subtitle tracks and it's responsible for checking if any of the subtitles matches the user's favourite language.[/LIST][B]
Version qt4-0625-1[/B] [missed][LIST]
[*]Updated the German and Polish translations.
(Let's start with the easiest...)
[*]Removed the prep section in Makefile, and the conv2qt4.sh and conv2qt4.bat in src/ as they won't be needed anymore.
[*]Ported filedialog.h and filedialog.cpp. Removed all KDE 3 code.
These files contain all open/save dialogs. Now using the Qt 4 dialogs, which are a little bit nicer (in Linux).
[*]Ported aboutdialog.h and aboutdialog.cpp. This is the "About SMPlayer" dialog.
Note: the link at the bottom still doesn't work.
[*]Ported core.h and core.cpp. Only the Qt headers have been changed. 
It seems no other change is required.
[*]Ported infofile.h and infofile.cpp. Only the Qt headers were changed.
This class creates the info text you can see in Options->View info and properties (Information tab).
[*]Ported desktopinfo.h and desktopinfo.cpp. Only the Qt headers were needed to change.[/LIST]

---

### Post by mboliver` on 2007-06-27
Is it possible to explain the whole change directory thing when attempting to install this program? I apologize for being new and I promise that I did search.

After step four, I am at a loss.

---

### Post by Shinoda on 2007-06-27
> **mboliver` said:**
> Is it possible to explain the whole change directory thing when attempting to install this program?What I mean is a truly basic procedure: just go to a terminal and type [FONT=Courier New]cd[/FONT] followed by the path to the directory (folder) extracted in step 1. So if you for instance downloaded the [FONT=Courier New]smplayer-qt4-0627.tar.gz[/FONT] file to your desktop, right-clicked its icon, and chose "Extract Here" from the context menu, open up a terminal and type```
cd ~/Desktop/smplayer-qt4-0627
```(remember Linux is case-sensitive).

---

### Post by rvm4000 on 2007-06-27
> **TyPhoon101 said:**
> i could not play  a vcd in smplayer .i selected open vcd and it showed the the cd/dvd drive is not configured yet. and took me to the cd/dvd drive configuration tab. i chose /dev/cdrom from the drop-down menu clicked ok but nothing happened. but in mplayer i chose open vcd and it started playing :confused:

Once you have chosen your cdrom drive, you have to select again Open->VCD. If that doesn't work check the mplayer log, maybe there's an error message.

> **TyPhoon101 said:**
> also one problem when i play a rmvb file in mplayer the seek bar does not work it just starts from the beginning no matter what position i choose. 

I guess you're using mplayer 1.0rc1. You should update it, that's fixed in the svn releases.

---

### Post by pickarooney on 2007-06-27
Download for the 0.5.21 version doesn't work; the downlaoded file is of type data and not deb

---

### Post by mboliver` on 2007-06-27
Thanks for the info...I will give it a shot:D

---

### Post by Shinoda on 2007-06-27
> **pickarooney said:**
> Download for the 0.5.21 version doesn't work; the downlaoded file is of type data and not debI think IFPost is experiencing technical difficulties atm since all file downloads get corrupted. I'll use some other file hosting service for future releases in the meanwhile. Either way there's a deb for that version in SMPlayer's [site]("http://smplayer.sourceforge.net/linux/download_en.php").

---

### Post by Shinoda on 2007-06-27
[**Version qt4-0627**]("http://content-type.com/-1586027705/smplayer_qt4-0627_i386.deb.htm")[LIST]
[*]Updated the French translation, using the one sent by Kud Gray.
[*]Ported inputdvddirectory.h, inputdvddirectory.cpp and inputdvddirectorybase.ui (first ui ported, not easy to port these files...). This dialog appears when the user selects Open->DVD from folder.
[*]Ported logwindow.h, logwindow.cpp and logwindowbase.ui. This is the    widget used to display the mplayer/smplayer logs.
[*]Ported (partially) filepropertiesdialog.h, filepropertiesdialog.cpp, and filepropertiesdialogbase.ui. Still using Q3ListBox. This dialog appears with Options->View info and properties.[/LIST]

---

### Post by TyPhoon101 on 2007-06-28
> **rvm4000 said:**
> Once you have chosen your cdrom drive, you have to select again Open->VCD. If that doesn't work check the mplayer log, maybe there's an error message.



I guess you're using mplayer 1.0rc1. You should update it, that's fixed in the svn releases.

everything worked out nicely. thank you for the valuable advice:popcorn:

---

### Post by Shinoda on 2007-06-28
[**Version 0.5.29-qt4-0628**]("http://content-type.com/-900110935/smplayer_0.5.29-qt4-0628_i386.deb.htm")[LIST]
[*]Updated the Ukrainian and Russian translations.
[*]Ported (partially) inforeader.h and inforeader.cpp. Now using QLists  instead of Q3ValueLists. Still using Q3Process though.
[*]Ported eqslider.h, eqslider.cpp, eqsliderbase.ui, verticaltext.h, verticaltext.cpp, videoequalizer.h and videoequalizer.cpp. All of this is the video equalizer.
[*]Ported seekwidget.h, seekwidget.cpp and seekwidgetbase.ui. This provides the widget that allows to change the seeking times in Preferences->Interface.
[*]Ported preferencesdialogbase.ui and made some small changes in preferencesdialog.h/preferencesdialog.cpp to make it compile. Still using a lot of Qt 3 widgets. This is the preferences dialog and it's huge. I'll change them later because I thought about splitting it in modules.
[*]Ported mplayerwindow.cpp and mplayerwindow.h. This is the widget used    for the video.[/LIST]

---

### Post by Shinoda on 2007-06-30
[**Version 0.5.29-qt4-0629-2**]("http://content-type.com/476546038/smplayer_0.5.29-qt4-0629-2_i386.deb.htm")
[list]
[*]Updated the German translation.
[*]Created the file create_deb.sh, specially for Ubunty users. If you run it,   it would create a deb package.
[*]Started to write the new preferences dialog. When finished it will look like the old one, but internally each section will be a separate widget, so it will be easier to maintain. This new dialog is hidden, if you want to see it press Ctrl+6.
[/list]
 
**Version 0.5.29-qt4-0629-1** [missed]
[list]
[*]Updated the pt_PT translation.
[*]filepropertiesdialog.cpp: replaced the Q3ListBox with QListWidget. So  this file is completely ported.
[*]mplayerprocess: changed the Qt headers but still using Q3Process.
[*]Ported global.h and global.cpp.
[*]The link in the "about" dialog at last works (if Qt >= 4.2).
[*]Fix: use setAutoFillBackground() only if Qt >= 4.1.
[*]Now the option "Don't repaint the video background" is checked by default  in Linux.
[/list]

---

### Post by Shinoda on 2007-07-01
[**Version 0.5.29-qt4-0630-2**]("http://content-type.com/997107660/smplayer_0.5.29-qt4-0630-2_i386.deb.htm")[LIST]
[*]The first two sections (General and Drives) in the new preferences dialog should now be fully functional, although testing is needed. It's very easy that I could have forgotten to copy some code from the old dialog and some options might not work as expected. So testing would be very appreciatted.
[*]Switched to the new Qt 4 automatic connections in FilePropertiesDialog.[/LIST] 
**Version 0.5.29-qt4-0630-1** [missed][LIST]
[*]Made InfoReader a little bit smarter. Now it calls mplayer by its own, and PreferencesDialog and FilePropertiesDialog ask it for the info (available drivers, codecs...), so this is not done anymore by BaseGui.
[*]Now the new preferences dialog is used if compiled with #define NEW_PREFERENCES_DIALOG 1 (in config.h). Otherwise the old dialog will be used to keep things working.[/LIST]

---

### Post by Shinoda on 2007-07-01
[**Version 0.5.29-qt4-0701-1**]("http://content-type.com/496349690/smplayer_0.5.29-qt4-0701-1_i386.deb.htm")
[list]
[*]Updated the Ukrainian, German, Russian and Polish translations.
[*]The interface section is available in the preferences dialog. I added this section first because I needed to test the language and iconset change.
[/list]

---

### Post by Shinoda on 2007-07-01
[**Version 0.5.29-qt4-0701-2**]("http://content-type.com/1135631103/smplayer_0.5.29-qt4-0701-2_i386.deb.htm")
[list]
[*]Updated the German translation.
[*]The performance section is now available in the preferences dialog.
[*]Added the keyboard & mouse section too.
[*]Added the subtitle section. And now using the new QFontComboBox to select the system font. BTW, I've just realized that the QFontComboBox was added in Qt 4.2. So that means that now SMPlayer requires at least Qt 4.2.
[/list]

---

### Post by Shinoda on 2007-07-02
[**Version 0.5.29-qt4-0702-1**]("http://content-type.com/-1659216294/smplayer_0.5.29-qt4-0702-1_i386.deb.htm")
[list]
[*]Updated the German and Polish translations.
[*]The advanced section is also available in the preferences dialog.
 So now all sections are available again. Although it looks like before, the preferences dialog has completely been rewritten, so there could be bugs. So please test it, and report if you find any problem.
[/list]

---

### Post by Shinoda on 2007-07-03
[**Version 0.5.29-qt4-0702-2**]("http://content-type.com/-679781759/smplayer_0.5.29-qt4-0702-2_i386.deb.htm")[LIST]
[*]Updated the Polish translation.
[*]Added the "whatsthis" help again to the preferences dialog. So now the  preferences dialog recovers whole functionality.
[*]And something new: the "help" button works. It will display all "whatsthis" messages in a single page. There's not help for everything yet.
[*]Moved the old preferences stuff to old-preferences directory. Now the old preferences dialog is not compiled any more.
   So the new preferecences dialog is mostly finished.[/LIST]

---

### Post by Shinoda on 2007-07-03
[**Version 0.5.29-qt4-0703**]("http://content-type.com/129230310/smplayer_0.5.29-qt4-0703_i386.deb.htm")[LIST]
[*]Updated the German and Polish translations.
[*]Some fixes with the new help window in preferences.
[*]To save some space in the tar.gz, now the *.qm files won't be distributed, as they can be generated by lrelease. So now the Makefile will try to create those files. By default it will call to lrelease (which should be included in the Qt development package). In (k)ubuntu this tool is named lrelease-qt4, you can pass it to Makefile this way: make LRELEASE=lrelease-qt4
[*]Removed the old preferences code in basegui.
[*]Ported main.cpp (and removed the KDE 3 code).
[*]Improved inputdvddirectory. Now using automatic connections, and a buttonbox for the Ok and cancel buttons (if you're using the cleanlooks style you'll see the difference).
[*]Using automatic connections in the logwindow. So I think now all the *.ui files are properly ported to Qt 4.[/LIST]

---

### Post by Shinoda on 2007-07-05
[**Version 0.5.29-qt4-0704**]("http://content-type.com/-1352250010/smplayer_0.5.29-qt4-0704_i386.deb.htm")
[list]
[*]Added a bat file (compile_windows.bat) to make easier the compilation in Windows.
 
[*]Updated the German and Japanese translations.
 
[*]Renamed some UI files.
 
[*]Using a QDialogButtonGroup in the about dialog.
 
[*]Try to load the Qt translation file. This way texts directly generated by the Qt library (ok and cancel buttons, the file dialog...) will also be translated (if a translation is available for your language). Currently it will try to load the *.qm file from the Qt translation path (querying QLibraryInfo). It should work on Linux but I don't know if it will work on Windows. 
   Note: currently the language for this translations can't be changed   at run-time.
[/list]

---

### Post by Shinoda on 2007-07-06
[**Version 0.5.29-qt4-0705**]("http://content-type.com/1036014312/smplayer_0.5.29-qt4-0705_i386.deb.htm")
[list]
[*]Now the Qt translation file is loaded too when the user changes the language in the preferences dialog (unfortunately it seems that the strings in buttons are not updated at runtime, so you'll need to restart the program to have a full translation).
   This is what it will be done:
 First it will try to load the Qt translation from the Qt translation folder, if that fails then it will try to load it from the SMPlayer translation folder. This would allow SMPlayer to use non official Qt translations for other languages, without having to install them in the Qt directories.
 In Windows it will just look for the translations in the SMPlayer translation folder, as most Windows users won't have Qt installed.
 
[*]Made some changes in the actions editor to avoid corruption of the key shortcuts. The corruption happened because the shortcuts were translated (for example, the shortcut "Ctrl+Right" was translated to "Ctrl+Derecha" in Spanish) but when a language change occurs at runtime, the new language doesn't understand the shortcuts. This has been fixed not allowing the shortcuts to be translated.
[*]Using a QDialogButtonGroup in the file properties dialog. The QDialogButtonBox shows the Ok, Cancel... buttons in different ways according to the current style. The best way to see the difference is to use the Cleanlooks style: *smplayer -style cleanlooks*
[*]Updated the Ukrainian, German, Polish and Russian translations.
[/list]

---

### Post by Shinoda on 2007-07-06
[**Version 0.5.29-qt4-0706-2**]("http://content-type.com/397880249/smplayer_0.5.29-qt4-0706-2_i386.deb.htm")
[list]
[*]New feature: on startup SMPlayer will try to create two directories: $HOME/.smplayer and $HOME/.smplayer/screenshots
 Now the configuration file will be stored in $HOME/.smplayer/ If you want to keep your configuration just copy $HOME/.config/RVM/smplayer.ini to $HOME/.smplayer/
 And obviously the directory $HOME/.smplayer/screenshots will be used to store the screenshots (this also fulfills an old request).
 This change affects also Windows! Not compiled yet on Windows but according to the Qt docs the directories will be C:/Documents and Settings/Username/.smplayer and C:/Documents and Settings/Username/.smplayer/screenshots
[/list]
 
**Version 0.5.29-qt4-0706-1** [missed]
[list]
[*]Started to use the new (and more complicated) method in Qt 4 for retranslating the texts. While doing this I have found a bug: the vertical texts in the video equalizer don't appear when the language is Japanese, Chinese or Georgian (it worked with Qt 3 but it seems that it never worked with Qt 4). Until I find a fix, as a workaround I added a tooltip so the user could know what's each control for.
[*]The problem with texts in buttons in QDialogButtonGroups, which are not retranslated, seems to be fixed in Qt 4.3. I'm still using Qt 4.2.3 so I added a workaround for Qt 4.2.
[*]Added "buddies" (or key accelerators) in the Advanced section in preferences. I'm afraid this breaks the translations but it's something that has to be done. I'll add them too in the other sections.
[/list]

---

### Post by Shinoda on 2007-07-07
[**Themes Version 0.1.3**]("http://content-type.com/754569808/smplayer-themes_0.1.3_all.deb.htm")
[list]
[*]Added the Tango theme by Yurkovsky Andrey <anyr@tut.by>
[*]Removed the Oxygen theme as I don't know the license of the icons.
[/list]

---

### Post by Shinoda on 2007-07-09
[**Version 0.5.29-qt4-0708**]("http://content-type.com/-1661654353/smplayer_0.5.29-qt4-0708_i386.deb.htm")
[list]
[*]Updated the zh_CN, German and Turkish translations.
[*]Bug fix: now the info about the demuxer, audio and video codec are updated  after a restart of the mplayer process.
[*]Ported the shortcuts' editor, by using a QTableWidget instead of a Q3Table.
 This has been a very hard task (and in fact it's not completely finished yet), as there are a lot of differences between Q3Table and QTableWidget. Moreover QTableWidget is more prone to crashes as it requires the use of pointers all around.
[*]Updated the shorcuts/default.keys as the previous one lacked the action "quit".
[/list]

---

### Post by Shinoda on 2007-07-11
[**Version 0.5.29-qt4-0709**]("http://sendspace.com/file/z9ux27")
[list]
[*]The priority option in preferences was broken. Fixed.
[*]Still some changes in the action editor.
[/list]

---

### Post by Shinoda on 2007-07-11
[**Version 0.5.29-qt4-0710**]("http://sendspace.com/file/u00mwa")
[list]
[*]Updated the Russian translation.
[*]Now changing a key shortcut in the actions' editor is much easier. Now you double click or press enter on a shortcut (you can do it in any column) and a dialog will appear to ask you for the new shortcut. In this dialog you press the key or combination of keys that you want to assign to the shortcut. If you want to delete, just click on the Clear button.
   Note: this has been done by using some code from Edyuk ([http://www.edyuk.org](http://www.edyuk.org))
   Note 2: it's possible that some keys are not caught properly. In that case  report it.
[/list]

---

### Post by Shinoda on 2007-07-14
[**Version 0.5.29-qt4-0714-1**]("http://content-type.com/1542792454/smplayer_0.5.29-qt4-0714-1_i386.deb.htm")
[list]
[*]Updated the German translation.
[*]Tried to fix the AltGr issue but I have also realized that the Tab key can't be entered so I think it's best to go back definitely to the old method. Retrieved the old intro text for preferences.
[*]make clean deletes the file src/Makefile, as this file is generated by qmake.
[/list]

**Version 0.5.29-qt4-0713** [missed]
[list]
[*]Updated the German, Polish and Ukrainian translations.
[*]In the action editor the AltGr key is not detected properly. So it's not possible to enter keys such as "#" or "@" as shortcuts. Until I fix it, I'm going back to the old method to enter keys.
[/list]

---

### Post by Chymera on 2007-07-17
I have had some problems in the past with playing dvds, as stated [here]("http://ubuntuforums.org/showthread.php?t=474708&page=2"). Thus i have decided to try smplayer out. I have downloaded fakeroot, and have proceeded as described in this thread's first post. However once I got to "./create_deb.sh" i was prompted with the following error mesage 

> ./create_deb.sh: 4: dpkg-buildpackage: not found

I tried to follow the install instructions which came with the package, namely make && make install. I typed "make" and guess what...
> 
cd src && qmake  && DATA_PATH=\\\"/usr/local/share/smplayer\\\" CONF_PATH=\\\"/usr/local/etc/smplayer\\\" TRANSLATION_PATH=\\\"/usr/local/share/smplayer/translations\\\" DOC_PATH=\\\"/usr/local/share/doc/packages/smplayer\\\" THEMES_PATH=\\\"/usr/local/share/smplayer/themes\\\" SHORTCUTS_PATH=\\\"/usr/local/share/smplayer/shortcuts\\\" make
/bin/sh: qmake: not found
make: *** [src/smplayer] Error 127

I thought i may not have qt3 or qt4 (whatever those are), but synaptic says otherwise (or maybe I didnt understand what it said :confused: ). anyway the install package also says that if make fails QTDIR may not point to the right path... If so... how do I find out where it should point... and how do i correct that?

---

### Post by Shinoda on 2007-07-17
> **Chymera said:**
> ./create_deb.sh: 4: dpkg-buildpackage: not found
Do you have dpkg-dev installed?
> **Chymera said:**
> /bin/sh: qmake: not found
And what about qt3-dev-tools?
> **Chymera said:**
> I thought i may not have qt3 or qt4 (whatever those are)
[Qt]("http://en.wikipedia.org/wiki/Qt_%28toolkit%29") is an application development framework, or toolkit.

---

### Post by Shinoda on 2007-07-17
[**Version 0.5.29-qt4-0716**]("http://content-type.com/953925173/smplayer_0.5.29-qt4-0716_i386.deb.htm")
[list]
[*]Updated the Ukrainian, Japanese and Russian translations.
[*]Started to write myprocess class. But this is done separately in a testing program.
[*]Fix: now reading the info about video, audio drivers, codecs and demuxers is done in a language independent way (it looks for tags like "ID_VIDEO_OUTPUTS" instead of English text).
[/list]

---

### Post by Chymera on 2007-07-17
thank you for pointing out the packages which were missing, i installed them, and another few which the installer asked for... still, as i type  ./create_deb.sh i get the following error message at the end of a long progress log.


>  make
/bin/sh: qmake-qt4: not found
make[1]: *** [src/smplayer] Error 127
make[1]: Leaving directory `/home/chymera/Desktop/smplayer-0.5.29-qt4-0716'
make: *** [build-stamp] Error 2



I tried looking for the package qmake-qt4 under synaptic.... but its nowhere to be found.

---

### Post by Shinoda on 2007-07-17
> **Chymera said:**
> /bin/sh: qmake-qt4: not found
Try installing libqt4-dev.

---

### Post by Chymera on 2007-07-18
10x again for pointing out the package. But "./create_deb.sh" still dosent work, and neither does "make"... only this time i cant make anything out of the huge progress list i get... only a couple of errors at the end 
> 
make[2]: g++: Command not found
make[2]: *** [.obj/global.o] Error 127
make[2]: Leaving directory `/home/chymera/Desktop/smplayer-0.5.29-qt4-0716/src'
make[1]: *** [src/smplayer] Error 2
make[1]: Leaving directory `/home/chymera/Desktop/smplayer-0.5.29-qt4-0716'
make: *** [build-stamp] Error 2

Am i the only one geting this or is the player just screwed :confused:

---

### Post by Shinoda on 2007-07-18
> **Chymera said:**
> make[2]: g++: Command not found
Is build-essential installed?
> **Chymera said:**
> Am i the only one geting this or is the player just screwed
I think it's just a matter of installing all required packages to finally get it going.

---

### Post by Chymera on 2007-07-18
10q for your help. I just got it running and it is working even better than kaffeine. Still i have a file which it can indeed play, but inside of which it cannot search (ie. go forward or backward). Could it be that i need additional codecs (i read somewhere that it doesnt have or need codecs at all), or is the file just corrupted? (file format .mkv)

---

### Post by Shinoda on 2007-07-18
> **Chymera said:**
> Still i have a file which it can indeed play, but inside of which it cannot search (ie. go forward or backward). Could it be that i need additional codecs (i read somewhere that it doesnt have or need codecs at all), or is the file just corrupted? (file format .mkv)
I very much doubt you need anything else, except maybe latest [MPlayer SVN]("http://www.mplayerhq.hu/design7/dload.html"). I believe MKV files are searchable even when corrupted, probably unless they're heavily corrupted of course. Otherwise that would be a question better directed towards rvm4000.

---

### Post by rvm4000 on 2007-07-18
Maybe seeking doesn't work because the index is corrupted or something.

You can try the -idx option.

Open the file in smplayer, and now select Options->View info and properties. Go to the MPlayer options tab, and type **-idx** in the Options field.

This option makes mplayer to recreate an index (in memory, the file is untouched).

---

### Post by Shinoda on 2007-07-18
[**Version 0.5.29-qt4-0718**]("http://content-type.com/123707679/smplayer_0.5.29-qt4-0718_i386.deb.htm")
[list]
[*]Updated the Polish and German translations.
[*]Now inforeader and mplayerprocess use the new myprocess. This is an important change. MyProcess is a class which inherits from QProcess (the Qt4 one, of course, although it provides some compatibility functions, like addArgument(), otherwise I would have to make a lot of changes in core.cpp). It provides a special working mode for Windows: the output of mplayer is sent to a temporary file and read from it. I hope this could improve performance under Windows.
[/list]

---

### Post by Chymera on 2007-07-20
well i tried your suggestion out. Previously, when i moved the progress indicator nothing happened, now whenever i move it the picture jams slightly (ie becomes static and seems to be torn apart by further movement in the video), the audio stream remains unchanged, however the video stream recovers after a few seconds and continues as if the progress bar werent moved, the progress bar returns to the corresponding spot as well.

---

### Post by TyPhoon101 on 2007-07-20
i have installed the latest development version but i can't get it to play any video : only the audio:here's the bash output :
Debug: MplayerProcess::parseLine: '[mkv] |  + Track number: 2'
Debug: MplayerProcess::parseLine: '[mkv] |  + Track type: Audio'
Debug: MplayerProcess::parseLine: '[mkv] |  + Default flag: 1'
Debug: MplayerProcess::parseLine: '[mkv] |  + Codec ID: A_MPEG/L3'
Debug: MplayerProcess::parseLine: '[mkv] |  + Default duration: 24.000ms ( = 41.667 fps)'
Debug: MplayerProcess::parseLine: '[mkv] |  + Language: und'
Debug: MplayerProcess::parseLine: '[mkv] |  + Audio track'
Debug: MplayerProcess::parseLine: '[mkv] |   + Sampling frequency: 48000.000000'
Debug: MplayerProcess::parseLine: '[mkv] |   + Channels: 2'
Debug: MplayerProcess::parseLine: '[mkv] |+ found cluster, headers are parsed completely :)'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ID=0'
Debug: MplayerProcess::parseLine: '[mkv] Aspect: 1.777778'
Debug: MplayerProcess::parseLine: '[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_ID=0'
Debug: MplayerProcess::parseLine: ID_AUDIO_ID: 0
Debug: MplayerProcess::parseLine: 'ID_AID_0_LANG=und'
Debug: MplayerProcess::parseLine: Audio: ID: 0, Lang: 'und' Type: 'LANG'
Debug: MplayerProcess::parseLine: '[mkv] Track ID 2: audio (A_MPEG/L3), -aid 0, -alang und'
Debug: MplayerProcess::parseLine: '[mkv] Will play video track 1.'
Debug: MplayerProcess::parseLine: 'Matroska file format detected.'
Debug: MplayerProcess::parseLine: 'VIDEO:  [avc1]  704x396  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)'
Debug: MplayerProcess::parseLine: 'ID_FILENAME=/media/hda4/Heroic Age/[Your-Mom]_Heroic_Age_-_06_[C0752A13].mkv'
Debug: MplayerProcess::parseLine: 'ID_DEMUXER=mkv'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_FORMAT=avc1'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_BITRATE=0'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_WIDTH=704'
Debug: MplayerProcess::parseLine: md.video_width set to 704
Debug: MplayerProcess::parseLine: 'ID_VIDEO_HEIGHT=396'
Debug: MplayerProcess::parseLine: md.video_height set to 396
Debug: MplayerProcess::parseLine: 'ID_VIDEO_FPS=23.976'
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7778'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.777800
Debug: MplayerProcess::parseLine: 'ID_AUDIO_FORMAT=85'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=0'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
Debug: MplayerProcess::parseLine: 'ID_LENGTH=1449.95'
Debug: MplayerProcess::parseLine: md.duration set to 1449.950000
Debug: MplayerProcess::parseLine: 'xscreensaver_disable: Could not find XScreenSaver window.'
Debug: MplayerProcess::parseLine: 'Opening video filter: [screenshot]'
Debug: MplayerProcess::parseLine: 'Opening video filter: [***]'
Debug: MplayerProcess::parseLine: '[***] Init'
Debug: MplayerProcess::parseLine: '[***] Updating font cache.'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family'
Debug: MplayerProcess::parseLine: 'Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'ID_VIDEO_CODEC=ffh264'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'Opening audio decoder: [mp3lib] MPEG layer-2, layer-3'
Debug: MplayerProcess::parseLine: 'AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_BITRATE=192000'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_RATE=48000'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_NCH=2'
Debug: MplayerProcess::parseLine: 'Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)'
Debug: MplayerProcess::parseLine: '=========================================================================='
Debug: MplayerProcess::parseLine: 'AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)'
Debug: Core::gotAO: 'alsa'
Debug: MplayerProcess::parseLine: 'ID_AUDIO_CODEC=mp3'
Debug: MplayerProcess::parseLine: 'Starting playback...'
Debug: MplayerProcess::parseLine: 'VDec: vo config request - 704 x 396 (preferred colorspace: Planar YV12)'
Debug: MplayerProcess::parseLine: 'VDec: using Planar YV12 as output csp (no 0)'
Debug: MplayerProcess::parseLine: 'Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.780000
Debug: MplayerProcess::parseLine: 'ID_VIDEO_ASPECT=1.7778'
Debug: MplayerProcess::parseLine: md.video_aspect set to 1.777800
Debug: MplayerProcess::parseLine: '[swscaler @ 0x886d6b8]SwScaler: using unscaled yuv420p -> bgr24 special converter'
Debug: MplayerProcess::parseLine: 'VO: [xv] 704x396 => 704x396 Planar YV12  [zoom]'
Debug: Core::gotVO: 'xv'
Debug: Core::gotWindowResolution: 704, 396
Debug: BaseGuiPlus::resizeWindow: 704, 396
Debug: BaseGui::resizeWindow: 704, 396
Debug: width: 704, height: 511
Debug: mplayerwindow->size: 704, 396
Debug: MplayerProcess::parseLine: 'X11 error: BadAccess during XSelectInput Call'
Debug: MplayerProcess::parseLine: 'X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)'
Debug: MplayerProcess::parseLine: 'X11 error: MPlayer discards mouse control (reconfiguring)'
Debug: MplayerProcess::parseLine: starting sec: 57.400000
Debug: Core::gotStartingTime: 57.400000
Debug: Core::gotStartingTime: current_sec: 50.100000
Debug: Core::finishRestart
Debug: Core::newMediaPlaying
Debug: Core::initializeMenus
Debug: BaseGui::initializeMenus
Debug: MediaData::list
Debug:   filename: '/media/hda4/Heroic Age/[Your-Mom]_Heroic_Age_-_06_[C0752A13].mkv'
Debug:   duration: 1449.950000
Debug:   video_width: 704
Debug:   video_height: 396
Debug:   video_aspect: 1.777800
Debug:   type: 0
Debug:   novideo: 0
Debug:   dvd_id: ''
Debug:   initialized: 1
Debug:   mkv_chapters: 0
Debug:   Subs:
Debug:   Audios:
Debug:     item # 0
Debug:      ID: '0' lang: 'und' name: ''
Debug:      filename: '' duration: 0.000000 chapters: 0 angles: 0
Debug:   Titles:
Debug:   demuxer: 'mkv'
Debug:   video_format: 'avc1'
Debug:   audio_format: '85'
Debug:   video_bitrate: 0
Debug:   video_fps: '23.976'
Debug:   audio_bitrate: 192000
Debug:   audio_rate: 48000
Debug:   audio_nch: 2
Debug:   video_codec: 'ffh264'
Debug:   audio_codec: 'mp3'
Debug: MediaSettings::list
Debug:   current_sec: 50.100000
Debug:   current_sub_id: 90000
Debug:   current_audio_id: 0
Debug:   current_title_id: -1000
Debug:   current_chapter_id: 0
Debug:   current_angle_id: -1000
Debug:   letterbox: 0
Debug:   aspect_ratio_id: 1
Debug:   volume: 52
Debug:   mute: 0
Debug:   external_subtitles: ''
Debug:   external_audio: ''
Debug:   sub_delay: 0
Debug:   audio_delay: 0
Debug:   sub_pos: 100
Debug:   brightness: 0
Debug:   contrast: 0
Debug:   gamma: 0
Debug:   hue: 0
Debug:   saturation: 0
Debug:   speed: 1.000000
Debug:   phase_filter: 0
Debug:   current_denoiser: 0
Debug:   deblock_filter: 0
Debug:   dering_filter: 0
Debug:   noise_filter: 0
Debug:   postprocessing_filter: 0
Debug:   current_deinterlacer: 0
Debug:   panscan_filter: ''
Debug:   crop_43to169_filter: ''
Debug:   karaoke_filter: 0
Debug:   extrastereo_filter: 0
Debug:   volnorm_filter: 0
Debug:   audio_use_channels: 0
Debug:   stereo_mode: 0
Debug:   panscan_factor: 1.000000
Debug:   forced_demuxer: ''
Debug:   forced_video_codec: ''
Debug:   forced_audio_codec: ''
Debug:   original_demuxer: ''
Debug:   original_video_codec: ''
Debug:   original_audio_codec: ''
Debug:   mplayer_additional_options: ''
Debug:   mplayer_additional_video_filters: ''
Debug:   mplayer_additional_audio_filters: ''
Debug:   win_width: 704
Debug:   win_height: 396
Debug:   win_aspect(): 1.777778
Debug:   starting_time: 0.000000
Debug: Core::changeSubtitle: 90000
Debug: Core::changeSubtitle: ID: -1
Debug: Core::tellmp: 'sub_select -1'
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: Core::changeAspectRatio: 1
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: Core::setVolume: 52
Debug: Core::tellmp: 'volume 52 1'
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: Core::displayMessage
Debug: Core::setVolume: 52
Debug: Core::setVolume: 52
Debug: Core::setVolume: 52
Debug: Core::setGamma: 0
Debug: Core::tellmp: 'gamma 0 1'
Debug: Core::displayMessage
Debug: Core::changePanscan: 1.000000
Debug: Core::displayMessage
Debug: Core::updateWidgets
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::newMediaLoaded
Debug: Recents::add: '/media/hda4/Heroic Age/[Your-Mom]_Heroic_Age_-_06_[C0752A13].mkv'
Debug: BaseGui::updateRecents
Debug: Playlist:: getMediaInfo
Debug: BaseGuiPlus::updateMediaInfo
Debug: BaseGui::updateMediaInfo
Debug: mplayer reports that now it's playing
Debug: BaseGui::toggleFullscreen: 1
Debug: DefaultGui::aboutToEnterFullscreen
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::toggleFullscreen: 1
Debug: BaseGui::toggleFullscreen: 1
Debug: BaseGui::displayState: 0
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: BaseGui::toggleFullscreen: 0
Debug: DefaultGui::aboutToExitFullscreen
Debug: DefaultGui::showMainToolBar: 1
Debug: DefaultGui::showLanguageToolBar: 1
Debug: DefaultGui::updateWidgets
Debug: BaseGui::updateWidgets
Debug: BaseGui::toggleFullscreen: 0
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'Invalid command for bound key f : invalid_command             '
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: BaseGuiPlus::quit
Debug: BaseGui::closeWindow
Debug: Core::stop
Debug:    state: 0
Debug: Core::stopMplayer
Debug: Core::tellmp: 'quit'
Debug: Core::stopMplayer: Waiting mplayer to finish...
Debug: MplayerProcess::parseLine: 'X11 error: BadMatch (invalid parameter attributes)'
Debug: MplayerProcess::parseLine: ''
Debug: MplayerProcess::parseLine: 'Exiting... (Quit)'
Debug: MyProcess::procFinished
Debug: MyProcess::procFinished: Bytes available: 0
Debug: Core::processFinished
Debug: Helper::setScreensaverEnabled: 1
Debug: Core::processFinished: we_are_restarting: 0
Debug: Core::processFinished: play has finished!
Debug: BaseGui::displayState: 2
Debug:  exit_status: 0
Debug: MplayerLayer::playingStopped
Debug: Core::stopMplayer: Finished. (I hope)
Debug: DefaultGui::saveConfig
Debug: BaseGuiPlus::saveConfig
Debug: Core::saveMediaInfo
Debug: MediaSettings::save
Debug: Playlist::saveSettings
Debug: Recents::save
Debug: global_end
Debug: Preferences::save

---

### Post by Shinoda on 2007-07-20
[**Version 0.5.29-qt4-0720**]("http://content-type.com/1178818388/smplayer_0.5.29-qt4-0720_i386.deb.htm")
[list]
[*]Fix with the myprocess stuff. A connection was not made. This could  make that the screensaver weren't turned on.
[*]Some changes in mplayerwindow. Now it knows when a video starts or stops so it could manage clearing or not the video background. This was previously done in core. It also has a fix, now the video background stops repainting just *before* the mplayer process starts, instead of doing it when it already has started. This could fix that the video window could still get black sometimes.
[*]Shortcut editor: the new dialog for editing key shortcuts comes back. The problems are not fixed, you can't enter yet keys like "Tab" but for those cases I've added a button "Capture". When toggled it will try to capture the shortcut (as before), otherwise you can freely edit the shortcut as regular text.
[/list]

---

### Post by Shinoda on 2007-07-23
[**Version 0.5.29-qt4-0722**]("http://content-type.com/895671196/smplayer_0.5.29-qt4-0722_i386.deb.htm")
[list]
[*]Updated the Romanian, Russian and Ukrainian translations.
[*]Bug fix: exit from fullscreen when playing an audio file.
[*]Bug fix: the end of file is signaling once the process has finished.
[*]In the info window, note it prints the absolute file path, instead of   the directory only.
[*]Bug fix: the size of the main window might be much bigger than it should when playing a file passed through command line. I think this is fixed now.
 The problem was that the file begins to play when the main window is not shown yet. Anyway this part of the code is a mess and has to be fixed.
[/list]

---

### Post by Shinoda on 2007-07-23
[**Version 0.5.29-qt4-0723**]("http://content-type.com/-1869571799/smplayer_0.5.29-qt4-0723_i386.deb.htm")
[list]
[*]Updated the German, Polish and Ukrainian translations.
[*]Started to port the network stuff (for the single instance). Implemented a blocking client. This makes things a lot easier. Previously this was done in a main window, which waited hidden until knowing if it can show (no other running instance) or quit. Now the connection to another instance is done in main.cpp with 2 or 3 lines of code, and before creating the main window. This is *much faster*. Now the file passed to the running instance starts to play almost instantaneously.
 The code (myclient.h, myclient.cpp) is quite simple and does few checks, and I don't even know if it is correctly implemented. I'll try to improve it (this is the first time I use QTcpSocket, and the 2nd time I do something relative to networking).
 There's a problem, though. For simplicity the main window always shows. This is a problem if you use to leave SMPlayer running in the system tray for the whole session, as when you enter the next session the main window of SMPlayer will be visible. I'll try to fix it in the future.
[/list]

---

### Post by Shinoda on 2007-07-24
[**Version 0.5.29-qt4-0724**]("http://content-type.com/-505957231/smplayer_0.5.29-qt4-0724_i386.deb.htm")
[list]
[*]Some fixes in myclient. Now uses UTF-8 to encode the text, the timeout is set to 200 ms.
 Anyway I'm not sure this is properly done. For instance if it tries to read a line from the server just before sending the data, only the first line is sent, the rest is lost.
[*]Fix: if you don't pass any file to the 2nd instance, it won't show.
[*]Fix: tray icon: it will remember again if the main window was hidden on  startup.
[/list]

---

### Post by Shinoda on 2007-07-25
[**Version 0.5.29-qt4-0724-2**]("http://www.ifpost.com/ifpost/download/6699443372436043")
[list]
[*]More fixes in myclient.cpp.
[*]Fix: when a video finished and a 2nd one started to play from the playlist, the setting for not repainting the window background was ignored.
[/list]

---

### Post by Shinoda on 2007-07-26
[**Version 0.5.29-qt4-0725**]("http://www.ifpost.com/ifpost/download/4807329903170676")
[list]
[*]Properly fixed a problem with a signal.
[*]Got rid of the QTextStream in myclient.cpp.
[*]By user request: added a new option in Preferences->Interface: Change volume on every file. If checked SMPlayer will remember the volume of every file, and will be restored when played again. For new files the default volume will be used. That was the normal behavior until now. The new thing is if you uncheck it. In this case SMPlayer will never change the volume when a file is loaded. Problem: on startup SMPlayer won't know the current volume value, the volume slider will be wrong.
[/list]

---

### Post by Shinoda on 2007-07-27
[**Version 0.5.29-qt4-0727**]("http://content-type.com/151297859/smplayer_0.5.29-qt4-0727_i386.deb.htm")
[list]
[*]Updated the Japanese, Russian, German, Ukrainian and French translations.
[*]Set the new option dont_change_volume to false as default, as it seems that MPlayer in Windows starts to play all videos with a very high volume.
[*]If the name of the executable (without extension) is "smplayer_portable" then the option -ini-path will be activated (that means that SMPlayer will look for the config file in the app path).
[*]The volume icon in Preferences->Interface is hidden so the dialog is not so wide.
[*]Some changes in the widgets of Preferences->Interface. Enabled the changing of style again.
[*]I started to document some of the classes for doxygen.
[/list]

---

### Post by Shinoda on 2007-07-30
[**Version 0.5.29-qt4-0730**]("http://content-type.com/569938424/smplayer_0.5.29-qt4-0730_i386.deb.htm")
[list]
[*]Updated the French translation.
[*]Some small, but important fixes for Windows.
[*]New option for command line that I think it could be very useful: -action
 This option passes the specified action to an already running instance. For instance, you're watching a video in SMPlayer, then you type:
   *smplayer -action pause* and the video will be paused.
   *smplayer -action fullscreen* will toggle the video to fullscreen.
 This will allow to control SMPlayer with a remote control. You can see a list of all available actions in "Preferences->Keyboard and mouse". Under the "Name" column in the shortcut editor you've got all action's names.
 When using -action all other parameters (except ini-path) are ignored. So if you want to open a movie and enter in fullscreen, this is NOT valid:
   *smplayer movie.avi -action fullscreen*
   But you can do it in two steps:
   *smplayer movie.avi*
   *smplayer -action fullscreen*
   The exit code will be 0 if the -action option is successful and -1 if there's an error.
[/list]
 
**Version 0.5.29-qt4-0729** [missed]
[list]
[*]Updated the Polish translation.
[*]Fix: if the MPlayer path is a relative path, don't convert it to an absolute one. Otherwise SMPlayer may not work in external devices as it might not find MPlayer.
[*]Single instance: ported the server, and deleted old code. And now changes in the server (Preferences->Interface) don't require to restart the application.
[*]Some fixes with the style stuff in Preferences->Interface.
   BTW, it seems that changing style still crashes the app from time to time, a Qt bug?
[/list]

---

### Post by Shinoda on 2007-08-02
[**Version 0.5.29-qt4-0801**]("http://content-type.com/-648360080/smplayer_0.5.29-qt4-0801_i386.deb.htm")[LIST]
[*]Updated the German translation.
[*](Windows) Added some code to prevent that the monitor turns off when watching a video (Not tested yet).
[*]Disabled some code in helper.cpp, as it's not needed anymore.
[*]Renamed preferencesdialog2 to preferencesdialog.[/LIST]

---

### Post by Chymera on 2007-08-02
[http://smplayer.sourceforge.net/linux/download_en.php](http://smplayer.sourceforge.net/linux/download_en.php) , the page you mentioned for download, gives a 404 error, where can i get the packages now?

---

### Post by rvm4000 on 2007-08-02
[http://smplayer.sourceforge.net/en/linux/download.php](http://smplayer.sourceforge.net/en/linux/download.php)

---

### Post by Chymera on 2007-08-02
10x

the current note below the development package reads:
> currently SMPlayer is being ported to Qt 4. These versions could be really unstable. You're warned.
is it that serious? (ie can it crash my system?), if so, do you have any idea when porting it will be finished?

---

### Post by rvm4000 on 2007-08-02
Hi, I'm the developer of smplayer.

It can't crash your system.

It means that the porting to Qt 4 requires to change a lot of code, and there's the possibility that some current features stop working or don't work as expected.

You can get an updated list of known broken things [here](http://www.phpbbplanet.com/smplayer/viewtopic.php?t=223) (currently there are none).

There are two things still to be ported: the playlist and the main window. Unfortunately I think these will be the hardest parts to port and I estimate some things will break while doing it.

---

### Post by Chymera on 2007-08-03
so that means it won't work with qt3 anymore?

---

### Post by rvm4000 on 2007-08-03
No. Version 0.5.21 is the last one that can be compiled with Qt 3.

---

### Post by Shinoda on 2007-08-03
[**Version 0.5.29-qt4-0803**]("http://content-type.com/1198206507/smplayer_0.5.29-qt4-0803_i386.deb.htm")
[list]
[*]Updated the German translation.
[*]Trying to keep pause after taking a screenshot.
[*]Moved options for volume from Preferences->Interface to General->Video & audio (which required to redesign the Interface section).
[*]Hidden the option "Use -subfont" as it seems that new SVN releases of mplayer don't require it. Also that option is not documented in the manpage.
[/list]

---

### Post by Shinoda on 2007-08-05
[**Version 0.5.29-qt4-0804**]("http://content-type.com/1694820079/smplayer_0.5.29-qt4-0804_i386.deb.htm")
[list]
[*]Updated the German and Ukrainian translations.
[*]The message "Screenshot taken..." is not displayed in the OSD if the video is in pause. This is to prevent that the video advances one frame.
[*]Some changes in the about dialog.
[*]Changes in some UI files.
[*]Added shortcuts in the Interface and Mouse sections in Preferences.
[/list]

---

### Post by Shinoda on 2007-08-07
[**Version 0.5.29-qt4-0807**]("http://content-type.com/1217375798/smplayer_0.5.29-qt4-0807_i386.deb.htm")
[list]
[*]Updated the Chinese (zh_CN), Ukrainian, German, Polish and French  translations.
[*]Removed obsolete translations in the *.ts files.
[*]Compiled again without option to change style. It still causes crashes.
[/list]

---

### Post by Shinoda on 2007-08-08
[**Version 0.5.29-qt4-0808**]("http://content-type.com/-188716194/smplayer_0.5.29-qt4-0808_i386.deb.htm")
[list]
[*]Added the updated qt_fr.qm sent by Kud Gray.
[*]Now "make clean" will only delete the smplayer_*.qm files in the translation  folder, to keep the qt_*.qm ones.
[*](Linux) Try to load first the qt_*.qm from the smplayer translation path, and if that fails then try to load from the Qt translation path (previously it was the opposite).
[*]Ported timeslider.h, timeslider.cpp and some small changes in other files.
[*]Now the moc_*.cpp files are included in the *.cpp files. This reduces the compilation time. In my computer, previously it took about 2 minutes, now it takes 1:30. This also made me find serious mistakes in some headers.
[*]Added shortcuts in the General, Drives and Performance sections in preferences. (Translators are gonna "love" this change...)
[/list]

---

### Post by Shinoda on 2007-08-09
[**Version 0.5.29-qt4-0809**]("http://content-type.com/652121594/smplayer_0.5.29-qt4-0809_i386.deb.htm")[LIST]
[*]Updated the German, Polish, Russian and Ukrainian translations.
[*]I started to port the playlist. Ported things: the toolbar, the actions, and the popup menu (See the "broken things" below).
 Other minor changes: Q3ValueList -> QList, Q3TextStream -> QTextStream (I hope not, but there's the possibility that something has broken).
Now the playlist is not a QMainWindow, but a QWidget (previously I had to use a QMainWindow because in Qt 3 it's not possible to add a toolbar to a normal widget, now at last I can do what I initially wanted).
   You'll see that now the playlist looks slightly different.
   Still to port: the list view (which will be the hardest part) and drag&drop.
[*]Fixed a bug in the playlist. The "length" field of the items was incorrectly read when loaded from the config file.

**Broken things:**
[*]The playlist actions are not shown in the actions' editor. Reason: now the playlist uses QActions while the actions' editor shows Q3Actions (used in the main window).[/LIST]

---

### Post by Shinoda on 2007-08-09
[**Version 0.5.29-qt4-0810**]("http://content-type.com/-2138198828/smplayer_0.5.29-qt4-0810_i386.deb.htm")
[list]
[*](Playlist) Using now a QTableWidget. This is the area where the items of the list are shown. Please test if everything is ok (moving items, selecting items, deleting selected items...).
   Still to port the drag&drop code.
[*](Windows) When changing the audio track, MPlayer doesn't keep the volume (it's louder). Added a workaround, SMPlayer will restore the volume just after the change of the audio track.

**Broken things:**
[*]The playlist actions are not shown in the actions' editor. Reason: now the playlist uses QActions while the actions' editor shows Q3Actions (used in the main window).
[/list]

---

### Post by Shinoda on 2007-08-10
[**Version 0.5.29-qt4-0811**]("http://content-type.com/-689462529/smplayer_0.5.29-qt4-0811_i386.deb.htm")
[list]
[*](Playlist) Ported the drag&drop. Easier than expected, less code than with Qt 3 and no extra code needed to support Firefox.
[*]Some small changes in playlist: no alternating row colors (doesn't look good in Windows), bigger icons in the table.
[*]So the port of the playlist is finished.
[*]Internal changes in core.

**Broken things:**
[*]The playlist actions are not shown in the actions' editor. Reason: now the playlist uses QActions while the actions' editor shows Q3Actions (still used in the main window).
[/list]

---

### Post by Shinoda on 2007-08-11
[**Version 0.5.29-qt4-0812**]("http://content-type.com/693283225/smplayer_0.5.29-qt4-0812_i386.deb.htm")
[list]
[*]Updated the Japanese and French translations.
[*]Trying to reduce warnings when compiling with QT3_SUPPORT_WARNINGS. There's still a lot. This requires a lot of changes, simple in most of cases, but there's always the possibility that something could break.

**Broken things:**
[*]The playlist actions are not shown in the actions' editor. Reason: now the playlist uses QActions while the actions' editor shows Q3Actions (still used in the main window).
[/list]

---

### Post by pickarooney on 2007-08-12
Is it possible in any recent version of smplayer to display subtitles in the black part of the screen beneath a widescreen video?

---

### Post by rvm4000 on 2007-08-12
Video->Aspect ratio->4:3 letterbox

That will add a black border on which subtitles will be displayed.

---

### Post by Shinoda on 2007-08-12
[**Version 0.5.29-qt4-0813**]("http://content-type.com/-367907538/smplayer_0.5.29-qt4-0813_i386.deb.htm")
[list]
[*]Updated the Romanian translation.
[*]Added a new option for the config file: restore_pos_after_fullscreen (in section [Preferences]). If its value is "true" then the main window will save the current position on screen and restore it again when exiting from fullscreen mode. The default value is "true" for Windows and "false" for Linux. Change it if the main window moves up or down after exiting from fullscreen mode.
[*](By user request) Added a new option in Preferences->Interface: "Remember position and size" (of the main window). Checked by default.
[*](By user request) Added two new options in Preferences->General->Video & audio: "Direct rendering" and "Double buffering".

**Broken things:**
[*]The playlist actions are not shown in the actions' editor. Reason: now the playlist uses QActions while the actions' editor shows Q3Actions (still used in the main window).
[/list]

---

### Post by Shinoda on 2007-08-20
[**Version 0.5.30-qt4-0819**]("http://content-type.com/1772810749/smplayer_0.5.30-qt4-0819_i386.deb.htm")
 
[list]
[*]Updated the Japanese translation.
[*]Undid something with submenus. I realized there's an easy way.
[*]Ported Video->Denoise.
[*]Ported Video->Size. Now you can add shortcuts for these options. But unfortunately an old problem previously fixed comes back: if you select an already selected option it will do nothing. That means that if you resize the window manually and then select Video->Size->100% it won't resize to the original size. I'll try to fix it in the future.
[*]Ported Video->Deinterlace.
[*]Ported Audio->Channels.
[*]Ported Audio->Stereo mode.
[*]Ported Video->Aspect ratio.
[*]Added the denoise filters into the Video->Filters menu.
[/list]
 
**Version 0.5.30-qt4-0818** [missed]
 
[list]
[*]Updated the Ukrainian translation.
[*]Continuing with the boring task of porting the menus.
[*]Created myactiongroup, to make easy creating menus where only one of  the options should be checked.
[*]Now the menu Options->OSD uses this new system. And the good thing is  that options can have shortcuts.
[/list]
 
**Version 0.5.30-qt4-0817** [missed]
 
[list]
[*]Updated the French translation.
[*]Actions' editor: only save or load actions with a name.
[*]Ported the floating control.
[*]baseguiplus and defaultgui almost ported.
[*]A few changes in basegui. Still a lot of work to do with the menus.
[/list]
 
**Version 0.5.30-qt4-0816** [missed]
[list]
[*]Started to port the main window. There's a lot of things to do. Today I've just made it to compile and a few other changes to make it show the toolbars properly. WARNING: there might be something broken.
[*]The action's editor shows now QActions, instead of Q3Actions, as the  main window now uses QActions.
[/list]
 
**Version 0.5.29-qt4-0815** [missed]
[list]
[*]Updated the Traditional Chinese, German, Ukrainian, Russian and Simplified Chinese translations.
[*]The icons in File properties->Info didn't appear. Fixed.
[*]Renamed the icons starting with the letter "x". For example, "xnext.png" is now "next.png". Anyway if an icon with the new name is not found it will still look for an icon with the old name to keep compatibility with the icon's themes.
[/list]
 
**Version 0.5.29-qt4-0814** [missed]
[list]
[*]Updated the French, German and Polish translations.
[*]Changed the behavior of "Use postprocessing" and "Volume normalization" in Preferences->General. Previously if you checked "Use postprocessing" for instance, then all videos would use postprocessing, no matter of the setting in Video->Filter->Postprocessing. Now this specifies the default setting for new videos. If checked, all new videos you open will have the option Video->Filter->Postprocessing enabled but you **can** disable it if you want. Previously this wasn't possible.   I think this behavior is more consistent.
[*]Ported images.h/images.cpp and moved to the new resource system. Right now the only thing still to be ported is the main window.
[/list]

---

### Post by ntlam on 2007-08-20
I just installed:

Version 0.5.30-qt4-0819

Everything seems fine

Thanks

I'll see if it's unstable as it's warned...

---

### Post by Shinoda on 2007-08-21
[**Version 0.5.30-qt4-0820**]("http://content-type.com/1578946171/smplayer_0.5.30-qt4-0820_i386.deb.htm")
[list]
[*]Updated the Romanian, German, Polish and Ukrainian translations.
[*]Now the maximum value for volume is 100 instead of 99.
[*]Ported Open->Recent files. And some fixes: now if the list is empty the submenu won't appear. You can also set the max. number of items in the list to 0 in Preferences->Interface.
[*]Ported the rest of the menus: audio and subtitle track selection, title, chapter and angle submenus. I left this for the end for a reason: it was to be the hardest part and very error-prone. So test it, it wouldn't be strange if there were crashes or weird things. BTW, the angle submenu is completely untested (I don't have any multi-angle DVD).
[/list]

---

### Post by Shinoda on 2007-08-22
[**Version 0.5.40**]("http://content-type.com/1661741972/smplayer_0.5.40_i386.deb.htm")
[list]
[*]Ported the drag&drop in main window.
[*]The file properties dialog was still using a Q3GroupBox. Fixed. Now SMPlayer won't be linked anymore to the qt3support library. :)
[*]Ported the code to embed the playlist in the main window. It's not compiled by default because there are still some things to fix but you can try it, it works better than before (there's even an animation when you move the playlist to the top area). To do it change the value of DOCK_PLAYLIST to 1 in config.h before compiling.
[*]Reduced the number of warnings when compiling with QT3_SUPPORT_WARNINGS.  This change is very error-prone.
[/list]
[list]
[*]Ported to Qt 4. Easy to say but it took almost 2 months, and it's not completely finished yet (still using some deprecated functions).
[/list]

---

### Post by Shinoda on 2007-08-22
[**Version 0.5.41**]("http://content-type.com/-1136273300/smplayer_0.5.41_i386.deb.htm")
[list]
[*]Updated the Ukrainian and Russian translations.
[*]Fixed the problem with the Video->Size menu. All options will work now  no matter the previous selection.
[*]Some changes in Install.txt, just to mark some obsolete sections and make clear that it can only be compiled with Qt >= 4.2.
[/list]

---

### Post by Shinoda on 2007-08-23
[**Version 0.5.42**]("http://content-type.com/-379201611/smplayer_0.5.42_i386.deb.htm")
[list]
[*]Serious bug: a lot of actions were missing in the actions' editor. Fixed.
[*]More improvements with the playlist embedded in the main window: now it should be properly hidden/shown when toggling compact and fullscreen mode, and when clicking on the systray icon. Also the playlist button in toolbar (and menu) should be updated when the playlist is closed by clicking on its close button. But you'll see that now the main window is not resized when the playlist is shown or hidden. I left this problem for the end (it's not trivial). Anyway you can press CTRL-1 to force a resize.
This code is not compiled by default yet. If you want to see it, change the value of DOCK_PLAYLIST to 1 in config.h before compiling.
[/list]

---

### Post by Shinoda on 2007-08-25
[**Version 0.5.43**]("http://content-type.com/1034006965/smplayer_0.5.43_i386.deb.htm")
[list]
[*]Updated the Italian translation.
[*]Small fix for Windows in the fullscreen code.
[*]Removed the "&" characters in the description of the actions in the  actions' editor.
[*]Using less deprecated functions.
[/list]

---

### Post by PatheticMoFo on 2007-08-26
I'm getting a dependency error about libc6 with the latest Version 0.5.43:

> dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on libc6 (>= 2.6); however:
  Version of libc6 on system is 2.5-0ubuntu1

Is libc6 >= 2.6 even in the Ubuntu repositories?

---

### Post by Shinoda on 2007-08-26
> **PatheticMoFo said:**
> Is libc6 >= 2.6 even in the Ubuntu repositories?
That's the current version in Gutsy, but you may install it in Feisty anyway. Get it [here]("http://packages.ubuntu.com/gutsy/base/libc6").

---

### Post by PatheticMoFo on 2007-08-26
Thanks, forgot to mention I was using feisty, sorry. But while installing the gutsy version did work, and everything appeared to go smoothly, now apt-get wants me to uninstall 128 packages, so I'm going to have to downgrade libc6 and uninstall smplayer. Thanks, though.

---

### Post by Shinoda on 2007-08-26
You can always use a previous version of SMPlayer until Gutsy is released in October. It's not that far away, and maybe you won't miss or really need most if not all changes in the player until then anyway. Unless you're not planning to upgrade, of course.

---

### Post by rvm4000 on 2007-08-26
And you can always compile smplayer by yourself. It's quite easy.

---

### Post by Shinoda on 2007-08-26
[**Themes Version 0.1.4**]("http://content-type.com/-1380802906/smplayer-themes_0.1.4_all.deb.htm")
[list]
[*]Updated the Tango theme.
[/list]

---

### Post by Shinoda on 2007-08-26
[**Version 0.5.44**]("http://content-type.com/-1248547791/smplayer_0.5.44_i386.deb.htm")
[list]
[*]Updated the Polish, German and French translations.
[*]When trying to stop a video, the MPlayer process will be killed if it doesn't finish within 3 seconds.
[*]New dialog to enter a URL (the playlist check doesn't work yet).
[*]Don't load actions from playlist to the actions' editor as it seems they are already there from the main window (in Qt 4.3 they appear twice).
[/list]

---

### Post by PatheticMoFo on 2007-08-27
> **rvm4000 said:**
> And you can always compile smplayer by yourself. It's quite easy.

Yeah I was gonna do that anyway, but when I saw that there were deb's available I got all lazy lol. Oh well, VERY nice app, by the way, once I got over the lazyness. GREAT for audiobooks too. Much thanks.

---

### Post by rvm4000 on 2007-08-27
Here you have a package for version 0.5.44 compiled on a Kubuntu 7.04 (with no updates): [smplayer_0.5.44_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.44_i386.deb?use_mirror=osdn)

---

### Post by Chymera on 2007-08-27
can smplayer play .rm files?

---

### Post by PatheticMoFo on 2007-08-27
> **rvm4000 said:**
> Here you have a package for version 0.5.44 compiled on a Kubuntu 7.04 (with no updates): [smplayer_0.5.44_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.44_i386.deb?use_mirror=osdn)

Oh sorry, I already compiled it for myself. I guess this'll be for anyone else who can't/won't upgrade to the gutsy packages yet.

> **Chymera said:**
> can smplayer play .rm files?
Yes it can, just tested it myself.

---

### Post by rvm4000 on 2007-08-28
> **Chymera said:**
> can smplayer play .rm files?

I think you need the w32codecs package installed for that.

---

### Post by Shinoda on 2007-08-28
[**Version 0.5.45**]("http://content-type.com/-259426980/smplayer_0.5.45_i386.deb.htm")[LIST]
[*]Updated the Ukrainian and German translations.
[*]The playlist check in the open URL dialog works. If checked the option -playlist will be added to the MPlayer command line. (Internally some text will be appended to the URL, so SMPlayer can recognize it. This may seem ugly (and it is) but allows to add the URL to a playlist or to the recent files menu, and it will still work.)
[*]Added an icon to the open URL dialog (url_big.png).
[*]Added two options for the config file: *enable_audiocd_on_windows* and *enable_vcd_on_windows*. It seems that MPlayer on Windows doesn't have support for VCDs and Audio CDs (at least not the build supplied with SMPlayer). Setting these options to "true" will enable the entries in the open menu.[/LIST]

---

### Post by Chymera on 2007-08-28
> **rvm4000 said:**
> I think you need the w32codecs package installed for that.

I installed it and don't get any output... except some sound... occasionally

---

### Post by Shinoda on 2007-08-28
[**Version 0.5.46**]("http://content-type.com/674610859/smplayer_0.5.46_i386.deb.htm")[LIST]
[*]Added the option -playlist for command line. This option should be prepended in front of a filename (URL or whatever). This option will make MPlayer to treat the file as a playlist. This option has nothing to do with SMPlayer's playlist! In fact SMPlayer won't have any control over the playlist at all. For SMPlayer it will just be like a single file.
[*]Added the option -help for command line. It will show a helping message.
BTW, the translators will have a challenge, as keeping the formatting  is not easy. (Take a look at the Spanish translation.)
[*]Added the option -close-at-end for command line. The main window will be  closed when the file/playlist finishes.[/LIST]

---

### Post by Shinoda on 2007-08-29
[**Themes Version 0.1.5**]("http://content-type.com/401018499/smplayer-themes_0.1.5_all.deb.htm")
[list]
[*]Added the Gartoon theme created by Kud Gray, based on the Gartoon Icons for Gnome.
[*]Added the create_deb.sh script.
[/list]

---

### Post by ntlam on 2007-08-29
Hi Master,
How can I update Smplayer to newer version?

---

### Post by ntlam on 2007-08-29
I just downloaded the version smplayer-0.5.46.tar.bz2
extracted it
go to smplayer-0.5.46
run ./create_deb.sh
then cd ..
then ls
but there is no deb file to run the next step.
Did I do something wrong?

---

### Post by rvm4000 on 2007-08-29
Probably you don't have installed some of the development packages required. I think they are the following:

libqt4-dev 
fakeroot 
build-essential 
dpkg-dev

Anyway I created this morning a package for Feisty of the latest release:
[http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb)

---

### Post by ntlam on 2007-08-29
> **rvm4000 said:**
> Probably you don't have installed some of the development packages required. I think they are the following:

libqt4-dev 
fakeroot 
build-essential 
dpkg-dev

Anyway I created this morning a package for Feisty of the latest release:
[http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb)

I did install them at the very beginning. BTW I will try ur package

---

### Post by Shinoda on 2007-08-30
> **ntlam said:**
> Hi Master
You're too kind. =)
> **ntlam said:**
> How can I update Smplayer to newer version?
Aren't my packages working for you?
> **ntlam said:**
> there is no deb file to run the next step.
Please post the output you get after [FONT=Courier New]./create_deb.sh[/FONT].

---

### Post by Shinoda on 2007-08-30
[**Themes Version 0.1.6**]("http://content-type.com/22457596/smplayer-themes_0.1.6_all.deb.htm")[LIST]
[*]Updated the Tango theme.[/LIST]

---

### Post by Shinoda on 2007-08-30
[**Version 0.5.47**]("http://content-type.com/-652144651/smplayer_0.5.47_i386.deb.htm")
[list]
[*]Updated the Russian, German, French and Romanian translations.
[*]Now the helping messages (for -help) are formatted automatically by a function, making it easy to translate these messages. I apologize for yesterday's madness. As compensation I have adapted myself the translations I received today.
   There's nothing more new in this version, but I release it so other translators don't go crazy.
[/list]

---

### Post by ntlam on 2007-08-30
> **Shinoda said:**
> You're too kind. =)

Aren't my packages working for you?

Please post the output you get after [FONT=Courier New]./create_deb.sh[/FONT].

I rerun ./create_deb.sh
ln: creating symbolic link `debian/debian-rvm' to `debian-rvm': File exists
dpkg-buildpackage: source package is smplayer
dpkg-buildpackage: source version is 0.5.46
dpkg-buildpackage: source changed by Ricardo Villalba <rvm@escomposlinux.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.46
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

maybe I dont have enough dependencies

---

### Post by ntlam on 2007-08-30
> **rvm4000 said:**
> Probably you don't have installed some of the development packages required. I think they are the following:

libqt4-dev 
fakeroot 
build-essential 
dpkg-dev

Anyway I created this morning a package for Feisty of the latest release:
[http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.5.46_i386.deb)

thanks again

I used your file and it seemed to work now.

---

### Post by ntlam on 2007-08-30
This problem I got on my Desktop only.

I installed smplayer on my laptop before and it worked well. But how can I update the new versions?

---

### Post by Shinoda on 2007-08-30
> **ntlam said:**
> maybe I dont have enough dependencies
Did you install the packages mentioned in step 1 of the how-to?
> **ntlam said:**
> I used your file and it seemed to work now.
What about my packages? Did you try them and, if so, didn't they work for you?
> **ntlam said:**
> how can I update the new versions?
You'll have to do it manually until SMPlayer hits the official (or any) repos or someone creates one for it.

---

### Post by ntlam on 2007-08-31
> **Shinoda said:**
> Did you install the packages mentioned in step 1 of the how-to?

What about my packages? Did you try them and, if so, didn't they work for you?

You'll have to do it manually until SMPlayer hits the official (or any) repos or someone creates one for it.

Yes I did install all packages in step 1. But then when I ran ./create... again, it did not work. I've posted the output in some above post.

---

### Post by Shinoda on 2007-08-31
> **ntlam said:**
> Yes I did install all packages in step 1. But then when I ran ./create... again, it did not work. I've posted the output in some above post.
I know, thanks, just checking. Please try again after installing debhelper then, and let me know how it goes so I may update the how-to as needed.

Can you also tell me if my SMPlayer packages work for you at all?

---

### Post by Shinoda on 2007-08-31
[**Version 0.5.48**]("http://content-type.com/-1435991769/smplayer_0.5.48_i386.deb.htm")
[list]
[*]Updated the Russian and Japanese translations.
[*]Now SMPlayer will also look for icon themes in $HOME/.smplayer/themes. In the case a theme is both in the user directory and the system directory (usually /usr/share/smplayer/themes) it will look first in the user directory. If the icon is not there then it will look in the system directory.
[*]Under Linux the buttons for color selection (Preferences->Subtitles) now look better.
[/list]

---

### Post by Shinoda on 2007-09-01
[**Themes Version 0.1.7**]("http://content-type.com/-588007743/smplayer-themes_0.1.7_all.deb.htm")
[list]
[*]New theme: Oxygen-Refit.
[*]Updated Play/styles.qss for Qt 4.
[/list]

---

### Post by Shinoda on 2007-09-02
[**Version 0.5.49**]("http://content-type.com/-1524465209/smplayer_0.5.49_i386.deb.htm")[LIST]
[*]Updated the Polish and Ukrainian translations.
[*]Fixed warnings about using deprecated setBackgroundColor.
[*]Renamed command line option -action to -send-action. This option will try to send the specified action to another running instance of SMPlayer, after that it will quit.
[*]Added a new option for command line: -actions. As opposite to -send-action, this option will run the actions in the same instance. There could be several actions, separated by spaces (and enclosed in quotes). Examples: 
   *smplayer video.avi -actions fullscreen* (the file video.avi will be  loaded, and just after that fullscreen mode will be toggled)
   *smplayer video.avi -actions "extrastereo_filter on_top"* (will load the video, and then the extrastereo filter and the stay on top options will be toggled)
 "Toggled" means: if the option was previously enabled now it will be disabled and vice versa. If you want to be sure that an option will be on or off you can pass "true" or "false" as parameter:
   *smplayer video.avi -actions "on_top true"* (the option Video->Stay on  top will be checked, no matter the previous state)
   *smplayer -actions "show_language_toolbar false"* (will hide the  language toolbar)
 Some actions are not checkable, like open_vcd, double_speed... In that case you shouldn't use "true" or "false". But if you do it will be ignored.
 If you make a mistake and enter an action that doesn't exists, you'll get a warning (in the logs or in the console) and it'll be ignored.[/LIST]

---

### Post by Shinoda on 2007-09-03
[**Themes Version 0.1.8**]("http://content-type.com/-1402302127/smplayer-themes_0.1.8_all.deb.htm")
[list]
[*]Added the Noia theme, created by Vitaliy Motsyo.
[/list]

---

### Post by ntlam on 2007-09-03
> **Shinoda said:**
> I know, thanks, just checking. Please try again after installing debhelper then, and let me know how it goes so I may update the how-to as needed.

Can you also tell me if my SMPlayer packages work for you at all?

I installed the deb package suggested by my friend **rvm4000** and it works:

[QUOTE]  Originally Posted by rvm4000  View Post
Probably you don't have installed some of the development packages required. I think they are the following:

libqt4-dev
fakeroot
build-essential
dpkg-dev

Anyway I created this morning a package for Feisty of the latest release:
[http://downloads.sourceforge.net/smp....5.46_i386.deb](http://downloads.sourceforge.net/smp....5.46_i386.deb)[QUOTE]

---

### Post by Shinoda on 2007-09-04
> **ntlam said:**
> I installed the deb package suggested by my friend **rvm4000** and it works
Yes, I understand that. What I'm asking though is for you to install the package named "debhelper" and try building SMPlayer again, as well as test my latest deb out and tell me if it works for you. I'd really appreciate it. TIA.


---

### Post by Shinoda on 2007-09-04
[**Themes Version 0.1.9**]("http://content-type.com/1429730493/smplayer-themes_0.1.9_all.deb.htm")
[list]
[*]Added the Nuvola theme, created by Nardog.
[/list]

---

### Post by Shinoda on 2007-09-04
[**Version 0.5.50**]("http://content-type.com/1204329874/smplayer_0.5.50_i386.deb.htm")[LIST]
[*]Updated the German, Ukrainian and Japanese translations.
[*]Hopefully fixed a problem with the playlist actions not showing (or appearing duplicated) in the actions editor. Now it works ok with Qt 4.2.3 but I won't be sure the problem is really fixed until I test it with Qt 4.3.
[*]Added the option Subtitles->Use S.S.A./A.S.S. library, to make it easy to enable or disable the use of the A.S.S. lib without having to open the preferences dialog.
[*]Added new option in Preferences->General: Close when finished. If checked, the main window will be closed when the current file/playlist finishes.
Now the command line option -close-at-end will just enable that option.
[*]Added shortcuts in the Preferences->Subtitles dialog.[/LIST]

---

### Post by ntlam on 2007-09-04
> **Shinoda said:**
> Yes, I understand that. What I'm asking though is for you to install the package named "debhelper" and try building SMPlayer again, as well as test my latest deb out and tell me if it works for you. I'd really appreciate it. TIA.

holle,

yes it worked after I installed the debhelper. how did you know that I did not have the debhelper?

---

### Post by ntlam on 2007-09-04
and the latest version works fine....

---

### Post by Shinoda on 2007-09-04
> **ntlam said:**
> yes it worked after I installed the debhelper. how did you know that I did not have the debhelper?
By looking at the output you posted earlier:
> **ntlam said:**
> dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5)
Sometimes it helps to actually read it, you know. =P


> **ntlam said:**
> and the latest version works fine....
Alright then. Thanks a lot, mate.

---

### Post by Shinoda on 2007-09-05
[**Themes Version 0.1.10**]("http://content-type.com/1615959962/smplayer-themes_0.1.10_all.deb.htm")[LIST]
[*]Added the Breathless theme, by Kud Gray.[/LIST]

---

### Post by Shinoda on 2007-09-05
[**Version 0.5.51**]("http://content-type.com/-1119001528/smplayer_0.5.51_i386.deb.htm")
[list]
[*]Updated the Chinese (zh_CN), French, Romanian, German, Ukrainian and  Polish translations.
[*]By mistake, the new option "close when finished" was enabled by default.  Now that option will be disabled by default.
[*](Windows) When using Qt 4.3, inforeader fails, it can't read the output of MPlayer. That means there won't be info about the codecs, demuxers, output drivers... I don't know why that happens, but disabling redirection of the MPlayer output to a temporary file makes it work again. I also realized that QProcess in Qt 4.3 works much better, so it's not necessary to send the MPlayer output to a temporary file. So now if compiled with Qt 4.3 it won't use temporary files, fixing the problem with inforeader. Still there's a problem, if compiled with Qt 4.2.3 but using the Qt 4.3 dll's, the problem will still be present. Unless...
[*]Now inforeader uses QProcess (not myprocess), so now it shouldn't be  affected by the problem metioned before.
[*]It doesn't try to create the app home directory ($HOME/.smplayer) if -ini-path is used.
[/list]

---

### Post by Shinoda on 2007-09-07
[**Version 0.5.52**]("http://content-type.com/338310401/smplayer_0.5.52_i386.deb.htm")
[list]
[*]Updated the Russian translation.
[*]Fix in the open URL dialog: the text should be selected now.
[*]Fix for Qt 4.3.1 under Windows: after playing an audio file the video window didn't show when playing a video.
[*]Experimental: add file to be opened in the playlist (deleting the whole playlist first). This prevents that when a file finishes, an item from an old playlist starts to play.
[*]Added a context menu for when clicking on a toolbar.
[/list]

[**Themes Version 0.1.11**]("http://content-type.com/631265682/smplayer-themes_0.1.11_all.deb.htm")
[list]
[*]New version of the Breathless theme with smaller icons (32x32 instead of 128x128).
[/list]

---

### Post by Shinoda on 2007-09-08
[**Version 0.5.53**]("http://content-type.com/971856223/smplayer_0.5.53_i386.deb.htm")
[list]
[*]Some fixes in the code to add the file to play in the playlist.
[*]Some more improvements on the playlist embedded in the main window: now the main window resizes when the playlist is docked/undocked. It also remembers its state on startup.
For the first time this code will be compiled as default so other people could test it. Anyway there's two known issues: the main window doesn't resize properly when playing an audio file (no video window) and the playlist is undocked (maybe another Qt 4.2.3 bug?). And to avoid some problems when exiting from fullscreen, the playlist is made floatable when entering in fullscreen mode.
 How to use it? The playlist will appear by default docked in the bottom area. You can move it to the top area if you want, or make it floatable by dragging it outside the window. You can dock it again by dragging the playlist to the bottom or top areas of the main window (there's also a button in the title bar for this).
[*]Added a help message about the option "It's a playlist" in Open->URL.
[/list]

---

### Post by Shinoda on 2007-09-09
[**Version 0.5.54**]("http://content-type.com/2011422046/smplayer_0.5.54_i386.deb.htm")
[list]
[*]Updated the German, Ukrainian and Romanian translations.
[*]Disabled again the playlist in main window as it has serious problems with Qt 4.3.1 (at least in Windows).
[*]The trailing "/" in DVD device paths won't be removed. It seems that sometimes it's necessary. But be careful, Windows users, when playing a DVD from a folder in the hard disc the path shouldn't end in "/", that would make MPlayer fail.
[*](By user request) Added "Video->Flip image" which flips the image upside-down. This option will affect the current video only, it's not a global option.
[*]Now you can move the toolbars wherever you want.
[*]Added the option "Create index if needed" in Preferences->Performance. The option will pass -idx to MPlayer. From MPlayer manpage: "Rebuilds index of files if no index was found, allowing seeking. Useful with broken/incomplete downloads, or badly created files."
 
[/list]

---

### Post by Shinoda on 2007-09-09
[**Version 0.5.55**]("http://content-type.com/84619094/smplayer_0.5.55_i386.deb.htm")
[list]
[*]Updated the Japanese, Polish, Ukrainian, German, Romanian and Dutch  translations.
[*]The trailing "/" in DVD device paths will be removed again, but not if used with drive letters (E:/ for instance). It seems that sometimes it's necessary to enter the drive that way in order to play a DVD.
[*]Fixed all deprecated warnings. Now SMPlayer can be compiled without QT3_SUPPORT defined. Still using deprecated signals (for instance for QActions) but I've got no warnings about them so it'll be difficult to fix unless I compile Qt with no Qt3 support at all (I guess).
[/list]

---

### Post by TheMono on 2007-09-10
Not wanting to steal anyones thunder, but I've set up a launchpad PPA for smplayer. These are built with the Ubuntu build system for both AMD64 and I386, for feisty. Packages available are smplayer and smplayer-themes (the equivalents of what Shinoda is offering), and also an smplayer-classic package for the pre-qt4 version. You cannot install both smplayer and smplayer-classic.

The repository is usable by adding the following to your /etc/apt/sources.list

deb [http://ppa.launchpad.net/themono/ubuntu](http://ppa.launchpad.net/themono/ubuntu) feisty main restricted universe

After this, install smplayer (or smplayer-classic) and smplayer-themes, and they will be automatically updated as new versions become available.

---

### Post by Shinoda on 2007-09-10
> **TheMono said:**
> Not wanting to steal anyones thunder, but I've set up a launchpad PPA for smplayer.
How dare you releasing me of my duty like this? =P Seriously though, thanks. I guess there's no need for me to go on building these debs then, and to be honest I was hoping someone would set up a repo or whatnot so I could, you know, be excused. Cheers.

---

### Post by TheMono on 2007-09-10
Cool. Updated to 0.5.56 this morning. Oh, if anyone wants to use just deb packages still instead of adding a repo, you can download the repo's deb packages from here:

[http://ppa.launchpad.net/themono/ubuntu/pool/main/s/](http://ppa.launchpad.net/themono/ubuntu/pool/main/s/)

---

### Post by Shinoda on 2007-09-10
By the way, are you planning to do the same for Gutsy once it's out?

---

### Post by TheMono on 2007-09-10
Yes, Gutsy will be supported when released. There's nothing really stopping me doing it for Gutsy now, other than I don't run it so I can't test the packages. However, I will upgrade to Gutsy soon after release and the repo will go to Gutsy + Feisty for a while, then Feisty will be dropped.

If you want I can upload some gutsy packages now, and they can be in there just on the chance that they work? Although I can't see why they wouldn't.

A question for you on that note - with the debian/changelog file, the debian guidelines specify that if a package is to be built for multiple distributions, to list them separated by a space; ie, 

smplayer (0.5.56~PPA1) dapper feisty gutsy; urgency=low

However, the ubuntu build system rejects this for reason of their being no distribution named 'dapper feisty gutsy'. Do you know what the ubuntu style is for this, or if it is even possible with the ubuntu build system?

---

### Post by Shinoda on 2007-09-11
> **TheMono said:**
> If you want I can upload some gutsy packages now, and they can be in there just on the chance that they work?
It will only make a difference to me when Gutsy is released, but certainly current testers would appreciate it now, and you'd also be sparing disturbedite [the same work]("http://ubuntuforums.org/showthread.php?t=440351") you spared me.
> **TheMono said:**
> Do you know what the ubuntu style is for this, or if it is even possible with the ubuntu build system?
Sorry, I have no idea, the only thing in that file I've ever meddled with was the version numbers. Have you tried separating with commas or commas and spaces, regardless of what the guidelines say? You never know. :p

---

### Post by TheMono on 2007-09-11
I'm talking to some of the MOTU's on the mailing list, and it seems that it isn't possible. Ah well, I will just do it the long way lol. I've posted about the repository in the gutsy thread, and added support for gutsy. I haven't included smplayer-classic though as a gutsy package.

---

### Post by Shinoda on 2007-09-11
Does your PPA happen to have a PGP key, and if not could you please set one up? Much obliged. :)

---

### Post by TheMono on 2007-09-11
I would, but unfortunately PPA's do not support this at the moment. I believe that this will be fixed soon though. The source packages are signed for upload, but are then not signed by launchpad upon build. As I don't have any contact with the resulting binarys, I can't sign anything without launchpad doing it for me.

Edit: See this launchpad bug for more:

[https://bugs.launchpad.net/soyuz/+bug/125103](https://bugs.launchpad.net/soyuz/+bug/125103)

---

### Post by ntlam on 2008-02-15
Hi,

I downloaded the following package and installed it on gutsy. But Smplayer doesn't seem to play. 

smplayer_0.5+svn080116+gutsy_i386.deb

Do you have any idea?

Lam

---

### Post by rvm4000 on 2008-02-15
What does the mplayer log say? (Options->View logs)

---

### Post by ntlam on 2008-02-15
it says nothing....no words

---

### Post by rvm4000 on 2008-02-16
Did you try to play something? Until that the log is empty.

---

### Post by ntlam on 2008-02-16
here is the log after I try to play:

mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -zoom -nokeepaspect -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 58720270 -colorkey 0x020202 -monitoraspect 1.6 -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -nocache -osdlevel 0 -vf-add expand=osd=1 -noslices -vf-add screenshot -channels 2 -af scaletempo /home/nguyen/Desktop/phim/freakyfriday.divx

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/nguyen/Desktop/phim/freakyfriday.divx.
AVI file format detected.
ID_VIDEO_ID=0
ID_AUDIO_ID=1
VIDEO:  [DX50]  720x480  24bpp  23.976 fps  780.2 kbps (95.2 kbyte/s)
ID_FILENAME=/home/nguyen/Desktop/phim/freakyfriday.divx
ID_DEMUXER=avi
ID_VIDEO_FORMAT=DX50
ID_VIDEO_BITRATE=780184
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=5678.39
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Opening video filter: [screenshot]
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Couldn't find audio filter 'scaletempo'
[libaf] Couldn't create or open audio filter 'scaletempo'
Error at audio filter chain pre-init!

Exiting... (Fatal error)


Is it something wrong with Mplayer?
If I want to open Mplayer I have to use command gmplayer instead of mplayer.
Then I change mplayer --> gmplayer in the preference of Smplayer. It does not work either.

---

### Post by rvm4000 on 2008-02-16
> **ntlam said:**
> Couldn't find audio filter 'scaletempo'
[libaf] Couldn't create or open audio filter 'scaletempo'
Error at audio filter chain pre-init!

Exiting... (Fatal error)

Fortunately this is a problem very easy to fix. SMPlayer is trying to use an audio filter (scaletempo) which is not available in mplayer 1.0rc1.

Go to Preferences->General->Audio and select **No** for the option "High speed playback without altering the pitch".

You can also consider to use the new packages for smplayer and mplayer you can find in the [smplayer site](http://smplayer.sourceforge.net/downloads.php).

---

### Post by ntlam on 2008-02-16
Thanks a lot,

Now I can play most of my favourites. But still, I can not play DVDs. Everytime smplayer hangs when I try to play DVD.

I set in preference, drives as dev/cdrom

---

### Post by ntlam on 2008-02-16
and here is the log:

mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -zoom -nokeepaspect -stop-xscreensaver -subfont-autoscale 1 -subfont-text-scale 5 -subcp ISO-8859-1 -subpos 100 -contrast 0 -brightness 0 -hue 0 -saturation 0 -dvd-device /dev/cdrom -chapter 1 -dvdangle 1 -nocache -osdlevel 0 -vf-add expand=osd=1 -noslices -vf-add screenshot -channels 2 dvd://1

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing dvd://1.

*** libdvdread: CHECK_VALUE failed in ifo_read.c:2019 ***
*** for vts_attributes->last_byte + 1 >= VTS_ATTRIBUTES_MIN_SIZE ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:2019 ***
*** for vts_attributes->last_byte + 1 >= VTS_ATTRIBUTES_MIN_SIZE ***

*** Zero check failed in ifo_read.c:1535
    for c_adt->zero_1 = 0xb7b6

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1539 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1567 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***

---

### Post by ntlam on 2008-02-16
Never mind,

After I install the new version of mplayer, it runs OK now.

Thanks

---

