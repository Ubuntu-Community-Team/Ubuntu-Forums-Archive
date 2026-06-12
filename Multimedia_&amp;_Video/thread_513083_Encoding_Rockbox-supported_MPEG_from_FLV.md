---
title: "Encoding Rockbox-supported MPEG from FLV"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by onero on 2007-07-30
I use Rockbox on my iPod Nano, and it can play MPEG files. I tried encoding some FLV files I had into MPEG using ffmpeg by simply entering ffmpeg -i video1.flv video1.mpg. That worked great and I had an .mpg file, but when I transferred it to Rockbox, it wouldn't play correctly. Are there any encoding options, etc., that I should include? Or are there specific types of MPEG files that Rockbox supports? Thanks.

---

### Post by zedlander on 2008-06-05
sudo apt-get install mencoder

mencoder <inputfilename> -of mpeg -oac lavc -lavcopts acodec=mp2:abitrate=96:vmax_b_frames=16:vb_strategy=2 -af resample=44100:0:0 -ovc lavc -lavcopts vcodec=mpeg2video:vbitrate=200 -vf scale=176:128,harddup -ofps 25 -o <outputfilename>

These settings are optimized for the iPod Nano.

---

