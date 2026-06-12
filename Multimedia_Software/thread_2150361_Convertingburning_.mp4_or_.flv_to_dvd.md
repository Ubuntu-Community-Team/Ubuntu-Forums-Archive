---
title: "Converting/burning .mp4 or .flv to dvd"
date: 2013-05-31
forum: Multimedia Software
---

### Post by patagriff on 2013-05-31
Does anyone of any linux compatible video conversion software that will enable me to burn movies I've downloaded as .mp4 or .flv files to DVD and that will play in a DVD player? As far as I know, Brasero will only burn them to data disks, unrecognizable by a DVD player.

---

### Post by shantiq on 2013-06-01
DeVeDe which is in repo is excellent for this

---

### Post by patagriff on 2013-06-01
Installed DVD and used it to convert a 350 MB .flv file of a movie and make a DVD playable on a DVD player. Worked beautifully, but for one problem. It took 2 hours. My computers is fairly fast. Is this normal? I have a dual core 64 bit AMD processor running at 2.0 ghz with 3 gig of memory and the only other thing I was using the computer for at the time was to watch a movie using VLC media player.

---

### Post by patagriff on 2013-06-01
Used De-ve-de to convert a 350 MB .flv file to burn to a DVD. It worked beautifully, with the single exception taht it took 2 hours. Is this process usually that time consuming?

---

### Post by shantiq on 2013-06-02
yes it takes time:::}}]]]   there is an option where you just copy the video and audio as is....    I have never used it but i guess it will be a lot faster that way

have a look in all your options you will find it   ....    i would love to know too

---

### Post by andrew.46 on 2013-06-02
You can do it 'by hand' if you like. First convert the video, pal 16:9 in my case:
```

ffmpeg -i input.mp4 -target pal-dvd -aspect 16:9 -ac 2 output.mpg
```

Then create the dvd structure:

```
dvdauthor -t -o dvd --video=pal -f output.mpg
dvdauthor -T -o dvd
```

and finally create the iso and burn it:
```

mkisofs -dvd-video -o output.iso dvd/
growisofs -dvd-compat -Z /dev/sr0=output.iso
```

Room for countless variations there...

---

### Post by SeijiSensei on 2013-06-02
The reason it takes time is that you have to convert the video to the MPEG2 standard used on DVDs.  Most of your files are probably encoded with H.264 or some other more recent codec so conversion is required.  

Copying the audio and video "as is" as shantiq describes only works if the input and output codecs are the same.  Otherwise you need to convert.

---

### Post by shantiq on 2013-06-03
thanx for clarification Sensei was not sure as i have never tried; or know much about DVD by and large; also why i stick to DeVeDe ::]]  will check Andrew's route tho sometime

---

### Post by Dale61 on 2013-06-09
I used to use DVDStyler (found in Software Centre), but as I'm now going back the other way (DVD to mp4), I no longer have a need to use it.

---

