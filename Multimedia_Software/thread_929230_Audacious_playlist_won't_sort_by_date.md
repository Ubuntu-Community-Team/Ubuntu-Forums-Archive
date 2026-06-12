---
title: "Audacious playlist won't sort by date"
date: 2008-09-24
forum: Multimedia Software
---

### Post by hugecolin on 2008-09-24
I'm using Audacious 1.5.1, and the playlist won't sort by date. It'll randomize and sort by title or artist just fine. When sorting by date, apparently the timestamps aren't retrieved properly, and the list ends up in alphabetical order (which I assume is the fallback for files with identical timestamps.)

Any ideas? (Date sort has worked for me in the past, but I'm not sure with which version -- something before 1.4.5.) I'm reading the files from an NFS mount, but that apparently doesn't have anything to do with the problem because it couldn't date-sort files on a local ext3 mount either.

--Colin

More info:
I just ran Audacious as root, and it was broken in the same way.

---

### Post by hugecolin on 2009-01-11
I finally got a chance to look into this, and I found the problem:

In the Audacious source file src/audacious/playlist.c, the function "playlist_compare_date" calls stat() on the two files being compared. However, it's using a hex-escaped URL instead of a plain file path. (For example: "file:///path/to/My%20File" instead of just "/path/to/My File")

I honestly don't know how this ever worked. I'm pretty sure stat() could never parse URL-encoded paths. As a kludgey workaround, I hacked it to decode the URL and strip the protocol prefix ("file://") before stat() is called. While this does work, it's a bad solution for the following reasons:

(a) The URL-encoded path is stored in the PlaylistEntry structs that are passed around, so similar problems could definitely occur elsewhere. (I only checked the date sort.)

(b) Doing all this string processing slows down the date sort substantially.

I'll leave it to someone with a better grasp of the Audacious codebase to un-break this properly.

--Colin

---

