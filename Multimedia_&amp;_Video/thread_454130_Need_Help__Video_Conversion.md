---
title: "Need Help : Video Conversion"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by Prometheus.172214 on 2007-05-25
I have a collection of Real Video files that I downloaded a while ago and before I loose them, I would like to convert them into avi files (xvid with mp3 or something like that). Is there a program that I can use, which will help me do this, without loss in quality and aspect ratio? The file extension of all the files is .rmvb 

:popcorn:

---

### Post by Prometheus.172214 on 2007-05-25
Hmmm, do not wish to bring this thread back to the front, but then I am very much lost and was hoping on someone telling me how...... Would be helpfull, If I can convert .rmvb to .avi and also .dat to .avi (I am thinking of converting my old VCD collection to avi)

---

### Post by fenian on 2007-05-25
I think you can do it wiyh mencoder.To install mencoder and other packages you need do this...
> 
sudo apt-get install mplayer mencoder mozilla-mplayer

then  do this to convert the file
> 
mencoder in.rmvb -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o out.avi

change in.rmvb to the filepath and name of your clip .Change out.avi to the name you want the avi to have it will be saved in your home directory.

---

### Post by rsambuca on 2007-05-25
Wow, very wierd.  I thought this would be easy, but after looking around for quite a while, I can find only Windows programs.  Sorry.

Let us know if you do find anything.:(

---

### Post by Prometheus.172214 on 2007-06-02
Weird..... You said it. I was away on work and could not really check. Will try your idea of using Mencoder to check what happens.

---

