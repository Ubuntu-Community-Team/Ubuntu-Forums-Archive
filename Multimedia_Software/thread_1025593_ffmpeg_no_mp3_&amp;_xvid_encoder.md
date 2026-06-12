---
title: "ffmpeg no mp3 &amp; xvid encoder ?"
date: 2008-12-30
forum: Multimedia Software
---

### Post by Ofloo on 2008-12-30
How do i enable XviD codec and MP3 codec in ffmpeg, ..

---

### Post by 67GTA on 2008-12-30
Are you using 8.10?

---

### Post by Ofloo on 2008-12-30
Yes i am, .. just to make sure to encode

---

### Post by 67GTA on 2008-12-30
Something weird happened in 8.10. The Medibuntu repo used to have the "full" version of ffmpeg. In 8.10, it is no longer there. It is now in the regular Ubuntu repos, but crippled. You need to enable the multiverse repos, update, and search the package manager for "unstripped". Then install every package with unstripped in the name. This will give ffmpeg back full capabilities.

---

