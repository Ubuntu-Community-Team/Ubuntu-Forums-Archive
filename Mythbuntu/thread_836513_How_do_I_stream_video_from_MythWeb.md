---
title: "How do I stream video from MythWeb?"
date: 2008-06-21
forum: Mythbuntu
---

### Post by QA_manager on 2008-06-21
I have searched pretty hard and haven't found anyone describing the problem I have so...

I have installed MythBuntu 8.04 as a backend only, with the default storage on an NFS share; it works nicely.  Using Mythweb I can schedule recordings, check status, etc.  However, when I look at 'Recorded Programs' and click on the 'ASX Stream' button, it doesn't stream the video.  Firefox downloads 269 bytes of an ASX file, Totem appears with a black screen, and nothing else happens.  After waiting several minutes I click to close Totem and am told that it has stopped responding; I had to force quit.

If I tell Firefox to open it with mplayer, mplayer says it isn't a movie.

I have tried Ubuntu 8.04, Fedora 9, and OS X 10.4; nothing plays a video.

However, if I click 'Direct Download' the video plays just fine after downloading.

The only thing the least bit non-standard about my configuration is that the videos are not stored on the backend, but on an NFS share that the backend mounts at boot time.  I don't think that should cause problems; mounted shares are pretty vanilla, and the files record and download just fine; they just won't stream.

How do I get videos to stream?

---

### Post by Dilligaf on 2008-06-22
Try opening with a different media player, I had this problem with Totem and found that VLC media player works.

Mike

---

### Post by boblablah on 2008-06-26
mine prompts me for credentials, of which any functional ones on the system in question do not work...  i never get streaming to actually start...   any idea?

---

### Post by QA_manager on 2008-06-26
> **Dilligaf said:**
> Try opening with a different media player, I had this problem with Totem and found that VLC media player works.

Mike

Thank you; that works (VLC plays the recording).  It does give me an error dialog - "ts: cannot peek" - is that a bug in VLC?  Despite the error, the video plays just fine.

So why don't Totem and Mplayer work?  Is that a bug in both players, or is there an underlying bug in the Mythweb code?

------------------

boblablah, what OS and media player are you using?  When posting for help it is always a good idea to post the OS and the software you are using, and perhaps also the versions.

---

### Post by jrhaws on 2008-06-30
> **QA_manager said:**
> Thank you; that works (VLC plays the recording).  It does give me an error dialog - "ts: cannot peek" - is that a bug in VLC?  Despite the error, the video plays just fine.

So why don't Totem and Mplayer work?  Is that a bug in both players, or is there an underlying bug in the Mythweb code?

------------------

boblablah, what OS and media player are you using?  When posting for help it is always a good idea to post the OS and the software you are using, and perhaps also the versions.
I am having the same issue as boblablah.  I can download the mpg and VLC plays it fine, but it will not authenticate on the stream.

Mythbuntu 8.04 is my OS (same issue on a Windows box at work).

---

### Post by jlagrone on 2008-06-30
If you have a mythweb password protected, the default uses htdigest.  Currently, most players are not parsing the passwords correctly.  You can change the security to htaccess (but it will be less secure) or I know that the nightly builds of vlc will play the stream, the current stable version may also but I haven't tried it (and it's not the one in the Ubuntu repo last I checked)

---

### Post by nickrout on 2008-06-30
> **QA_manager said:**
> Thank you; that works (VLC plays the recording).  It does give me an error dialog - "ts: cannot peek" - is that a bug in VLC?  Despite the error, the video plays just fine.

So why don't Totem and Mplayer work?  Is that a bug in both players, or is there an underlying bug in the Mythweb code?


I suspect that mplayer needs ot be explicitly told that the asx file is not a media file but a pointer to a media file. That means you probably need to open it with ```
mplayer -playlist
``` rather than just ```
mplayer
```

---

### Post by kainalu on 2008-07-27
I have a similar issue... I cant play it in anything, no vlc, no nothing. What ports does it use? is the mythbuntu team working on a patch? What info can I send to help?


Edit: I also noticed that it forwards to port 80, which is not my standard mythweb port and is blocked by my isp. any way to reroute?

---

### Post by entourage on 2008-07-30
I was also unable to get it to stream or play the ASX stream files because of having a password.

I was using the non-standard port 8081 and had it password protected.  Both of these in conjunction prevented the streams.  I removed the password and changed the port back to 80, then I could do both.

I then tried to go back to port 8081 and was unable to stream either.

This is just an FYI for those trying and failing.  Maybe this is part of the 'experimental' portion of the stream.

---

### Post by Triptol on 2009-11-09
There is a file /etc/mythtv/mythweb-config.php which tells you to remove some remarks so streaming works when you enable authentication.

---

