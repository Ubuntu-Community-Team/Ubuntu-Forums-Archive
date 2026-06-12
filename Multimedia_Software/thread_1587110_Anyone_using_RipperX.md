---
title: "Anyone using RipperX"
date: 2010-10-03
forum: Multimedia Software
---

### Post by mapman88 on 2010-10-03
Hi, I am using RipperX in Ubuntu 10.04. When I rip a CD I am encoding the tracks with Lame as mp3 files to a folder named after the album. In RipperX config, I have checked "Create a playlist.m3u file". Everything works fine, but the playlist.m3u file only includes the first nine tracks of any album (CD). Open Ripper, click Config, In the Files tab it lists %# = Track NO., but does not allow for editing. Should this be %## = Track No., for when the album contains more than nine tracks. Wen I import these albums into Guayadeque, I only get tracks 1-9 in each album. Any tracks above nine, in any album are imported to Guayadeque with no album associated to it which creates a mess.

I am wondering (1) if I am correct in my assumptionabout the playlist.m3u files, and (2) if so, is there a script I could run to fix my playlist.m3u file in each album folder file, or (3) if I am wrong, anyone else been there done that?

thanks,

---

### Post by mapman88 on 2010-10-03
screenshot1 = fifteen mp3 files ripped from CD
screenshot2 = Guayadeque library showing only 9 mp3 files from CD
screenshot3 = playlist.m3u created by RipperX during rip
screenshot4 = RipperX/Config/Files shows %# = Track No. Should it be %## for over nine tracks?

---

### Post by cchhrriiss121212 on 2010-10-03
I tried copying your settings but I have no such problems with track numbering or the m3u. The %# is just there as a legend to allow you to name your files differently, I doubt this is the problem.

For example, this is what I use: 
filename format string: %# - %s

Are you using CDDB to label your tracks?

---

### Post by mapman88 on 2010-10-03
> **cchhrriiss121212 said:**
> I tried copying your settings but I have no such problems with track numbering or the m3u. The %# is just there as a legend to allow you to name your files differently, I doubt this is the problem.

For example, this is what I use: 
filename format string: %# - %s

Are you using CDDB to label your tracks?

Yes, I am using CDDB. CDDB lists all of the tracks, and all of the tracks are encoded to .mp3 in the album folder. The playlist.m3u only lists nine of the tracks.
 I never changed the filename format string when I started ripping cd's - , it was %a - %s. I have changed it to %# - %a - %s and I am ripping The Commitments, which has fourteen tracks. oops - done ripping - same old nine tracks in playlist.m3u

---

### Post by mapman88 on 2010-10-03
> **mapman88 said:**
> Yes, I am using CDDB. CDDB lists all of the tracks, and all of the tracks are encoded to .mp3 in the album folder. The playlist.m3u only lists nine of the tracks.
 I never changed the filename format string when I started ripping cd's - , it was %a - %s. I have changed it to %# - %a - %s and I am ripping The Commitments, which has fourteen tracks. oops - done ripping - same old nine tracks in playlist.m3u

Ripper is responsive to my changes, as you can see when I ripped The Commitments again, but still only nine tracks in playlist.m3u.

---

