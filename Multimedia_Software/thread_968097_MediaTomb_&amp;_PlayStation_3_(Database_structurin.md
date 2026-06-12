---
title: "MediaTomb &amp; PlayStation 3 (Database structuring issues)"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Apocrathia on 2008-11-02
So I have MediaTomb setup on my  Ubuntu home server, it's pretty awesome. No real complaints. I have noticed that my database is wiped upon reboot, however I think it's because I am loading files off of NTFS partitions and they just don't get mounted on the initial system boot. No big deal, I'm waiting on a couple of terrabyte drives and a sata backplane to start centralizing everything to a raid.
My worry is about the actual file structure of the database. Everything is just lumped into the same container. For instance, I have the complete south park series to date. That is going to be a big problem when I get it on to the same drive as everything else (It's sitting on another computers smb share right now because I don't have the room for it anywhere else). If everything is just lumped into the same container, that means I am going to have several hundred south park episodes in the list rather than them being lumped into a container.
How can I get the MediaTomb database to mirror the structure of my filesystem? I am going to have all of my media shared via AFP (netatalk) and all managed from my iMac. I've already got everything in place and ready to go, but this is the only hitch I've run into so far. I've already got a PC in my living room (soon to be reformatted to mythbuntu) that is serving as a media center front end for all of my data on the server. However, I am trying to get everything running through the PS3 as well, but it's a big problem if it takes me 10 minutes to look through a massive list of ALL of my videos just to find the one I am looking for.
Any ideas?
(PS: I know I could manually make containers for everything, but that's just a real pain in the ***. I just want to keep a scan going every so often that will scan for new data and mirror the file systems structure accordingly.

---

### Post by ut40755 on 2008-11-02
I just set this up myself, and although everything is lumped together in your MT database, when you go through it in your ps3, if you go through the PC directory folder instead of video, it takes you through the exact hierarchy on your drive you imported from.

---

