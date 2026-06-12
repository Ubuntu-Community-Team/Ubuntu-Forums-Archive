---
title: "Auto scan and backup changes to server"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by sentiax on 2009-02-23
Ok so here's the deal. I've got a main gaming desktop that I use all the time. I've also got an HTPC and a Fileserver. My dilemma is that I like to have my Music, Pictures, Videos, and other important data backed up onto the Fileserver (which is running Xubuntu). 

I've gotten FTP, Samba, and everything setup correctly, can access it from outside the home network and stuff so I can stream music to my laptop when I'm on my college campus without having to take up so much hdd space on my laptop, as well as backup my programming and essay homework. 

What I would like to do is have the fileserver automatically detect  changes in my main desktops 1TB hard drive where all the Music, videos etc are originally from and then copy the new files to itself. Is there any way to have this done without it completely copying the whole folders over. I've found a guide on how to do it with rsync, but it basically copies the entire folder over again, and with 230GB worth of data, that's not worth it every time there's a 20MB change.

Just as an example and for more details in case I've made this confusing:

My terrabyte hard drive on my main Desktop is J:\. The folders I have backed up onto the Fileserver from J:\ are titled Games, Installs, ISO, Pictures, Music, Vids and are named exactly that on the fileserver as well. Let's say I buy a new Album from Itunes and save it to J:\Music\<artist name>\<album name> is there a way to have the fileserver detect that change, and then automatically copy JUST the new data?

Thanks in advance for help. Let me know if I need to give any more info.

---

