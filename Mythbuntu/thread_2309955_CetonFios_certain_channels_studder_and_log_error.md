---
title: "Ceton/Fios certain channels studder and log error"
date: 2016-01-14
forum: Mythbuntu
---

### Post by korgman on 2016-01-14
Hello,
   I've had myth .27 working as my backend from the latest Mythbuntu release for a few months.  i use Kodi as the front end, and have a Ceton Infinitv6 tuner card for my Fios.  I get all my copy free channels, and generally the viewing experience is perfect.  Fox 45 Baltimore, channel 510 in my Fios package has periodic problems, it studders badly, very badly, and its only that channel.  Its not all the time, but when it happens its more or less a screen freeze.  I thought it was Kodi at first, but the Kodi logs were clean.  

I just had it happen, and I was tailing the mythbackend log.  Here is what I see.  A discontinuity detected.  
```

Jan 14 22:02:39 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4d9 discontinuity detected ((1+1)%16!=4)  0.02%
Jan 14 22:02:45 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4d9 discontinuity detected ((6+1)%16!=15)  0.02%
Jan 14 22:02:45 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4da discontinuity detected ((3+1)%16!=10)  0.02%
Jan 14 22:02:50 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4d9 discontinuity detected ((1+1)%16!=8)  0.02%
Jan 14 22:02:50 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4da discontinuity detected ((11+1)%16!=3)  0.02%
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 205 MB for 2665 at 2016-01-15T03:00:00Z => "House Hunters"
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 0 MB for 2510 at 2016-01-15T03:01:47Z => "FOX 45 News at 10"
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 httprequest.cpp:1365 (ExtractMethodFromURL) ExtractMethodFromURL(end) : GetRecorded : /Dvr
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 servicehost.cpp:294 (ProcessRequest) ServiceHost::ProcessRequest: GetRecorded : GET /Dvr/GetRecorded?ChanId=%32%36%36%35&StartTime=%32%30%31%36%2D%30%31%2D%31%35%54%30%33%3A%30%30%3A%30%30%5A HTTP/1.1#015
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 httprequest.cpp:244 (SendResponse) HTTPRequest::SendResponse(xml/html) () :200 OK -> 127.0.0.1: 4
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 httprequest.cpp:1365 (ExtractMethodFromURL) ExtractMethodFromURL(end) : GetRecorded : /Dvr
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 servicehost.cpp:294 (ProcessRequest) ServiceHost::ProcessRequest: GetRecorded : GET /Dvr/GetRecorded?ChanId=%32%35%31%30&StartTime=%32%30%31%36%2D%30%31%2D%31%35%54%30%33%3A%30%31%3A%34%37%5A HTTP/1.1#015
Jan 14 22:02:55 mythtv mythbackend: mythbackend[1711]: I HttpServer89 httprequest.cpp:244 (SendResponse) HTTPRequest::SendResponse(xml/html) () :200 OK -> 127.0.0.1: 4
Jan 14 22:02:56 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4da discontinuity detected ((8+1)%16!=15)  0.02%
Jan 14 22:02:59 mythtv mythbackend: mythbackend[1711]: I HttpServer91 httprequest.cpp:1365 (ExtractMethodFromURL) ExtractMethodFromURL(end) : GetRecorded : /Dvr
Jan 14 22:02:59 mythtv mythbackend: mythbackend[1711]: I HttpServer91 servicehost.cpp:294 (ProcessRequest) ServiceHost::ProcessRequest: GetRecorded : GET /Dvr/GetRecorded?ChanId=%32%36%36%35&StartTime=%32%30%31%36%2D%30%31%2D%31%35%54%30%33%3A%30%30%3A%30%30%5A HTTP/1.1#015
Jan 14 22:02:59 mythtv mythbackend: mythbackend[1711]: I HttpServer91 httprequest.cpp:244 (SendResponse) HTTPRequest::SendResponse(xml/html) () :200 OK -> 127.0.0.1: 4
Jan 14 22:03:02 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4d9 discontinuity detected ((4+1)%16!=1)  0.02%
Jan 14 22:03:02 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4da discontinuity detected ((5+1)%16!=13)  0.02%
Jan 14 22:03:03 mythtv mythbackend: mythbackend[1711]: I HttpServer93 httprequest.cpp:1365 (ExtractMethodFromURL) ExtractMethodFromURL(end) : GetRecorded : /Dvr
Jan 14 22:03:03 mythtv mythbackend: mythbackend[1711]: I HttpServer93 servicehost.cpp:294 (ProcessRequest) ServiceHost::ProcessRequest: GetRecorded : GET /Dvr/GetRecorded?ChanId=%32%35%31%30&StartTime=%32%30%31%36%2D%30%31%2D%31%35%54%30%33%3A%30%31%3A%34%37%5A HTTP/1.1#015
Jan 14 22:03:03 mythtv mythbackend: mythbackend[1711]: I HttpServer93 httprequest.cpp:244 (SendResponse) HTTPRequest::SendResponse(xml/html) () :200 OK -> 127.0.0.1: 4
Jan 14 22:03:08 mythtv mythbackend: mythbackend[1711]: W CetonStreamHandler recorders/dtvrecorder.cpp:1433 (ProcessAVTSPacket) DTVRec[3]: A/V PID 0x4d9 discontinuity detected ((12+1)%16!=9)  0.02%

```

No idea what to do next.
Matt

---

