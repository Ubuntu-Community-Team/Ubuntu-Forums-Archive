---
title: "Ubuntu on 2nd harddrive: Errors! Please help."
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Skeer on 2009-01-07
I had ubuntu 8.10 64bit on my 1st hard drive working flawlessly. I'm dual booting with vista home right now. I had erased the partition and installed ubuntu on my 2nd hd now. The main thing is that my internet doesn't work, but there are tiny differences like the volume controll being faulty but i can live with that.

Do you guys think of why ubuntu wouldn't work as before? Thanks!

PS
Do you guys know where to check system specs?

---

### Post by hotweiss on 2009-01-07
> **Skeer said:**
> I had ubuntu 8.10 64bit on my 1st hard drive working flawlessly. I'm dual booting with vista home right now. I had erased the partition and installed ubuntu on my 2nd hd now. The main thing is that my internet doesn't work, but there are tiny differences like the volume controll being faulty but i can live with that.

Do you guys think of why ubuntu wouldn't work as before? Thanks!

PS
Do you guys know where to check system specs?

What network card do you have? Usually the best thing to do in such a case is to use NDISwrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Skeer on 2009-01-07
Mine is a wired connection (sorry, forgot to mention)
I am sure that it isnt the network card's problem because it worked before and on liveCD

---

### Post by hotweiss on 2009-01-08
> **Skeer said:**
> Mine is a wired connection (sorry, forgot to mention)
I am sure that it isnt the network card's problem because it worked before and on liveCD

Write lspci in terminal to see what network card you have...

---

