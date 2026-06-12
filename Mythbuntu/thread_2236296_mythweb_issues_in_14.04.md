---
title: "mythweb issues in 14.04"
date: 2014-07-25
forum: Mythbuntu
---

### Post by jrbless on 2014-07-25
I have a mythbuntu 14.04 machine that is from a clean install and am having issues with mythweb.  The main mythtv computer is used in a backend/frontend configuration downstairs with a separate frontend-only machine that is used upstairs.  On the frontends (both downstairs and upstairs), everything works correctly for watching recordings, videos, and music.  The mythweb interface is where I'm having issues.  There are 3 issues in total, but two of them are very closely related (and are probably the same issue).


[LIST=1]
[*]On the "recorded programs" page, I am unable to watch a video by using the "ASX stream" link.  It returns a 404 not found error.  The URL it is accessing (for one of the recordings) is: [http://192.168.0.20//mythweb/pl/stream/1008/1406287800.asx](http://192.168.0.20//mythweb/pl/stream/1008/1406287800.asx)
[*]On the "recorded programs" page, I am unable to use the "direct download" link.  It returns a 404 not found error.  The URL it is accessing (for the same recording as above) is: [http://192.168.0.20//mythweb/pl/stream/1008/1406287800](http://192.168.0.20//mythweb/pl/stream/1008/1406287800)
[*]On the "videos" screen, none of the cover art displays.  A sample URL for where the images is coming from is "pl/coverart/812_coverart.jpg"
[/LIST]

On the "recorded programs" page, the image for the episode appears just fine.  On the videos screen, I can watch any of the movies just fine from mythweb.  I'm very sure that issues 1 and 2 are the same issue, just being manifested slightly differently.

I'm not sure where to start with these issues.  If anyone can tell me where to start looking, I would be very appreciative.

Thanks in advance,
James

---

### Post by jrbless on 2014-07-27
I found the problem and was able to fix it.  All 3 errors were different manifestations of the same underlying problem - perl scripting was not enabled by default in the install.  Following the instructions here [https://bugs.launchpad.net/mythbuntu/+bug/1316409](https://bugs.launchpad.net/mythbuntu/+bug/1316409) corrected the issue and now the ASX streams, direct downloads, and cover art are now working properly.

---

### Post by neutron68 on 2014-07-30
The ASX stream has not worked in any version of Mythbuntu I've ever used.  This goes back to version 8.04.
Will this procedure work for older versions, such as 12.04?

> To get it working, I needed to make the following changes:

1) sudo ln -s /etc/apache2/mods-available/cgi.load /etc/apache2/mods-enabled/cgi.load
2) In /etc/apache2/mods-available/mime.conf, add:
AddHandler cgi-script .cgi .pl

After these changes and restarting apache2, downloading works just fine.

---

