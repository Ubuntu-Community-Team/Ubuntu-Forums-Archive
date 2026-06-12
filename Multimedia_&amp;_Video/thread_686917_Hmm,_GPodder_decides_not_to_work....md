---
title: "Hmm, GPodder decides not to work..."
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by SZF2001 on 2008-02-03
It's weird. It was working just fine for a few days and now it refuses to stay open. It will open up in it's GUI but then decide to close out.

I used a terminal, here's the output (still closes too):

```
coleman@ubuntu:~$ gpodder
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 148, in <module>
    sys.exit( main())
  File "/usr/bin/gpodder", line 144, in main
    gui.main()
  File "/var/lib/python-support/python2.5/gpodder/gui.py", line 2222, in main
    gPodder().run()
  File "/var/lib/python-support/python2.5/gpodder/gui.py", line 77, in __init__
    SimpleGladeApp.SimpleGladeApp.__init__( self, path, root, domain, **kwargs)
  File "/var/lib/python-support/python2.5/gpodder/SimpleGladeApp.py", line 110, in __init__
    self.new()
  File "/var/lib/python-support/python2.5/gpodder/gui.py", line 270, in new
    self.channels = load_channels( load_items = False, offline = True)
  File "/var/lib/python-support/python2.5/gpodder/libpodcasts.py", line 773, in load_channels
    podcastChannel.clear_cache(urls_to_keep)
  File "/var/lib/python-support/python2.5/gpodder/libpodcasts.py", line 111, in clear_cache
    for url in cls.storage.keys():
  File "/usr/lib/python2.5/shelve.py", line 92, in keys
    return self.dict.keys()
  File "bsddb/__init__.py", line 252, in keys
  File "bsddb/dbutils.py", line 62, in DeadlockWrap
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')

```

---

### Post by jpeach on 2008-05-28
I am having the same problem after an upgrade to hardy.  Have you resolved the issue?

---

### Post by SZF2001 on 2008-05-29
I fixed it by switching to PClinuxOS.

---

### Post by Gallienus on 2008-05-29
I'm getting this problem too. I did some updates this morning, then used GPodder successfully a few times before the problem started, so I don't know if the trouble is related to the updates or not. I've only been using GPodder for a couple of days, so perhaps the program is just unstable? A pity, it seemed like a good program.

---

### Post by yo_pandabear on 2008-06-07
Almost same story here, however gPodder seems to never load or it loads and closes in a flash.

"Going Linux" is a great podcast for me.

---

### Post by jpeach on 2008-06-07
yo_pandabear

I was able to get things working again by deleting the configuration files.  One of the databases had been corrupted and that was causing it to hang or crash.  To purge the configurations, issue the following command.  You will loose all your settings!!!  But you can always recreate them

```
rm -rf ~/.config/gpodder
```

---

### Post by yo_pandabear on 2008-06-07
jpeach:

Now this seems to work.  Thanks-Thanks-Thanks

---

### Post by Gallienus on 2008-06-07
Yes, that worked for me too. :) Thanks, jpeach.

---

### Post by Sukarn on 2008-06-08
Sorry that I missed this thread earlier.

I had posted this same solution in some other thread some time back.

Run this command instead of the one mentioned above.

```
rm ~/.config/gpodder/feedcache.db
```

The command given by jpeach deletes all your gpodder configuration including the list of podcasts. This one just deletes the cache, which seems to do the job for me.

---

### Post by bakuzen on 2008-06-12
I did something a little less drastic. Go into your home folder then rename the .config/gpodder folder. Run gpodder. This will result in a new .config/gpodder folder being created. Copy the files in your original folder into the new folder skipping the three files that are already there. That should allow you to keep your settings.

---

### Post by Sukarn on 2008-06-13
> **bakuzen said:**
> I did something a little less drastic. Go into your home folder then rename the .config/gpodder folder. Run gpodder. This will result in a new .config/gpodder folder being created. Copy the files in your original folder into the new folder skipping the three files that are already there. That should allow you to keep your settings.

See my post above. That is definitely less drastic, easier and faster to do than to first rename it, then run the application, then quit the application and move the configurations, making sure than you do not overwrite any files in the process.

The method I gave earlier requires the deletion of only one file, and that file is safe to delete because it only holds a cache of all your podcast feeds. When you delete this file and run gPodder, it downloads the podcast feeds again (something which is done everytime gPodder starts) and then you're good to go.

---

### Post by inyoka on 2008-06-27
I had this same error message and Sukarn's fix worked perfectly.  Its definitely the least troublesome answer and I didn't loose anything.

Thanks Sukarn.

---

