---
title: "Previous errors retained with upgrade"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by M4570D0N on 2011-03-03
I have a few issues that are admittedly self induced. I have two linux partitions, one that was running Ubuntu 10.10 and one running Mint 10. I while back I was trying to use the Mint Backup tool to back up /home on my Mint partition, but I made two critical errors. First, I mistakenly selected "preserve structure" rather than creating an archive. Then, I saved it to /home on my Ubuntu 10.10 partition rather than a folder within /home. Long story short, the process failed when the backup maxed out the remaining free space I had on my 10.10 partition, and I realized that it also was overwriting any file/folder in the 10.10 /home which had the same file/folder names. However, because the partition was out of space and stopped, this left many files as blank, 0 byte files.

I thought that installing 11.04 might resolve the issues but it does seem to have changed anything, in that sense. The OS is still functional, albeit very buggy, but I'd like to fix the damaged files. What would be the best way to go about discovering which files/packages need to be fixed/replaced? 

The biggest issue I'm having is with my browser. I'm not sure if the problem is with compiz or a javascript error. As an example, here's what the forum main page looks like:
[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_ubuntu-forums.png[/IMG]]("http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/ubuntu-forums.png")

As you can see, some areas show up, but some text/frames are missing. It's much worse on a few other forums/sites I went to. 

Now that I'm on 11.04, compiz seems crash prone, but I don't know if it's a result of retaining the errors that were already present on 10.10 before the upgrade or new bugs, so I have not filed any bug reports yet.


Here's some of  the output in x-session errors, but I'm not sure that any of it is related.

```

** (<unknown>:1774): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:1774): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

** (<unknown>:1774): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

(<unknown>:1774): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1774): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
** (<unknown>:1774): DEBUG: MaximizeIfBigEnough: Firefox window size doesn't fit

** (<unknown>:1774): WARNING **: bool IconLoader::ProcessGIconTask(IconLoader::IconLoaderTask*): Unable to load icon computerjanitor at size 48

** (<unknown>:1774): WARNING **: bool IconLoader::ProcessGIconTask(IconLoader::IconLoaderTask*): Unable to load icon stock_line_in at size 48

** (<unknown>:1774): WARNING **: bool IconLoader::ProcessGIconTask(IconLoader::IconLoaderTask*): Unable to load icon gnome-volume-control at size 48

(<unknown>:1774): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(<unknown>:1774): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/applications.png: Error opening file: No such file or directory

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/files.png: Error opening file: No such file or directory

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/applications.png: Error opening file: No such file or directory

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/files.png: Error opening file: No such file or directory
** (<unknown>:1774): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/applications.png: Error opening file: No such file or directory

** (<unknown>:1774): WARNING **: static void IconLoader::LoadContentsReady(GObject*, GAsyncResult*, IconLoader::IconLoaderTask*): Unable to load contents of /usr/share/unity/files.png: Error opening file: No such file or directory

(nautilus:11030): GLib-GIO-CRITICAL **: g_bus_unwatch_name: assertion `watcher_id > 0' failed

(nautilus:1783): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** (<unknown>:1774): DEBUG: MaximizeIfBigEnough: Nautilus window size doesn't fit

(nautilus:1783): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (<unknown>:1774): DEBUG: MaximizeIfBigEnough: Gedit window size doesn't fit

```

---

### Post by cariboo on 2011-03-03
In a lot of cases removing the configuration files in your home directory will solve many problems, especially in an upgrade situation.

---

### Post by M4570D0N on 2011-03-04
Thank you for the prompt reply. Unfortunately, this did not resolve the issue. I'm also having issues with window borders/menus not showing up. If I edit anything in compiz configuration manager, it crashed unity. I couldn't get the terminal to allow me to type anything until I was able to disable the window transparency, so that's apparently an issue as well.

---

### Post by dino99 on 2011-03-04
try making some cleanings:

sudo rm /var/cache/apt/archives/*

into synaptic:
- deselect all non genuine ubuntu repo (ppa, third parties)
- update

into a terminal:
- sudo apt-get install -f
- sudo dpkg --configure -a

For deeper cleanings, you can install & use bleachbit & gconf-cleaner & gtkorphan

---

### Post by cariboo on 2011-03-04
> **dino99 said:**
> try making some cleanings:

sudo rm /var/cache/apt/archives/*

into synaptic:
- deselect all non genuine ubuntu repo (ppa, third parties)
- update

into a terminal:
- sudo apt-get install -f
- sudo dpkg --configure -a

For deeper cleanings, you can install & use bleachbit & gconf-cleaner & gtkorphan

sudo apt-get clean, does the same job removing cached packages from the archive, and it's easier to type :) But that won't solve the op's problem. 

@M4570D0N have you tried creating another user to see if the problems still exists?

---

### Post by M4570D0N on 2011-03-05
> **cariboo907 said:**
> sudo apt-get clean, does the same job removing cached packages from the archive, and it's easier to type :) But that won't solve the op's problem. 

@M4570D0N have you tried creating another user to see if the problems still exists?

I had not, but I have now, and unfortunately, it still persists. However, I gained my window borders back. I guess I changed something in compiz that it didnt like. Granted, when I first booted into the new user, it stalled after logging in and I got a message saying compiz crashed. I had to drop down ctrl+alt+f1 style and restart gdm and it loaded correctly. It seems though, that if I make any change whatsoever from the compizconfig settings manager, even just clicking the box to enable jpeg under image loading, my window borders disappear, and compiz/unity crash. My cursor still responds but nothing else does if I click on it. I'm really at a loss now for what is causing the initial issues though, or how to trouble shoot it. I might just back up my personal files and do a clean install.

---

### Post by cariboo on 2011-03-05
I use docky with a few apps including the terminal for just what you are experiencing. That way if compiz or unity crashes, I can still open a terminal and type:

```
unity --reset
```

---

