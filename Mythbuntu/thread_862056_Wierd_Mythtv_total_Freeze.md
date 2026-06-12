---
title: "Wierd Mythtv total Freeze"
date: 2008-07-17
forum: Mythbuntu
---

### Post by nrune on 2008-07-17
Myth tv not responding to any commands IR or Keystroke.  No clue what is going on, any help?  Here are the logs...

Backend log
```
2008-07-16 22:00:21.198 New DB DataDirect connection
2008-07-16 22:00:21.200 Connected to database 'mythconverg' at host: 192.168.1.138
2008-07-16 22:00:22.830 Speculative scheduled 681 items in 1.6 = 0.00 match + 1.58 place
2008-07-16 22:00:57.033 MainServer::HandleAnnounce Playback
2008-07-16 22:00:57.045 adding: mythtv as a client (events: 0)
2008-07-16 22:00:57.047 MainServer::HandleAnnounce FileTransfer
2008-07-16 22:00:57.048 adding: mythtv as a remote file transfer
2008-07-16 22:00:57.088 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.089 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.090 RingBuffer::RingBuffer(): Failed to open remote file ()
2008-07-16 22:00:57.208 MainServer::HandleAnnounce Playback
2008-07-16 22:00:57.218 adding: mythtv as a client (events: 0)
2008-07-16 22:00:57.226 MainServer::HandleAnnounce FileTransfer
2008-07-16 22:00:57.233 adding: mythtv as a remote file transfer
2008-07-16 22:00:57.242 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.250 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.258 RingBuffer::RingBuffer(): Failed to open remote file ()
2008-07-16 22:00:57.382 MainServer::HandleAnnounce Playback
2008-07-16 22:00:57.383 adding: mythtv as a client (events: 0)
2008-07-16 22:00:57.393 MainServer::HandleAnnounce FileTransfer
2008-07-16 22:00:57.400 adding: mythtv as a remote file transfer
2008-07-16 22:00:57.409 RemoteFile::openSocket(control socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.417 RemoteFile::openSocket(file data socket):
                        Could not connect to server "" @ port -1
2008-07-16 22:00:57.425 RingBuffer::RingBuffer(): Failed to open remote file ()
2008-07-16 22:01:02.668 MainServer::HandleAnnounce Playback
2008-07-16 22:01:02.669 adding: mythtv as a client (events: 0)
2008-07-16 22:01:02.670 MainServer::HandleAnnounce FileTransfer
2008-07-16 22:01:02.670 adding: mythtv as a remote file transfer

```

Frontend.log
```
2008-07-16 22:00:00.157 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-07-16 22:00:00.362 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-07-16 22:00:05.267 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-07-16 22:00:06.535 TV: Attempting to change from WatchingRecording to WatchingPreRecorded
2008-07-16 22:00:06.535 TV: Changing from WatchingRecording to WatchingPreRecorded
2008-07-16 22:00:20.362 New DB scheduler connection
2008-07-16 22:00:20.364 Connected to database 'mythconverg' at host: 192.168.1.138
2008-07-16 22:00:20.647 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-07-16 22:01:26.255 WriteAudio: buffer underrun
2008-07-16 22:01:45.263 WriteAudio: buffer underrun
2008-07-16 22:02:31.230 WriteAudio: buffer underrun
2008-07-16 22:02:43.439 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-07-16 22:02:57.294 WriteAudio: buffer underrun
2008-07-16 22:02:58.307 WriteAudio: buffer underrun
2008-07-16 22:02:58.954 WriteAudio: buffer underrun
2008-07-16 22:03:10.920 WriteAudio: buffer underrun
2008-07-16 22:03:12.619 Starting update of NDFD-6_day
2008-07-16 22:03:12.664 Starting update of NWS-XML
2008-07-16 22:03:12.807 Starting update of NDFD-18_Hour
2008-07-16 22:03:15.097 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/nrune/.mythtv/MythWeathe$
2008-07-16 22:03:16.759 Starting update of Map-Download
2008-07-16 22:03:17.191 Starting update of Animated-Map-Download
2008-07-16 22:03:21.787 nice /usr/share/mythtv/mythweather/scripts/us_nws/maps.pl -u ENG -d /home/nrune/.mythtv/MythWeather/$
2008-07-16 22:03:23.980 nice /usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl -u ENG -d /home/nrune/.mythtv/MythWeath$
2008-07-16 22:03:27.979 nice /usr/share/mythtv/mythweather/scripts/us_nws/ndfd18.pl -u ENG -d /home/nrune/.mythtv/MythWeathe$
2008-07-16 22:03:29.792 NVP: prebuffering pause

```

And then in the frontend log there are pages and pages of this...
```
2008-07-16 22:03:32.778 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:32.779 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:32.779 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:32.788 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:34.307 NVP: Prebuffer wait timed out 10 times.
2008-07-16 22:03:35.291 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.292 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.341 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.392 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.441 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.491 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.541 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.591 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.641 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.691 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.741 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.791 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.841 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.891 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.941 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:35.991 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.041 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.091 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.141 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.191 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.241 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.291 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.341 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.391 VideoOutputXv Error: Child      B       was already marked as available.
2008-07-16 22:03:36.441 VideoOutputXv Error: Child      B       was already marked as available.

```

Any help apprecated.  Reboot seemed to solve the problem for now.

Thanks!

---

