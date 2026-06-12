---
title: "tring to get ffmpeg to encode divx"
date: 2011-01-04
forum: Multimedia Software
---

### Post by thefrenchdog1@hotmail.com on 2011-01-04
first time poster sometime reader.


So what I want to do is encode files with divx so that I can watch them on a regular DVD player hooked up to a TV.  I don't want to format them into vob DVD's.  I've tried a couple of things and I get burns that I can watch on a computer but not on a TV.  

I also don't like asking until I've let my searching run its course but converting and then burning is time consuming and wastes discs.

So if anyone has used ffmpeg what is the secret of making avi's like the ones I can torrent that can be burned and played on a regular dvd player?  I want to use ffmpeg so that I can do something like the below when I leave for work and let it convert away.





ffmpeg -i bb202.mkv -s uxga bb202.avi | ffmpeg -i bb203.mkv -s uxga bb203.avi | ffmpeg -i bb204.mkv -s uxga bb204.avi | ffmpeg -i bb205.mkv -s uxga bb205.avi | ffmpeg -i bb206.mkv -s uxga bb206.avi | ffmpeg -i bb207.mkv -s uxga bb207.avi | ffmpeg -i bb208.mkv -s uxga bb208.avi | ffmpeg -i bb209.mkv -s uxga bb209.avi | ffmpeg -i bb2010.mkv -s uxga bb2010.avi | ffmpeg -i bb2011.mkv -s uxga bb2011.avi | ffmpeg -i bb212.mkv -s uxga bb212.avi | ffmpeg -i bb213.mkv -s uxga bb213.avi

---

### Post by BicyclerBoy on 2011-01-04
stolen from ffmpeg website  

[http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html)



 * You can transcode decrypted VOBs:    
ffmpeg -i snatch_1.vob -f avi -vcodec mpeg4 -b 800k -g 300 -bf 2 -acodec libmp3lame -ab 128k snatch.avi
  This is a typical DVD ripping example; the input is a VOB file, the output an AVI file with MPEG-4 video and MP3 audio. Note that in this command we use B-frames so the MPEG-4 stream is DivX5 compatible, and GOP size is 300 which means one intra frame every 10 seconds for 29.97fps input video. Furthermore, the audio stream is MP3-encoded so you need to enable LAME support by passing --enable-libmp3lame to configure. The mapping is particularly useful for DVD transcoding to get the desired audio language. 





This example gives you the required output settings
You may need to pick the correct input streams.

You might have to build ffmpeg to get mp3 encoder support (or install mp3 encoder lib)

The 'FakeOutdoorsMan' is your friend here for ffmpeg howtobuild...

---

### Post by ilil on 2011-01-06
You still need to reencode your videos to vobs.
You may try Bombono DVD to make it in one step, [http://www.bombono.org](http://www.bombono.org)

---

