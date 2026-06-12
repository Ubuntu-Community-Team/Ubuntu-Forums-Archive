---
title: "MythTV Screen Resolution Settings Issue"
date: 2009-04-22
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-04-22
Okay, I had another issue that eventually morphed in to this one, and I figured I should start a new thread.  Short version:  I upgraded to 8.10, it wasn't working well on my hardware so I migrated back to 8.04.  I now can't get the display resolution to the right setting.  It has all worked on this hardware before, so I know it's possible.

Hardware:

760+MHz Pentium CPU
524 MB RAM
ATI Radeon 9200 GPU (Yes, I know.  ATI = Bad)

The problem is, in a nutshell, that I cannot get the resolution of the GUI to display correctly on my TV.  I think that this will be easiest to explain with pictures.

When I start the remote frontend up (Note:  All other fronts and the front/back work fine) it looks like this:

[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/MythTV/MythTV1.png[/IMG]

Note that the settings say that the res is set to 1024x768.  
[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/MythTV/Mythtv3-1.png[/IMG]

The desktop settings are the same (in fact, changing one seems to automatically change the other.)  
[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/MythTV/MythTV2.png[/IMG]

If I exit Myth and restart it, it resizes to everything being perfect, but the appearance settings still say 1024x768, as if nothing has changed:

[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/MythTV/MythTV5.png[/IMG]


The only thing that I can think of that is different from my last installation that worked is that, in that case, I had the gnome desktop installed...I wasn't using it, though.  However, since it gave me different programs on the applications menu, I didn't know if maybe it was doing more behind the scenes.

---

### Post by AlecJ on 2009-04-23
turn off the separate video mode option?
That way the whole screen will be used.

---

### Post by Weidbrewer on 2009-04-23
Any other ideas?  That *did* get the resolution right...so the mission was *technically* accomplished:)...it just goes black locks up now when you hit play on a video.

I switched everything back to the way it was, and with resolutions for GUI, desktop and video set to 800x600, it displays correctly now...however, is still won't play videos.

Note:  Videos did play before changes.

---

### Post by nickrout on 2009-04-23
you need to report what errors the mythfrontend log gives when it "won't play videos"

---

### Post by Weidbrewer on 2009-04-23
Sorry.  Here is the chunk that pertains to (I believe) the last startup, run, and attempt to play a video:

```
Starting mythfrontend.real..
2009-04-23 20:01:52.731 New DB connection, total: 2
2009-04-23 20:01:52.734 Connected to database 'mythtv' at host: 192.168.1.47
2009-04-23 20:01:52.745 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-04-23 20:01:52.746 Enabled verbose msgs:  important general
2009-04-23 20:01:53.185 Unable to parse themeinfo.xml for glass-wide
2009-04-23 20:01:53.186 The theme (glass-wide) is missing a themeinfo.xml file
2009-04-23 20:01:53.923 Unable to parse themeinfo.xml for glass-wide
2009-04-23 20:01:53.923 The theme (glass-wide) is missing a themeinfo.xml file
2009-04-23 20:01:54.959 Primary screen 0.
2009-04-23 20:01:54.961 Using screen 0, 800x600 at 0,0
2009-04-23 20:01:54.973 Switching to square mode (Mythbuntu-8.04)
2009-04-23 20:01:55.519 Using the Qt painter
2009-04-23 20:01:55.526 JoystickMenuClient Error: Joystick disabled - Failed to read /home/weidman/.mythtv/joystickmenurc
2009-04-23 20:01:55.527 lirc init success using configuration file: /home/weidman/.mythtv/lircrc
2009-04-23 20:01:57.257 Specified base font 'medium' does not exist for font clock
2009-04-23 20:01:57.257 Specified base font 'medium' does not exist for font small
2009-04-23 20:01:57.258 Specified base font 'medium' does not exist for font medium
2009-04-23 20:01:57.259 Specified base font 'medium' does not exist for font large
2009-04-23 20:01:57.289 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-04-23 20:01:57.713 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-04-23 20:01:58.363 Registering Internal as a media playback plugin.
2009-04-23 20:01:58.775 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-04-23 20:01:59.125 Failed to run 'cdrecord --scanbus'
2009-04-23 20:01:59.197 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-04-23 20:01:59.216 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-04-23 20:01:59.503 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.40:5060 NAT address 192.168.1.40
SIP: Cannot register; proxy, username or password not set
2009-04-23 20:03:19.352 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/video-ui.xml
2009-04-23 20:03:19.355 Unable to find image file: /usr/share/mythtv/themes/Mythbuntu-8.04/vidgallerybackg.png
2009-04-23 20:03:19.355 UIImageType::LoadImage() - Cannot find image: vidgallerybackg.png
Container: background already exists
2009-04-23 20:03:19.393 Failed to parse a container. Ignoring.
2009-04-23 20:03:20.216 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-04-23 20:04:04.940 Loading from: /usr/share/mythtv/themes/default/appear-ui.xml
2009-04-23 20:04:28.848 Connecting to backend server: 192.168.1.47:6543 (try 1 of 5)
2009-04-23 20:04:28.852 Using protocol version 40
2009-04-23 20:04:28.881 Received a remote 'Clear Cache' request
2009-04-23 20:06:15.350 Received a remote 'Clear Cache' request
method return sender=:1.5 -> dest=:1.16 reply_serial=2
   int32 0
Destroying SipFsm object 
mythfrontend.real: Fatal IO error: client killed
```



Further note:  To make sure that it was not an issue with the remote back-up, I tested two of the other frontends.  They are working normally.

---

### Post by Weidbrewer on 2009-04-25
...Wow.  Did I screw it up that badly?

---

### Post by Weidbrewer on 2009-05-01
Well...another wipe and reinstall seemed to do the trick.

---

