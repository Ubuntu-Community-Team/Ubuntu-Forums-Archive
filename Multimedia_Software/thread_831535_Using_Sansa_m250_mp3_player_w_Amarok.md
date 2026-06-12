---
title: "Using Sansa m250 mp3 player w/ Amarok"
date: 2008-06-16
forum: Multimedia Software
---

### Post by M4rotku on 2008-06-16
Hello,

I have been trying for a long time to get my Sansa mp3 player to work with Amarok first in 7.10 and now in 8.04.  It mounts and shows up on the desktop, but I can't see the music files when I look around for them.  I have successfully used this mp3 player with windows in the past, both XP and Vista.

When using Amarok, I give it the right commands to mount and eject the media player as far as I know:

> mount /media/Sansa\ m250

and

eject /media/Sansa\ m250

and nothing happens.


When I try to access the mp3 player using Rhythmbox, I recieve the following error:

> Location:
file:///media/Sansa m250/CONFIG/CONFIG.TCC

Error:
the MIME type of the file could not be identified.

I have no idea how to fix this.  Can anyone help?

Much thanks,
M4rotku

---

### Post by Majin_Buu on 2008-06-17
Hi!

I can't speak for the m250 series, since i'm on the 280 my self.

But my unit is automatically detected in any linux if I set the USB mode to MSC.

> Use under Linux: 
After upgrading the Firmware in Windows using the firmware updater downloaded from SanDisk, I set out to see if the device would work under Linux (Suse 10.1). With the USB mode on the player set to "MSC", the e280 appeared as an ~8GB storage drive, to which .mp3 files could be added. Music could also be added easily using Amarok (version 1.44). Artist and title tags used by Amarok were recognized by the e280. Currently, only MSC mode appears to be useful--when the USB mode on the e280 was set to "MTP" the device would not work with Amarok. The lack of MTP function is not critical--the device in MSC mode works very smoothly with Amarok, and I would still recommend this player to Linux/Amarok users.

---

### Post by Puptentacle on 2008-06-17
I've got an m250 and the fight I had a HORRIBLE fight with XP over it. Computers, where "Your experience may vary" takes on new meaning. 

As Majin_Buu says, set the player for MSC mode. Go into Settings, USB and cick "MSC" instead of "AutoDetect". That should do it.

---

### Post by Mattevt on 2008-06-17
> **M4rotku said:**
> Hello,

I have been trying for a long time to get my Sansa mp3 player to work with Amarok first in 7.10 and now in 8.04.  It mounts and shows up on the desktop, but I can't see the music files when I look around for them.  I have successfully used this mp3 player with windows in the past, both XP and Vista.

When using Amarok, I give it the right commands to mount and eject the media player as far as I know:



and nothing happens.


When I try to access the mp3 player using Rhythmbox, I recieve the following error:



I have no idea how to fix this.  Can anyone help?

Much thanks,
M4rotku

I have a Sansa View, and this page helped me out. Might want to give it a shot.

[http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html]("http://www.micahcarrick.com/05-21-2008/sansa-view-ubuntu.html")

---

### Post by M4rotku on 2008-06-17
I can't seem to find the correct navigation to the USB controls.  When I click on the Settings tab, the only options are:

> Hide Toolbar
Show Player Window
___________________
Configure Global Shortcuts
Configure Shortcuts
Configure Toolbars
Configure Amarok

When I click on "Configure Amarok" it brings up a menu that I added as the attached file.  I could not find anything about USB options on this menu.

Can anyone guide me to the USB options?

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-06-19
bump

---

### Post by M4rotku on 2008-06-21
bump

---

### Post by M4rotku on 2008-06-22
bump

---

### Post by h4v0k_d0m on 2008-11-18
> **M4rotku said:**
> I can't seem to find the correct navigation to the USB controls.  When I click on the Settings tab, the only options are:



When I click on "Configure Amarok" it brings up a menu that I added as the attached file.  I could not find anything about USB options on this menu.

Can anyone guide me to the USB options?

Much thanks,
M4rotku

Seriously?? The USB Settings are on your sansa itself hold it in your hand and scroll around to settings > system settings > USB Mode

It has nothing to do with amarok its on your player that you carry around.

---

### Post by OlehWho on 2010-08-23
I can use my Sansa M250 with Amarok with Ubuntu 9.10, the only problem is that I can only load one mp3 per time.  After I load one file I have to unplug my m250 and restart Amarok to get it to load,  
The m250 needs to be setup in MTP mode in order for Amarok to recognize it.
If I set it up in MSC mode then Ubuntu sees it,  but not Amarok and I cannot transfer files to it.  I think I have to edit the playlist manually  and drag and drop using File Manager in order to do it that way,

Does anyone have an idea how to make my m250 work with Amarok without having to reboot the m250 and Amarok?

Thanks

---

