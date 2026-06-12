---
title: "iPhone cannot play music"
date: 2010-10-21
forum: Multimedia Software
---

### Post by prefec2 on 2010-10-21
I have a rather strange problem and it surfaced just recently. Most likely it has something to do with switching from Ubuntu 10.04 to Ubuntu 10.10.

When I upload music to my iPhone 3gs with iOS 3.1.3 (7E18) it shows in iTunes, however the phone skips over the music. This does not happen to songs I uploaded via rhythmbox two weeks ago. 

For a test purposes I deleted the old songs from the iPhone and tried to put them on again. Now I cannot listen to them as well. At least I know it has nothing to do with the used mp3 coding.

I even can use the iPhone as a harddrive for that music and play music from their through rhythmbox.

The song list shows the right sizes on the iPhone.

It is save to say that the data is transfered and the music database is updated. So there must be a strange error in detecting the length of the songs which would point to a problem in updating the iPhone database. However, I cannot be sure, because the phone is not reporting any errors.

And as the iPhone didn't change its hard- and software. It is obviously something different with my ubuntu.

---

### Post by prefec2 on 2010-10-22
I'll file a bug report. I can produce the desired result using banshee. So it has nothing to do with the underlying iPhone connector stuff.

---

### Post by vkcaspervk on 2010-10-29
Same problem, I had songs synced when I was version 10.04 they play just fine, the ones I just synced with 10.10 will not play. It shows the images, song names, even goes like its going to play, then bounces back like something is just not right. : sighs :

---

### Post by alex30002 on 2010-10-29
> **vkcaspervk said:**
> Same problem, I had songs synced when I was version 10.04 they play just fine, the ones I just synced with 10.10 will not play. It shows the images, song names, even goes like its going to play, then bounces back like something is just not right. : sighs :

same mine does

---

### Post by prefec2 on 2010-12-10
Looks like more people have this or a similar problem. 
[https://bugs.launchpad.net/rhythmbox/+bug/553301](https://bugs.launchpad.net/rhythmbox/+bug/553301)

However, I can still reproduce it bug with iOS 4.x

---

