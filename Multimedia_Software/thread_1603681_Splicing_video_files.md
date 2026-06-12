---
title: "Splicing video files?"
date: 2010-10-23
forum: Multimedia Software
---

### Post by kz6090 on 2010-10-23
I have two files, aw1.mp4 and aw2.mp4, each about 1 GB in size. 
I want to splice them together (aw2 after aw1) on a single 4.7 GB DVD, *as one movie*, and burn (transcode?) them so that the disc will play on a home DVD player that's +/-5 years old. 
How can I do this?
Thank you.

******************************

ffmpeg -i aw1 aw2 worked.
So does avidemux, and thanks for the googlubuntu tips. I have a new page for Speed Dial. :)

---

### Post by jerrrys on 2010-10-23
hi kz6090; welcome to the fourm

my video editing skills is limited to our home movies and really not much of a help in this case, but i search the subject and got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=splice+mpeg4&as_qdr=all&sa=Google+Search&lang=en#1290](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=splice+mpeg4&as_qdr=all&sa=Google+Search&lang=en#1290)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=video+editor+mpeg4&as_qdr=all&sa=Google+Search&lang=en#1131](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=video+editor+mpeg4&as_qdr=all&sa=Google+Search&lang=en#1131)

hope that helps

---

### Post by Enigmapond on 2010-10-23
I recommend you use avidemux. It's the Linux version of VirtualDub and I find it works great. just make sure both parts are the same format. Load the first file and then "append" or attach the second file to it...save it however you want. Hope this helps..:)

---

### Post by perspectoff on 2010-10-23
> **Enigmapond said:**
> I recommend you use avidemux. It's the Linux version of VirtualDub and I find it works great. just make sure both parts are the same format. Load the first file and then "append" or attach the second file to it...save it however you want. Hope this helps..:)

Agree.

---

