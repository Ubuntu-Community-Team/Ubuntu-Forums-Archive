---
title: "Help with Banshee"
date: 2008-06-17
forum: Multimedia Software
---

### Post by Hashmere on 2008-06-17
Hey Guys! First Time poster and I am also pretty new to Linux in general.

On my computer I have a 35 gig partition for Linux (ubuntu: Hardy Heron) and the rest I have for Vista. On Vista I have an Itunes library set up.

 I downloaded and installed Banshee through the Synaptic Package Manager and the installation seemed to go fine. 

 
I then import the music from my Itunes Music folder which of course is stored on the Vista Partition. All 2500 songs or so are imported and i can see them in the player yet I can not play any music. I click the song i want to listen to and nothing happens. It recognizes the song because at the bottom it properly displays common artists and the top songs by the artist i am trying to listen to yet there is no music!!
 
I dont think the problem is that the music is on a different partion because i can listen to the same music if i use Rythmbox Music Player.

 Anyone got an ideas or tips for me? And please ask if i did not make something clear.

---

### Post by boombox1387 on 2008-08-04
Hey, did you ever solve this?  If not, I don't know a whole lot either, but here are some things that might help.  First of all, go to Help > About, because I'm just curious about which version of Banshee you're using.  I think the Banshee from Synaptic in Hardy is old (pre v1.2).  If you have anything older than Banshee-1, you may just want to start over and install the new one.  Instructions here: [http://banshee-project.org/download/#ubuntu]("http://banshee-project.org/download/#ubuntu").

Hopefully that will help, although I would guess by now you've figured something out.

---

### Post by boombox1387 on 2008-08-04
Sorry, this link would be a better website to tell you how to install the new Banshee on Hardy: [https://edge.launchpad.net/~banshee-team/+archive]("https://edge.launchpad.net/~banshee-team/+archive")

---

### Post by Hashmere on 2008-08-15
Hey,
Thanks for the advice. Shortly after posting the original message i did upgrade to the new banshee. I got it working but it is still quite buggy. Many times i have to reimport my music and sometimes songs wont play at all.

---

### Post by kidwithshirt on 2008-08-15
Hashmere. Don't know if this applies, but if Firefox is open first and you opened a flash-streamed video then any music player wont work. This is a conflict I am trying to resolve. Just open music player (banshee) first then firefox.

Also, the NTFS disk must be mounted first too. When you open up computer, open up your C: drive whatever in explorer to first mount it.

I am totally new to linux and these are my work arounds.

---

### Post by Hashmere on 2008-08-15
Could you give me more information about mounting the partition? And if i were to mount the partition, would it effect the performance of the computer when i run Vista?

---

### Post by kidwithshirt on 2008-08-15
> **Hashmere said:**
> Could you give me more information about mounting the partition? And if i were to mount the partition, would it effect the performance of the computer when i run Vista?

I was told to edit something called "fstab" (or fsatb? pretty sure it's the former) 

However I have yet to do that. It works fine for me. Pretty much my understanding is that mounting is letting linux know that the NTFS drive exists so the music player -- I assume doesn't mount properly -- recognizes the directory from your vista partition

Just pretty much don't sleep vista then boot into ubuntu, because you couldn't access your vista partition that way. I always sleep vista then boot into ubuntu for something but then my music won't work at all. :popcorn:

---

### Post by Hashmere on 2008-08-15
I dual boot Linux and Vista so when my linux is running vista is not. That is my understanding. I can still axcess my windows files however under "OS". I set the root of my music library to "/media/OS/Users/David/Music/iTunes". This works most of the time but often i have to reimport the files.

---

