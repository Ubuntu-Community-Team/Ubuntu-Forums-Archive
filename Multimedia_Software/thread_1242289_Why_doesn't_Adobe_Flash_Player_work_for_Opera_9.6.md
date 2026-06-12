---
title: "Why doesn't Adobe Flash Player work for Opera 9.6?"
date: 2009-08-17
forum: Multimedia Software
---

### Post by cardinalsfan030 on 2009-08-17
It works fine for Firefox, but when I try to watch a video say on youtube or hulu, I get nothing.  I just use Opera for my backup broswer incase Firefox starts acting up.  I went here > [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP) just to make sure that I had it installed and my GDebi package installer said that it was.  So is there a command that I can run from the terminal to install Flash Player for Opera?
Thanks for your help :)

---

### Post by HappyFeet on 2009-08-17
You need to download the .tar.gz flash file from [here]("http://get.adobe.com/flashplayer/"). Right click and "extract here". As root, you will now put the **libflashplayer.so** file into /usr/lib/opera/plugins. 

I'll assume you have the libflashplayer.so file on your desktop. Do:
```
sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib/opera/plugins
```
Make sure the D in Desktop is capitalized. And change **your_user_name** to the name you login with. ;)

Restart opera if open.

---

### Post by cardinalsfan030 on 2009-08-17
> **HappyFeet said:**
> You need to download the .tar.gz flash file from [here]("http://get.adobe.com/flashplayer/"). Right click and "extract here". As root, you will now put the **libflashplayer.so** file into /usr/lib/opera/plugins. 

I'll assume you have the libflashplayer.so file on your desktop. Do:
```
sudo cp /home/your_user_name/Desktop/libflashplayer.so /usr/lib/opera/plugins
```Make sure the D in Desktop is capitalized. And change **your_user_name** to the name you login with. ;)

Restart opera if open.

Ok i downloaded the file, extracted it, I kept everything on my desktop just to make it simple, the file shows in    	usr/lib/opera/plugins but i still have no flash.  I have restarted Opera a couple of times, but still nothing.

---

### Post by HappyFeet on 2009-08-17
I'll bump this for you in the hopes someone else knows a different way to do it. I don't know what else to say, as it always works for me.

---

