---
title: "Need a simple way to get ipod shuffle 2nd gen working"
date: 2013-12-19
forum: Multimedia Software
---

### Post by sofasurfer on 2013-12-19
I have a ipod shuffle that someone at work wants me to get working for them. I know nothing about them. I dragged some songs onto it but they would not play. I then learned that rythmbox was supposed to make it work. So I installed it and attached the ipod to the computer. I was given the option to initialize. I then loaded more songs. When I tried to play them only one song would play. I then hooked it back up to the computer and deleted all files. Then when I played it the song that played before STILL WAS ON IT AND STILL PLAYED. Then I messed around with GTKPOD and banshee. Now I can get nothing to play on it. Any ideas on how I can make this thing work without going though all kinds of crap. I'm really not up to figuring out how to run all kinds of commands and stuff. Getting to old and tired for that. Is there an easier way?

---

### Post by tgalati4 on 2013-12-19
You have to initialize the ipod on a Windows machine using iTunes and that wipes it and puts a FAT32 file system on it.  Then the linux packages can interact with it.  Otherwise the ipod is formatted with HFS+ and you have to turn off journaling (turning it into HFS filesystem) using a Mac computer and Disk Utilities.  There are some linux utilities to do that but they are not consistent with your premise.

---

