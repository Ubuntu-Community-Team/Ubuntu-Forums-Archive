---
title: "Unknown encoder"
date: 2009-08-02
forum: Multimedia Software
---

### Post by ProStockNut on 2009-08-02
[IMG]http://i28.tinypic.com/9untjc.png[/IMG]


After a fresh install of Jaunty i now get this error. What to do to correct this?:confused:_[IMG]http://%5BIMG%5Dhttp://i28.tinypic.com/9untjc.png%5B/IMG%5D[/IMG]_[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://i28.tinypic.com/9untjc.png%5B/IMG%5D[/IMG][IMG]http://ubuntuforums.org/%3Ca%20href=%22http://tinypic.com%22%20target=%22_blank%22%3E%3Cimg%20src=%22http://i28.tinypic.com/9untjc.png%22%20border=%220%22%20alt=%22Image%20and%20video%20hosting%20by%20TinyPic%22%3E%3C/a%3E[/IMG]

---

### Post by mc4man on 2009-08-02
Install,at a min, the unstripped version of libavcodec (for jaunty libavcodec52
```

sudo apt-get install libavcodec-unstripped-52 
```

And or search in synaptic for ffmpeg - there are unstripped versions of all the ffmpeg libs (7)
If desired replace with the unstripped versions, (don't remove an existing lib, just mark the unstripped version for install and apply


edtit
screensshots are better as an attachment (manage attachments

In this case just the code box would have sufficed, for that put focus on box (click in with mouse) and then go Alt+PrntScm (or whatever your print screen keyboard button is

---

### Post by vinutux on 2009-08-03
use better converters like **avidemux or Handbreake**

```
sudo apt-get install avidemux
```

...................

install from here[** www.getdeb.net/app/HandBrake**]("www.getdeb.net/app/HandBrake")


or


PPA for hnadbreake **[https://launchpad.net/~handbrake-ubuntu/+archive/ppa]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")**

---

### Post by ProStockNut on 2009-08-03
> **mc4man said:**
> Install,at a min, the unstripped version of libavcodec (for jaunty libavcodec52
```

sudo apt-get install libavcodec-unstripped-52 
```And or search in synaptic for ffmpeg - there are unstripped versions of all the ffmpeg libs (7)
If desired replace with the unstripped versions, (don't remove an existing lib, just mark the unstripped version for install and apply


edtit
screensshots are better as an attachment (manage attachments

In this case just the code box would have sufficed, for that put focus on box (click in with mouse) and then go Alt+PrntScm (or whatever your print screen keyboard button is

Thankyou. That did the trick. And i will work on my screenshots as well. Thanks again.

---

### Post by ProStockNut on 2009-08-03
> **vinutux said:**
> use better converters like **avidemux or Handbreake**

```
sudo apt-get install avidemux
```...................

install from here[** www.getdeb.net/app/HandBrake**]("http://www.getdeb.net/app/HandBrake")


or


PPA for hnadbreake **[https://launchpad.net/~handbrake-ubuntu/+archive/ppa]("https://launchpad.net/%7Ehandbrake-ubuntu/+archive/ppa")**

Avidemux crashes every time i use it. I just installed Handbrake and will give it a go. Thanks.

---

