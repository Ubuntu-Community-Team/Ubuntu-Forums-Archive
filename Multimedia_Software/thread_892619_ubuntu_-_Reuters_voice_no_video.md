---
title: "ubuntu - Reuters voice no video"
date: 2008-08-17
forum: Multimedia Software
---

### Post by united on 2008-08-17
I used to have video and voice at 
[http://www.reuters.com/news/video](http://www.reuters.com/news/video)
not sure just when but now I only get sound (no video) did I do something, did a update do something or did Reuters change something. Any help would be appreciated.

ubuntu 8.04 with all updates applied 

thanks - John

---

### Post by Linux&amp;Gsus on 2008-08-17
I just quickly tried it. Works perfectly fine for me.
My setup is Kubuntu 7.10, 32bit system, KDE 3.5.9, Firefox 2.0.0.16, all updates installed. I have the "NoScript" add-on in Firefox, as soon as I allowed Reuters it started playing with sound.
I don't know what you have setup. But maybe try another browser. Also maybe check if there are available updates. You got another computer or a friends computer to try?

Those are just my spontaneous thoughts. Don't know if they are any helpful.

Cheers.

---

### Post by united on 2008-08-17
I have tried several different browsers still voice no video in all.

---

### Post by crazyjimbo on 2008-08-20
I was having this same problem, with the same setup as you. It turns out that there is no problem with the video itself, there is just *another* blank flash application on top of it which obscures the video. Hence why you can still hear the sound. I got around this by blocking the top flash app with Adblock. The URL you need to block is 

```
http://www.reuters.com/resources/flash/video_skin.swf
```

I have no idea why this happened and whether it is a bug with their site, Firefox, Flash or something else. But at least now I can watch my news!

---

### Post by paletti on 2008-08-29
Thanks, that worked fine for me! :)

---

### Post by mikeys749A on 2008-08-31
I have hardy x64 and have EXACTLY the same problem as you. Do you know of any solution???



> **united said:**
> I used to have video and voice at 
[http://www.reuters.com/news/video](http://www.reuters.com/news/video)
not sure just when but now I only get sound (no video) did I do something, did a update do something or did Reuters change something. Any help would be appreciated.

ubuntu 8.04 with all updates applied 

thanks - John

---

### Post by ad_267 on 2008-09-24
I sent them an email and got a reply. They have a FAQ about this at [http://reuters-en.custhelp.com/cgi-bin/reuters_en.cfg/php/enduser/std_adp.php?p_faqid=1268&p_created=1222256289](http://reuters-en.custhelp.com/cgi-bin/reuters_en.cfg/php/enduser/std_adp.php?p_faqid=1268&p_created=1222256289)

Apparently flash player 10 should fix this issue.

---

### Post by lazy gun on 2008-10-02
> **crazyjimbo said:**
> I was having this same problem, with the same setup as you. It turns out that there is no problem with the video itself, there is just *another* blank flash application on top of it which obscures the video. Hence why you can still hear the sound. I got around this by blocking the top flash app with Adblock. The URL you need to block is 

```
http://www.reuters.com/resources/flash/video_skin.swf
```

I have no idea why this happened and whether it is a bug with their site, Firefox, Flash or something else. But at least now I can watch my news!

Thanks for that! It worked fine for me. :popcorn:

---

### Post by PatricioLearner on 2008-10-08
Yes, it worked for me too. I am using Flash 9,0,48,0 However, a newer version was producing choppy video... so be careful if you update.

---

### Post by dilidon on 2008-11-23
> **ad_267 said:**
> I sent them an email and got a reply. They have a FAQ about this at [http://reuters-en.custhelp.com/cgi-bin/reuters_en.cfg/php/enduser/std_adp.php?p_faqid=1268&p_created=1222256289](http://reuters-en.custhelp.com/cgi-bin/reuters_en.cfg/php/enduser/std_adp.php?p_faqid=1268&p_created=1222256289)

Apparently flash player 10 should fix this issue.

Thanks for doing that. Im using 
    File name: libflashplayer.so
    Shockwave Flash 10.0.0 d569
I still had the problem. Using the adblock solution offered above worked.

---

