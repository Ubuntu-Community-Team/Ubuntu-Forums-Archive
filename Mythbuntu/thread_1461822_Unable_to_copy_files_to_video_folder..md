---
title: "Unable to copy files to video folder."
date: 2010-04-24
forum: Mythbuntu
---

### Post by acsidental on 2010-04-24
Hi,

OK spent most of yesterday upgrading my backend and slave boxes from 8.04 too 9.10.

2 reasons for doing this were that the DVD player no longer worked and the master was unstable with a replacement motherboard and cpu (Athlon II 630 X4, Gigabyte GA-MA785GMT-US2H).

The DVD is now working using the internal player but still not via Xine.

But the main problem now is that I cannot copy files over to the Videos folder via the network. I can connect and see everything in the folder but after it copies the file it then says it I don't have permission to access some of the items.

I can delete the existing files though.

Any ideas?

---

### Post by acsidental on 2010-04-26
Fixed. 

Ran "sudo chmod -R 755 videos" on the directory and now it works.

However it seems I spoke to soon about the DVD playback. It stutters on encrypted disc's using the internal player. Will have to try xine or mplayer again.

---

