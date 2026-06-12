---
title: "codec woes"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by gendokai1 on 2007-12-28
Hi,

I've been having trouble being able to playback movie files. I'm running ubuntu 7.10 on an acer aspire 3660 laptop.

I've downloaded and installed many codecs manually and also used automatix2 to do the job for me.

I've also tried several movie players but all have the same issue.

The audio works fine, but the picture does not render as it should, just comes up with lines that obviously relate in some way to the movie, but not in any watchable way.

Is there an easy way for me to uninstall all codecs installed on my machine so that I can start again?

Or alternatively, does someone have any idea where I could be going wrong.

cheers

---

### Post by overdrank on 2007-12-28
> **gendokai1 said:**
> Hi,

I've been having trouble being able to playback movie files. I'm running ubuntu 7.10 on an acer aspire 3660 laptop.

I've downloaded and installed many codecs manually and also used automatix2 to do the job for me.

I've also tried several movie players but all have the same issue.

The audio works fine, but the picture does not render as it should, just comes up with lines that obviously relate in some way to the movie, but not in any watchable way.

Is there an easy way for me to uninstall all codecs installed on my machine so that I can start again?

Or alternatively, does someone have any idea where I could be going wrong.

cheers

HI and automatix is not recommended. You can install codecs with these links
 [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Also have you install the drivers for your graphics card and what it the model?

[http://ubuntuforums.org/showthread.php?t=650663&highlight=automatix](http://ubuntuforums.org/showthread.php?t=650663&highlight=automatix)

---

### Post by gendokai1 on 2007-12-28
hi, thanks for the quick response.

the video card is an  ati radeon xpress 200M. I've updated the drivers for this, and every other graphical feature works fine, its just video I have trouble with, which suggests (to me at least, but I dont know much!) that the problem lies with the video codecs..

I installed the codecs (using the same links that you provided) when I first came across the problem. I resorted to automatix when I couldnt think of what else to do.

is it worthwhile/possible to start afresh and remove all the codecs I have installed?

---

### Post by zazkia on 2007-12-28
Hi, sorry to have no answer but at least we can share our woes. :( I seem to have the exact same problem and the exact same ati radeon 200 m card, the stripes are nice in itself... 
 I tried to install the 'new' ati driver but that didn't work either. 
yet I think it is odd if it is indeed the ati card causing troubles, when I had gutsy just installed, I could view open source video, after installing the codecs, I couldn't even see that.
weird weird weird, just a nice reminder for anyone buying a new laptop to ensure that there is an nvidia card on it, other than that no lessons here... 

:(:(:(

---

### Post by zazkia on 2008-01-09
Just another tip that wasn't worth it. gstreamer.dll wasn't installed along with w32codecs. So I installed it but it was of no avail. Now looking in xorg.conf whether it says vesa or ati there, but I not having high hopes for that.

---

### Post by zazkia on 2008-03-02
WOOOOOOOOOOOOOOOOOHOOOOOOOOOOOOOOOOOOOOO 

Finally I can watch  videos, the solution was to change settings in VLC, i am bout to try whether it works in MPLayer as well. 


[http://ubuntuforums.org/showthread.php?t=712198](http://ubuntuforums.org/showthread.php?t=712198)

---

