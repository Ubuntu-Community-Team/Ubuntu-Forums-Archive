---
title: "Flash Content covered with pink layer"
date: 2011-03-10
forum: Multimedia Software
---

### Post by lukasu on 2011-03-10
hey guys,

im at the end of my knowlegde, so i discovered this great place...

i try to watch flash content but everything is covered with a pink layer... (see attachment file)

im using firefox 3.6.1.5 (same prob with opera!) and flash 1.0.2.r152 in ubuntu 10.10 with compiz disabled and GPU Override set to true (no difference with false..)

i tried FlashAID for a clean setup an i have only flashplugin-installer on my laptop (no gnash or libswf...), i also tried it with the package "adobe-flashplugin" same problem

oh guys if u could give me a hint it would be great, this and the a2dp-skips are my last problems before a perfect setup :):)

cheers,
lukas

---

### Post by lukasu on 2011-03-10
Ive just upgraded to 
Shockwave Flash 10.3 d180:$

but no difference...

strange as this problem did not occur from the beginning and not everytime, but at least at 97% of flash content...

---

### Post by andrew.46 on 2011-03-11
You are not alone with this problem :). Best advice at the moment is to disable Hardware Acceleration by right clicking on a Flash stream and going to options. This option is usually *not* available on YouTube itself which seems to be the main culprit of miscellaneous colour oddities and crashes recently, so look for another Flash site...

---

### Post by lukasu on 2011-03-11
Thanks, so hopefully if im not alone this will get solved in the next years :D

---

### Post by kidsodateless on 2011-03-11
Same problem here about a week ago, sometimes you could watch without any problems.
Maybe that's because of flash player. it is really annoying.

---

### Post by morgue on 2011-03-11
This site has some tips 
[http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html](http://www.webupd8.org/2011/03/fix-pinkred-youtube-videos-bug-using.html)

---

### Post by beew on 2011-03-11
That seems to be graphic card dependent as well. I have one laptop with a  Nvidia G105M graphic card and there is no issue whatsoever (flash also  uses vpdau quite nicely on Youtube, on other sites it is hit and miss).  On my other machines (with Intel cards) I get the red hue and have to  disable hardware acceleration for flash.

But then I have not even noticed this until reading about it on this  forum because on my older machines I don't even use flash, it just chokes my cpu to death. Instead I use the firefox plugin called flashvideoreplacer to  watch Youtube and it is a lot smoother than flash and I can watch 720P  videos in fullscreen without choking my CPU (with flash I can only play  up to 480P without full screen on some of these older machines )

I also use minitube for Youtube viewing, it is faster and smoother  than  watching the videos on youtube itself and uses way less cpu than flash.  It has the added advantage of not having to work through a browser like FF which utilizes a  bit of resources.   (get version 1.4 from a PPA if you want to try that, the version in the  repo is broken and outdated)

---

### Post by ajgreeny on 2011-03-12
If you are using a 32 bit system, try the flash 11 beta available from [http://download.macromedia.com/pub/labs/flashplatformruntimes/incubator/flashplayer_inc_debug_lin_022711.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/incubator/flashplayer_inc_debug_lin_022711.tar.gz)

You will need to manually replace your current libflashplayer.so file from wherever it is now, which depends on how you installed flash.  To find it go to **about:plugins** in the addressbar of firefox and you will see the file path shown.  Then open up a root nautilus with```
gksudo nautilus
``` and rename the original and copy the new libflashplayer.so from the downloaded tar.gz archive into the correct folder.  Job done.  That flash works OK for my system.

---

### Post by lukasu on 2011-03-12
> **ajgreeny said:**
> If you are using a 32 bit system, try the flash 11 beta available from [http://download.macromedia.com/pub/labs/flashplatformruntimes/incubator/flashplayer_inc_debug_lin_022711.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/incubator/flashplayer_inc_debug_lin_022711.tar.gz)




that worked for me!! thanks ajgreeny!
so is this a "SOLVED" topic??

---

### Post by lovinglinux on 2011-03-13
You could also use a different plugin, like gecko-mediaplayer,  through my extension FlashVideoReplacer.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

Make sure to get version 2.1.0, which is the most recent and full of new features.

---

### Post by MDaugaard on 2011-08-04
> **lovinglinux said:**
> You could also use a different plugin, like gecko-mediaplayer,  through my extension FlashVideoReplacer.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

Make sure to get version 2.1.0, which is the most recent and full of new features.

Works like a charm for me.

Clean and simple interface.

Thanks.

---

