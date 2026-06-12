---
title: "Floola: Use the latest video conversion feature"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by jollyr0ger on 2007-08-13
Hi to all!

Yesterday i was trying to use the latest floola version that include the video conversion (and web video downloading), but on my Ubuntu won't run properly. 
Afther some work, now floola work correctly. 

So now the instruction for you... 
You have first to install ffmpeg:
```
sudo apt-get install ffmpeg
```

Afther you have to do this:
```
sudo ln ffmpeg /usr/local/bin/ffmpeg
sudo ln ffplay /usr/local/bin/ffplay
sudo ln ffserver /usr/local/bin/ffserver
```

You have to do this work because, floola want that ffmpeg is installed into /usr/local/bin, but in the default ubuntu installation it isn't. With this little trick you have solved the problem.

Now enjoy your Pod :D
jollyr0ger

---

### Post by toem on 2007-08-26
before you have to:

cd /usr/bin

Have fun
toem

---

