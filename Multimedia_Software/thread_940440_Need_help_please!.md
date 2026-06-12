---
title: "Need help please!"
date: 2008-10-07
forum: Multimedia Software
---

### Post by ekss on 2008-10-07
i cant play/stream 181.fm on my hardy. 

i tried this [http://ubuntuforums.org/showthread.php?t=258815&highlight=181.fm](http://ubuntuforums.org/showthread.php?t=258815&highlight=181.fm) but still wont play/stream.

anyone please!

---

### Post by eternalnewbee on 2008-10-07
There's a firefox addon named media connectivity. Just type "stream" in the searchbar and scroll down till you find it.
That's how I listen to the bbc...

---

### Post by patrickballeux on 2008-10-07
Hi,

I did it and downloaded the PLS file, double-click on it and it is now playing in my Totem Video player...
(Just found out that clicking on the left links actually start the feed in the browser without downloading the PLS file... and it works)


Are you missing a codec?  Run this:

```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse

```

And what player do you want to use?

---

### Post by ekss on 2008-10-07
> **eternalnewbee said:**
> There's a firefox addon named media connectivity. Just type "stream" in the searchbar and scroll down till you find it.
That's how I listen to the bbc...



> **patrickballeux said:**
> Hi,

I did it and downloaded the PLS file, double-click on it and it is now playing in my Totem Video player...
(Just found out that clicking on the left links actually start the feed in the browser without downloading the PLS file... and it works)


Are you missing a codec?  Run this:

```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse

```

And what player do you want to use?



thanx for your help guys. it works now :)

---

