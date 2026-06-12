---
title: "Merging 2 pictures"
date: 2013-01-07
forum: Multimedia Software
---

### Post by thusgaard on 2013-01-07
Hi 

I have setup a script that takes 2 photos every minute. It uses 2 cameras and then waits a minute. The pictures are taken almost simultaneous.

The cameras are placed in a way that they don't overlap each
other. Each picture is 960 * 544 pixels. I'd love to merge 2 pictures to a picture of 1920 * 544 pixels and save this picture. Is this possible using a script. 

Please let me know if what I'm saying is odd. I'll love to tro to explain it better if it's needed. 

This is my script it's not super timing, but then it's not critical either. 

I expect the merging of pictures to be prior to the copying to new location. 

```

#!/bin/bash

SLEEP=59

uvccapture -m -o/home/jesper/pix0.jpg -d/dev/video0 -w -v -x960 -y544
uvccapture -m -o/home/jesper/pix1.jpg -d/dev/video1 -w -v -x960 -y544 

myfilename=/home/jesper/pix0/"$(date +%F-%T)".jpg
mv /home/jesper/pix0.jpg $myfilename			 

myfilename=/home/jesper/pix1/"$(date +%F-%T)".jpg
mv /home/jesper/pix1.jpg $myfilename			 

sleep $SLEEP

exec $0
```

Please let me know if you have ideas to how I can clean up my script. I still need to add comments to it. 

J;-)

---

### Post by Lars Noodén on 2013-01-07
My guess would be that you could do it with ImageMagick.

[http://www.imagemagick.org/script/composite.php](http://www.imagemagick.org/script/composite.php)
[http://www.imagemagick.org/Usage/compose/](http://www.imagemagick.org/Usage/compose/)

About using the date in the filename, you call the date function twice.  It's theoretically possible for the date to roll over between the first and second call.  So it would be better to call it once into a variable and use that for forming the filenames, avoiding the race condition.

---

### Post by thusgaard on 2013-01-07
> **Lars Noodén said:**
> 
About using the date in the filename, you call the date function twice.  It's theoretically possible for the date to roll over between the first and second call.  So it would be better to call it once into a variable and use that for forming the filenames, avoiding the race condition.

Changed that bit. 

Now I'm going to see if I can fix the bit with merging pictures. Although I can't see exactly how to do this.

---

### Post by Lars Noodén on 2013-01-07
Looking around, there is also Hugin:

[http://lifehacker.com/378490/stitch-photos-into-panoramas-with-free-software](http://lifehacker.com/378490/stitch-photos-into-panoramas-with-free-software)

It is also in the repository.

---

### Post by thusgaard on 2013-01-09
I changed my code. And learned a lot about variables. I'll be using them a lot more, and probably use a few loops too. But this script will do for now, and I'll be using it tomorrow!

```

#!/bin/bash

SLEEP=59
DATE=$(date +%F-%T)

uvccapture -m -o/home/jesper/pix0.jpg -d/dev/video0 -w -v -x960 -y720 
uvccapture -m -o/home/jesper/pix1.jpg -d/dev/video1 -w -v -x960 -y720 

montage -geometry '+0+0' -background 'none' /home/jesper/pix0.jpg /home/jesper/pix1.jpg /home/jesper/pixmerge/"$DATE.jpg"

myfilename=/home/jesper/pix0/"$DATE.jpg"
mv /home/jesper/pix0.jpg $myfilename			 

myfilename=/home/jesper/pix1/"$DATE.jpg"
mv /home/jesper/pix1.jpg $myfilename			 

sleep $SLEEP

exec $0

```

---

### Post by evilsoup on 2013-01-09
You can simplify your script slightly more by using [bash string expansion](http://www.catonmat.net/blog/bash-one-liners-explained-part-two/).

You can replace

```

myfilename=/home/jesper/pix0/"$DATE.jpg" 
mv /home/jesper/pix0.jpg $myfilename 

myfilename=/home/jesper/pix1/"$DATE.jpg" 
mv /home/jesper/pix1.jpg $myfilename

```

with
```

mv /home/jesper/pix0{.jpg,"/$DATE.jpg"}	
mv /home/jesper/pix1{.jpg,"/$DATE.jpg"}

```

This works because 'mv /home/jesper/pix0{.jpg,"/$DATE.jpg"}'	becomes 'mv /home/jesper/pix0.jpg /home/jesper/pix0"/$DATE.jpg"' when bash expands the string. Other than that, it looks about perfect (and it is a little bit more readable).

---

### Post by thusgaard on 2013-01-09
> **evilsoup said:**
> 
with
```

mv /home/jesper/pix0{.jpg,"/$DATE.jpg"}	
mv /home/jesper/pix1{.jpg,"/$DATE.jpg"}

```

This works because 'mv /home/jesper/pix0{.jpg,"/$DATE.jpg"}'	becomes 'mv /home/jesper/pix0.jpg /home/jesper/pix0"/$DATE.jpg"' when bash expands the string. Other than that, it looks about perfect (and it is a little bit more readable).

That is very close to what I was planning. 
Mine would be a bit closer to human readable.... But this looks very neat.

---

### Post by thusgaard on 2013-01-18
> **thusgaard said:**
> That is very close to what I was planning. 
Mine would be a bit closer to human readable.... But this looks very neat.

It worked like a charm. Unfortunatly one camera crashed and then woke up again... So I now have a new post trying to solve that

[http://ubuntuforums.org/showthread.php?t=2106127](http://ubuntuforums.org/showthread.php?t=2106127)

---

