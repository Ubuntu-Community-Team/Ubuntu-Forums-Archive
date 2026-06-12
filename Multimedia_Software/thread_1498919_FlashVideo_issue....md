---
title: "Flash/Video issue..."
date: 2010-06-01
forum: Multimedia Software
---

### Post by Linuxperiment on 2010-06-01
Sometimes when I watch videos on YouTube, it'll stop loading and then all of a sudden I can't go to anymore websites, even if I close the website. Here's a sequence of events that usually happens:

1. I watch YouTube video.
2. It stops loading (gives those circles that indicate it is loading)
3. I close it, and open another Window/Tab. I type in some random address, and website won't load.
4. I restart my computer then it is all fine again.

My hardware:
MSI U120 (netbook)
1 GB RAM
1.6 GHZ Intel Atom
Intel GMA 950 Graphics
Ubuntu 10.04
BIOS Flashed to the latest BIOS

I know that the Atom/950 combo isn't the best for flash viewing, but flash is smooth but then it just stops, so I know something is buggy/wrong here. Can anyone assist?

---

### Post by Linuxperiment on 2010-06-02
Anyone?

---

### Post by cchhrriiss121212 on 2010-06-02
Sounds like a wireless dropout to me, is your signal strong?

---

### Post by Linuxperiment on 2010-06-02
> **cchhrriiss121212 said:**
> Sounds like a wireless dropout to me, is your signal strong?

It's generally 65-75%.

---

### Post by cchhrriiss121212 on 2010-06-02
i have a similar strength but it still gets interupted sometimes. If this happens again try disabling and enabling wireless, its not much of a fix but should be quicker than a reboot.

---

### Post by gandaran on 2010-06-02
could also be /temp directory is running out of space, you root partition, is it full?
try deleting all temporary files in /temp when it stops loading.
also run this command to clean up all downloaded packages in root file system.
```
sudo apt-get clean
```

---

