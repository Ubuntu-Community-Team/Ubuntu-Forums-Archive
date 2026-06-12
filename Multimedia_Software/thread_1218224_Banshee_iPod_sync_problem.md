---
title: "Banshee iPod sync problem"
date: 2009-07-20
forum: Multimedia Software
---

### Post by divinityofnumber on 2009-07-20
Hi everyone, 

I have recently started having a problem with Banshee. It worked great for me for the last couple of months, but now, it seems as though it will not allow me to add anything else to my iPod. Here is what happens. 

1) The albums are in my Banshee music library, I can play them, etc, just fine. 
2) I plug in my iPod, everything works as usual. I can select an album or two, drag them to my iPod, it says that it is adding, syncing, etc, and everything happens at the normal speed. After it is complete, I click on my iPod, it shows the albums being on there, I can play them, etc. 

But, when I eject my iPod, and then unplug it....nothing that I added is there. 

Any help would be appreciated.

---

### Post by internalkernel on 2009-07-20
If you don't find the answer here, send an email out on the Banshee mailing list. I've seen this issue come up several times, I think it has to do with rebuilding the database or something. But don't quote me on it... I remember reading about it though...

---

### Post by divinityofnumber on 2009-07-21
At least I know that I am not the only one now. :)

I will go ahead and send them an email so they can more greatly understand the magnitude of the problem. 

I did fix it, or rather find a solution. I plugged my iPod into a Windows machine, used iTunes to restore it to factory condition, and then let Banshee spend all night adding everything back onto it. The things that I had been trying to add that were not working went onto it just fine. 

So, who knows. Hopefully every couple months I will not run into the same problem and have to format my iPod and then reload all of my stuff back onto it.

But, even with that hassle it still beats using Windows. lol. :D

---

### Post by internalkernel on 2009-07-21
lol... I keep WinXP in a virtual machine and one of it's tasks is dealing with my ipod. I had another issue with the artwork on Banshee that unfortunately stopped me from using it. There's a bug in one of the libraries that Banshee reallies on that enters the album artwork for each track separately - thereby bloating the thumbs.db. On my ipod it was using about 5gigs of space. Doesn't sound like you had that issue but you may want to keep an eye on that one too.

The banshee mailing list was a great help though... they are really friendly.

---

### Post by cj.surrusco on 2009-12-02
I have this same exact problem with my ipod classic. But even after restoring it twice, I still have the problem. Any suggestions?
Thanks,
CJ

---

### Post by whysea on 2009-12-11
Here is the method I found. 
Do a partial sync (i.e. 300/400 at a time) interrupting the synchronization. When you do that, the second part of the sync, i.e. when banshee transfers to the ipod proper, starts

---

### Post by tlee on 2009-12-27
FYI:

I had the same problem, but doing a partial sync didn't work for me.  I have found that a manual sync (dragging/dropping) does work.


Good luck!

---

### Post by porlaizquierda on 2009-12-28
I have the exact same problem. I manual sync and still nothing shows up when i unplug my ipod. Banshee was working fine the first few days I stalled it, but now, nothing.

---

### Post by stanton warrior on 2009-12-28
I'm yet another person having problems with this. Banshee has found the cover art for most of my collection but just can't transfer it to my iPod classic.

Seems a bit of a coincidence that  several people are having issues at the same time. I'll try asking on their mailing list, as suggested above.

---

### Post by ninecrosses on 2009-12-28
I was having that problem with my Nano 4g Black. Nothing would let it transfer; amarok, banshee, floola, gtkpod, etc. It all started after I upgraded to v9.10.

I've downgraded again to 9.04 and have finally got my ipod working again with Banshee with quite a bit of difficulty. But...when I finally successfully added songs (I uploaded one) and it sent the cover art with it. I seen it on the iPod, so the next song; the first songs cover art is gone, but the newly uploaded one shows. 

A third song and it does the same thing. It show the newest uploaded songs cover art, but the first two are gone. And now I manually sync'd the iPod and all of the cover art is gone. Anyone had a problem like this?

I was using armarok before I upgraded and actually got most of my cover art. But, I nit-pick anyway just has anyone got a solve for this fix?

---

### Post by tlee on 2009-12-31
Not sure if this will help any of the recent posters, but I just upgraded Banshee from 1.5.1 to 1.5.2 (aka 1.6 Beta 3) and I no longer have to manually sync.  Everything seems to work fine now.  

I'm running Karmic, and I have a 120gb iPod classic.

---

### Post by stanton warrior on 2009-12-31
I managed to fix most of the problems by filling my 80GB Classic a few thousand songs at a time.

I've now upgraded to 1.5.2 (was on 1.4 for some reason) and that's fixed a few more probs.

The only problem that remains is that I can't import my ratings from the iPod to Banshee.

---

### Post by mazzatelli on 2010-01-05
I'm encountering the same problem.
I've tried to manually sync, so when I drag and drop items it says its adding - but never shows that it is "flushing the disk" and updating the ipod.

When I disconnect, no songs have been updated.
Every now and then when I add < 10 songs it will update...frustrating at the moment

---

### Post by Ed54_3 on 2010-01-28
This is definitely an issue.  I've had banshee get stuck at "preparing to synchronize" without ever getting around to it.  Occasionally it will work on about 50 songs, but no more than that, no matter how much time i give it.  Other programs work fine, but I would love it if banshee was fixed.

I have an 80 GB 6th Gen Classic, running Ubuntu 9.10 with everything updated.

---

### Post by fcastillo on 2010-06-10
Any news if this is fixed? I just updated to Banshe 1.7.1 and I still have the same problem that it says preparing to synchronize, but the problem appears only when I create a playlist on my iPod

---

### Post by gcintra on 2010-06-15
Having the same problem here with 1.7.1 and Lucid. The iPod clasic (160GB) is recognized, and seems to be transfered, but once I disconect it shows the transfered music as "other".

---

