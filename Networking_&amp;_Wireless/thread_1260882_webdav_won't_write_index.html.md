---
title: "webdav won't write index.html"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by billynoah on 2009-09-08
i have a server running ubuntu 9.04 and webdav enabled. my main client is a MacPro running OS 10.5.8.   i can mount my webdav directory on the OS X desktop, i can read and write files perfectly fine with one exception:

i cannot write "index.html" to the main directory

i CAN write index.html to any subdirectory. i can also write any other file by any other name to the main directory.

when i try to write index.html to the main directroy from the OS X desktop via drag and drop i get this error msg:

"You cannot copy some of these items to the destination because their names are too long or contain invalid characters for the destination. Do you want to skip copying these items and continue copying the other items?"

i am so confused... i can easily scp the index.html file without a problem. i can also send it over with an altered filename like index.ht and subsequently log in via ssh and change it's filename.

all directories are user and group www-data and are readable and writeable.. as is my davlockdb file and directory... though i don't think it's related to the davlockdb because cadaver shows no locks.

oddly, if index.html DOES exist and i try to upload it via find i told that the file exists and do i want to replace it. if i click "replace" then it erases the index.html file on the webdav directory and leaves nothing. no file at all.

i've also tried using cadaver from command line but upon attemping to "PUT" index.html it gives a "404 Not Found" error UNLESS the index.html file already exists in which case it overwrites it properly as one would expect.

i inspected log files after receiving the 404 Not Found error from cadaver and discovered this in /var/log/apache2/access.log

fe70::21d:4fff:fe4b:17d5 - user [08/Sep/2009:03:21:11 -0400] "PUT /webmaster/index.html HTTP/1.1" 404 310 "-" "cadaver/0.22.5 neon/0.26.4"

and in /var/log/apache2/error.log:

[Tue Sep 08 03:21:11 2009] [error] [client fe70::21d:4fff:fe4b:17d5] Negotiation: discovered file(s) matching request: /var/www/website/index.html (None could be negotiated).


in light of this i'm tending to think this problem is server side.

can anyone make heads or tails of this?

---

### Post by billynoah on 2009-09-08
bump.  anyone?

---

