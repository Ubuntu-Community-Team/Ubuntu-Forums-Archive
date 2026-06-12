---
title: "Home Media Networks: An inquiry to the masters of networking"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Rockman4140 on 2009-12-16
This community has been so good to me, and I hope I will be blessed with knowledge I can impart back to the community one day, but I yet again ask for help, more like a peer review of an idea I have.

I would like to turn my old desktop into a media server. I've got a few TB external hard drives with the recent Black Friday sales, and I had planned on using them for general storage and media storage. My idea was to have my old desktop running some flavor of Ubuntu to have a constant, always on media "node". Then I got to thinking about what else the network could do for me; I thought that networked disk images wouldn't be a bad idea, but I have no clue how to implement something like that.

My other ordeal would be having stored copies of programs I wouldn't use often, like... GIMP or something, so I could use it when needed, but keep it stored on the remote PC.

Is there any advantage to running Ubuntu Server Edition for such a project, and if so, what would be a decent program I could look into for such a task? My network is currently a mismatch of Ubuntu clients and Windows clients, so interoperability for the imaging would also be an awesome thing if possible.

If you haven't left yet of my mad notion, thank you for reading this.

---

### Post by endeavormac on 2009-12-16
Samba will hook you up with windows file sharing, but honestly, when it comes to file sharing on a private network, I usually just stick with ftp.

First, understand if you're on a 100mbps network, the theoretical fastest you're going to transfer information is 12.5mb/s. You're computer should be able to read off those externals at something close to 20-25mb/s, and the speed difference will be noticable when transferring movies. Perhaps upgrade to gigabit ethernet if you need to.

But as far as ubuntu goes, I would just install ubuntu server on the machine, and ftp in to access your external hard drives.

If you want something else, look into NFS for your linux machines, and Samba for your windows machines.

---

### Post by doas777 on 2009-12-16
I disagree about FTP. use Samba for internal networks. FTP requires you to save each file to your host before use, rather than streaming it live.

it would be hard to install applications on remote drives (not impossible but tricky) since install pathing is usually automated with repo operations. 

I have a simmilar rig (a box with many 1TB drives for sharing media content), and I also run DNS, DHCP, a Firefly music streaming server (it's a lot easier than it sounds), sabnzb+, and torrentflux, and freenx off that box.

that way, whatever room of the house I'm in, I can play a playlist of audio or video, queue up a torrent or nzb, or just remote into the server desktop.

BTW, I would recomend using a desktop edition for your home server. the ubuntu server package does not have a gui by default, and for home servers that can be useful. wouldn't expose it to the public Internet though.

---

### Post by Rockman4140 on 2009-12-16
I need to look a bit more into my network plan and securing it as much as possible before I throw up something like that.

doas777, thanks for the name drops on the programs and the proof of concept, it will motivate me to look into it further.

I recall browsing across something involving X to run processes on other networked computers, I'll need to try and find it later.

Any other suggestions would be absolutely amazing.

---

