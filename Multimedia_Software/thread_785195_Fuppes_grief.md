---
title: "Fuppes grief"
date: 2008-05-07
forum: Multimedia Software
---

### Post by stewils on 2008-05-07
I've worked through the tutorials and I'm ALMOST there.  My Xbox picks up the fuppes server, but all is not as it should be.
Problem a) Music files are found, but not sorted by artist or album, just one long long long list.

Problem b)Vids appear in a nice list uder the folder name but upon attempting to play the screen goes blank and then I get a disconnect message.
Provided are my fuppes.cfg and vfolder.cfg and the debug info upon attempting to play an avi file.

This is the debug info:
```
== lib/HTTP/HTTPRequestHandler.cpp (80) :: Wed May  7 10:20:02 2008 ==
HandleHTTPRequest() :: /MediaServer/VideoItems/00FFFFFFE2.wmv

== lib/ContentDirectory/ContentDatabase.cpp (417) :: Wed May  7 10:20:02 2008 ==
SELECT select count(*) as VALUE from OBJECTS where OBJECT_ID = 4294967266 and DEVICE = 'Xbox 360';

== lib/ContentDirectory/ContentDatabase.cpp (417) :: Wed May  7 10:20:02 2008 ==
SELECT select   * from   OBJECTS o   left join OBJECT_DETAILS d on (d.ID = o.DETAIL_ID) where   o.OBJECT_ID = 4294967266 and o.DEVICE = 'Xbox 360'

== lib/HTTP/HTTPRequestHandler.cpp (268) :: Wed May  7 10:20:02 2008 ==
transcode /media/sbd/My Videos/movie.avi

== lib/HTTP/HTTPMessage.cpp (688) :: Wed May  7 10:20:02 2008 ==
TranscodeContentFromFile :: /media/sbd/My Videos/movie.avi

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:02 2008 ==
we are sending faster then we can transcode!
  try     : 1/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:02 2008 ==
we are sending faster then we can transcode!
  try     : 2/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:03 2008 ==
we are sending faster then we can transcode!
  try     : 3/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:03 2008 ==
we are sending faster then we can transcode!
  try     : 4/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:04 2008 ==
we are sending faster then we can transcode!
  try     : 5/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:04 2008 ==
we are sending faster then we can transcode!
  try     : 6/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:05 2008 ==
we are sending faster then we can transcode!
  try     : 7/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:05 2008 ==
we are sending faster then we can transcode!
  try     : 8/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:06 2008 ==
we are sending faster then we can transcode!
  try     : 9/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:06 2008 ==
we are sending faster then we can transcode!
  try     : 10/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:07 2008 ==
we are sending faster then we can transcode!
  try     : 11/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:07 2008 ==
we are sending faster then we can transcode!
  try     : 12/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:08 2008 ==
we are sending faster then we can transcode!
  try     : 13/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:08 2008 ==
we are sending faster then we can transcode!
  try     : 14/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:09 2008 ==
we are sending faster then we can transcode!
  try     : 15/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:09 2008 ==
we are sending faster then we can transcode!
  try     : 16/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:10 2008 ==
we are sending faster then we can transcode!
  try     : 17/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:10 2008 ==
we are sending faster then we can transcode!
  try     : 18/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:11 2008 ==
we are sending faster then we can transcode!
  try     : 19/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/HTTP/HTTPMessage.cpp (438) :: Wed May  7 10:20:11 2008 ==
we are sending faster then we can transcode!
  try     : 20/20
  length  : 0
  position: 0
  size    : 1048576
  rest    : 0
delaying send-process!

== lib/Transcoding/TranscodingCache.cpp (555) :: Wed May  7 10:20:12 2008 ==
release object "/media/sbd/movie.avi"
ref count: 1
delay: 4

== lib/SSDP/SSDPCtrl.cpp (82) :: Wed May  7 10:20:15 2008 ==
CleanupSessions

== lib/Transcoding/TranscodingCache.cpp (589) :: Wed May  7 10:20:17 2008 ==
delete object "/media/sbd/My Videos/movie.avi"
delay: 4
```

---

### Post by stewils on 2008-05-08
bump?

---

### Post by stewils on 2008-05-09
Please, somebody...anybody....please....

---

### Post by stewils on 2008-05-09
Never mind.  Solved.
For anyone else..update to the latest fuppes build.
Easy instructions are on the fuppes wiki.

then get [this]("http://fuppes.ulrich-voelkel.de/forum/viewtopic.php?f=7&t=37&p=449#p449")
config file.  Well it worked for me.

---

