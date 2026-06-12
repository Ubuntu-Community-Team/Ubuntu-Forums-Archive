---
title: "unable to play youtube videos"
date: 2012-04-26
forum: Multimedia Software
---

### Post by rebeltaz on 2012-04-26
I have installed Ubuntu 11.10 with xfce 4.8 on my girlfriends computer and we cannot get youtube videos to play. 

I installed the following plugins:

DivX Web Player v1.4.0233
IcedTea Web Plugin v1.1.3
QuickTime Plugin v7.6.6 (Totem v3.0.1)
Shockwave Flash v11.2r202
VLC Multimedia Plugin (Totem v3.0.1)
Windows Media Player Plugin (Totem v3.0.1)

Can anyone tell me what I am missing? Thanks...

---

### Post by papibe on 2012-04-26
Hi rebeltaz.

You also need to install the 'Adobe Flash Plugin'.

Regards.

---

### Post by rebeltaz on 2012-04-26
> **papibe said:**
> Hi rebeltaz.

You also need to install the 'Adobe Flash Plugin'.

Regards.

When I went to Adobe and downloaded the plugin, Shockwave Flash is what it installed....

---

### Post by papibe on 2012-04-26
Install 'Adobe Flash Plugin' (not Shockwave, see [here]("http://www.askdavetaylor.com/the_difference_between_flash_and_shockwave.html")) from the Software Center.

Regards.

---

### Post by rebeltaz on 2012-04-27
> **papibe said:**
> Install 'Adobe Flash Plugin' (not Shockwave, see [here]("http://www.askdavetaylor.com/the_difference_between_flash_and_shockwave.html")) from the Software Center.

Regards.

Thanks, but when I went to Adobe the first time to install Flash, what it installed was Adobe Flash Plugin 10, which shows up as Shockwave Flash v11.2r202 under Firefox's Plugins. 

But just to be sure, I went into the Software Center, as you suggested, and noticed that there were two Flash packages - Adobe Flash Plugin 10 (which is the one that I had already installed and was marked as such) and Adobe Flash plugin (which was NOT installed). Just to rule out everything, I uninstalled the Adobe Flash Plugin 10 and installed Adobe Flash plugin instead. 

Still no youtube videos... :(

---

### Post by Meneer Jansen on 2012-04-27
I think that the latest Flash plugin for Linux is broken. And no way to downgrade to the version that worked until yesterday.

---

### Post by rebeltaz on 2012-04-27
> **Meneer Jansen said:**
> I think that the latest Flash plugin for Linux is broken. And no way to downgrade to the version that worked until yesterday.

So there IS a way to downgrade to the older version? How so?

---

### Post by Meneer Jansen on 2012-04-28
> **rebeltaz said:**
> So there IS a way to downgrade to the older version? How so?
In Synaptic select the dreaded package and click in the menu on: "Package > Force version (Ctrl+E)". This is not always enabled (i.e. grayed out).

---

### Post by Meneer Jansen on 2012-04-28
My workaround:

1. Delete '*libflashplugin.so*' files on my computer. (use *updatedb* and *locate*).
2. Use Synaptic to install the **old** version of Flash!! This will only work if you install the "Falsh plugin installer" instead of the "Adobe-flash plugin" package!! (Hat trick here).
3. Synaptic will delete Firefox. No sweat. I installed the latest version via the zip file from [Mozilla]("http://www.mozilla.org/nl/firefox/fx/") itself.
4. Start Firefox and youtube (= Flash) works again.
5. Start Chromium and it will wine that your Flash plugin is out of date and it won't work.

This way you'll end u with the Flash library (= *libflashplayer.so*) in
```

/usr/lib/flashplugin-installer/

```With various symlinks to it. This old libray is of version 10.0 r45 and it's size is 9.8 MB. The latest version at the time of writing is 11.2.202 and its size is 16.6 MB. So you bet yer sweet little hiny that the latest flash plugin HAS issues.

---

### Post by rebeltaz on 2012-04-28
Oh, this is a pain in the...


I tried both suggestions. 

updatebd and locate do not return any results for libflashplugin.so

When I tried "force version" it wanted to remove firefox and I said OK. When I clicked Apply it said something about an error and broken packages. I clicked Apply again for giggles and it did it's thing that time. I then reinstalled firefox and STILL no youtube!

Personally, I could not care less, but this is my girlfriends computer and she really likes watching old Selena videos on youtube. She's regretting letting me put Linux on her computer right about now! :confused:

---

### Post by cocaine2000 on 2012-07-16
Thanks Guys I had the same issue. I went to Adobe website and downloaded the libflashplayer.so
But I went to Ubuntu Software Center and installed the flash player plugin.
The file sizes were same for both.
It didnt work rightaway.
I rebooted and violla!!  I believe the cnn.com player is more difficult to play than youtube.
Hope that helps anybody..

---

