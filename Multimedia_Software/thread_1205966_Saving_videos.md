---
title: "Saving videos?"
date: 2009-07-06
forum: Multimedia Software
---

### Post by Mariane on 2009-07-06
Hi, 

Does anyone know a browser where you can right click on a video (ANY format) and do "open link in new window" (to watch the video full screen) or "save link target as" (to watch the video later offline)? 

I am sooooo fed up with this streaming and flash ****... You watch a video segment, then it stops, then you wait, then you watch another segment... I can't understand why good browsers don't offer the option to save the file by default instead of offering 10000 ways of viewing it and no way to save it... :(

I mean, look at totem for example. It's connected to Seamonkey so it opened the video for me. But in the available options THERE IS SIMPLY NO "SAVE" OPTION! Incredible! Everthing else has a "save" option! How could they forget it??? 

Mariane

---

### Post by ajgreeny on 2009-07-06
There is a firefox movie downloader extension that I have used in the past which allows you to do just that.  see it here in the add-ons web pages.
[https://addons.mozilla.org/en-US/firefox/addon/7851](https://addons.mozilla.org/en-US/firefox/addon/7851)

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Another popular solution is the Video DownloadHelper plugin for Firefox:  [https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

42 Million downloads and counting...

---

### Post by stinger30au on 2009-07-06
if your going to save videos from you tube or the likes, make sure you get the high quality mp4 files

there is a few web sites that do it for free, this is one

[http://www.farkie.com/](http://www.farkie.com/)

---

### Post by ajgreeny on 2009-07-06
Actually, that could be the one I was thinking about.  I just couldn't remember the right name.

---

### Post by Mariane on 2009-07-06
Thank you, all of you. 
Actually I managed to get my video in 
mms:// protocol
was not accepted by firefox and not even by Konqueror (which is more suprising because Konqueror usually accepts anything). 

I did: 

sudo apt-get install mimms

then 

mimms mms://vod-dun.u-strasbg.fr/vod/2009/0128_egc/egc_kodratoff.wmv

and this saved the video in the current folder. Took a while but worked fine. 

The reverse operation: just put your file online as it is, and include an html 
link to it like this, after opening the .html file with a text editor: 

<br>
There is my video <a href="myvideo.wmv">here</a>.
<br> 

Then anyone can watch it easily. (Of course you don't have to write "There is 
my video here", you can say what you like instead, this is just an example).

Mariane

---

