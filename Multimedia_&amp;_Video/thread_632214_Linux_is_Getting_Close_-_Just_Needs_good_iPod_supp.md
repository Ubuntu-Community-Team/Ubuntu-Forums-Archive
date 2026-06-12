---
title: "Linux is Getting Close - Just Needs good iPod support"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by sjcarr on 2007-12-05
I am running Gusty on an HP Pavilion DV5139 and I am impressed with how well this new release runs on my machine.  I have tested past versions and none have been able to activate my Broadcom 4311 Rev 2 card, but this version did it without any trouble.

I am making the move to linux day-to-day because I don't like what I see coming in the Windows world.  The only hang up I have right now is trying to sync my ipod.  I have a new Classic 80gb and after three tries with Amarok, Banshee, and Songbird I had to restore the database on my windows partition from Itunes... three times.  Finally I located a new ipod library of some sort that enable Amarok to write correctly to the database so that my ipod would work.  All previous attempts transferred the data, but the ipod showed no songs, videos, or podcasts.

Amarok is fine for doing music I suppose, but the podcast support just is not there.  I was able to subscribe, but it would wait to download until I drug the files to a que and told them to transfer.  Itunes has me spoiled.  It will just download all day and all night, then transfer in a few minutes while I am getting ready in the morning.  Bansee and Songbird looked promising in this regard, but both trashed my ipod database making the little gem an expensive paperweight.  

I listen to/watch podcasts all day and to download all of them while I sync is not productive.  Ideally, Amarok should be downloading all day and automatically syncing when I dock my ipod.

So... all this rant is just to say this...
If anyone has a good solution for podcast and music sync to my newer generation IPOD, please let me know.  Until I can find a good solution, I will continue using linux as much as possible and booting back to windows for Itunes.

Thanks!
Steven

---

### Post by eentonig on 2007-12-05
I never had a problem with amarok and Ipod synchronisation. Just used a good howto to get it up and running.

---

### Post by fmartinez on 2007-12-05
I use Rythem Box to manage my IPOD... it'll seach for all you music and all you have to do is drag and drop new music or delete old music. Really easy to use.... tested with a shuffle and a nano. :)

---

### Post by edm1 on 2007-12-05
gtkpod isn't exactly pretty but it might be what you're looking for.

---

### Post by sjcarr on 2007-12-05
I tried gtkpod and rhythmbox and neither worked for me.  gtk locked up when I plugged the ipod in this most recent time and rhythmbox corrupted by ipod's db.  What I have determined is that Apple updated the new ipods to add a checksum for the database when syncing, which I am guessing previous ipods did not have.  As a result, the ipod will compare the checksum and if it does not match, it will not read the database resulting in the "no music..." messages being displayed.  

eentonig:  What howto did you use, and what gen of ipods do you sync?

I was able to find this thread which looks like running win2k in a vmware client might get the job done:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=614208](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=614208)

---

### Post by sjcarr on 2007-12-05
No big deal... but I have a typo in the title... how can I fix that?

---

### Post by sjcarr on 2007-12-05
fmartinez:  What generation is your ipod?

---

### Post by Wobblybob on 2007-12-07
Hi, I have a new iPod classic 80GB with 1.0.2 firmware and am running Gutsy 7.10 on a Intel PC, I followed the stuff on the following threads [thanks to the guys who posted] and got my iPod to work with Amarok for music and gtkpod-acc to upload my videos again. It was a bit of a long job but it was worth it to leave itunes and windows behind. I've only been using ubuntu a few months after 30 years on Windows so I'm still a newb but got there in the end!

ubuntu threads [[COLOR="Navy"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic") and [[COLOR="Navy"]here[/COLOR]]("http://ohioloco.ubuntuforums.org/showthread.php?t=611404&page=2")

**note** if your copy of Gusty is 64 then you may need to make some amendments to the code, I have a laptop [see below] with AMD64 Fiesty but not tried above on that yet.
Good Luck

---

### Post by bomanizer on 2007-12-08
> **Wobblybob said:**
> Hi, I have a new iPod classic 80GB with 1.0.2 firmware and am running Gutsy 7.10 on a Intel PC, I followed the stuff on the following threads .......

Do you have cover art and/or cover flow working?

-Cheers

---

### Post by Wobblybob on 2007-12-08
yes to cover flow and I had already added cover art to all tracks prior to moving to the iPod using EasyTag so they have uploaded with the tracks and continue to work.

---

