---
title: "AOL Radio-Rhythmbox"
date: 2008-05-22
forum: Multimedia Software
---

### Post by lordfkiller on 2008-05-22
When I try to play an AOL Radio channel in rhythmbox, I get "A text/html decoder plugin is required to play this stream, but not installed."

Any idea?

---

### Post by wolfen69 on 2008-05-22
try
```
sudo apt-get install tcllib
```

i didnt see an AOL stream in rhythmbox. where did you find it?

---

### Post by lordfkiller on 2008-05-22
Well after reading some articles in this regard, the URL does not seem to be correct(http). Is it possible to listen to AOL radio using Rhythmbox at all?
Where can I find some radio stations for Rhythmbox?

---

### Post by wolfen69 on 2008-05-22
for online radio i recommend tunapie. it has 1000's of stations(every kind of music from all over the world) from shoutcast, plus online tv.
```
sudo apt-get install tunapie
```

---

### Post by lordfkiller on 2008-05-22
Is it possible to listen to say BBC radio through Rhythmbox? Which channels can be listened to in general? I'm new to Internet Radio.

---

### Post by Dlizard on 2008-06-10
> **lordfkiller said:**
> Is it possible to listen to say BBC radio through Rhythmbox? Which channels can be listened to in general? I'm new to Internet Radio.

I can't listen to BBC (and other radios, like RAI, Classical 96.8, etc...) through Rhythmbox. I add the URL,then when I click Play I hear a terrible garbled/distorted sound. When I go to the webpage of the radio I can hear the program normally. Does anybody know how to fix this problem?

---

### Post by markbuntu on 2008-06-11
Tunapie will load stations into rythmbox automatically. You can also use streamtuner which connects to live365 and a some other places but you have to cut and paste the urls manually from the properties pop up for the station to the new internet radio station box in Rythmbox.

You can also do this from pretty much any radio stations web site by playing the stream in your browsers player and then copying the url into the rythmbox new internet station box. Some stations have more than one stream and sometimes you have to try different ones to get the right one for rythmbox. The Windows Media stream usually works. Also, some stations are now streaming in some new proprietary windows format which will not work in any player in Ubuntu. If you run across one of those, complain to the station.

Streamtuner was written for xmms which is deprecated and no longer avialable in the repos. A new version of streamtuner is working its way from Gnome to Ubuntu so hopefully we will see it working with rythmbox soon.

---

