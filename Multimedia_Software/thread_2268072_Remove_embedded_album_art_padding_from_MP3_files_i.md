---
title: "Remove embedded album art padding from MP3 files in mass"
date: 2015-03-05
forum: Multimedia Software
---

### Post by nekoc4se on 2015-03-05
I only know how to remove the embedded artwork and padding from mp3's by removing all ID3 tags. However I have to re-tag the album's files. Doing this to my entire music catalog would take me months. So is there a way to remove the padding from my entire catalog at once? I have used countless programs(easytag,puddletag etc.) and they all seem to remove the embedded album art but not the padding. I have also tried the command line program "eyed3" with the same result as the UI programs.

Results:

album size without any ID3 tags: 84.9 MB

album size with ID3 tags (no embedded art): 84.9 MB

album size with 1MB embedded image per song: 95.9 MB

album size with embedded album art removed: 95.9 MB

---

### Post by andrew.46 on 2015-03-06
Perhaps have a look at this eyeD3 option:

```

  --max-padding NUM_BYTES
                        Shrink file if tag padding (unused space) exceeds the
                        given number of bytes. [B][COLOR="#FF0000"](Useful e.g. after removal of
                        large cover art.)[/COLOR][/B] Default is 64 KiB, file will be
                        rewritten with default padding (1 KiB) or max padding,
                        whichever is smaller.

```

---

### Post by nekoc4se on 2015-03-07
> **andrew.46 said:**
> Perhaps have a look at this eyeD3 option:

```

  --max-padding NUM_BYTES
                        Shrink file if tag padding (unused space) exceeds the
                        given number of bytes. [B][COLOR=#FF0000](Useful e.g. after removal of
                        large cover art.)[/COLOR][/B] Default is 64 KiB, file will be
                        rewritten with default padding (1 KiB) or max padding,
                        whichever is smaller.

```

i ran this **eyeD3 --remove-images --max-padding NUM_BYTES**

and got this [B]eyeD3: error: no such option: --max-padding
[/B]
this is the version **eyeD3 0.6.18**

---

### Post by andrew.46 on 2015-03-07
I suspect you would need to replace *NUM_BYTES* with a numerical value :). And certainly it looks like you will need a newer version of eyeD3, latest is 0.7.5.

---

### Post by nekoc4se on 2015-03-07
> **andrew.46 said:**
> I suspect you would need to replace *NUM_BYTES* with a numerical value :). And certainly it looks like you will need a newer version of eyeD3, latest is 0.7.5.

I'm new to linux so it took me a good 5 hours just to install the latest version of eyeD3. Anyways it worked! Padding is gone and the ID3 tags are still there. Thanks for pointing me in the right direction.

```
eyeD3 --remove-all-images --max-padding 1
```

---

### Post by andrew.46 on 2015-03-07
Good to hear that the issue is resolved :).

---

