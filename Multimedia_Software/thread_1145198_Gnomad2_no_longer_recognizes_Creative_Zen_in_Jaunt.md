---
title: "Gnomad2 no longer recognizes Creative Zen in Jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by therieb on 2009-05-01
Hello everyone,

I hope you can help me with a small problem.  I have a Creative Zen and I've been using Gnomad2 to transfer video to from my laptop to the Zen in Ibex.  Unfortunately, after upgrading to Jaunty, Gnomad no longer sees the Zen.  Rhythmbox sees it just fine, and it now even appears on the desktop.  However, when I transfer videos directly from the desktop they don't appear in the Zen's list and therefore I can't play them.  I believe that if I could get Gnomad working again I wouldn't have this problem.  Any help would be greatly appreciated.

P.S. has anyone found a method to get gapless playback on the Zen?

---

### Post by Nicke on 2009-05-01
I´ve got the same problem, anyone got a solution?

---

### Post by garvied on 2009-05-01
gnomad work fine if you umount the creative zen and then open gnomad2

---

### Post by therieb on 2009-05-02
Thank you for the excellent advice garvied!  That did the trick.  Now with my combination of Iriverter and Gnomad2, I'm happily transferring video again.  One more question: do you have any recommendations for gapless playback on the Zen in Ubuntu?  Rhythmbox 12 isn't getting the job done on my system.  Thanks again!

---

### Post by huczek on 2009-05-02
It doesn't work with my Creative Zen V Plus 2GB. I have no additional disks mounted. I use Ubuntu Intrepid Ibex and Gnomad2 doesn't find my device.

---

### Post by chaser.nl on 2009-05-02
> **huczek said:**
> It doesn't work with my Creative Zen V Plus 2GB. I have no additional disks mounted. I use Ubuntu Intrepid Ibex and Gnomad2 doesn't find my device.

i was having the same problem, running gnomad with sudo solved it for me hope this helps you ;)

---

### Post by TusharG on 2009-05-05
I'm also a Creative Zen and I found that 9.04 has fixed many issues and I'm lot more excited to use my Zen with this release as I was able address most of my blocker issues.
   To explain in detail my experience with Zen and other apps I have written a blog, do check the same.

[http://tusharg.blogspot.com](http://tusharg.blogspot.com)

I hope it will help someone.

---

### Post by wpwend42 on 2009-05-10
I'm having the same problem; how do I unmount my mp3 player?  I don't see anywhere to unmount like I do my flash drive, etc.

---

### Post by granny6989 on 2009-05-18
Unmount = right click the icon on your desktop and tell it to unmount (towards end of list).

Otherwise try going to top menu 'Places', scroll down to your device and select. On the left side of the window that opens, you can choose eject icon near the Zen name.

If you don't see your Zen at all you may have other issues...

S*

---

### Post by wpwend42 on 2009-05-25
Ok when I go to unmount, I get this error:

Error initializing camera: -60: Could not lock the device

and the mp3 player freezes up and won't unfreeze until it runs out of power.

---

### Post by AlexGein on 2009-06-09
I found that I was only able to unmount when the open zen dialog first appears using the unmount button on the bottom left of the dialog.

every other attempt fails...

---

### Post by wpwend42 on 2009-06-12
I've also encountered where it can mount for about 20 seconds and then locks up.

---

### Post by wpwend42 on 2009-07-06
Was a solution ever found for this problem?

---

### Post by centos on 2009-07-09
Does for all of you work mtp-detect? I'm getting this error 
```
Attempting to connect device(s)
usb_claim_interface(): Device or resource busy
LIBMTP PANIC: Unable to initialize device
Unable to open raw device 0

```
and gnomad2 tells me that Zen wasn't found. And I don't even see it in Places in order to unmount it..

---

### Post by Jimtheplanner on 2009-07-09
Just out of interest I use Mandriva 2009.1 & with both Gnome & KDE found that my Zen is automatically detected by Amarok. Until this point I had also used Gnomad2.

I can use Amarok to transfer files et al

I'm not sure about Ubuntu by you never know Amarok may work for you...

Jim

---

### Post by linopus on 2009-08-01
It worked for me too.
After spending 2 evenings to install this Creative ZEN mp4 player on Win XP without success (XP has a problem with usb driver of Creative,...) I did a search on Creative in Synaptic and installed GnoMad2 but also not working :-( Ubuntu 9.04 mount as a mobile hard drive so that was already a relief but transferred files did show up on my ZEN player. Thanks to your great tip Gnomad works and the transferred music files are now playing on my ZEN. Even transfered music clips works (not 100% but I guess it is the codec). Many thanks, again a satisfied Ubuntu user.

---

### Post by rhchia on 2009-08-24
gnomad2 works for me but i could not copy the folders. i need to go in each folder and move the media and back to the root again. the process repeat itself. 
i tried rythmbox and bansee but i don't see my zen vision M on any of the menu. 
anyone can advise what can do i do now?

---

### Post by rp3 on 2009-10-18
> **garvied said:**
> gnomad work fine if you umount the creative zen and then open gnomad2


Solved my problem as well thanks!

---

### Post by wpwend42 on 2009-11-01
Is this still a problem in 9.10? I am still getting freezes even if I unmount.

---

### Post by cpearless on 2009-11-03
@Garvied

That worked great, thanks! Not being able to sync my Zen was the only reason why I even still had Windoze on my machine!

Thanks again!

---

### Post by lavinog on 2009-11-11
> **wpwend42 said:**
> Is this still a problem in 9.10? I am still getting freezes even if I unmount.

I was having issues at first with my zen x-fi, but after using the cleanup in the recovery menu, everything works great.

to get to the recovery menu with a zen x-fi (should be the same as a zen) press and hold the play button, while holding the reset button and turn on the device.

---

### Post by pistacoppu on 2009-12-09
> **garvied said:**
> gnomad work fine if you umount the creative zen and then open gnomad2

work perfect with my good-old ZEN micro 4gb

Thank you very much garvied;)

---

### Post by wpwend42 on 2009-12-09
This seems to be resolved in 9.10 as long as you unmount.

---

### Post by shiroyoshida on 2009-12-26
Unmounting the player and then running gnomad2 worked for me as well. Didn't work when I attempted to transfer an entire folder but it did work when I tried to transfer the contents of the folder. 

Thank you garvied!

---

### Post by wpwend42 on 2009-12-26
This was fixed for me in 9.10. Hooray!

New problem: Been using a V Plus for about 3 years. Works great in Gnomad2, but yesterday my player broke.  It turned itself off and now refuses to turn on or charge.

Of the current generation Creative mp3 players, which one works with Ubuntu the best?

---

