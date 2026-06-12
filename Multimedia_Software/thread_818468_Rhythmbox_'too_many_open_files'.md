---
title: "Rhythmbox 'too many open files'"
date: 2008-06-04
forum: Multimedia Software
---

### Post by mortalfunk on 2008-06-04
Rhythmbox will only import about half my collection. If I look at the Import Errors I see half my collection listed with:

Failed to create pipe for communicating with child process (Too many open files)

6958 Songs import fine so my collection isn't really that large. Shouldn't basic bugs like this already be worked out?

Ubuntu Hardy 8.04 with default version of Rhythmbox 0.11.5

---

### Post by omega_drh on 2008-06-08
I just wanted to note that I'm experiencing this problem as well. This thread is the only google result for this problem right now. :/

---

### Post by xc3RnbFO8P on 2008-06-08
[http://ohioloco.ubuntuforums.org/showpost.php?p=4360206&postcount=4]("http://ohioloco.ubuntuforums.org/showpost.php?p=4360206&postcount=4")

> 3. Last but not least, if this problem occurs only when you try to view a directory full of music files:

Nautilus (Gnome's file manager) lets the user preview all music files when s/he hovers the mouse on it. However, this may cause a "too many open files" error when the directory has hundreds of music files.

To disable text, music and image previewing (which is both useless and system resource hog in my opinion), you should enter the setting in the Nautilus menu and disable all previews as illustrated in the attachment below:

---

### Post by cariboo on 2008-06-08
I just imported all my mp3's in Rythymbox (about 10,000) had absolutely no problems at all. Could it be that you've got some weird filenames with lots of spaces, comma's and quote marks?

Jim

---

### Post by markbuntu on 2008-06-08
Rythmbox definitely does not like spaces in file names. There is a thread about that around here somewhere.

---

### Post by mortalfunk on 2008-06-10
There are definitely many spaces in my file names. Probably some weird characters since I do appreciate some good world music. Is there a way to crawl through a directory to find these files?  Will I have to remove these files for most of my library to be imported?

I turned off the music preview as mentioned above. It did not correct the problem.

---

### Post by kostkon on 2008-06-10
> **mortalfunk said:**
> There are definitely many spaces in my file names. Probably some weird characters since I do appreciate some good world music. Is there a way to crawl through a directory to find these files?  Will I have to remove these files for most of my library to be imported?

I turned off the music preview as mentioned above. It did not correct the problem.
Definitely, spaces in filenames is not a problem for *Rhythmbox*. Look for non-music files since it does not like them much (except images because it can use them as covers). Also look for any corrupted music files you may have.

---

### Post by omega_drh on 2008-06-10
I'm not sure it's necessarily filenames with spaces, but my rhythmbox definitely does fail to import a ton of files that it can't decode, prior to failing with the "too many files open" error. Specifically, I've got a lot of .ape files, but I don't have an updated gstreamer-ffmpeg build that can decode them. If I check out the file descriptors open for rhythmbox, I see it hits a 1020 before bombing, but almost all of these are pipes ... I think they may be to failed rhythmbox-metadata (or something) processes. I see lots of these processes spawning and ending immediately during rhythmbox startup. If I run rhythmbox in a terminal, I get lots of these lines:
```
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|APE tag demuxer|decoder-application/x-ape (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
```
Digging into this briefly, this occurs, basically, at metadata/rb-metadata-dbus-client.c:236 (at least, on my snapshot of the source), where this is called:
```
res = g_spawn_async_with_pipes (NULL,
                                (char **)argv->pdata,
                                NULL,
                                0,
                                NULL, NULL,
                                &metadata_child,
                                NULL,
                                &metadata_stdout,
                                NULL,
                                &local_error);
```

**Fake edit**: Bah, crap. I've been composing this response in my browser off and on for the past couple days. I did successfully track this down, fixed it, and was building on my machine, only to discover that this bug was just fixed upstream (literally, as of now, this is the last SVN checkin on the file in question). The upstream bug is here: [http://bugzilla.gnome.org/show_bug.cgi?id=534582](http://bugzilla.gnome.org/show_bug.cgi?id=534582) . I don't know exactly how Ubuntu's bug policy works ... but I don't *think* they'd port this change back to Hardy :-/.

---

