---
title: "Problem with youtube and flashh"
date: 2008-11-02
forum: Multimedia Software
---

### Post by magusxp on 2008-11-02
I have this problem with flash videos, I play them well and stuff but videos, they dont run continuously they kinda have gaps or the image gets stucked then jumps to another frame, any idea how to solve this?

---

### Post by ciscosurfer on 2008-11-02
> **magusxp said:**
> I have this problem with flash videos, I play them well and stuff but videos, they dont run continuously they kinda have gaps or the image gets stucked then jumps to another frame, any idea how to solve this?Choppy video could be a symptom of not having the proper video drivers installed and enabled.  Do you have your restricted drivers, or the like, enabled?

---

### Post by ashmew2 on 2008-11-02
Which version are you using ? I had those kind of problems when i used Hardy. But since doing Intrepid's fresh install and installing the plugins from inside Firefox , they run flawlessly without crashes! :D

---

### Post by ashmew2 on 2008-11-02
I think removing flash first , then updating lists and then installing swf mozilla support , gnash , and flash again should fix it , for that do :

```
sudo apt-get remove swfdec-mozilla gnash mozilla-plugin-gnash flashplugin-nonfree
```

```
sudo apt-get update

```

```
sudo apt-get install flashplugin-nonfree swfdec-mozilla gnash mozilla-plugin-gnash 
```

Restart Firefox after this and check again!

---

### Post by gandaran on 2008-11-02
> 
Code:

sudo apt-get install flashplugin-nonfree swfdec-mozilla gnash mozilla-plugin-gnash


 this will never work! you cant have three deferent flash packages installed! just one of them and the recommended one is flashplugin-nonfree (adobe flash 10)

---

### Post by ashmew2 on 2008-11-02
> **gandaran said:**
> this will never work! you cant have three deferent flash packages installed! just one of them and the recommended one is flashplugin-nonfree (adobe flash 10)

I am running intrepid right now and Firefox told me to install all three of these and after i installed all three the embedded videos started working flawlessly.

---

### Post by gandaran on 2008-11-02
> **ashmew2 said:**
> I am running intrepid right now and Firefox told me to install all three of these and after i installed all three the embedded videos started working flawlessly.
firefox doesn't ask you to install all three, it asks to choose one! any one will work but with different results, you provably have gnash working for you as it usually takes over firefox, the other ones will not work!

edit;
this used to be so on hardy 8.04, now on intrepid 8.10 firefox directs you to the adobe site for flash download!

---

### Post by ashmew2 on 2008-11-03
lol...when i installed flash the embedded video on a site wasnt working..When i installed swfdec-mozilla , it worked but still the video was misbehaving..I installed gnash after that and restarted firefox again and it started working seamlessly! :P

---

### Post by magusxp on 2008-11-06
Ok solved with the gnash thing thanks a lot

---

### Post by magusxp on 2008-11-06
> **ashmew2 said:**
> I think removing flash first , then updating lists and then installing swf mozilla support , gnash , and flash again should fix it , for that do :

```
sudo apt-get remove swfdec-mozilla gnash mozilla-plugin-gnash flashplugin-nonfree
```

```
sudo apt-get update

```

```
sudo apt-get install flashplugin-nonfree swfdec-mozilla gnash mozilla-plugin-gnash 
```

Restart Firefox after this and check again!

This solved my problem thanks a lot !!!

---

