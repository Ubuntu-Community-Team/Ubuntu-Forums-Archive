---
title: "MPlayer Plugin for Mozilla Not Working"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by dbsoundman on 2008-01-04
I used to have the totem plugin, but it always started up in Mozilla Swiftfox, but never actually worked, as in the file never played. On my laptop, I have the MPlayer plugin and it works beautifully, so I went into synaptic on the desktop computer here and uninstalled the totem plugin and totem itself, and the totem xine, and installed the mplayer plugin. It was actually already installed, but I reinstalled it anyway. Now, even though in Swiftfox it says that mp3s should be opened with the MPlayer plugin, nothing happens; I get a blank page. How can I fix this? I saw some other users having problems with divx videos with this plugin, maybe I have a similar solution?

Thanks,
Dan

---

### Post by cor2y on 2008-01-05
check about:plugins (about: plugins without the space between : and p) in swiftfox and see if the mplayer plugin is listed b the browser if not you will have to create a symbolic link in the swiftfox plugin floder going to mozilla mplayer plugin files (usually found in /usr/lib/mozilla/plugins)
If the mplayer plugin is listed look adn see if other media plugins might be listed as well for example perhaps the vlc media plugin (if vlc is installed) or the totem plugins although you have said they have been removed.
If the totem/vlc plugins are there but it is uninstalled via synaptic then you will have to manually remove them from the swiftfox plugin folder.Then restart swiftfox.
If all these things are done but the error is still then its the way the website has set up media streaming its probably nonstandard.

---

### Post by wolfen69 on 2008-01-05
try
```
sudo apt-get install ubuntu-restricted-extras vlc mozilla-plugin-vlc
```
vlc is a great simple media player.

---

### Post by dbsoundman on 2008-01-05
Cory- I checked it out, and my about plug-ins says that Totem is still the default for mp-anything files, but there are no Totem files in the /usr/ file for Mozilla Plugins. What can I do?

I may try that VLC player, but I first want to get Totem all the way out before I dump in more junk.

-Dan

---

### Post by ubuntu-freak on 2008-01-06
Try removing swiftfox and deleting the folder. It still thinks it should be using totem. Then reinstall mozilla-mplayer (Works better than vlc) and java, flash etc.
 
There is a file you can delete to stop it doing that, then it recreates it but I can't remember what it is.
  
Then follow my guide here [http://ubuntuforums.org/showthread.php?t=658970&page=3](http://ubuntuforums.org/showthread.php?t=658970&page=3)
 
Works for me. 
 
Nathan

---

### Post by dbsoundman on 2008-01-06
Just to make sure I know what you're saying...

I should unintstall Swiftfox and delete the folder (which one?), then reinstall Swiftfox, then reinstall mplayer plugin, java, all that stuff. Sounds simple enough as long as I remember to save my bookmarks somewhere beforehand...

If I do this, I don't really remember where I can find the right other plugins like java and such for Swiftfox...is there some place where they are all listed? I seem to remember something like that...or maybe it was some search in synaptic. I forget.

-Dan

---

### Post by ubuntu-freak on 2008-01-06
It's a dirty way to do it I know.
 
I just can't remember which file you delete to stop firefox/swiftfox from thinking you want to use totem. 
 
I meant delete the swiftfox folder in /usr/lib but to be honest I think it's the hidden swiftfox folder in your home directory which has that file in it. Delete that folder and reinstall swiftfox. Backup your bookmarks first though.

Let me know how my settings for the mplayer plugin work.
 
Nathan 
 
P.S. If you ever need to install java 5 again (don't use 6 for now) just remember there are three packages you need to search for in synaptic:
 
Sun java plugin 
Sun java fonts 
Sun java jre

---

### Post by dbsoundman on 2008-01-07
That seems to have worked...I will get to your modifications and tweaks in a bit. First, I have a bit of a problem though. It seems that, somewhere in the process, I changed the default handling of MP3 files (via the content menu under preferences) to either download or open with a separate window of vlc media player. I need to switch it back to mplayer-plugin. How do I do that? The MP3 handling option has disappeared from that menu completely, and even after I reinstalled, the menu remains the same (even my bookmarks are still there!). But at least about:plugins shows the right setup now...

-Dan

---

### Post by ubuntu-freak on 2008-01-07
Do you mean m3u? That's how mp3's are handled with streaming.
 
I think if you add my settings mplayer will take over anyway.
 
You don't have mozilla-plugin-vlc installed do you? That needs removing. 
 
Do you have the win32codecs installed? If so then all you need to do now is paste those settings to your
mplayerplug-in.conf. 
 
You won't regret it:)
 
Nathan

---

### Post by dbsoundman on 2008-01-07
I got it all working. I don't know about Firefox itself, but I use Swiftfox and it actually has much better control over plugins and such, so I got it straightened out in this one. Firefox won't even open if I already have Swiftfox running, so I'm not too worried about Firefox's issues. It was actually a problem with streaming MP3s though and not M3U; like listening to an MP3 straight off a site instead of downloading it first and opening it with a separate program.

Anyway, I will do what you say with those settings, but what exactly will it achieve?

-Dan

---

### Post by ubuntu-freak on 2008-01-07
> **dbsoundman said:**
> Anyway, I will do what you say with those settings, but what exactly will it achieve?

-Dan

Virtually everything will stream and stream better. Even rm. 
 
Test it after on divx.com stage6 and bbc.co.uk rm tv clips. 
 
Nathan

---

### Post by mattsadd on 2008-01-20
This was easy enough for me to fix by opening up /opt/swiftox/plugins and deleting all the files beginning with "lib-totem...." then restarting Swiftfox.  I dunno why swiftfox installs into /opt instead of /usr, but I didn't see that mentioned above so I thought I would bring attention to it.

:)

---

### Post by ubuntu-freak on 2008-01-21
> **mattsadd said:**
> This was easy enough for me to fix by opening up /opt/swiftox/plugins and deleting all the files beginning with "lib-totem...." then restarting Swiftfox.  I dunno why swiftfox installs into /opt instead of /usr, but I didn't see that mentioned above so I thought I would bring attention to it.

:)


Did you uninstall totem-mozilla though? Cos when you update your system it will probably put the plugins back in their respective folders (when there is a plugin update at least). 

Nathan

---

