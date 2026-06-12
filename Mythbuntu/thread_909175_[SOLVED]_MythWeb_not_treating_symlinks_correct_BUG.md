---
title: "[SOLVED] MythWeb not treating symlinks correct BUG?"
date: 2008-09-03
forum: Mythbuntu
---

### Post by sebrock on 2008-09-03
have a issue with MythWeb not working with the symlinks in /mythweb/data.

I have separate frontend/backend and mythweb is obviously installed on backend.

As an example I can use video_covers which works perfect on frontend but does not work at all on backend/mytweb.

video_covers is a symlink to /var/Files/200GB/video_covers. When checking the path of files in mythweb GUI (ie the webpage source) the path to the covers seems to be:

[code]
http://htpc.buks.se/data/video_covers//var/Files/200GB/video_covers//0358856.jpg
[code]

This is not the correct path and the symlinks are not treated right. Funny enough if I set the symlink data/video_covers to / (root) the covers all show and work fine. However this is a security flaw I will not accept. So somehow mythweb is not following the symlink correct.

I've checked with people on irc (#mythtv-users, not using mythbuntu) and it works fine for them.

Any clues on how I get mythweb to use the symlinks correct. If you have it all setup and working please paste your apache configuration and all other relevant stuff... this is really annoying me and as far as I can see this must be a bug?

regards.

---

### Post by ian dobson on 2008-09-03
Hi,

Sounds like an absolute/relative path problem. Maybe there's an option in apache/php on how to follow symblic links. 

Sorry I can't be any more exact than that.

Regards
Ian Dobson

---

### Post by sebrock on 2008-09-03
> **ian dobson said:**
> Hi,

Sounds like an absolute/relative path problem. Maybe there's an option in apache/php on how to follow symblic links. 

Sorry I can't be any more exact than that.

Regards
Ian Dobson

Apache and MythWeb are both configured to follow symlinks:

```

    # Allow browsers to follow symlinks that point outside of the web document
    # tree.  This is how we access music, videos, etc.
        Options         FollowSymLinks

```

Is Mythweb working correct for you?

---

### Post by newlinux on 2008-09-03
my /var/www/mythweb/data/video_covers directory is symlinked to a mounted share and works fine in mythweb for me (on two different installs - I have a distributed system, and then one standalone complete system isolated from the rest).

Looking at my mythweb source, the links are all relative - they reference the covers at the relative image link data/video_covers.  In my case it seems to properly parse the the links

My apache.conf is the default from the myth install on ubuntu (I added myth to an ubuntu install) and includes the FollowSymlinks option as does yours.

---

### Post by sebrock on 2008-09-03
Wow so this makes my issue even more complicated... I really dont know what the issue can bere here.

Could you attach your apache.conf/httpd.conf and mythweb.conf?

As I said, setting the symlink to / works because it then adds the symlink from that path creating the correct link. But that is really not a good option security-wise...

By far the most :lolflag:-ish thing Ive ever seen...

---

### Post by newlinux on 2008-09-03
attached

---

### Post by sebrock on 2008-09-08
> **newlinux said:**
> attached

AMazing, nothing differs on our config files except specific parameters as password and so on. Am I really the only one having issues with symlinks and mythweb???

Any clue on what to do? I even tried re-installing it to no avail!

---

### Post by sebrock on 2008-09-13
Well, apparently this was a pretty small nut to crack. As it turns out MythWeb has so create the symlinks itself. Helping and setting the symlinks by your own creates this issue. That is because MythWeb has to use the settings provided in db. So it automatically adds that setting to any (valid) symlink. Thats why setting my symlink to / worked.

ANyhow solved now...

---

