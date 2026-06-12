---
title: "About the graphic card."
date: 2010-01-27
forum: Multimedia Software
---

### Post by BlindSoul on 2010-01-27
[B]Hey.

I'm new here and i had a few questions.
I'm getting a new Desktop tomorrow and i would like to install on it the latest version of Ubuntu. But i don't know if the graphic card i'm gonna have has a driver for Ubuntu. How is it possible to check? Since on the Nvidia website there isn't...
My graphic card gonna be Geforce GT240 1GB Ram.


Does anyone can help me?

Thank you!
Ryan.[/B]

---

### Post by realzippy on 2010-01-27
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

..there is GT 240

---

### Post by cascade9 on 2010-01-27
> **realzippy said:**
> [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

..there is GT 240

Nah, there is not. You get the classic msg-

> No certified downloads were found for this configuration. To include beta downloads in your search, click [here]("http://www.nvidia.com/Download/Find.aspx?lang=en-us").'here' leads you to the beta section...and there is no drivers there either for the GTS240. (or GT230 for that matter)

---

### Post by BlindSoul on 2010-01-27
" No certified downloads were found for this configuration. To include beta downloads in your search, click here. "

---

### Post by LuisGMarine on 2010-01-27
I have the GTS 250 and it works great with the 185 drivers that you find and install by going to System > Administration > Hardware Drivers.

So yes if yours is one model down, I'm sure its supported.  Good luck!

---

### Post by BlindSoul on 2010-01-27
Okay i will check it out when i will have it installed. Anyone have other suggestions? Incase it won't work... Also, When i had Linux on my VMware. When i was installing drivers it always took me to a black page and i had to write user password. But everytime i was writing it it didn't type anything... O.o Does anyone know why?

---

### Post by realzippy on 2010-01-27
> **cascade9 said:**
> Nah, there is not. You get the classic msg-

'here' leads you to the beta section...and there is no drivers there either for the GTS240. (or GT230 for that matter)

ok,they are not supported,but 195.xx seems to run.

[http://www.nvnews.net/vbulletin/showthread.php?t=142020&page=5](http://www.nvnews.net/vbulletin/showthread.php?t=142020&page=5)

---

### Post by cascade9 on 2010-01-27
> **realzippy said:**
> ok,they are not supported,but 195.xx seems to run.

[http://www.nvnews.net/vbulletin/showthread.php?t=142020&page=5](http://www.nvnews.net/vbulletin/showthread.php?t=142020&page=5)

Hmm..this is why I hate people making multipule threads on one subject. Other thread here-

[http://ubuntuforums.org/showthread.php?t=1391904](http://ubuntuforums.org/showthread.php?t=1391904)

The open source nv driver works, 190.xx works, 195.xx works better. But there are _major_ issues with the performance of the 190.xx/195.xx drivers with the GTS240. See here-

[http://www.phoronix.com/scan.php?page=article&item=ecs_geforce_240&num=1](http://www.phoronix.com/scan.php?page=article&item=ecs_geforce_240&num=1)

My guess is that it wont get 'official' support under linux until at least 195.xx being out of beta...and probably more like the 200.xx series drivers.

---

