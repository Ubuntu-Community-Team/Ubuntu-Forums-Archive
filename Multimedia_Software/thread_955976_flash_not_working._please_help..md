---
title: "flash not working. please help."
date: 2008-10-22
forum: Multimedia Software
---

### Post by thingy87654321 on 2008-10-22
hi 
i am running ubuntu 8.04 hardy heron edition on my toshiba satellite m45-s351 laptop computer. i am using mozilla firefox internet browser 2 [in synaptic packages] and i installed the following apps under the search term " flash"
gstreamer ffmpeg video plugin
swfdec flash player
gnash swf veiwer

and i cant play flash files on the web [like youtube]
i installed ubuntu 8.04 hardy heron edition on my friends toshiba satellite computer [same one i have] and he can watch flash videos

i treid installing windows emulator [wine]
and downloaded the following
firefox 3.0 for windows
flash player for windows

they installed fine but when i opened firefox it worked, i could watch youtube videos then, but then mozilla firefox crashed. and now 3 minutes after i open firefox it crashes again

i tried sarafi, same thing

i tried using firefox [the one for ubuntu] and tried watching youtube videos but it shows the little loading symbol, but also a mute`symbol, error symbol and 3 other symbols
i check to see if it was muted and it was not muted


it would be highly apecated if someone would help me out
:(

---

### Post by rocky5051 on 2008-10-22
First off, welcome to Ubuntu forums. :)

Second, you need to install the Adobe Flash plugin. Simply run this command:

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

Make sure Firefox is closed before you do it. Once it is installed, just open up your (linux version) of Firefox and Flash should work now.

Also, if this doesn't work, make sure you have the most up-to-date version of Wine (Wine-1.1.6) if you want Firefox to work without crashing.

Hope that helps.

EDIT: Make sure all of your repositories are selected in Synaptic, and that you have followed the instructions for Ubuntu users from WineHQ to get the most recent version of Wine (assuming you have some problem which keeps you using the windows version of Firefox for flash, which you should not).

---

### Post by dustigroove on 2008-10-22
You can also download the latest [Adobe Flash Player 10]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb") from Adobe's web site.

1) Download the Flash .deb package from the above link.
2) Double-click on it to launch the package installer.
3) Click on the "Install Package" button when prompted.

Cheers

---

### Post by thingy87654321 on 2008-10-22
dustigrove, rocky5051 i tried both of the options you gave me but none of them work
please help me out, i really need flash player to work

dustigrove, rock5051 thank you for your help:KS
please do not tell me i have to reinstall my o.s. i judt reinstalled it 2 weeks ago and finally got it the way i want:confused:

---

### Post by gandaran on 2008-10-23
you have to remove gnash and swfdec first, only then firefox can use adobe flash if it's installed, you must only have one kind of flash or version installed for it to work properly.

about those crashes, your os is updated? ubuntu firefox is the latest version 3.0.3?

---

