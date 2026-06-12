---
title: "how can I fix Zapping segmentation fault?"
date: 2009-12-15
forum: Multimedia Software
---

### Post by phreakshew on 2009-12-15
Hi. I just about had Zapping working all the way with my TV tuner card in 9.10 when I changed a preference (deinterlace) to see what would happen. The result is that Zapping now immediately quits upon starting with a segmentation fault. I uninstalled /reinstalled it, but it still happens. How can I get it to work again? Thanks~

---

### Post by Sin@Sin-Sacrifice on 2009-12-15
Look for any user preference files in /home/user (might be in a folder called /home/username/.zapping?) that might have your 'deinterlace' setting in it and open with gedit (or whatever) and change it to the working setting. I've never used zapping but you may be able to figure something out by looking at ```
$ zapping --help
``` Considering you reinstalled and it still happens leans toward the fact that it's in a user preference file in your home directory though. Otherwise it would have gone away... I would say delete the folder but it might remove other settings that made it work with your tuner card.

---

### Post by phreakshew on 2009-12-16
Thanx Sin ~

Went ahead and deleted that file, but decided against trying Zapping again in favor of XawTV. 

XawTV worked immediately - only had to open alsamixer in a terminal to get the sound working correctly. 

BTW, I like yer sig. Have you seen this:[ http://www.youtube.com/watch?v=VebOTc-7shU]("http://www.youtube.com/watch?v=VebOTc-7shU")

:popcorn:

---

### Post by Sin@Sin-Sacrifice on 2009-12-16
Yep... seen all the Alex Jones movies. Zeitgeist and a few others floating around out there by other people. The latest news is that Obama is actually going to sign that Copenhagen treaty with or without The House and Senate. I try to stay up to date but some of the bills they're releasing are hundreds if not thousands of pages long and only radio personalities like Alex have time to sit there and read every word. Luckily he and other revolutionists point out the important parts. Glad you fixed your tv issue.

---

