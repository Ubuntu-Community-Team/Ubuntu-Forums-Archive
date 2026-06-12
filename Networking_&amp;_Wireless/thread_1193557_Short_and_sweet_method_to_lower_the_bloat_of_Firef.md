---
title: "Short and sweet method to lower the bloat of Firefox"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by monsterstack on 2009-06-21
Saw this one posted on Slashdot. Thought I'd repost it in case anyone wishes to make use of it.

If you find that Firefox uses so much memory over time that it becomes almost unusable, then this can help. The solution is to make a temporary filesystem in your RAM and tell Firefox to use that as its cache. So, here's how you do that.

Make a temporary filesystem anywhere you like (your home directory or maybe /tmp or /mnt, if you prefer). Set the size to whatever you feel is appropriate depending on how much RAM you have. I have a gigabyte of RAM, so I set mine to be 100mb. If you have 512mb RAM, then setting it to something smaller is a good idea (50mb or smaller).

```
sudo mount -t tmpfs -o 'size=100M' tmpfs /path/to/mountpoint
```

Now open up Firefox and type "about:config" into the URL bar. Right-click anywhere and add a new string variable, with the title,

```
browser.cache.disk.parent_directory
```

And the string value,

```
/path/to/mountpoint
```

Restart Firefox to start reaping the benefits. A few important things to consider:

[LIST]
[*]As this filesystem uses your RAM and not your hard-disk, it is *very* fast, but like RAM, it will lose all of its data after you switch your computer off. Do not use it as a place to store important files.
[*]Users who open Firefox and leave it on all day will reap the most benefit. If you turn your computer off and on a lot regularly, this method won't bring you much joy.
[*]You'll need to mount the filesystem again the next time you switch your computer on. You can add the mount command to whichever start-up script or settings you may have, if you prefer.
[/LIST]

Firefox has been up and running on my computer for hours now, and it's currently using 120mb of RAM, with several tabs open. Still feels fast and responsive. All in all, a big improvement! I hope this little trick helps others. Enjoy. :)

---

