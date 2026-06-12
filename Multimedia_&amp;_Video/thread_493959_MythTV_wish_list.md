---
title: "MythTV wish list"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by bignickel on 2007-07-06
I just installed MythTV on my server, in the hopes that I could use it mainly as a media playback machine.  I do really like it, but there are some things I wish it did better, or maybe it already does and I just don't know how to enable these features.

1)  Support for downloaded recordings.  I don't have cable, but I do download some shows via bittorrent.  In my ideal world, Myth would run a torrent client which would scan RSS feeds, automatically download new episodes, and put them in recordings.  There is a plugin called  [torrentocracy]("http://torrentocracy.com/blog/") which seems like exactly what I want, but also seems like abandonware.  I can't get it to compile with Myth 0.20.  There's also  [MythNetTV]("http://www.stillhq.com/mythtv/mythnettv/000006.html") which is being actively developed.  It will take RSS feeds and add them to recordings, but only if it's an actual video file, not a torrent.

2) Have Video Manager update automatically for MythVideo.  This is tied in with #1.  Right now I get shows by keeping a second session with KTorrent running continuously.  I VNC into that session if I need to play with something, but for the most part it grabs stuff I want automatically with RSS feeds.  But since I can't put them in recordings they go into the Media Library.  Then I can watch them with MythVideo, but only if I run the Video Manager program to update the database, and confirm all my deleted shows.

I can't be the only one with these problems.  Has anyone got torrentocracy running, or is there a better solution I just don't know about?

---

### Post by Hendrixski on 2007-08-06
You're not the only one.  I have a problem trying to compile torrentocracy as well. It can't seem to find a inetcomm.h file, because for some reason there isn't one in /usr/include/mythtv.  Perhaps it was discontinued.  :-( If I find a workaround I'll tell you :-)

---

### Post by Hendrixski on 2007-08-08
well, guess what. Torrentocracy uses a library that was deprecated as of mythtv 0.19.  so it hasn't worked for a year or so now.  It's called inetcomms.h and it's been replaced byhttpcomms.h.

If Democracyplayer weren't so prone to crashing I'd say just use that.  There needs to be a torrentocracy substitute. or somebody has to fix torrentocracy and send the patch upstream.  that's on top of my wishlist.

---

### Post by nickgriffiths on 2007-12-07
> **bignickel said:**
> 2) Have Video Manager update automatically for MythVideo.  This is tied in with #1.

[...]

I can't be the only one with these problems.

No, you're not! I am also quite frustrated by having to open Video Manager every time I want to watch a newly downloaded video. I did some searching and found something which may interest you:

[http://www.gossamer-threads.com/lists/mythtv/dev/104294](http://www.gossamer-threads.com/lists/mythtv/dev/104294)

Bear in mind I have yet to try this myself, but from the description it looks like exactly what we are both looking for.

---

### Post by bignickel on 2008-01-09
I've finally had some success turning my myth box into a PVR of downloaded torrents.

1) I have a second session with deluge running in the background.  Deluge scans RSS feeds for shows I watch, and grabs them automatically and dumps them into my recordings directory.

2) I found a script called ragetvgrab which scans TV Rage for the show descriptions and original air dates/times based on their filenames.  You can find it [here]("http://www.jobs-khakis-chicks.com/MythTV/").  It's remarkably effective.

3) I wrote a little script which navigates to the directory, and uses the TV Rage script to query the information for any show newer than 1 day (I do this to avoid hammering TV Rage's servers for information I already have).  It then builds a seek table for each show.  Here's the code:

```
cd /media/server/unsorted
find . -name '*.avi' -mtime -1 -type f -exec ~/mythtv-0.20.2/contrib/ragetvgrab-0.5.pl -import -v {} \;
find . -name '*.avi' -mtime -1 -type f -exec mythcommflag --rebuild -f {} \;
```

4) I have a cron job that runs this script once a day.

5) I manually edited the script and the SQL database for shows that it made some mistakes on, but there weren't many.

---

### Post by Gidon on 2008-05-27
Congrats on your success.  I'm copied your method verbatim and ragetvgrab can find the TV Show Metadata just fine and insert an entry into the myth database.  However, when I navigate to the show in the recordings screen and select it, I get "There is no video file for the recording"  Any idea what's happening here?

---

### Post by bignickel on 2008-05-29
I have an idea... it may be that the filenames all get put into the database with a leading ./ (which is a result of the find statement) and myth barfs on that.

Try running this command but replace PASSWORD with your mysql password.  If it works append it to the end of the script so it runs every day to strip the ./ off of the new entries.

```
mysql -u mythtv -pPASSWORD mythconverg -e "update recorded set basename=replace(basename,'./','')"
```

There's got to a better way to do this.  Ideally a torrent client would download the show, then run this script once on the new file when the torrent completes.  I'm sure there's a really elegant way to do it, and at some point I might put some more time into it.

---

