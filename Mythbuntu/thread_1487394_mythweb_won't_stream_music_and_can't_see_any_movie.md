---
title: "mythweb won't stream music and can't see any movies"
date: 2010-05-18
forum: Mythbuntu
---

### Post by Meph1st0 on 2010-05-18
Two problems; probably should be in two separate threads but since they're both related to mythweb I figured maybe not.

I'm running Mythbuntu 9.10 32 bit.  This is almost a default install except that I've changed the port that it's running on to 1080.  I've also passprotected my Mythweb install as well using MCC.  Aside from that, I've made almost no changes to the installation.  Well some minor ones mentioned below.

1. I can't get music to stream from mythweb.  Once logged in and I go to the music section and browse my collection and click the play button it opens up windows media player, or iTunes or VLC (whichever one I chose to try) and I enter my username and pasword and then it doesn't work.  With windows media player I get an error that says, "Windows Media Player cannot play the file.  One or more codecs required to play the file could not be found."  With iTunes it appears to try to play the .m3u file but it just doesn't and I don't even get an error message.  With VLC it also appears to try but then it just quits.  I'm seeing an error that says "ts error: cannot peek" in the messages window.

I've read several threads about having to configure the mythweb.conf file in /etc/apache2/sites-enabled folder.  I've edited that file to uncomment the lines regarding authentication for mythweb but that didn't fix it.  (oops, I guess this isn't a perfectly default install)

Is there anything else I can try to get music to stream?

2.  The other problem is I can't get any videos (not recording) to appear in the videos section.  I click "scan collection" and nothing happens.

I've confirmed that there is a symlink at /var/www/mythweb/data for each of the various media types in /var/lib/mythtv and each of them have read permissions accross the board.  I don't see any reason why mythweb wouldn't have permissions to read the /var/lib/mythtv/videos folder.

One thing I noticed is that the symlink /var/www/mythweb/data/video_covers was linked to /var/lib/mythtv/videos when that's where the videos are, but not the video_covers.  I think it should be linked to /var/lib/mythtv/coverart so I fixed that symlink, but I still don't see any videos in mythweb and clicking scan collection.

I don't even care if I can't watch them.  I want to at least see which videos are there, with coverart.

Any help on both these issues would be great.

---

### Post by JQE on 2010-06-08
> **Meph1st0 said:**
> 
1. I can't get music to stream from mythweb.  Once logged in and I go to the music section and browse my collection and click the play button it opens up windows media player, or iTunes or VLC (whichever one I chose to try) and I enter my username and pasword and then it doesn't work.  With windows media player I get an error that says, "Windows Media Player cannot play the file.  One or more codecs required to play the file could not be found."  With iTunes it appears to try to play the .m3u file but it just doesn't and I don't even get an error message.  With VLC it also appears to try but then it just quits.  I'm seeing an error that says "ts error: cannot peek" in the messages window.

I've read several threads about having to configure the mythweb.conf file in /etc/apache2/sites-enabled folder.  I've edited that file to uncomment the lines regarding authentication for mythweb but that didn't fix it.  (oops, I guess this isn't a perfectly default install)



I know this thread is a little old, but i am having the same issue and see no resolution in site. I have searched and tried a lot of different things, with no luck.

Went so far to install a basic Mythbuntu config and see if it works.

For me videos stream and everything works (weather and such) EXCEPT i can't play my MP3 files. The m3u file looks accurate.

The only thing that may be an issue that i can see is that the hostname does not get automatically found. I have tried setting it in apache, and mythweb and in the hosts file with no luck.. I am hoping someone can help? Do i need to run an internal DNS server to get the hosts responding properly? Do i need to re-compile something with mp3 support ?? Please i would really love to get this working, it's the last hitch in my setup...

---

