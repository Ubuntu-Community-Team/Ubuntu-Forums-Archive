---
title: "Gapless AND lossless music on linux - what do you use?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by kko1 on 2008-04-23
I am searching for a practical solution to achieve a **lossless + gapless** listening experience. I haven't come across one, so if you have a **working solution** or a link to one, please do tell.

My criteria:
- The music *must* be stored in a **lossless** format that uses **tags**.
- The files *may* be stored in a **compressed** format.
- The files *may* be stored as **single-track-per-file** OR **album-per-file** (possibly with cuesheets).
- The player *must* be able to **identify and operate with single songs** AS WELL AS **play an album seamlessly** i.e. gaplessly (with the chosen way to store the files).

A bonus criterion:
- I don't care too much about hidden pre-tracks, as I don't have many such CDs, but *if* there is a way to **store all information on a music CD** (so as to be able to restore the equivalent of the "original CD") **in all cases**, this is a bonus. (In other words, if the files act as a complete backup.)

Is there a nice lossless and seamless solution that doesn't involve keeping bit-to-bit backup copies of the original CDs in addition to the extracted music tracks?

*

**Before you reply:** I am on Kubuntu (currently Dapper, soon Hardy), but don't care about what programs to use nor the file format, as long as they work nicely and achieve what I ask for above. I currently use Amarok + single-track FLAC, which, at least with this version, isn't a gapless combination.

---

### Post by eldepeche on 2008-05-14
MPD handles gapless FLAC and MP3 well. MPD is a daemon that runs in the background; it also requires a frontend client. Check out [http://musicpd.org](http://musicpd.org) .

---

### Post by kko1 on 2008-05-17
> **eldepeche said:**
> MPD handles gapless FLAC well.

It does. Thanks. :)

I tried it with the *pygmy* frontend now, I'll try other options when I update to Hardy.

EDIT: Other good solutions to the original question are still welcome in the thread, so I won't mark this as solved yet. Perhaps we can gather more information accessible in the same thread.

---

