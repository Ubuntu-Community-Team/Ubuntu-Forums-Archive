---
title: "Amarok + iPod"
date: 2009-02-09
forum: Multimedia Software
---

### Post by Atzu on 2009-02-09
Right now I'm using Amarok 1.4.10 with my iPod nano (4th gen) but every time I connect it and then disconnect the database of my iPod will get messed up... Albums don't match covers... :/ it's quite annoying every time that happen I need to go back to windows -> itunes and re-add all music to my iPod. 


Thanks in advance.

---

### Post by djbushido on 2009-02-09
see if this helps:
```
sudo apt-get install libmtp
```
Also check in Amarok settings to make sure device type is set to iPod.

---

### Post by Atzu on 2009-02-09
> **djbushido said:**
> 
```
sudo apt-get install libmtp
```


Hmm That was a fast answer :P

But I can't install libmtp :/ I need any special repo or something?
```
andres@Andres-HP:~$ sudo apt-get install libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmtp
```

EDIT: Hmm I searched synaptic package manager and found that I have installed libmtp8

More info: This also happen with songbird (1.0.0) (windows and ubuntu) :/ if anyone know about a pretty media player that support my ipod model please let me know! (I know foobar2000 support it sadly i don't like to wine to get it to work and actually won't really support my ipod cuz of wine)

---

### Post by greyfox1 on 2009-02-09
I have had this problem in the past with my 5th gen iPod.  I don't recall what program I was using at the time because I've used so many.  However, it seems to me that restoring the iPod then starting fresh should help (you can do this in Songbird easily).  Have you tried this at any point?

Also, if you use MediaMonkey (under a Virtualization program or WINE) there is an option called "Rebuild Device Database" that might help as well.  Good luck!!

---

### Post by Atzu on 2009-02-09
Well this is like the third time i restore my ipod (using iTunes) not sure how to do it on songbird haven't searched songbird at all :p Next time I'll try that and see what happens else I'll post again here... Anyway I think that will be in the next 2-3 hours :lolflag: thanks a lot for helping.

---

### Post by Atzu on 2009-02-09
Sorry for double post >.<


> **greyfox1 said:**
> I have had this problem in the past with my 5th gen iPod.  I don't recall what program I was using at the time because I've used so many.  However, it seems to me that restoring the iPod then starting fresh should help (you can do this in Songbird easily).  Have you tried this at any point?

Also, if you use MediaMonkey (under a Virtualization program or WINE) there is an option called "Rebuild Device Database" that might help as well.  Good luck!!

I tried restoring my iPod with songbird and tried add songs, the songs will be added but not the album art :/ so it doesn't really work... Now I use Windows to play games and sync my iPod :/ Thanks for your help again :D.

---

### Post by greyfox1 on 2009-02-09
Oh, sorry, I should have been more specific.  What I meant was you could restore your iPod to factory using Songbird (basically wipe the slate clean) and start fresh by syncing by using your program of choice.  I wouldn't recommend Songbird for this, however, because it unfortunately doesn't support artwork yet.  

I definitely recommend AmaroK 1.4 for syncing.  I actually just wrote about this earlier in another thread - see my post [here]("http://ubuntuforums.org/showthread.php?p=6705812#post6705812").  I try not to use Windows for anything I don't really need to and I'm pretty sure you can understand what I mean ;)  

I hope this helps!

---

### Post by Atzu on 2009-02-09
I see :o well now i understand what u mean :p I'll see what i can do with amarok I still think if I add music with amarok will still be messy, maybe ipod db now is organized different (well not maybe... i bet it is), but anyway I'll try it later, I understand when you say you try not to use windows.

---

