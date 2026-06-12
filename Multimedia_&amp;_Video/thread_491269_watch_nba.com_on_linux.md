---
title: "watch nba.com on linux"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by Siggij on 2007-07-03
Hi,
The only thing I cant do on linux is watching multimedia streams of probably windows media player formats. Mplayer plugin doesnt hack it or totem-mozilla. This is a pain because I want to be windows free. All feedback would be appreciated.

[www.nba.com](www.nba.com) 
.broadband.nba.com 

Thanks in advance
Siggi

---

### Post by RomeReactor on 2007-07-03
Hi. If they *are* wmv videos, you'll need **w32codecs**; if you don't have the Medibuntu repository, or don't know what that is, look [here]("http://ubuntuforums.org/showpost.php?p=2947630&postcount=12"). Follow the first **three** steps, and then enter this in the command line:
```
sudo apt-get install w32codecs
```
After the codecs are installed, you should be able to watch wmv videos on Firefox.

---

### Post by Siggij on 2007-07-04
This does not work properly for some reason. It starts, stops a few times. Then the output is off color and slow. Guess I'll have to use IE to watch these videos.

Thanks anyway,

---

### Post by Bend3r on 2008-02-25
The problem (I think) is that you don't have the video file in the nba.com site. I mean in nbabroadband.com there is an .asx file, which is a playlist file. I have read in other forum that you have to download the .asx file (unplug extension works fine in that issue) and then open it with a text editor to look for the address. I have done this, but I couldn't find any useful address. I will keep on looking for another solution, because I only need to watch nba.com videos and run nba live 2k8 in linux to be windows free.

Regards.

---

### Post by wolfen69 on 2008-02-25
> **Bend3r said:**
> The problem (I think) is that you don't have the video file in the nba.com site. I mean in nbabroadband.com there is an .asx file, which is a playlist file. I have read in other forum that you have to download the .asx file (unplug extension works fine in that issue) and then open it with a text editor to look for the address. I have done this, but I couldn't find any useful address. I will keep on looking for another solution, because I only need to watch nba.com videos and run nba live 2k8 in linux to be windows free.

Regards.

did you notice that your response is for a post that was last answered july 4, 07?

---

### Post by Bend3r on 2008-02-27
No. Thanks.

---

### Post by cttytony on 2008-05-21
Bend3r,

Not sure if your problem is already solved. Anyway I'd still post my experience here. I'm using Ubuntu 8.04, and I'm a big fans of NBA too so I follow up the highlights from nba.com on a daily basis. At my first attempt to play the highlight within my Firefox 2, it prompted me that I got to install a plugin in order to proceed. So I just clicked to d/l the plugin and Firefox gave me 5 choices. I tried all 5 and found that only Xine plays the clip as good as when I was using Windows (Firefox 2 too!). 

Hope this helps.

Tony

---

### Post by pushkin22 on 2008-06-07
You need totem-xine (with totem-mozilla) and w32codecs to watch the videos on nba.com

---

