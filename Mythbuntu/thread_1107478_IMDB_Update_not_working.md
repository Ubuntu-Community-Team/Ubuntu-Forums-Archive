---
title: "IMDB Update not working?"
date: 2009-03-26
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2009-03-26
When I update my movies through IMDB I'm not downloading a cover.

The location that Myth had set for covers to be downloaded to didn't exist, so I created the directory and attempted to download them again.

Still didn't work.

Any ideas?

---

### Post by novellahub on 2009-03-27
Make sure your new folder is writeable and the mythtv user has rights to access it.

```
chmod 775 [folder]
```
```
chown mythtv:mythtv [folder]
```

Replace [folder] about with the actual folder name.

---

### Post by Nobodyspeshul on 2009-03-27
That did it, along with the update .pl script I got from my buddy.

Thanks!

---

### Post by Slate8 on 2009-03-27
This might be in the fixes branch by now but if you want high-res posters you might be interested in [http://www.oneweb.co.uk/mythtv/2009/02/updated-imdbpl-for-getting-hi-res-movie-posters/]("http://www.oneweb.co.uk/mythtv/2009/02/updated-imdbpl-for-getting-hi-res-movie-posters/")

---

