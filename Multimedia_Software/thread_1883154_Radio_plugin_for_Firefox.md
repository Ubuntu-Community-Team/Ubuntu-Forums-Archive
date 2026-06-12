---
title: "Radio plugin for Firefox"
date: 2011-11-18
forum: Multimedia Software
---

### Post by glennbates on 2011-11-18
On my old computer, I had a plugin where I selected a station and listened to music on the top of my firefox window.  Anyone know how to enable/install that?  May even be different on Linux.  Or, maybe even a better way to have music now that I am using Linux.  Any suggestions?  Thanks!

---

### Post by ajgreeny on 2011-11-18
Have a look at radiotray from [http://sourceforge.net/projects/radiotray/files/releases/radiotray_0.6.4_all.deb/download?use_mirror=ignum](http://sourceforge.net/projects/radiotray/files/releases/radiotray_0.6.4_all.deb/download?use_mirror=ignum)

It's a small applet for your panel, not the firefox window.  I have no idea if it will work in 11.04 or 11.10 unity desktops, but it certainly does in the classic gnome2 desktop of 10.04.

---

### Post by glennbates on 2011-11-18
> **ajgreeny said:**
> Have a look at radiotray from [http://sourceforge.net/projects/radiotray/files/releases/radiotray_0.6.4_all.deb/download?use_mirror=ignum](http://sourceforge.net/projects/radiotray/files/releases/radiotray_0.6.4_all.deb/download?use_mirror=ignum)

It's a small applet for your panel, not the firefox window.  I have no idea if it will work in 11.04 or 11.10 unity desktops, but it certainly does in the classic gnome2 desktop of 10.04.
Looks awesome but I can't get it to run.  Do I have to reboot the computer after installing it?

---

### Post by ajgreeny on 2011-11-18
No, you shouldn't need to do that, but the default configuration does not seem to work properly, as far as I can see.

Delete the config file with ```
rm ~/.local/share/radiotray/config.xml
``` in your home folder, or use nautilus to do the same.   Now run ```
killall radiotray
``` to make sure it is not running, and then start it again from the menu.  A dialog box will appear asking if you want it to show as an app indicator or an icon in the notification area;  choose icon;  I chose app indicator the first time but it showed nothing, so had to start again.

---

### Post by glennbates on 2011-11-18
> **ajgreeny said:**
> No, you shouldn't need to do that, but the default configuration does not seem to work properly, as far as I can see.

Delete the config file with ```
rm ~/.local/share/radiotray/config.xml
``` in your home folder, or use nautilus to do the same.   Now run ```
killall radiotray
``` to make sure it is not running, and then start it again from the menu.  A dialog box will appear asking if you want it to show as an app indicator or an icon in the notification area;  choose icon;  I chose app indicator the first time but it showed nothing, so had to start again.
Still nothing.  It did stop it running in the background because it actually came up again and asked with radio buttons, 

o Icon in the Notification Area
o App Indicator

---

### Post by ajgreeny on 2011-11-18
If you chose the notification area icon, and have the notification area enabled on your system (11.10 may be different) you should see a small icon like the blue one under my cursor in the screenshot.

---

### Post by shantiq on 2011-11-19
maybe you have looked there already but on gnome 3 it appears

 in Applications/Sound and video then shows in topbar

and is a brilliant little applet   extra help [**here**]("http://www.liberiangeek.net/2011/10/how-to-install-and-use-radiotray-in-ubuntu-11-10-oneiric-ocelot/") for Oneiric


=========================================

actually going back to original question > 
On my old computer, I had a plugin where I selected a station and listened to music on the top of my firefox window


the plugin you need is probably[** Mediapimp**]("https://addons.mozilla.org/en-US/firefox/addon/mediapimp-internet-radio-save-/?src=search") although there seems to be issues with VLC plugin

---

### Post by glennbates on 2011-11-19
Not sure what I did different but it is now working.  When I first turn it on, I get the name of the song and artist.  How do I see that again without restarting it?

---

### Post by ajgreeny on 2011-11-19
> **glennbates said:**
> Not sure what I did different but it is now working.  When I first turn it on, I get the name of the song and artist.  How do I see that again without restarting it?
This is radiotray?  I've never seen that, just the radio station name shows on my setup, or with the stations I use.

---

### Post by glennbates on 2011-11-19
> **ajgreeny said:**
> This is radiotray?  I've never seen that, just the radio station name shows on my setup, or with the stations I use.
Yes, it's radiotray.  Every time a new song comes on, it will give the title and artist for about 6 to 8 seconds.

---

### Post by shantiq on 2011-11-20
> Yes, it's radiotray. Every time a new song comes on, it will give the title and artist for about 6 to 8 seconds.



i think that is what it does i do not think it can be controlled tho

---

