---
title: "MythTV and UPnP"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by jimbolaya on 2006-12-02
Hello all,

I have two mythtv boxes, one is a backend and the other is a backend/frontend.  They work very well together.  I've been dying to have a UPnP AV server running with all my MythTV stuff being served.  I've gotten tantalizingly close, but I can't seem to figure out the last few bits.

I've been trying to test this all out with both Nero ShowTime Essentials and an OmniFi DMS-1.  I can see the server and I can browse all my music and video recordings (just the NUV files however) but when I try to play them, I have problems.

With ShowTime the music will show up correctly when listed, but when I copy it to the "playlist", it turns into a URL.  The URL loads the file fine when I point a regular browser to it, but ShowTime just sits there and becomes unresponsive and I have to kill it with the "End this program now" dialog.  I did a tcpdump to watch the traffic there was a big burst at the beginning which tapers off to a couple packets a minute.  It looks like most of the packets are from ShowTime to the server.

The OmniFi will also browse the music (it doesn't play videos, but it will browse the entries), but says "Track was not found, may have been moved" when I try to play an audio track.  The packets are much more evenly distributed between the server and the OmniFi.

Additionally, I would love to be able to serve out my existing video collection, saved movies and the like.  Those don't show up at all, just the music and recorded programs.

Is there some setting somewhere that I'm missing?  I didn't see any explicit configuration for the UPnP stuff.

Thanks
James Klaas

---

### Post by superm1 on 2006-12-03
Well - the master backend - is it the backend/frontend box?  There was unfortunately a packaging bug.  For Upnp to work, the master backend will need to have the frontend and backend packages installed.  I'm not sure if this is what your hitting on though.

---

### Post by jimbolaya on 2006-12-04
I did see that, thanks.  It was rather challenging to find.

The master does have the frontend packages on it as well.  Do I need to be running a frontend on my master backend?  Is there maybe some confusion in the UPnP because I'm running two servers?

I had changed the path to my music when I did my upgrades, but I corrected them and was able to find them on my frontend.  I also ran the frontend on my master backend to correct the path, but I'm not sure if that helped any.  Is there a table entry somewhere I can correct for this?

James

---

### Post by superm1 on 2006-12-04
Just the "packages" for the frontend software have to be installed on the backend to get this fix.  

You may want to edit /etc/default/mythtv-backend on both backends.

Replace #ARGS="" with ARGS="-v important,general,upnp" and restart the backend on each.  You will now get logging in /var/log/mythtv/mythbackend.log that you should be able to debug as you connect to find out which one actually runs the UPNP (if only one does) and hopefully where things are going south.

---

### Post by jimbolaya on 2006-12-06
OK, it looks like the master backend is the only one running UPnP:

2006-12-06 14:10:18.477 UPnp::UPnp:Begin
2006-12-06 14:10:18.477 UPnp::UPnp:Starting TaskQueue
2006-12-06 14:10:18.478 UPnp::UPnp:Loading UPnp Description
2006-12-06 14:10:18.504 UPnp::UPnp:Starting SSDP Thread
2006-12-06 14:10:18.505 UPnp::UPnp:Adding Context Listener
2006-12-06 14:10:18.505 UPnp::UPnp:End
2006-12-06 14:10:18.505 Main::Registering UPnpCDSTv Extension
2006-12-06 14:10:18.505 Main::Registering UPnpCDSMusic Extension

Here's the part of my log that I think is relavent:

I open up the web page:

2006-12-06 14:12:56.016 MainServer::HandleAnnounce Monitor
2006-12-06 14:12:56.016 adding: dvrsrvr as a client (events: 0)
2006-12-06 14:13:05.178 MainServer::HandleAnnounce Monitor
2006-12-06 14:13:05.178 adding: dvrsrvr as a client (events: 0)
2006-12-06 14:13:05.200 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=16
2006-12-06 14:13:05.570 HttpWorkerThread::ProcessWork:End( 1149274448 )

I try to play a file from my OmniFi:

2006-12-06 14:15:43.434 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=15
2006-12-06 14:15:43.452 HttpWorkerThread::ProcessWork:End( 1149274448 )
2006-12-06 14:15:47.680 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=15
2006-12-06 14:15:47.700 HttpWorkerThread::ProcessWork:End( 1149274448 )
2006-12-06 14:15:51.461 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=15
2006-12-06 14:15:51.480 HttpWorkerThread::ProcessWork:End( 1149274448 )
2006-12-06 14:16:01.372 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=15
2006-12-06 14:16:01.391 HttpWorkerThread::ProcessWork:End( 1149274448 )

I open up the web page again:

2006-12-06 14:19:52.326 MainServer::HandleAnnounce Monitor
2006-12-06 14:19:52.326 adding: dvrsrvr as a client (events: 0)
2006-12-06 14:19:52.330 HttpWorkerThread::ProcessWork:Begin( 1149274448 ) socket=17
2006-12-06 14:19:52.542 HttpWorkerThread::ProcessWork:End( 1149274448 )


I guess I don't see anything informative here except that access to the web server was attempted four times.  Should I add some more "v"s to increase the verbosity?

James

---

### Post by superm1 on 2006-12-06
Well I think you have hit the limit of debugging I can help with here.  I personally haven't tried the UPNP stuff.  I don't have a windows machine to try nero on :)

I think its time I steer you over in the direction of the mythtv mailing list and mythtv channel on IRC, #mythtv-users (as I expect that very few others have tried this as well on ubuntu- and if they have your luck would probably be them not browsing the forums :-?)

---

### Post by jimbolaya on 2006-12-06
Thanks, I wasn't entirely aware how to debug this.  I'll see what I can find out on other lists.

---

### Post by superm1 on 2006-12-06
I should mention though - If and when you solve this, please post back your solution.  I'll add it to the wiki page and other users who search these forums will definitely benefit.

---

### Post by ifross on 2007-12-04
Ive got the upnp up and running if you still have problems... I think the missing files may be something to do with the fact you have two backends... If you have the data on one (say music) then for some reason when your upnp device tries to access the data, it tries to get it on the other backend to which the data is stored on. To get the videos to show up I had to run the mythfrontend from my backend ( i have backend and frontend on seperate machines, but the backend has the frontend installed).

You then go into setup > video setup (or something) and it should find your videos if you have the correct directory set up then your device should be able to find it.

As I said Ive got it working, but I may be just plain wrong. I need to know more about which machines  hold what data etc. before I can really get whats going on.


Edit. Didnt see the date, its really old and so probs not relevant anymore. Sorry for ressurecting this thread.

---

