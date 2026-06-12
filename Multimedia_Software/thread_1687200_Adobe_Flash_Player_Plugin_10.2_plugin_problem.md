---
title: "Adobe Flash Player Plugin 10.2 plugin problem"
date: 2011-02-13
forum: Multimedia Software
---

### Post by babltiga on 2011-02-13
I have ubuntu 10.04.1 (x64), after updating system, the adobe flash player plugin was updated to version 10.2.152.27ubuntu0.10.04.1 and now all the browsers (Firefox 3.6.13, Opera 11 and Chrome 9.0.5x) doesn't see the plugin and now it is not possible to view pages with flash, even You Tube :D

---

### Post by babltiga on 2011-03-16
Solved by completely removing old flash-player plugin and installing new one from a scratch ...

---

### Post by chitowner2 on 2011-04-13
So where in ubuntu 10.4 does one find the installed flash player?

I tried running a locate *flash* and it didn't turn up, but my firefox 4 is definitely using flash 9.

???
CT

---

### Post by Karlchen on 2011-04-13
> **chitowner2 said:**
> So where in ubuntu 10.4 does one find the installed flash player?System => System Administration => Synaptic Package Administration (Genuine English terms may be slightly different, I translated back from German.) Search for "adobe-flashplugin".

Karl

---

### Post by chitowner2 on 2011-04-14
Sorry, but what I meant was, where IN A DIRECTORY TREE would the flashplayer plugin normally be found? Assume using FireFox.

CT




> **Karlchen said:**
> System => System Administration => Synaptic Package Administration (Genuine English terms may be slightly different, I translated back from German.) Search for "adobe-flashplugin".

Karl

---

### Post by Karlchen on 2011-04-14
Hello, chitowner2.

Went to System => System Administration => Synaptic Package Administration. Selected "adobe-flashplugin". Right-clicked it and selected "Properties" => tab "Installed files". Checked the listed pathnames.

_Result:_
/usr/share/doc/adobe-flashplugin
**/usr/lib/adobe-flashplugin/libflashplayer.so** (the plugin file)
/usr/lib/xulrunner-addons/plugins (symlink) => /etc/alternatives/firefox-flashplugin
/usr/lib/xulrunner/plugins (symlink) => /etc/alternatives/firefox-flashplugin
/usr/lib/mozilla/plugins (symlink) => /etc/alternatives/firefox-flashplugin
/usr/lib/firefox/plugins (symlink) => /etc/alternatives/firefox-flashplugin
/etc/alternatives/firefox-flashplugin (symlink) => /usr/lib/adobe-flashplugin/libflashplayer.so

This is true provided the flash-plugin has been installed system-wide, i.e. for all users, using Synaptic Package Administration (which in turn uses aptitude).

If a user installs the flash-plugin for his Firefox profile only, the file **libflashplayer.so **will be located somewhere inside the user's Firefox profile. Something like /home/username/.mozilla/firefox/blablabla.default/*plugins* or maybe /home/username/.mozilla/firefox/blablabla.default/*extensions*. Always installed Flash for all users.

HTH,
Karl

---

### Post by smalldog on 2011-04-25
I had similar problem; even though synaptic show that latest flashplugin had installed. Finally, it was solved by manually add the symbol link to mozilla plugin as below. Good luck

ln -s /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by chitowner2 on 2011-05-14
Thanks for the help guys. Now if I can just remember this stuff when Adobe pushes out yet another upgrade. :)

CT

---

### Post by macmike on 2011-05-16
I am trying to get Adobe Flash Player to work on my Ubuntu 11.04 install. I went to adobe to try and download it. I get a message - This link needs to be opened with an application. I don't know what application I need to open it. Any help appreciated.

macmike

---

