---
title: "I can't play dvds"
date: 2009-01-06
forum: Multimedia Software
---

### Post by Dustin2128 on 2009-01-06
I've got a million different movie players, but totem, and real won't work, and I can't figure out how to get it in the other problems. If it helps at all, I'm trying to watch Lord of the rings 2 towers, and it's on a dual layer disk. If you could answer quickly, I would like to watch the movie tonight:popcorn:

---

### Post by Dustin2128 on 2009-01-06
ha ha ha, I meant programs, not problems

---

### Post by wolfen69 on 2009-01-06
are you using intrepid? if so, open terminal and do: (copy and paste)
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``` then 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` then
```
sudo apt-get install libdvdcss2
```

---

### Post by mikeize on 2009-01-06
Have you tried using VLC?  It's a fantastic media player that plays almost anything.

---

### Post by wolfen69 on 2009-01-06
> **mikeize said:**
> Have you tried using VLC?  It's a fantastic media player that plays almost anything.

unless you have libdvdcss2 installed, vlc will not play encrypted dvd's. only the windows version ships with dvd playback capability.

---

### Post by Dustin2128 on 2009-01-06
I don't mean to sound like an idiot, thanks for all the help, but how do you play dvd's in vlc, I've got it, but can't figure it out! By the way, if anyone wants to know, I'm running hardy, because intrepid dosen't have a good nvidia driver.

---

### Post by Dustin2128 on 2009-01-06
I'm running hardy

---

### Post by Dustin2128 on 2009-01-06
oh! I got it, but on the other hand, how do I rip dvds, I have acid rip, but I can't figure out how to do it! I have a huge hard drive, and most of my movies get scratched up.

---

### Post by Lee_Machine on 2009-01-06
To rip dvds just use the program DVD::RIP its found in add/remove programs.

I find it better than acid rip.

Here is an extensive how to

[http://www.exit1.org/dvdrip/doc/gui.cipp](http://www.exit1.org/dvdrip/doc/gui.cipp)

enjoy :popcorn:

---

