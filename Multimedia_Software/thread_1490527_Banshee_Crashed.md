---
title: "Banshee Crashed"
date: 2010-05-22
forum: Multimedia Software
---

### Post by caver1 on 2010-05-22
Banshee just crashed on me with the following error Message and details;
         An Exception has been thrown by the target of an invocation
           Details
            An unhandled exception was thrown: The database disk image is malformed

database disk image is malformed

  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] 
  at Mono.Data.Sqlite.SqliteDataReader.NextResult () [0x00000] 
  at Mono.Data.Sqlite.SqliteDataReader..ctor (Mono.Data.Sqlite.SqliteCommand cmd, CommandBehavior behave) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteDataReader:.ctor (Mono.Data.Sqlite.SqliteCommand,System.Data.CommandBehavior)
  at Mono.Data.Sqlite.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteReader ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.22

Assembly Version Information:

Banshee.AudioCd (1.6.0.0)
Banshee.CoverArt (1.6.0.0)
Banshee.Bookmarks (1.6.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.6.0.0)
Lastfm (1.6.0.0)
Banshee.Dap (1.6.0.0)
Banshee.MultimediaKeys (1.6.0.0)
Banshee.Bpm (1.6.0.0)
webkit-sharp (1.1.15.0)
Banshee.Wikipedia (1.6.0.0)
Banshee.Lastfm (1.6.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.6.0.0)
Banshee.Hal (1.6.0.0)
Banshee.Unix (1.6.0.0)
Banshee.GStreamer (1.6.0.0)
Mono.Media (1.6.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.6.0.0)
Banshee.NowPlaying (1.6.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.6.0.0)
System.Xml (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.6.0.0)
gtk-sharp (2.12.0.0)
Banshee.Core (1.6.0.0)
Banshee.ThickClient (1.6.0.0)
Nereid (1.6.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
System (2.0.0.0)
Hyena (1.6.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.6.0.0)
Banshee (1.6.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-22-generic x86_64 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

[/etc/debian_version]
squeeze/sid


How to get around this?

---

### Post by boombox1387 on 2010-05-26
> **caver1 said:**
> 
database disk image is malformed

This is why Banshee crashed.  Something must have recently trashed your banshee.db file.  A loss of power to your computer or system crash could have caused this problem, if Banshee was running at the time.

> **caver1 said:**
> 
How to get around this?

Unfortunately, this problem isn't uncommon.  It's so common, in fact, that it earned a spot on [Banshee's FAQ list]("http://banshee-project.org/support/faq/") (see the bottom of the page).  To summarize, this problem can often be fixed by running the following commands:

First, you'll need sqlite3 installed.  I think this should do the trick:
```
sudo apt-get install sqlite3
```

Then run:
```
cd ~/.config/banshee-1
```
```
sqlite3 banshee.db ".dump" > dump
```
```
mv banshee.db banshee.db.backup
```
```
cat dump | sqlite3 banshee.db
```

Or, if you don't care about saving your playlists, ratings, and play count information, you can just delete (or rename) the bad database, found here: ~/.config/banshee-1/banshee.db

If you have any problems, be sure to report back here.  Hope this helps!

---

### Post by kellsens on 2010-10-18
boombox1387 Thank's a lot.

---

### Post by Curbuntu on 2011-02-01
I hope it's not too late to join in this discussion, because I, too, have had a Banshee "fatal error," but I tried the fix recommended and it did nothing to fix the sqlite database.  I have a LOT of playlists representing a considerable amount of time invested (playlists by composer, performer[s], orchestras, conductors, genre, categories and subcategories).  I have dozens of hours invested in creating these playlists.  Starting from scratch would probably mean just dumping Banshee for a more stable equivalent; but I'd rather not re-create my datalists or change music players if I can help it.

Here is the original error message:

```
An unhandled exception was thrown: 0

at Hyena.Collections.RangeCollection.get_Item (int) <0x0009e>
at Hyena.Collections.Selection.get_FirstIndex () <0x0002a>
at Banshee.Collection.Gui.BaseTrackListView.UpdateSelection () <0x000b5>
at Banshee.Collection.Gui.BaseTrackListView.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs) <0x00020>
at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs) <0x00108>
at Banshee.MediaEngine.PlayerEngineService.OnEngineEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x000d9>
at Banshee.MediaEngine.PlayerEngine.RaiseEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x0001f>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEventArgs) <0x000f9>
at Banshee.MediaEngine.PlayerEngine.OnEventChanged (Banshee.MediaEngine.PlayerEvent) <0x0002d>
at Banshee.GStreamer.PlayerEngine.OnStateChange (intptr,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState) <0x00092>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnStateChange (intptr,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState,Banshee.GStreamer.GstState) <0x00051>
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x0000a>
at Banshee.Gui.GtkBaseClient.Run () <0x00054>
at Banshee.Gui.GtkBaseClient.Startup () <0x00044>
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x00089>


.NET Version: 2.0.50727.1433
OS Version: Unix 2.6.32.27

Assembly Version Information:

Mtp (1.6.0.0)
karma-sharp (0.0.0.0)
ipod-sharp (0.0.1.0)
System.Configuration (2.0.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Zeroconf.Providers.AvahiDBus (4.0.0.90)
Mono.Zeroconf (4.0.0.90)
Banshee.Dap.Mtp (1.6.0.0)
Banshee.Dap.Karma (1.6.0.0)
Banshee.Dap.MassStorage (1.6.0.0)
taglib-sharp (2.0.3.7)
Banshee.Audiobook (1.6.0.0)
Banshee.InternetArchive (1.6.0.0)
Banshee.FileSystemQueue (1.6.0.0)
Banshee.InternetRadio (1.6.0.0)
Banshee.PlayQueue (1.6.0.0)
ClutterFlow (1.9.0.0)
clutter-sharp (1.0.0.0)
clutter-gtk-sharp (1.0.0.0)
Banshee.ClutterFlow (1.9.0.0)
Banshee.AudioCd (1.6.0.0)
Banshee.MiniMode (1.6.0.0)
Banshee.CoverArt (1.6.0.0)
Banshee.Bookmarks (1.6.0.0)
Banshee.Emusic (1.6.0.0)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.6.0.0)
Banshee.Daap (1.6.0.0)
Lastfm (1.6.0.0)
Boo.Lang.Compiler (2.0.9.2)
Banshee.BooScript (1.6.0.0)
Migo (1.6.0.0)
Banshee.Podcasting (1.6.0.0)
Banshee.LibraryWatcher (1.6.0.0)
Banshee.MultimediaKeys (1.6.0.0)
Banshee.Bpm (1.6.0.0)
Banshee.YouTube (1.6.0.0)
webkit-sharp (1.1.15.0)
Banshee.Wikipedia (1.6.0.0)
Banshee.Lastfm (1.6.0.0)
pango-sharp (2.12.0.0)
Banshee.Widgets (1.6.0.0)
Banshee.Dap.Ipod (1.6.0.0)
Banshee.Dap (1.6.0.0)
Banshee.Hal (1.6.0.0)
Banshee.Unix (1.6.0.0)
Banshee.GStreamer (1.6.0.0)
Mono.Media (1.6.0.0)
System.Transactions (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gconf-sharp (2.24.0.0)
Banshee.Gnome (1.6.0.0)
Banshee.NowPlaying (1.6.0.0)
Mono.Cairo (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.Sqlite (1.6.0.0)
System.Xml (2.0.0.0)
System.Core (3.5.0.0)
gdk-sharp (2.12.0.0)
Mono.Addins (0.4.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.6.0.0)
gtk-sharp (2.12.0.0)
Banshee.Core (1.6.0.0)
Banshee.ThickClient (1.6.0.0)
Nereid (1.6.0.0)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
System (2.0.0.0)
Hyena (1.6.0.0)
NDesk.DBus (1.0.0.0)
glib-sharp (2.12.0.0)
Banshee.Services (1.6.0.0)
Banshee (1.6.0.0)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.32-27-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

[/etc/debian_version]
squeeze/sid


```When I tried the recommended "cat dump" etc., the command threw a long list of errors, of which this is a sample:

```
Error: near line 38526: PRIMARY KEY must be unique
Error: near line 38527: PRIMARY KEY must be unique
Error: near line 38528: PRIMARY KEY must be unique
Error: near line 38529: PRIMARY KEY must be unique
Error: near line 38530: PRIMARY KEY must be unique
Error: near line 38531: PRIMARY KEY must be unique
Error: near line 38532: PRIMARY KEY must be unique
Error: near line 38533: PRIMARY KEY must be unique
Error: near line 38534: PRIMARY KEY must be unique
Error: near line 38535: PRIMARY KEY must be unique
Error: near line 38536: PRIMARY KEY must be unique
Error: near line 38537: PRIMARY KEY must be unique
Error: near line 38538: PRIMARY KEY must be unique
Error: near line 38539: PRIMARY KEY must be unique
Error: near line 38540: PRIMARY KEY must be unique
Error: near line 38541: PRIMARY KEY must be unique
```...and the error litany ended with:

```
Error: near line 38747: index CoreTracksPrimarySourceIndex already exists
Error: near line 38748: index CoreTracksAggregatesIndex already exists
Error: near line 38749: index CoreTracksExternalIDIndex already exists
Error: near line 38750: index CoreTracksUriIndex already exists
Error: near line 38751: index CoreTracksCoverArtIndex already exists
Error: near line 38752: index CoreAlbumsIndex already exists
Error: near line 38753: index CoreAlbumsArtistIndex already exists
Error: near line 38754: index CoreArtistsIndex already exists
Error: near line 38755: index CorePlaylistEntriesIndex already exists
Error: near line 38756: index CoreSmartPlaylistEntriesIndex already exists
Error: near line 38757: index CoreShufflesIndex already exists
Error: near line 38758: index CoreShuffleModificationsIndex already exists
Error: near line 38759: index PodcastSyndicationsIndex already exists
Error: near line 38760: index PodcastItemsFeedIDIndex already exists
Error: near line 38761: index PodcastItemsGuidIndex already exists
Error: near line 38762: index PodcastItemIsReadIndex already exists
Error: near line 38763: index PodcastEnclosuresItemIDIndex already exists
```

Thanks in advance for any help you can give.

---

### Post by boombox1387 on 2011-02-03
Ouch, that doesn't look good.  I don't exactly know what went wrong or how to fix it, because I was mostly copying and pasting those instructions from the Banshee website.  I can, however, recommend asking the Banshee community about this.  I'd ask a question on the [mailing list]("http://mail.gnome.org/mailman/listinfo/banshee-list") (which you can also do using the [forum interface]("http://banshee-media-player.2283330.n4.nabble.com/")).  If you don't get a response there, you can ask about it on [Banshee's IRC channel]("irc://irc.gnome.org/#banshee").  It might take a little while for someone to answer, but if you're patient, I'm sure someone will want to help.

Also, you might want to try looking at your Banshee database in a database browser.  I don't remember which one I've used before, but you should find something if you search in the Software Center for SQLite3 Database Browser.  That way you can have a look around, and see if anything looks obviously wrong with the database.  You'll probably want to make a backup first, though:

```
cp ~/.config/banshee-1/banshee.db ~/.config/banshee-1/banshee.backup.db
```

If anyone is going to be able to fix the database, they'll probably want to have a copy to look at.  If you don't mind sharing your database, it would be best if you would have some way to get it onto the Internet (Ubuntu One or Dropbox would both be good options).  If you post it somewhere that I can get to it, I'll be happy to take a look at it and see if I can figure anything out.  My SQL skills are a bit weak, but there are definitely people more capable than me in the Banshee community who will probably be glad to help.

Good luck!

---

### Post by Curbuntu on 2011-02-03
@boombox1387, thanks so much for your reply.

After following your original advice (including cp'ing the corrupted database before running the fix), things looked very grim.  Banshee still wouldn't load.  Then it finally came up, but with an almost out-of-the-box set of playlists.  (Strange to say, it remembered some "Unplayed" items from December.)  Time to call it a day, power down, and go to bed.

However, the next morning when the audio server booted, **Banshee loaded just fine -- with all of my dozens of playlists were fully restored!**  I don't know why a reboot was required.  My guess is that some temporary files are deleted or reset on system power down, but that's just a shot in the dark.  Anyway, everything is back the way it should be, and my confidence in Banshee and sqlite is restored.  (And, more importantly, my wife didn't lose faith in Linux or Ubuntu or Banshee.  This project of digitizing and cross-referencing [as it were] her very large collection of [mostly] classical CDs is my year-long "Christmas present" to her.  I started it November '10, and at an average of one CD per day, the task will take me well into 2012 before it's complete.  Losing that database would have been "epic fail.")

I do back up all our Ubuntu machines daily with CrashPlan, but it was unclear to me how far back I would have had to go (and how many entries I would have lost) in order to restore an uncorrupted version of the database.  Happily, none of the FLAC files were affected.

Once again, many thanks for your assistance.

---

### Post by KFwLsKvVAs on 2011-10-13
boombox1387

thanks for the fix, I was going to bitch and moan about banshee being buggy and not being able to find a decent media player on linux but the fact that the .db file could get jacked up and then there's a way to save it, with like 5 lines of code is awesome.  so thanks again.

---

