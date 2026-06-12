---
title: "no sound when burning a DVD"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by leveliv on 2007-08-30
There is only one thing I miss about windows and that is Nerovision....Im looking for a program that I can take my movie backups (.avis) and burn them straight to DVD without having the sound screwed with or ...the sound just totally not there...
I've used DeVeDe, Man DVD and they both stole my sound or screwed with it...will I have to take the sound out first then sync it when I am encoding? or is there an easier way?

---

### Post by yabbies on 2007-08-30
you need to encode it to mpeg before you can burn to a DVD.

---

### Post by misfitpierce on 2007-08-30
Honestly DeVeDe is great software but I found ManDVD and have never since looked back :)

---

### Post by leveliv on 2007-08-30
uhh yeah I know but I did that and it made my sound all snowy...and fuzzy...I couldnt understand what was going on. I burned one with Devede and there was no "Audio_ts" folder.

---

### Post by yabbies on 2007-08-30
Tovid

get Tovid by using apt-get or from Synaptic 

```
apt-get install tovid
```

after installation
open a terminal and get to the directory where your avi file is and type:

> tovid -wide -in *filename*.avi -out *newfilename*

**leave out the -wide if you want a pan and scan 4:6 ratio rather than wide 16:9**

this will take a while to encode to mpg
when done and you have a mpg
stay in the directory where your new mpg is and type:

```
makexml -in filename.mpg -out newfilename
```

this will make an xml file of the mpg, adding chapters
after it is done type

```
makedvd -burn filename.xml
```

this will make a dvd file and burn it to disc.

make popcorn and enjoy.

---

### Post by yabbies on 2007-08-30
I just looked and noticed that tovid is no longer in the repos

[here]("http://tovid.wikia.com/wiki/Installing_tovid/Ubuntu") is a good install method.

I have never had any problems with sound from tovid. When I get sound problems it is because I have combined 2 or 3 files together and then they must be remuxed.

let me know if you are combing files and I can help with remuxing for it can be a very difficult process.

---

