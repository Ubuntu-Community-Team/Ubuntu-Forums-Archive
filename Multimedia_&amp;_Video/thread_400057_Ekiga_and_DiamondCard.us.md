---
title: "Ekiga and DiamondCard.us"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by Michlis on 2007-04-03
Hi,
I wanted to make PC-To-Phone calls from my Ubuntu desktop (6.06) so I opened Ekiga (2.0.1) and created an account in DiamondCard.us as advised.
The problem is that I can't set up this account in Ekiga. I put my account ID and Pin code from DiamondCard.us as account number and password in the PC-To-Phone configuration window, but I get "Registration failed" error. Can you help me solve the problem?
Maybe it's because of my network? I'm using academic network, maybe there are some firewalls etc. Should I change default Ekiga configuration settings? Or maybe I should try another soft phone working with DiamondCard.us?

---

### Post by depp on 2007-04-20
you should use the user id and pin, that you find on your homepage at diamondcard.us. they are not the ones you use to logon diamondcard.us.

---

### Post by Michlis on 2007-04-20
> **depp said:**
> you should use the user id and pin, that you find on your homepage at diamondcard.us.
I know and that's exactly what I'm doing, but still it doesn't work. All the time I get "registration failed" error. I tried Gizmondo and it seems to register but when I dial a number there is no connection (Denmark->Poland). To be sure I tried DiamondCard's windows softphone and it also doesn't work! I can dial a number, but after ~30s there is still no connection and I get a timeout error. Looks like I just have lost 10$ :(

---

### Post by depp on 2007-04-20
upgrade your ekiga to have another try. 
here ist the address of the repo for dapper.
[http://wiki.ekiga.org/index.php/Linux_Users#Dapper_i386]("http://wiki.ekiga.org/index.php/Linux_Users#Dapper_i386")

---

### Post by Michlis on 2007-04-21
Unfortunatelly, update didn't help at all. I have an impression that it's even worst then before, because I can't even connect to Ekiga account. I get "registrafion failed - timouot error" for both Ekiga and PC-to-phone account. I am starting to suspect my academic network, maybe it blocks some ports and cause this problems...(However, VoIPDiscount on Windows was running for test without any problems)

---

### Post by sup on 2007-04-21
you can use another voip provider than DiamondCard. I emailed the developer about that and he said it worked and I tried it and it worked - however when I asked him to alter that misleading FAQ, he did not do so, I guess DiamondCard is a sponsor of Ekiga or something...

---

### Post by Michlis on 2007-04-21
I'm not sure if I want to spend next 10$ or 10e for service that may not work again. What makes me worried is that I can't even conect to Ekiga account and make a echo test call.

---

### Post by sup on 2007-04-21
Just to be sure, did you see [this]("http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x149.html")?
And also [this]("http://www.gnomemeeting.org/index.php?rub=3&pos=0&faqpage=x161.html")? I once found that Ekiga could not get through my router, try, I you can, use it at a different location.

---

### Post by twoey on 2008-04-24
I know this might be a late reply but you might want to check your  more options (or advance settings) when your putting your id and pincode. Make sure your ID is in the Authentication Login. At least thats what the problem was with me. Hope this helps for anyone else who might experience the same problem.

---

