---
title: "[SOLVED] Gpodder Will Not Sync to iPod 6G Classic in Hardy"
date: 2008-07-19
forum: Multimedia Software
---

### Post by JeremyTheGeek on 2008-07-19
I have been using gPodder for the last few months to catch my podcasts and sync them to my iPod. This was working until today. On one podcast (Buzz Out Loud Ep 769) it would not sync. Confuzzled i checked to see if my gPodder was the current version. It was not so I upgraded to 0.12.0 . The install went smoothly and gPodder pulled all of my new podcasts down. When i went to sync nothing appeared to happen. I tried restarting gpodder as well as deleting .config/gpodder/ and restoring my podcasts from a .opml file i had. After running gpodder from a CLI i was given the folowing errors...

```
germ@Ubuntu:~$ gpodder
/var/lib/python-support/python2.5/gpodder/SimpleGladeApp.py:337: GtkWarning: Global Menu Library(libgnomenu) not found. Fall back to GTK code for handling menu bar. GTK-aqd is intended to provide Global Menusupport from legacy GTK applications. 
  return gtk.glade.XML(self.glade_path, root, domain)
Exception in thread Thread-109:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/var/lib/python-support/python2.5/gpodder/gui.py", line 1705, in sync_to_ipod_thread
    if not device.episode_on_device(episode):
  File "/var/lib/python-support/python2.5/gpodder/sync.py", line 205, in episode_on_device
    return self.__track_on_device(episode)
AttributeError: 'iPodDevice' object has no attribute '_Device__track_on_device'

Exception in thread Thread-110:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/var/lib/python-support/python2.5/gpodder/gui.py", line 1705, in sync_to_ipod_thread
    if not device.episode_on_device(episode):
  File "/var/lib/python-support/python2.5/gpodder/sync.py", line 205, in episode_on_device
    return self.__track_on_device(episode)
AttributeError: 'iPodDevice' object has no attribute '_Device__track_on_device'

germ@Ubuntu:~$ 

```


Any help in solving this problem would be appreciated


    -Germ

---

### Post by JeremyTheGeek on 2008-07-19
Thanks to nikosapi in the #gpodder irc on irc.freenode.net for providing me with these instructions...


1) sudo apt-get remove gpodder

2)  sudo apt-get install subversion python-feedparser python-gpod python-pymad mplayer help2man intltool gettext python-dev imagemagick

3) wget [http://nikosapi.org/gpodder/gpodder-0.12.0-1.tar.bz2](http://nikosapi.org/gpodder/gpodder-0.12.0-1.tar.bz2)

4) tar xvf gpodder-0.12.0-1.tar.bz2

5) cd gpodder-0.12.0-1

6) sudo make install

7) Enjoy!

---

### Post by neekz on 2008-10-02
Thanks, It worked flawlessly! :guitar:

---

