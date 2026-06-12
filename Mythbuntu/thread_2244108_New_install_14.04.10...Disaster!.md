---
title: "New install 14.04.10...Disaster!"
date: 2014-09-13
forum: Mythbuntu
---

### Post by paul164 on 2014-09-13
I had a working 12.04 that was perfectly happy on my system but wanted to expand the partition and a few other things on another partition so I foolishly upgraded to 14.04.10.  It has been a total cluster****!  

1.  Nvidia driver incompatibility with kernel(s):  Seems like anything I try with various nVidia drivers results in a black screen.  While the nouveau driver works, it does not support HD and stutters terribly if I try to run it. I have a Zotac 8200 mobo with an onboard GE8200 card.  Does anyone know what works

2.  Screw-up with SchedulesDirect:  Can't get SD to load the program schedule anymore.  Mythfilldatabase seems to run ok but when I look at the program, all the fields are blank.  They claim to have a work-around or a replacement for mythfilldatabase but getting it to work requires a computer engineering degree. My eyes glassed over after the second screen of the readme on github.  I can manually schedule my programs but why did I pay these folks $25 when their stuff doesn't work.

Warning to any one with a working setup contemplating an upgrade to 14.04.10...DON'T DO IT!

---

### Post by tgm4883 on 2014-09-14
> **paul164 said:**
> 
2.  Screw-up with SchedulesDirect:  Can't get SD to load the program schedule anymore.  Mythfilldatabase seems to run ok but when I look at the program, all the fields are blank.  They claim to have a work-around or a replacement for mythfilldatabase but getting it to work requires a computer engineering degree. My eyes glassed over after the second screen of the readme on github.  I can manually schedule my programs but why did I pay these folks $25 when their stuff doesn't work.


mythfilldatabase works fine in 14.04 with 0.27, I'm not sure why your first inclination is to replace it rather than troubleshoot your issue.

---

### Post by khPWXxF on 2014-09-14
The default nvidia driver with 14.04 is version 311 but I found it quite unstable with my 8300 onboard graphics.  Downgrade it with:
```
sudo apt-get update
sudo apt-get install nvidia-304
``` 
With dvb-t mpeg2 SD recordings in the UK it’s stable, but the frontend HD demo (man in snow) is a bit ‘blurred’.
 
You may experience 2 other issues:

1.  blank screen if HDMI TV is powered on after frontend.   To fix it, see:    
[http://ubuntuforums.org/showthread.php?t=2243778](http://ubuntuforums.org/showthread.php?t=2243778)

2. xfce remnants across top of screen.  Should be fixed with latest bug fixes, but seemingly I'm alone in having to need a cludge to avoid it.
   
hth
Phil

---

### Post by ian-weisser on 2014-09-14
> **paul164 said:**
> I foolishly upgraded to 14.04.10.  

No such release exists.

14.04 is the most recently released version of Ubuntu. It was released in April 2014 (hence the 14.04), and coincidentally is an LTS and supported for 5 years.

14.10 is the *in-development *version of Ubuntu, which -when complete- will be released in October 2014 (hence the 14.10). It will not be an LTS version. It will be supported only until mid-2015, just long enough to update to 15.04 when it is released in April 2015 (hence the 15.04).
14.10 is not finished. It is not ready for you. It was not foolish of you to try it, but it is rude of you to trash an incomplete, unreleased version for not being release-quality and having a known bug that the developers seem to be actively working upon.

---

### Post by SuperFreak on 2014-09-14
> **ian-weisser said:**
> No such release exists.

14.04 is the most recently released version of Ubuntu. It was released in April 2014 (hence the 14.04), and coincidentally is an LTS and supported for 5 years.

14.10 is the *in-development *version of Ubuntu, which -when complete- will be released in October 2014 (hence the 14.10). It will not be an LTS version. It will be supported only until mid-2015, just long enough to update to 15.04 when it is released in April 2015 (hence the 15.04).
14.10 is not finished. It is not ready for you. It was not foolish of you to try it, but it is rude of you to trash an incomplete, unreleased version for not being release-quality and having a known bug that the developers seem to be actively working upon.

Perhaps he meant 14.04.1 the latest point release

---

### Post by paul164 on 2014-09-29
@ian-weisser

> [B][http://www.mythbuntu.org/downloads](http://www.mythbuntu.org/downloads)

Mythbuntu 14.04.1[/B]

 Mythbuntu 14.04.1 is the current release and was released on Thursday, July 24th, 2014. It is available via the links above.


This is what I downloaded and installed. Oh gee, did I incorrectly add a zero after the .1?  *Mea maxima culpa*.  It still doesn't work.   I was not trashing an unreleased version and my comments were and are what I feel.  Between the nVidia issues and the SchedulesDirect detonation, I am absolutely sick and tired of screwing around with this mess.  As far as rudeness, I think you have that market cornered with your unhelpful remark.

@khPWXxF:  I think I tried that (the 304 regression)...if I ever get the desire to waste some more time, I will try it again. On the other hand, maybe enough diff between the onboard 8200 and the 8300 to mess it up?  In the mean time, sincerely,  thanks for a response that tried to help.

---

### Post by ian-weisser on 2014-09-29
> **paul164 said:**
> Oh gee, did I incorrectly add a zero after the .1?  *Mea maxima culpa*.

Thanks for clarifying which version you are having trouble with (14.04).
It does make a big difference.

A lot of people _do_ show up in these forums to complain than an in-development version has (shock!) broken. My apologies for seeming rather defensive on the topic.

---

### Post by topcat5 on 2014-09-30
I didn't have any trouble with moving from 12.04 (0.26) to 14.04 (0.27).   I works fine for me.   

I followed the upgrade advice on mythbuntu.org which basically advises you to backup your DB and other relevant files, and then follow the Ubuntu process from jumping from LTS version to LTS version.   i.e.  Format & do a new install.   I've had several bad experiences in the past with trying to do an in place upgrade of Ubuntu so I didn't try that. 

In this case, I did a format, new install of mythbuntu, then recovered the DB as given on mythbuntu.org.  I keep the OS on a different partition than the videos.  About the only issue I had by this method was some video tearing which I fixed by turning of composting.  The location of the channel icons was changed but easy to fix.    Everything else is fine.

The issue with mythfilldatabase can possibly be related to issues with /tmp or /var/tmp or wherever you have tmp specified, not having enough space.

---

