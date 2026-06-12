---
title: "Mencoder, .sub and .idx, can't figure out"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by vlanhopper on 2008-02-04
I know what to do with .srt subs, but I have spent two hours trying to google and find the answer on what to do with .idx and .sub. This is what I tried:


mencoder  -oac lavc  -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup -srate 48000  -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:trell:mbd=2:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3 -sub   yella.2007.dvdrip.xvid.fragment.sub  -subpos 20   -ofps 30000/1001  -o    YELLA.mpg  Yella.avi

No error, it encodes, just no subs. What's the deal?

---

### Post by croto on 2008-02-04
I guess the subtitles file you have to feed mencoder is the one with .idx extension. Why don't you give it a try? (You don't have to encode the whole thing, just enough to see the subtitles working (or not))

EDIT: you can try to watch it with mplayer first, before mencoding it.

---

### Post by vlanhopper on 2008-02-04
No I already tried that script you see, it didn't work, it encodes to mpg but I need to figure out how to insert these .sub and .idx. It's vobsub subs.

---

### Post by croto on 2008-02-04
I see you're giving mencoder the file "yella.2007.dvdrip.xvid.fragment.sub". Do you have also the file "yella.2007.dvdrip.xvid.fragment.idx"? I think that's the one you should use with the option -sub (you also need the .sub file in the same directory though)

---

### Post by vlanhopper on 2008-02-04
Yes I have that file, also in the same directory. What is the syntax for including the .idx file? I have not seen that anywhere in mencoder.

---

### Post by croto on 2008-02-04
It's the same: -sub yella.2007.dvdrip.xvid.fragment.idx (without specifying the .sub file)

---

### Post by vlanhopper on 2008-02-05
I tried that and:      

      SUB: Could not determine file format
Cannot load subtitles: /home/pabloescabar/yella.2007.dvdrip.xvid.fragment.idx


I tried subrip, and several other of the most popular windows subtitle software packages and they fire up but crash or can't load the file and I know it's not corrupt. I really want to watch this German movie, I won't give up.

---

### Post by gsmanners on 2008-02-05
Try doing this:

mplayer Yella.avi -vobsub yella.2007.dvdrip.xvid.fragment

Do not include the file name extension. Press J to select which sub track you want.

---

### Post by vlanhopper on 2008-02-05
That's just to play it right? Can I redirect stdout to >file.avi so I can go ahead and then convert to mpg?

---

### Post by gsmanners on 2008-02-05
Mencoder uses the same options as mplayer, so whatever plays okay in mplayer should encode with mencoder.

---

### Post by vlanhopper on 2008-02-05
Ok I got it another way, I got one more problem, I am using -subpos 30, which is not high enough on the screen. You can barely see it at the bottom, what is crazy is that I started at -subpos 10 and now I tried 30 and it is not moving anywhere, why is -subpos not working?

---

### Post by gsmanners on 2008-02-05
VobSub already has position information, so you evidently need to force it to scale that data (although I wouldn't have thought you'd need to from your first post).

Try using -spuaa 19 or 20 and see if that helps. If that doesn't work, you could try -spualign 2 (which will force it to align the subs at the bottom).

---

