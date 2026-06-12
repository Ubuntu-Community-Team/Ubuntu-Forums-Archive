---
title: "Linksys WMP54G: Freeze on Boot"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Raptor45 on 2006-06-03
I just reinstalled Ubuntu (I had wanted a clean install), however it now fails to boot. It pauses when it reaches Configuring Network Interfaces. It doesn't appear to actually crash, but I've let it sit for 5-10 mins and it did not continue. I have the same issue in the safe mode. I assume this is due to the WMP54G, I have the one with the Ralink chip.

I originally had issues with seeing the card in Breezy (the OS would run fine, just wouldn't see the card), but got around that by using Ralink's linux drivers. I had hoped that would it would be able to run natively in Dapper, but now it appears it won't even start. Could anyone help?

---

### Post by Raptor45 on 2006-06-04
I got it started by reinstalling. Aparantly it was trying to use the settings I had (unsucessfully) tried on the Live CD. Anyone have advice on setting it up? Searching around it seems others are having problems with connecting as well..

---

### Post by djsroknrol on 2006-06-07
Take a look at this I found tonight...I have the same card someone gave me and I'm in investigative mode right now, weighing weither or not to install it...

[http://ubuntuforums.org/showthread.php?t=161376]("http://ubuntuforums.org/showthread.php?t=161376")

---

### Post by RavenOfOdin on 2006-06-08
Did you download the Ralink Network Configuration Utility from repositories?

It should be labeled as "rt2500"

---

### Post by bionnaki on 2006-06-08
wmp54g is easy to set up...no need to download/install anything. works out of the box. see the link djsroknrol posted....and just follow my instructions.

---

### Post by loserboy on 2006-08-06
> I just reinstalled Ubuntu (I had wanted a clean install), however it now fails to boot. It pauses when it reaches Configuring Network Interfaces. It doesn't appear to actually crash, but I've let it sit for 5-10 mins and it did not continue. I have the same issue in the safe mode. I assume this is due to the WMP54G, I have the one with the Ralink chip.

I'm having the exact same problem...  Is there anyway to fix this without re-installing

---

