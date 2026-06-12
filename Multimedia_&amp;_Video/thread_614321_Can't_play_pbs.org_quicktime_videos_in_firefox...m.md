---
title: "Can't play pbs.org quicktime videos in firefox...may involve Adobe Flash"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by hurtstotalktoyou on 2007-11-15
Hi, all.

I'm trying to watch [some NOVA videos on the PBS website](http://www.pbs.org/wgbh/nova/id/program.html).  According to PBS, they require Quicktime to play.  Unfortunately, they can't be downloaded (at least, not that I know of), so I have to watch them within Firefox.  But whenever I try to view them, all I get is a grey bar (like a progress bar without an indicator) across the middle of an otherwise blank screen.

Now, I can play certain Quicktime videos.  For example, I can play [these Quicktime 5 movies](http://www.pixar.com/theater/shorts/ftb/index.html) in Firefox just fine.  Then there are other Quicktime feeds which sort of work, but not properly.  For example, [this movie](http://onegoodmove.org/1gm) which claims to require Quicktime 7 displays the video just fine, but the audio is choppy and reverse-stretched (AKA the chipmunk effect).

I've installed ubuntu-restricted-extras (which includes flashplugin-nonfree), quicktime-utils and quicktime-x11utils.  I've also installed all available general updates.  Nothing seems to solve my problem.

So, what do y'all think?  How do I watch these NOVA videos?

Oh, one last thing:  On my Windows PC, the videos play just fine, but as I was installing Quicktime it told me that there was a Adobe Flash component which needed to work with (or inside of) Quicktime in order for the PBS videos to play properly.  I'm not sure if that matters or not, but I thought I'd mention it.

Thanks in advance, guys!

---

### Post by Wijsneus on 2007-11-16
I have the exact same problem. I've viewed the source of the page and found the address of the movie (actually not that difficult to find) and tried playing it directly in VLC and Totem without succes.

 I've tried WGETting the url and get an unplayable .mov file

Installed quicktime-utils and tried to play the downloaded file (commandline: "lqtplay prog-player-enh.mov") and got the folowing output:
> 
INFO: playing prog-player-enh.mov
  copyright: &#65533; 2007 WGBH Educational Foundation
  video: 2 track(s)
    track #1
      width : 452
      height: 20
      depth : 8 bit
      rate  : 1.00 fps
      codec : gif 
    track #2
      width : 452
      height: 20
      depth : 8 bit
      rate  : 1.00 fps
      codec : gif 
WARNING: unsupported video codec
WARNING: no audio stream

Looks like a codec problem - anyone know how to find out what codec to install to get this running?

---

### Post by tritiumlucidium on 2007-11-20
Hi I'm having the same problem.  Wijsneus, the .mov file you are trying to play is fake.  Notice that its imbeded in some java script code that generates an XML file to send to another java script.  I wasn't able to debug the java script to figure out how it parses the input parameters.  However, entering the google search query:    ```
mov site:http://www.pbs.org/media
```  reveals that each pbs program with online content has sub-directories with video files present.  After a little work I found the nova directory at [http://www.pbs.org/media/wgbh/nova/programs/](http://www.pbs.org/media/wgbh/nova/programs/)   which is viewable.
Looking at the source code for the nova page for the 'moviename' line reveals that I was trying to watch '(e)3416(/e)(c)02(/c)', or show #3416 part 2, the second part of intellegent design program.  This is located at [http://www.pbs.org/media/wgbh/nova/programs/3416-02-300.mov](http://www.pbs.org/media/wgbh/nova/programs/3416-02-300.mov) for the high quality version.

---

### Post by Wijsneus on 2007-11-23
Good work! I'll try this as soon as i get home.

tnx

---

