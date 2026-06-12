---
title: "S-video out resolution."
date: 2008-09-22
forum: Multimedia Software
---

### Post by Rizzrat on 2008-09-22
Morning, 

Apologies if this has been posted already, but am looking for a solution to my problem.

I have a Dell laptop which i run S-Video out to my 42" TV so i can watch movies through it.

Running Ubuntu Hardy Heron i can get the desktop on the TV using the screen settings, but the resolution is fixed and really poor. The image is so low quality its not worth doing. The laptop had XP on previously and managed to sync to the TV fine. Is this something that can be fixed by a set of drivers or do i have to wait for Ubuntu to update their dual screen stuff?

Thanks for your help.

---

### Post by aeiah on 2008-09-22
its unusual that s-video ever produces a decent result, windows xp or linux or anything. what resolution did it display at in windows? you could perhaps use these settings but the best solution if possible, would be to output through vga or hdmi if at all possible.

what graphics card do you have in your pc? have you installed the restricted drivers?

you may be able to get it to output higher by messing around with the xorg.conf file. dual screen support is pretty good in linux for most cards i think, but s-video is kind of a dying thing and probably wont improve much in the future. dosent mean you cant get a good result by configuring properly though.

are you aware of pstrip for windows? i managed to get linux modeline settings for my tv from it and applied the settings in windows. worked like a charm. this was for hdmi though, not s-video. same principle could apply though if your graphics card driver supports it though

---

### Post by Rizzrat on 2008-09-22
I have installed the restricted drivers..

Not sure what XP did, it was all automatic (F8).

I will check out those programs though. thanks for the info.

---

### Post by aeiah on 2008-09-22
yea it would habe been automatic but when its all working in xp, you should be able to just right click on the desktop, go properties and go to the tab as if you're gonna change your resolution. this'll let you know what res its running at on your big tv and what you should be aiming for under linux.

if you have an nvidia card, pick up the nvidia-settings package in linux if you havent got it already. it'll give you a better control panel and may make things easier than messing with xorg.conf and custom modelines

---

### Post by Rizzrat on 2008-09-22
Indeed, the Ubuntu Control panel has no options though. When i switch to dual screen (extended or cloned) it fixes the TV resolution to something really small and wont let you change it. 

I would imagine getting it to release the other resolutions will fix the problem. But i have no idea how to do that, and i dont want to get into the code as its my wife's laptop o.O

(as for graphics card.. its onboard Dell standard stuff for the Inspiron series)

---

### Post by aeiah on 2008-09-22
right so its an intel card. it'll still be useful for you to find out what chip it uses specifically as they update them as time goes on. intel are pretty good with linux so you might be in luck, but i was always of the understanding that you can only really get 800x600 resolution out of an s-video connection anyway, windows or linux. what res is it outputting in windows? 

after looking at the s-video wikipedia page, it seems you can really only get 700x486 res. which is about the res of a dvd. so perhaps windows is shrinking things down and making it appear to have a better resolution when in fact its sending the same amount of detail down to the tv?

---

### Post by Rizzrat on 2008-09-22
I cant check the XP unfortunately.. No longer on the PC.

Its possible that XP was resizing to suit the TV, but the Ubuntu picture is just horrible. You cant even read text on it. If it could do the 800x600 accurately then i would be quite happy to watch movies on my TV, but the picture just doesnt come out right.

Are there any special control panel downloads i can try to see if i can force the picture?

(also, when cloned, the picture on the laptop screen is at low res but is clear.. so its definitely an issue with the way the info is being sent to the TV and rendered)

---

### Post by aeiah on 2008-09-22
i dont know if there is one for intel, as i have nvidia :(

only thing i suggest is making sure its set to the right refresh rate and make sure its PAL or NTSC depending on what your tv allows (a lot of pal tvs with display ntsc stuff but it'll be fuzzy and sometimes black and white etc, it may be the same problem). im pretty sure you'll still be stuck with a low resolution no matter what due to the nature of s-video but if it works right it'll be fine for watching movies. reading text will always be a blurry nightmare though id have thought.

sorry i cant help more. depending on how old your tv and your laptop are, you might be able to use component instead and use a supplied adapter or one that you can buy, but i wouldnt waste money as it'll still be a nightmare to set up and if your tv isnt hd you still wont get an impressive resolution.

---

