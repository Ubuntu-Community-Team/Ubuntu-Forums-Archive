---
title: "How does Mythweb/MythVideo transform URL into filepath?"
date: 2013-08-15
forum: Mythbuntu
---

### Post by nhtrader on 2013-08-15
MythTV v0.26.0-220 (BE &FE on same PC)
ubuntu 12.0.4.2 LTS (x86_64)
Accessing Mythweb using webbrowser from same PC
VLC plugin 2.0.8 Twoflower installed
Opera 9.80 (view network traffic using built in developer tools - DragonFly option)
FireFox 23.0 (view network traffic using addon Live HTTP Headers)
Chromium 28.0.1500.71 (view network traffic using built in developer tools)

For testing purposes, authentication is disabled in /etc/apache2/sites-available/mythweb.conf

BTW, /usr/share/mythtv/mythweb/modules/video/stream.php contains a typo which I have corrected.
The misspelled code: 
.          $mime = applicatoin/octet-stream
the corrected code:
.          $mime = application/octet-stream
and while was in there I added the following MIME type:
case 'm4v': (colon)
$mime = 'video/x-m4v'; (semi-colon)
break; (semi-colon)

.
.

I am looking for a flowchart with regards to how the pieces of code within Mythweb fit together.

Specifically, I'm trying learn how Mythweb's MythVideo (section) translates the URL to the actual file location.

 Currently, when a movie is selected in MythVideo, it displays the following URL:

[http://10,10,10,10/mythweb/video/stream?Id=1]("http://localhost/mythweb/video/stream?Id=1")

 This gets passed to the following PHP script: /usr/share/mythtv/mythweb/modules/video/stream.php

Where the URL above is transformed/converted to:

[http://10.10.10.10:6544/Content/GetVideo?Id=1]("http://localhost:6544/Content/GetVideo?Id=1")

 where the PHP line of code readfile([http://]("http://localhost:6544/Content/GetVideo?Id=1")[10.10.10.10]("http://localhost:6544/Content/GetVideo?Id=1")[:6544/Content/GetVideo?Id=1]("http://localhost:6544/Content/GetVideo?Id=1"))  presumably gets the data to send (answer the HTTP request).

 And here is where I am stuck b/c I can't figure out how this URL gets translated. I can't find any reference to "Content/GetVideo" anywhere.

 I am trying to learn how this URL ([http://]("http://localhost:6544/Content/GetVideo?Id=1")[10.10.10.10]("http://localhost:6544/Content/GetVideo?Id=1")[:6544/Content/GetVideo?Id=1]("http://localhost:6544/Content/GetVideo?Id=1")) get transformed into the actual file path:

/var/www/mythweb/data/video/movie_title_indexed_as_001.m4v

What code or scripts are involved to make this conversion possible?
And ultimately, what does the webbrowser see/receive as the response?

  The reason why I'm interested in learning what goes on behind the scenes is b/c I can't stream web optimized *.m4v movies created with handbrake v0.9.9 rev0 to any webbrowser. The response headers state that there is an HTTP/1.0 500 - Internal Server Error. So I'm trying to figure out how to fix the problem.

---

