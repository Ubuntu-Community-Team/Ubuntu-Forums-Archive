---
title: "Will ipod classics work with ubuntu?"
date: 2009-08-05
forum: Multimedia Software
---

### Post by cody7002002 on 2009-08-05
I currently have an ipod touch but am buying a 120GB ipod classic soon. I know that the ipod touch isn't very easily compatible with ubuntu but I'm not too sure about the ipod classic. Is there some program or work-around for getting it to work with ubuntu?

---

### Post by Omnutia on 2009-08-08
Having tried to get my iPod classic working with Ubuntu, you get songs and that's about it.

Amarok used to be pretty competent at managing an iPod. Once you worked out how, it wasn't hard to sync over your podcasts manually; You could even add videos.

With the release of Amarok 2, it became needlessly complex for my uses so I switched to using Banshee which has no functioning support for anything other than songs and play-lists. Podcasts are coppied but the podcast menu on the iPod itself remains empty. I had videos work once but they were all copied to the music videos section.

---

### Post by PureLoneWolf on 2009-08-09
I have a 120gb Classic and don't have any issues at all on 9.04 Jaunty.

Gtkpod-aac from the repos manages my video, podcasts and photos, and I use Amarok 1.4 on Jaunty (see my sig) for my music (as I prefer the interface for my 100gb collection)

If I ever need to perform a restore, I use XP in a Virtualbox PUEL installation.

Hope that helps

---

### Post by Omnutia on 2009-08-10
Man I missed Amarok 1.4. I'll give this method a try untill Banshee gets itself in gear.

---

### Post by cody7002002 on 2009-08-12
Well I will be only using the iPod for music so how difficult would it be to get a program working with it?

---

### Post by jrox717 on 2009-08-12
Shouldn't be too hard. I used Rhythmbox with my iPod nano for a while and it worked flawlessly without any configuration. Or you could try gtkpod as PureLoneWolf suggested. Try out a few programs and see which one works/ you like best.

---

### Post by PureLoneWolf on 2009-08-12
It's very easy - Ubuntu will recognise and mount the device automatically - From there it is down to whatever software solution you choose.

Amarok sometimes struggles to autodetect devices, so you have to tell it where the ipod is mounted... normally /media/IPODNAME

GTKPod finds it automatically without issue for me and I don't know about Banshee.

If all else fails, you can even run iTunes through a Virtualbox PUEL XP installation - I have done this for friends.

---

