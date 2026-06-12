---
title: "Clementine Is Inconsistently Showing Cover Art In Notifications and Status Bar"
date: 2016-02-03
forum: Multimedia Software
---

### Post by linux4me on 2016-02-03
I'm using Ubuntu 14.04, and I've been using Clementine for years. I love it; however, I have one niggling little problem with it that I haven't been able to solve. 

I had some albums in my music library that didn't have cover art, so I used Clementine's Cover Manager to fetch the cover art. Now, Cover Manager shows that none of my albums are missing covers. I used Cover Manager to export all the cover art as "albumart.jpg" for all the albums, and then used EasyTag to embed the cover art image for each song (flacs). I added "albumart" as the first entry to Clementine in Preferences -> Music Library -> Automatic Updating -> Preferred album art file names.

The cover art showed up in the Music Library in Clementine by each album, but not in the notification that pops up when a new song starts or in the status bar of Clementine. Those are both showing the default blank CD case even though I have Notifications set to include album art.  In the process of trying to figure this out, I noticed that the cover art didn't show up for the images when I browsed to their folders in Nautilus, either, but deleting the files in ./cache/thumbnails/fail/gnome-thumbnail-factory solved that. 

In case Clementine was also doing some caching that prevented the cover art from showing up in the notifications and status bar, I deleted all the folders/files in .cache/Clementine, restarted Clementine, and then did a full library scan, but I still inconsistently get the cover art in the notifications and status bar. It works for some albums, but not for others. This makes it seem like it's not a setting I'm missing.

In Clementine, I right-clicked a song that wasn't showing cover art, and clicked Edit Track Information. On the Summary Tab, I see the correct cover art, and it shows it is from the embedded image, so it looks like the tags are okay. If it's not a setting or a tag issue, it seems like it's probably a caching issue.

Is there some other cache I need to delete to get the newly added cover art to show up in the notifications and status bar of Clementine?

---

### Post by linux4me on 2016-02-04
I got out the big hammer and purged Clementine using apt-get, then I removed all the files with "clementine" in them from the computer that I could find. Somehow, it still retained my settings. There must be another file in my home folder that does it that I haven't found yet. Anyway, still no joy. The cover art isn't showing up in the notifications or status bar in Clemenine. I'm going to look for that configuration file(s) next. Maybe that's where the settings and cover art info is lingering.

---

### Post by linux4me on 2016-02-04
I discovered a couple of things. The album covers for Clementine are kept in /Home/.config/Clementine/albumcovers and the configuration settings are in /Home/.config/Clementine/Clementine.conf. I missed them when I did my deletions, probably because they're in a hidden file. There are also a couple of database files in there that may be the source of my problem. I guess the next step is to rename that folder and restart Clementine to see if starting from scratch does the trick.

---

### Post by linux4me on 2016-02-04
It may be premature, but I'm going to claim success. My cover art is now showing up in the notifications and the Clementine status bar. My guess is that the databases I found in /Home/.config/Clementine contained some reference to the fact that the covers were not available when the albums were added, and Clementine consequently kept using the default images even after I added cover art. I could test it by switching back to my old configuration files and deleting just the databases, but it seems to be working now and I don't want to tempt fate.

If you're having this issue, here's what I recommend:
[LIST=1]
[*]Make sure Clementine is not running.
[*]Rename your /Home/.config/Clementine folder to something else, like "Clementine-old".
[*]Start Clementine, and go Tools -> Preferences to set all your preferred settings. If you're using a name other than "folder" or "cover" for your album covers, make sure to add that to the list on the Music Library tab.
[*]Save your changes.
[*]When Clementine is finished scanning your music library, go Tools -> Cover Manager and fetch all the covers you're missing, if any.
[/LIST]

It's possible that just deleting the databases in /Home/.config/Clementine would have done the trick, and leaving the Clementine.conf file would avoid re-doing all the settings. If I were doing this over, I'd give that a try.

---

### Post by almalaci on 2016-11-23
Thanks for this,

I had a stubborn album cover that I chose for an album and Clementine kept applying it to a complete different playlist. Now it's deleted successfully!

---

