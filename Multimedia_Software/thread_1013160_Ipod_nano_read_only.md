---
title: "Ipod nano read only"
date: 2008-12-16
forum: Multimedia Software
---

### Post by HEN*K on 2008-12-16
Hi!

I have recently had to reset my 1st gen. Nano to factory settings because every two months or so it gets crashed. Anyway, the last time I did it, afterwards the gtkpod application would work jsut fine and put new music onto it without any problems, but this time it first determined my 4 Gb Ipod as a 256 mb device and then as I reset it (again) on a friends Mac through Itunes and got back home, the Ipod is suddenly readonly. What could I do to resolve this problem (without having to buy a new computer or a new Ipod). Has any one had this problem before and how can I solve it? Gtkpod used to work just fine... The newest Itunes claims that my Ipod has the most recent upgrade and there was no problem loading music onto it at my friends house on his Mac. Is there any other program than gtkpod or is there any way to get my Ipod working again through Ubuntu? I would be very greatful for any help on the subject as I'm not very used to resolving problems in a Linux environment.

Thanks!

/Henke

---

### Post by razy60 on 2008-12-16
as a suggestion you probably need to go back to your friends and reset the ipod, i suspect that something in your friends mac has set it to read only, so that at the moment only a mac can access it correctly.
 Itunes is funny like that. It can get a bit proprietary especially with macs and the fact that you used his mac to load music etc, something to do with ......apple licensing.

Raz

---

### Post by HEN*K on 2008-12-21
Now I've tried resetting the Ipod again and also we found some settings to change through the Mac so that it appears that it would no longer be read-only. But it doesn't work any way. If I make the Ipod accessible for all users and turn off every possible setting that might make it read-only, and then save and close, then the former settings are still applied when I open the Ipos again. I can't figure out how to solve this problem...

/Henke

---

### Post by razy60 on 2008-12-21
I dont know if this is any good to you, it might help.                      
[http://www.poddox.com](http://www.poddox.com)

Raz

---

### Post by ruru on 2008-12-24
I also use a mac-formatted iPod nano under ubuntu and also have problems sometimes with it being mounted read-only.
A couple of suggestions though; set 'ignore permissions', and make sure that journalling is turned off on the iPod. Linux can read/write HFS+ without journalling, but can only read journalled HFS+ volumes. Resetting the iPod may have changed these back to defaults.

That being said, this does not solve my current read-only problem, but it is somewhere to start...

---

### Post by ruru on 2008-12-24
Check out [_this post_]("http://ubuntuforums.org/showthread.php?t=999300&highlight=mount+read+ipod#7"). This was the solution for me...

---

