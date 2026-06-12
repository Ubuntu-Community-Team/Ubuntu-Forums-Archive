---
title: "Streamripper doesn't rip, crashes"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by zds on 2006-11-07
Running streamripper on Xubuntu 6.06.1 I get the following crash:

```
:~$ streamripper wers.org/wers.pls -l 5 --debug
Connecting...
stream: Streamripper_rips
server name: Microsoft-IIS/6.0
bitrate: 0
meta interval: -1

Time to stop is here, bailing
shutting down
Floating point exception (core dumped)
:~$
```

No content is ripped. The error log contains the following:


```
=========================
STREAMRIPPER unix 1.61.17
LOCALE is en_US.UTF-8
Using nl_langinfo() to get system codeset.
Found iconv.
LOCALE CODESET is UTF-8
inet_sc_connect(): calling httplib_parse_url
inet_sc_connect(): calling sockinit
inet_sc_connect(): calling sock_open: host=wers.org, port=80
inet_sc_connect(): calling httplib_construct_sc_request
inet_sc_connect(): calling socklib_sendall
inet_sc_connect(): calling get_sc_header
RECV req     1 bytes, got     1 bytes
RECV req     1 bytes, got     1 bytes
RECV req     1 bytes, got     1 bytes
RECV req     1 bytes, got     1 bytes
```

this continues for a while, then

```
http header:
HTTP/1.1 200 OK
Content-Length: 230
Content-Type: audio/x-scpls
Last-Modified: Tue, 05 Sep 2006 05:58:29 GMT
Accept-Ranges: bytes
ETag: "80704e4fb0d0c61:26d"
Server: Microsoft-IIS/6.0
Date: Wed, 08 Nov 2006 01:24:44 GMT
Connection: close

Deduced content type: 1
FILELIB_INIT: output_directory=./
FILELIB_INIT: output_pattern=
FILELIB_INIT: showfile_pattern=
Stripping icy name...
strip_invalid_chars() mb_in:
Streamripper_rips
53 74 72 65 61 6d 72 69 70 70 65 72 5f 72 69 70 73 
Conversion returned 10
strip_invalid_chars() w_in (pre):
0053 0074 0072 0065 0061 006d 0072 0069 0070 0070 0065 0072 005f 0072 0069 0070 0073 
strip_invalid_chars() w_invalid:
005c 002f 003a 002a 003f 0022 003c 003e 007c 007e 
strip_invalid_chars() w_in (post):
0053 0074 0072 0065 0061 006d 0072 0069 0070 0070 0065 0072 005f 0072 0069 0070 0073 
strip_invalid_chars() mb_in (post):
Streamripper_rips
53 74 72 65 61 6d 72 69 70 70 65 72 5f 72 69 70 73 
Done stripping icy name.
SET_OUTPUT_DIR:output_pattern=
SET_OUTPUT_DIR:output_directory=./
SET_OUTPUT_DIR:default_pattern=%S/%A - %T
SET_OUTPUT_DIR:default_pattern_tail=%A - %T
SET_OUTPUT_DIR:pattern_head(pre)=/home/zachary/./
SET_OUTPUT_DIR:opat_path=%S/%A - %T
::16 0 16 0
::33 2 16 0
::34 3 34 3
::34 3 34 3
Got pattern head: /home/zachary/./Streamripper_rips/
Got opat tail:    %A - %T
Trying to make output_directory: /home/zachary/./Streamripper_rips/
RIPSTREAM_DESTROY
RIPSTREAM_RIP: top of loop
RECV req  1024 bytes, got   230 bytes
RECV req   794 bytes, got     0 bytes
recv recieved zero bytes!
rip_manager_recv: expected 1024, got 230
get_stream_data bad return code: -7
relaylib_shutdown:start
***relaylib_shutdown:return
RIPSTREAM_DESTROY
inet_sc_connect(): calling httplib_parse_url
inet_sc_connect(): calling sockinit
inet_sc_connect(): calling sock_open: host=wers.org, port=80
inet_sc_connect(): calling httplib_construct_sc_request
inet_sc_connect(): calling socklib_sendall
inet_sc_connect(): calling get_sc_header
RECV req     1 bytes, got     1 bytes
RECV req     1 bytes, got     1 bytes
RECV req     1 bytes, got     1 bytes
```

And it continues...

I am able to rip this URL with Streamripper on Windows XP.

Does anyone have any suggestions? Information?

---

