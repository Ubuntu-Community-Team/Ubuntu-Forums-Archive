---
title: "VP7 Codec"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by nipun_jain on 2007-07-16
Can anyone tell me how to play avi files encoded with Vp7 codec on an Ubuntu System?

Thanks.

---

### Post by sethosayher on 2008-01-09
I also want to know how to play this codec in Ubuntu...or is it already supported?

---

### Post by altonbr on 2008-01-21
I've never been able to get the VP7 codec working in Ubuntu. I'll let you know if I find anything...

---

### Post by stoanhart on 2008-02-02
I have had success using Mplayer with the w32codecs package installed from medibuntu. It includes the VP7 codec. You can also use MEncoder to transcode any Mplayer playable video into whatever you want. I'm converting a season of Simpsons I accidentally downloaded in VP7 into XVid4.

---

### Post by stoanhart on 2008-02-02
Followup on my previous post. I have successfully converted a VP7 video to XVid4:

(bellow is one command, split over two lines - copy and paste the whole thing)
```

mencoder somesourcevideo.avi -oac copy -ovc xvid -xvidencopts pass=1 -o /dev/null && \
mencoder somesourcevideo.avi -oac copy -ovc xvid -xvidencopts pass=2:bitrate=950 -o destinationvideo.avi

```

This command will do a 2-pass Xvid4 transcoding of somsourcevideo.avi to destinationvideo.avi at 950kbps. The audio is untouched (copy) since the source video was already in mp3.

The audio in the original video was 132kbps mp3, so 950 kbps gives a 175MB AVI file, which is my preferred size/quality for half-hour cartoons.

Good luck!

edit: I wrote a little bash script to convert the entire season, if anyone wants it.

```

#!/bin/bash

for inFile in *VP7*.avi
do
	outFile=`echo $inFile | sed 's/.DVDRIP.VP7.KEGGERMAN//g'`
	mencoder $inFile -oac copy -ovc xvid -xvidencopts pass=1 -o /dev/null
	mencoder $inFile -oac copy -ovc xvid -xvidencopts pass=2:bitrate=950 -o ./converted/$outFile
done

```

All of the videos in the season included the ".DVDRIP.VP7.KEGGERMAN" tag. So, I used that to find all VP7 video with: *VP7*.avi
Then, I used sed to strip the above tag to form the output file name. I put the transcoded videos in a subdirectory called "converted" - make sure you create that before you use this script.

Obviously this script is not universal; you need to tweak it to match your situation.

Pascal

---

### Post by jameshoo on 2008-07-14
[SIZE="3"]stoanhart[/SIZE]
     Thanks for the script...

---

