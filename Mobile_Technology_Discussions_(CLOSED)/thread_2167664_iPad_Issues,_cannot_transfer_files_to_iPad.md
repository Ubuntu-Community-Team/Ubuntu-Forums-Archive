---
title: "iPad Issues, cannot transfer files to iPad"
date: 2013-08-14
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Jason_Maynor on 2013-08-14
Hello there, I am not sure if this is in the right group, but Will post and hope I am in the right area!

I am trying to transfer some of my Movies / Tv Shows / Videos etc. to my iPad using ubuntu 13.04, again it worked Fine on my Desktop (Same version of Ubuntu) Now that I am out on the road I need to do it on my Laptop, which for some reason every time I try, I get 

```
Invalid Apple File Control data received
```

around 40mb ish and it Failes to transfer. It does not matter what size file, anything fails.

What I do is go to "Files" select what I am trying to transfer, I have tried the Drag n Drop method, and Copy / Paste, then select "Documents on iPad" navigate to CineXplayer, Documents and dump it in there.. Error's out every time. I have tried searching google for this issue, and I have not found an answer. CLosest thing I have found is put up a virtual box with Windows on it. I will if I have too, but I would like to do it nativly in ubuntu. I know it can be done my desktop did it. Thanks for the help

---

### Post by Jason_Maynor on 2013-08-15
Well, Update for anyone that cares, I finally got Virtualbox installed with a copy of Win7 on it, installed itunes, now Windows sees the iPad but iTunes does not... ugh /fml

---

### Post by Jason_Maynor on 2013-08-15
Ok, well SOLVED... Finally got the stupid iPad to register under Windows.... Took Much Much Digging!!!

---

### Post by AbdelRahman_AbuRas on 2013-09-30
I was Hoping to fix this without reverting to stupid windows. I'm facing similar problem.

Can you please try the below in the terminal and check if ther is any diffrence, as your problem seems simpler than mine
sudo apt-get install libimobiledevice-utils ifuse
idevicepair unpair && idevicepair pair

---

