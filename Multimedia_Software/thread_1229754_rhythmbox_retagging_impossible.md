---
title: "rhythmbox retagging impossible"
date: 2009-08-02
forum: Multimedia Software
---

### Post by heluani on 2009-08-02
1) open an audio file properties (any type) on RB and change it's title tag
2) relaunch RB and try to change back the tag

I get a "Error saving metadata: Internal GStreamer problem; file a bug" message

gst-launch -t shows the right tags 

The only way I have to retag the file is to use another application (for example id3tag from id3lib) to retag the file, then open RB and I can edit the properties again (only once as in 1) above).

Running RB --debug shows this in in console:
```
....
(10:10:56) [0xbad950] [rb_metadata_dbus_add_to_message] rb-metadata-dbus.c:132:
opening container type {uv}
(10:10:56) [0xdfcfc0] [_handle_message] rb-metadata-dbus-service.c:345:
handling metadata service message: save
(10:10:56) [0xdfcfc0] [rb_metadata_save] rb-metadata-gst.c:951: saving metadata
for uri:
file:///usr/share/media/music/iTunes/iTunes%20Music/Willie%20Nelson/Rainbow%20Connection/01%20Rainbow%20Connection.mp3
(10:10:56) [0xdfcfc0] [rb_metadata_save] rb-metadata-gst.c:954: temporary file
name prefix:
file:///usr/share/media/music/iTunes/iTunes%20Music/Willie%20Nelson/Rainbow%20Connection/.01%20Rainbow%20Connection.mp3
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting album-sortname
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting album
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting date
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting genre
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting title
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting comment
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting track-number
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting artist
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting album-disc-number
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting bitrate
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting replaygain-track-gain
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting replaygain-track-peak
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting replaygain-album-gain
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting replaygain-album-peak
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting musicbrainz-trackid
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting musicbrainz-artistid
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting musicbrainz-albumid
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting musicbrainz-albumartistid
(10:10:56) [0xdfcfc0] [rb_metadata_gst_add_tag_data] rb-metadata-gst.c:905:
Setting musicbrainz-sortname
(10:10:56) [0xdfcfc0] [id3_pad_added_cb] rb-metadata-gst.c:104: linked pad from
id3demux to id3v2mux
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from giostreamsink
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from id3v2mux0
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from id3demux1
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from urisrc
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from pipeline
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from id3v2mux0
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from id3demux1
(10:10:56) [0xdfcfc0] [rb_metadata_bus_handler] rb-metadata-gst.c:642: message
of type state-changed from urisrc
(10:10:56) [0xdfcfc0] [rb_metadata_gst_load_tag] rb-metadata-gst.c:355: no
metadata field for tag "private-id3v2-frame"
(10:10:56) [0xdfcfc0] [rb_metadata_gst_load_tag] rb-metadata-gst.c:411:
processed string tag "album": "Rainbow Connection"
(10:10:56) [0xdfcfc0] [rb_metadata_gst_load_tag] rb-metadata-gst.c:402: Got
shorter duplicate tag
(10:10:56) [0xbad950] [kill_metadata_service] rb-metadata-dbus-client.c:154:
dbus connection already closed
(10:10:56) [0xbad950] [kill_metadata_service] rb-metadata-dbus-client.c:161:
killing child process
(10:10:56) [0xbad950] [kill_metadata_service] rb-metadata-dbus-client.c:168:
closing metadata child process stdout pipe
(10:10:56) [0xbad950] [default_sync_metadata] rhythmdb.c:4645: error saving
metadata for
file:///usr/share/media/music/iTunes/iTunes%20Music/Willie%20Nelson/Rainbow%20Connection/01%20Rainbow%20Connection.mp3:
Internal GStreamer problem; file a bug; reloading metadata to revert
.....
.....
```

I'd be really grateful for any idea

R.

---

