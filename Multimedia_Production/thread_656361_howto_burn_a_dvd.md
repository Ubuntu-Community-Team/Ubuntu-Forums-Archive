---
title: "howto burn a dvd ??"
date: 2008-01-02
forum: Multimedia Production
---

### Post by mjkelly on 2008-01-02
I'm having a hell of a hard time finding a comprehensive ubuntu guide on burning a dvd from an avi.

Can someone point me in the direction of a good guide? I'm finding a lot of posts where everyone is recommending something different: tovid, devede, k3b or a bunch more. It seems like i have to use like 5 different apps to burn a dvd ???

There are hundreds of really detailed good guides here on the forums, where is one for burning a video dvd?

---

### Post by ~LoKe on 2008-01-02
[This](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/) is the guide I've used to convert an avi file to .iso, which I can then burn to a DVD.  I wrote a script based on it.

You'll need to do this:
```
sudo apt-get install ffmpeg dvdauthor mencoder
```

The script:
**/usr/bin/convertdvd**
```
echo "Converting avi.  This shouldn't take too long." &&
ffmpeg -i *.avi -y -target ntsc-dvd -sameq -aspect 16:9 finalmovie.mpg &&
dvdauthor --title -o dvd -f finalmovie.mpg &&
dvdauthor -o dvd -T &&
mkisofs -dvd-video -o dvd.iso dvd/ &&
echo "Conversion complete.  Time to burn."
```

All you is place that script into your /usr/bin/ directory, chmod +x it, then execute it while in the folder containing the avi.

Ex:
> [13:43:35 loke]$ cd ~/Movies/Click
[~/Movies/Click]
[13:43:37 loke]$ convertdvd
Converting avi.  This shouldn't take too long.

---

### Post by mjkelly on 2008-01-02
The movie came in 2 avi files, parts 1 and 2. When i run the script its asking me if i want to overwrite one?

---

### Post by yabbies on 2008-01-02
you will need to combine the two avi files in one

If you are comfortable with the command line
open a terminal 
and type

```
cat file1.avi file2.avi > combinedfile.avi
```

after you have the combined file a lot of times the scr will move backwards (aka the break between the two video files starts over) you will have to mencode to remux the timing.

so you can use

```
mencoder -noidx -oac copy -ovc copy combinedfile.avi -o finalfile.avi
```

---

