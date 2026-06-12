---
title: "nvidia GPU running hot"
date: 2010-07-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by joske on 2010-07-14
Hi,

I'm running with nvidia-current, and for some reason, the GPU temp is always really high (90+ degrees C), and the fan blowing all the time. This was not the case in Lucid on same hardware. I'm using metacity with compositing, and no graphical intensive app running.

Anyone else seeing this?

---

### Post by jpeddicord on 2010-07-14
> **joske said:**
> Hi,

I'm running with nvidia-current, and for some reason, the GPU temp is always really high (90+ degrees C), and the fan blowing all the time. This was not the case in Lucid on same hardware. I'm using metacity with compositing, and no graphical intensive app running.

Anyone else seeing this?

That's strange. If the fan is constantly on, it should be at least cooling it down a *little*. My guess is that the sensor is broken and is reading the wrong temperature; there's no way it should be getting that hot with fans always on.

Where are you getting your temperature readings from? Both Nvidia X Settings > Thermal and the nvidia sensor are reporting 39C for me.

What's your graphics card model? Also, is anything blocking the fan or output?

---

### Post by alexmurray on 2010-07-14
Try posting on [NVIDIA's Linux forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14") and you'll probably get a reply direct from one of the NVIDIA driver developers since I think some others over there have been having similar issues: [http://www.nvnews.net/vbulletin/showthread.php?t=148976](http://www.nvnews.net/vbulletin/showthread.php?t=148976)
[http://www.nvnews.net/vbulletin/showthread.php?t=151931](http://www.nvnews.net/vbulletin/showthread.php?t=151931)

---

### Post by cariboo on 2010-07-14
Ambient temp in my house at the moment is 30°C, nvidia-settings reports gpu temp at 49°C

---

### Post by MacUntu on 2010-07-15
> **cariboo907 said:**
> Ambient temp in my house at the moment is 30°C, nvidia-settings reports gpu temp at 49°C

30°C room temperature? Holy sh*t! :-o

I'm at 27°C room temperature and the GPU temp is at 50°C (nvidia-current/256.35).

---

### Post by jpeddicord on 2010-07-15
Ok, maybe mine just has good cooling? It never idles above 40°C on the lowest fan speed.

Edit: though, it is a bit chilly in here. ~22°C room.

Anyway, I still think that, for 90°C, the sensor is just broken. If you really think the card is that hot, then you may want to be contacting the manufacturer if it's under warranty. If the hardware sensor is broken (ie, you've determined it isn't a software issue somehow) then that could probably also be covered.

---

### Post by cariboo on 2010-07-15
Just to add a bit to what jpeddicord said, if your gpu is actually running at 90°C, it should affect the rest of the temps inside the case, you should see higher than normal motherboard temps too.

---

### Post by joske on 2010-07-15
> **jpeddicord said:**
> That's strange. If the fan is constantly on, it should be at least cooling it down a *little*. My guess is that the sensor is broken and is reading the wrong temperature; there's no way it should be getting that hot with fans always on.

Where are you getting your temperature readings from? Both Nvidia X Settings > Thermal and the nvidia sensor are reporting 39C for me.

What's your graphics card model? Also, is anything blocking the fan or output?

Got the reading from nvidia-settings. I checked there because I noticed the fan was blowing all the time. 

I think it's a Quadro 110 NVS if I remember correctly (don't have the system handy here)

The laptop was just sitting on the table with ambient temp around 24 degrees.

---

