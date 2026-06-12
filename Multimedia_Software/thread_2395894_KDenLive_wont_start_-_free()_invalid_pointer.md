---
title: "KDenLive wont start - free(): invalid pointer"
date: 2018-07-08
forum: Multimedia Software
---

### Post by kazakore on 2018-07-08
KDenLive has stopped opening again. Last time I had an issue I deleted the ~/.config/kedenliverc and this seems to solve everything (but that was due to me changing something in the Preferences it didn't like.) This time it hasn't been used for a while but has stopped working on its own.

```
$ kdenlive
qt5ct: using qt5ct plugin
QApplication: invalid style override passed, ignoring it.
free(): invalid pointer
Aborted (core dumped)

```

The qt5ct usually works fine (in fact you can find an old thread where somebody else was having issues and I posted my terminal output from a successful boot and those lines are there) it is used to get my theme working in qt5 programs as well as gtk.

From a bit of research it seems free(): invalid pointer errors are to do with C/C++ and the way they deal with memory. Something is obviously not right here!

I tried deleting the kdenliverc file as before. No change. I apt purged and reinstalled the program as I had very little configuration changes from default (just the theme and project folder location) and this hasn't helped either.

Any idea how I can get this running again??

---

### Post by TheFu on 2018-07-08
Yes, the free() using an invalid pointer is bad, though really the free'ing of memory should be accomplished using the delete() call in a class destructor.  So ... assuming the Kdenlive guys are following normal C++ methods, then having an incorrect pointer becomes harder and the most likely problem is with incorrect libraries being called.

So, you should check all the dependencies, especially 3rd party libraries, are the correct versions.

I'd start by 
* sudo apt update 
* sudo apt upgrade
* sudo  apt full-upgrade
and if everything is fine, no errors shown, then start the program again, inside a terminal.  If there are errors, remove  kdenlive, all dependencies, and reinstall.  Pay special attention to library dependencies that include "qt" in the names.

---

### Post by kazakore on 2018-07-08
Nothing to do for any of those commands

Never seen apt full-upgrade before. Is that the same as apt-get dist-upgrade?

Have already tried removing (full purging) the application and reinstalling with no joy. Haven't checked libraries. I assume apt-cache show to list them would be a suitable methods for this? Trying now.....

---

### Post by kazakore on 2018-07-08
That wants to remove far more than I'm willing to!!

```
$ sudo apt-get remove libqt5core5a  libqt5dbus5  libqt5gui5  libqt5network5 libqt5qml5  libqt5quick5  libqt5svg5  libqt5webkit5  libqt5widgets5  libqt5xml5
Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following packages will be REMOVED
  adwaita-qt audacity cadence cadence-data cadence-tools calibre calibre-bin catia claudia drumkv1 drumkv1-common drumkv1-lv2 kded5 kdoctools5 khelpcenter kid3-core
  kid3-qt kinit kio kpackagelauncherqml kpackagetool5 krita kwayland-integration libdbusmenu-qt5-2 libgrantlee-templates5 libkf5archive5 libkf5attica5 libkf5auth5
  libkf5bookmarks5 libkf5codecs5 libkf5completion5 libkf5config-bin libkf5configcore5 libkf5configgui5 libkf5configwidgets5 libkf5coreaddons5 libkf5crash5
  libkf5dbusaddons-bin libkf5dbusaddons5 libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes5 libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 libkf5khtml-bin
  libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff5 libkf5newstuffcore5 libkf5notifications5
  libkf5notifyconfig5 libkf5package5 libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5service-bin libkf5service5 libkf5solid5 libkf5sonnetcore5
  libkf5sonnetui5 libkf5textwidgets5 libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons5 libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui5
  libkwalletbackend5-5 libmlt++3 libmlt6 libopenshot14 libphonon4qt5-4 libpolkit-qt5-1-1 libpoppler-qt5-1 libqgsttools-p1 libqt5concurrent5 libqt5core5a libqt5dbus5
  libqt5designer5 libqt5gui5 libqt5help5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5network5 libqt5opengl5
  libqt5opengl5-dev libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5script5
  libqt5scripttools5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5svg5-dev libqt5test5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5webchannel5 libqt5webkit5 libqt5widgets5 libqt5x11extras5 libqt5xml5 libqt5xmlpatterns5 libqt5xmlpatterns5-dev libquazip5-1
  libsuil-0-0 libsynfig0 melt musescore openshot openshot-qt phantomjs phonon4qt5 phonon4qt5-backend-vlc plume-creator python-pyqt5 python-pyqt5.qtsvg
  python-pyqt5.qtwebkit python3-dbus.mainloop.pyqt5 python3-dbus.mainloop.pyqt5-neonfix python3-openshot python3-pyqt5 python3-pyqt5.qtopengl python3-pyqt5.qtsvg
  python3-pyqt5.qtwebkit qasconfig qashctl qasmixer qbittorrent qjackctl qmidinet qmidiroute qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-newstuff qml-module-qtgraphicaleffects qml-module-qtmultimedia qml-module-qtqml-models2 qml-module-qtquick-controls qml-module-qtquick-controls2
  qml-module-qtquick-dialogs qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qsynth qt5-default qt5-gtk-platformtheme qt5-image-formats-plugins qt5-style-plugins qt5ct qtbase5-dev qtbase5-dev-tools qtractor qtscript5-dev qtwayland5
  rapid-photo-downloader samplv1 samplv1-common samplv1-lv2 sc3-plugins sc3-plugins-language simplescreenrecorder sonnet-plugins suil-libs supercollider
  supercollider-ide supercollider-language synfigstudio synthv1 synthv1-common synthv1-lv2 virtualbox-qt vlc vlc-plugin-qt vlc-plugin-skins2 vokoscreen
0 to upgrade, 0 to newly install, 201 to remove and 0 not to upgrade.

```


I use other of the qt apps on a daily basis so can't see it being the qt libraries at fault really.



Additional:
I have tried instead a apt-get install --reinstall (every single dependency) and it has made no difference.

---

### Post by TheFu on 2018-07-08
No risk. No reward.

Save a list of packages being removed. You can put them back.

If you remove all Qt libs, then all programs dependent on them will necessarily be removed too.  That's sorta the way dependency stuff works, AND it is exactly what you want.

If you don't understand an option, the manpage explains it.
```
$ man apt
...
       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.
....
```

And you should have a backup before doing any upgrades every week anyways.

We don't absolutely **Know** the cause of the problem, so all of this could be for nothing. It could be a bug in kdenlive and nothing you do will matter. How did you install it?  From the Canonical repos, a PPA or some other method?

---

### Post by kazakore on 2018-07-08
This is from the Canonical repos, I don't think KDenLive have one for Bionic yet and finally there is a fairly recent one in the official repos.

It was working fine a few weeks ago but I can't remember if the last time I used it was before or after (I think after but unsure) I installed some qt5 dev libs to compile some other software so it is possible something there has conflicted with it....

---

### Post by kazakore on 2018-07-11
Removed every single lib* dependency installed. Apt installed kdenlive again. No change to symptoms!

---

### Post by TheFu on 2018-07-11
1 last thing to try.
Create a new account.
Logout.
Login using that new account.
Run KdenLive - does the issue happen with a 100% fresh,new, account?

If not, then some settings you have are causing the issue.  If not, maybe 16.04 would be better until the project has a PPA for 18.04?

Clearly, neither is a great solution.

---

### Post by kazakore on 2018-07-12
Kinda good news. KDenLive have now got the ppa set up for Bionic.

The bad news is that adding it and upgrading to the latest version on there made no difference.

Also tried what you suggest, created a brand new user and tried there. Still get an error, which to my untrained eyes looks similar/related but a little different.

```
$ kdenlive
qt5ct: using qt5ct plugin
QApplication: invalid style override passed, ignoring it.
double free or corruption (out)
Aborted (core dumped)
```

---

### Post by TheFu on 2018-07-12
Seems like reloading the OS or putting one inside a virtual machine just to run KDenlive would be my next step.  If you don't already run KDE, I'd try that, since KDE uses the same libraries as KDenlive, the risks of unwanted dependencies should be less.  In theory.

That's all I got for ideas.

---

### Post by kazakore on 2018-07-12
As I use it so rarely and for such simple things, and they've given me no reply through their own forum, I think I might just try Cinerella as I've seen a few people say it has also improved in leaps and bounds over the last year or so (definitely preferred KdenLive last time i compared but that was a quite a while ago now.)

I do also keep on saying I'm going to give a couple of other distros a try..... ;)


EDIT: seems the situation of Cinerella is an absolute mess! Not sure why I've seen more than one person suggesting it in the last couple of months.... Multiple websites, all a mess, last news about six months ago for a beta release, one of the websites listing three different competing versions, not in the official repo and instructions (of the only one that mentions a ppa) doesn't seem to have been done for Bionic yet. Don't think I'll bother with that!


But on the plus side, I've just downloaded the appImage of the latest development version of KDenLive and at least that works. :) First time I've used an appImage but actually been reading and talking about them a bit elsewhere the last couple of days :)

---

