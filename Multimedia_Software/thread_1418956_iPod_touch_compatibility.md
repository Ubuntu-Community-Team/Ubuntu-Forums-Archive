---
title: "iPod touch compatibility"
date: 2010-03-01
forum: Multimedia Software
---

### Post by elreteipos on 2010-03-01
I've read that Ubuntu will soon support the iPhone and iPod touch. But...

[list][*]Will it sync a music library like iTunes?
[*]Does it support podcasts?
[*]Does it still allow me to use the iTunes Store?
[*]Can it back up my apps and app-related data?
[*]Can it do all this without jailbreaking my iPod touch?
[*]Is this feature immune to Apple's ongoing effort to block Linux compatibility?
[/list]

---

### Post by ElSlunko on 2010-03-01
I don't think it will support anything iTunes store related but everything else should work.

Just did a quick test with my g/f's ipod Touch & it transfers music to and from the device. I'll get back with more testing to see if podcasts & syncing work. 

The device is not jailbroken, btw.

---

### Post by elreteipos on 2010-03-02
What about album art and lyrics?

---

### Post by FunkyM on 2010-04-02
> **elreteipos said:**
> I've read that Ubuntu will soon support the iPhone and iPod touch. But...

[list][*]**Will it sync a music library like iTunes?** - Yes, it already does with any media player using the libgpod library.
[*]**Does it support podcasts?** - Partly, take it like music within the "podcast" genre.
[*]**Does it still allow me to use the iTunes Store?** - Use yes, however purchased tracks with DRM won't be synced nor you can transfer such purchased tracks onto the device.
[*]**Can it back up my apps and app-related data?** - Yes, and it allows much more like full native backups (same as iTunes) and manging the apps on the device.
[*]**Can it do all this without jailbreaking my iPod touch?** - Yes. All without jailbreaking a device.
[*]**Is this feature immune to Apple's ongoing effort to block Linux compatibility?** - The work is based on the library called libimobiledevice which is in development since late 2007. Until now, that library has never stopped working with newer firmware releases while a lot of jailbreaking tools and other custom tools on Windows and Mac OS X always broke. Even further, it seems the library will directly support the iPad and iPhone 4G. The reason for this is that it talks to the device in a non-hackish clean native way; like iTunes does.
[/list]

For even more info of what it can do checkout [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by elreteipos on 2010-04-02
Sounds like a lot of fantastic work has been done to support the Touch lately! I really need smooth podcast sync though, so I'm afraid I'll have to wait a couple more months until that gets smoothened out.

---

### Post by temporos on 2010-04-06
> **FunkyM said:**
> 
[LIST]
[*]**Will it sync a music library like iTunes?** - Yes, it already does with any media player using the libgpod library.
[/LIST]

Is this library included with Ubuntu 9.10?  How can I tell (sorry, relative newbie here)?

> **FunkyM said:**
> 

[LIST]
[*]**Does it still allow me to use the iTunes Store?** - Use yes, however purchased tracks with DRM won't be synced nor you can transfer such purchased tracks onto the device.
[/LIST]

I looked in Rhythmbox, and I can't find anything that mentions the iTunes Store.  How do I access it and purchase music through it?

> **FunkyM said:**
> 

[LIST]
[*]**Can it back up my apps and app-related data?** - Yes, and it allows much more like full native backups (same as iTunes) and manging the apps on the device.
[/LIST]

Again, I can't find this feature in Rhythmbox...  Is it a hidden option?

Basically, if I open Rhythmbox (the music player included with Ubuntu 9.10 Karmic) and plug in my iTouch, all these options you mentioned should become visible, right?

---

