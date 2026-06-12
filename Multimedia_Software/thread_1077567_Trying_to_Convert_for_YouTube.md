---
title: "Trying to Convert for YouTube"
date: 2009-02-22
forum: Multimedia Software
---

### Post by joe215 on 2009-02-22
I am trying to convert something from my dvd drive onto my computer for upload onto YouTube. Thing is first I've got to get my computer to recognize the file from Windows Media Player,then once I get it into my computer files I've got to probably convert that into a file acceptable to YouTube.

---

### Post by gandaran on 2009-02-22
there are many tools you can use but I think the best is winff [http://winff.org/html/](http://winff.org/html/)

---

### Post by joe215 on 2009-02-24
> **gandaran said:**
> there are many tools you can use but I think the best is winff [http://winff.org/html/](http://winff.org/html/)

Ok I did the winff thing,but it doesn't seem to be converting. Perhaps there's something I'm missing,how would I go about finding info on this? If it would help I actually recorded a vid of me trying to figure the thing out-

[http://www.youtube.com/watch?v=TmdX_D36Czg](http://www.youtube.com/watch?v=TmdX_D36Czg)

---

### Post by gandaran on 2009-02-24
> **joe215 said:**
> Ok I did the winff thing,but it doesn't seem to be converting. Perhaps there's something I'm missing,how would I go about finding info on this? If it would help I actually recorded a vid of me trying to figure the thing out-

[http://www.youtube.com/watch?v=TmdX_D36Czg](http://www.youtube.com/watch?v=TmdX_D36Czg)
do you get any errors, post them!
one question, did you add the correct winff repository? which ubuntu you have 8.04 or 8.10? the winff application is not the same for ubuntu 8.04 and 8.10, there are big deferences in the codecs they use.

---

### Post by Anxious Nut on 2009-02-24
I've tried winff, and i say it is not as good as MEncoder, use MEncoder and believe me you won't be disappointed.

download it

```
sudo apt-get install mencoder
```

All you have to do now is to open the terminal, move to your directory, and paste the following:

```
mencoder **YourVideo.Extension ** -oac lavc -ovc lavc -lavcopts abitrate=160 -o Output.Extension
```

available extensions are: avi, flv, mpeg, mp4,...

---

