---
title: "Mobility Radeon X1600 wont work with lucid"
date: 2010-05-28
forum: Multimedia Software
---

### Post by amdemas on 2010-05-28
Hi,

I currently have a Hp NC8430 laptop running 10.04 and this one is amazing and love it, but my video card wont allow me to hook up an external monitor. I can enable compiz, but nothing else. When i install the ATI driver from the website for catalyst it allows the external monitor to work, but now compiz wont work??? I dont understand what i am doing wrong and would like if someone could help me. My Video car is a ATI mobility Radeon x1600 and is not supported anymore which sucks so if anyone knows of where to get opensource drivers that would be awesome or a way to set this up. I would hate to have to use another distro, but i need external support. So if anyone can help that would be awesome.

Thanks everyone.

---

### Post by amdemas on 2010-06-03
Ok found my solution....

I downgraded the kernel I will post the website that i used later if i find it again. The external screen works now when i turn off my laptop monitor when connected and compiz works too while connected...

---

### Post by amdemas on 2010-06-30
> **amdemas said:**
> Ok found my solution....

I downgraded the kernel I will post the website that i used later if i find it again. The external screen works now when i turn off my laptop monitor when connected and compiz works too while connected...


This was an old solution follow this it worked for me.

[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)


Hope this helps others   ):P

---

### Post by Warprunner on 2010-07-01
> **amdemas said:**
> This was an old solution follow this it worked for me.

[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)


Hope this helps others   ):P

Thank you it did!!! I was using the different headers and kernal since 10.04 came out. I can now update everything and it's been a while since my update box has been empty. Drove me nuts!

---

### Post by amdemas on 2010-07-01
> **Warprunner said:**
> Thank you it did!!! I was using the different headers and kernal since 10.04 came out. I can now update everything and it's been a while since my update box has been empty. Drove me nuts!

Glad I could help..curious if you had this problem too... Did you boot screen lose resolution after this change? Like the ubuntu logo is huge on start up and log off?

---

### Post by Warprunner on 2010-07-01
> **amdemas said:**
> Glad I could help..curious if you had this problem too... Did you boot screen lose resolution after this change? Like the ubuntu logo is huge on start up and log off?

What I had was that I couldn't use my external monitor. I do alot of graphic manipulation and a laptop screen doesn't get it. The external monitor was flickering and the resolution was off...fuzzy. It looked like 60hz interference. It was as soon as the logo was displayed.

---

### Post by amdemas on 2010-07-01
Yea i had the same trouble with mine... I would have to disable my laptop monitor completely for it to work on the external it was really annoying lol. Now i have it though when i boot my machine the resolution is in the 600x800 for the purple boot splash and then when it gets to the sign in it auto corrects itself. Its something i can live with but it doesnt look pretty if I show someone what Ubuntu is all about you know.  Did you have that kind of issue with the login?

---

### Post by Warprunner on 2010-07-01
> **amdemas said:**
> Yea i had the same trouble with mine... I would have to disable my laptop monitor completely for it to work on the external it was really annoying lol. Now i have it though when i boot my machine the resolution is in the 600x800 for the purple boot splash and then when it gets to the sign in it auto corrects itself. Its something i can live with but it doesnt look pretty if I show someone what Ubuntu is all about you know.  Did you have that kind of issue with the login?

Nope, mine was constant. I had to use the laptop screen. Once I put the older beta kernal headers on...fixed it all. I just didn't like having to not update. So with thanks to you...that issue is solved and I am running great! Thank you again!

---

### Post by amdemas on 2010-07-01
> **Warprunner said:**
> Nope, mine was constant. I had to use the laptop screen. Once I put the older beta kernal headers on...fixed it all. I just didn't like having to not update. So with thanks to you...that issue is solved and I am running great! Thank you again!


No problem glad to help out

---

