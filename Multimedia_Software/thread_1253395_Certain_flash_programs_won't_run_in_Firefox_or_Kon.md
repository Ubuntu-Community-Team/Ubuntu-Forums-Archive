---
title: "Certain flash programs won't run in Firefox or Konqueror"
date: 2009-08-30
forum: Multimedia Software
---

### Post by sandman887 on 2009-08-30
I have 9.04 installed. I just got a new 1.5 TB sata hard drive so I reinstalled this new just a few days ago. I had it installed previously on an IDE hard drive. I was able to load and listen to music on playlist.com like normal on the previous installation which was also 9.04.

But now that I installed it on this new hard drive (which I have no clue why it would matter), I can load those advertisements which are either flash or shockwave files, but I can't load that music player on playlist.com.

I can watch videos on youtube, but whenver I went to playlist.com, the plugin part where the music player should be said I didn't have the latest version of Adobe flash. I have reinstalled it 3 times, so I do have it installed. I have also apt-get installed every plugin I could find for firefox and konqueror, and it has all been in vain.

I don't know what to do now. 

I appreciate any help.

---

### Post by hal10000 on 2009-08-30
I have flash version installed with [COLOR="Red"]sudo apt-get install flshplugin-installer[/COLOR] and it works perfectly on playlist.com and any other sites. I have firefox 3.5.2, but i remember that it also worked in older versions of firefox.
Sometimes it happens, that flash disappears in firefox, but usually after restarting firefox it works again.

---

### Post by sandman887 on 2009-09-01
Yeah I tried apt-get install flashplugin-installer several times and it just won't work. I really can't figure this out. This is strange. Here is a screenshot to prove it.

[IMG]http://blueboardsoftware.com/images/Screenshot-9.png[/IMG]

---

### Post by sandman887 on 2009-09-01
also, it's not just playlist.com, I used to be able to watch videos on youtube great, even on this installation. But I must have done something to mess up flash. I even uninstalled firefox and reinstalled it twice. 

I'm beginning to think it is unfixable.

---

### Post by hal10000 on 2009-09-01
You can look in firefox to see if it recognizes flash: Go to "Tools"--->"Add-ons" and look for "Shockwave Flash" in the plugin list. Since you installed Version 10.0.32 there would have to appear Somewhere in the plugin-list "Shockwave Flash 10.0 r32".
You said that you have installed every plugin you could find, and therefor it may be, that you have installed another flashplayer-plugin like swfdec or gnash e.g., but these plugins are usually old versions and may lead to a wrong entry in your plugin list.
If you find a wrong version, try
[COLOR="Red"]sudo update-alternatives --config firefox-flashplugin[/COLOR] and type in the correct number from what you get offered.
It is also a good idea to remove any other flash plugin but flashplugin-installer (try it with synaptic package manager).

---

### Post by sandman887 on 2009-09-01
You're awesome. It WAS because I had swfdec-mozilla installed. I looked in Tools > Addons etc. And found Shockwave flash 9.0 r9999. When I apt-get removed swfdec-mozilla, and went back to the Tools place where you told me to look, it showed the 10.0.32. Weird. But it works now, so thanks!

---

