---
title: "Album Cover Art problems"
date: 2010-05-24
forum: Multimedia Software
---

### Post by ak123 on 2010-05-24
I think i'm experiencing a slightly unique problem

several Months ago, i installed a program called Album cover Art downloader on my old Ubuntu 9.04 machine...
I tried to make it download all the cover art for my music... however, it screwed up and assigned one image to every single track in my library... (it was about 200 odd songs back then). i subsequently removed it.. 
Now, today, after 2 disk formats, a total reinstall of ubuntu, and finally a complete system change, That Image is still being automatically assigned to all tracks with no cover art...

so far, i haven't seen a mention of this problem in any website...

Please someone help me

---

### Post by cascade9 on 2010-05-24
Thats the way that some album art downloaders do things. Its because portable media players (and some computer media players) dont look for artwork in the folder, etc, but instead look for artwork embedded in the tags. The same artwork is showing up becuase its been embedded in the ID3 tags. 

You can remove embedded artwork with EasyTag ;)

---

### Post by ak123 on 2010-05-26
ive already tried easytag... The weird thing is, the art didnt get embedded in the ID3 tags...

---

### Post by psychoelf on 2010-09-10
I had a lot of messed up album art from years of itunes, windows and other media players.

I finally found out how to get rid of all the album artwork.  Now I've started all over doing it right.

eyeD3 is in synaptics.  
Install, navigate to your music folder in the terminal and run```
eyeD3 --remove-images * *.mp3
```

This removed all the images.  Yay!

P.S.  I also used did a search for *.jpg in my music folder and *.ini just in case and deleted all.

---

