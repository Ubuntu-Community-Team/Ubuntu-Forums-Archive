---
title: "Chromium Flash Pepper on precise, how?"
date: 2012-05-08
forum: Multimedia Software
---

### Post by jamesmika on 2012-05-08
It's not acceptable for me to use Chrome but it's acceptable to use the spyware-cleaned Chromium. Even if I normally prefer Firefox, it's also acceptable for me for a few flash sites to use Chromium.

My wish:
Chromium with Flash Pepper on precise

Should work well to play flash?

Which ppa do I have to choose?
[https://launchpad.net/chromium-project](https://launchpad.net/chromium-project)

Which branch contains Flash Pepper? Beta? Dev? Daily?

Unfortunately they don't have precise added yet.
apt-get can't see [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/precise/main/binary-amd64/Packages) (they don't have it yet)

Can I use [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/oneiric/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/oneiric/) ?

Or should I learn how to compile Chromium from source?

Can you give instructions please how to get Flash Pepper on precise?

---

### Post by shantiq on 2012-05-09
tried this on precise

[https://launchpad.net/~chromium-daily/+archive/stable]("https://launchpad.net/~chromium-daily/+archive/stable")[https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable)


works fine


but it does not use pepper    it still uses flash

---

### Post by jamesmika on 2012-05-09
How to install that?

---

### Post by shantiq on 2012-05-10
-------------sorry multiple posts my browser is playing up--------------

---

### Post by shantiq on 2012-05-10
in your terminal




```
 sudo add-apt-repository ppa:chromium-daily/stable

```



press enter/return to accept keys


```
sudo apt-get update

```

```
sudo apt-get install chromium-browser
```

---

### Post by shantiq on 2012-05-10
------------------

---

### Post by jamesmika on 2012-05-10
Thanks, installation succeeded.

Flash doesn't work for me any better than the version from Ubuntu repos.

Will they add Flash Pepper? Or is this exclusively for Chrome due to the closed source flash.so?

They can probable add the Pepper API.

But I got to download the flash.so from somewhere else?

---

### Post by shantiq on 2012-05-10
flash not working on chromium for you?    does it not start even?

---

### Post by jamesmika on 2012-05-10
It starts but I am having the same problems as with Firefox.

(Problems: can't leave fullscreen without alt + tab. Sound works, video lags heavily. Perhaps same problem like [http://ubuntuforums.org/showthread.php?p=11887129](http://ubuntuforums.org/showthread.php?p=11887129) while performance can not be the problem. Also none of the suggestions from [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) worked for me.)

(System: amd64, precise, ATI Mobility)

(It worked before on edit: on oneiric, not precise. It also worked before on Windows 7. It  also works in a vm on top of precise. Performance can not be the  problem.)

That's why I want to see, if Flash Pepper is better supported on my system.

---

### Post by jamesmika on 2012-06-04
Purging fglrx and installing fglrx-updates fixed my problem.

(jockey broken on precise, there is a confirmed bug)

The question for Flash Pepper still interesting.

---

### Post by Placenta Juan on 2012-06-10
The pepper version of flash will never be distributed with chromium, but you can always grab it from the chrome binaries. Simply download the latest unstable chrome build for your arch,
```
wget "http://dl.google.com/dl/linux/direct/google-chrome-unstable_current_i386.rpm"
```
for example, and extract the file /chrome/PepperFlash/libpepflashplayer.so. You'll have to add a flag when you call chromium pointing to the plugin,
```
--ppapi-flash-path=/usr/lib/PepperFlash/libpepflashplayer.so --ppapi-flash-version=11.3.31.103
```
(assuming you copied it to /usr/lib and are using the current version as of this post). Then you'll have to go into chrome://plugins/ and disable the non-ppapi version of flash. Seems to work fairly well, but full-screen seems to not work for me.

---

### Post by jamesmika on 2012-06-15
Thank you very much!

Also works for me. Sound is messed up and I can't leave fullscreen. It's still unstable version.

---

### Post by Lyfang on 2012-07-03
**On Lubuntu 12.04**
WARNING! Caution, don't try on production machines without fear of dealing with problems. Reminder: Is done at your own risk (as usual)! Probably can be a future security risk if you don't update the Flash plugin regularly, at this point manually. But it should work, it did for me.

Downloaded google-chrome-stable_current_i386.deb version 20 from [http://google.com/chrome](http://google.com/chrome). Installed Google Chrome on one computer & copied /opt/google/chrome/PepperFlash/libpepflashplayer.so

Copy libpepflashplayer.so to /usr/lib/chromium-browser/
```
sudo cp /home/USERNAME/Downloads/libpepflashplayer.so /usr/lib/chromium-browser/
```

Alternative way with GUI  file manager
Open Terminal
```
gksudo pcmanfm
```

Copy libpepflashplayer.so to /usr/lib/chromium-browser/

Edit the 'default' text file:
```
gksudo leafpad /etc/chromium-browser/default
```

# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/libpepflashplayer.so --ppapi-flash-version=11.3.31.103"

[Adobe Flash Player version check HERE]("http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html")

Go to (address bar): chrome://plugins

Disable the Adobe Flash plugin 11.2 r202, /usr/lib/adobe-flashplugin/libflashplayer.so (abandoned by Adobe?), use the 'Pepper' Adobe Flash Player instead.

The original file 'default':

# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS=""

---

### Post by Lyfang on 2012-09-22
Adobe Pepper Flash Player, libpepflashplayer.so version 11.3.31.232 "crashes" Chromium Version 20.0.1132.47 Ubuntu 12.04 (144678), apport-gtk starts and reports false positive browser crash after watching a fullscreen YouTube video. apport-gtk also says: "It seems you have modified the contents of "/etc/chromium-browser/default".  Would you like to add the contents of it to your bug report?"

---

### Post by Lyfang on 2012-09-28
Just submitted a bug report. I hope Chromium will soon be supported by Adobe (Pepper Flash) and will fix the problem: [Pepper Flash 11.3.31.232 crashes on Chromium 20.0 (Precise)]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1058304")

---

### Post by Lyfang on 2012-10-20
**WARNING! Caution, don't try on production machines without fear of dealing with problems since this guide is using a development release!**

Pepper Flash from the [Chrome Dev Channel]("http://www.chromium.org/getting-involved/dev-channel"), [Click here to download the Google Chrome 64-bit Ubuntu/Debian version]("https://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb").

1. Open Archive Manager with root privileges. Open Terminal: 
```
gksudo file-roller 
```
2. Open /home/USERNAME/Downloads google-chrome-unstable_current_amd64.deb
3. Browse to: /opt/google/chrome/PepperFlash/
4. Right-click libpepflashplayer.so Extract... libpepflashplayer.so to /usr/lib/chromium-browser/

Edit the 'default' text file:
```
gksudo leafpad /etc/chromium-browser/default
```

```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/libpepflashplayer.so --ppapi-flash-version=11.4.31.203"
```

YouTube works, watching a fullscreen YouTube video without problems. About Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065).

The original file 'default':
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS=""
```

---

### Post by Lyfang on 2012-10-24
"Shockwave Flash has crashed." playing Café World, a Facebook game. libpepflashplayer.so PPAPI Flash Version: 11.4.31.203. About Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065).

---

### Post by Lyfang on 2012-10-31
If you have Google Chrome installed too: I'm using Google Chrome version 22.0.1229.94 stable's Pepper Flash version 11.4.31.110 in Chromium. It works fine with Chromium version 22.0.1229.94 Ubuntu 12.10 (161065).

```
gksudo leafpad /etc/chromium-browser/default
```
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so --ppapi-flash-version=11.4.31.110"
```

See also: [HOW TO MAKE CHROMIUM USE FLASH PLAYER `PEPPER` FROM GOOGLE CHROME]("http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html")

---

### Post by Lyfang on 2012-12-04
> **Lyfang said:**
> **WARNING! Caution, don't try on production machines without fear of dealing with problems since this guide is using a development release!**

Pepper Flash from the [Chrome Dev Channel]("http://www.chromium.org/getting-involved/dev-channel"), [Click here to download the Google Chrome 64-bit Ubuntu/Debian version]("https://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb").

1. Open Archive Manager with root privileges. Open Terminal: 
```
gksudo file-roller 
```
2. Open /home/USERNAME/Downloads google-chrome-unstable_current_amd64.deb
3. Browse to: /opt/google/chrome/PepperFlash/
4. Right-click libpepflashplayer.so Extract... libpepflashplayer.so to /usr/lib/chromium-browser/

Edit the 'default' text file:
```
gksudo leafpad /etc/chromium-browser/default
```

```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/libpepflashplayer.so --ppapi-flash-version=11.4.31.203"
```

YouTube works, watching a fullscreen YouTube video without problems. About Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065).

The original file 'default':
```
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS=""
```
I downloaded today's Google Chrome stable 64-bit .deb and I have Pepper Flash 11.5.31.2 with Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065). Playing Café World, a Facebook game, without a crash so far. YouTube works great too. It would be great if an updated version of Pepper Flash existed in the Ubuntu repository for the Chromium browser.

---

### Post by Lyfang on 2012-12-13
> **Lyfang said:**
> I downloaded today's Google Chrome stable 64-bit .deb and I have Pepper Flash 11.5.31.2 with Chromium Version 22.0.1229.94 Ubuntu 12.10 (161065). Playing Café World, a Facebook game, without a crash so far. YouTube works great too. It would be great if an updated version of Pepper Flash existed in the Ubuntu repository for the Chromium browser.
My Pepper Flash version is 11.5.31.2 according to [Find Version | Flash Player - Adobe]("http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html") and the latest Pepper Flash version is: Chrome (Pepper-based Flash Player)	11.5.31.5 

STATUS is 11.5.31.0, ACTION is Up to Date according to [Firefox Web Browser — Plugin Check & Updates]("https://www.mozilla.org/en-US/plugincheck/") 

Question about Pepper Flash security vulnerabilities. Should I upgrade to the newest Pepper Flash by downloading the Google Chrome package for Linux and extract the latest Flash Player? If not, how often should I (manually) update the Pepper Flash Player? BTW Pepper Flash full-screen mode works for me.

I want to automate the process of upgrading Pepper Flash. I would like a BASH or Python script that downloads the latest Google Chrome stable and extracts Pepper Flash Player to the /usr/lib/chromium-browser/ folder. Can someone write a simple "pepper-flash-updater.sh" script?

---

### Post by iSKUNK! on 2013-01-16
> **Lyfang said:**
> I want to automate the process of upgrading Pepper Flash. I would like a BASH or Python script that downloads the latest Google Chrome stable and extracts Pepper Flash Player to the /usr/lib/chromium-browser/ folder. Can someone write a simple "pepper-flash-updater.sh" script?

I've written up just such a script, and attached it to [this Chromium bug report](http://code.google.com/p/chromium/issues/detail?id=169986) which aims to find a better solution. Hope it helps!

---

### Post by beefcakefu on 2013-02-28
> **iSKUNK! said:**
> I've written up just such a script, and attached it to [this Chromium bug report]("http://code.google.com/p/chromium/issues/detail?id=169986") which aims to find a better solution. Hope it helps!

Got a suggestion for your script. How about curl/wget Adobe's Flash test page [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) for Linux Chrome (Pepper-based Flash Player) updates? This ensures .debs are only downloaded with a new Pepper Flash version, rather than every new Chrome release.

---

### Post by iSKUNK! on 2013-03-07
> **beefcakefu said:**
> Got a suggestion for your script. How about curl/wget Adobe's Flash test page [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) for Linux Chrome (Pepper-based Flash Player) updates? This ensures .debs are only downloaded with a new Pepper Flash version, rather than every new Chrome release.

Downloading the ~37MB Chrome package when the Flash plug-in hasn't changed is a problem, which I've solved in a different way.

I would like to announce here an Ubuntu PPA I've put together, that provides a **pepflashplugin-installer** package that works in the same way as the Ubuntu flashplugin-installer package:

[CENTER][SIZE=4][https://launchpad.net/~skunk/+archive/pepper-flash/](https://launchpad.net/~skunk/+archive/pepper-flash/)[/SIZE]
[/CENTER]

This package is updated each time Google releases a new version of Chrome. However, it will only download the new Chrome package if you don't already have the plug-in files that would be installed. (The package checks the MD5 hashes of files under /usr/lib/pepflashplugin-installer/, and skips the download if the hashes match the latest version.)

The PPA supports Precise (12.04), Quantal (12.10) and Raring (13.04). Note that due to the way the Quantal and Raring packages are synchronized, their versions may fall behind compared to Precise. The packages are exactly the same for those three Ubuntu releases, so I would suggest adding "precise" lines to sources.list(.d) even if you're on a newer release:

```
deb     http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
```

If you're on Oneiric (11.10), you can still use this package, but you'll have to upgrade a couple of packages to the versions in Precise. (See the PPA description for details.)

---

### Post by beefcakefu on 2013-03-07
> **iSKUNK! said:**
> Downloading the ~37MB Chrome package when the Flash plug-in hasn't changed is a problem, which I've solved in a different way.

I would like to announce here an Ubuntu PPA I've put together, that provides a **pepflashplugin-installer** package that works in the same way as the Ubuntu flashplugin-installer package:

[CENTER][SIZE=4][https://launchpad.net/~skunk/+archive/pepper-flash/](https://launchpad.net/~skunk/+archive/pepper-flash/)[/SIZE]
[/CENTER]

This package is updated each time Google releases a new version of Chrome. However, it will only download the new Chrome package if you don't already have the plug-in files that would be installed. (The package checks the MD5 hashes of files under /usr/lib/pepflashplugin-installer/, and skips the download if the hashes match the latest version.)

The PPA supports Precise (12.04), Quantal (12.10) and Raring (13.04). Note that due to the way the Quantal and Raring packages are synchronized, their versions may fall behind compared to Precise. The packages are exactly the same for those three Ubuntu releases, so I would suggest adding "precise" lines to sources.list(.d) even if you're on a newer release:

```
deb     http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
```

If you're on Oneiric (11.10), you can still use this package, but you'll have to upgrade a couple of packages to the versions in Precise. (See the PPA description for details.)

Thanks for the PPA, works great!

For users who were already using Pepper Flash manually, you can remove the chromium flags for Pepper Flash plugin within `/etc/chromium-browser/default`. These flags are set for you in `/usr/lib/pepflashplugin-installer/pepflashplayer.sh`.

Cheers!

---

### Post by DJWYMAN on 2013-05-21
> **iSKUNK! said:**
> Downloading the ~37MB Chrome package when the Flash plug-in hasn't changed is a problem, which I've solved in a different way.

I would like to announce here an Ubuntu PPA I've put together, that provides a **pepflashplugin-installer** package that works in the same way as the Ubuntu flashplugin-installer package:

[CENTER][SIZE=4][https://launchpad.net/~skunk/+archive/pepper-flash/](https://launchpad.net/~skunk/+archive/pepper-flash/)[/SIZE]
[/CENTER]

This package is updated each time Google releases a new version of Chrome. However, it will only download the new Chrome package if you don't already have the plug-in files that would be installed. (The package checks the MD5 hashes of files under /usr/lib/pepflashplugin-installer/, and skips the download if the hashes match the latest version.)

The PPA supports Precise (12.04), Quantal (12.10) and Raring (13.04). Note that due to the way the Quantal and Raring packages are synchronized, their versions may fall behind compared to Precise. The packages are exactly the same for those three Ubuntu releases, so I would suggest adding "precise" lines to sources.list(.d) even if you're on a newer release:

```
deb     http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu precise main
```

If you're on Oneiric (11.10), you can still use this package, but you'll have to upgrade a couple of packages to the versions in Precise. (See the PPA description for details.)

ok I added these ppas and installed the package but my chromium shows me having the old flash from ubuntu its self is there something else I should do?

---

### Post by beefcakefu on 2013-05-21
> **DJWYMAN said:**
> ok I added these ppas and installed the package but my chromium shows me having the old flash from ubuntu its self is there something else I should do?

Hey DJWYMAN,

It's right there on the [project page]("https://launchpad.net/~skunk/+archive/pepper-flash/"):

[COLOR=#333333][FONT=Ubuntu Mono]MAKING CHROMIUM USE PEPPER FLASH[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Once the pepflashplugin-installer package is installed, you will need to configure Chromium to use the plugin. Open /etc/chromium-browser/default in a text editor and add the following line, after the CHROMIUM_FLAGS= assignment:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]    . /usr/lib/pepflashplugin-installer/pepflashplayer.sh[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono](I.e. a period, then a space, then the filepath.)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Restart Chromium, and load the chrome://plugins page to verify that the plugin is active. (Note that if you see a Flash plugin with a version of 11.2 or lower, then that is an old, non-PPAPI version of Flash. A current version of Pepper Flash will be 11.5 or higher.)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]Hope that helps![COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by DJWYMAN on 2013-05-21
> **beefcakefu said:**
> Hey DJWYMAN,

It's right there on the [project page]("https://launchpad.net/~skunk/+archive/pepper-flash/"):

[COLOR=#333333][FONT=Ubuntu Mono]MAKING CHROMIUM USE PEPPER FLASH[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Once the pepflashplugin-installer package is installed, you will need to configure Chromium to use the plugin. Open /etc/chromium-browser/default in a text editor and add the following line, after the CHROMIUM_FLAGS= assignment:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]    . /usr/lib/pepflashplugin-installer/pepflashplayer.sh[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono](I.e. a period, then a space, then the filepath.)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Restart Chromium, and load the chrome://plugins page to verify that the plugin is active. (Note that if you see a Flash plugin with a version of 11.2 or lower, then that is an old, non-PPAPI version of Flash. A current version of Pepper Flash will be 11.5 or higher.)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]Hope that helps![COLOR=#333333][FONT=Ubuntu Mono]

[/FONT][/COLOR]


I tried that but it did not work so I used the method that I was using before where I had chrome installed and was using it to leach off of like in this link : [http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

but instead of using:
 export PEPPER_FLASH_VERSION=$(grep '"version":' /opt/google/chrome/PepperFlash/manifest.json| grep -Po '(?<=version": ")(?:\d|\.)*')

I changed it to:
export PEPPER_FLASH_VERSION=$(grep '"version":' /usr/lib/pepflashplugin-installer/manifest.json| grep -Po '(?<=version": ")(?:\d|\.)*')

and instead of:
CHROMIUM_FLAGS="--ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so --ppapi-flash-version=$PEPPER_FLASH_VERSION"

I used:
CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/pepflashplugin-installer/libpepflashplayer.so --ppapi-flash-version=$PEPPER_FLASH_VERSION"

and that worked.

---

### Post by beefcakefu on 2013-05-22
Hey DJWYMAN,

Glad to hear you got 'pepper-flash' working.

> **DJWYMAN said:**
> I tried that but it did not work so I used the method that I was using before where I had chrome installed and was using it to leach off of like in this link : [http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

I suspect the instructions didn't work for you due to the conflicting chromium flags that were set in '/etc/chromium-browser/default' and '/usr/lib/pepflashplugin-installer/pepflashplayer.sh'. Web Upd8's method relied on Chrome being installed and kept up-to-date. With the alterations you described, it should now be safe to uninstall Chrome without breaking Chromium's flash.

Web Upd8's method greps the version number from 'manifest.json' each time '~/.profile' is processed. This extra step should not be noticeable from a performance standpoint, and likelihood of filename changes of 'manifest.json' or its variable name 'version' is extremely low, so you should be good there. But if you are interested, you can undo the changes made to '~/.profile' and amend your '/etc/chromium-browser/default' to look like this:

```
# Default settings for chromium-browser. This file is sourced by /bin/sh from# /usr/bin/chromium-browser


# Options to pass to chromium-browser
CHROMIUM_FLAGS=""
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

'&#822;p&#822;e&#822;p&#822;p&#822;e&#822;r&#822;-&#822;f&#822;l&#822;a&#822;s&#822;h&#822;'&#822; &#822;w&#822;i&#822;l&#822;l&#822; &#822;t&#822;h&#822;e&#822;n&#822; &#822;k&#822;e&#822;e&#822;p&#822; &#822;t&#822;h&#822;e&#822; &#822;v&#822;e&#822;r&#822;s&#822;i&#822;o&#822;n&#822; &#822;n&#822;u&#822;m&#822;b&#822;e&#822;r&#822; &#822;u&#822;p&#822;d&#822;a&#822;t&#822;e&#822;d&#822; &#822;f&#822;o&#822;r&#822; &#822;y&#822;o&#822;u&#822; &#822;i&#822;n&#822; &#822;'&#822;/&#822;u&#822;s&#822;r&#822;/&#822;l&#822;i&#822;b&#822;/&#822;p&#822;e&#822;p&#822;f&#822;l&#822;a&#822;s&#822;h&#822;p&#822;l&#822;u&#822;g&#822;i&#822;n&#822;-&#822;i&#822;n&#822;s&#822;t&#822;a&#822;l&#822;l&#822;e&#822;r&#822;/&#822;p&#822;e&#822;p&#822;f&#822;l&#822;a&#822;s&#822;h&#822;p&#822;l&#822;a&#822;y&#822;e&#822;r&#822;.&#822;s&#822;h&#822;'&#822;.&#822;

**Edit: **'pepper-flash' always keep the version number updated in '/usr/lib/pepflashplugin-installer/pepflashplayer.sh', the changes described will make chromium aware of the version number provided by 'pepper-flash'.

---

### Post by DJWYMAN on 2013-05-22
> **beefcakefu said:**
> Hey DJWYMAN,

Glad to hear you got 'pepper-flash' working.



I suspect the instructions didn't work for you due to the conflicting chromium flags that were set in '/etc/chromium-browser/default' and '/usr/lib/pepflashplugin-installer/pepflashplayer.sh'. Web Upd8's method relied on Chrome being installed and kept up-to-date. With the alterations you described, it should now be safe to uninstall Chrome without breaking Chromium's flash.

Web Upd8's method greps the version number from 'manifest.json' each time '~/.profile' is processed. This extra step should not be noticeable from a performance standpoint, and likelihood of filename changes of 'manifest.json' or its variable name 'version' is extremely low, so you should be good there. But if you are interested, you can undo the changes made to '~/.profile' and amend your '/etc/chromium-browser/default' to look like this:

```
# Default settings for chromium-browser. This file is sourced by /bin/sh from# /usr/bin/chromium-browser


# Options to pass to chromium-browser
CHROMIUM_FLAGS=""
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

'&#822;p&#822;e&#822;p&#822;p&#822;e&#822;r&#822;-&#822;f&#822;l&#822;a&#822;s&#822;h&#822;'&#822; &#822;w&#822;i&#822;l&#822;l&#822; &#822;t&#822;h&#822;e&#822;n&#822; &#822;k&#822;e&#822;e&#822;p&#822; &#822;t&#822;h&#822;e&#822; &#822;v&#822;e&#822;r&#822;s&#822;i&#822;o&#822;n&#822; &#822;n&#822;u&#822;m&#822;b&#822;e&#822;r&#822; &#822;u&#822;p&#822;d&#822;a&#822;t&#822;e&#822;d&#822; &#822;f&#822;o&#822;r&#822; &#822;y&#822;o&#822;u&#822; &#822;i&#822;n&#822; &#822;'&#822;/&#822;u&#822;s&#822;r&#822;/&#822;l&#822;i&#822;b&#822;/&#822;p&#822;e&#822;p&#822;f&#822;l&#822;a&#822;s&#822;h&#822;p&#822;l&#822;u&#822;g&#822;i&#822;n&#822;-&#822;i&#822;n&#822;s&#822;t&#822;a&#822;l&#822;l&#822;e&#822;r&#822;/&#822;p&#822;e&#822;p&#822;f&#822;l&#822;a&#822;s&#822;h&#822;p&#822;l&#822;a&#822;y&#822;e&#822;r&#822;.&#822;s&#822;h&#822;'&#822;.&#822;

**Edit: **'pepper-flash' always keep the version number updated in '/usr/lib/pepflashplugin-installer/pepflashplayer.sh', the changes described will make chromium aware of the version number provided by 'pepper-flash'.

thanks I rewrote my /etc/chromium-browser/default to look like that and it worked. I think the reason it did not work when I tried it before was because I was inputting . /usr/lib/pepflashplugin-installer/pepflashplayer.sh on the same line as CHROMIUM_FLAGS=""

also I had uninstalled chrome before my second post so yea that way worked as well but this one is far less complicated.

---

### Post by Lyfang on 2013-12-25
I'm running Debian Sid and have both Chromium and Google Chrome installed. My Chromium default (gksudo leafpad etc/chromium/default) currently looks like this:&#65279;
```
# Default settings for chromium. This file is sourced by /bin/sh from
# /usr/bin/chromium

# Options to pass to chromium
CHROMIUM_FLAGS="--password-store=detect"
CHROMIUM_FLAGS="-ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so --ppapi-flash-version=11.9.900.170"
```

---

### Post by Lyfang on 2014-01-20
[[COLOR=#000000][FONT=monospace]Pepper Flash Player Installer For Chromium Available In The Ubuntu 14.04 Repositories[/FONT][/COLOR]]("http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html")

---

### Post by Lyfang on 2014-05-20
[Fresh Player Plugin: Pepper Flash Wrapper For Firefox And Other NPAPI-Compatible Browsers]("http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html")

---

