---
title: "Stream audio to sterio"
date: 2011-06-17
forum: Multimedia Software
---

### Post by delta_one_ on 2011-06-17
I have an old computer that I have put Ubuntu on. I would like to connect it to my stereo and stream audio to it from my laptop, so that it plays through the stereo.

I'm hoping to find some software to put onto this old computer to make it work similarly to an airport express.

Anyone know of any software like this? Any ideas would be much appreciated.

---

### Post by amauk on 2011-06-17
[http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/](http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/)

---

### Post by Derek Karpinski on 2011-06-17
Like a Squeezebox?

[http://www.logitech.com/en-us/speakers-audio/wireless-music-systems](http://www.logitech.com/en-us/speakers-audio/wireless-music-systems)

You can probably find a cheap Squeezebox 3 on ebay.  They're great.

---

### Post by delta_one_ on 2011-06-17
Thanks for your quick replies!


> **amauk said:**
> [http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/](http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/)

Unfortunately I do not actually have an airport express, I am trying to make this old ubuntu box have the same functionality as one.



> **Derek Karpinski said:**
> Like a Squeezebox?

[http://www.logitech.com/en-us/speakers-audio/wireless-music-systems](http://www.logitech.com/en-us/speakers-audio/wireless-music-systems)

You can probably find a cheap Squeezebox 3 on ebay.  They're great.

Yeah, that is the kind of thing I am thinking of. Except I was hoping to be able to make one out of this old ubuntu box, instead of having to buy a new product.

Any software you know of to get an ubuntu computer to do what these devices do?

Thanks!

---

### Post by amauk on 2011-06-17
> **delta_one_ said:**
> Unfortunately I do not actually have an airport express, I am trying to make this old ubuntu box have the same functionality as one.Oops, sorry
Just saw the words "airport express" in your post without reading it properly

---

### Post by delta_one_ on 2011-06-17
> **amauk said:**
> Oops, sorry
Just saw the words "airport express" in your post without reading it properly

All good. Btw, congrats, it was your 1000th post =)

---

### Post by nothingspecial on 2011-06-17
There are a number of ways you can do this.

You can install the squeezebox server software on your laptop and play the stream on the old computer using the url

```
http://<ipadress>:9000/stream.mp3
```

So if the ip address of your laptop is 192.168.1.2 you would use


```
http://192.168.1.2:9000/stream.mp3
```

You can play it with any software (vlc, mplayer, etc etc) that will play a stream.

Then you control it from your laptop using the web interface at

```
http://localhost:9000/
```

You don't actualy need a squeezebox.

---

### Post by delta_one_ on 2011-06-17
> **nothingspecial said:**
> There are a number of ways you can do this.

You can install the squeezebox server software on your laptop and play the stream on the old computer using the url

```
http://<ipadress>:9000/stream.mp3
```

So if the ip address of your laptop is 192.168.1.2 you would use


```
http://192.168.1.2:9000/stream.mp3
```

You can play it with any software (vlc, mplayer, etc etc) that will play a stream.

Then you control it from your laptop using the web interface at

```
http://localhost:9000/
```

You don't actualy need a squeezebox.

Thanks for that! that looks like exactly what I want to do, and that software is open source too, is it not? Always a bonus. I will try set that up now

---

