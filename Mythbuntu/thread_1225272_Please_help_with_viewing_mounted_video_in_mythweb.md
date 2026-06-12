---
title: "Please help with viewing mounted video in mythweb"
date: 2009-07-28
forum: Mythbuntu
---

### Post by kevins7189 on 2009-07-28
***Was able to find the correct httpd.conf setttings for this to work, new problem with uPNP***

I can't seem to figure out what the secret is to be able to get mythweb to be able to display videos from mounted servers. I currently have my Videostartupdir being /mnt/storage/mythtv, in there I have a TV1 dir, which has videos on the server, and two more dirs, movies and tv2, which are mounted from windows shares. When myth scans these dirs, it sees all the videos in the list, but when I try to play a video from the mounted dirs, it displays no video.  There is no errors in the httpd error_log, and in access log.
 I've tried uid/gid/filemode/dirmode switches to no avail. The videos play fine in mplayer and what not, just mythweb/upnp refuses to play them.
 any help appreciated.
 




     to be more specific, this issue only occurs in mythweb, I can view mounted videos on frontend on the same machine as backend OK, just not through mythweb or through upnp.


Here is my setup
Videostartupdir - /mnt/storage/mythTV
/mnt/storage/mythTV/TV (local)
                                TV2 (share)
                               Movies (share)
/usr/share/mythweb/data/videos is a symlink to /mnt/storage/mythTV (created by mythweb)



when I go to mythweb, and pick a video from the TV2 dir in the video browse list, the initial folder to the video points here
[http://server:6969/mythweb/video?path=%2Fmnt%2Fstorage%2FmythTV%2FTV2%2Fcaprica%2F](http://server:6969/mythweb/video?path=%2Fmnt%2Fstorage%2FmythTV%2FTV2%2Fcaprica%2F)


when I get to the video link, the link is this
[http://server:6969/mythweb/data/video/TV2/caprica/caprica-xvid.avi](http://server:6969/mythweb/data/video/TV2/caprica/caprica-xvid.avi)


here is what the httpd log says
"GET /mythweb/video/imdb?action=metadata&id=68615 HTTP/1.1" 200
 331 "http://server:6969/mythweb/video?path=%2Fmnt%2Fstorage%2FmythTV%2FTV2%2Fcaprica
%2F" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.1.1) Gecko/20090715 Firefox/3.5.1"

"GET /mythweb/data/video/TV2/caprica/caprica-xvi
d.avi HTTP/1.1" 206 576475136 "-" "VLC media player - version 1.0.0 Goldeneye - (c) 1996-2009 the VideoLAN tea
m"


i've tried symlinks in /usr/share/mythweb/data/ to point to the files with no avail.  I've tried having files owned by myth user/apache/777, etc no difference.
Everything in TV (local) plays fine, just nothing in the mounts.


any help appreciated, this is about the last thing I need to get working on my setup!

---

### Post by newlinux on 2009-07-28
I don't know if this is a typo or not, but my mythweb vidoes directory is:

/usr/share/mythtv/mythweb/data/video
not
/usr/share/mythweb/data/videos

My video directory is symlinked to a network share as well. In mythweb, my links look similar to yours, given we have different symlinks and mount points.

Maybe the problem is with the application/plugin you are trying to play the file with. Have you tried simply saving the file (right click, save...). Do you have password protection enabled?

---

### Post by kevins7189 on 2009-07-28
thanks for replying, my mythtv is definately running from /usr/share/mythtv
in mythweb.conf I have 

Alias /mythweb/ "/usr/share/mythweb/"
<Directory "/usr/share/mythweb">

I'm guessing it wouldn't play anything if something like that was wrong, not just the files in the mounted dirs.  But I'm so confused right now anything is possible I guess.

---

### Post by newlinux on 2009-07-28
have you tried downloading the file as I mentioned in my previous post?

---

### Post by kevins7189 on 2009-07-28
sorry I did not answer that question, yes I have.  Downloads a 0 byte filename.

---

### Post by kevins7189 on 2009-07-29
finally got it figured out, the problem was in apache and not mythweb.  Learn something new every day
in httpd.conf, these need to be set to off for access to mounted dirs

EnableMMAP Off
EnableSendfile Off

---

### Post by kevins7189 on 2009-07-29
I seem to have the same basic problem in uPnP connections as well, everything plays fine from the local dir but not from the mounted dirs again.  This is occurring on the backend machine and others (Boxee, xbox, etc).
Still works in mythweb though.

Any ideas what settings may be controlling/denying this?

---

### Post by newlinux on 2009-07-29
> **kevins7189 said:**
> finally got it figured out, the problem was in apache and not mythweb.  Learn something new every day
in httpd.conf, these need to be set to off for access to mounted dirs

EnableMMAP Off
EnableSendfile Off

I don't have either of those options set at all (in fact my httpd.conf is blank) and it works fine for me... My master backend/apache server is still on Hardy though, so maybe there are differences. Glad you got it working!

---

### Post by kevins7189 on 2009-07-29
thanks now if I could only get uPnp working with the mounted filesystems, and LiveTV to stop screwing up when I change channels, things will be golden

---

### Post by newlinux on 2009-07-29
wish I could help, but I don't use myth's UPnP server for videos (I have XBMC and my other UPnP clients set up to look directly at the network shares). I do use it for recordings with my Ziova z500 and it works fine for recordings on any of my backends).

Maybe there is something going on with your sharing. Are you using NFS, or SAMBA/CIFS, or SSHFS? I'm just grasping at straws here...

---

