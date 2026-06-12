---
title: "Flash videos won't play."
date: 2013-05-04
forum: Multimedia Software
---

### Post by SlickStretch on 2013-05-04
Whenever I go to YouTube with Firefox (ver. 20.0), the space where the video should be is empty.  No black box or anything, and it does not show any warnings about plug-ins or flash or anything like that.  When I try to use Chromium (ver. 25.0), it shows a yellow bar across the top of the screen which says "Could not load shockwave fla..." and there's a black box with a broken puzzle piece in it where the video should be.

I have installed "lubuntu-restricted-extras" and I have the latest version of flashplayer-installer (synaptic says version 11.2)

I am pretty new to linux, so go easy on me...

---

### Post by SlickStretch on 2013-05-06
101 people have read this and no one can help.  That's a damn shame.

---

### Post by lovebluesky2009 on 2013-05-06
strange, my chrome is never disappointed me, did you try to reinstall firefox, chrome and flash plugins?

---

### Post by midnightramen on 2013-05-07
i usually use the version at the official adobe site. They won't be updating it anymore, but still, it is fairly recent. Plus, it can play the DRM hulu episodes as well, but requires the HAL package to be installed. 

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

Regarding Chrome, there is a native Flash player in Chrome, which is why it works out of the box for youtube and the like.

---

### Post by cibalo on 2013-05-08
Hello,

> **SlickStretch said:**
> I have the latest version of flashplayer-installer

You need adobe-flashplugin package.

Try:
```
sudo apt-get install adobe-flashplugin
```

---

### Post by SlickStretch on 2013-05-10
> i usually use the version at the official adobe site. They won't be  updating it anymore, but still, it is fairly recent. Plus, it can play  the DRM hulu episodes as well, but requires the HAL package to be  installed. 

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)
When I try to download it, I get a pop-up saying "The channel 'raring-partner' is not known."

> Regarding Chrome, there is a native Flash player in Chrome, which is why it works out of the box for youtube and the like.
Mine doesn't.

> You need adobe-flashplugin package.
```
stretch@Z:~$ sudo apt-get install adobe-flashplugin
[sudo] password for stretch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate
stretch@Z:~$
```

---

### Post by cibalo on 2013-05-16
Hi,

> **SlickStretch said:**
> 
Mine doesn't.
```
stretch@Z:~$ sudo apt-get install adobe-flashplugin
E: Package 'adobe-flashplugin' has no installation candidate
stretch@Z:~$
```

You need to enable the Canonical Partners repository before install as detailed in [http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository](http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository).

---

### Post by midnightramen on 2013-05-16
you can try the partners repository above and "adobe-flashplugin" see if that works, although a "flashplugin-installer" should also be available in the "multiverse" repository. Its been a while for me, but I think that the "flashplugin-installer" just downloads a script that you'll have to execute: "sudo /usr/lib/flashplugin-installer/install_plugin" probably.

Chrome should have Pepperflash built-in. In Chrome, go to "about:plugins" (no quotes) and you should see a list of plugins. Click on the Details link on the right-hand side, and you should see the list of plugins, including "PepperFlash".

---

### Post by SlickStretch on 2013-05-17
> Chrome should have Pepperflash built-in. In Chrome, go to "about:plugins"  (no quotes) and you should see a list of plugins. Click on the Details  link on the right-hand side, and you should see the list of plugins,  including "PepperFlash".

I don't see anything called pepperflash.  Just "Macromedia Flash Plugin"

> You need to enable the Canonical Partners repository before install as detailed in [http://askubuntu.com/questions/14629...ner-repository]("http://askubuntu.com/questions/14629/how-do-i-enable-the-partner-repository").

I enabled the partner repository, and installed adobe-flashplugin.  Everything seemed to go fine, but still no change.  No flash video.

Just in case it's helpful...
```
stretch@Z:~$ sudo apt-get install adobe-flashplugin
[sudo] password for stretch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins x-ttcidfont-conf ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  flashplugin-installer
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 6,729 kB of archives.
After this operation, 17.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ raring/partner adobe-flashplugin i386 11.2.202.285-0raring1 [6,598 kB]
Get:2 http://archive.canonical.com/ubuntu/ raring/partner adobe-flash-properties-gtk i386 11.2.202.285-0raring1 [131 kB]
Fetched 6,729 kB in 3s (1,945 kB/s)             
(Reading database ... 139185 files and directories currently installed.)
Removing flashplugin-installer ...
Processing triggers for update-notifier-common ...
Selecting previously unselected package adobe-flashplugin.
(Reading database ... 139165 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.285-0raring1_i386.deb) ...
Selecting previously unselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.285-0raring1_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up adobe-flashplugin (11.2.202.285-0raring1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (11.2.202.285-0raring1) ...
stretch@Z:~$ 
```

---

### Post by cibalo on 2013-05-17
Hello,

> **SlickStretch said:**
> 
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins x-ttcidfont-conf ttf-xfree86-nonfree xfs
[COLOR=#ff0000]The following packages will be REMOVED:
  flashplugin-installer[/COLOR]
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.

Setting up adobe-flashplugin (11.2.202.285-0raring1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (11.2.202.285-0raring1) ...
stretch@Z:~$ [/CODE]

You may have a broken [COLOR=#ff0000]flashplugin-installer[/COLOR] installed previously.

Have a look at about:plugins in your firefox and see if you can see the following lines. 
Shockwave Flash
    File: libflashplayer.so
    Version: 11,2,202,285
    State: Enabled
    Shockwave Flash 11.2 r202

Now, go to youtube with your firefox.

---

### Post by SlickStretch on 2013-05-18
Yup, that's exactly what's listed in my plugins.  On YouTube, there's still an empty space where the video should be.

EDIT: After waiting about a minute or so, a black box appeared where the video should be.

---

### Post by SlickStretch on 2013-05-18
That's exactly what's in my plugins.  YouTube still doesn't work.

---

### Post by cibalo on 2013-05-19
Hello,

> **SlickStretch said:**
> Yup, that's exactly what's listed in my plugins.  On YouTube, there's still an empty space where the video should be.

EDIT: After waiting about a minute or so, a black box appeared where the video should be.

In that case, you can check if your flash player is working by visiting the flash test page at [http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html).

If your flash player is running, you will see a running red ball.

---

### Post by SlickStretch on 2013-05-19
I was not able to see the test.  Unfortunately, they only had troubleshooting steps for windows and mac...

---

### Post by SonnyE on 2013-05-19
I've had similar results in the last year (a blank, or sometimes a blank that later fills in with a black box in Chromium) from installing the usual updated Adobe Flash for Linux. Adobe stopped making new versions of Flash for Linux at 11.2, and the latest update for Linux is 11.2.202.285, while new versions of Flash are up to 11.7. When I "manually" installed 11.1.102.63 instead, Flash worked. However, this may not have been the best thing to do and may not work for you, and Firefox stopped allowing old versions of Adobe Flash to run a month or two ago.


Other Flash options that may be better instead of mucking around with trying to use old, unsupported versions of Adobe's original Flash: Lightspark, Gnash, Shumway, Pepper-based Flash in Chrome (which is different from Chromium) or some combination of any or all of those, in order to enable more kinds of Flash content.


How I "manually" made an older version of Adobe Flash run in Chromium, based on my notes that I followed several times:


I downloaded fp_11.1.102.63_archive.zip from Adobe at [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) (Edit: deep link may not work, search on Adobe's site for: archived flash player versions)


I extracted flashplayer11_1r102_63_linux.i386.tar.gz to a new folder "flashpluginextract" (using Archive Manager, but any new file extractor will do)


Then I followed the instructions that were in the readme.txt for the newer fp_11.2.202.228_archive.zip (a version that didn't work for me) modifying them appropriately for where I wanted to install Flash, resulting in these manual installation commands (using LXTerminal, but any terminal window will do)


$ cd Downloads/Adobe/flashpluginextract
$ sudo cp -r usr/* /usr
$ sudo cp libflashplayer.so /usr/lib/chromium-browser/plugins/


Then I restart Chromium and enter chrome://plugins in the address bar to see whether the old version is detected and enabled.


My system: Lubuntu 12.04 - HP Pavilion ze4800 notebook - 1GB RAM - AMD IGP320M graphics (the OSS driver is supposed to be able to run the IGP320, at one one-hundredth the speed of newer on-chip graphics, but it tends not to be well-supported)

---

### Post by cibalo on 2013-05-21
Hello,

> **SlickStretch said:**
> I was not able to see the test.  Unfortunately, they only had troubleshooting steps for windows and mac...

I have no idea what went wrong with your flash player. But, it might help if you can remove all those broken packages from all your previous installations, as detailed in [http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed](http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed).

Then run:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get install --reinstall adobe-flashplugin
```

Hope That Helps!

---

