---
title: "opera and flash?"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by darkos on 2007-04-07
Well i wanted to have some flash support on my opera browser and i followed these instructions located on the opera site:

1.Download the plug-in from Adobe's Web site.
2.Follow the instructions on the download page. The installer will offer to install the plug-in, and for Opera you should choose /usr/lib/opera as the installation path.
3.Restart Opera.
4.Verify that the plug-in is working by going to Adobe's test page.

I downloaded install_flash_player_9_linux.tar.gz from the adobe site, started the installation and woooooooop
```

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla):  /usr/lib/opera
dir= /usr/lib/opera

ERROR: Opera is not supported.

```

Then i read this one [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Install_OpenMotif_in_Opera]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Install_OpenMotif_in_Opera")
I download openmotif, right click on the file, click on **Kubuntu Package Menu** and **Install Package**. D'oh what do i get??
```

dpkg: dependency problems prevent configuration of openmotif:
 openmotif depends on xlib6g (>= 3.3.6-10); however:
  Package xlib6g is not installed.
dpkg: error processing openmotif (--install):
 dependency problems - leaving unconfigured

```
So i search for the xlib6g package which is probably nowhere available...
Whats now?

---

### Post by dreadlord_chris on 2007-04-07
so I take it you don't have firefox installed huh?

This should work(around) for you.
```

sudo mkdir /usr/lib/mozilla
sudo mkdir /usr/lib/mozilla/plugins

```

then re-run the flash installer and enter /usr/lib/mozilla when asked for an install dir...

---

### Post by darkos on 2007-04-07
yeah but this will install the plugin in the mozilla/plugins dir, we want it in the opera dir though... I must say you confused me. :confused:

---

### Post by RomeReactor on 2007-04-07
Hi. To install flash in Opera, go in the flash directory that you downloaded from Adobe, and copy **libflashplayer.so** (should wiegh in at about 6.7 MB); now open a terminal and write

```
gksudo nautilus
```

That will bring up Nautilus with root properties, so navigate to **/usr/lib/opera/plugins** and paste the **libflashplayer.so** there. Close Nautilus and the terminal. Now open Opera and go to "Tools-->Preferences-->Advanced-->Content-->Plug-in options" and make sure the plugin path only reads **/usr/lib/opera/plugins**; close Opera and open it again and go to a page that requires flash to see if it's working now.

---

### Post by willmacleod on 2007-04-07
Or You could just switch to firefox and its beautiful plugin installer:)

---

### Post by darkos on 2007-04-08
wohoooo its workin :guitar: 
nice idea over there!!
well if i wanted to use firefox i'd just install it :-P you cant compare firefox with opera...thx for the idea though!

---

