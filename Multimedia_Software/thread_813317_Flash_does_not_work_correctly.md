---
title: "Flash does not work correctly"
date: 2008-05-30
forum: Multimedia Software
---

### Post by Klonoa on 2008-05-30
Flash player works but it moves very choppy and slow, it seems to be the flash player because it did the same in openSUSE and Mandriva, is there anything I can do?

---

### Post by bannik on 2008-05-30
> **Klonoa said:**
> Flash player works but it moves very choppy and slow, it seems to be the flash player because it did the same in openSUSE and Mandriva, is there anything I can do?

nothing you can do, its the same for a lot of people even me, its flash problem for not making flash compatible with linux.

maybe you can tinker so that VLC might stream videos for you

---

### Post by Bakon Jarser on 2008-05-30
You could try gnash and if that doesn't work you could try installing flash 10 beta, although I know there are bugs with it because I have tried it myself.  Still it would be better than having unwatchable flash videos.  But try gnash first.  Uninstall flash before you install gnash.  there is probably a how to posted somewhere on the forum if you search for it.

---

### Post by pdadad on 2008-05-30
I'm new to Ubuntu so I can only share from what worked for me, but Flash seems to work well with Firefox 2.0.0.14 in Gutsy.

I did the following to make it work:
Shut down your browsers. Download the .tar.gz file extract the contents. [ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")Double click on the flashplayer-installer. Click on "run in terminal". Click enter after verifying that you shut down your browsers. For Firefox type "y" to agree to install the plugin in /home/<user>/.mozilla. Then delete xpti.dat from /home/<user>/.mozilla/firefox/aogi9o89.default.

The one problem I had was that it did not help Opera, which is my primary browser.

I hope this helps.

---

### Post by ubuntu-freak on 2008-05-30
Give Adobe Flash v10 beta a try, it works much better. Disabling effects may help also, as v10 beta should use hardware acceleration. 
 
This is taken from my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683), check it out for more multimedia-related advice, or if you wish to use v10 beta in Gutsy.
 
 
 **[COLOR="DarkRed"]UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY[/COLOR]**
 
 
 Install the Flash plugin manually by downloading the tar archive of [Adobe Flash v10 beta](http://labs.adobe.com/downloads/flashplayer10.html). Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:
 
 **[COLOR="DarkRed"]32-Bit Ubuntu Family Users Only:[/COLOR]**
 
 **sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplugin-alternative.so**
 
 You may now restart Firefox and use the plugin.
 
 **[COLOR="DarkRed"]64-Bit Ubuntu Family Users Only:[/COLOR]**
 
 **sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so**
 
 You may now restart Firefox and use the plugin.   
 
Nathan

---

### Post by Klonoa on 2008-05-31
Flash Player 10 Works, its Amazing, but for some reason I can't get ti to work in Opera.

---

### Post by gandaran on 2008-05-31
> **Klonoa said:**
> Flash Player 10 Works, its Amazing, but for some reason I can't get ti to work in Opera.

flash 10 only works with opera 9.50b2!
get opera [http://www.opera.com/download/linux/?ver=9.50b2](http://www.opera.com/download/linux/?ver=9.50b2)

if you already have opera 9.50b2 installed and doesn't work with the flash, it's because you installed flash 10 in the home .mozilla folder, if this is the case then just copy the plugins folder in the hidden home .mozilla folder and paste in the home .opera folder.
if the flash is not in the home .mozilla directory, then find out where you installed it on the file system.

---

### Post by stevoo on 2008-05-31
the problem is not with flash ... but basically that flash is uploading something instead of downloading thus cutting your download nad causing lag .... 

have no idea why , i have the same problem

---

### Post by stevoo on 2008-05-31
> **stevoo said:**
> the problem is not with flash ... but basically that flash is uploading something instead of downloading thus cutting your download nad causing lag .... 

have no idea why , i have the same problem


Well the small command seems to have solved this .... 
the upload think


Thanx

---

### Post by wiljohnson on 2009-06-23
> **ubuntu-freak said:**
> Give Adobe Flash v10 beta a try, it works much better. Disabling effects may help also, as v10 beta should use hardware acceleration. 
 
This is taken from my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683), check it out for more multimedia-related advice, or if you wish to use v10 beta in Gutsy.
 
 
 **[COLOR="DarkRed"]UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY[/COLOR]**
 
 
 Install the Flash plugin manually by downloading the tar archive of [Adobe Flash v10 beta](http://labs.adobe.com/downloads/flashplayer10.html). Simply open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:
 
 **[COLOR="DarkRed"]32-Bit Ubuntu Family Users Only:[/COLOR]**
 
 **sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplugin-alternative.so**
 
 You may now restart Firefox and use the plugin.
 
 **[COLOR="DarkRed"]64-Bit Ubuntu Family Users Only:[/COLOR]**
 
 **sudo apt-get purge flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo nspluginwrapper -i /usr/lib/flashplugin-nonfree/libflashplayer.so && sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so && sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so**
 
 You may now restart Firefox and use the plugin.   
 
Nathan

This works with 9.04 Thanks

---

