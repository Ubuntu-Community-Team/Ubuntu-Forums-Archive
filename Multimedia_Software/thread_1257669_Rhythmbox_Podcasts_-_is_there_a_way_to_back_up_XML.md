---
title: "Rhythmbox Podcasts - is there a way to back up XML feeds?"
date: 2009-09-04
forum: Multimedia Software
---

### Post by moshimoshi99 on 2009-09-04
Hi there! :D

I like to listen to the radio in general, and BBC programmes in particular. In Rhythmbox, I clicked on Music -> New Podcast Feed, and then I copied and paste the XML link to the podcast.

I have now subscribed to about 20 (!) BBC radio podcasts.

Now, I would like to back up / export my selection of podcasts.

If I format my hard drive or buy a new computer, I will have to subscribe again to each podcast. It'd be nice just to click on "Import podcasts from a file" and get my 20 podcasts again.

I'm talking about a functionality similar to the one in Firefox for Bookmarks. You can back up / export Bookmarks as well as restore / import them when the time comes.

Is there a similar functionality in Rhythmbox?

Thank you for your help! :)

---

### Post by DaithiF on 2009-09-04
Hi,
I don't think you can do this in Rhythmbox.

A couple of suggestions:
1. use a different application for managing podcasts.  gpodder offers several ways of importing and exporting your subscribed feeds.
2. if you are happy to use the command line you can get at the rhythmbox data in order to extract/backup your feeds.  And also to restore them.  Restore might not work in the future if rhythmbox were to change how it stores its information though, so this isn't an ideal solution.  Also, best to close out of Rhythmbox before running these commands, so that you can be sure it has written any in-memory changes to its database file first.
```
sed -n '/entry type="podcast-feed"/,/<\/entry>/p' ~/.local/share/rhythmbox/rhythmdb.xml
```
this will output the xml description of the podcast feeds.  capture the output it in a file like so:
```
sed -n '/entry type="podcast-feed"/,/<\/entry>/p' ~/.local/share/rhythmbox/rhythmdb.xml > ~/mypodcasts.bak
```
If you wanted to restore these to a new rhythmbox install you could edit the rhythmbox file in ~/.local/share/rhythmbox/rhythmdb.xml and paste in the contents of your backup file.
For a more human-readable list of just the titles & urls of your podcasts:
```
sed -n '/entry type="podcast-feed"/,/<\/entry>/p' ~/.local/share/rhythmbox/rhythmdb.xml | grep -E "(<title>|<location>)"

```

---

### Post by moshimoshi99 on 2009-09-09
Dear DaithiF,

Thank you very much for your reply!

I backed up the XML description of my podcasts with the command line that you suggested. Thank you! :)

I may also give gpodder a whirl.

Thanks a lot!

Regards

---

### Post by moshimoshi99 on 2009-09-17
Dear DaithiF,

I've downloaded and installed gpodder. With gpodder, I can export my subscribed feeds. It works fine! 

Thanks for the tip! :)

Regards

---

### Post by furofuro on 2010-12-06
Hi,

there wouldn't by any chance be the option to render the output into OPML format? Meaning, I could just import the podcasts that are locked into rhythmbox unsing gpodder.

And besides, BBC podcasts are among the finest out there.

Thanks

---

### Post by lookslikepat on 2011-02-23
Had the same question, and found this little terminal gem over at [commandlinefu]("http://www.commandlinefu.com/commands/view/5662/creates-podfeeds.txt-a-file-that-lists-the-urls-of-rhythmbox-podcasts-from-the-rhythmdb.xml-file.") that makes a newline separated txt file of all the urls. Better than nothing...

```
grep -A 5 -e podcast-feed ~/.local/share/rhythmbox/rhythmdb.xml | grep -e "<location>" | sed 's: *</*[a-t]*>::g' > ~/PodFeeds.txt
```

Saves the file on your home directory. Tested it in Ubuntu 10.10 - Rhythmbox 0.13.1

---

