---
title: "Dvd"
date: 2008-09-14
forum: Multimedia Software
---

### Post by cowboytech on 2008-09-14
I am new to Linux (Ubuntu 8.04) but not to computers. I've worked on computers for 40 years. No matter what I do, I can get only about half my DVD's to play on my Ubuntu 8.04 desktop. My machine is an AMD X2-6400+ w/2 gig DDR2 RAM, (2) 320 Gig vertical write SATA 7200 w/16 meg cache hard drives, (2) Geforce 8500 SLI Video cards with 512 DDR2 RAM each (1 gig total video RAM). Everything, hardware wise (sound, video, etc) works fine, but some DVD's play and some don't.

I've tried Mplayer (all codecs), SMplayer, VLC (no screen shows up, just menu), Gnome Player, and a couple others. Would love to get this working so I can finally start using the Ubuntu more often and start distancing myself from the Vista Ultimate desktop (not that I will ever completely give up on Windows).

Otherwise, I just love Ubuntu, and spend time helping others learn it.

---

### Post by lisati on 2008-09-14
Have you installed the codec to play encrypted DVDs? This can be done from the Terminal (from the Applications->Accessories->Terminal menu) with the following command:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

