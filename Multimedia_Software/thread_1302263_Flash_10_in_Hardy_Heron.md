---
title: "Flash 10 in Hardy Heron?"
date: 2009-10-26
forum: Multimedia Software
---

### Post by BlueNoteExpress on 2009-10-26
I've been unsuccessfully trying to get Flash 10 to work in Hardy Heron and was wondering if anyone can tell me what I'm doing wrong.

I've been trying to install Flash 10 using the .deb file I obtained from Adobe's site as instructed by [this site](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html).

However, after Flash 10 is supposedly installed and I try to use it in Firefox, I seem to have no flash players available at all.  Typing "about:plugins" in the address bar shows no Flash plugins available.  Then, when I browse to a site that uses Flash, I'm prompted to install the Flash plugin.  A "Plugin Finder Service" window pops up, and lets me choose one of three Flash plugins to install.  My choices are as follows:

1.  Adobe Flash Player (installer)
2.  Swfdec player for Adobe/Macromedia Flash
3.  Gnash SWF Player

So far, I've been choosing the first option (Adobe Flash Player (installer)), but all that seems to do is re-install Flash 9.

What gives?  Does anyone know how I can get Flash 10 working?

Thanks,
Nick

---

### Post by HappyFeet on 2009-10-26
Uninstall any flash or whatever you may have installed. Then go [here]("http://get.adobe.com/flashplayer/") and download the .tar.gz flash file. Then just right click and **extract here**. Then put the resulting libflashplayer.so file into /usr/lib/mozilla/plugins or /home/username/.mozilla/plugins.  

.mozilla is a hidden directory in your home folder. Do Ctrl-H to show it. You will also need to make the plugins folder. Then restart firefox.

---

### Post by kostkon on 2009-10-26
Flash 10 is offered by the *Partner* repo so you should be able to install it even in 8.04. The name of the package is:
```
adobe-flashplugin
```

Search for it in Synaptic and install it. Before doing that, it would be good to remove any other version/implementation of Flash that you have installed.

---

### Post by RichardLinx on 2009-10-26
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
Restart Firefox.

If that doesn't fix it mark firefox for complete removal from synaptic and reinstall. That tends to fix it for a lot of people. (It's how I fixed it for 8.04 a long time ago).

If it still doesn't work then completely remove and reinstall flash. Remove via synaptic and download again from the adobe site.

Still not working? Install Opera 10: [http://www.opera.com/browser/](http://www.opera.com/browser/)

---

### Post by BlueNoteExpress on 2009-10-26
Other than replacing Firefox with Opera (which I really don't want to do), I've tried all of these suggestions, and I still can't get Flash 10 working.

Any other ideas?  This is beyond frustrating!

---

### Post by BlueNoteExpress on 2009-10-27
It seems that I can install the Flash 10 plugin, at least according to Ubuntu.  However, I can't seem to make Firefox see that the Flash 10 plugin is there.  Flash content only seems to work if I install the Flash 9 plugin (flashplugin-nonfree).  How can I make Firefox see that the Flash 10 plugin (adobe-flashplugin) is there?

---

### Post by RichardLinx on 2009-10-27
Try:
```
sudo apt-get remove --purge firefox
```
Then **completely** remove flash via Synaptic.
Then run:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
Then restart.
Reinstall Firefox:
```
sudo apt-get install firefox
```
Then visit the Adobe website and get the plugin:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Make sure you select the .deb for Ubuntu 8.04+
Close Firefox, install the plugin. Launch Firefox and see if it's working.

Note: If you have any bookmarks you might want to save them before removing firefox.

Additionally, you could try:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install flash, but it will install a few other things as well. (Like multimedia codecs)

---

### Post by BlueNoteExpress on 2009-10-27
A search for "firefox" in Synaptic reveals that I have packages named both "firefox" and "firefox-3.0" installed?  Do I need to remove both of these?

> **RichardLinx said:**
> Try:
```
sudo apt-get remove --purge firefox
```
Then **completely** remove flash via Synaptic.
Then run:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
Then restart.
Reinstall Firefox:
```
sudo apt-get install firefox
```
Then visit the Adobe website and get the plugin:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Make sure you select the .deb for Ubuntu 8.04+
Close Firefox, install the plugin. Launch Firefox and see if it's working.

Note: If you have any bookmarks you might want to save them before removing firefox.

Additionally, you could try:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install flash, but it will install a few other things as well. (Like multimedia codecs)

---

### Post by RichardLinx on 2009-10-27
Select firefox-3.0 for complete removal. It should pull all the associated dependancies.

---

### Post by BlueNoteExpress on 2009-10-27
> **RichardLinx said:**
> Select firefox-3.0 for complete removal. It should pull all the associated dependancies.

Well, I did that and everything else you suggested, but it still didn't work.

However, in the mean time, I started poking around on my own.  I looked at the properties for the adobe-flashplugin package in synaptic and started looking at the files/folders listed on the "Installed Files" tab.  While looking at the flash stuff in some of those locations, I noticed that most of the files in those locations that dealt with flash were broken links to other locations.  Eventually, I ended up creating the directory /usr/lib/flashplugin-nonfree by hand and copying libflashplayer.so into it.

After doing that, I restarted the computer, and now the Flash 10 plugin works in Firefox.

It seems strange that I should have to copy that .so file into that particular directory to get it to work, but that got it working when nothing else did.

With all of that said, does anyone see any problems with what I did?

---

### Post by RichardLinx on 2009-10-27
That's strange, I guess it wasn't unpacking properly for some reason. Nice work on finding a solution your self. :)

---

