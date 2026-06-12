---
title: "WUSB54G v4 wireless adapter"
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by Cpierce on 2010-09-06
Once again I need to call on my Ubuntu friends for help. I have read other posts, but they don't seem to have the same problem. I have a number of computers working just fine on my wireless network so I don't believe it is a router issue. I am running 10.04 on a dell gx280. I plug in the WUSB54g and ubuntu sees it and it connects to the internet just as it should. I can surf the internet thru different browsers, and although a little sluggish, it works just fine. The problem is when I download a file. It starts out working as it should but continues to slow down to a crawl. Update manager had a 54MB update, it started out downloading, but then said it would take 2 hours so I just cancelled. I have several WUSB54g's and they all have the same issue. I changed to a different type of adapter, and the update manager only took a couple of minutes. 

I don't know which command line outputs would help, so please just let me know and I will be happy to post them.

---

### Post by Cpierce on 2010-09-09
Bump

---

### Post by kerry_s on 2010-09-09
you can't trust what it says for the time it will take, thats a guess. did you actually try it & see if it takes that long?

wireless speeds go up & down to get the best strength, they say 54g(54mb's) but it can very depending on strength & interference, as well as what your router is set to accept.

by the sound of it, my first thought would be to check the router settings, it might actually not be serving fast enough so it's causing your system to wait, thus you'll see the drop, then it should eventually pick up again. check your router logs. make sure your settings are right. if your running all g, disable b, etc...


for example: mine does anywhere between 6 to 54, every now & then the router automatically updates & some switch to basic support, it's slower.

ps: linksys are really crappy. i got the wusb54gs 2.1, i don't even use it, it's just a backup in the pile.

---

### Post by Cpierce on 2010-09-10
thanks for the reply and info. I don't believe it was the router since about half a dozen other computers are working fine. However I did change it from WPA2 to WPA and it seems to be working now.

---

### Post by Fernando Negro on 2011-12-29
I had the same problem, with this model, of a slow connection and frequent connection losses on Ubuntu 10.04 lucid.

I've [installed a new kernel]("http://ubuntuforums.org/showthread.php?p=11572146#post11572146") and the problem was solved.

---

