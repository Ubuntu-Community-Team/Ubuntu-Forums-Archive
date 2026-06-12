---
title: "Rygel and Playstation 3"
date: 2011-03-03
forum: Multimedia Software
---

### Post by mattshow on 2011-03-03
I was wondering if anyone had much experience getting Rygel to play nicely with the Playstation 3.

Weirdly, OGGs play perfectly. The PS3 makes the request to Rygel, Rygel transcodes the file to PCM and sends it to the PS3. The list of available tracks loads quickly, the song starts playing immediately once I select it, and I can skip between tracks with ease. There's none of the delays I've experienced trying to play OGGs with other servers like PS3 Media Server. 

MP3s are a different story. From the Rygel debug log (included below) it looks like the PS3 tries to get the MP3 in pieces: It request the file, aborts the request after a certain number of bytes, and then requests the next chunk of the file. This results in delays when trying to play MP3s. 

Both the PS3 and the machine serving the media are connected to the network wirelessly, which isn't optimal. But this still seems like bad behavior on the part of the PS3. 

Has anyone had any luck getting the PS3 to play MP3s served by Rygel without delays? Or can anyone suggest a different UPnP server that can serve OGGs and MP3s to the PS3 without delays when selecting and skipping tracks?




Serving an OGG:

> 
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=8d55153547fc1542267330ee06795d96&transcode=LPCM'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: TimeSeekRange.dlna.org : npt=0.000-
** (rygel:8476): DEBUG: rygel-http-request.vala:170: Transcoding target: LPCM
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:09 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/L16;rate=44100;channels=2
** (rygel:8476): DEBUG: rygel-http-request.vala:144: TimeSeekRange.dlna.org : npt=0.00-176.99/177.00
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=LPCM;DLNA.ORG_OP=10;DLNA.ORG_CI=1;DLNA.ORG_FLAGS=01000000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=8d55153547fc1542267330ee06795d96&transcode=LPCM' handled.



Serving an MP3:
> 
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=0-
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:29 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 0-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=6561171-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:30 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 6561171-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=6561161-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:30 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 6561161-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=0-
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:30 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 0-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=0-
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:31 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 0-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=6561171-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:33 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 6561171-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=6561161-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:33 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 6561161-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=0-
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:33 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 0-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=2392-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:34 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 2392-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=2392-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:35 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 2392-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:177: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'. Headers:
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Host : 192.168.1.102:51946
** (rygel:8476): DEBUG: rygel-http-server.vala:181: User-Agent : PLAYSTATION 3
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Connection : Keep-Alive
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Accept-Encoding : identity
** (rygel:8476): DEBUG: rygel-http-server.vala:181: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-server.vala:181: Range : bytes=2392-6561298
** (rygel:8476): DEBUG: rygel-http-request.vala:142: Following HTTP headers appended to response:
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Date : Thu, 03 Mar 2011 20:24:36 GMT
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Type : audio/mpeg
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Accept-Ranges : bytes
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Range : bytes 2392-6561298/6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: Content-Length : 6561299
** (rygel:8476): DEBUG: rygel-http-request.vala:144: transferMode.dlna.org : Streaming
** (rygel:8476): DEBUG: rygel-http-request.vala:144: contentFeatures.dlna.org : DLNA.ORG_PN=MP3;DLNA.ORG_OP=01;DLNA.ORG_FLAGS=01500000000000000000000000000000
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.
** (rygel:8476): DEBUG: rygel-http-server.vala:198: HTTP client aborted GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236'.
** (rygel:8476): DEBUG: rygel-http-server.vala:167: HTTP GET request for URI 'http://192.168.1.102:51946/RygelHTTPServer/RygelMediaExportContentDir?itemid=58bdb030ad2f289989c1ecbe35ef6236' handled.



---

