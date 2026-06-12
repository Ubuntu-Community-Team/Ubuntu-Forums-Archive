---
title: "Google Chrome still states Flash plugin is out of date"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by BentFX on 2011-05-18
Ubuntu 10.04

For some time Google Chrome has identified the flash plugin as being out of date. The fix is to add "--allow-outdated-plugins" to the Chrome command line.

My question is... Yesterday I got the newest Chrome, and today I got the newest Flash via Update Manager. Chrome still complains. Is this an issue with Chrome, or is my Chrome not seeing the most recent plugin?

Does your Chrome complain?

Thanks,


Skip

---

### Post by mikewhatever on 2011-05-18
Simple, what you get via the update manager is not the flash plugin that Google Chrome uses. The first is **/usr/lib/adobe-flashplugin/libflashplayer.so**, while GC has its own, **/opt/google/chrome/libgcflashplayer.so**.
To check what version is in GC, type [noparse]'about:plugins'[/noparse] in its URL bar.

---

### Post by BentFX on 2011-05-18
**/usr/lib/adobe-flashplugin/libflashplayer.so** doesn't exist on my system. Neither the folder or the file.

**/opt/google/chrome/libgcflashplayer.so** file doesn't exist.

I did sort out my issue though. There was an old **libflashplayer.so** in **/usr/lib/browser-plugins/** that Chrome was finding, rather than the more recent version: **/var/lib/flashplugin-installer/npwrapper.libflashplayer.so**

That isn't the internal player you spoke of, but it is V10.3 r181, which is the most recent, and Chrome don't complain.

---

### Post by lovinglinux on 2011-05-18
> **BentFX said:**
> **/usr/lib/adobe-flashplugin/libflashplayer.so** doesn't exist on my system. Neither the folder or the file.

**/opt/google/chrome/libgcflashplayer.so** file doesn't exist.

I did sort out my issue though. There was an old **libflashplayer.so** in **/usr/lib/browser-plugins/** that Chrome was finding, rather than the more recent version: **/var/lib/flashplugin-installer/npwrapper.libflashplayer.so**

That isn't the internal player you spoke of, but it is V10.3 r181, which is the most recent, and Chrome don't complain.

You are using a 64bit system, so Chrome doesn't have that plugin mentioned by mikewhatever.

Now you are using the 32bit Adobe flash plugin provided by the repositories, which runs with a 64bit wrapper.

You might want to try the 64bit preview plugin.

If you still have Firefox installed, you can use [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") to install the 64bit plugin. The plugin installed by Flash-Aid will be recognized by Chrome as well.

---

### Post by freedomAboveAll on 2011-12-15
Hello,

I am running 64-bit system.  Latest Chrome update (version 16.00x) now complains of Flash out of date.   Chrome allowed me to download and install Flash 11 from Adobe Site.  

```
chrome://plugins/

```showed that Chrome still had the old version of Flash in its plugins directory and it was seeing that as well as the new  Flash 11.

so a 

```
sudo rm /opt/google/chrome/plugins/libflashplayer.so

```to remove the old Flash fixed me right up!


Hope this helps someone!

---

### Post by lovinglinux on 2011-12-15
> **freedomAboveAll said:**
> Hello,

I am running 64-bit system.  Latest Chrome update (version 16.00x) now complains of Flash out of date.   Chrome allowed me to download and install Flash 11 from Adobe Site.  

```
chrome://plugins/

```showed that Chrome still had the old version of Flash in its plugins directory and it was seeing that as well as the new  Flash 11.

so a 

```
sudo rm /opt/google/chrome/plugins/libflashplayer.so

```to remove the old Flash fixed me right up!


Hope this helps someone!

You do not need to delete any files from your installation. Type *[noparse]about:plugins[/noparse]* in the address bar and hit enter, then click the *Details*, then disable the version you don't want. Additionally, the path you provided is not the default chrome installation. The plugin installed with Chrome is *libgcflashplayer.so*. I don't know how you got that *libflashplayer.so* on the chrome opt folder. If you had installed it from the repositories, it would be in another place. So I presume you have installed that file manually, which is not a common thing.

---

