---
title: "Audacity 1.3.2 beta will not import mp3 files"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by johnleonard on 2007-06-15
Hi

I have compiled Audacity 1.3.2 according to the excellent article here. 

[http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/](http://www.ubustu.com/globe/2007/04/21/compile-audacity-132-beta-with-feisty/)

and also installed LAME, which works great for exporting to MP3. But ... I can't import MP3 files in the first place, getting an error message to the effect that the application has not been compiled to import MP3.

I have libmad installed /usr/lib/libmad.so.0 and I guess I have to compile Audacity to look at this.

Anyone know how I do this?

Thanks

---

### Post by johnleonard on 2007-06-15
Solved - I thought libmad was installed but it seems I was wrong.

After installing libmad0-dev 

 sudo apt-get install libmad0-dev

and recompiling it worked fine

---

