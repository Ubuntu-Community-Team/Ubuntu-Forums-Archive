---
title: "Plex Media Manager Metadata"
date: 2015-04-27
forum: Multimedia Software
---

### Post by mdavis1231 on 2015-04-27
Does anyone know where Plex Media Manager stores the metadata posters that it collects?  I'm wanting to edit one that has a white stripe down one side of it, but I can't seem to figure out where they're stored.  Thanks in advance!

---

### Post by TheFu on 2015-04-27
Easiest way it to use the web interface, find the movie/tv show, and use the "edit" button.

Metadata files are buried deep, deep, deep, deep, deeep, deeeeeeep, deeeeeeeeep, deeeeeeeeeeeeeeeep under /var/lib/plexmediaserver/. Actually they are buried so deep there as to be "stupid", IMHO.  
You aren't going to find a nice movie/poster.jpg there either.  Definitely use the web interface at [http://ip-to-plex-machine:32400/manage/index.html](http://ip-to-plex-machine:32400/manage/index.html) to change the settings.

---

### Post by ajgreeny on 2015-04-27
All of that data seems to be stored in **/var/lib/plexmediaserver** which can get very large depending on how much media you have on the machine in libraries.

On my desktop with all my photos and music in PMS libraries that folder is 1.2GB, a lot I accept but OK when I have 1TB available, and I do not know of a way to reduce it, so will be interested to see if anyone else knows if it's possible.

I agree with TheFu, however, that even if you did find anything in there, it will take so long as to be as total waste of time, and if, like me, you run PMS on a desktop machine and not specifically a headless server machine, you can use your web-browser of choice and use [http://localhost:32400/web/index.html](http://localhost:32400/web/index.html) to manage everything graphically.

---

### Post by TheFu on 2015-04-27
If you disable *analyzing media,* I seem to recall it saves a bunch of storage.  I was unable to find it in the web settings just now, but it was there 8+ months ago when I ran out of space on /var on my box.  Don't know where that toggle is.  I haven't found any downside, except ffwd/rev don't show thumbnails on a roku.  Since I don't really use the roku or other devices like that, having all those images created for all video files was a complete waste.

---

### Post by mdavis1231 on 2015-04-27
> **TheFu said:**
> Easiest way it to use the web interface, find the movie/tv show, and use the "edit" button.

Metadata files are buried deep, deep, deep, deep, deeep, deeeeeeep, deeeeeeeeep, deeeeeeeeeeeeeeeep under /var/lib/plexmediaserver/. Actually they are buried so deep there as to be "stupid", IMHO.  
You aren't going to find a nice movie/poster.jpg there either.  Definitely use the web interface at [http://ip-to-plex-machine:32400/manage/index.html](http://ip-to-plex-machine:32400/manage/index.html) to change the settings.

Thanks for the response.  I'll just try and find the movie poster online, and drag & drop it into Plex Media Manager.

P.S. - What I did was find the poster on the Internet, but it was the wrong size.  So I rescaled the image using GIMP 2.8 to 185X278, saved it to my own personal folder .plexmediaposters, and switched the poster out on the web app.

---

### Post by TheFu on 2015-04-27
> **mdavis1231 said:**
> Thanks for the response.  I'll just try and find the movie poster online, and drag & drop it into Plex Media Manager.

P.S. - What I did was find the poster on the Internet, but it was the wrong size.  So I rescaled the image using GIMP 2.8 to 185X278, saved it to my own personal folder .plexmediaposters, and switched the poster out on the web app.

ImageMagick has a **convert** tool which is probably much faster than even starting Gimp. For example, to create a thumbnail, retaining the aspect ratio:
```
convert -resize 64x  t.tn.png $filename.tn.png
```
Or ... 
```
convert -resize 1850x  file.jpg  file-resized.jpg
```

It can rotate, scale, add text ... convert formats and "web optimize" images too. Plus it is really easy to script.

For example, here's my web-image-opt script:
$ more img-opt.sh ```

#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"

done

echo "rename 's/-opt.jpg/.jpg/g' "
```

Use is **./img-opt.sh *jpg** and all the current files which match the pattern (it is regex) will be run through it.  OTOH, hardly worth the effort for a single file, but anyone that uses GIMP probably handles lots and lots of images.  This will reduce the storage size of most jpg files 10x-20x without much change in the appearance and ZERO change to the resolution.

---

