---
title: "Playing media over network with Rhythmbox"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by FastZ on 2006-10-28
I just recently performed an upgrade from Dapper to Edgy via the Update Manager and now my Rhythmbox program wont play music from my home file server.  Before the upgrade, I could play music over my LAN without problem.  I can access my file server from this computer just fine other ways, just cant get Rhythmbox to see what's on my server.  When I go to add a folder to the playlist, it will come back up with errors saying "could not read from resource".  Any ideas?  Anybody know of a better alternative to Rhythmbox that'll work well under GNOME?

---

### Post by cat0 on 2006-10-29
I have the exact same problem here, with Rhythmbox, XMMS and Beep. Also, I cannot play any video files on my home server, regardless of player.
If I copy them to the Ubuntu desktop first, they play just fine.

---

### Post by doclivingston on 2006-10-29
I can play tracks on a remote share (samba) fine here. Can you try opening a terminal, running "rhythmbox -d" and posting the last 10 or 20 lines of output?

---

### Post by hidden80 on 2006-10-29
> **doclivingston said:**
> I can play tracks on a remote share (samba) fine here. Can you try opening a terminal, running "rhythmbox -d" and posting the last 10 or 20 lines of output?

Same problem here. I can't play any MP3 from my samba share (I can from Windows XP and Mac OS X). Here it is the output:

> 
(18:00:27) [0x81632d0] [rb_shell_load_uri] rb-shell.c:3051: adding uri smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3
(18:00:27) [0x81632d0] [rb_shell_load_uri] rb-shell.c:3086: smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3 didn't parse as a playlist
(18:00:27) [0x81632d0] [rb_shell_guess_source_for_uri] rb-shell.c:2949: source Cola de reproducción returned strength 25 for uri smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3
(18:00:27) [0x81632d0] [rb_shell_guess_source_for_uri] rb-shell.c:2949: source Fonoteca returned strength 50 for uri smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3
(18:00:27) [0x81632d0] [impl_add_uri] rb-library-source.c:1241: adding uri smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3 to library
(18:00:27) [0x81632d0] [queue_stat_uri] rhythmdb.c:2003: queueing stat for "smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3"
(18:00:28) [0x81632d0] [rhythmdb_process_events] rhythmdb.c:1830: processing RHYTHMDB_EVENT_STAT
(18:00:28) [0x81632d0] [rhythmdb_process_stat_event] rhythmdb.c:1550: queuing a RHYTHMDB_ACTION_LOAD: smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3
(18:00:28) [0x86db390] [action_thread_main] rhythmdb.c:2229: executing RHYTHMDB_ACTION_LOAD for "smb://iomega-004711/NetHDD/Musica/ACDC/ACDC%20-%20The%20very%20best/02%20-%20Let%20There%20Be%20Rock.mp3"
(18:00:28) [0x86db390] [rb_metadata_load] rb-metadata-dbus-client.c:356: sending metadata load request
(18:00:29) [0x81632d0] [rhythmdb_process_events] rhythmdb.c:1834: processing RHYTHMDB_EVENT_METADATA_LOAD
(18:00:29) [0x81632d0] [rhythmdb_entry_new] rhythmdb.c:1121: emitting entry added
(18:00:29) [0x81632d0] [rb_entry_view_row_inserted_cb] rb-entry-view.c:1667: row added


---

### Post by doclivingston on 2006-10-30
The debug output looks like it is reporting that the track was added sucessfully. Was this when you were importing one track, or several? If it was several, it might have failed on some and just happened to work on the last. Could you try importing just one file from a samba share and getting the end of the debug log?

---

### Post by cat0 on 2006-10-30
> **doclivingston said:**
> The debug output looks like it is reporting that the track was added sucessfully. Was this when you were importing one track, or several? If it was several, it might have failed on some and just happened to work on the last. Could you try importing just one file from a samba share and getting the end of the debug log?


Allow me :)
After trying to import one song, absolutely nothing happens in the Rhythmbox window, but the debug log shows the following:

```

(18:42:08) [0x8161890] [rhythmdb_process_events] rhythmdb.c:1863: processing RHYTHMDB_EVENT_QUERY_COMPLETE
(18:42:08) [0x8161890] [rhythmdb_read_leave] rhythmdb.c:763: counter: 0
(18:42:08) [0x8161890] [rhythmdb_process_events] rhythmdb.c:1856: processing RHYTHMDB_EVENT_THREAD_EXITED
(18:42:11) [0x8161890] [rb_shell_load_uri] rb-shell.c:3051: adding uri smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3
(18:42:11) [0x8161890] [rb_shell_load_uri] rb-shell.c:3086: smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3 didn't parse as a playlist
(18:42:11) [0x8161890] [rb_shell_guess_source_for_uri] rb-shell.c:2949: source Play Queue returned strength 25 for uri smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3
(18:42:11) [0x8161890] [rb_shell_guess_source_for_uri] rb-shell.c:2949: source Library returned strength 50 for uri smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3
(18:42:11) [0x8161890] [impl_add_uri] rb-library-source.c:1241: adding uri smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3 to library
(18:42:11) [0x8161890] [queue_stat_uri] rhythmdb.c:2003: queueing stat for "smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3"
(18:42:11) [0x8161890] [rhythmdb_process_events] rhythmdb.c:1830: processing RHYTHMDB_EVENT_STAT
(18:42:11) [0x8161890] [rhythmdb_process_stat_event] rhythmdb.c:1550: queuing a RHYTHMDB_ACTION_LOAD: smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3
(18:42:11) [0x85ee348] [action_thread_main] rhythmdb.c:2229: executing RHYTHMDB_ACTION_LOAD for "smb://10.0.0.5/music/Album/Enslaved%20-%202006%20-%20RUUN/01-entroper.mp3"
(18:42:11) [0x85ee348] [start_metadata_service] rb-metadata-dbus-client.c:244: Got metadata helper D-BUS address unix:abstract=/tmp/dbus-Rh8rfGn2zo,guid=733946452ecb8dfbd04a9c54bd4d0900
(18:42:11) [0x85ee348] [start_metadata_service] rb-metadata-dbus-client.c:260: Metadata process 11170 started
(18:42:11) [0x85ee348] [rb_metadata_load] rb-metadata-dbus-client.c:356: sending metadata load request
(18:42:12) [0x8161890] [rhythmdb_process_events] rhythmdb.c:1834: processing RHYTHMDB_EVENT_METADATA_LOAD
(18:42:12) [0x8161890] [rhythmdb_entry_new] rhythmdb.c:1121: emitting entry added
(18:42:12) [0x8161890] [rb_entry_view_row_inserted_cb] rb-entry-view.c:1667: row added
(18:42:12) [0x8161890] [rb_source_set_property] rb-source.c:464: Setting Import Errors visibility to 1
(18:42:12) [0x8161890] [visibility_notify_cb] rb-sourcelist.c:830: Source visibility changed: Import Errors
(18:42:12) [0x8161890] [paned_size_allocate_cb] rb-shell.c:2712: paned position 373
(18:42:12) [0x8161890] [sidebar_paned_size_allocate_cb] rb-shell.c:2722: sidebar paned position 300

```

---

### Post by FastZ on 2006-10-30
This is what I get when I try to import one song and then running rhythmbox -d in a terminal window....

```
matt@linux:~$ rhythmbox -d
(12:40:27) [0x8161340] [rb_debug_init_match] rb-debug.c:141: Debugging enabled
(12:40:27) [0x8161340] [main] main.c:204: initializing Rhythmbox 0.9.6
(12:40:27) [0x8161340] [main] main.c:212: going to create DBus object
(12:40:27) [0x8161340] [main] main.c:399: THE END

```

This is what I get when I run that command with sudo....
```
(12:43:35) [0x84a6200] [save_entry_type] rhythmdb-tree.c:969: saving entries of type song
(12:43:35) [0x84a6200] [save_entry_type] rhythmdb-tree.c:969: saving entries of type ignore
(12:43:35) [0x84a6200] [save_entry_type] rhythmdb-tree.c:969: saving entries of type iradio
(12:43:35) [0x84a6200] [save_entry_type] rhythmdb-tree.c:969: saving entries of type podcast-feed
(12:43:35) [0x84a6200] [save_entry_type] rhythmdb-tree.c:969: saving entries of type podcast-post
(12:43:35) [0x8161340] [rb_tray_icon_finalize] rb-tray-icon.c:232: tray icon 0x846f0c8 finalizing
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:906: shutting down playlist manager
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:909: unreffing playlist manager
(12:43:35) [0x8161340] [rb_playlist_manager_finalize] rb-playlist-manager.c:273: Finalizing playlist manager
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:912: unreffing removable media manager
(12:43:35) [0x8161340] [rb_proxy_config_dispose] rb-proxy-config.c:133: Removing HTTP proxy config watch
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:917: unreffing clipboard shell
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:920: destroying prefs
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:924: destroying tooltips
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:931: destroying window
(12:43:35) [0x8161340] [rb_static_playlist_source_dispose] rb-static-playlist-source.c:186: Disposing static playlist source 0x83ee030
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:313: Disposing playlist source 0x83ee030
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x83ee030: 'Play Queue'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x83ea4c0
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x83ea450
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x83ea488
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x847a000: 'Library'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x8469b70
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x8469b00
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x8469b38
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x8489800: 'Radio'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x8469e08
(12:43:35) [0x8161340] [rb_iradio_source_finalize] rb-iradio-source.c:255: finalizing iradio source
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x8489800: 'Radio'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x84879c0 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x84879c0
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x84879c0
(12:43:35) [0x8161340] [rb_podcast_source_dispose] rb-podcast-source.c:424: dispose podcast_source
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x829a1c8: 'Podcasts'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x846a048
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x84976d8
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x84976d8
(12:43:35) [0x8161340] [rb_podcast_source_dispose] rb-podcast-source.c:424: dispose podcast_source
(12:43:35) [0x8161340] [rb_podcast_source_finalize] rb-podcast-source.c:453: finalizing podcast source
(12:43:35) [0x8161340] [rb_podcast_manager_finalize] rb-podcast-manager.c:329: Podcast Manager END
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x829a1c8: 'Podcasts'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x8497808 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x8497808
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x8497808
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x849b188: 'Missing Files'
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x849b188: 'Missing Files'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x849b188: 'Missing Files'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x8497870 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x8497870
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x8497870
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x849b588: 'Import Errors'
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x849b588: 'Import Errors'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x849b588: 'Import Errors'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x84a1418 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x84a1418
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x84a1418
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:313: Disposing playlist source 0x83ee100
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x83ee100: 'Recently Added'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x84cbf58
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x84cc128
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x84cc080
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:307: Dispose has already run for playlist source 0x83ee100
(12:43:35) [0x8161340] [rb_playlist_source_finalize] rb-playlist-source.c:338: Finalizing playlist source 0x83ee100
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x83ee100: 'Recently Added'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x85e0800 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x85e0800
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x85e0800
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:313: Disposing playlist source 0x83ee1d0
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x83ee1d0: 'Recently Played'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9088
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9018
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9050
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:307: Dispose has already run for playlist source 0x83ee1d0
(12:43:35) [0x8161340] [rb_playlist_source_finalize] rb-playlist-source.c:338: Finalizing playlist source 0x83ee1d0
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x83ee1d0: 'Recently Played'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x85eaaf0 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x85eaaf0
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x85eaaf0
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:313: Disposing playlist source 0x83ee2a0
(12:43:35) [0x8161340] [rb_source_dispose] rb-source.c:297: Disposing source 0x83ee2a0: 'My Top Rated'
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9290
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9220
(12:43:35) [0x8161340] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:438: finalizing property model 0x85e9258
(12:43:35) [0x8161340] [rb_playlist_source_dispose] rb-playlist-source.c:307: Dispose has already run for playlist source 0x83ee2a0
(12:43:35) [0x8161340] [rb_playlist_source_finalize] rb-playlist-source.c:338: Finalizing playlist source 0x83ee2a0
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:324: Finalizing source 0x83ee2a0: 'My Top Rated'
(12:43:35) [0x8161340] [rb_source_finalize] rb-source.c:327: Unreffing model 0x8600e08 count: 1
(12:43:35) [0x8161340] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:619: disposing query model 0x8600e08
(12:43:35) [0x8161340] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:662: finalizing query model 0x8600e08
(12:43:35) [0x8161340] [rb_shell_finalize] rb-shell.c:939: shutting down DB
(12:43:35) [0x8161340] [rhythmdb_shutdown] rhythmdb.c:596: 2 outstanding threads
(12:43:36) [0x8609e00] [action_thread_main] rhythmdb.c:2274: exiting main thread
(12:43:36) [0x8161340] [rb_shell_finalize] rb-shell.c:942: unreffing DB
(12:43:36) [0x8161340] [rb_shell_finalize] rb-shell.c:947: shell shutdown complete
(12:43:36) [0x8161340] [main] main.c:384: out of toplevel loop
(12:43:36) [0x8161340] [main] main.c:399: THE END
matt@linux:~$ 

```

running it with sudo brings up a whole 'nother instance of Rhythmbox and gives about a gazillion lines of garbage in the terminal window.  That last bit there is what showed up after I had closed the Rhythmbox program that the sudo command opened.  Where's the debug logs?

---

### Post by Phil_Mulley on 2006-11-10
I am getting exactly the same thing.  Everything was fine on the last version of Ubuntu but with edgy I cannot play MP3s from my Windows SMB share using Rhythmbox or anything else.  To make matters worse I specified the SMB share as its library and now it just hangs on startup.

---

### Post by hiwatt156 on 2006-11-15
I was having the same issue, I'm a newb, so I'm not so sure what the "right" way to fix this is, but I was able to at least figure out that the problem seems to be something about the Samba configuration and NOT the media player(s).  My thinking was that if I could mount the folder it might treat the files as local, but I found that in addition to the above issues I could not even successfully mount the share via Nautilus, trying to do so generated "Nautilus cannot display smb://servername/sharename Please select another viewer and try again.".

Not sure what's going on with that and couldn't find anything about this issue that seemed right.

So, went to mount manually, and found that the only thing that works is to mount using cifs instead of smbmount, additionally found that I had to use the IP to make that work (couldn't resolve server by name).

Here's my workaround:

First I made a mount point

```
sudo mkdir /mnt/data
```

or to get it to show up under "places" in Nautilus do:

```
sudo mkdir /media/data
```

then to get it to happen at boot I did:

```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

I then added the line:

```
//10.10.50.1/data /mnt/data cifs credentials=/root/.smbcredentials,uid=500,gid=500

(substitute your IP/share and your mount point)
```

I then created the credentials file referenced in the above:

```
gksudo gedit /root/.smbcredentials

```

Added the lines:

```
username=(username)
password=(password)
```

Saved the file, then changed the permissions:

```
sudo chmod 700 /root/.smbcredentials

```

Then refreshed the mount points with:

```
sudo mount -a
```

Now I have the remote folder in my mount point and I can open everything.

If anyone knows of a better way to do this PLEASE post it.  I think the issue is that Gnome uses SMBFS and that only CIFS really works correctly with 2k/2k3/XP.  I'm pretty sure that I did NOT have this problem using KDE on my slax CD.

One other weird thing I noticed is that I could browse to and open my word documents no problem, so maybe there's something that just blocks certain file types???

-Chris

---

### Post by Skerit on 2006-11-30
I did it this way, I mounted my network drive to a folder in my home map, it used to work perfectly but since a couple of days RB is crashing like crazy... I even considered using another musicplayer (Gave that songbird a chance but too many bells and whistles making the interface too damn bloated...) Rhythmbox is just waay too good to give up...

---

