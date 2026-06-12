---
title: "How do I install, activate and use the MythTV plugin in Totem?"
date: 2008-05-05
forum: Mythbuntu
---

### Post by nattugglan on 2008-05-05
Hi.

I'm running Ubuntu 8.04 on my laptop. MythTV frontend works fine, but I cannot get the MythTV plugin in Totem to work..

There is no MythTV plugin listed in Totem -> Edit -> Plugins...

But there is info in gconf-editor. I've tried to add the master backend IP-address in the address field in gconf-editor (apps -> totem -> plugins -> totem_mythtv). I've also tried to add the password, and adding a new key called active (boolean set to true), but nothing works.. Not even after rebooting.

MythTV does not appear in the Playlist-dropdown menu in Totem, and MythTV never appears in the list of plugins..

I've searched for a plugin in Synaptic, but cannot find a plugin to install.

:. nattugglan

---

### Post by superm1 on 2008-05-05
Click this link to install the plugin:

[apt://totem-plugins-extra](apt://totem-plugins-extra)

---

### Post by tgm4883 on 2008-05-05
Bust open synaptic and look for totem.   There is an extra plugins package that you need to install (maybe called totem-extra-plugins) this will install the myth plugin.  You already added the necessary stuff in gconf-editor, then activate the plugin in totem (via the plugins list), now in the right panel of totem (you may have to restart totem after activating the plugin), you should be able to select mythtv from the drop down menu in the top.  Then select refresh and it should give you a list of shows

---

### Post by nattugglan on 2008-05-07
Thank you both!

The package called totem-plugins-extra was what needed to be installed. The reason I didn't find it was that "MythTV" isn't mentioned, and therefore not searchable in the package info.

I have quite a lot of recordings in MythTV (4 TB), so the list takes ages to appear. For some reason only around 1 KiB/s bandwidth is used when fetching the list..

I've installed all the packages that Totem informs about when it can't play the recordings, but I've gotten no video so far..
Installed the last one a while ago, gstreamer fluendo, but now Totem doesn't get the list recordings from MythTV.

Will try again later.

:. nattugglan

---

### Post by NeoFax on 2008-11-13
This plugin is not available on Intrepid.

---

### Post by ahood on 2008-12-17
The myth plugin is unavailable for me too in Intrepid, even after installing the totem-plugin-extras. The plugin seems to have been removed. The links below has more information.

[https://launchpad.net/ubuntu/intrepid/+source/totem/2.23.4-0ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/totem/2.23.4-0ubuntu1))
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/278748](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/278748)

---

### Post by axelsvag on 2009-06-14
If you use the suggestion in the above I can get the mythtv plugin back on totem but when I use gconf-editor and try to change the ipadress and mythtv password  and.. there is just one option left " activate " so though I can get the plugin to work I can not connect to the backend server due to the lack of options.

---

