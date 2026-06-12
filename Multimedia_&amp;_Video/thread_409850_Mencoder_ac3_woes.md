---
title: "Mencoder ac3 woes"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by wonkycross on 2007-04-15
i'm having something of an issue with ac3 audio.  everytime i try to make a dvd whether it be with tovid, mandvd, manencode, etc., the audio comes out just as a bunch of noise.  i thought it could be just a problem with my sound settings, but i tried playing back the dvd on my tv and got the same result.  i'd use another audio format but none of the above mentioned apps allow you to change the audio format afaik.  i think this could be a mencoder problem because all three of those apps use mencoder for encoding audio.  any help would be appreciated.

---

### Post by tbroderick on 2007-04-15
Maybe there is a problem with the movie file. Use mplayer to see what the audio is encoded in.

---

### Post by wonkycross on 2007-04-15
well, i've tried it on a couple of different files.  two of them were mp2 and one was lpcm i believe.  i could understand if the files didn't play correctly on my computer but the audio is fine until i try to convert it.

---

### Post by housty on 2008-02-13
Any update on this? I've the same problem.. I've Ubuntu installed on nine computers at home including a laptop and all of them have this issue? I even went to the extent of recompiling mencoder with just about everything included without any luck.. Its really disappointing as it works on my Gentoo box as was hoping to remove Gentoo from my list of Linux distro's. 

What I have to do to get things working is this>

use mencoder to encode my movie file to mpeg2 with tweaked options etc.. just "copy" audio 

then

 ffmpeg -i ffmpeg.mpg -vcodec copy -acodec ac3 -ab 448 -target pal-dvd final.mpg  

this is of-course very annoying I'd like to do the ac3 audio encoding in mencoder but all I get 
is the audio and lots of static hissing zx spectrum noise ....

:(

---

### Post by nas11116 on 2008-02-27
same issue here i tried a lot of stuff and couldnt get it to fix the static so i came up with a workaround.  
mplayer -vc null -vo null -hardframedrop -ao pcm:fast:file=filetest.wav inputfile.avi
and than use the regular mencoder like
mencoder -audiofile file.wav -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3 -ofps 30000/1001 -o movie.mpg inputmovie.avi

this should work fine. i havent had any audio sync issues yet.

---

### Post by andrew.46 on 2008-02-29
Hi,

I think you may have an old bug:

> **nas11116 said:**
> same issue here i tried a lot of stuff and couldnt get it to fix the static so i came up with a workaround.

Can I suggest that you try the latest svn mplayer / mencoder? This should eliminate your problem:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

    Andrew

---

