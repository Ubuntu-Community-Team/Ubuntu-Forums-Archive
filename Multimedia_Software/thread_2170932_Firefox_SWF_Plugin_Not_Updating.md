---
title: "Firefox SWF Plugin Not Updating"
date: 2013-08-28
forum: Multimedia Software
---

### Post by ron3 on 2013-08-28
I tried updating the Shockwave Flash plugin in Firefox 23 several times from unpacking and installing libflashplayer.so into the plugins folder from the install_flash_player_11_linux.i386.tar.gz, which I downloaded from Adobe.  It appears to have installed in the plugins folder, however I still cannot view youtube videos in Firefox. It also appears there are two flash plugins installed, and for some reason I cannot delete either one from the Firefox plugins folder, even though I am the system owner and administrator I don't have full permissions. What am I doing wrong? How can I get this plugin working to watch youtube videos? Why has this problem never happened to me before in Firefox for Windows? I expected Firefox included in Ubuntu 12.04.3 (which I just d/l and installed 2 days ago) would be fully updated, or is there a new update or package I need to look for?   Here is the SWF info from my Firefox pluginreg.dat:   [PLUGINS] libflashplayer.so:$install_flash_player_11_linux.i386.tar.gz /usr/lib/flashplugin-installer/libflashplayer.so:$ 11,2,202,297:$ 1377692989000:0:0:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1377650576000:0:0:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$

---

### Post by ron3 on 2013-08-29
I hoped to find someone here who would help, but thanks to YouTube I found a workaround. There's a plugin, YouTube Flash to HTML5, which has solved this issue. Maybe the problem I was having is my outdated video card, maybe Adobe SWF isn't compatible with my computer's configuration, or maybe I really messed something up trying to use the Console to install a plugin. In the end though, Adobe is no longer supporting Linux based systems with it's next flash version, so I'm happy to have found another solution.

---

### Post by SeijiSensei on 2013-08-30
For future reference, the Ubuntu method is to activate the "partners" repository and install the "adobe-flashplugin" package.  You get the added benefit of automatic updates, though since Adobe has discontinued development of Flash for Linux, the only updates that come down the pike these days are security fixes.

---

### Post by Yellow Pasque on 2013-08-31
The package is not named adobe-flashplugin and I don't think it's in the partner repo anymore. Installing Flash should be as simple as:
```
sudo apt-get install flashplugin-installer
```

Of course, you have to remove the Flash installs you tried manually or they'll conflict with each other...

---

### Post by SeijiSensei on 2013-08-31
It's right here on my Kubuntu 13.04 machine.  When you take this route, the installer automatically deletes flashplayer-installer.

Have a look in the partner repository: [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/)

The most recent release is dated July 10th.

---

