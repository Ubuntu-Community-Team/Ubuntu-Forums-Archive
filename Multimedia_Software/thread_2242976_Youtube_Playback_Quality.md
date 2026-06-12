---
title: "Youtube Playback Quality"
date: 2014-09-05
forum: Multimedia Software
---

### Post by Ritchiejoe8 on 2014-09-05
Hello,

I have recently installed Ubuntu 14.04.1 LTS on my laptop, when trying to watch video's on youtube the highest quality I can set is 360p, on windows it's 1080P?
[h=2][/h]

---

### Post by shantiq on 2014-09-05
Hi R playing youtube through a browser   is a very frustrating experience on U
but it becomes really easy if you copy URL you open VLC >> CTRL+V >> enter 
   then 1080p is fine
Takes 15 seconds to do that and it feels like your own private movie


even better copy a list of URLs in a txt editor   call it anything
drag in in VLC   your own TV :)

---

### Post by mc4man on 2014-09-05
> **shantiq said:**
> Hi R playing youtube through a browser   is a very frustrating experience on U
but it becomes really easy if you copy URL you open VLC >> CTRL+V >> enter 
   then 1080p is fine
Takes 15 seconds to do that and it feels like your own private movie


even better copy a list of URLs in a txt editor   call it anything
drag in in VLC   your own TV :)

shantiq - 
just curious, what version of vlc are you using? I've found that [2.2+ & 3.0+ have issues with http/https]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186") for h.264. (.mp4/.mov),  while 2.1.X is fine (except for vevo which I use smtube > mpv for

Ex. picking something at random right now from yt main page
[https://www.youtube.com/watch?v=YoB8t0B4jx4](https://www.youtube.com/watch?v=YoB8t0B4jx4)


edit:
Also this FF extensions works ok for most of yt, vevo & some "Official" music vids excepted - see screen (with vlc < 2.2/3.0

---

### Post by Ritchiejoe8 on 2014-09-05
Thank you both for the replies :)

---

### Post by vasa1 on 2014-09-05
> **Ritchiejoe8 said:**
> Hello,

I have recently installed Ubuntu 14.04.1 LTS on my laptop, when trying to watch video's on youtube the highest quality I can set is 360p, on windows it's 1080P?
...

I could watch the sample YouTube video link that mc4man provided at the best quality (1080) available. The browser I used is Firefox, fully updated. My laptop doesn't have a GPU; it's from 2009 with integrated graphics.

When I click on the cog wheel and select the highest quality, the wheel rotates for a while and then I see "HD" as shown in the image. 

I don't normally watch HD on my laptop. Things get a bit hot.

---

### Post by andrew.46 on 2014-09-06
> **mc4man said:**
> I've found that [2.2+ & 3.0+ have issues with http/https]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1364186") for h.264. (.mp4/.mov),  while 2.1.X is fine (except for vevo which I use smtube > mpv for

Ex. picking something at random right now from yt main page
[https://www.youtube.com/watch?v=YoB8t0B4jx4](https://www.youtube.com/watch?v=YoB8t0B4jx4)

Mind you the latest vlc from git had no trouble with this and the NASA vid you linked to from Launchpad.... Not sure which part of the logs would be useful to you to find the issue though?

---

### Post by shantiq on 2014-09-06
hi guys     well Mutant Spider Giant Dog    plays a treat here in 2.1.5 Rincewind    and thank you for the cinematic experience


But VLC can be temperamental;    plays different things at different times on different versions of U  :   let us coin a phrase and call it "a moody blitch"



oh yes mc and [mpv]("https://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CDcQFjAA&url=https%3A%2F%2Flaunchpad.net%2F~mc3man%2F%2Barchive%2Fubuntu%2Fmpv-tests&ei=_bgKVIepFIXSaJLegvgC&usg=AFQjCNEFpXdjZfikCbnBDiAxEh-VXSI-tA&sig2=mK-KUfa9ksnqKk1kgq1dXA&bvm=bv.74649129,d.d2s") of course     all you need is      > mpv url   fast and great     and forgot [**smtube**]("http://smplayer.sourceforge.net/en/smtube") that is great too to bypass Ubuntu Browsers

---

### Post by mc4man on 2014-09-08
> **andrew.46 said:**
> Mind you the latest vlc from git had no trouble with this and the NASA vid you linked to from Launchpad.... Not sure which part of the logs would be useful to you to find the issue though?

It seems the issue is the vlc 2.2.x source that ubuntu is using , -  2.1.x, newer 2.2.x &  3.0-git are fine. 
(Ubuntu has decided to go with 2.2.0pre.. in 14.10 even though vlc has yet to release it. Myself will not be using 14.10 but was trying that source in 14.04..

---

