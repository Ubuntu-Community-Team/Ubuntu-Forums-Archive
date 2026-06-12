---
title: "Wired Network Stopped Working, works with Win XP"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Trophy on 2010-10-22
Hi All, 

It has been a while and many ubuntu updates since i connected the windows laptop, it used to work fine but this ubuntu machine keeps telling me the cable is unplugged. When i boot into windows XP the network works fine and the laptop can connect through the network to use the internet. I have a very simple home network ... 3 pc into one switch. I am by no stretch of the imagination good with networking. PLease help

---

### Post by Trophy on 2010-10-22
I have the [same problem]("http://ubuntuforums.org/showthread.php?p=10012501"). I know the hardware is good. If i boot into windows .. the network works fine. Back into Ubuntu and it keeps telling me the network cable is unplugged. I am waiting for some to try and help me tackle this one.

---

### Post by Iowan on 2010-10-22
Moved to new thread - merged with similar (duplicate?).

This is a 10.04 upgrade - not a 10.10?

---

### Post by jerrrys on 2010-10-23
haven't had this problem, but my kernel is not up to date either.  have either one of you Trophys :) tried backing up to a prior kernel?

---

### Post by Trophy on 2010-10-23
Sorry, i thought i had posted the second comment with someone elses thread ... not sure what happened. When you say restore to a previous kernel .. do you mean choose one of the older boot options to load ubuntu in the grub menu?

---

### Post by jerrrys on 2010-10-23
yes, when grub comes up you have 10 seconds to choose or you default to the latest kernel.  default kernel should be generic.  use your arrow key and drop down to the next (older) generic kernel and enter

---

### Post by Trophy on 2010-10-23
Cool, I'll try when i get back ... if that does work ... does that mean it was the kernal upgrade and i will have to keep choosing the older one each time i want to use the network? And then hope it is fixed in a later kernal update.

---

### Post by jerrrys on 2010-10-23
yes, thats about the size of it.  you can send in a trouble report and/or search [**launchpad**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=launchpad&as_qdr=all&sa=Google+Search&lang=en#1041") site.  some people even [**lock**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=lock+kernel&as_qdr=all&sa=Google+Search&lang=en#1093") their kernel.  good luck

i should also add that this is just one possibility and [**others**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=troubleshooting+wired+networks&as_qdr=all&sa=Google+Search&lang=en#1154") exist

---

