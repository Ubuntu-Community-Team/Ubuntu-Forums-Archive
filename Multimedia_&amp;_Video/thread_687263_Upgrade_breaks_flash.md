---
title: "Upgrade breaks flash"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by Iskendar on 2008-02-04
Ok, did an upgrade using adept_manager yesterday (using kubuntu 7.10), and suddenly the flash player is broken. No more youtube for me :-( Checked it both in opera 9.25 and firefox 2.0.0.11, opera shows a grey square where the youtube vid should be, firefox plays only audio. Same applies for non-video flash sites.

Javascript is on in both browsers, and when checking in adept_manager, flashplugin-nonfree 9.0.48.0.2+really0ubuntu12.1 is installed. Tried uninstalling/reinstalling, doesn't change a thing. When I check plugins in firefox with "about:plugins" I get this bit:

Shockwave Flash

File name: libflashplayer.so
Shockwave Flash 9.0 r115

MIME Type                    Description               Suffixes    Enabled
application/x-shockwave-flash    Shockwave Flash    swf    Yes
application/futuresplash    FutureSplash Player    spl    Yes

In opera, Tools->Preferences->Advanced->Plugin-options shows these relevant bits:

Name                       Description                            Path
Shockwave Flash      Shockwave Flash 9.0r115      /usr/lib/flashplugin-nonfree/libflashplayer.so
Shockwave Flash      Shockwave Flash 9.0r115      /usr/lib/firefox/plugins/flashplugin-alternative.so
Shockwave Flash      Shockwave Flash 9.0r115      /usr/lib/mozilla/plugins/flashplugin-alternative.so

The last two are links to /etc/alternatives/firefox-flashplugin which itself is a link to /usr/lib/flashplugin-nonfree/libflashplayer.so, so there's only one version installed. Can't figure out what the problem is, tried un- and reinstalling the flash player, but that doesn't do zip. Haven't tried a manual reinstall yet, I try to stay within the package management system as much as possible (after all, it *should* work). Everything worked fine until the full upgrade yesterday. Any help?

---

### Post by gandaran on 2008-02-04
opera 9.25 doesn't work with flash 9.0.115, you will have to install the opera beta 9.50b, otherwise forget opera.

probably you installed the broken flash package, see this [http://ubuntuforums.org/showthread.php?t=686624](http://ubuntuforums.org/showthread.php?t=686624)

is your kubuntu 7.10, 32 or 64 bit ?

---

### Post by Iskendar on 2008-02-04
> **gandaran said:**
> opera 9.25 doesn't work with flash 9.0.115, you will have to install the opera beta 9.50b, otherwise forget opera.

probably you installed the broken flash package, see this [http://ubuntuforums.org/showthread.php?t=686624](http://ubuntuforums.org/showthread.php?t=686624)

is your kubuntu 7.10, 32 or 64 bit ?

32 bit. Meanwhile, I tried downloading the flash plugin from adobe directly and untarring it in /usr/lib/flashplugin-nonfree. Same problem, audio only in firefox.

---

### Post by gandaran on 2008-02-04
you installed the flash 9.0.115 you downloaded on a flash 9.0.48 folder?  (flashplugin-nonfree), I think that will never work!

try this,
          copy the libflashplayer.so and flashplayer.xpt file from the /usr/lib/flashplugin-nonfree or where ever you installed flash, then paste in a new folder (rename it » plugins «) on you home/user/.mozilla folder (I don't know if there is a home mozilla folder in kubuntu! I use ubuntu.) then uninstall that flashplugin-nonfree,
if this doesn't work try reinstall firefox.

---

### Post by Iskendar on 2008-02-07
> **gandaran said:**
> you installed the flash 9.0.115 you downloaded on a flash 9.0.48 folder?  (flashplugin-nonfree), I think that will never work!

 Why not? Opera identifies the installed plugin as 115 and points to that directory, and the .so files in /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins files both point to that flashplugin-nonfree file. Where should the 115 .so file reside, if not there?

> **gandaran said:**
> 
try this,
          copy the libflashplayer.so and flashplayer.xpt file from the /usr/lib/flashplugin-nonfree or where ever you installed flash, then paste in a new folder (rename it » plugins «) on you home/user/.mozilla folder (I don't know if there is a home mozilla folder in kubuntu! I use ubuntu.) then uninstall that flashplugin-nonfree,
if this doesn't work try reinstall firefox.

Firefox is the same in (k)ubuntu. Problem with installing in ~/mozilla/plugins is obviously that it will only work for one user (it's my home pc, but I still have 2 on it). But I'll try it.

---

### Post by gandaran on 2008-02-07
> **Iskendar said:**
> Why not? Opera identifies the installed plugin as 115 and points to that directory, and the .so files in /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins files both point to that flashplugin-nonfree file. Where should the 115 .so file reside, if not there?



Firefox is the same in (k)ubuntu. Problem with installing in ~/mozilla/plugins is obviously that it will only work for one user (it's my home pc, but I still have 2 on it). But I'll try it.

when you install flashplugin-nonfree 9.0.48, a firefox configuration file is also installed, so firefox will be looking for that particular flash, if it's not there it rejects anything else. you can copy that .so file to /usr/lib/mozilla for all users then uninstall flashplugin-nonfree or copy to home mozilla folder and if it works on firefox then just copy that home .mozilla plugin folder to the second user account home .mozilla folder, do the same for the opera browser  home .opera folder, I am using opera that way, and it's easier if you need to update flash. 
only opera 2.50b will work with flash 9.0.115 . 

any way if you have any problems you can install flash this way!

the easy way to install flash is to let firefox install it for you, find a webpage that needs flash, when you get that message flash plugin missing you just click install, but to do that, first you must remove/deactivate the ubufox addon extension (look it up on firefox menu bar»tools»extras/addons) close and restart firefox, you can activate it later if you wish,
uninstall first any flash, like flashplugin-nonfree or gnash if you happen to have any of these installed.

if you have the ubufox activated it will install using synaptic package manager which has the broken flash package!

disabling ubufox extension will allow a direct install from the adobe flash site (updated flash 9.0.115) on your home mozilla folder , try it .

only for 32-bit ubuntu 7.10 (not sure it works on kubuntu)

gandaran

---

### Post by dracovich on 2008-02-07
Hey guys, i think i may be having a similar problem. I just earlier installed a flash update, i honestly can't remember exactly what it was, as it came into my automatic update wizard thingy in the upper right corner. I tend to install whatever it tells me to and assume that it's safe, so i don't think too much about it when i just click update.

Following this firefox has been telling me i don't hvae the right plugins to play flash videos, and when i click on it to install flashplayer, it tells me that flash player is already installed. I t also gave me an option of installing something called "GNASH", which i did, but that seemed to make things worse if antyhing now it tries to play them but fails.

---

### Post by samwyse on 2008-02-07
I got this problem in Kubuntu. Fix it with:

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

---

### Post by dracovich on 2008-02-07
Ok cool that fixed it for me as well. Weird though, i had tried marking the plugin in synaptics for re-installation, which i assumed did exactly what those two commands did, but that didn't help.

---

### Post by gandaran on 2008-02-08
> **samwyse said:**
> I got this problem in Kubuntu. Fix it with:

sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

I have tried that way many times in three different computers and it never works,
I had to install using another method !


update:
confirmed; flashplugin-nonfree is back, I believe the link was repaired a couple days ago
it will install an alternative version of flash now, not sure if it's 9.0.115

---

### Post by samwyse on 2008-02-08
There was a new upgrade today to both firefox and flashplugin-nonfree that work.

---

### Post by Rapax on 2008-02-10
Having the same problem here. Kubuntu 7.10, Opera 9.25. I did my standard apt-get upgrade today, now opera shows only gray squares for flash stuff. Firefox still works fine (but using firefox is painful if you're used to the goodness of opera).

---

### Post by PhilipOwrutsky on 2008-02-11
Yeah, def still doesn't work for me in 64 bit land...

---

### Post by hugomeeuwes on 2008-02-13
I got an similar problem.
Bij typing about: plugins (no space after : ) in the address bar in firefox, I saw the flash plugin of crossover office on top.
Probably, after updating flash, this one got on top, so every install I tried failed, because it wasn't used.
I just removed the cxoffice flash plugin (~/.cxoffice/win98/desktopdata/cxnsplugin/linux/do sdevices_c^3A_windows_system32_Macromed_Flash_NPSW F32.dll.so) and restarted firefox.
Automatically firefox took the next plugin and worked!

---

### Post by ubuntu-freak on 2008-02-13
See paragraph 7 of "Troubleshooting" in my  [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

### Post by Pandarsson on 2008-02-17
Okay, I've had the same problem twice after upgrading - in both Konqueror and Firefox - and have found that the problem is flashplugin-alternative.so.  Once I delete those (and in the case of Konqueror, rescan for plugins), flash works just fine.  I'd just like to know which dang package puts that file in there so I can avoid updating it.  Anyone know?

---

### Post by ubuntu-freak on 2008-02-17
It was a temporary fix for flash cos the repo one was broken.
 
Nathan

---

