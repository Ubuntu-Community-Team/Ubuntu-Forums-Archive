---
title: "X-FI Xtreme Audio not working"
date: 2010-07-30
forum: Multimedia Software
---

### Post by jamessimo on 2010-07-30
I have no sound on my X-FI Xtreme Audio (known as  SB X-FI Xtreme Audio CA0110-IBG in sound preferences) I am using Ubuntu 10.04 LXF (I'm a fedora 13 user normally but wanted a nice OS for my big pc) 

I have searched for hours on end for an answer but to no avail . The most promising one was here [http://ubuntuforums.org/showthread.php?t=1063987](http://ubuntuforums.org/showthread.php?t=1063987) however it was for a older build so I could not follow the instructions.

the most up-to-date thread I could find was here [http://ubuntuforums.org/showthread.php?t=1471444](http://ubuntuforums.org/showthread.php?t=1471444) (the only 10.04 thread relating to my problem) but it ended in nothing. 

I know that there must be a answer considering this problem has been around since 2006. Thanks for reading and any input is welcome! 
(really upset that my first post had to be a "how-do-I" Concidering I got everything else sorted(Graphics, Visuals e.c.t))

---

### Post by lidex on 2010-07-30
Actually post #2 of that first thread should help. But instead of sound preferences, use:
```
gstreamer-properties
``` to set alsa as default

---

### Post by jamessimo on 2010-07-31
Hey lidex! Thanks for the reply! I tryied it but it diddnt work, I think however that I have messed up my ALSA drivers through following a old HOWTO, could you please direct me to were I can re-install the [FONT=monospace]updated[/FONT] ALSA drivers, then ill try 
gstreamer-properties again! Once again thrilled for the responce, think it may work!

---

### Post by lidex on 2010-07-31
Yes, use the alsa-upgrade link in my sig.

---

### Post by jamessimo on 2010-08-03
Hey lidex, the update messed up so I had to re-install. 

I'm now fully installed and updated with alsa standard, still no sound.

also in sound preferences, what settings should I have? Anyone that uses the sound card causes just forces music to stop playing.

PS I'm using a head set connected to the sound card (works in windows so its not the headset/connections) 

Thanks again!

---

### Post by jamessimo on 2010-08-03
Shameless Bump, Really need some help :(

---

### Post by lidex on 2010-08-05
have a look here:
[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

---

### Post by jamessimo on 2010-08-05
I was told to not do that in this thread [http://ubuntuforums.org/showthread.php?t=1254492&page=4](http://ubuntuforums.org/showthread.php?t=1254492&page=4) because the snd-ctxfi driver comes installed on all ubuntu 10.04 distros. 

However on page 3 this post [http://ubuntuforums.org/showpost.php?p=8011636&postcount=21](http://ubuntuforums.org/showpost.php?p=8011636&postcount=21) tells you how to follow the debian wiki. Should I follow that but not follow the first post of the thread?

---

### Post by Lantizia on 2010-08-05
Hi, If you have one of these PCI-E X-Fi Xtreme Audio cards... then if memory serves they are not really X-Fi cards at all... they are rebadged Audigy2 cards.

You can see in the release notes below that they are excluded from the official X-Fi drivers too (the ones that were eventually open sourced and ALSA got their hands on)...
[http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx](http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx)

I had one of these cards, got tired of trying to make it work and got a X-Fi Xtreme Music instead.  You may be able to get it working by trying to make ALSA think it is dealing with an Audigy2 card instead, not that I've never seen anyone get that working.  If you look at the ALSA matrix for Creative Labs then you'll see that the Xtreme Audio cards do not even use the same driver...
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

The guide I wrote for 9.04 users last year was not intended for Xtreme Audio users.

---

### Post by jamessimo on 2010-08-06
> **Lantizia said:**
> Hi, If you have one of these PCI-E X-Fi Xtreme Audio cards... then if memory serves they are not really X-Fi cards at all... they are rebadged Audigy2 cards.

You can see in the release notes below that they are excluded from the official X-Fi drivers too (the ones that were eventually open sourced and ALSA got their hands on)...
[http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx](http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx)

I had one of these cards, got tired of trying to make it work and got a X-Fi Xtreme Music instead.  You may be able to get it working by trying to make ALSA think it is dealing with an Audigy2 card instead, not that I've never seen anyone get that working.  If you look at the ALSA matrix for Creative Labs then you'll see that the Xtreme Audio cards do not even use the same driver...
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

The guide I wrote for 9.04 users last year was not intended for Xtreme Audio users.

Thanks for the really informative post! I feared this may be the case. Alsa don't say if they do or don't support the card but with creative it is normally the latter. 

I have a rampage mobo that came with its own HD sound card so ill stick that in and hope for the best!
 (Don't wana buy a new sound card considering I went linux for the price tag of free :P)

Thanks for the reply's Ubuntu community and I'm glad I can put the lid down on this case.

Thank you all and hopefully my next thread will be all good news!

(Ps. I hate creative)

---

### Post by lidex on 2010-08-06
I think the audigy's have a switch in the mixer that needs to be toggled from digital to analog. Sorry I don't have the thread handy.

---

### Post by jamessimo on 2010-08-15
> **lidex said:**
> I think the audigy's have a switch in the mixer that needs to be toggled from digital to analog. Sorry I don't have the thread handy.

Its ok, I stuck my Rampage HD card in there and it worked from the off. Creative beat me but now I can listen to music, watch TV and play all my favourite video games. This is now my main OS and all is good! 

One again thanks to the community for the help and getting this sorted, sadly my X-fi is just not Linux friendly but I'm glad its gone. Hate creative anyway.

---

### Post by Chutney3k on 2012-02-07
This is still relevant.

Please see [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

scroll down to the PCIe version of X-fi Xtreme Audio... DOES NOT WORK.

Seems we either need to buy a new Soundcard or use or On board sound :(

---

