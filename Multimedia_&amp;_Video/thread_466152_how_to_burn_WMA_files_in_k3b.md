---
title: "how to burn WMA files in k3b"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by miatawnt2b on 2007-06-06
I have compiled the latest k3b and ffmpeg, and k3b still will not burn an audio cd from wma files.

When compiling ffmpeg, i used the ./configure --enable-shared after which I compiled k3b using the ./configure --enable-ffmpeg-all-codecs

everything seemed to make and make install without error, but k3b still does not list ffmpeg in plugins (not sure if it should be there) nor make the audio CD from WMA.  

Can someone help me with getting WMA support into k3b?

Thanks,
-J

---

### Post by bdean42 on 2007-07-27
i was trying to do the same thing and i saw on the kde-app.org page for k3b a comment from a kubuntu user which mentioned that k3b in debian based systems doesn't work with the ffmpeg plugin. i'm not sure if that's true or not but ... i can't get it to work. i know ffmpeg can decode wma because i've tried playing a few with ffplay.

however a stupid solution is to just translate all your wma files to wav with ffmpeg before running k3b. something like:

```
ffmpeg -i 01_somefile.wma 01_somefile.wav
```

i had tried putting this in a little batch script to get all wma's in a given directory but there's something screwy with my script so .... it doesn't work.

but ffmpeg has no problem converting wma to wav (which is essentially what needs to be done to burn a cd) and k3b has no problem burning wav files. i know this is really a non-solution but ... it's something

is this the sort of thing that deserves a bug report on launchpad?

- b

---

### Post by deadgobby on 2007-07-27
I just convert the wma files to mp3 by using Audacity.  
Gobby

---

### Post by bdean42 on 2007-07-27
i'm not a big fan of converting from lossy (wma) to lossy (mp3). when the source already has had stuff removed from it, removing more is going to further decrease quality. personally i just encode CDs i own into ogg. but that's beside the point.

the point is, if we have wma, k3b should be able to burn them. k3b is supposed to have wma support since before version 1.0 but somehow it didn't make it to ubuntu.

i'm fairly certain there is a batch transcoding application that could change whole directories of wma's to wav or mp3 or whatever

i had tried writing this script to take all the wma files in a directory and convert to wav. however due to some problem with spaces in file names and something i'm not quite understanding about bash, it's not working

```

#!/bin/bash

ls -1b *.wma | while read -r WMA
do  
    OUT=${WMA/%wma/wav}
    ffmpeg -i "$WMA" "$OUT"
done

```

any thoughts from bash guru's?

---

### Post by codecaine on 2007-08-22
Solution to your script
#!/bin/bash
#
# Dump wma to wav
for i in *.wma
do
 if [ -f "$i" ]; then
	ffmpeg -i "$i" "${i%.wma}".wav
 fi
done

---

### Post by andressis2k on 2007-11-08
Also, you can convert  your mp3/wma/ogg files to Wav by selecting "Disk writer" driver output in XMMS Preferences, and then drag&drop all your wma files into the xmms window

---

