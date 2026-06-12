---
title: "Album art trouble"
date: 2008-10-23
forum: Multimedia Software
---

### Post by dbbolton on 2008-10-23
I am having trouble to get my album artwork to show up in my MP3 player (iRiver Clix). I added photos to a few songs using Easy Tag, then saved them to my my player. But when I play those files, the album artwork is a completely screwed up image- random colors and shapes everywhere. I am using JPGs of various sizes and qualities as the artworks, all of them under 300x300 pixels and less than 10KB file size.

There was one album that had the artworked automatically integrated into it when I downloaded it, and it showed up fine on the MP3 player, so I know there is nothing wrong with it.

---

### Post by nikosm on 2009-04-03
Hi dbbolton,

In another forum someone suggested that non-standard JPGs might be problematic, he says you shouldn't use progressive or optimized but only standard. You can convert an optimized JPG to a standard using imagemagick:

```
convert input.jpg -interlace none output.jpg
```

I haven't tried this yet. I hope it helps.

Nikos

---

