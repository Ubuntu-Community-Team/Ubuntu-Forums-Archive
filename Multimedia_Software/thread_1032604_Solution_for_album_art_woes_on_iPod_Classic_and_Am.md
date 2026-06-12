---
title: "Solution for album art woes on iPod Classic and Amarok"
date: 2009-01-06
forum: Multimedia Software
---

### Post by dartmusic on 2009-01-06
I searched and searched for months and of the posted solutions I found, they all either involved loading SVN's or much fiddling with inner workings.  

I was able to get the "tiny" thumbnail of artwork to appear in the list of albums by artist, and sometimes get them to show in coverflow, but not (or rarely) when playing an album.  

The solution that worked for me (running an up-to-date install of Intrepid 32bit, the latest Amarok, the latest libgpod3, model and capacity properly selected in Amarok) was to simply add libgpod3-dev (which adds approximately 40 *-dev packages as well) and suddenly, there is artwork on every track, though sometimes I still get incorrect artwork (correct artist and album, but sometimes NOT the file that is folder.jpg from the album folder but another jpg file), and every now and then, nothing at all, but 90+% of the time, all works well.

Now I have Amarok 1.4.x transcoding FLACs, copying artwork all seamlessly...finally!

I hope that this helps someone who is as frustrated as I was.

---

