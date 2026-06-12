---
title: "Installing two versions of flash."
date: 2008-11-09
forum: Multimedia Software
---

### Post by Islington on 2008-11-09
I have flash 10 installed according to the sticky. Firefox works perfectly. Unfortunately there is one game that I play (a silly mmo) that refuses to work with flash 10 and Linux. I want to install flash 9 on another browser, while keeping my flash 10+Firefox untouched. Help me out, please.

THe other browser doesn't matter to me. K-melon, opera whatever...

---

### Post by lovinglinux on 2008-11-09
You could download the standalone version of flash 9 from [[COLOR="DarkRed"]**Adobe**[/COLOR]]("http://www.adobe.com/support/flashplayer/downloads.html") and open the game with it, so you don't have to install another browser.

Scroll down that page until you see a Linux debugger/standalone version, then extract the content of the tar file and grab the "flashplayer.tar.gz" that is inside the extracted /standalone/release folder. Extract the "flashplayer.tar.gz" and you have the standalone flashplayer.

---

### Post by psyke83 on 2008-11-09
> **Islington said:**
> I have flash 10 installed according to the sticky. Firefox works perfectly. Unfortunately there is one game that I play (a silly mmo) that refuses to work with flash 10 and Linux. I want to install flash 9 on another browser, while keeping my flash 10+Firefox untouched. Help me out, please.

THe other browser doesn't matter to me. K-melon, opera whatever...

You can try the [Flash Switcher]("https://addons.mozilla.org/en-US/firefox/addon/5044") Firefox extension, though it wasn't updated to be compatible with the latest release of Firefox. You'll need to force compatibility via [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/6543").

---

### Post by gandaran on 2008-11-10
> **Islington said:**
> I have flash 10 installed according to the sticky. Firefox works perfectly. Unfortunately there is one game that I play (a silly mmo) that refuses to work with flash 10 and Linux. I want to install flash 9 on another browser, while keeping my flash 10+Firefox untouched. Help me out, please.

THe other browser doesn't matter to me. K-melon, opera whatever...
this can be easily done by just installing flash (libflashplayer.so file) manually for firefox in home/'user'/.mozilla/plugins folder, flash installed in any root file system firefox/mozilla plugins folder can be detected by other browsers but not in the hidden home folder, only firefox and every firefox clone can do that
now you just install another version of flash manually for opera, it must be in /usr/lib/opera/plugins.
to install flash download the tar.gz packages from adobe, unpack and just copy/paste or drag the libflashplayer.so file to the target folders

another way; keep the flash already installed in file system for all browsers, install the extra one in home/'user'/.mozilla/plugins, then go to firefox » tools » addons » plugins, click the flash plugin, disable one of them and restart firefox.
do this everytime you have to switch flash version

edit; the last tip mite not work, disabling one flash version can disable all flash in firefox

---

