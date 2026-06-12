---
title: "DVD Play Back"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by bobshowrocks on 2007-03-11
Hey, I've tried all the guides on DVD Play back in the Wiki, and in the forums, but when I play a DVD is VLC or Totem the image gets distorted by little horizontal lines on the edges of objects in the picture. This seems to be a problem with the Codecs or decryption since when I use DVD::Rip the same problem occurs on the transcoded file. 

Is this just a reality of watching DVDs in Linux for the time being?

---

### Post by x64Jimbo on 2007-03-11
Absolutely not. Try getting Automatix and have it install the AUD-DVD package. That should help.

---

### Post by bobshowrocks on 2007-03-11
That seems to have helped a bit. But those horizontal lines are still visible when there is movment.

---

### Post by bobshowrocks on 2007-03-11
Maybe a screenshot of what is happening would help ...

[http://lh5.google.com/image/bobshowrocks/RfTPX0mdJrI/AAAAAAAAADQ/5-Fv2ZemfAI/Screenshot001.jpeg?imgmax=1024]("http://lh5.google.com/image/bobshowrocks/RfTPX0mdJrI/AAAAAAAAADQ/5-Fv2ZemfAI/Screenshot001.jpeg?imgmax=1024")

---

### Post by x64Jimbo on 2007-03-12
403 Forbidden error on trying that link

---

### Post by bobshowrocks on 2007-03-12
[http://i49.photobucket.com/albums/f289/bobshowrocks/Screenshot001.jpg]("http://i49.photobucket.com/albums/f289/bobshowrocks/Screenshot001.jpg")

Sorry about that....

---

### Post by x64Jimbo on 2007-03-12
I think I'd have to see it playing. I don't see anything wrong. 
Just out of curiosity, have you installed the driver for your video card? I used to experience some lag/jumpiness when watching movies before I installed my video card's driver.

---

### Post by bobshowrocks on 2007-03-12
Its not the best shot, in the hand there are some noticable lines, but they become more noticeable with the movement of the movies. And Yes, I've installed the lastest drivers from nvidia (my card maker).

---

### Post by x64Jimbo on 2007-03-12
Have you tried different players? Like for instance, have you tried Mplayer? I have had great luck with that one. You can also change the engine that Totem uses, like xine or mplayer.

---

### Post by mpince on 2007-10-29
That distortion is called **combing** and it has to do with whether video is interlaced or not. It's part of many NTSC broadcasts. A different codec or player may do a better job at  rendering interlaced video better.

---

### Post by sonicsmooth on 2007-10-29
You can also try enabling the deinterlace option.  On xine you can press 'i' while playing.  I think mplayer is the same or similar.  The result is an image that looks a bit more anti-aliased, but the obvious lines go away.

Michael

---

