---
title: "adobe flash player"
date: 2011-08-24
forum: Multimedia Software
---

### Post by blue-phoenix on 2011-08-24
hey guys im needing to view a adobe flash crash report, or preferably watch the crash happen(in the code)
Ubuntu 11.04(up to date)
flash plugin - v11,0,1,98
flash aid - adobe beta, from adobe labs
Firefox - 6.0(according to the "about firefox" under help)
i have installed and reinstalled both the flash player and flash aid 
is there a way to do this and how?
the player works on some sites and not others is it possible that im up to date and there not?

---

### Post by hubertofliege on 2011-08-25
I'm having similar issues.  It crashes a lot.

---

### Post by blue-phoenix on 2011-08-25
if i could c the crash report or watch the crash happen i could fix it but i haven't found a way to do this yet

---

### Post by thewolfman on 2011-08-25
Hi chaps, 

cannot say this will help but it should, put the following in a terminal:

32 bit:

sudo apt-get remove flashplugin-installer
sudo dpkg -r adobe-flashplugin
sudo rm -rf "/usr/lib/adobe-flashplugin/"
sudo rm -f "/usr/lib/opera/plugins/libflashplayer.so"
sudo rm -f "/usr/lib/mozilla/plugins/libflashplayer.so"
sudo rm -f $(find "/home/" -name "libflashplayer.so")
sudo updatedb
locate libflashplayer.so 

then

sudo apt-get install flashplugin-installer

For 64 bit:

sudo apt-get purge --yes adobe-flashplugin
sudo apt-get purge --yes flashplugin-installer
sudo apt-get purge --yes flashplugin-nonfree
sudo apt-get purge --yes mozilla-plugin-gnash
sudo apt-get purge --yes swfdec-mozilla
sudo apt-get purge --yes browser-plugin-lightspark
sudo apt-get purge --yes mozilla-plugin-gnash
sudo apt-get purge --yes konqueror-plugin-gnash
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

Hope this helps.

Regards thewolfman:P

---

### Post by Derek Karpinski on 2011-08-25
Run flash-aid, and turn OFF HW accleration.  Worked for me.

---

### Post by blue-phoenix on 2011-08-25
my flash player is not just flat out refusing to work its only having problems with cirten sites like youtube plays fine, and a flash chat site works fine but on some sites when the play btn is pressed all frames that use the flash plugin crash
that is y i need to SEE the error report

---

