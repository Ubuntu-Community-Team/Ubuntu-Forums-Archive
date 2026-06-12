---
title: "Flash plugin issues"
date: 2010-05-31
forum: Multimedia Software
---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> It does detect the correct version now (Progress!) but I still get the "install missing plugins" message and I still show nothing under "about:plugins" ...

I've installed Firefox a few different ways (I *am* worried that there might be traces of other installations hiding around...) but the latest is just 3.5.3 from the repositories.  I had installed "Namoroka" (the development version) and for whatever reason my launcher still says that but I don't *think *it's still on here anywhere :(

I'm sure I've screwed it up mainly by trying different scripts and such that I've found around the web... just like I tend to do with my audio configuration (Which is still messed up too!)

Thanks for your help!

Edit: I can't seem to get Firefox to recognize ANY plugins... whatever I try to add asks me to install it, then says it's already installed.

Close Firefox, move the file pluginreg.dat from your Firefox profile folder to a backup location and restart Firefox. See if that works.

---

### Post by lovinglinux on 2010-05-31
> **lovinglinux said:**
> Close Firefox, move the file pluginreg.dat from your Firefox profile folder to a backup location and restart Firefox. See if that works.

I imagine you have other plugins installed. Is Firefox recognizing other plugins?

Create a new profile from the profile manager:

```
firefox -P
```

Then check if the new profile can detect any plugins.

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> I imagine you have other plugins installed. Is Firefox recognizing other plugins?

Create a new profile from the profile manager:

```
firefox -P
```Then check if the new profile can detect any plugins.

The only instances of pluginreg.dat were in a backup folder (which I just deleted :-) ) and in Thunderbird, none in a current install at all.

Here's what comes up when I run it from terminal...

```

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loaded md5.js
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so


```A new profile was the exact same...  Is it me or does Firefox not realize that it's 64-bit?!?!

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> The only instances of pluginreg.dat were in a backup folder (which I just deleted :-) ) and in Thunderbird, none in a current install at all.

Here's what comes up when I run it from terminal...

```

/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
loaded md5.js
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/xine-plugin/xineplugin.so [/usr/lib/xine-plugin/xineplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libvlcplugin.so [/usr/lib/mozilla/plugins/libvlcplugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS64]
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so


```

A new profile was the exact same...

It seems you are using Ubuntu Lucid Lynx 64bit with an older version of Firefox (3.5.3), which is weird because Lucid comes with Firefox 3.6.3.

So did you install any other version of Firefox? Did you upgrade from Ubuntu 9.10 or did you do a clean install of 10.04?

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> It seems you are using Ubuntu Lucid Lynx 64bit with an older version of Firefox (3.5.3), which is weird because Lucid comes with Firefox 3.6.3.

So did you install any other version of Firefox? Did you upgrade from Ubuntu 9.10 or did you do a clean install of 10.04?

I've upgraded since 7.10!  I had a newer version but it did the same thing so I just did 'apt-get remove firefox' and 'apt-get install firefox' to start fresh (I thought!) ... should I purge Firefox again and install 3.6.3 directly?  It never seems to totally go away...

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> I've upgraded since 7.10!  I had a newer version but it did the same thing so I just did 'apt-get remove firefox' and 'apt-get install firefox' to start fresh (I thought!)

So do this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.5
sudo apt-get install firefox
```

Post any errors.

Then open Firefox, go to Help >> About Firefox and copy/paste the version info. Then go to **about[noparse]:[/noparse]plugins** and check if the plugins are there.

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> So do this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.5
sudo apt-get install firefox
```Post any errors.

Then open Firefox, go to Help >> About Firefox and copy/paste the version info. Then go to **about[noparse]:[/noparse]plugins** and check if the plugins are there.


Nope - not only is it still 3.5.3 but all the add-ons are still there, and no plugins.  I'm not getting it totally removed, obviously.

---

### Post by Superluke on 2010-05-31
> **Superluke said:**
> Nope - not only is it still 3.5.3 but all the add-ons are still there, and no plugins.  I'm not getting it totally removed, obviously.

Not only that, but I tried installing firefox-3.6 and when I start firefox it's STILL 3.5.3!!!

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> Nope - not only is it still 3.5.3 but all the add-ons are still there, and no plugins.  I'm not getting it totally removed, obviously.

Addons and personal data are not deleted when you remove Firefox. This is normal behavior.

> **Superluke said:**
> Not only that, but I tried installing firefox-3.6 and when I start firefox it's STILL 3.5.3!!!

Something is wrong here. Go to "System >> Administration >> Synaptic", then search for firefox, select all firefox packages installed and mark them for complete removal and apply.

Then go to "System >> Administration >> Software Sources >> Other Software" and disable any item containing mozilla or firefox.

Then run these:

```
sudo apt-get update
```

```
sudo apt-get install firefox
```

Then post the output of these:

```
whereis firefox
```

```
locate firefox
```

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> Addons and personal data are not deleted when you remove Firefox. This is normal behavior.



Something is wrong here. Go to "System >> Administration >> Synaptic", then search for firefox, select all firefox packages installed and mark them for complete removal and apply.

Then go to "System >> Administration >> Software Sources >> Other Software" and disable any item containing mozilla or firefox.

Then run these:

```
sudo apt-get update
```

```
sudo apt-get install firefox
```

Then post the output of these:

```
whereis firefox
```

```
locate firefox
```

```
luke@luke-desktop:~$ whereis firefox
firefox: /usr/bin/firefox /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
```

```

luke@luke-desktop:~$ locate firefox
/etc/firefox
/etc/firefox-3.0
/etc/firefox-3.5
/etc/alternatives/firefox-flashplugin
/etc/alternatives/firefox-homepage
/etc/alternatives/firefox-homepage-locales
/etc/apparmor.d/usr.bin.firefox
/etc/apparmor.d/usr.bin.firefox-3.5.dpkg-old
/etc/apparmor.d/disable/usr.bin.firefox
/etc/apparmor.d/disable/usr.bin.firefox-3.5
/etc/firefox/pref
/etc/firefox/profile
/etc/firefox/pref/firefox.js
/etc/firefox/profile/bookmarks.html
/etc/firefox/profile/chrome
/etc/firefox/profile/localstore.rdf
/etc/firefox/profile/mimeTypes.rdf
/etc/firefox/profile/prefs.js
/etc/firefox/profile/chrome/userChrome-example.css
/etc/firefox/profile/chrome/userContent-example.css
/etc/firefox-3.0/pref
/etc/firefox-3.0/profile
/etc/firefox-3.0/pref/apturl.js
/etc/firefox-3.0/pref/firefox.js
/etc/firefox-3.0/pref/limewire.js
/etc/firefox-3.0/profile/bookmarks.html
/etc/firefox-3.0/profile/chrome
/etc/firefox-3.0/profile/localstore.rdf
/etc/firefox-3.0/profile/mimeTypes.rdf
/etc/firefox-3.0/profile/prefs.js
/etc/firefox-3.0/profile/chrome/userChrome-example.css
/etc/firefox-3.0/profile/chrome/userContent-example.css
/etc/firefox-3.5/pref
/etc/firefox-3.5/profile
/etc/firefox-3.5/pref/firefox.js
/etc/firefox-3.5/profile/bookmarks.html
/etc/firefox-3.5/profile/chrome
/etc/firefox-3.5/profile/localstore.rdf
/etc/firefox-3.5/profile/mimeTypes.rdf
/etc/firefox-3.5/profile/prefs.js
/etc/firefox-3.5/profile/chrome/userChrome-example.css
/etc/firefox-3.5/profile/chrome/userContent-example.css
/home/luke/.mozilla/firefox
/home/luke/.mozilla/firefox/Crash Reports
/home/luke/.mozilla/firefox/enjccsq9.default
/home/luke/.mozilla/firefox/profiles.ini
/home/luke/.mozilla/firefox/Crash Reports/InstallTime20090824085743
/home/luke/.mozilla/firefox/Crash Reports/LastCrash
/home/luke/.mozilla/firefox/Crash Reports/crashreporter.ini
/home/luke/.mozilla/firefox/Crash Reports/pending
/home/luke/.mozilla/firefox/Crash Reports/submit.log
/home/luke/.mozilla/firefox/Crash Reports/submitted
/home/luke/.opera/icons/http%3A%2F%2Fwww.spreadfirefox.com%2F5years%2Ffavicon.ico
/home/luke/.opera/icons/www.spreadfirefox.com.idx
/opt/firefox
/opt/firefox/.autoreg
/opt/firefox/README.txt
/opt/firefox/Throbber-small.gif
/opt/firefox/application.ini
/opt/firefox/blocklist.xml
/opt/firefox/browserconfig.properties
/opt/firefox/chrome
/opt/firefox/components
/opt/firefox/crashreporter
/opt/firefox/crashreporter-override.ini
/opt/firefox/crashreporter.ini
/opt/firefox/defaults
/opt/firefox/dictionaries
/opt/firefox/dictionaries_2009-10-15T13:02:27-0400
/opt/firefox/extensions
/opt/firefox/firefox
/opt/firefox/firefox-bin
/opt/firefox/greprefs
/opt/firefox/icons
/opt/firefox/libfreebl3.chk
/opt/firefox/libfreebl3.so
/opt/firefox/libmozjs.so
/opt/firefox/libnspr4.so
/opt/firefox/libnss3.so
/opt/firefox/libnssckbi.so
/opt/firefox/libnssdbm3.so
/opt/firefox/libnssutil3.so
/opt/firefox/libplc4.so
/opt/firefox/libplds4.so
/opt/firefox/libsmime3.so
/opt/firefox/libsoftokn3.chk
/opt/firefox/libsoftokn3.so
/opt/firefox/libsqlite3.so
/opt/firefox/libssl3.so
/opt/firefox/libxpcom.so
/opt/firefox/libxul.so
/opt/firefox/modules
/opt/firefox/mozilla-xremote-client
/opt/firefox/old-homepage-default.properties
/opt/firefox/platform.ini
/opt/firefox/plugins
/opt/firefox/plugins_2009-10-15T13:02:27-0400
/opt/firefox/removed-files
/opt/firefox/res
/opt/firefox/run-mozilla.sh
/opt/firefox/searchplugins
/opt/firefox/update.locale
/opt/firefox/updater
/opt/firefox/updater.ini
/opt/firefox/chrome/browser.jar
/opt/firefox/chrome/browser.manifest
/opt/firefox/chrome/classic.jar
/opt/firefox/chrome/classic.manifest
/opt/firefox/chrome/comm.jar
/opt/firefox/chrome/comm.manifest
/opt/firefox/chrome/en-US.jar
/opt/firefox/chrome/en-US.manifest
/opt/firefox/chrome/icons
/opt/firefox/chrome/pippki.jar
/opt/firefox/chrome/pippki.manifest
/opt/firefox/chrome/reporter.jar
/opt/firefox/chrome/reporter.manifest
/opt/firefox/chrome/toolkit.jar
/opt/firefox/chrome/toolkit.manifest
/opt/firefox/chrome/icons/default
/opt/firefox/chrome/icons/default/default16.png
/opt/firefox/chrome/icons/default/default32.png
/opt/firefox/chrome/icons/default/default48.png
/opt/firefox/components/FeedConverter.js
/opt/firefox/components/FeedProcessor.js
/opt/firefox/components/FeedWriter.js
/opt/firefox/components/NetworkGeolocationProvider.js
/opt/firefox/components/WebContentConverter.js
/opt/firefox/components/aboutCertError.js
/opt/firefox/components/aboutPrivateBrowsing.js
/opt/firefox/components/aboutRights.js
/opt/firefox/components/aboutRobots.js
/opt/firefox/components/aboutSessionRestore.js
/opt/firefox/components/browser.xpt
/opt/firefox/components/fuelApplication.js
/opt/firefox/components/jsconsole-clhandler.js
/opt/firefox/components/libbrowsercomps.so
/opt/firefox/components/libbrowserdirprovider.so
/opt/firefox/components/libdbusservice.so
/opt/firefox/components/libimgicon.so
/opt/firefox/components/libmozgnome.so
/opt/firefox/components/libnkgnomevfs.so
/opt/firefox/components/nsAddonRepository.js
/opt/firefox/components/nsBadCertHandler.js
/opt/firefox/components/nsBlocklistService.js
/opt/firefox/components/nsBrowserContentHandler.js
/opt/firefox/components/nsBrowserGlue.js
/opt/firefox/components/nsContentDispatchChooser.js
/opt/firefox/components/nsContentPrefService.js
/opt/firefox/components/nsDefaultCLH.js
/opt/firefox/components/nsDownloadManagerUI.js
/opt/firefox/components/nsExtensionManager.js
/opt/firefox/components/nsFilePicker.js
/opt/firefox/components/nsHandlerService.js
/opt/firefox/components/nsHelperAppDlg.js
/opt/firefox/components/nsLivemarkService.js
/opt/firefox/components/nsLoginInfo.js
/opt/firefox/components/nsLoginManager.js
/opt/firefox/components/nsLoginManagerPrompter.js
/opt/firefox/components/nsMicrosummaryService.js
/opt/firefox/components/nsPlacesDBFlush.js
/opt/firefox/components/nsPlacesTransactionsService.js
/opt/firefox/components/nsPrivateBrowsingService.js
/opt/firefox/components/nsProxyAutoConfig.js
/opt/firefox/components/nsSafebrowsingApplication.js
/opt/firefox/components/nsSearchService.js
/opt/firefox/components/nsSearchSuggestions.js
/opt/firefox/components/nsSessionStartup.js
/opt/firefox/components/nsSessionStore.js
/opt/firefox/components/nsSetDefaultBrowser.js
/opt/firefox/components/nsSidebar.js
/opt/firefox/components/nsTaggingService.js
/opt/firefox/components/nsTryToClose.js
/opt/firefox/components/nsURLFormatter.js
/opt/firefox/components/nsUpdateService.js
/opt/firefox/components/nsUrlClassifierLib.js
/opt/firefox/components/nsUrlClassifierListManager.js
/opt/firefox/components/nsWebHandlerApp.js
/opt/firefox/components/pluginGlue.js
/opt/firefox/components/storage-Legacy.js
/opt/firefox/components/storage-mozStorage.js
/opt/firefox/components/txEXSLTRegExFunctions.js
/opt/firefox/defaults/autoconfig
/opt/firefox/defaults/pref
/opt/firefox/defaults/profile
/opt/firefox/defaults/autoconfig/platform.js
/opt/firefox/defaults/autoconfig/prefcalls.js
/opt/firefox/defaults/pref/channel-prefs.js
/opt/firefox/defaults/pref/firefox-branding.js
/opt/firefox/defaults/pref/firefox-l10n.js
/opt/firefox/defaults/pref/firefox.js
/opt/firefox/defaults/pref/reporter.js
/opt/firefox/defaults/profile/bookmarks.html
/opt/firefox/defaults/profile/chrome
/opt/firefox/defaults/profile/localstore.rdf
/opt/firefox/defaults/profile/mimeTypes.rdf
/opt/firefox/defaults/profile/prefs.js
/opt/firefox/defaults/profile/chrome/userChrome-example.css
/opt/firefox/defaults/profile/chrome/userContent-example.css
/opt/firefox/dictionaries_2009-10-15T13:02:27-0400/en-US.aff
/opt/firefox/dictionaries_2009-10-15T13:02:27-0400/en-US.dic
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/opt/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/opt/firefox/greprefs/all.js
/opt/firefox/greprefs/security-prefs.js
/opt/firefox/greprefs/xpinstall.js
/opt/firefox/icons/document.png
/opt/firefox/icons/mozicon128.png
/opt/firefox/icons/mozicon16.xpm
/opt/firefox/icons/mozicon50.xpm
/opt/firefox/icons/updater.png
/opt/firefox/modules/DownloadLastDir.jsm
/opt/firefox/modules/DownloadUtils.jsm
/opt/firefox/modules/ISO8601DateUtils.jsm
/opt/firefox/modules/Microformats.js
/opt/firefox/modules/PlacesDBUtils.jsm
/opt/firefox/modules/PluralForm.jsm
/opt/firefox/modules/SpatialNavigation.js
/opt/firefox/modules/WindowDraggingUtils.jsm
/opt/firefox/modules/XPCOMUtils.jsm
/opt/firefox/modules/debug.js
/opt/firefox/modules/distribution.js
/opt/firefox/modules/utils.js
/opt/firefox/plugins_2009-10-15T13:02:27-0400/libnullplugin.so
/opt/firefox/res/EditorOverride.css
/opt/firefox/res/arrow.gif
/opt/firefox/res/arrowd.gif
/opt/firefox/res/broken-image.gif
/opt/firefox/res/charsetData.properties
/opt/firefox/res/charsetalias.properties
/opt/firefox/res/contenteditable.css
/opt/firefox/res/designmode.css
/opt/firefox/res/dtd
/opt/firefox/res/entityTables
/opt/firefox/res/fonts
/opt/firefox/res/forms.css
/opt/firefox/res/grabber.gif
/opt/firefox/res/hiddenWindow.html
/opt/firefox/res/html
/opt/firefox/res/html.css
/opt/firefox/res/langGroups.properties
/opt/firefox/res/language.properties
/opt/firefox/res/loading-image.gif
/opt/firefox/res/mathml.css
/opt/firefox/res/quirk.css
/opt/firefox/res/svg.css
/opt/firefox/res/table-add-column-after-active.gif
/opt/firefox/res/table-add-column-after-hover.gif
/opt/firefox/res/table-add-column-after.gif
/opt/firefox/res/table-add-column-before-active.gif
/opt/firefox/res/table-add-column-before-hover.gif
/opt/firefox/res/table-add-column-before.gif
/opt/firefox/res/table-add-row-after-active.gif
/opt/firefox/res/table-add-row-after-hover.gif
/opt/firefox/res/table-add-row-after.gif
/opt/firefox/res/table-add-row-before-active.gif
/opt/firefox/res/table-add-row-before-hover.gif
/opt/firefox/res/table-add-row-before.gif
/opt/firefox/res/table-remove-column-active.gif
/opt/firefox/res/table-remove-column-hover.gif
/opt/firefox/res/table-remove-column.gif
/opt/firefox/res/table-remove-row-active.gif
/opt/firefox/res/table-remove-row-hover.gif
/opt/firefox/res/table-remove-row.gif
/opt/firefox/res/ua.css
/opt/firefox/res/unixcharset.properties
/opt/firefox/res/viewsource.css
/opt/firefox/res/dtd/mathml.dtd
/opt/firefox/res/dtd/xhtml11.dtd
/opt/firefox/res/entityTables/html40Latin1.properties
/opt/firefox/res/entityTables/html40Special.properties
/opt/firefox/res/entityTables/html40Symbols.properties
/opt/firefox/res/entityTables/htmlEntityVersions.properties
/opt/firefox/res/entityTables/mathml20.properties
/opt/firefox/res/entityTables/transliterate.properties
/opt/firefox/res/fonts/mathfont.properties
/opt/firefox/res/fonts/mathfontSTIXNonUnicode.properties
/opt/firefox/res/fonts/mathfontSTIXSize1.properties
/opt/firefox/res/fonts/mathfontStandardSymbolsL.properties
/opt/firefox/res/fonts/mathfontUnicode.properties
/opt/firefox/res/html/folder.png
/opt/firefox/searchplugins/amazondotcom.xml
/opt/firefox/searchplugins/answers.xml
/opt/firefox/searchplugins/creativecommons.xml
/opt/firefox/searchplugins/eBay.xml
/opt/firefox/searchplugins/google.xml
/opt/firefox/searchplugins/wikipedia.xml
/opt/firefox/searchplugins/yahoo.xml
/usr/bin/firefox
/usr/bin/firefox.ubuntu
/usr/bin/mozilla-firefox
/usr/lib/firefox
/usr/lib/firefox-3.6.5pre
/usr/lib/firefox-addons
/usr/lib/mozilla-firefox
/usr/lib/firefox/plugins
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox/plugins/xineplugin.so
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/extensions/langpack-en-AU@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-CA@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/langpack-en@firefox-3.6.ubuntu.com
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/searchplugins/common
/usr/lib/firefox-addons/searchplugins/en-GB
/usr/lib/firefox-addons/searchplugins/en-US
/usr/lib/firefox-addons/searchplugins/en-US/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/en-US/answers.xml
/usr/lib/firefox-addons/searchplugins/en-US/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/en-US/eBay.xml
/usr/lib/firefox-addons/searchplugins/en-US/google.xml
/usr/lib/firefox-addons/searchplugins/en-US/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/en-US/yahoo.xml
/usr/share/firefox
/usr/share/app-install/desktop/firefox-greasemonkey.desktop
/usr/share/app-install/desktop/firefox-launchpad-plugin.desktop
/usr/share/app-install/desktop/firefox-ubuntu-it-menu.desktop
/usr/share/app-install/desktop/firefox-webdeveloper.desktop
/usr/share/app-install/desktop/firefox.desktop
/usr/share/app-install/icons/firefox-greasemonkey.xpm
/usr/share/app-install/icons/firefox-installer.png
/usr/share/app-install/icons/firefox-launchpad-plugin.xpm
/usr/share/app-install/icons/firefox-themes-ubuntu.xpm
/usr/share/app-install/icons/firefox-ubuntu-it-menu.png
/usr/share/app-install/icons/firefox-webdeveloper.xpm
/usr/share/applications/firefox.desktop
/usr/share/apport/package-hooks/firefox.py
/usr/share/bug/firefox
/usr/share/bug/firefox/presubj
/usr/share/doc/firefox
/usr/share/doc/firefox-3.6
/usr/share/doc/firefox-branding
/usr/share/doc/firefox/MPL.gz
/usr/share/doc/firefox/README.Debian
/usr/share/doc/firefox/changelog.Debian.gz
/usr/share/doc/firefox/copyright
/usr/share/doc/firefox/firefox.cfg
/usr/share/doc/firefox-branding/changelog.Debian.gz
/usr/share/doc/firefox-branding/copyright
/usr/share/firefox/defaults
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/apturl.js
/usr/share/locale-langpack/en_AU/LC_MESSAGES/desktop_kubuntu-firefox-installer.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/kubuntu-firefox-installer.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/desktop_kubuntu-firefox-installer.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/kubuntu-firefox-installer.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/desktop_kubuntu-firefox-installer.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/kubuntu-firefox-installer.mo
/usr/share/menu/firefox
/usr/share/pixmaps/firefox.png
/usr/share/ubuntu-tweak/data/applogos/firefox.png
/usr/share/ubuntu-tweak/data/aptkeys/firefox.gpg
/usr/share/xfce4/helpers/firefox.desktop
/var/cache/apt/archives/firefox-3.0-gnome-support_3.6.3+nobinonly-0ubuntu4_all.deb
/var/cache/apt/archives/firefox-3.0_3.6.3+nobinonly-0ubuntu4_all.deb
/var/cache/apt/archives/firefox-3.5-branding_3.6.3+nobinonly-0ubuntu4_all.deb
/var/cache/apt/archives/firefox-3.5-gnome-support_3.6.3+nobinonly-0ubuntu4_all.deb
/var/cache/apt/archives/firefox-3.5_3.6.3+nobinonly-0ubuntu4_all.deb
/var/cache/apt/archives/firefox-3.6_3.6+lucid_all.deb
/var/cache/apt/archives/firefox-branding_3.6.3+nobinonly-0ubuntu4_amd64.deb
/var/cache/apt/archives/firefox-branding_3.6.5~hg20100525r34247+nobinonly-0ubuntu1~umd1~lucid_amd64.deb
/var/cache/apt/archives/firefox-gnome-support_3.6.3+nobinonly-0ubuntu4_amd64.deb
/var/cache/apt/archives/firefox_3.6.3+nobinonly-0ubuntu4_amd64.deb
/var/cache/apt/archives/firefox_3.6.5~hg20100525r34247+nobinonly-0ubuntu1~umd1~lucid_amd64.deb
/var/lib/dpkg/alternatives/firefox-flashplugin
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/info/firefox-3.0.list
/var/lib/dpkg/info/firefox-3.5.list
/var/lib/dpkg/info/firefox-3.6.list
/var/lib/dpkg/info/firefox-3.6.md5sums
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm
/var/lib/update-notifier/user.d/firefox-3.0-restart-required
/var/lib/update-notifier/user.d/firefox-3.5-restart-required

```

There you go...:(

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> There you go...:(

Close Firefox, then run these:

```
sudo rm /usr/bin/firefox
```

```
sudo dpkg-divert --rename --remove /usr/bin/firefox 
```

Start Firefox, check the version and if plugins are loaded.

---

### Post by Superluke on 2010-05-31
> **lovinglinux said:**
> Close Firefox, then run these:

```
sudo rm /usr/bin/firefox
``````
sudo dpkg-divert --rename --remove /usr/bin/firefox 
```Start Firefox, check the version and if plugins are loaded.


Woohoo!  That worked perfectly, I have Flash again ... but ... now I'm getting a bunch of:

```
(firefox-bin:8494): Gdk-WARNING **: XID collision, trouble ahead
```

and then a crash... randomly.  Nothing to do with your add-on, which now works flawlessly.  Thanks so much for your help!  My wife doesn't have to boot to Windows to play Farmville now! :|

---

### Post by lovinglinux on 2010-05-31
> **Superluke said:**
> Woohoo!  That worked perfectly, I have Flash again ... but ... now I'm getting a bunch of:

```
(firefox-bin:8494): Gdk-WARNING **: XID collision, trouble ahead
```

and then a crash... randomly.  Nothing to do with your add-on, which now works flawlessly.  Thanks so much for your help!  My wife doesn't have to boot to Windows to play Farmville now! :|

First lets remove the extra Firefox you have installed:

```
sudo rm -r /opt/firefox
```

Restart Firefox and tell me what version do you have.

If you don't mind, I will ask a moderator to delete our post exchange from this thread, because it is not relevant to the discussion. I should have asked you to create a new thread instead of posting here, but I didn't imagine the issue would require so many attempts to fix it. Anyway, please create a new thread so I can continue to help with the new problem.

BTW, would be really nice if you could rectify your review about my extension at [Mozilla](https://addons.mozilla.org/en-US/firefox/addon/161939). I normally wouldn't ask that, but since you gave it one star and the problem wasn't actually my extension, then would be really nice if you could do that. The real problem was that you diverted your Firefox to an older version downloaded manually and installed under /opt/firefox. Probably you didn't make the proper symlinks to the real plugins folder, so even after installing flash, that version of Firefox couldn't find it.

---

### Post by bapoumba on 2010-05-31
Moved to its own thread.

---

### Post by Superluke on 2010-06-01
> **lovinglinux said:**
> First lets remove the extra Firefox you have installed:

```
sudo rm -r /opt/firefox
```Restart Firefox and tell me what version do you have.

If you don't mind, I will ask a moderator to delete our post exchange from this thread, because it is not relevant to the discussion. I should have asked you to create a new thread instead of posting here, but I didn't imagine the issue would require so many attempts to fix it. Anyway, please create a new thread so I can continue to help with the new problem.

BTW, would be really nice if you could rectify your review about my extension at [Mozilla]("https://addons.mozilla.org/en-US/firefox/addon/161939"). I normally wouldn't ask that, but since you gave it one star and the problem wasn't actually my extension, then would be really nice if you could do that. The real problem was that you diverted your Firefox to an older version downloaded manually and installed under /opt/firefox. Probably you didn't make the proper symlinks to the real plugins folder, so even after installing flash, that version of Firefox couldn't find it.

It's 3.6.3 now... perfect.  I can't seem to change my review... I guess I can post another one though :-)  I see what you mean.  I wonder when I installed that other Firefox...

---

### Post by lovinglinux on 2010-06-01
> **Superluke said:**
> It's 3.6.3 now... perfect.  I can't seem to change my review... I guess I can post another one though :-)  I see what you mean.  I wonder when I installed that other Firefox...

Thanks. Are you still experiencing crashes?

---

### Post by lovinglinux on 2010-06-01
> **Superluke said:**
> It's 3.6.3 now... perfect.  I can't seem to change my review... I guess I can post another one though :-)  I see what you mean.  I wonder when I installed that other Firefox...

Thanks for the new positive review. I really appreciate it.

---

