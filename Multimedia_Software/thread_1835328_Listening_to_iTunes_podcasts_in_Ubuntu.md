---
title: "Listening to iTunes podcasts in Ubuntu"
date: 2011-08-29
forum: Multimedia Software
---

### Post by Lars Noodén on 2011-08-29
How can podcasts from iTunes be loaded in Ubuntu?  Is it even possible?

[http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly)

[http://itunes.apple.com/us/podcast/floss-weekly/id140847216](http://itunes.apple.com/us/podcast/floss-weekly/id140847216)

---

### Post by howefield on 2011-08-29
Add a new podcast in Rhythmbox or Banshee ? 

[http://leoville.tv/podcasts/floss.xml](http://leoville.tv/podcasts/floss.xml)

---

### Post by jeremybentham on 2011-08-29
One of the few things I miss from windows is itunes which really is great at sourcing and subscribing to podcasts.

Using eg rhythmbox you need to put the xml feed into new podcast to subscribe. It&#347; not always obvious where to get the xml feed and for this reason I prefer itunes.

Id be interested to hear if anyone has managed to get itunes running in ubuntu...

---

### Post by Lars Noodén on 2011-08-29
> **jeremybentham said:**
> ...Using eg rhythmbox you need to put the xml feed into new podcast to subscribe. It&#347; not always obvious where to get the xml feed ...

I'm not finding it.  I see the link in iTunes but it seems to be missing information specific to the audio I am trying to get.

---

### Post by nothingspecial on 2011-08-29
Try this link, it has helped with my distance learning course

[http://www.ubuntugeek.com/tunesviewer-itunes-university-media-and-podcasts-in-linux.html](http://www.ubuntugeek.com/tunesviewer-itunes-university-media-and-podcasts-in-linux.html)

---

### Post by gordintoronto on 2011-08-29
Miro can handle many podcasts.

---

### Post by Lars Noodén on 2011-08-30
Neither Rhythmbox nor Miro seem to be able to get at these:
[http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly)

---

### Post by shantiq on 2011-08-30
you can try this mayhaps


1. download and install [**this deb file**]("http://ubuntuforums.org/attachment.php?attachmentid=198933&d=1312132095") for tunesviewer
2. find tunesviewer in applications/internet
3. search for what you want ; more choices from following [**link**]("http://itunes.apple.com/vn/genre/podcasts/id26")


i tested it on floss weekly      flawless    see image attached

---

### Post by Lars Noodén on 2011-08-30
If it's in the official repositories, I'll take a look but it does not look like it is there.

---

### Post by shantiq on 2011-08-30
Larsen i have attached the deb in the previous post
Simply download and double click      it is a safe file


shan  ::)))

---

### Post by Lars Noodén on 2011-08-30
I've learned over time that to simplify life, I only do the official repositories.  Thanks though.

---

### Post by shantiq on 2011-08-30
> **Lars Noodén said:**
> I've learned over time that to simplify life, I only do the official repositories.  Thanks though.



well it in the repositories just checked on natty


so


```
sudo apt-get install tunesviewer

```


nice little   app    enjoy

---

### Post by Lars Noodén on 2011-08-30
It's not in Oneiric yet.  I'll keep it in mind though.  I think the problem I have is more due to malformed links at the iTunes site than anything else.

---

### Post by nothingspecial on 2011-08-30
> **shantiq said:**
> Larsen i have attached the deb in the previous post
Simply download and double click      it is a safe file


shan  ::)))

Same thing I linked in my post, it is safe, but rules are rules.

---

### Post by gordintoronto on 2011-09-01
> **Lars Noodén said:**
> Neither Rhythmbox nor Miro seem to be able to get at these:
[http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly)

I ran Miro, searched for floss, and added floss-weekly to my feeds. Works just fine.

---

### Post by Lars Noodén on 2011-09-01
> **gordintoronto said:**
> I ran Miro, searched for floss, and added floss-weekly to my feeds. Works just fine.

Ok got it that way. Thanks. I was looking to be able to do it the regular way, just grabbing a URL and putting that in.  This new way is something I'll have to look at more.

Edit: It seems like a complicated, convoluted way to get at the file for playback.  The 'old' way is much simpler with far fewer steps needed.

---

### Post by Loevborg on 2011-10-03
The trouble is less with the software but with the podcasts' making it hard for you to find the right RSS feed. To find it, go to [http://twit.tv/show/floss-weekly](http://twit.tv/show/floss-weekly), click on "Subscribe to audio" and then select RSS. That ought to work. I can recommend gPodder to listen to the podcasts, too.

---

