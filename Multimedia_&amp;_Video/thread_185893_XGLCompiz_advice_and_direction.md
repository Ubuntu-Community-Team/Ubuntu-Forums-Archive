---
title: "XGL/Compiz advice and direction"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by dmorel on 2006-06-01
I'm running the live CD of Dapper Drake and other then the fact that the Help keeps randomly appearing (every dozen or so keystrokes), it's looking fantastic and I believe I'm ready to do a full install onto my HDD and finally make the move to a linux desktop.

I admit, I want the wow factor of running the XGL/Compiz stuff (hey, I spend 10 hours a day at my desk!), but I believe from what I've read that my ati radeon 9250 just doesn't cut it... 

I don't want to spend a bazillion dollars, but I am willing to pick up a new graphics card so I can get things running smoothly. I had previously presumed (again based on what I have read)  anything with an Nvidia chipset in the GeForce 6000 or 7000 series would be fine, but now I'm seeing a lot of reports that there are some issues with 6.06 and the Nvidia drivers?

Everything I have read up until today suggest that Nvidia is more stable then ATI for XGL/Compiz.. 

I know it's early since today was the first gold release of 6.06, but if anyone can share what graphics cards they are using succesfully and (relatively) easily to run the XGL/compiz effects under Dapper Drake, I would be appreciative. I want to get the new card before I do the full install to minimize my futzing around time.
thanks!
- the unintentionally verbose dm

---

### Post by bluevoodoo1 on 2006-06-01
This link...
[http://getkororaa.com/releases/xgl/xgl-cards](http://getkororaa.com/releases/xgl/xgl-cards)
shows which cards *should* work with Xgl/compiz (link is from Kororaa Xgl live CD which is very neat). 

I have an FX5500 because my computer only supports PCI slots and it runs fine. I've been running Dapper for a few months now with no major problems. If you can get a 6000 or 7000 series card, I'd go for it. Search around for specific models and see what has been working (or not) for users. Here's a product listing for the new Linux nvidia drivers... [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

---

### Post by reclusivemonkey on 2006-06-01
[QUOTE=dmorel]
I don't want to spend a bazillion dollars, but I am willing to pick up a new graphics card so I can get things running smoothly. I had previously presumed (again based on what I have read)  anything with an Nvidia chipset in the GeForce 6000 or 7000 series would be fine, but now I'm seeing a lot of reports that there are some issues with 6.06 and the Nvidia drivers?[/QUOTE]

I have a NVIDIA FX5200, which I believe is the cheapest FX card you can get (I paid about £35 for it a few months ago now so its probably even cheaper now). It runs XGL/Compiz fine with all the effects. From what I understand, things are only going to get better as well, with speed improvements already in CVS.

---

### Post by dmorel on 2006-06-01
Thanks for your feedback guys.
Much good news, I'm home from work and completed a fresh install of dapper, followed [this tutorical]("http://www.ubuntuforums.org/showthread.php?t=131267") and all is working super fine on my old Nvidia GeForce 2 MX400 chip. Nice!

Now, if I could just get the resolution up to 1900x1200 I would be golden, but that's a seperate thread (that I'll post in a minute ;)!

thanks again for the assistance.
-dm

---

### Post by M@dMerC on 2006-06-01
i assume u used that glitzy thing because ur vid card is quite old (mine is a gforce4 mx and apparently i need it) so i was wondering where u can get it :P

---

### Post by dmorel on 2006-06-02
> i assume u used that glitzy thing because ur vid card is quite old (mine is a gforce4 mx and apparently i need it) so i was wondering where u can get it :P

M@dMerC,
I'm not sure if you are asking me a question here or not, but The vid card I'm using **is** super old, but apparently supported fine now with XGL/Compiz.

FWIW, the solution to the resolution issue was to remove all options in xorg.conf for depth of 24 except the one I wanted to use 1920x1200

If there was something else you wanted to know, let me know...
-dm

---

