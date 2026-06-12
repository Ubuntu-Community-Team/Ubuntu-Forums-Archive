---
title: "Is there resumable file transfer access to 8.04 ISOs?"
date: 2008-03-10
forum: Mythbuntu
---

### Post by ozybushwalker on 2008-03-10
I downloaded about half the 8.04 alpha 3 .iso file through firefox when something happened and the transfer stopped. Is there a bit torrent or rsync access to the images so that I could resume transfer without having to download the first couple of hundred megabytes again?

---

### Post by NightwishFan on 2008-03-10
Do you mean you wish to start a new download? Torrents are avilable at: [http://cdimage.ubuntu.com/releases/hardy/alpha-6/](http://cdimage.ubuntu.com/releases/hardy/alpha-6/)
Look down to the bottom for the list.

---

### Post by ozybushwalker on 2008-03-10
Sorry, I was after the mythbuntu isos rather than the ubuntu isos.

Torrents are good for using in future downloads.

rsync access would be good so I can effectively resume the partial download  I already have. 

The household has been running pretty close to the download quota the last couple of months so It prefer to not download the couple of hundred megabytes I already have unless I really need to download it.

---

### Post by hyperair on 2008-03-10
Doesn't "wget -c" work for you?

---

### Post by ozybushwalker on 2008-03-10
wget -c did just work for me and md5sum confirmed the transfer.

However I had to massage the original URL in the announcement page to get wget to work.

I've not had an entirely satisfactory experience with resumed transfers but that might be my windows experience talking rather than my more limited unix/linux experience.

I'd like a torrent or rsync access because the checksums give me more confidence the download completed correctly.

---

### Post by hyperair on 2008-03-10
If your connection is fine then wget -c usually works very well. However, if there are trailing garbage bytes, then when you resume, sometimes there are problems. instead of wget -c perhaps you could use a download manager like... DownloadThemAll (plugin for Firefox), or D4X. In my previous experiences I say that D4X isn't very stable, it crashes often for me, but DownloadThemAll has very good performance.

---

