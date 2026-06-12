---
title: "DVD problems"
date: 2010-05-31
forum: Multimedia Software
---

### Post by Squall001 on 2010-05-31
My problem is that I am trying to copy my friends Heroes DVD's. I have both the discs and images of the discs on my hard-drive. What I want to know is if it is possible to split it up into only the episodes (minus the special features etc.), and how to do that. Thanks in advance for the help.

---

### Post by inameiname on 2010-05-31
I guess the first thing to know is how you made the images? Did you just right-click and copy to hard drive or something?

k9copy is a good one, but having never tried it for your specific reason, I can't say for sure if it does or doesn't. But worth seeing, as you can decide what tracks (ie, videos) you want on, and what you don't want on the DVD. 

Personally I use DVDFab through Wine and it does what you need just fine. But it's shareware software.

---

### Post by Squall001 on 2010-06-01
I did just right click it and use Brasero to create ISO files of the discs. I don't have any other programs for disc burning or whatever, so I don't have anything to play about with yet. I'm new to Ubuntu still, so I might not understand everything you tell me :P

---

### Post by inameiname on 2010-06-01
No worries. Well let's see, k9copy is probably the best application for Linux to use to backup a DVD. ManDVD is another, but I always preferred the former. 

Basically it works the same as the Windows ones, if you've ever backed up or copied dvds in Windows, in which you would insert the dvd, or ISO, open the application, and scroll through the options, deciding on if you want an exact copy, a compressed copy (dvd-9 to dvd-5), or as you want, to pick and choose just what you want to copy. Use the 'k9copy assistant' part as it's easier, and just plug in the ISO as the source, and then make sure to only keep the episodes only. And then you can save it as new ISO, or burn it to a dvd if you want. That's all.

Oh, and you can download k9copy through the Ubuntu Software Center. Or if you use the terminal, just copy and paste:

sudo apt-get install k9copy

Hope that helps.

---

