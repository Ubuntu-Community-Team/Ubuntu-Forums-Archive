---
title: "Problems with watching videos online"
date: 2015-06-13
forum: Multimedia Software
---

### Post by Illoca on 2015-06-13
[COLOR=#212121][FONT=Times New Roman]Hello everyone,[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]I am writing you because I need your help to try to solve some problems related to visualising videos online (scattering, continuous buffering) and generally slow browsing. The problem is there using all the browsers I have tried (e.g. chrome / chromium and firefox). I should start by stating that I am not an expert, so be please be patient if the information I provide is a bit vague at times.[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]Quick background: I'm using an old laptop (Acer Series 2000 with Pentium M 1.6GHz, 2GB of RAM and ATI Mobility Radeon 9200).[/FONT][/COLOR]
[COLOR=#212121][FONT=Times New Roman]For years I used Ubuntu, but from release 11.04 I haven’t updated it anymore because my graphic card was not able to handle Unity. Everything worked acceptably, except for visualising videos online and slow browsing at times.[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]Last week I decided to move on and install Xubuntu 14.04 LTS. Everything works perfectly (and I'm very happy with it), except for watching videos online (eg Youtube, streaming tv, etc).[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]I tried to read a little bit around and I think that one of the possible problems is the fact that Flash (and perhaps others) mainly use the GPU instead of the CPU. Since the GPU is the weak link in my laptop )as shown by the problems with Unity) I thought I had found the problem. To confirm this I tried to open e youtube videos through network stream with VLC (which should mainly use the CPU), and they work perfectly.[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]So I tried to disable hardware acceleration in chrome (I mainly use this browser), but it didn’t change anything! And I now find myself in a dead end.[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]On the one hand it makes me think that the laptop simply cannot make it being too old, but on the other hand I think hat hardware should be enough given:[/FONT][/COLOR]
[COLOR=#212121][FONT=Times New Roman]• With old version of Ubuntu I had no problems watching videos online[/FONT][/COLOR]
[COLOR=#212121][FONT=Times New Roman]• Opening videos  as a network stream with VLC I have no problems[/FONT][/COLOR]
[COLOR=#212121][FONT=Times New Roman]• Opening normal video files (avi, mkv, mp4) from my hard drive I have no problems up to 720p (1080p do have problems, but this is due to my VGA graphic card, and I can live with that)[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]I would be incredibly grateful if you were able to help me with this problem.[/FONT][/COLOR]

[COLOR=#212121][FONT=Times New Roman]Many thanks and greetings[/FONT][/COLOR]

---

### Post by kerry_s on 2015-06-13
your specs are similar to mine, i'm guessing what's happening is memory related as chrome will easily reach 600->800mb ram.

sudo apt-get install zram-config
then reboot

that will compress swap in ram, which will help with performance. you may want to consider using midori browser when you want to watch streaming stuff.
make sure you check additional drivers to make sure you have all available.

---

### Post by monkeybrain20122 on 2015-06-14
Maybe flash is too resource hungry, try this  [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)
It works for many sites that use flash and other formats (html5, quicktime etc) for streaming videos, since you said you can watch 720p locally this should work very well for you.

You need to have up to date mpv and Youtube-dl in your system.
Get mpv from 
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)
and youtube-dl from 
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

---

### Post by Illoca on 2015-06-14
Hi both, thanks a lot for the suggestions, I've been really helpful. I have tried all of them, and the most successful seems to have been the mpv mozilla add-on. With this add on youtube videos are pretty decen on firefox, although sometimes they speed up or slow down a bit weirdly. But definitely a step forward. Zram may have helped as well, although no improvements on chrome nor using midori. Any other suggestions to build on these?

---

### Post by kerry_s on 2015-06-14
sounds like slow internet issues. how are you connected ?
[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by Illoca on 2015-06-15
This is the result:

[http://www.speedtest.net/my-result/4435047066](http://www.speedtest.net/my-result/4435047066)

Could it really be just the connection? With other laptops or on the mobile it works fine..

---

### Post by kerry_s on 2015-06-15
i don't think so 5mb/s is enough to get smooth streaming if others are not streaming while you are.
i'm going to assume it's your vid driver, try some googling for a fix.

---

### Post by Illoca on 2015-06-16
It seems like ATI doesn't update Mobility Radeon 9200 drivers anymore. Do you know where I could find some non proprietary ones?

---

### Post by kerry_s on 2015-06-16
if nothing is in additional drivers, you probably using the open source drivers.

---

### Post by shantiq on 2015-06-17
Look    forget watching ANYTHING in browsers ...    in my time with Ubuntu [2009 =>>]or any Linux it has always checked buffered etc...   and it has nothing to do with Connection Speed it seems     but with the  flash pepper  gnash  etc   


the EASY way to bypass all of this once and for all is to **NOT use a browser**    find the url of your video   and play it in VLC   ctrl +v + enter

or cvlc    ```
 cvlc https://www.youtube.com/watch?v=koxpJ7nhz2Y
```    no fuss   no check   no buffer

I know in Windows it does none of this stuff;   but I do not have Windows and personally do not wish for it;  but here just bypass the browsers;   your viewing life will become much easier.


Or use mpv   even better and more stable than vlc

```
sudo add-apt-repository ppa:mc3man/trusty-media
```
```
sudo apt-get update ; sudo apt-get install mpv
```


then   run     ```
mpv https://www.youtube.com/watch?v=koxpJ7nhz2Y
```


This simple!    and you can seek back and forth so easily   too!

---

