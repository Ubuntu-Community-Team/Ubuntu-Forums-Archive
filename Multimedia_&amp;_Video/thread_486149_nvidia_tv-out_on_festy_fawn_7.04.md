---
title: "nvidia tv-out on festy fawn 7.04"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by bldninja on 2007-06-27
After setting up tv-out in xorg.conf and using nvidia-config this seems to work ok when i log in as root. I get 2 seperate x screens with gdm. 1 on my laptop and 1 on my tv. But if i log on as my user i get only working gdm session on my laptop. On my tv i can move my mouse (no arrow only X) and black screen. I found a thread yesterday and i made an .Xclients file in the home/user folder with the text gdm. After restart of x i got the gdm background and top/bottom panel, but nothing else appear (Menys, programs, icons, clock). I cant use the x-session!!!! Can anyone help me?

---

### Post by NT4usB on 2007-06-27
There's been a lot of discussion on these boards.
Might start your search [here]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+howto+tv-out+nvidia+feisty&btnG=Search")

---

### Post by bldninja on 2007-06-28
I used the thread you are refering to when i configured my xorg.conf file. I can't find anyone who have posted the same problem in this thread.  So if anyone can help me????

---

### Post by litago on 2007-07-13
it's due to a conflict with compis/beryl! I've disabled desktop effect and now it's working!

---

### Post by bldninja on 2007-07-17
I also disabled desktop effects in Beryl and now it's working! Thanks!

---

