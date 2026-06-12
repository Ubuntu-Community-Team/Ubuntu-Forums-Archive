---
title: "adobe flash broken in firefox 3.6.6 32-bit"
date: 2010-07-18
forum: Multimedia Software
---

### Post by transporter_ii on 2010-07-18
I've spent the better part of a day off working on this. I can't pinpoint the problem, either.

I've removed *every* flash package in synaptic and installed:

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53 

I've rebooted, removed, purged, installed, reinstalled. rebooted. rebooted.

I've tried flash-aid. I've searched the forum.

If I remove ALL flash, youtube correctly says the plugin isn't installed.

If I install adobe-flahplugin, I get a black box where the video should be.

The only thing that worked is installing Google Chrome...where flash worked on the first freaking run. But I'm really partial to firefox and this is kind of really POing me.

What I would like to know is if Firefox 3.6.6 and Flash 10.1 r53 WORK FOR ANYONE or if I'm just wasting my time???

---

### Post by lovinglinux on 2010-07-18
If you tried FLASH-AID prior to version 1.0.7, then you might have experienced a bug in my extension that only affects 32bit users. [Get version 1.0.7 from my site](http://flash-aid-extension.blogspot.com) and run it again.

After that you shouldn't get those warnings. Don't forget that only installing FLASH-AID in Firefox doesn't fix flash. You need to click the FLASH-AID button in the status bar and select the install option to install flash. Nevertheless, depending on the version of the extension, it will prompt for installation automatically as soon as you update the extension and restart the browser.

---

### Post by transporter_ii on 2010-07-31
Opened Firefox a minute ago and it updated to Flash-aid 1.0.10 before I noticed this post from you. Ran it from install and restarted Firefox, which is now version 3.6.8.

I still get a black box where there should be flash.

I'm a firefox fan, but it has turned into a steaming pile for me. Google Chrome is running circles around it for me. Everything else on my system seems to be working fine, so I have to assume that it is Firefox...and that is a shame considering how intergrated it is into Ubuntu. You would think if there was one program that would run good on Ubuntu, it would be Firefox.

---

### Post by ratcheer on 2010-07-31
In Firefox, do Tools >> AddOns >> Plugins. Does "Shockwave Flash" show as one of the plugins?

Tim

---

### Post by lovinglinux on 2010-07-31
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```
echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
```

---

### Post by linux18 on 2010-07-31
+1 for flash aid

---

### Post by transporter_ii on 2010-07-31
Ok, after weeks of no flash in Firefox, I finally got it working today. Everything was removed and reinstalled from the command line, as well as installed directly from the adobe package and it still wouldn't work. What exactly the problem or the fix was, I don't know (and Firefox still seems too sluggish compared to Chrome), but here is what I did:

I ran Flash Aid and restarted Firefox several times, but it still didn't work (but Flash-aid 1.0.10 may have done something? I sure can't rule it out). 

I shut down Firefox and I went to my home folder, setting view to show hidden files. I went to .mozilla and renamed profiles.ini to profiles.bak and I started Firefox. Firefox generated a new profile on startup and Flash worked the first try after that.

I had to copy my bookmark backups to the new profile's backup directory. From there I did a restore and it put my bookmarks back in Firefox.

I had to reinstall the few add-ons I use, and everything seems fairly normal...except for the fact that Firefox still seems too slow (but the rest of my system runs fine like it always has).

I've got a media server and a bunch of other partitions with other operating systems on them, as well as a virtual machine running out Ubuntu from time to time, or I would have done a clean install of 10.04 LTS when everything went south a few weeks ago.

As it is, it is working good enough that I can live with it for a while, because I don't have time to reinstall everything on this system just because one program seems slow.

Thanks guys,

---

### Post by lovinglinux on 2010-07-31
> **transporter_ii said:**
> I ran Flash Aid and restarted Firefox several times, but it still didn't work (but Flash-aid 1.0.10 may have done something? I sure can't rule it out). 

I'm suspicious, but FLASH-AID 10.0.10 probably fixed it. I have released this version recently to fix an issue on some machines, where flash was just uninstalled and not installed back. Most likely that this is your case.

> **transporter_ii said:**
> I shut down Firefox and I went to my home folder, setting view to show hidden files. I went to .mozilla and renamed profiles.ini to profiles.bak and I started Firefox. Firefox generated a new profile on startup and Flash worked the first try after that.

I had to copy my bookmark backups to the new profile's backup directory. From there I did a restore and it put my bookmarks back in Firefox.

For future reference, see [Fixing a problematic or corrupted profile]("http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html").

> **transporter_ii said:**
> I've got a media server and a bunch of other partitions with other operating systems on them, as well as a virtual machine running out Ubuntu from time to time, or I would have done a clean install of 10.04 LTS when everything went south a few weeks ago.

As it is, it is working good enough that I can live with it for a while, because I don't have time to reinstall everything on this system just because one program seems slow.

Thanks guys,

See my Firefox optimization tutorials: [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

I would recommend start with [Database Optimization]("http://firefox-tutorials.blogspot.com/2010/05/database-optimization.html") tutorial and checking if you have the proper graphics driver installed.

---

