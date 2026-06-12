---
title: "Can you play .wma files?"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by Sup3rkirby on 2007-04-11
I can not seem to play any of my music in .wma format.  I have tried xfmedia and amaroK.  Pretty much all of my music is in .wma format so I would really like to know how you can play the files.

Right now it will just skip through a song in like 3 seconds, not playing any sound.

Is there some codec or something you must download and install?  and if so, how do you do this?


I would greatly appreciate any help anyone can give.

---

### Post by wesley_of_course on 2007-04-11
Wesley here ; 
   
                           Here's a link that helped me out -  

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


  Good Luck

---

### Post by MaX on 2007-04-11
> **Sup3rkirby said:**
> I can not seem to play any of my music in .wma format.  I have tried xfmedia and amaroK.  Pretty much all of my music is in .wma format so I would really like to know how you can play the files.

Right now it will just skip through a song in like 3 seconds, not playing any sound.

Is there some codec or something you must download and install?  and if so, how do you do this?


I would greatly appreciate any help anyone can give.

Yes, the only legal way (as far as I know) is to use the [Fluendo plugins]("https://shop.fluendo.com/") for Gstreamer. The Windows Media ones cost 16&#8364; 

You could try gstreamer-pitfdll and download w32codecs from some unofficial repository. But that's not totaly legal.

---

### Post by Sup3rkirby on 2007-04-11
> **wesley_of_course said:**
> Wesley here ; 
   
                           Here's a link that helped me out -  

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


  Good Luck

I downloaded and installed everything from the terminal and it sort of worked....  The .wma files will play, although any media info on them is not read(not even the song length).  And when they play the song sounds very funny....  For instance, on one song, I will hear everything, but only the guitar part is played clearly.  Everything else will be muffled, as if I were using some funny equalizer setting.  It changes around and sometimes different things will be louder....  It is kind of interesting.

I will look into Gstreamer though.

---

