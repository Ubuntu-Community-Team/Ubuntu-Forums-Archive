---
title: "Banshee Music Player - The Moving Target"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-03-14
I'll have to say...

Of all the challenges I've run across in Natty, Banshee has gotta be the longest running one.

I'm developing a suitable Conky script for Natty, but every time I get the Banshee code pinned down, the devs change things.  :D

2 days ago, I could call Banshee functions with either 'banshee' or 'banshee-1' and/or a combination of both.

Yesterday, 'banshee' wasn't working.  CLI indicated 'banshee' wasn't installed, so I switched my Conky code to use 'banshee-1'.

Today, there was a Banshee Update, now 'banshee-1' doesn't work.  I have to use 'banshee' again.

Example:

```

vindsl@Zuul:~$ banshee-1
The program 'banshee-1' is currently not installed.  You can install it by typing:
sudo apt-get install banshee
vindsl@Zuul:~$ banshee-1 --help
The program 'banshee-1' is currently not installed.  You can install it by typing:
sudo apt-get install banshee
vindsl@Zuul:~$ banshee --help
Usage: banshee-1 [options...] [files|URIs...]

Help Options

  --help                   Show this help
  --help-playback          Show options for controlling playback
  --help-query-track       Show options for querying the playing track
  --help-query-player      Show options for querying the playing engine
  --help-ui                Show options for the user interface
  --help-debug             Show options for developers and debugging
  --help-all               Show all option groups
  --version                Show version information
vindsl@Zuul:~$

```

I suppose it's an aliasing problem, but I wish they would settle on one name or another...  :)

As an aside, after today's update, Banshee won't start from the Unity Launcher - only from CLI. LoL!

Of, the joys of Alpha!

---

### Post by cariboo on 2011-03-14
On my system banshee is aliased to banshee-1, both work for me. For your purposes, would using the full path to banshee make a difference eg: /usr/bin/banshee?

---

### Post by gnomeuser on 2011-03-14
The banshee-1 name dates back to when Banshee was working towards 1.0 and it needed to be parallel installable. We have just committed the required changes to go back to plain banshee.

---

### Post by VinDSL on 2011-03-15
Thanks, for the replies!

Banshee remains a mystery, and a moving target.

I just got home -- cranked up Natty -- and did an update.

I tried to start Banshee using the Unity Launcher... nothing, but a pulsing icon.

Then, I went into 'Applications' and clicked the Banshee icon there... nothing.

Then, I went to CLI...  'banshee' did the trick, but...

Here's the dialog in CLI:

```

vindsl@Zuul:~$ banshee
[Info  23:21:41.713] Running Banshee 1.9.5: [Ubuntu Natty (development branch) efd69d9 (linux-gnu, i686) @ 2011-03-14 17:29:07 UTC]
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
[Info  23:21:47.911] Updating web proxy from GConf
[Info  23:21:48.063] All services are started 5.342819

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed
[Info  23:21:49.884] nereid Client Started
[Info  23:21:50.138] GStreamer version 0.10.32.0, gapless: False, replaygain: False
[Info  23:21:50.394] AppleDeviceSource is ignoring unmounted volume Ubuntu 10.10
[Warn  23:21:50.401] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed

(Banshee:3564): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_gtk_parse_get_cached_item: assertion `GTK_IS_MENU_ITEM(widget)' failed
[Info  23:21:50.553] AppleDeviceSource is ignoring unmounted volume 68 GB Filesystem
[Warn  23:21:50.553] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;

(Banshee:3564): Pango-WARNING **: pango_layout_set_markup_with_accel: Error on line 1: Entity did not end with a semicolon; most likely you used an ampersand character without intending to start an entity - escape ampersand as &amp;
[Info  23:22:41.280] Uncached artwork size 39 requested
[Info  23:22:52.009] Uncached artwork size 39 requested

```

Blah, blah, blah...


Whatever... at least Banshee started.

The odd thing is, my Conky script recognized 'banshee-1' as running, and adjusted itself to receive Banshee output, but none was present. Output required calls to 'banshee'.

I rewrote the Conky code to use 'banshee-1' for the 'if_running' call, and 'banshee-1' for the 'if_match', 'execi', 'execpi' and so forth, and so on.

Soooo, I'm back to having to use both 'banshee' & 'banshee-1' in Conky, just like 3 days ago.

Evidently, Python is still seeing 'banshee-1', but Bash isn't.  Go figure!

Bwahahahaha!  What a mess!  :D

Truely, this constant Banshee renaming is going to be a deal-breaker for a lot of ppl.

The devs need to stick with one name or the other, and clean up the mess that all of this fiddling around has caused.

---

### Post by mc4man on 2011-03-15
Well you're probably using one of the banshee ppas (daily ? 
I'd assume opening from the soundmenu probably works

So now it's just /usr/bin/banshee  for the loader script.
It's likely the various banshee-1*.desktops ( 3 total in /usr/share/applications) are still using a Exec=banshee-1 <whatever>.

So either wait for a better update or edit the .desktops to reflect 
Exec=banshee <whatever>
Ex. for the  banshee-1.desktop 

Exec=banshee --redirect-log --play-enqueued %U

---

### Post by VinDSL on 2011-03-15
> **mc4man said:**
> Well you're probably using one of the banshee ppas (daily) ?

Correctamundo!  :)

From my sources.list...
```
deb http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu natty main #Banshee daily builds
```


> **mc4man said:**
> I'd assume opening from the soundmenu probably works.

No dice!  Doesn't open from there either (just tried it)...  :(


> **mc4man said:**
> So either wait for a better update or [...]

Yes, thanks!  That's what I'll do.

I'm trying to work within 'the system', if you will.

If it was just me, I'd fix it for myself, but...

When you're developing scripts for others, patches add a whole new level of complexity.  

Everyone is in a different walk in computerdom, you know?  I don't want to take responsibility for them crashing their desktops, or whatever.

K.I.S.S. is the name of the game...  ;)

---

### Post by gnomeuser on 2011-03-15
It should also be noted that as Banshee is shipped today the dbus interface and thus the commandline interaction arguments might not work.

The problem is that our DBus implementation NDesk.Dbus is abandoned and broken. Dbus-Sharp has risen from it's ashes recently and Banshee has been ported. It is though a major change which will only be introduced after the release of 2.0. So out of the box on Natty this is likely going to be broken. Natty does ship dbus-sharp though so creating a PPA with builds from the dbus-branch should be easy till the post 2.0 stable release or if desired development release of choice (snapshots or dailies we do it all baby).

So sorry, I think your dreams of Conky goodness might be in trouble, temporarily.

---

### Post by VinDSL on 2011-03-16
> **gnomeuser said:**
> So sorry, I think your dreams of Conky goodness might be in trouble, temporarily.
Interesting!  Thanks, for the insight(s)!  ;)

I'm keeping a close eye on:  [http://git.gnome.org/browse/banshee/](http://git.gnome.org/browse/banshee/)

As an aside, tonight, I got home, cranked up Natty, and did an update.

Banshee is now working in the Unity Dashboard (haven't tried the sound menu yet).

Of particular significance is... 

This is the first time that Banshee has NOT opened in 2-3 instances, when I initially clicked the Unity widget, on a fresh boot!  Yeah, team!!!

Once again, my Conky script wasn't working, so I changed all calls to 'banshee'... and boom! Banshee is working like a champ in Conky.

Heh!  Tomorrow is another day, and we'll go from there, but things are looking up!

Thanks, again, for filling me in on the underpinnings!

---

### Post by gnomeuser on 2011-03-16
> **VinDSL said:**
> Interesting!  Thanks, for the insight(s)!  ;)

I'm keeping a close eye on:  [http://git.gnome.org/browse/banshee/](http://git.gnome.org/browse/banshee/)

As an aside, tonight, I got home, cranked up Natty, and did an update.

Banshee is now working in the Unity Dashboard (haven't tried the sound menu yet).

Of particular significance is... 

This is the first time that Banshee has NOT opened in 2-3 instances, when I initially clicked the Unity widget, on a fresh boot!  Yeah, team!!!

Once again, my Conky script wasn't working, so I changed all calls to 'banshee'... and boom! Banshee is working like a champ in Conky.

Heh!  Tomorrow is another day, and we'll go from there, but things are looking up!

Thanks, again, for filling me in on the underpinnings!

If you read OMG Ubuntu I will also be sure to post a Banshee news post once the code gets merged.

---

### Post by VinDSL on 2011-03-19
> **gnomeuser said:**
> If you read OMG Ubuntu I will also be sure to post a Banshee news post once the code gets merged.
Thanks!  Yes, I love that site!

BTW, here's the latest anomaly...  Opening Banshee mutes the volume in Natty.


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-19-mar-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-19-mar-2011.png")[/INDENT]


If you'll notice, in the top-right corner, when I open Banshee, the system volume mutes itself.

This started about 3 days ago, after one of the updates.

There have been so many updates lately, I'm not sure which one is responsible for it...

---

### Post by mc4man on 2011-03-19
> Opening Banshee mutes the volume in Natty.
It's not just banshee 
Was fixed about a week ago, then broken again 
[https://bugs.launchpad.net/indicator-sound/+bug/730925](https://bugs.launchpad.net/indicator-sound/+bug/730925)

---

### Post by VinDSL on 2011-03-19
> **mc4man said:**
> It's not just banshee 
Was fixed about a week ago, then broken again 
[https://bugs.launchpad.net/indicator-sound/+bug/730925](https://bugs.launchpad.net/indicator-sound/+bug/730925)
Oh, ok, thanks!

That pinpoints it.

Subscribed...  ;)

---

### Post by rburkartjo on 2011-03-20
i have most of my music on a different partition that mounts at startup. banshee would not import my music or even play a directory until i moved it into my home folder. vlc still seems to function the best so far. i dont have the above problem with it.

---

### Post by P-I H on 2011-03-20
I am using Banshee to play music. I have all music in an Ubuntu server and it is not possible to move the music to my home directory. I think the message in Banshee to move media to the home directory is kind of strange.
However I have manage play my music from the NAS with this procedure:
- changed the Music folder to the NAS by Edit/Preferences/Source specific
- Import the music by Media/Import media
As I understand Banshee will then create a "Music Library".
I have also a Folder.jpg file that contains album art in each album directory. With this set up you can brows the music library by album pictures, which is quite nice

---

### Post by gnomeuser on 2011-03-21
> **P-I H said:**
> I am using Banshee to play music. I have all music in an Ubuntu server and it is not possible to move the music to my home directory. I think the message in Banshee to move media to the home directory is kind of strange.
However I have manage play my music from the NAS with this procedure:
- changed the Music folder to the NAS by Edit/Preferences/Source specific
- Import the music by Media/Import media
As I understand Banshee will then create a "Music Library".
I have also a Folder.jpg file that contains album art in each album directory. With this set up you can brows the music library by album pictures, which is quite nice

That specific feature is an Ubuntu change. It depends on the Library Watcher which is disabled by default (and please keep it that way, the library watcher is unfortunately prone to making Banshee eat gigs of RAM for reasons currently fairly hard to fix without introducing problematic regressions in every gnome# using application - e.g. the fix for the memory leak makes Banshee crash when scanning the library and makes docky.. well unfunny, we are working on the right solution though).

The intend is good though, and in most normal cases the message makes sense.

---

### Post by Amaranth on 2011-03-21
Err, the sound menu requires dbus (it uses the mpris interface) so I doubt banshee is going to ship in natty with a non-functional dbus interface.

---

### Post by VinDSL on 2011-03-24
w00t!  Things are looking up!  :D

I just cranked up Natty and did an update.

This is the first time, in ages, that Banshee did NOT (initially) open up in 2-3 instances, with error dialogs all over the place.

Plus, not only did Banshee open in a single instance (with no errors), but the volume was NOT muted!


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-23-mar-2011(3)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-23-mar-2011(3).png")[/INDENT]


Yeah, team!!!

---

### Post by encefalocardia on 2011-03-24
Seems evolving pretty nice. I'm still waiting for my iPad support.

---

### Post by VinDSL on 2011-03-24
> **encefalocardia said:**
> Seems evolving pretty nice. I'm still waiting for my iPad support.
I'm waiting for the devs to add a full-out command line interface.  That would make Banshee World-Class!  :D

For instance:

With rhythmbox-client, you can specify --print-playing-format %tt --no-start.

This outputs the title, without starting a new instance of rhythmbox.  Very useful for things like Conky!

With Banshee, I've been using --no-present --hide (which I'm not even confident does anything).  Timing becomes paramount when you're sucking Banshee data (especially on exit).  If you don't give Banshee enough breathing room, it starts looping on you.

The trick is to add wait-states, to allow Banshee to catch up.  

Applying the brakes to the parser works a treat, but it's kind of a ghetto fix, you know?

I *thought* about asking them to consider adding some command line functionality, similar to (or a clone of) the Rhythmbox CLI, but I know they're busy right now.

Maybe later...  ;)

---

