---
title: "Ipod + banshee = no music on ipod!"
date: 2010-03-12
forum: Multimedia Software
---

### Post by hatapota on 2010-03-12
I've had ubuntu on my computer for a whole fortnight now, and decided last night that it was about time I sorted out my ipod. I'm using Banshee, which I like, and I have a 3g ipod nano. I plugged it in and was asked what program I wanted to use, I selected Banshee, and... nothing. I eventually got Banshee to see the ipod by following the instructions here:
[http://luisgmarine.blogspot.com/2010/01/fix-ipod-detection-in-ubuntu-910.html](http://luisgmarine.blogspot.com/2010/01/fix-ipod-detection-in-ubuntu-910.html)
 
However, Banshee then said it couldn't read the ipod and that it needed to rebuild the database. So, I did that. When it had finished I could see all the tracks in my ipod - great! Or so I thought... I tried to drag and drop some tracks from my music library to the ipod but I soon noticed there wasn't a sync button, so I decided to leave it for the evening. 
 
I closed Banshee, ejected the ipod, and then had a look at the ipod - and it was empty!!! I plugged it back in and Banshee said that it had 7gb "other" data (instead of the 7gb music tracks that should be on there) and asked to rebuild the database again. I did that, and the data type changed to music instead of "other". But it still wouldn't let me sync to the ipod, and there is still nothing on the ipod when I switch it on.
 
This morning I tried using rhythmbox to sort out the ipod. I had to switch auto mounting back on, and then rythymbox could recognise the ipod and also see all the music on it. But I can't do anything beyond there.
 
I've been doing a lot of googling and looking on here for what to do next but I'm stumped. I don't mind about losing everything on the ipod (I don't really use playlists and all the music is on my computer so I can easily stick more stuff on there) but I do need to be able to use SOME sort of music player to sync my ipod (and I really don't mind what program I use, as long as it works). Going to work today without my ipod has made me realise how dependent I am on it!!
 
Any help much appreciated!! :)

---

### Post by tgpraveen on 2010-03-12
get latest banshee version from the daily ppa and i think it works there. though not sure.

---

### Post by hatapota on 2010-03-12
Awesome - thanks, I will try that tonight. 
 
Do you reckon that will bring my ipod back to life? This weekend I have access to a laptop running Windows/itunes so if I need to restore factory settings then I can.

---

### Post by rob22941 on 2010-03-12
I just posted this on another thread. Banshee released 1.5.5 two days ago and it fixed all my ipod problems. I removed the version and it's add-ons on my computer using synaptic and reinstalled according to the site below. Everything's working perfectly now for me.

[http://banshee-project.org/download/](http://banshee-project.org/download/)

---

### Post by hatapota on 2010-03-12
Great - I'm on my way home now to try it out! I will report back...
 
Thanks :)

---

### Post by hatapota on 2010-03-12
I did as you suggested, rob22941, and uninstalled Banshee, then reinstalled the latest version from the PPA.

On the plus side, my ipod is recognised in Banshee straight away, without having to disable auto mount. It still says I need to rebuild the database, but after that it does recognise that there are media files on the ipod. After that, I can look through the ipod library, and I can seem to be adding things to the ipod, but when I unplug it, again, nothing! I just had a scroll through the (empty seeming!) ipod and it is very slow and unresponsive - taking a few seconds to go from menu to menu.

Has anyone had this before - and what do you do next?! All help HUGELY appreciated.

---

### Post by Chronon on 2010-03-12
The problem seems to be mismatched versions of the iTunesDB.  Banshee seems to be rebuilding it because it can't properly parse the one that iTunes made.  In turn, the iPod's firmware can't understand the deprecated format that Banshee wrote to the iPod.  At least, this seems to explain the symptoms you described.  Your files are still on the iPod and could be recovered to your computer's HD if needed (just copy the iTunes_Control/Music directory from iPod to PC).  

I don't know any specifics about which firmware versions (on which models) are expected to work as I haven't used an iPod in a few years.  This just seems like a reasonable explanation for the behavior that you're seeing.  If you poke around you can probably find a solution for this.

---

### Post by hatapota on 2010-03-15
The good news is that my ipod is working again! The problem's not totally solved though...

I just restored the factory settings (using itunes on my ancient windows pc, which I had to get out of a cupboard specially) of my ipod, then plugged it into my pc - it could immediately be seen in both Rhythmbox and Banshee. Banshee again said that it couldn't read the database, so I ignored that and put a couple of songs on it using Rhythmbox - and when I unplugged the ipod, the songs were still there!! I plugged it back in, and Banshee could see the songs without asking to rebuild the database. But - when I tried to use Banshee to put more songs on the ipod, Banshee greyed out and stopped responding...

I think this may be a problem for another day though as I've got music on my ipod (through rhythmbox), which was my main priority... I would prefer to use Banshee but I don't have the time to look into it properly at the moment. It is amazing that my tiny little ipod has taken 2 pc's and 3 media players to get working again!!!

---

### Post by Chronon on 2010-03-15
You might want to make sure the Banshee devs are aware of this issue.

---

### Post by hatapota on 2010-03-16
Good call - I will some more investigation into what is going wrong so I can let them know in more detail. :)

---

