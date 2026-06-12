---
title: "STILL looking for a good music player..."
date: 2008-11-13
forum: Multimedia Software
---

### Post by x C0MMAND0 x on 2008-11-13
Okay, so here's the deal.  I love Ubuntu and I want to switch over to it completely.  However, I am still very unsatisfied with all of the audio players out there.  Perhaps I am being to picky, but I really liked iTunes (and yes I realize there are many that are very close to it).  So here are my problems, does anybody know of an audio player I haven't tried, or a fix to my problems?

**Rhythmbox**- I love this, and it is probably my favorite, but there is one huge problem.  Whenever I use 3d switching, or any effects, or basically anything that uses a lot of memory, the audio will cut and and "lag" basically.

**Songbird**- This, in my opinion, was a poor attempt to integrate a web browser into an audio application and is trying to do too much when I want simpler.

**Amarok**- Ah, the seemingly crowd favorite.  Amarok is nice, but I just don't like the interface and difficulties I have with it.  Perhaps I need to explore it more.  For example, when I move around the columns (Title, Artist, Album, etc...) after rebooting they aren't saved.  There is always a "Media Transfer Que" every time I connect my iPod and remove it.  Also, it was tougher than I thought to get the program to actually SEE my iPod.

**Banshee**- Another program I like, but lack of visualization and the fact that the damn list's won't even alphabetize- that bug really made me loath this program.

What do I do?  Please keep in mind I could just be missing some very simple quick fix or add ons for a given program, so if so please just let me know.  Are there more programs I am missing and not trying or what?

Thank you.

---

### Post by ericesque on 2008-11-13
I went looking for other players when Rhythmbox was playing choppy or utilizing 99% of my CPU.  Turned out to be a bug with gstreamer and AAC. Specifically I had issues with AAC that was ripped in Ubuntu.  I've installed dBpoweramp in Wine and it works fantastic--plugins and all.  Now I'm extremely happy with Rhythmbox.  iTunes takes upwards to 10x longer to get music onto my iPod. That's a good chunk of time when you want to get out the door for work!

My second favorite player was Listen-- it's in the repos.  Get it from Add/Remove. I don't know if it has visualizations though.  The reason I didn't stick with it was slower development than Rhythmbox.  But it was certainly a nice option.

---

### Post by wolfen69 on 2008-11-13
i've always been a big fan of vlc. it's simple, yet plays everything. but it sounds to me like you are looking for alot of bells and whistles.

---

### Post by x C0MMAND0 x on 2008-11-13
> **ericesque said:**
> I went looking for other players when Rhythmbox was playing choppy or utilizing 99% of my CPU.  Turned out to be a bug with gstreamer and AAC. Specifically I had issues with AAC that was ripped in Ubuntu.  I've installed dBpoweramp in Wine and it works fantastic--plugins and all.  Now I'm extremely happy with Rhythmbox.  iTunes takes upwards to 10x longer to get music onto my iPod. That's a good chunk of time when you want to get out the door for work!

My second favorite player was Listen-- it's in the repos.  Get it from Add/Remove. I don't know if it has visualizations though.  The reason I didn't stick with it was slower development than Rhythmbox.  But it was certainly a nice option.

I tried listen, and it loaded my library but the playback was not functioning well at all.  Also, I didn't see any option for integrated iPod support or media device.

---

### Post by x C0MMAND0 x on 2008-11-14
I really like Rhythmbox still.  I just added 2 new albums into my library, and upon booting up it automatically added them in no problem.  Is there ANY way to fix the fact that the audio will cut out whenever I am doing anything that takes up a lot of processing power?  (ie 3d switching/unfolding cube etc...).  If so , that would be AWESOME!

---

### Post by rossmoore on 2008-11-14
I haven't had your audio problems with Rhythmbox, BUT:

Why can't I sync playlists with an iPod (or other MP3 player)? Now that's annoying. Syncing music but not playlists seems silly. I know you can use GtkPod to sync playlists, but why use a yet another little program for one simple job? It seems like it should be an easy plugin for Rhythmbox.

Ah well, it is free, I suppose.

---

### Post by finite9 on 2008-11-14
If I were you I would find the app that has the least problems, then bug the hell out of the developers to fix the problems you have on the mailing list for that application, then wait for next release.

I had a hard time getting responses on the Rhythmbox mailing list though, but in Intrepid, Rhythmbox works for what I use/need it for.  I haven't messed around with it enough to experience your issues with choppy audio but I do run full accelerated graphics desktop.

What is the spec of your PC?  If it's "old" then it may simply be a resource problem, and not neccessarily a bug with the software.

---

### Post by ericesque on 2008-11-14
> **x C0MMAND0 x said:**
> I really like Rhythmbox still.  I just added 2 new albums into my library, and upon booting up it automatically added them in no problem.  Is there ANY way to fix the fact that the audio will cut out whenever I am doing anything that takes up a lot of processing power?  (ie 3d switching/unfolding cube etc...).  If so , that would be AWESOME!

hm.  Really if 3d switching or unfolding the cube causes CPU usage to spike, it sounds like you either want to address that issue or else turn off Compiz if you know it's just taxing your hardware.  You could try updating video drivers or perhaps substitute fancier effects with quicker and less fancy effects...

---

### Post by Yoshokatana on 2008-11-14
I was also wondering about this. I use ubuntu (switched recently from gentoo) dual-booted, but I generally spend most of my time in Windows. I'd like to only use Windows for gaming, and the only thing stopping me is my >100 gig iTunes music library.

I know how to "transfer" the library to a linux program, but I'm not sure which program to use. I'm worried about slow-downs with such a large database (100-150 gigs). I want to use all of the normal iTunes functions (playlists, ipod sync, podcasts, visualizations), but with some cool features available in open source apps (projectM visualizations, grabbing artwork/info from wikipedia/amazon/cddb, etc). Interface-wise, I really like the whole flipping-through-records/Coverflow idea, and think it would be fun once I have more album artwork.

I've been looking at Amarok, because it has proper mySQL support, but if Banshee or some other (Listen looks interesting) program with a good UI has the features and stability I need, I'll gladly use that. Amarok's UI is somewhat sub-par.

So, any thoughts?

---

### Post by Idefix82 on 2008-11-14
> **x C0MMAND0 x said:**
> I really like Rhythmbox still.  I just added 2 new albums into my library, and upon booting up it automatically added them in no problem.  Is there ANY way to fix the fact that the audio will cut out whenever I am doing anything that takes up a lot of processing power?  (ie 3d switching/unfolding cube etc...).  If so , that would be AWESOME!

Have you tried changing the priorities of the processes? You could assign Rhythmbox a high priority and Compiz a low one. It might be that then the visual effects will become choppier, though. To do that, first type
```
top
```
and hit Ctrl+x. Now type in
```
sudo renice 1 PID1
sudo renice 20 PID2
```
where PID1 is the PID of the process Rhythmbox (it was shown by the 'top' command in the left column) and PID2 is the PID of the process compiz.real. You can play around with these priorities, possibly assigning compiz an even lower priority and see if that helps.

---

### Post by x C0MMAND0 x on 2008-11-14
> **Idefix82 said:**
> Have you tried changing the priorities of the processes? You could assign Rhythmbox a high priority and Compiz a low one. It might be that then the visual effects will become choppier, though. To do that, first type
```
top
```
and hit Ctrl+x. Now type in
```
sudo renice 1 PID1
sudo renice 20 PID2
```
where PID1 is the PID of the process Rhythmbox (it was shown by the 'top' command in the left column) and PID2 is the PID of the process compiz.real. You can play around with these priorities, possibly assigning compiz an even lower priority and see if that helps.

I am still new to Ubuntu, so please bare with me if I'm asking noobie questions.  After using the **top** code, and playing around with that, it turns out that it's Xorg that ends up taking up 70% + of my CPU and only 10% of my MEM or so...I guess what I want to know is what exactly is Xorg and what does it do?  Is there anyway to make it "do" less?  Is it the fact I have an older computer (2years)

My PC specs: AMD Athlon(tm) 64 Processor 3500+ , 512 KB Cache, 1000.000 MHz Frequency 
2gb Mem

---

### Post by SuperSonic4 on 2008-11-14
Xorg is your graphical desktop. It gives you mouse function and a GUI. Turning off compiz should reduce it

Exaile is meant to good, I hear it's a fork of amarok or audacious.

---

### Post by ericesque on 2008-11-14
> **SuperSonic4 said:**
> 
Exaile is meant to good, I hear it's a fork of amarok or audacious.

Not a fork, but intended more as a clone.  
[http://www.exaile.org/wiki/Main_Page](http://www.exaile.org/wiki/Main_Page)

---

