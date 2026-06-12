---
title: "Hulu (Express Install is not supported)"
date: 2010-01-05
forum: Multimedia Software
---

### Post by tbzep on 2010-01-05
Hulu stopped working tonight.  Youtube still works, so the flash plugin shouldn't be the problem.  

I get this message when I start a Hulu video:

"Express Install is not supported on this operating system.  To upgrade, please visit: Flash player download center."

According to Firefox, I still have Shockwave 10.0 d21 installed. I was able to watch video on Hulu as recently as last night.

---

### Post by TracyO on 2010-01-05
Same problem here.

There was another post about Facebook Flash games not working ([http://ubuntuforums.org/showthread.php?t=1310920&highlight=flash+facebook](http://ubuntuforums.org/showthread.php?t=1310920&highlight=flash+facebook)).  I installed my restricted extras, but I'm still having the problem.

I went to freedancer's site (in the facebook thread) and uninstalled Flash, but re-installing it didn't work for me.  Now I'm trying to figure out what to do...

---

### Post by TracyO on 2010-01-05
Well, I think I got Flash 10 installed ([http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)), but Hulu's still not working (while other sites do).  

Also, the Hulu message shows Flash Download Center as a link, but I cannot click on it.  Hopefully it's the site, and it'll be back up soon.

---

### Post by firebug2 on 2010-01-06
I had the same problem.  Apparently, the issue is that Hulu now needs flash 10.  I installed it from the debian package provided by adobe, but firefox (and chrome) still showed shockwave flash version 9 something.

It turns out I had flash installed semi-manually long time ago and when you install new version via deb-package it does not supersede what is in $HOME/.mozilla/plugins.  What worked for me eventually was manually wiping out the libflashplayer.so from that folder.

HTH.

---

### Post by firebug2 on 2010-01-06
See also this thread
[http://ubuntuforums.org/showthread.php?t=1193479](http://ubuntuforums.org/showthread.php?t=1193479)

---

### Post by markbuntu on 2010-01-06
I am using hardy and, not paying a lot of attention installed flash 10 from the adobe site. Of course, it did not work, still showing flash9 in firefox.

To fix it all I had to do was move the usr/lib/adobe-flashplugin/libflashplayer.so to usr/lib/flashplayer-nonfree/. Now I have flash10.0r42 that works with Hulu.

Oops, update manager has a new flash 10 for me...lets see whats up with that...stand by.

Ok, still the same 10.0r42 but there is now a flashplayer.so in usr/lb/adobe-flashplugin that was not there before because I moved it. Hmmmmm,

It seems the adobe .deb installer, and Update Mangler are putting the new flash in the wrong place.

---

### Post by rkent on 2010-01-07
Just chiming in to say that markbuntu's procedure was the one that helped me.  

Just noticed earlier this evening that Hulu stopped working recently (hadn't been using it much, so can't say exactly when).  I went to the adobe site to download the .deb, as I am still on 8.04.  Install via dpkg, restart firefox, still didn't work.

Removed files from ~/.mozilla/plugins, still didn't work.

Copied the file into "flashplayer-nonfree", and that did the trick.  Oh yeah, I also restarted firefox after basically every operation.

Thanks!


> **markbuntu said:**
> I am using hardy and, not paying a lot of attention installed flash 10 from the adobe site. Of course, it did not work, still showing flash9 in firefox.

To fix it all I had to do was move the usr/lib/adobe-flashplugin/libflashplayer.so to usr/lib/flashplayer-nonfree/. Now I have flash10.0r42 that works with Hulu.

Oops, update manager has a new flash 10 for me...lets see whats up with that...stand by.

Ok, still the same 10.0r42 but there is now a flashplayer.so in usr/lb/adobe-flashplugin that was not there before because I moved it. Hmmmmm,

It seems the adobe .deb installer, and Update Mangler are putting the new flash in the wrong place.

---

### Post by tbzep on 2010-01-07
I got it working by using this script.  I saved it as a text file, then used chmod 755 to make it executable. 

Thanks to all who replied and to the authors of this script (noted in the first few lines) who made the fix as easy as a quick as copy/paste, and a few mouse clicks.  =D>

> #!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"


---

### Post by JSuresh on 2010-01-08
Just reiterating, this is what worked on both my Gutsy and Hardy machines:

Go to /usr/lib/  Here I found a folder named 'flashplugin-nonfree'.  If you have it too, this might work for you too.  Rename the libflashplayer.so in there to something like 'libflashplayer_old.so'.  Now go to adobe.com and find the flash player tar.gz.  It should have a new libflashplayer.so file in it.  Just put it in the /usr/lib/flashplugin-nonfree folder, restart firefox, and you're good to go!

If you don't know how to do any of the steps I mentioned, please don't hesitate to ask :KS

---

### Post by tjkopena on 2010-01-12
Note that if the above steps do not work for you, you may have an older Flash player installed that is taking precedence over verson 10 and preventing Hulu from working.  Go to Edit->Preferences->Main->Manage Add-ons->Plugins.  If you see more than one Shockwave Flash entry, you are having this problem.  I somehow had v9 installed in my user account, which was overriding the v10 I installed similarly to the directions above.  Disable the older version, restart Firefox, and you should be good to go.  These steps and those above fixed the problem for me.

---

### Post by slowtrain on 2010-01-16
> **firebug2 said:**
> It turns out I had flash installed semi-manually long time ago and when you install new version via deb-package it does not supersede what is in $HOME/.mozilla/plugins.  What worked for me eventually was manually wiping out the libflashplayer.so from that folder.

HTH.

Hi folks:  I've been pulling my hair out for a couple weeks on this one.  Hulu works fine on my Ubuntu work desktop (not that I ever use it there, ahem), but not at all on my home computer since late Dec.  I've got version 10 of the flash player installed via Synaptic, yet I kept getting the error that I didn't have a sufficiently up to date player.  Well, I looked in my .mozilla/plugins folder and there was a libflashplayer.so in there from 2008.  Thank you firebug2!!!

---

### Post by fixitdude on 2010-03-25
Why didn't someone flag that script above as a possible security problem?

You are downloading something from a strange site (which is down now) and installing it as ROOT!!!

If you used that script YOU MAY BE INFECTED! There was no reason apt-get couldn't have gotten the libcurl etc.. packages, and most likely they were already installed.

I don't know what you could do except uninstall "libcurl3 libnss3-1d libnspr4-0d" and re-install them from your normal apt-get sources. Then hope, because they could have done anything with a script as root.

How hard was it to look and see "http:" to a UNTRUSTED SITE and then just NOT DO IT????


On the upgrade to flash 10 what I found that worked is to simply use the System -> Synaptic Package Manager.

Hit "Reload" so your sources are up to date, and if you haven't updated everything lately you should do that. Close Firefox.

Now find "flashplugin-nonfree" by scrolling down the list. Select it for install (or upgrade).

Don't ask me why Ubuntu / Adobe is so lame about this simple install, but now you need to copy the new "libflashplayer.so" over to your user's plugin folder using a terminal.

If you want to save the old one (if it's still there):

mv ~/.mozilla/plugins/libflashplayer.so ~/libflashplayer-old1.so

sudo cp /usr/lib/adobe-flashplugin/libflashplayer.so ~/.mozilla/plugins/

If you go to Tools --> Add-ons in Firefox and select Plugins, you may see the old version and the new version, but it will use the new version so don't worry. Proof is if Hulu works again. You may have to clean up some directories if it doesn't work, see my next post.

You could probably download the plugin from adobe as previously mentioned, then just copy it into the plugin folder as shown above, but I didn't do it that way so I don't know if that would just work.



For security, and optional, I recommend making a new user that you will use just for flash and heavy javascript sites. This user would have no important files or private data on it so if there is ever a breach with flash or javascript you are OK.

To use firefox from that user, open a terminal window and log in as that user via "local" ssh, it allows quick X11 forwarding.

ssh -2 -Xc blowfish alt-user-name@127.0.0.1

Now type in "firefox &", then hit return. You can run that Firefox while your "normal" user Firefox is running. Very cool. Just leave the terminal window open and when you need to go to a flash site, start the "safe" Firefox.

Don't forget to copy the "libflashplayer.so" over for this new user as shown above.

---

### Post by fixitdude on 2010-03-27
I ran into *other* problems on another system trying to view Hulu shows, the fix is below, after the rant.

Why do these people always want the latest version? Why can't they just be compatible with the older versions, keep track of what versions are hitting the site and WAIT until most of the people visiting are using a newer version.

I don't like being forced to upgrade to a newer, possibly buggy version when I had a perfectly good setup the way it was.

And all those highly paid programmers over at Adobe can't make this a easy thing? WTF? STOP FORCING ME TO UPGRADE TILL YOU GET IT RIGHT, BASTARDS!!! 

Rant done....

If you still have problems, you need to get rid of any possible old copies of the old flash.

You can save the old one if you want, put it somewhere else, don't just rename it in place.

Note: I am not running a 64 bit version!!! As I understand it you need to install the "nspluginwrapper" stuff for that but like I said above don't use that untrusted "deb" file or the script, do it manually.

If you don't know if you are running a 64 bit version, do a "uname -m" and if it says "x86_64" somewhere in the line then you are 64 bit.

Plus, if you aren't running 64 bit, you won't have "nspluginwrapper" available, if I understand right.

Just to be clear, I'm running Hardy.

Check to make sure you have the correct NEW flash version where it should be, look at it's size against the new one you got from Adobe. And get rid of any old versions that may still be in there.

ls -al ~/.mozilla/plugins/

All you need for flash to work is a copy of "libflashplayer.so" in that folder! It doesn't need to be anywhere else!

I also got rid of any other copies in any other place, and had to remove "flashplugin-nonfree" on that system for some reason. And getting rid of "swfdec-mozilla" and "mozilla-plugin-gnash" is a good idea too.


sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

sudo apt-get update
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree

If you are still having problems, check all those directories for "symbolic links" to other places for flash stuff. The above should have removed them but who knows...

That made it work for me. Hope this helps others.

---

