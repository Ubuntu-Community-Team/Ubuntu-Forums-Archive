---
title: "Broken gpodder 2.14 update - numberous issues"
date: 2011-04-13
forum: Multimedia Software
---

### Post by kevinlyfellow on 2011-04-13
The last update for gpodder broke it.  I'm running the current LTS and I'm receiving the application from the gpodder ppa.

Here are some of the symptoms,

Right clicking on a new item to download outputs this to the command line
```

Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gpodder/gui.py", line 3965, in on_download_selected_episodes
    self.download_episode_list(episodes)
  File "/usr/lib/pymodules/python2.6/gpodder/gui.py", line 3379, in download_episode_list
    self.mygpo_client.on_download([task.episode])
  File "/usr/lib/pymodules/python2.6/gpodder/my.py", line 296, in on_download
    self._store.save(self._convert_episode(e, 'download') for e in episodes)
  File "/usr/lib/pymodules/python2.6/gpodder/minidb.py", line 104, in save
    self.save(child)
  File "/usr/lib/pymodules/python2.6/gpodder/minidb.py", line 116, in save
    ', '.join(slots), ', '.join('?'*len(slots))), values)
sqlite3.DatabaseError: database disk image is malformed
```

Will not play any item, no errors.

I can drag and drop items, but the "Transfer" button doesn't work.

Upon exit, 
```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gpodder/gui.py", line 3099, in on_gPodder_delete_event
    self.close_gpodder()
  File "/usr/lib/pymodules/python2.6/gpodder/gui.py", line 3123, in close_gpodder
    self.db.close()
  File "/usr/lib/pymodules/python2.6/gpodder/dbsqlite.py", line 131, in close
    cur.execute("VACUUM")
sqlite3.DatabaseError: database disk image is malformed
```

And it freezes there.

Given that I have warnings that say "sqlite3.DatabaseError" I figured it was a problem with the database file.  I went to ~/.config/gpodder and deleted the file database.sqlite.  Starting the application again, the welcome screen had two broken buttons on it.  Once I figured out how to get past that, I subscribed to new podcast to see if the same problems arose and sure enough, the problems were still present.

Does anyone know the source of these problems?  Is it me or are there others with this problem?

---

### Post by kevinlyfellow on 2011-04-13
A little more information

The welcome screen problem, click the first button
```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gpodder/gtkui/interface/welcome.py", line 46, in on_show_example_podcasts
    self.gPodderWelcome.destroy()
AttributeError: 'gPodderWelcome' object has no attribute 'gPodderWelcome'

```

The second button
```

Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/gpodder/gtkui/interface/welcome.py", line 50, in on_setup_my_gpodder
    self.gPodderWelcome.destroy()
AttributeError: 'gPodderWelcome' object has no attribute 'gPodderWelcome'

```

The close button does not work.  Same error as above.

I'm wondering if the latest from gpodder introduces an extra dependency or something that I'm missing.

---

### Post by kevinlyfellow on 2011-04-13
The welcome screen bug has been reported on the redhat bugilla [https://bugzilla.redhat.com/show_bug.cgi?id=650647#c5](https://bugzilla.redhat.com/show_bug.cgi?id=650647#c5)

---

### Post by kevinlyfellow on 2011-04-13
Hmmm... removed all configuration files and ran the program.  Ignored the welcome screen warnings and downloaded an episode of skeptoid and it now works.

Now to figure out what settings I can get back.

---

### Post by kevinlyfellow on 2011-04-13
Fixed it.

It was a a database.  I focused on the database.sqlite file, but I'm not sure if it was that.

I renamed the ~/.config/gpodder directory to gpodder_bak.  Opened up gpodder and all was good.  Even the welcome screen came back alive.  Closed gpodder, copied ~/.config/gpodder_bak/gpodder.conf to the new ~/.config/gpodder and opened gpodder up again.  Then imported my old ompl in the backup directory and it works.  I now have a bunch of orphaned episodes, but I'm happy my gpodder works again.

---

