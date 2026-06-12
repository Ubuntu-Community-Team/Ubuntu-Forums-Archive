---
title: "Rhythmbox won't play from daap share"
date: 2012-07-13
forum: Multimedia Software
---

### Post by c-m on 2012-07-13
I've setup a daap share using forked-daapd. I can successfully stream music to all the phones in my house using a simple android app.

The problem I have is that my laptops running 12.04, either can't connect or won't play music from the daap share.

I've tried both Rhythmbox, where I can see the music but it won't play, and Banshee, that just refuses to connect to the share.

---

### Post by Mithryn on 2012-09-05
+1

I'm also having a similar issue.  This has been occurring on multiple machines of mine, across multiple versions of Ubuntu (10.04 through 12.04) and different media players (Amarok, Rhythmbox).  They both complain that a required plugin could not be found and then crash. *Note that they can both view the contents of the DAAP without incident, it only occurs upon a playback attempt.   
The error message is:
"Required plugin could not be found
Python (v2.7) requires to install plugins to play media files of the following type: text/html decoder"

I have done some extensive googling and have come up with a few websites that either suggest that the streaming service has an incorrectly formatted website, that the person attempting to stream is attempting to stream a 'website' and not a stream, and the last one which I have tried to no avail, was to completely purge and reinstall the gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg packages.  Unfortunately, that hasn't worked.  

If anyone has any further information or can offer a solution, I'd be eternally grateful.

---

### Post by Stephen_at on 2013-03-09
Forked daap doesn't seem to work properly with most of Linux media players. Also it doesn't seem to be actively maintained any more.

---

