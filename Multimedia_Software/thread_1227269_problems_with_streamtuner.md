---
title: "problems with streamtuner"
date: 2009-07-30
forum: Multimedia Software
---

### Post by pstrbrc on 2009-07-30
Toshiba Satellite, Xubuntu 9.04
have installed StreamTuner, but the playlists of Live365 and SHOUTcast won't load, while Xiph playlists will. Unfortunately, the stations I want to listen to are all on SHOUTcast. What am I missing?

---

### Post by rtalcott on 2009-07-30
I have had that problem with streamtuner also...and for a fairly long time....it was great when the shoutcast worked!
rt

---

### Post by grndplane on 2009-07-30
This is not a solution but you can get shoutcast with Songbird.

---

### Post by pstrbrc on 2009-07-30
> **grndplane said:**
> This is not a solution but you can get shoutcast with Songbird.

OK, songbird's nice. But, I was going with streamtuner so I could record internet radio shows (streamripper) so I could listen to them when I had the time. (talk radio junky!) 
So, is there a program that works to record from songbird, like streamripper?

---

### Post by tgalati4 on 2009-07-30
try tunapie:
sudo apt-get install tunapie
streamripper works with any URL, you just have to find it.  Streamtuner found those URL's and organized them by genre.  You can get internet radio URL's in Rhythbox, Banshee, and other players then cut and paste the one you want to record on the command line:

streamripper [http://myradiostation.com:80/playlist/](http://myradiostation.com:80/playlist/)

man streamripper 

for details on streamripper.

---

