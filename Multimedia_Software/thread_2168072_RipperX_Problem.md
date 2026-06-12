---
title: "RipperX Problem"
date: 2013-08-16
forum: Multimedia Software
---

### Post by Polydorus on 2013-08-16
I'm having a problem with  RipperX using Ubuntu 12.04 64 bit.  I will rip a CD successfully but the MP3 files are nowhere to be found.  WAV file seem to work OK, at least they show up on my hard drive.  Any idea what I may be doing wrong?  TIA

---

### Post by shantiq on 2013-08-17
maybe you have not got lame installed or fluendo

```
sudo apt-get install lame  gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-fluendo-mp3

```


hope that works...


if not maybe Try another easy route:


put your disc again in cd drive and run [simple way]

open terminal and enter

```
sudo apt-get install pacpl

```


then




```
mkdir ~/Music/"Lianne la Havas" && pacpl --outdir ~/Music/"Lianne la Havas" --rip all -t mp3 --bitrate 320

```

&#9679; change name of folder both times within "" to describe your disc name where it says "Lianne la Havas"
&#9679;and change 320 if you want a lower number


&#9679;if you want flac instead change last bit to


```
-t  flac --fcomp 8
```

---

### Post by Polydorus on 2013-08-17
Thanks shantiq.  I'll give it a try.

---

### Post by Polydorus on 2013-08-18
Lame was installed but I followed the rest of your advice and now I get MP3.  Thank you very much.  

I would mark this solved if I knew how. :)

---

### Post by shantiq on 2013-08-19
glad it worked

mark as solved  ...    oh yeah  ...    [found it]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730")    ;)


> [COLOR=#000000]Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[/COLOR]

[COLOR=#000000]Please note that there is a [/COLOR][COLOR=#000000]60-day limit on being able to edit posts, and this would include changing the prefix.[/COLOR]

---

### Post by Polydorus on 2013-08-22
Thanks once again shantiq.

---

