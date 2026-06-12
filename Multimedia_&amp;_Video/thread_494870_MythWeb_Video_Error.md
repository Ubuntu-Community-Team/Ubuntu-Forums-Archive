---
title: "MythWeb Video Error"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by bengalsfan74 on 2007-07-07
After logging into my mythweb server, I attempt to access the videos that have been recorded.

However, when I hit the video icon, or text, I get the following error message:
Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 16 bytes) in /var/www/<myserver>.com/mythweb/modules/video/handler.php on line 190

I have changed the memory size in my php.ini file from 128MB to 512MB (NEVER should need more than 128, but what the heck), and still get the same problem.

Occassionally, I'd get an error from a different file, but its the same type of error.

Any ideas/suggestions would be helpful.

Feisty Fawn
MythWeb Init.php/Session.php fix
PHP5
Apache2 (also running mono)

---

