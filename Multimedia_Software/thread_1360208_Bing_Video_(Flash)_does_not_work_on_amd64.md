---
title: "Bing Video (Flash) does not work on amd64"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Vermind on 2009-12-20
Hi,
I tried to watch [The Guild]("http://www.bing.com/videos/watch/video/season-3-episode-4-get-it-back/y0gz7sy4") on my 64-bit Ubuntu Intel desktop (nvidia graphics) with the native 64bit Flash from Adobe (manual install), and the 32-bit one from Ubuntu repositories (flashplayer-installer). Both work flawlessly on Youtube, but show the white "loading" circle on Bing Video. Unfortunately, The Guild is not available on youtube any more, just on Bing Video. Any ideas?

I also tried with a 32-bit asus eee with Intel graphics, but the current experimental version of the Interl driver that I am using crashes the X when playing Flash.

---

### Post by mgmiller on 2009-12-20
Not sure what to tell you.  I have a clean install of 64 bit Karmic and I also am using the manual install of the native 64bit flash plug in and your link plays fine on my system.  I have an Nvidia 8600GT video card using the version 185 driver installed from the driver utility.

Are you sure you only have 1 version of flash installed?
Check in Synaptic and make sure you do not have flashplugin-installer, flashplugin-nonfree or 
any gnash packages installed.

If you did the manual install of the native 64 bit flash, you have to make sure all the others are removed.  If you do find they are there, then after removing them, you may need to reinstall the 64 bit one from Adobe again and restart Firefox.

---

### Post by Vermind on 2009-12-22
I copied my home onto a brand new 32 bit install on the same machine. Guess what? Same problem. I therefore deduced that my home must be sick.

I proceeded to rectify the problem with the following commands (don't try unless you know what they do):
```
mkdir dotfiles; mv $( ls -a | awk 'NR > 2 && $0 ~ "^\\..*" { print $0 }' ) dotfiles/.
```
This moves my configuration files, everything that begins with a dot, into a folder called dotfiles. I executed these commands in my home directory, in a virtual terminal (Ctrl-Alt-F2) without being logged in to the graphical environment (to prevent gconf or gvfs going awry).
I then copied back only the bare necessities; I left uncopied things that affect my desktop a lot, such as .config and .gnome*, in order to try to solve the problem. I copied back important things such as .Skype, .purple, .wesnoth1.6, .openoffice, .gstreamer, .evolution, .mozilla*, .local, and so on. Full list and command:
```
cd dotfiles; cp -r .amsn .arch-params .bash* .crossfire .crystalspace .cups .daimonin .dbus* .dia .dockbarx .dosemu .dropbox* .dvdcss .eclipse .emacs* .evolution .face .fillets-ng .font* .frozen-bubble .gimp-2.6 .googleearth .gqview .gstreamer-0.10 .gtk-bookmarks .htpasswd* .hugin .i* .j* .keystore .lbrc.conf .local .liferea_1.6 .macopix .mozilla* .mp3crc .mplayer .multisync .nano_history  .ngdstudios .open* .pengu* .phoronix-test-suite .profile .purple .qalculate .quakelive .rolauncher  .scorched3d/ .screen* .signature.txt .spring* .ssh .stratagus-2.1 .subversion/ .synaptic .synergy.conf .teeworlds .themes .tomboy* .toribash .ubuntu-tweak .ufoai .ufrawrc .ultrastar .unison .uqm .ut200* .vim* .w* .x* .Skype .PlaneShift .SciTEUser.properties .W* .FreeCAD .BillardGL.conf.v7 ..
```
After this, I logged back in to this cleaned user account. To make sure everything would really take and even dbus would forget my older settings, I restarted the machine.

And guess what, Flash works there now. I wonder if this solves some of my other mystery issues as well. I also am forced to wonder what in my config was so offending...

---

### Post by Tantor on 2010-08-26
Same problem here. Inspired by the solution above, I removed the .adobe and .macromedia folders in my home folder and it got fixed. I had all Flash permissions disabled; apparently Bing needs to be able to set some sort of Flash cookie to work. Anyway, solved also here. Thanks for the info.

---

