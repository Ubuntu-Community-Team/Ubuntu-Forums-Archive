---
title: "Syncing Ipod Touch"
date: 2008-06-09
forum: Multimedia Software
---

### Post by Cephaus on 2008-06-09
Ipod Touch FW 1.1.4 Jailbroken

Ubuntu Hardy Heron 8.04

Using Amarok

---

### Post by swatF1RESTORM on 2008-06-15
Bump because I'm looking for something that works as well. I have the same specs as Cephaus. I've tried the [official]("https://help.ubuntu.com/community/PortableDevices/iPhone") ubuntu touch/iphone walkthrough but couldn't get it to sync at all.

---

### Post by damis648 on 2008-06-15
The official wiki is the best way to go. Did you follow all the directions? Did you use GTKpod? It worked fine for me.

---

### Post by swatF1RESTORM on 2008-06-15
I'm trying to use GTKpod right now. I have it mounted but I can't figure out how to transfer the music to the iPod.

---

### Post by swatF1RESTORM on 2008-06-15
Just got it to work. I followed the official guide and just had to learn how to properly use the program to sync. Once GTKpod recognized my iPod I clicked "New Playlist" at the top of the screen, then the "Add Files" button to select the files to add to the playlist. Then I hit "Save Changes" and it copyed the files over just fine. I feel like I should've been able to get this from the start, I guess I was just making it difficult in my head. After the files copied I "ipod-touch-umount" in the terminal window and checked the new music on my iPod. It wasn't there at first but if you open your music collection and hold down the home button until it closes your new music should be there.

Hope this helps and I'll try help anyone if I can.

---

### Post by toupeiro on 2008-06-15
I recently went over to the dark side and got an iPod touch, and I have to say its 1) a great device, but 2) very difficult to use completely without iTunes.

I followed the guide, but I found it to be a little incomplete.  For 1, the Jailbreak link is broken, I tried it over 2 days and that link has been down 100% of the time.  Being ipod stupid, I started googling for another jailbreak application, and came across something called [ZiPhone]("http://www.ziphone.org/") which is more iPhone oriented, but said also worked with the iPod touch.  It did jailbreak the phone, but obviously used some different versions of openSSH because the steps to use keys for authentication did not work, and after reading a bit more, there may have been some better choices from a battery life perspective.  No big deal, I can always start over later if I want..

Jailbreaking a phone breaks some other stuff that has to be activated in iTunes apparently.  One of those things being the Youtube player...  After more googling, I found a fix [here]("http://www.macriot.com/article.php/20080211095515461"), and can confirm that the three files download works fine.  The only other thing I did as read from a different guide is that I went into the Activation Records directory and deleted everything out of it.  It was a step of the other guide I used for firmware 1.1.4, I just can't seem to find the link to it anymore.

So now I got youtube working, I can wirelessly sync with Amarok, album art is coming over fine, but thats only one part.. I still cannot sync photos, or videos, and have yet to find a way.  gtkpod gives me some kind of error about the Photo database, and doesn't appear to have video support at all.

Finally I said, ok, I will bite the bullet and load XP in virtualbox and just use iTunes...  Wishful thinking.  Apparently, using iTunes with an iPod touch / iPhone is broken, giving some kind of hex error like 0x80000001.  

I refuse to repartition and install windows natively and dual boot every time I want to sync my iPod, so I will just live without the photos and videos for a while, but it would sure be nice to know if anyone has had any success in getting their iPod touch working in virtualbox with iTunes or with any other VM solution.  I have to say that the iPod touch is everything I ever wanted in a device like this, I just loathe that I have to use their bloat software to gain access to it all after committing a few hundred dollars to their hardware..

---

