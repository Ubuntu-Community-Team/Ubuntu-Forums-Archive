---
title: "ITunes &amp; IPhone on ubuntu"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Gregorybekkers on 2010-04-02
Hi,

I got an iphone...
now i need to install Itunes.
I tried to install itunes on Wine but it isn't working...

anyone got an idea?

---

### Post by Chronon on 2010-04-02
One way is to install Windows inside of VirtualBox and install iTunes inside of that.

Check here:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by sarel29 on 2010-04-02
I'm having issues with my 5th generation iPod nano; no linux applications seem to be able to sync with it (or rather they do, but then the iPod doesn't see the music as music - it is classified as 'other').  So I decided to download iTunes and run it through wine, but when I try to open it I get the following error message:

> Apple Application Support was not found.

Apple Application Support is required to run iTunesHelper. Please uninstall iTunes, then install iTunes again.

Error 2

I tried reinstalling iTunes but I still get the same error message.  Does iTunes just not work with wine? I've seen quite a few threads where people seem to be running iTunes through VirtualBox but as I havn't used Windows for about 6 years, I don't have a copy I can install in VirtualBox.

Does anyone have any ideas?  It feels like I'm getting so close, and yet I'm still so far :(

Thanks!

---

### Post by Chronon on 2010-04-02
I don't think iTunes will run under WINE.  More information here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

There's quite a long discussion about 5th generation Nanos here:
[http://ubuntuforums.org/showthread.php?t=1267180](http://ubuntuforums.org/showthread.php?t=1267180)

You might find some useful information there.  I honestly haven't read very much of that topic since I don't use any iPods.

---

### Post by DexterP17 on 2010-04-02
You don't need to install itunes onto your computer because Ubuntu will have a store called Ubuntu one music store for you to purchase music and sync to your ipod so don't worry if you can't just install Ubuntu 10.04 to get the store. be careful as the the release is still in beta for now.

---

### Post by Gregorybekkers on 2010-04-04
Yeah but i'd like to have i tunes on ubuntu and not virtual under windows... cause it has too connect directly to  my usb port.

and for Iphone u need Itunes to sync your stuff and update it.

---

### Post by stderr on 2010-04-04
AFAIK, iTunes under Ubuntu is not possible. I have had an iPhone for years, and I have my laptop set to dual-boot Winblows/Linux so I can sync with iTunes. 

It is possible, as others have mentioned, to install Winblows under Virtualbox or similar and install iTunes onto that. As long as you download the proprietary (but still free £-wise) Virtualbox from its website, that comes with full USB support, and you should have no problems.

---

### Post by AlanR8 on 2010-04-04
Have synchronised Ipods and Itouches using the Virtualbox route and it works just fine.

However, as stated above, Lucid and Rhythmbox just works with the Touch and Phone

---

### Post by ChillMonkey on 2010-04-07
> **Gregorybekkers said:**
> and for Iphone u need Itunes to sync your stuff and update it.

Not exactly: [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

But I have been unable to test it, since I don't have an iPhone

---

