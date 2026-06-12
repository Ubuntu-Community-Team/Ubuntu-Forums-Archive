---
title: "Rhythmbox + SMB + 2 TB of FLAC = Totally Unusable"
date: 2013-11-15
forum: Multimedia Software
---

### Post by jamesisin on 2013-11-15
I have about 2 TB worth of FLAC files (mostly) sitting on an Ubuntu 10.04 machine sharing this collection across my network using Samba.  I have been running like this for a long time and Rhythmbox running on 10.04 has little or no difficulty running under these circumstances.  (All of this is running over wire, and I have 13.10 and 10.04 machines available in addition to the 10.04 desktop-as-server just mentioned.)

However, later versions of Rhythmbox (starting at least with 13.04, including 13.10 and now the latest through an added repository) can eventually load the whole music collection.  It probably takes about eight hours to scan the whole thing the first time through.  (Compare this to Clementine which can scan through the collection is perhaps an hour.)

Once the collection is scanned Rhythmbox will play music.  That being said, I also lose any control over the application.  Any operation I might attempt to perform once the music is started (pausing, searching, switching to a playlist, &c) plunges the GUI into a cycle of greyness and naught.  (On the plus side the music does continue to play through this.)

Additionally, and I think this might be related, if I attempt to burn a playlist (Rhythmbox uses Brasero for this) the files never fully scan and thus the CD can never be burned.

I could use some help troubleshooting this as I am at a total loss.

---

### Post by jamesisin on 2013-11-21
Here are some other interesting facts.  Rhythmbox uses 100% of one of my (4) cores for playback (or even when paused).  I am able to use the play/pause toggle under the volume control applet some of the time.  However, the GUI for Rhythmbox is essentially totally unusable.

Fascinating?

---

### Post by tgalati4 on 2013-11-22
Try running rhythmbox in a terminal and post any helpful messages.  It's possible that the database has changed a lot since 10.04 and it requires a lot more time and CPU power to fill it.  It doesn't help your situation.

You could uninstall rhythmbox and grab the *.deb packagse from an older version (perhaps 12.04) and install that.

Scroll down to "R"

[http://packages.ubuntu.com/precise/gnome/](http://packages.ubuntu.com/precise/gnome/)

---

### Post by jamesisin on 2013-11-23
Dry run from terminal:

```
$ rhythmbox

(rhythmbox:4939): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/ubuntuone/ubuntuone.py", line 29, in <module>
    'Purchased from Ubuntu One')
  File "/usr/lib/python3.3/posixpath.py", line 92, in join
    "components.") from None
TypeError: Can't mix strings and bytes in path components.

(rhythmbox:4939): libpeas-WARNING **: Error loading plugin 'ubuntuone'
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:4939): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid).  Unable to remove object from construction_objects list, so memory was probably just leaked.  Please use GInitable instead.

***[above on open and below on close]***

(rhythmbox:4939): Gtk-WARNING **: mnemonic "s" wasn't removed for widget (0x1b16a50)
Unable to open ~/.mtpz-data for reading, MTPZ disabled.
```

Thanks for taking a look.

I am more interested in helping Ubuntu/Rhythmbox than in solving this issue for myself.  I am currently using Clementine on my hi-fi system (and my main machine is still running 10.04 which has no similar issues).  But I advocate for Ubuntu and this is the default player, so it's an important issue.

---

### Post by tgalati4 on 2013-11-23
It looks like possibly an Ubuntu One integration error.  Do you have an Ubuntu One plug-in enabled in rhythmbox?  I don't see it in my 12.10 version, so perhaps Ubuntu One was added to 13.04 and 13.10.  That could certainly take some time if rhythmbox has to phone home for every track that is loaded into the database.

---

### Post by jamesisin on 2013-11-23
How can I disable the UO plugin *before* opening Rhythmbox (because once it's open that plugin is marked as unavailable and can't be unchecked)?

---

### Post by deadflowr on 2013-11-23
Though I'm sure there is something simpler, you can try looking over the file
/usr/lib/rhythmbox/plugins/ubuntuone/ubuntuone.plugin.

---

### Post by jamesisin on 2013-11-23
I suppose I could just (temporarily) hide that folder (the UO folder and not the entire plugins folder).

---

### Post by tgalati4 on 2013-11-23
If you don't use Ubuntu One services, you could try removing it from your system and see if that helps.  That would quickly isolate the problem.

---

### Post by jamesisin on 2013-11-23
Done.  This does prevent the UO plugin from loading (it doesn't appear in the list of plugins of course).  Nonetheless, this does not have a positive impact on the performance (or non-performance) of Rhythmbox.  The GUI remains essentially useless.  I can click on something and probably that will eventually take, but it's unusable in this state.

Here is the output without the plugin:

```
$ rhythmbox

(rhythmbox:6529): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:6529): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid).  Unable to remove object from construction_objects list, so memory was probably just leaked.  Please use GInitable instead.

(rhythmbox:6529): Gtk-WARNING **: mnemonic "s" wasn't removed for widget (0xe7fc10)
Unable to open ~/.mtpz-data for reading, MTPZ disabled.
```

(This is without playback.)

Incidentally, judging from my RAM state it looks as though RAM may not be released by Rb.

---

### Post by tgalati4 on 2013-11-23
Perhaps review the changes in rhythmbox between 12.10 and 13.04 and see if anything stands out. Also check through the bugs that have been logged against rhythmbox 13.04 to see if others are having a problem with large flac libraries.

---

### Post by jamesisin on 2013-11-24
I see where you are going.  I don't know that going back to 12.04 is sufficient though.  I have only done brief tests using 12.04, 12.10, and 13.04.  My previous stable build for this hi-fi machine was a 10.04 machine.  I am still running 10.04 on my main machine and Rb is rock steady there.  Damn, I was hoping for something perhaps a little less investigatively intensive.

(On this current 13.10 build I also added a Rb repo to use the very latest Rb with no improvement.)

---

### Post by Sarastro on 2013-12-10
I recently built a new machine and loaded 13.04.  Rhythmbox will not play any radio station that was not part of the preloaded list of stations.  Rhythmbox will not play from music from my large FLAC collection either.  Any attempt to play music results in blank Rhythmbox entries and under *Playlists* the  entry *Unnamed playlist* is displayed.

These are the error messages displayed in a terminal window:

```
(rhythmbox:2161): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion `path != NULL' failed
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory
(rhythmbox:2161): Rhythmbox-WARNING **: Could not open device /dev/radio0
(rhythmbox:2161): Gtk-WARNING **: mnemonic "s" wasn't removed for widget (0x93d750)
Unable to open ~/.mtpz-data for reading, MTPZ disabled
```
 

Otherwise, music plays normally using Video player or VLC player.

Any help would be appreciated.

---

