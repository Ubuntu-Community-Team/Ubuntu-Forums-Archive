---
title: "Mythweb: ASX and download link broken"
date: 2015-01-22
forum: Mythbuntu
---

### Post by nainsurvolte on 2015-01-22
I seem to have put back together all my mythtv with the fresh install of 14.04 and the import of my database.

Only thing not working are the link between the recorded shows listed in the database (through mythweb) and the files themselves.

I checked for similar issues and did fix a few things.

1) symlink for *recordings* in */usr/share/mythtv/mythweb/data* was pointing to default one. I updated it to point to the folders where all my recordings are
2) I made the changes described here [https://bugs.launchpad.net/mythbuntu/+bug/1316409](https://bugs.launchpad.net/mythbuntu/+bug/1316409)
3) I checked to make sure this one was in line too [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404) (everything fine here).

Despite all of that (and restarting apache2 and mythtv-backend) still nothing.

Is there something else I need to check?

Thanks

---

### Post by nainsurvolte on 2015-01-23
The first recordings have been made. And with the exact same setup (folder holding the recording , same mythconverg database) those recordings are still not accessible with mythweb, but they are with my front end. In addition, the old recordings (from before the re install and restore) are not accessible from the front end.

I use an Openelec Kodi frontend. When I try to read one of those recordings I get a disconnection from the database.

Suggestions where to look?

---

### Post by Kerby_Armand on 2015-01-25
I solved this by enabling the Apache CGI module.

---

### Post by nainsurvolte on 2015-01-25
](*,)

Thanks, I went too fast. Your post got me thinking. Maybe it was too obvious and I missed something in the fix... the symlink I created was *cgi-load* instead of [I]cgi.load

[/I]I hereby declare this problem a code 18...

---

