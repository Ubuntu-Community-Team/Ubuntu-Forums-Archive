---
title: "Flash video slow in Chrome browser"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Jerrac on 2010-06-01
Flash videos in Chrome are very choppy. In Firefox they're fine. Any suggestions on how I can figure out what's wrong? 

I'm using Ubuntu Lucid, and the latest Chrome I could get from Google a few days ago.

What other information would help?

Thanks!

---

### Post by mikeashelby on 2010-06-30
I've got the same problem. Really weird, 'cos it was running awesomely until recently. Now it's just slowing every thing down...

:(

Also on Lucid, which otherwise rocks!

---

### Post by Jerrac on 2010-06-30
I've been wondering if it has something to do with Adobe stopping the beta/alpha of 64bit flash. Did Ubuntu downgrade 64bit flash to 32bit in an update?

*goes to test his 32bit laptop*

---

### Post by Jerrac on 2010-06-30
Well, YouTube and Flash Player 10 played perfectly in HD on my 32bit laptop in Chromium.

I'll try my desktop again when I get home.

---

### Post by Jerrac on 2010-07-01
well, my desktop seems to work fine now. I don't know what the problem was...

Odd... Wish someone could have given me some troubleshooting tips, and give you som now.

---

### Post by mocoloco on 2010-07-08
Same thing here, no issues in FF but flash video is choppy in Chrome. Purging and reinstalling doesn't help. Anyone have another suggestion?

---

### Post by guigarfr on 2010-11-29
got the same problem in my desktop computer, using ubuntu 32 bits and chronium. Flash videos run badly, very slow showing only some frames.

---

### Post by grege on 2010-11-29
> **Jerrac said:**
> I've been wondering if it has something to do with Adobe stopping the beta/alpha of 64bit flash. Did Ubuntu downgrade 64bit flash to 32bit in an update?

*goes to test his 32bit laptop*

If you use AMD64 Ubuntu the installed flash is 32bit and it runs through nspluginwrapper. This is unsatisfactory for me when running Firefox 4 beta. Pages do not scroll smoothly and YouTube is unwatchable. Chrome installs it's own version of flash, so if you only use Chrome you can uninstall the Ubuntu supplied one. Chrome does not seem to mind having two flash installed, I presume it defaults to it's own version in preference.

I uninstalled flash and nspluginwrapper and got the 64 bit alpha flash from Adobe and manually copied it to /usr/lib/mozilla/plugins and now my Firefox 4 is as good as it should be.

---

### Post by lovinglinux on 2010-11-30
> **mocoloco said:**
> Same thing here, no issues in FF but flash video is choppy in Chrome. Purging and reinstalling doesn't help. Anyone have another suggestion?

> **guigarfr said:**
> got the same problem in my desktop computer, using ubuntu 32 bits and chronium. Flash videos run badly, very slow showing only some frames.

Chrome has it's own plugin file located at /opt/google/chrome/libgcflashplayer.so

So if only Chrome has this problem, you might want to disable the plugin that comes with it and let it use the one from the system. You can do that by typing about[noparse]:[/noparse]plugins in the address bar, the disabling the corresponding plugin.

Additionally, check these:

[Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

[Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

> **grege said:**
> If you use AMD64 Ubuntu the installed flash is 32bit and it runs through mozplugger. This is unsatisfactory for me when running Firefox 4 beta. Pages do not scroll smoothly and YouTube is unwatchable. Chrome installs it's own version of flash, so if you only use Chrome you can uninstall the Ubuntu supplied one. Chrome does not seem to mind having two flash installed, I presume it defaults to it's own version in preference.

I uninstalled flash and mozplugger and got the 64 bit alpha flash from Adobe and manually copied it to /usr/lib/mozilla/plugins and now my Firefox 4 is as good as it should be.

Flash 32bit on 64bit systems doesn't use mozplugger, which is another plugin. It uses nspluginwrapper.

**mozplugger description:**

> Plugin allowing external viewers to be launched inside Mozilla 

mozplugger allows you to seamlessly integrate external applications
to view files downloaded from the web that Mozilla can not normally
handle. The application is embedded within a Mozilla window as to act
like and feel like a true plugin.

This allows you to view PDFs, Postscript files, animations and
movies, amongst other file types all from within Mozilla (with
supporting applications).

The alpha 64bit from Adobe is the best solution for 64bit systems, although experience may vary.

Instead of downloading and moving it manually, get my [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension. You won't need to worry about flash updates, because whenever Adobe releases a new preview/beta version, I update the extension in order to warn you about the need for update. It downloads and extract the file for you. The extension also allows to install the 32bit if you want and also removes conflicting plugins.

---

### Post by grege on 2010-11-30
> **lovinglinux said:**
> 

Flash 32bit on 64bit systems doesn't use mozplugger, which is another plugin. It uses nspluginwrapper.

**mozplugger description:**



The alpha 64bit from Adobe is the best solution for 64bit systems, although experience may vary.

Instead of downloading and moving it manually, get my [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") extension. You won't need to worry about flash updates, because whenever Adobe releases a new preview/beta version, I update the extension in order to warn you about the need for update. It downloads and extract the file for you. The extension also allows to install the 32bit if you want and also removes conflicting plugins.

When i posted i meant nspluginwrapper, just what happens when you type stuff when you are tired.

I have installed your Firefox extension and it worked as expected. Great stuff.

---

### Post by grege on 2010-11-30
@LovingLinux

perhaps this thread is not the appropriate place for this, but ...

I did get a minor error in script as on my system /usr/lib/firefox-addons/plugins/ did not exist and the script ended with

libflashplayer.so
ln: creating symbolic link `/usr/lib/firefox-addons/plugins/libflashplayer.so': No such file or directory
Finished! You can close this terminal. You must restart Firefox now.

Flash still worked as Firefox 4 quite happily looked in /usr/lib/mozilla/plugins

I manually created the missing plugins folder and re-ran the script and then it made the symlink

cheers

ps
In general I do not understand the need to have a half dozen plugin folders spread through the system, when every program looks in /usr/lib/mozilla/plugins. It is just unnecessary complication, but that is for the Debian and Firefox devs

---

### Post by lovinglinux on 2010-11-30
Thanks for the feedback.

> **grege said:**
> In general I do not understand the need to have a half dozen plugin folders spread through the system, when every program looks in /usr/lib/mozilla/plugins. It is just unnecessary complication, but that is for the Debian and Firefox devs

Perhaps is because old versions of those programs used different locations, so they are created for compatibility reasons, just like they create dummy packages. For instance, flashplugin-nonfree is a dummy for flashplugin-installer, which is only available since Karmic. So, in order to provide compatibility with older versions of Ubuntu, I use flashplugin-nonfree in my extension, since it is available in all supported versions of Ubuntu.

---

### Post by tmcnulty1982 on 2011-02-07
I installed the Flash-Aid extension ([https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)), rebooted, and that fixed the issue for me - both the choppy video in both browsers and the slow scrolling in Chrome (as far as I can tell, Chrome just uses whatever Flash you have installed for Firefox).

I also removed nspluginwrapper; not sure if that's required or not.

Tobias

---

### Post by tmcnulty1982 on 2011-02-07
Nevermind, slow scrolling and choppy video are back after returning from suspend... *sigh*

---

### Post by Yamster on 2011-07-08
> **lovinglinux said:**
> Chrome has it's own plugin file located at /opt/google/chrome/libgcflashplayer.so

So if only Chrome has this problem, you might want to disable the plugin that comes with it and let it use the one from the system. You can do that by typing about[noparse]:[/noparse]plugins in the address bar, the disabling the corresponding plugin.


Just wanted to say thanks for this. I was having this problem where flash movies ran okay in Firefox but was choppy in Chrome.  Disabling the Flash plugins in Chrome fixed the problem.

---

