---
title: "Picture-position of non 4:3 videos for 4:3 displays"
date: 2010-02-08
forum: Mythbuntu
---

### Post by tnat on 2010-02-08
Hallo,

first, i'm new to this forum. I've been using MythTV for one year now (0.22 weekly changesets currently).

My setup looks like this:
- frontend width xorg-config for 800x600 with 4:3 aspect.
- a dlp projector with 800x600 also 4:3
- many, many videos with 16:9 or 2,35:1, some with 4:3

4:3 videos or Recordings are looking perfectly with this setup, filling the whole screen.

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;                    &#9474;
&#9474;                    &#9474;
&#9474;                    &#9474;
&#9474;      picture       &#9474;
&#9474;                    &#9474;
&#9474;                    &#9474;
&#9474;                    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

Videos or recordings with an aspect ratio of 16:9 or 2,35:1 are shown in the center of the screen with the corrent aspect ratio.
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;       black        &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;                    &#9474;
&#9474;      picture       &#9474;
&#9474;                    &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;       black        &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

Now my question. Because i like the position of the picture to be as low as possible, i would prefer following alignment:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;                    &#9474;
&#9474;       black        &#9474;
&#9474;                    &#9474;
&#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;                    &#9474;
&#9474;      picture       &#9474;
&#9474;                    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```

Why? My display-size of the projected picture has a width of 2,3m and a height of 1,7m. At this size, its much more comfotable to look not this much up, to the center of the picture.

I know, that the zoom-funktion during playback serve such a function.
Is there a possibility, that mythtv automatically bottoms the picture of non 4:3 videos or recordings, and only those?

---

