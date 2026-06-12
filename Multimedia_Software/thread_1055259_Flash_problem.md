---
title: "Flash problem"
date: 2009-01-30
forum: Multimedia Software
---

### Post by Zoquara on 2009-01-30
I do have the Flash plug-ins for Firefox installed. They worked fine til I fixed my sound problem... Now, they show up as giant gray play buttons.
Example:
[This website.]("http://upperechelonguild.com")Currently, it shows up to me as a black background with a huge gray "play button" on it. Ads on other webpages do the same.

What I did: I followed the directions on parts A & B, and my sound worked great. I'm wondering if I disabled something I shouldn't have, and how to re-enable it if so? I'm new to this, and don't want to screw up too horribly!

---

### Post by Zoquara on 2009-01-30
Still looking for a solution, please. I'm on 8.04, if that helps any.

---

### Post by gandaran on 2009-01-31
remove the swfdec flash plugin you have installed, firefox is using this plugin not adobe flash, check that the only flash plugin you must have installed is adobe flash or firefox will use any other.

---

### Post by Zoquara on 2009-01-31
At risk of sounding like a complete moron... How do I do that?

To clarify, I've checked in the Preferances and Addons in Firefox, and am not finding anything.. Unless the Totem set of stuff is interfering with Adobe Flash?

---

### Post by reahjw6 on 2009-01-31
Sytem>administration>synaptic type swfdec mark for complete removal.

---

### Post by redroad55 on 2009-01-31
Hi, I found this how too to be helpful for many things

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

this is from above guide

 > --TROUBLESHOOTING--


ADOBE FLASH PLAYER


On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.


UBUNTU FAMILY 8.04+ USERS ONLY


Note: You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

sudo apt-get purge flashplugin-nonfree

32-Bit Users Only: Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on this page of Adobe's site, then executing it and entering your root password when prompted.

32/64-bit Users: Alternatively, 32-bit users can download the Tar archive from the same link provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of this page to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so

You may now restart your web browser and use the plugin.



In addition I developed this same problem and I think that it came with last up dates hope this will be solved in next weeks updates .. Hope this helps .. best to you .. post back with results and or questions..

How I fixed was select applications choose ADD/REMOVE ..top center of page at "SHOW" open drop down box select "third party" and you should have flash player at top , check the box hit apply and it will install

---

### Post by Zoquara on 2009-01-31
Thank you guys SO much! It's working again!

Someday soon I hope I'll know how to use this OS effectively >.<

---

### Post by reahjw6 on 2009-01-31
We all need help and this forum is great for just that.
The guys on here have realy help me so much.
The best place to start.
Reah.

---

