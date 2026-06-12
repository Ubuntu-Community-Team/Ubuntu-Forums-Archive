---
title: "Firefox closes when going to youtube.com"
date: 2009-06-02
forum: Multimedia Software
---

### Post by The Funkbomb on 2009-06-02
So, I had an issue with some flash locking up firefox.

I went into the IRC chan and it was suggested that I do three commands.

1.  Remove everything flash.

2.  Download and untar the Flash 10.0 22r plugin.

3.  Move the plugin to the proper folder.  I think it was usr/lib/mozilla/plugins.

Now, instead of locking up firefox, even if I go to Youtube.com, it just closes firefox out.  Complete crash.  No more grayed out screen.

Here is the weird part.  If I do a search for a video and go directly to the video's youtube page through google, it works fine.

Hulu.com also crashes FF.

How do I fix this?

---

### Post by pastalavista on 2009-06-02
Mine was also acting like that for a while until I removed flashplugin-nonfree and replaced it with adobe-flashplugin. I didn't mind agreeing to their EULA at all because even Windows users have to.

I also installed it via the repositories. That way it gets updated.

---

### Post by The Funkbomb on 2009-06-02
I have tried both the -nonfree and the new 10.0 r22 plugin.

With the -nonfree, some videos just won't load.  NPviewer.bin eats up my CPU and crashes firefox.

With the 10.0 r22 plugin, just going to Youtube.com closes the browser.

It's weird and I can't win either way.

---

### Post by psyke83 on 2009-06-03
> **The Funkbomb said:**
> So, I had an issue with some flash locking up firefox.

I went into the IRC chan and it was suggested that I do three commands.

1.  Remove everything flash.

2.  Download and untar the Flash 10.0 22r plugin.

3.  Move the plugin to the proper folder.  I think it was usr/lib/mozilla/plugins.

Now, instead of locking up firefox, even if I go to Youtube.com, it just closes firefox out.  Complete crash.  No more grayed out screen.

Here is the weird part.  If I do a search for a video and go directly to the video's youtube page through google, it works fine.

Hulu.com also crashes FF.

How do I fix this?

The problem is that you are using the libflashsupport library which causes instability when navigating Flash pages. See bug [bug #192888]("https://code.launchpad.net/bugs/192888").

Another serious problem - don't install the Flash plugin manually, as it  causes far too much trouble. Always use the official packages so that files are always placed in the appropriate places (and updates work correctly, too), or else you will suffer the consequences later (when for example, you have two or three different versions of Flash in various folders that are conflicting).

First, find the locations where the plugin is installed:
```
$ sudo updatedb
$ locate libflashplayer.so
```

Delete all instances of libflashplayer.so file that you find.

Secondly, find the libflashsupport.so file:
```
$ locate libflashsupport.so
```

Delete all traces of the libflashsupport.so file as well.

Finally, ensure no open-source Flash packages are installed, and install the appropriate Flash package:
```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree-extrasound
$ sudo apt-get install flashplugin-nonfree
```

Restart Firefox for changes to take effect.

---

### Post by The Funkbomb on 2009-06-03
I fixed it.  I had to install flash into /usr/lib/firefox-3.0.10/plugins instead of /usr/lib/firefox/plugins.

---

### Post by psyke83 on 2009-06-03
> **The Funkbomb said:**
> I fixed it.  I had to install flash into /usr/lib/firefox-3.0.10/plugins instead of /usr/lib/firefox/plugins.

Will you remember to move the plugin when Firefox 3.0.11 is released, though? This is why you should use the package.

---

### Post by The Funkbomb on 2009-06-03
I've installed the package several times.  It doesn't work.

---

